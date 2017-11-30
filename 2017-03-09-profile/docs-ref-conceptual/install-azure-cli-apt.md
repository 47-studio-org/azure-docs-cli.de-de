---
title: Installieren der Azure CLI 2.0 mit apt
description: Installieren der Azure CLI 2.0 mit dem apt-Paket-Manager
keywords: Azure CLI,Azure CLI installieren,Azure apt, Azure Debian, Azure Ubuntu
author: sptramer
ms.author: sttramer
manager: routlaw
ms.date: 11/01/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ROBOTS: NOINDEX,NOFOLLOW
ms.openlocfilehash: 93d947d91973def1c05e2f5b2e7511bc1c5704a2
ms.sourcegitcommit: 905939cc44764b4d1cc79a9b36c0793f7055a686
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2017
---
# <a name="install-azure-cli-20-with-apt"></a><span data-ttu-id="9fb67-104">Installieren der Azure CLI 2.0 mit apt</span><span class="sxs-lookup"><span data-stu-id="9fb67-104">Install Azure CLI 2.0 with apt</span></span>

<span data-ttu-id="9fb67-105">Wenn Sie eine Distribution ausführen, in der `apt` enthalten ist (etwa Ubuntu oder Debian), steht ein Paket für die Azure CLI zur Verfügung, das Sie auf Ihrem System installieren können.</span><span class="sxs-lookup"><span data-stu-id="9fb67-105">If you are running a distirbution that comes with `apt`, such as Ubuntu or Debian, there is an available package for the Azure CLI that you can install on your system.</span></span>

> [!NOTE]
> <span data-ttu-id="9fb67-106">Sie benötigen Python 2.7.x oder Python 3.x, um die CLI nutzen zu können.</span><span class="sxs-lookup"><span data-stu-id="9fb67-106">You must have Python 2.7.x or Python 3.x in order to use the CLI.</span></span> <span data-ttu-id="9fb67-107">[Installieren Sie Python](https://www.python.org/downloads/), wenn Ihre Distribution keines dieser Pakete enthält.</span><span class="sxs-lookup"><span data-stu-id="9fb67-107">If your distribution does not have a package for either, [install Python](https://www.python.org/downloads/).</span></span>

## <a name="install"></a><span data-ttu-id="9fb67-108">Installieren</span><span class="sxs-lookup"><span data-stu-id="9fb67-108">Install</span></span>

1. <span data-ttu-id="9fb67-109">Ändern Sie die Quellenliste:</span><span class="sxs-lookup"><span data-stu-id="9fb67-109">Modify your sources list:</span></span>
 
   - <span data-ttu-id="9fb67-110">32-Bit-System</span><span class="sxs-lookup"><span data-stu-id="9fb67-110">32-bit system</span></span>

     ```bash
     echo "deb https://packages.microsoft.com/repos/azure-cli/ wheezy main" | \
          sudo tee /etc/apt/sources.list.d/azure-cli.list
     ```

   - <span data-ttu-id="9fb67-111">64-Bit-System</span><span class="sxs-lookup"><span data-stu-id="9fb67-111">64-bit system</span></span>

     ```bash
     echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ wheezy main" | \
          sudo tee /etc/apt/sources.list.d/azure-cli.list
     ```

2. <span data-ttu-id="9fb67-112">Führen Sie die folgenden sudo-Befehle aus:</span><span class="sxs-lookup"><span data-stu-id="9fb67-112">Run the following sudo commands:</span></span>

   ```bash
   sudo apt-key adv --keyserver packages.microsoft.com --recv-keys 52E16F86FEE04B979B07E28DB02C46DF417A0893
   sudo apt-get install apt-transport-https
   sudo apt-get update && sudo apt-get install azure-cli
   ```

<span data-ttu-id="9fb67-113">Sie können die Azure CLI mit dem Befehl `az` ausführen.</span><span class="sxs-lookup"><span data-stu-id="9fb67-113">You can run the Azure CLI with the `az` command.</span></span>

## <a name="update"></a><span data-ttu-id="9fb67-114">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="9fb67-114">Update</span></span>

<span data-ttu-id="9fb67-115">Verwenden Sie `apt-get upgrade` zum Aktualisieren des CLI-Pakets.</span><span class="sxs-lookup"><span data-stu-id="9fb67-115">Use `apt-get upgrade` to update the CLI package.</span></span>

   ```bash
   sudo apt-get update && sudo apt-get upgrade
   ```

> [!NOTE]
> <span data-ttu-id="9fb67-116">Dadurch werden alle installierten Pakete auf Ihrem System aktualisiert, deren Abhängigkeiten nicht geändert wurden.</span><span class="sxs-lookup"><span data-stu-id="9fb67-116">This will upgrade all of the installed packages on your system which have not had a dependency change.</span></span>
> <span data-ttu-id="9fb67-117">Um nur die CLI zu aktualisieren, verwenden Sie `apt-get install`.</span><span class="sxs-lookup"><span data-stu-id="9fb67-117">To upgrade only the CLI, use `apt-get install`.</span></span>
> ```bash
> sudo apt-get update && sudo apt-get install --only-upgrade -y azure-cli
> ```

### <a name="uninstall"></a><span data-ttu-id="9fb67-118">Deinstallieren</span><span class="sxs-lookup"><span data-stu-id="9fb67-118">Uninstall</span></span>

<span data-ttu-id="9fb67-119">Es tut uns leid, wenn Sie die Azure CLI deinstallieren möchten.</span><span class="sxs-lookup"><span data-stu-id="9fb67-119">If you ever decide to uninstall the Azure CLI, we're sorry to see you go.</span></span> <span data-ttu-id="9fb67-120">Teilen Sie uns vor der Deinstallation mithilfe des Befehls `az feedback` mit, warum Sie sich für die Deinstallation entschieden haben und wie wir die CLI verbessern können.</span><span class="sxs-lookup"><span data-stu-id="9fb67-120">Before you uninstall, use the `az feedback` command to give us some reasons why you chose to uninstall and how we could improve the CLI experience.</span></span> <span data-ttu-id="9fb67-121">Wir möchten sicherstellen, dass die Azure CLI möglichst fehlerfrei und benutzerfreundlich ist.</span><span class="sxs-lookup"><span data-stu-id="9fb67-121">We want to make sure that the Azure CLI is as bug-free and user-friendly as we can make it.</span></span> <span data-ttu-id="9fb67-122">Sie können auch ein [GitHub-Problem melden](https://github.com/Azure/azure-cli/issues).</span><span class="sxs-lookup"><span data-stu-id="9fb67-122">You can also [file a github issue](https://github.com/Azure/azure-cli/issues).</span></span>

1. <span data-ttu-id="9fb67-123">Deinstallieren Sie sie mit `apt-get remove`.</span><span class="sxs-lookup"><span data-stu-id="9fb67-123">Uninstall with `apt-get remove`.</span></span>

    ```bash
    sudo apt-get remove -y azure-cli
    ```

2. <span data-ttu-id="9fb67-124">Entfernen Sie die Azure CLI-Repositoryinformationen, wenn Sie nicht planen, die CLI neu zu installieren.</span><span class="sxs-lookup"><span data-stu-id="9fb67-124">If you do not plan to reinstall the CLI, remove the Azure CLI repository information.</span></span>

   ```bash
   sudo rm /etc/apt/sources.list.d/azure-cli.list
   ```

3. <span data-ttu-id="9fb67-125">Entfernen Sie alle nicht benötigten Pakete.</span><span class="sxs-lookup"><span data-stu-id="9fb67-125">Remove any unneeded packages.</span></span>

   ```bash
   sudo apt autoremove
   ```