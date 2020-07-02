---
title: Azure CLI-Referenzen für Azure IoT
description: Landing Page der Azure CLI-Referenzen für Azure IoT
author: dbradish-microsoft
manager: barbkess
ms.devlang: azurecli
ms.topic: reference
ms.date: 06/05/2020
ms.author: dbradish
ms.service: azure-cli
ms.reviewer: paymaun.heidari
ms.openlocfilehash: e3bf40eab68f09dfb94e14e59d8a746d87bb0766
ms.sourcegitcommit: 415c6ddcce1da133d96b8c700e6aa570e4746b3f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765091"
---
# <a name="azure-cli-for-azure-iot"></a><span data-ttu-id="2fef8-103">Azure CLI für Azure IoT</span><span class="sxs-lookup"><span data-stu-id="2fef8-103">Azure CLI for Azure IoT</span></span>

<span data-ttu-id="2fef8-104">Die Azure-Befehlszeilenschnittstelle ([Azure CLI](/cli/azure/what-is-azure-cli)) setzt sich aus Befehlen zum Erstellen und Verwalten von Azure-Ressourcen zusammen.</span><span class="sxs-lookup"><span data-stu-id="2fef8-104">The Azure Command Line Interface ([Azure CLI](/cli/azure/what-is-azure-cli)) is a set of commands used to create and manage Azure resources.</span></span>  <span data-ttu-id="2fef8-105">Sie ist in vielen Azure-Diensten verfügbar, darunter auch Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="2fef8-105">It is available across many Azure services including Azure IoT.</span></span>  <span data-ttu-id="2fef8-106">Es gibt mehr als 100 Referenzen für Azure IoT, die Sie bei der effektiven Verwendung von IoT-Diensten über eine Befehlszeile unterstützen.</span><span class="sxs-lookup"><span data-stu-id="2fef8-106">There are over 100 references for Azure IoT giving you the ability to work effectively with IoT services from a command line.</span></span>

## <a name="references-for-iot"></a><span data-ttu-id="2fef8-107">Referenzen für IoT</span><span class="sxs-lookup"><span data-stu-id="2fef8-107">References for IoT</span></span>

<span data-ttu-id="2fef8-108">Die Azure IoT-CLI-Umgebung setzt sich aus zwei Teilen zusammen: aus der Azure CLI (in der Regel als CLI **Core** bezeichnet) und der Azure IoT-CLI-**Erweiterung**.</span><span class="sxs-lookup"><span data-stu-id="2fef8-108">The Azure IoT CLI experience is composed of two parts: Azure CLI (commonly referred to as CLI **core**) and the Azure IoT CLI **extension**.</span></span>

<span data-ttu-id="2fef8-109">Bei den IoT-Funktionen in Azure CLI **Core** stehen Infrastrukturverwaltung und -konfiguration im Mittelpunkt.</span><span class="sxs-lookup"><span data-stu-id="2fef8-109">IoT functionality in Azure CLI **core** is focused on infrastructure management and configuration.</span></span> <span data-ttu-id="2fef8-110">IoT Hub-CRUD-Vorgänge oder das Konfigurieren von IoT Hub-Nachrichtenrouten sind typische Anwendungsfälle für Core-Befehle.</span><span class="sxs-lookup"><span data-stu-id="2fef8-110">IoT Hub CRUD operations, or configuring IoT Hub message routes are typical use cases for core commands.</span></span>

<span data-ttu-id="2fef8-111">Die IoT-**Erweiterung** bietet umfangreiche Features und Funktionen zum Verwalten und Bearbeiten von sowie zum Interagieren mit Daten, Entitäten und Objekten in der Infrastruktur selbst.</span><span class="sxs-lookup"><span data-stu-id="2fef8-111">The IoT **extension** introduces rich features and functionality to manage, manipulate and interact with the data, entities and objects on the infrastructure itself.</span></span> <span data-ttu-id="2fef8-112">Das Verwalten von Gerätebeständen, das Überwachen von Gerät-zu-Cloud-Ereignissen und das Aufrufen von Cloud-zu-Gerät-Methoden werden beispielsweise über die IoT-Erweiterung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="2fef8-112">For example managing fleets of devices, monitoring device-to-cloud events and invoking cloud to device methods are all enabled via the IoT extension.</span></span> <span data-ttu-id="2fef8-113">Die Azure IoT-Erweiterung für die Azure CLI macht den Einsatz von experimentellen Technologien oder Vorabversionen möglich und trägt damit zu ihrer Vielseitigkeit in einer Vielzahl von Szenarien und Anwendungsfällen bei.</span><span class="sxs-lookup"><span data-stu-id="2fef8-113">The Azure IoT extension for Azure CLI unlocks the use of experimental or pre-release technology contributing to its versatility in a variety of scenarios and use cases.</span></span>

### <a name="core-reference-commands"></a><span data-ttu-id="2fef8-114">Core-Referenz – Befehle</span><span class="sxs-lookup"><span data-stu-id="2fef8-114">Core reference commands</span></span>

| <span data-ttu-id="2fef8-115">Verweis</span><span class="sxs-lookup"><span data-stu-id="2fef8-115">Reference</span></span> | <span data-ttu-id="2fef8-116">Mit Erweiterung</span><span class="sxs-lookup"><span data-stu-id="2fef8-116">Has extension</span></span> | <span data-ttu-id="2fef8-117">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="2fef8-117">Description</span></span>
|-|-|-|
| [<span data-ttu-id="2fef8-118">az iot</span><span class="sxs-lookup"><span data-stu-id="2fef8-118">az iot</span></span>](/cli/azure/iot) | <span data-ttu-id="2fef8-119">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-119">yes</span></span>  | <span data-ttu-id="2fef8-120">Alle verfügbaren Azure CLI Core-Befehle für Azure IoT</span><span class="sxs-lookup"><span data-stu-id="2fef8-120">All available Azure CLI core commands for Azure IoT.</span></span>
| [<span data-ttu-id="2fef8-121">az iot central</span><span class="sxs-lookup"><span data-stu-id="2fef8-121">az iot central</span></span>](/cli/azure/iot/central) | <span data-ttu-id="2fef8-122">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-122">yes</span></span> | <span data-ttu-id="2fef8-123">Verwalten von IoT Central-Objekten</span><span class="sxs-lookup"><span data-stu-id="2fef8-123">Manage IoT Central assets.</span></span>
| [<span data-ttu-id="2fef8-124">az iot dps</span><span class="sxs-lookup"><span data-stu-id="2fef8-124">az iot dps</span></span>](/en-us/cli/azure/iot/dps) | <span data-ttu-id="2fef8-125">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-125">yes</span></span> | <span data-ttu-id="2fef8-126">Verwalten von Device Provisioning Service in Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="2fef8-126">Manage Azure IoT Hub Device Provisioning Service.</span></span>
| [<span data-ttu-id="2fef8-127">az iot hub</span><span class="sxs-lookup"><span data-stu-id="2fef8-127">az iot hub</span></span>](/cli/azure/iot/hub) | <span data-ttu-id="2fef8-128">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-128">yes</span></span> | <span data-ttu-id="2fef8-129">Verwalten der Azure IoT Hub-Infrastruktur</span><span class="sxs-lookup"><span data-stu-id="2fef8-129">Manage Azure IoT Hub infrastructure.</span></span>
| [<span data-ttu-id="2fef8-130">az iot pnp</span><span class="sxs-lookup"><span data-stu-id="2fef8-130">az iot pnp</span></span>](/cli/azure/iot/pnp) | <span data-ttu-id="2fef8-131">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-131">yes</span></span> | <span data-ttu-id="2fef8-132">Verwalten von IoT Plug & Play-Repositorys und -Repositoryzugriffsschlüsseln</span><span class="sxs-lookup"><span data-stu-id="2fef8-132">Manage IoT Plug and Play repositories and repository access keys.</span></span>

### <a name="extension-reference-commands"></a><span data-ttu-id="2fef8-133">Erweiterungsreferenz – Befehle</span><span class="sxs-lookup"><span data-stu-id="2fef8-133">Extension reference commands</span></span>

| <span data-ttu-id="2fef8-134">Verweis</span><span class="sxs-lookup"><span data-stu-id="2fef8-134">Reference</span></span> | <span data-ttu-id="2fef8-135">Mit Core</span><span class="sxs-lookup"><span data-stu-id="2fef8-135">Has core</span></span> | <span data-ttu-id="2fef8-136">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="2fef8-136">Description</span></span>
|-|-|-|
| [<span data-ttu-id="2fef8-137">az iot</span><span class="sxs-lookup"><span data-stu-id="2fef8-137">az iot</span></span>](/cli/azure/ext/azure-iot/iot) | <span data-ttu-id="2fef8-138">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-138">yes</span></span> | <span data-ttu-id="2fef8-139">Alle verfügbaren Azure CLI-Erweiterungsbefehle für Azure IoT</span><span class="sxs-lookup"><span data-stu-id="2fef8-139">All available Azure CLI extension commands for Azure IoT.</span></span>
| [<span data-ttu-id="2fef8-140">az iot central</span><span class="sxs-lookup"><span data-stu-id="2fef8-140">az iot central</span></span>](/cli/azure/ext/azure-iot/iot/central) | <span data-ttu-id="2fef8-141">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-141">yes</span></span> | <span data-ttu-id="2fef8-142">Verwalten von Azure Central-Lösungen und -Infrastrukturen (IoT Central)</span><span class="sxs-lookup"><span data-stu-id="2fef8-142">Manage Azure Central (IoT Central) solutions & infrastructure.</span></span>
| [<span data-ttu-id="2fef8-143">az iot device</span><span class="sxs-lookup"><span data-stu-id="2fef8-143">az iot device</span></span>](/cli/azure/ext/azure-iot/iot/device) | | <span data-ttu-id="2fef8-144">Nutzen der Funktionen für Gerät-zu-Cloud- und Cloud-zu-Gerät-Messaging</span><span class="sxs-lookup"><span data-stu-id="2fef8-144">Leverage device-to-cloud and cloud-to-device messaging capabilities.</span></span>
| [<span data-ttu-id="2fef8-145">az dt</span><span class="sxs-lookup"><span data-stu-id="2fef8-145">az dt</span></span>](/cli/azure/ext/azure-iot/dt) | | <span data-ttu-id="2fef8-146">Verwalten von Azure Digital Twins-Lösungen und -Infrastrukturen</span><span class="sxs-lookup"><span data-stu-id="2fef8-146">Manage Azure Digital Twins solutions & infrastructure.</span></span>
| [<span data-ttu-id="2fef8-147">az iot dps</span><span class="sxs-lookup"><span data-stu-id="2fef8-147">az iot dps</span></span>](/cli/azure/ext/azure-iot/iot/dps) | <span data-ttu-id="2fef8-148">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-148">yes</span></span> | <span data-ttu-id="2fef8-149">Verwalten von Entitäten in Device Provisioning Service in Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="2fef8-149">Manage entities in an Azure IoT Hub Device Provisioning Service.</span></span>
| [<span data-ttu-id="2fef8-150">az iot edge</span><span class="sxs-lookup"><span data-stu-id="2fef8-150">az iot edge</span></span>](/cli/azure/ext/azure-iot/iot/edge) | | <span data-ttu-id="2fef8-151">Verwalten von IoT-Lösungen am Edge</span><span class="sxs-lookup"><span data-stu-id="2fef8-151">Manage IoT solutions on the Edge.</span></span>
| [<span data-ttu-id="2fef8-152">az iot hub</span><span class="sxs-lookup"><span data-stu-id="2fef8-152">az iot hub</span></span>](/cli/azure/ext/azure-iot/iot/hub) | <span data-ttu-id="2fef8-153">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-153">yes</span></span> | <span data-ttu-id="2fef8-154">Verwalten von Entitäten in einer Azure IoT Hub-Instanz</span><span class="sxs-lookup"><span data-stu-id="2fef8-154">Manage entities in an Azure IoT Hub.</span></span>
| [<span data-ttu-id="2fef8-155">az iot pnp</span><span class="sxs-lookup"><span data-stu-id="2fef8-155">az iot pnp</span></span>](/cli/azure/ext/azure-iot/iot/pnp) | <span data-ttu-id="2fef8-156">ja</span><span class="sxs-lookup"><span data-stu-id="2fef8-156">yes</span></span> | <span data-ttu-id="2fef8-157">Verwalten der Entitäten eines IoT Plug & Play-Modellrepositorys</span><span class="sxs-lookup"><span data-stu-id="2fef8-157">Manage entities of an IoT Plug and Play model repository.</span></span>

### <a name="additional-cli-commands-for-azure-services-used-by-iot"></a><span data-ttu-id="2fef8-158">Weitere CLI-Befehle für von IoT verwendete Azure-Dienste</span><span class="sxs-lookup"><span data-stu-id="2fef8-158">Additional CLI commands for Azure services used by IoT</span></span>

| <span data-ttu-id="2fef8-159">Verweis</span><span class="sxs-lookup"><span data-stu-id="2fef8-159">Reference</span></span> | <span data-ttu-id="2fef8-160">type</span><span class="sxs-lookup"><span data-stu-id="2fef8-160">Type</span></span> | <span data-ttu-id="2fef8-161">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="2fef8-161">Description</span></span>
|-|-|-|
| [<span data-ttu-id="2fef8-162">az maps</span><span class="sxs-lookup"><span data-stu-id="2fef8-162">az maps</span></span>](/cli/azure/maps) | <span data-ttu-id="2fef8-163">core</span><span class="sxs-lookup"><span data-stu-id="2fef8-163">core</span></span> | <span data-ttu-id="2fef8-164">Verwalten von Azure Maps</span><span class="sxs-lookup"><span data-stu-id="2fef8-164">Manage Azure Maps.</span></span>
| [<span data-ttu-id="2fef8-165">az timeseriesinsights</span><span class="sxs-lookup"><span data-stu-id="2fef8-165">az timeseriesinsights</span></span>](/cli/azure/ext/timeseriesinsights/timeseriesinsights) | <span data-ttu-id="2fef8-166">Erweiterung</span><span class="sxs-lookup"><span data-stu-id="2fef8-166">extension</span></span> | <span data-ttu-id="2fef8-167">Verwalten von Azure Time Series Insights</span><span class="sxs-lookup"><span data-stu-id="2fef8-167">Manage Azure Time Series Insights.</span></span>

## <a name="popular-iot-articles-using-the-azure-cli"></a><span data-ttu-id="2fef8-168">Beliebte IoT-Artikel zur Azure CLI</span><span class="sxs-lookup"><span data-stu-id="2fef8-168">Popular IoT articles using the Azure CLI</span></span>

- [<span data-ttu-id="2fef8-169">Erstellen eines IoT Hubs mit der Azure-Befehlszeilenschnittstelle</span><span class="sxs-lookup"><span data-stu-id="2fef8-169">Create an IoT hub</span></span>](/azure/iot-hub/iot-hub-create-using-cli)
- [<span data-ttu-id="2fef8-170">Verwalten von IoT Central über Azure CLI</span><span class="sxs-lookup"><span data-stu-id="2fef8-170">Manage IoT Central</span></span>](/azure/iot-central/core/howto-manage-iot-central-from-cli)
- [<span data-ttu-id="2fef8-171">CLI-basierte Gerätetutorials mit Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="2fef8-171">CLI driven device tutorials using Azure RTOS</span></span>](/azure/rtos/getting-started?branch=master)
- [<span data-ttu-id="2fef8-172">Verwenden der IoT-Erweiterung für Azure CLI für die Verwaltung von Azure IoT Hub-Geräten</span><span class="sxs-lookup"><span data-stu-id="2fef8-172">Use the IoT extension for Azure IoT Hub device management</span></span>](/azure/iot-hub/iot-hub-device-management-iot-extension-azure-cli-2-0)
- [<span data-ttu-id="2fef8-173">Bedarfsgerechtes Bereitstellen und Überwachen von IoT Edge-Modulen mithilfe der Azure CLI</span><span class="sxs-lookup"><span data-stu-id="2fef8-173">Deploy and monitor IoT Edge modules at scale with the Azure CLI extension for IoT</span></span>](/azure/iot-edge/how-to-deploy-cli-at-scale)
- [<span data-ttu-id="2fef8-174">Schnellstart: Senden von Telemetriedaten von einem Gerät an einen IoT-Hub und Durchführen der Überwachung per Azure CLI</span><span class="sxs-lookup"><span data-stu-id="2fef8-174">Send Telemetry to a device and monitor it with the Azure CLI extension for IoT</span></span>](/azure/iot-hub/quickstart-send-telemetry-cli)
- [<span data-ttu-id="2fef8-175">Tutorial: Konfigurieren des IoT Hub-Nachrichtenroutings mithilfe der Azure-Befehlszeilenschnittstelle</span><span class="sxs-lookup"><span data-stu-id="2fef8-175">Use the Azure CLI to configure IoT Hub message routing</span></span>](/azure/iot-hub/tutorial-routing-config-message-routing-cli)
- [<span data-ttu-id="2fef8-176">Installieren und Verwenden der Azure IoT-Erweiterung für die Azure CLI</span><span class="sxs-lookup"><span data-stu-id="2fef8-176">Manage interfaces in a Plug and Play model repository</span></span>](/azure/iot-pnp/howto-install-pnp-cli#manage-interfaces-in-a-model-repository)

## <a name="azure-cli-reference-examples"></a><span data-ttu-id="2fef8-177">Azure CLI-Referenzbeispiele</span><span class="sxs-lookup"><span data-stu-id="2fef8-177">Azure CLI reference examples</span></span>

<span data-ttu-id="2fef8-178">Es stehen Beispiele für jede Azure CLI-Referenz bereit.</span><span class="sxs-lookup"><span data-stu-id="2fef8-178">Examples are provided with every Azure CLI reference.</span></span> <span data-ttu-id="2fef8-179">Sie können diese Aufgaben zwar auch über das Azure-Portal ausführen, doch ist zur Verwendung der Azure CLI nur eine einzige Befehlszeile erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2fef8-179">Although you can also complete these tasks through the Azure portal, using the Azure CLI requires a single command line.</span></span>  <span data-ttu-id="2fef8-180">Nachfolgend sehen Sie einige Codeblöcke, die Ihnen eine Vorstellung davon geben, wie einfach die Azure CLI zu verwenden ist.</span><span class="sxs-lookup"><span data-stu-id="2fef8-180">Here are a few code blocks to give you an idea of how easy it is to use the Azure CLI.</span></span>

<span data-ttu-id="2fef8-181">Zum Arbeiten mit Azure IoT benötigen Sie zunächst eine Ressourcengruppe.</span><span class="sxs-lookup"><span data-stu-id="2fef8-181">To work with Azure IoT, you'll first need a resource group.</span></span>  <span data-ttu-id="2fef8-182">Azure-Ressourcengruppen können auf einfache Weise mit der Azure CLI erstellt und verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="2fef8-182">Azure resource groups are simple to create and manage with the Azure CLI.</span></span>  

```azurecli
#create a resource group
az group create -location westus -name MyResourceGroup
```

```azurecli
#get a list of resource groups for a subscription
az group list --subscription MySubscription --output table
```

<span data-ttu-id="2fef8-183">Genauso einfach ist die Erstellung einer Azure IoT Hub-Instanz in der Region „westus“ im Tarif „Standard“.</span><span class="sxs-lookup"><span data-stu-id="2fef8-183">It is as straightforward to create an Azure IoT Hub in the '''westus''' region in the standard pricing tier.</span></span>

```azurecli
#create an Azure IoT hub
az iot hub create --resource-group MyResourceGroup --name MyIotHub --location westus
```

## <a name="see-also"></a><span data-ttu-id="2fef8-184">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2fef8-184">See also</span></span>

- <span data-ttu-id="2fef8-185">Unter [Erste Schritte mit der Azure CLI](/cli/azure/get-started-with-azure-cli) erhalten Sie Informationen zur Installation und Anmeldung.</span><span class="sxs-lookup"><span data-stu-id="2fef8-185">[Get started with Azure CLI](/cli/azure/get-started-with-azure-cli) to learn about installation and sign in.</span></span>

- <span data-ttu-id="2fef8-186">Entdecken Sie weitere [veröffentlichte Referenzen](/cli/azure/reference-index) und Referenzen zu [Erweiterungen](/cli/azure/azure-cli-extensions-list) in der Azure CLI-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="2fef8-186">Discover additional [released](/cli/azure/reference-index) and [extension](/cli/azure/azure-cli-extensions-list) references in the Azure CLI documentation.</span></span>

- <span data-ttu-id="2fef8-187">Weitere Informationen zu Erweiterungen finden Sie unter [Verwenden von Erweiterungen mit der Azure CLI](/cli/azure/azure-cli-extensions-overview).</span><span class="sxs-lookup"><span data-stu-id="2fef8-187">Find out more about extension references in [Use extensions with Azure CLI](/cli/azure/azure-cli-extensions-overview).</span></span>