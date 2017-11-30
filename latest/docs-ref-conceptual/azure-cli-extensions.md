---
title: Azure CLI 2.0-Erweiterungen
description: Verwenden von Erweiterungen mit Azure CLI 2.0
keywords: Azure CLI, Erweiterungen
author: sptramer
ms.author: sttramer
manager: routlaw
ms.date: 10/30/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ms.openlocfilehash: 930073324d68f9719ce5035388120e7b6ac41a98
ms.sourcegitcommit: 93f6bd2c199774fcb3b43c6b14d714196873ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="using-extensions-with-the-azure-cli-20"></a><span data-ttu-id="c3934-104">Verwenden von Erweiterungen mit Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="c3934-104">Using extensions with the Azure CLI 2.0</span></span>

<span data-ttu-id="c3934-105">Erweiterungen sind einzelne Module, die nicht mit der Azure CLI bereitgestellt werden und die Ihnen das Hinzufügen von Funktionen mit neuen Befehlen ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c3934-105">Extensions are individual modules not shipped with the Azure CLI itself that allow you to add functionality through new commands.</span></span> <span data-ttu-id="c3934-106">Dies können experimentelle oder Vorabangebote, spezielle Tools, die Microsoft zur Erfüllung Ihrer Anforderungen bereitstellt, oder auch von Ihnen selbst geschriebene Erweiterungen sein.</span><span class="sxs-lookup"><span data-stu-id="c3934-106">These might be experimental or pre-release offerings, specialized tools that Microsoft has for your needs, or even extensions that you yourself have written.</span></span> <span data-ttu-id="c3934-107">Erweiterungen ermöglichen das flexible Anpassen der CLI an Ihre eigenen Anforderungen, ohne dass Sie viele zusätzliche Pakete mitliefern müssen, die nicht als Teil des Kernfeaturesatzes angesehen werden.</span><span class="sxs-lookup"><span data-stu-id="c3934-107">Extensions allow for a degree of flexibility with the CLI that let you modify it to your own needs, without having to ship a lot of additional packages that aren't considered part of the core feature set.</span></span>

<span data-ttu-id="c3934-108">In diesem Artikel wird beschrieben, wie Sie Erweiterungen für die CLI installieren, aktualisieren und entfernen.</span><span class="sxs-lookup"><span data-stu-id="c3934-108">This article will help you understand how to install, update, and remove extensions for the CLI.</span></span> <span data-ttu-id="c3934-109">Außerdem werden häufige Fragen zum Verhalten von Erweiterungen beantwortet.</span><span class="sxs-lookup"><span data-stu-id="c3934-109">It should also answer common questions about extension behavior.</span></span>

## <a name="finding-extensions"></a><span data-ttu-id="c3934-110">Suchen nach Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="c3934-110">Finding extensions</span></span>

<span data-ttu-id="c3934-111">Um zu ermitteln, welche Erweiterungen verfügbar sind, können Sie `az extension list-available` verwenden.</span><span class="sxs-lookup"><span data-stu-id="c3934-111">In order to know what extensions are available, you can use `az extension list-available`.</span></span> <span data-ttu-id="c3934-112">Mit diesem Befehl werden die verfügbaren offiziellen Erweiterungen aufgelistet, die von Microsoft bereitgestellt und unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="c3934-112">This command lists the available, official extensions which are provided and supported by Microsoft.</span></span>

## <a name="installing-extensions"></a><span data-ttu-id="c3934-113">Installieren von Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="c3934-113">Installing extensions</span></span>

<span data-ttu-id="c3934-114">Nachdem Sie eine zu installierende Erweiterung gefunden haben, können Sie `az extension add` verwenden, um sie abzurufen.</span><span class="sxs-lookup"><span data-stu-id="c3934-114">Once you have found an extension to install, use `az extension add` to get it.</span></span> <span data-ttu-id="c3934-115">Wenn die Erweiterung eine offizielle Microsoft-Erweiterung ist, die bei Ausführung von `az extension list-available` aufgeführt wird, können Sie die Erweiterung anhand des Namens installieren.</span><span class="sxs-lookup"><span data-stu-id="c3934-115">If the extension is an official Microsoft extension listed in `az extension list-available`, you can install the extension by name.</span></span>

```azurecli
az extension add --name <extension-name>
```

<span data-ttu-id="c3934-116">Wenn die Erweiterung von einer externen Ressource stammt oder Sie über einen direkten Link dafür verfügen, können Sie die Quell-URL oder den lokalen Pfad angeben.</span><span class="sxs-lookup"><span data-stu-id="c3934-116">If the extension is from an external resource or you have a direct link to it, you can provide the source URL or local path.</span></span> <span data-ttu-id="c3934-117">Dies _muss_ eine kompilierte Python-Wheeldatei sein.</span><span class="sxs-lookup"><span data-stu-id="c3934-117">This _must_ be a compiled Python wheel file.</span></span>

```azurecli
az extension add --source <URL-or-path>
```

<span data-ttu-id="c3934-118">Nach der Installation einer Erweiterung befindet sich diese unter dem Wert der Shellvariablen `$AZURE_EXTENSION_DIR`.</span><span class="sxs-lookup"><span data-stu-id="c3934-118">Once an extension is installed, it can be found under the value of the `$AZURE_EXTENSION_DIR` shell variable.</span></span> <span data-ttu-id="c3934-119">Wenn diese Variable nicht festgelegt ist, befindet sich der Wert standardmäßig unter `$HOME/.azure/cliextensions` (Linux und macOS) bzw. `%USERPROFILE%\.azure\cliextensions` (Windows).</span><span class="sxs-lookup"><span data-stu-id="c3934-119">If this variable is unset, by default the value is `$HOME/.azure/cliextensions` on Linux and macOS, and `%USERPROFILE%\.azure\cliextensions` on Windows.</span></span>

## <a name="updating-extensions"></a><span data-ttu-id="c3934-120">Aktualisieren von Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="c3934-120">Updating extensions</span></span>

<span data-ttu-id="c3934-121">Erweiterungen können nur anhand des Namens aktualisiert werden:</span><span class="sxs-lookup"><span data-stu-id="c3934-121">Extensions can only be updated by name:</span></span>

```azurecli
az extension update --name <extension-name>
```

<span data-ttu-id="c3934-122">Wenn ein Erweiterungsname aus einem bestimmten Grund für die CLI nicht aufgelöst werden kann, sollten Sie die Erweiterung neu installieren, um sie zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c3934-122">If an extension name cannot be resolved by the CLI for whatever reason, reinstall the extension to update it.</span></span> <span data-ttu-id="c3934-123">Außerdem ist es möglich, dass die Erweiterung nicht mehr als Vorschauversion verfügbar und zu einem integrierten Befehl für die CLI geworden ist.</span><span class="sxs-lookup"><span data-stu-id="c3934-123">There is also the possibility that the extension was moved out of preview and became a built-in command for the CLI.</span></span> <span data-ttu-id="c3934-124">Aktualisieren Sie in diesem Fall die CLI, und deinstallieren Sie die Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="c3934-124">In that case, update the CLI and uninstall the extension.</span></span>

## <a name="uninstalling-extensions"></a><span data-ttu-id="c3934-125">Deinstallieren von Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="c3934-125">Uninstalling extensions</span></span>

<span data-ttu-id="c3934-126">Wenn Sie eine Erweiterung nicht mehr benötigen, können Sie sie mit `az extension remove` entfernen.</span><span class="sxs-lookup"><span data-stu-id="c3934-126">If you no longer need an extension, it can be removed with `az extension remove`,</span></span>

```azurecli
az extension remove --name <extension-name>
```

<span data-ttu-id="c3934-127">Sie können eine Erweiterung auch manuell entfernen, indem Sie sie am Installationsspeicherort löschen.</span><span class="sxs-lookup"><span data-stu-id="c3934-127">You can also remove an extension manually by deleting it from the location where it was installed.</span></span> <span data-ttu-id="c3934-128">Dies ist der Wert der Shellvariablen `$AZURE_EXTENSION_DIR`.</span><span class="sxs-lookup"><span data-stu-id="c3934-128">This will be the value of the `$AZURE_EXTENSION_DIR` shell variable.</span></span> <span data-ttu-id="c3934-129">Wenn diese Variable nicht festgelegt ist, befindet sich der Wert standardmäßig unter `$HOME/.azure/cliextensions` (Linux und macOS) bzw. `%USERPROFILE%\.azure\cliextensions` (Windows).</span><span class="sxs-lookup"><span data-stu-id="c3934-129">If this variable is unset, by default the value is `$HOME/.azure/cliextensions` on Linux and macOS, and `%USERPROFILE%\.azure\cliextensions` on Windows.</span></span>

```bash
rm -rf $AZURE_EXTENSION_DIR/<extension-name>
```

<span data-ttu-id="c3934-130">Es wird empfohlen, die Deinstallation mit `az extension remove` durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="c3934-130">It is recommended that you uninstall using `az extension remove`.</span></span>

## <a name="faq"></a><span data-ttu-id="c3934-131">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="c3934-131">FAQ</span></span>

<span data-ttu-id="c3934-132">Hier sind einige Antworten auf andere häufig gestellte Fragen zu CLI-Erweiterungen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="c3934-132">Here are some answers to other common questions about CLI extensions.</span></span>

### <a name="what-file-formats-are-allowed-for-installation"></a><span data-ttu-id="c3934-133">Welche Dateiformate sind für die Installation zulässig?</span><span class="sxs-lookup"><span data-stu-id="c3934-133">What file formats are allowed for installation?</span></span>

<span data-ttu-id="c3934-134">Derzeit können nur kompilierte Python-Wheels als Erweiterungen installiert werden.</span><span class="sxs-lookup"><span data-stu-id="c3934-134">Currently, only compiled Python wheels can be installed as extensions.</span></span>

### <a name="can-extensions-replace-existing-commands"></a><span data-ttu-id="c3934-135">Können Erweiterungen vorhandene Befehle ersetzen?</span><span class="sxs-lookup"><span data-stu-id="c3934-135">Can extensions replace existing commands?</span></span>

<span data-ttu-id="c3934-136">Ja.</span><span class="sxs-lookup"><span data-stu-id="c3934-136">Yes.</span></span> <span data-ttu-id="c3934-137">Erweiterungen können vorhandene Befehle ersetzen, aber vor dem Ausführen eines ersetzten Befehls wird von der CLI eine Warnung ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="c3934-137">Extensions may replace existing commands, but before running a command that has been replaced the CLI will issue a warning.</span></span>

### <a name="how-can-i-tell-if-an-extension-is-in-pre-release"></a><span data-ttu-id="c3934-138">Woran erkenne ich, dass es sich bei einer Erweiterung um eine Vorabversion handelt?</span><span class="sxs-lookup"><span data-stu-id="c3934-138">How can I tell if an extension is in pre-release?</span></span>

<span data-ttu-id="c3934-139">Für eine Erweiterung sollte in der dazugehörigen Dokumentation und in den Versionsinformationen angegeben sein, wenn es sich um eine Vorabversion handelt.</span><span class="sxs-lookup"><span data-stu-id="c3934-139">An extension should indicate through its own documentation and versioning if it is in pre-release.</span></span> <span data-ttu-id="c3934-140">Es kommt auch häufiger vor, dass Microsoft Vorschauversionen von Befehlen für die CLI als Erweiterungen veröffentlicht, die nach der Vorschauphase des Produkts in die Hauptoberfläche der CLI integriert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="c3934-140">It is also common for Microsoft to release preview commands for the CLI as extensions, with plans to move them into the main CLI interface once the product is out of preview.</span></span>

### <a name="can-extensions-depend-upon-each-other"></a><span data-ttu-id="c3934-141">Können Erweiterungen voneinander abhängig sein?</span><span class="sxs-lookup"><span data-stu-id="c3934-141">Can extensions depend upon each other?</span></span>

<span data-ttu-id="c3934-142">Nein.</span><span class="sxs-lookup"><span data-stu-id="c3934-142">No.</span></span> <span data-ttu-id="c3934-143">Erweiterungen müssen einzelne Pakete sein, die nicht voneinander abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="c3934-143">Extensions must be individual packages which do not rely on one another.</span></span> <span data-ttu-id="c3934-144">Dies liegt daran, dass für die CLI nicht garantiert ist, wann Erweiterungen geladen werden. Es kann also nicht sichergestellt werden, dass die Anforderungen von Abhängigkeiten erfüllt werden.</span><span class="sxs-lookup"><span data-stu-id="c3934-144">This is because the CLI gives no guarantee about when extensions are loaded, so dependencies could not be guaranteed to be satisfied.</span></span> <span data-ttu-id="c3934-145">Bei der Installation einer Erweiterung wird nur die jeweilige Erweiterung installiert, und sie sollte auch dann funktionieren, wenn Sie andere Erweiterungen entfernen.</span><span class="sxs-lookup"><span data-stu-id="c3934-145">Installing an extension installs that extension only, and it should continue to work even if you remove other extensions.</span></span>

### <a name="are-extensions-updated-along-with-the-cli"></a><span data-ttu-id="c3934-146">Werden Erweiterungen zusammen mit der CLI aktualisiert?</span><span class="sxs-lookup"><span data-stu-id="c3934-146">Are extensions updated along with the CLI?</span></span>

<span data-ttu-id="c3934-147">Nein.</span><span class="sxs-lookup"><span data-stu-id="c3934-147">No.</span></span> <span data-ttu-id="c3934-148">Erweiterungen müssen separat aktualisiert werden, wie im Abschnitt [Aktualisieren von Erweiterungen](#updating-extensions) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c3934-148">Extensions must be updated separately, as described in the [Updating extensions](#updating-extensions) section.</span></span>