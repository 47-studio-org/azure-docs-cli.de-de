---
title: "Ausgabeformate für Azure CLI 2.0"
description: "Verwenden Sie „--output“, um die Ausgabe von Azure CLI 2.0-Befehlen in Tabellen, Listen oder JSON-Code zu formatieren."
keywords: Azure CLI 2.0, Ausgabe, Formatieren, Tabelle, Liste, JSON, Linux, MacOS, Windows, OS X
author: rloutlaw
ms.author: routlaw
manager: douge
ms.date: 02/27/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ms.assetid: 74bdb727-481d-45f7-a44e-15d18dc55483
ms.openlocfilehash: de37b1ad6aa55c9ac73b5b6b89d9507c86cc1245
ms.sourcegitcommit: bcf93ad8ed8802072249cd8187cd4420da89b4c6
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="output-formats-for-azure-cli-20-commands"></a><span data-ttu-id="8f811-104">Ausgabeformate für Azure CLI 2.0-Befehle</span><span class="sxs-lookup"><span data-stu-id="8f811-104">Output formats for Azure CLI 2.0 commands</span></span>

<span data-ttu-id="8f811-105">Für Azure CLI 2.0 wird JSON als Standardoption für die Ausgabe verwendet, aber Sie haben verschiedene Möglichkeiten, die Ausgabe von Befehlen zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="8f811-105">Azure CLI 2.0 uses json as its default output option, but offers various ways for you to format the output of any command.</span></span>  <span data-ttu-id="8f811-106">Verwenden Sie den Parameter `--output` (oder `--out` oder `-o`), um die Ausgabe des Befehls basierend auf einem der Ausgabetypen zu formatieren, die in der folgenden Tabelle angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="8f811-106">Use the `--output` (or `--out` or `-o`) parameter to format the output of the command into one of the output types noted in the following table.</span></span> 

<span data-ttu-id="8f811-107">--output</span><span class="sxs-lookup"><span data-stu-id="8f811-107">--output</span></span> | <span data-ttu-id="8f811-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8f811-108">Description</span></span>
---------|-------------------------------
`json`   | <span data-ttu-id="8f811-109">JSON-Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="8f811-109">json string.</span></span> <span data-ttu-id="8f811-110">`json` ist die Standardeinstellung.</span><span class="sxs-lookup"><span data-stu-id="8f811-110">`json` is the default.</span></span>
`jsonc`  | <span data-ttu-id="8f811-111">Farbige JSON-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8f811-111">colorized json string.</span></span>
`table`  | <span data-ttu-id="8f811-112">Tabelle mit Spaltenüberschriften</span><span class="sxs-lookup"><span data-stu-id="8f811-112">table with column headings.</span></span>
`tsv`    | <span data-ttu-id="8f811-113">Per Tabulator getrennte Werte</span><span class="sxs-lookup"><span data-stu-id="8f811-113">tab-separated values.</span></span>

## <a name="using-the-json-option"></a><span data-ttu-id="8f811-114">Verwenden der Option „json“</span><span class="sxs-lookup"><span data-stu-id="8f811-114">Using the json option</span></span>

<span data-ttu-id="8f811-115">Im folgenden Beispiel wird die Liste mit den virtuellen Computern Ihrer Abonnements im JSON-Standardformat angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8f811-115">The following example displays the list of virtual machines in your subscriptions in the default json format.</span></span>

```azurecli
az vm list --output json
```

<span data-ttu-id="8f811-116">Die Ergebnisse werden wie folgt angezeigt (aus Platzgründen nur eine Teilausgabe).</span><span class="sxs-lookup"><span data-stu-id="8f811-116">The results are in this form (only showing partial output for sake of brevity).</span></span>

```json
[
  {
    "availabilitySet": null,
    "diagnosticsProfile": null,
    "hardwareProfile": {
      "vmSize": "Standard_DS1"
    },
    "id": "/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/DemoVM010",
    "instanceView": null,
    "licenseType": null,
    "location": "westus",
    "name": "DemoVM010",
    "networkProfile": {
      "networkInterfaces": [
        {
          "id": "/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/demorg1/providers/Microsoft.Network/networkInterfaces/DemoVM010VMNic",
          "primary": null,
          "resourceGroup": "demorg1"
        }
      ]
    },
          ...
          ...
          ...   
]
```
 
## <a name="using-the-table-option"></a><span data-ttu-id="8f811-117">Verwenden der Option „table“</span><span class="sxs-lookup"><span data-stu-id="8f811-117">Using the table option</span></span>

<span data-ttu-id="8f811-118">Mit der Option „table“ wird eine leicht lesbare Ausgabe bereitgestellt. Beachten Sie aber, dass geschachtelte Objekte beim einfachen Befehl `--output table` nicht in die Ausgabe einbezogen werden (im Gegensatz zum obigen json-Beispiel).</span><span class="sxs-lookup"><span data-stu-id="8f811-118">The table option provides an easy to read set of output, but note that nested objects are not included in the output with the simple `--output table`, unlike the preceding .json example.</span></span>  <span data-ttu-id="8f811-119">Bei Verwendung des gleichen Beispiels mit dem Ausgabeformat „table“ wird eine Liste mit den ausgewählten häufigsten Eigenschaftswerten bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8f811-119">Using the same example with 'table' output format provides a curated list of most common property values.</span></span>

```azurecli
az vm list --out table
```

```
Name         ResourceGroup    Location
-----------  ---------------  ----------
DemoVM010    DEMORG1          westus
demovm212    DEMORG1          westus
demovm213    DEMORG1          westus
KBDemo001VM  RGDEMO001        westus
KBDemo020    RGDEMO001        westus
```

<span data-ttu-id="8f811-120">Sie können den Parameter `--query` verwenden, um die Eigenschaften und Spalten anzupassen, die Sie in der Listenausgabe anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="8f811-120">You can use the `--query` parameter to customize the properties and columns you want to show in the list output.</span></span> <span data-ttu-id="8f811-121">Im folgenden Beispiel wird veranschaulicht, wie Sie im Befehl `list` nur den VM-Namen und den Ressourcengruppennamen auswählen.</span><span class="sxs-lookup"><span data-stu-id="8f811-121">The following example shows how to select just the VM Name and the Resource Group Name in the `list` command.</span></span>

```azurecli
az vm list --query "[].{ resource: resourceGroup, name: name }" -o table
```

```
Resource    Name
----------  -----------
DEMORG1     DemoVM010
DEMORG1     demovm212
DEMORG1     demovm213
RGDEMO001   KBDemo001VM
RGDEMO001   KBDemo020
```

## <a name="using-the-tsv-option"></a><span data-ttu-id="8f811-122">Verwenden der Option „tsv“</span><span class="sxs-lookup"><span data-stu-id="8f811-122">Using the tsv option</span></span>

<span data-ttu-id="8f811-123">Beim Ausgabeformat „tsv“ wird eine einfache textbasierte und per Tabulator getrennte Ausgabe ohne Überschriften und Bindestriche zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8f811-123">'tsv' output format returns a simple text-based and tab-separated output with no headings and dashes.</span></span> <span data-ttu-id="8f811-124">Mit diesem Format ist es leicht, die Ausgabe in anderen Befehlen und Tools zu nutzen, in denen der Text verarbeitet werden muss.</span><span class="sxs-lookup"><span data-stu-id="8f811-124">This format makes it easy to consume the output into other commands and tools that need to process the text in some form.</span></span> <span data-ttu-id="8f811-125">Wenn das obige Beispiel mit der Option `tsv` verwendet wird, wird das Ergebnis mit Tabulatortrennung ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="8f811-125">Using the preceding example with the `tsv` option outputs the tab-separated result.</span></span>

```azurecli
az vm list --out tsv
```

```
None    None        /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/DemoVM010    None    None    westus    DemoVM010            None    Succeeded    DEMORG1    None            Microsoft.Compute/virtualMachines    cbd56d9b-9340-44bc-a722-25f15b578444
None    None        /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/demovm212    None    None    westus    demovm212            None    Succeeded    DEMORG1    None            Microsoft.Compute/virtualMachines    4bdac85d-c2f7-410f-9907-ca7921d930b4
None    None        /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/DEMORG1/providers/Microsoft.Compute/virtualMachines/demovm213    None    None    westus    demovm213            None    Succeeded    DEMORG1    None            Microsoft.Compute/virtualMachines    2131c664-221a-4b7f-9653-f6d542fbfa34
None    None        /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/RGDEMO001/providers/Microsoft.Compute/virtualMachines/KBDemo001VM    None    None    westus    KBDemo001VM            None    Succeeded    RGDEMO001    None            Microsoft.Compute/virtualMachines    14e74761-c17e-4530-a7be-9e4ff06ea74b
None    None        /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/RGDEMO001/providers/Microsoft.Compute/virtualMachines/KBDemo02None    None    westus    KBDemo020            None    Succeeded    RGDEMO001    None            Microsoft.Compute/virtualMachinesed36baa9-9b80-48a8-b4a9-854c7a858ece
```

<span data-ttu-id="8f811-126">Im nächsten Beispiel wird veranschaulicht, wie Sie die Ausgabe von `tsv` per Pipe-Zeichen an Befehle wie `grep` und `cut` anfügen können, um bestimmte Werte der Ausgabe von `list` weiter zu analysieren.</span><span class="sxs-lookup"><span data-stu-id="8f811-126">The next example shows how the `tsv` output can be piped to commands like `grep` and `cut` to further parse specific values out of the `list` output.</span></span> <span data-ttu-id="8f811-127">Mit dem Befehl `grep` werden nur Elemente ausgewählt, die den Text „RGD“ enthalten, und anschließend wird mit dem Befehl `cut` nur der Wert des achten Felds (getrennt durch Tabulatoren) für die Anzeige in der Ausgabe ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="8f811-127">The `grep` command selects only items that have text "RGD" in them and then the `cut` command selects only the eighth field (separated by tabs) value to show in the output.</span></span>

```azurecli
az vm list --out tsv | grep RGD | cut -f8
```

```
KBDemo001VM
KBDemo020
```

## <a name="setting-the-default-output-format"></a><span data-ttu-id="8f811-128">Festlegen des Standardformats für die Ausgabe</span><span class="sxs-lookup"><span data-stu-id="8f811-128">Setting the default output format</span></span>

<span data-ttu-id="8f811-129">Sie können den Befehl `az configure` verwenden, um Ihre Umgebung einzurichten oder die bevorzugten Einstellungen festzulegen, z.B. Standardeinstellungen für Ausgabeformate.</span><span class="sxs-lookup"><span data-stu-id="8f811-129">You can use the `az configure` command to set up your environment or establish preferences such as default settings for output formats.</span></span> <span data-ttu-id="8f811-130">Die einfachste Standardeinstellung für das Ausgabeformat zur normalen Nutzung ist das Format „table“. Wählen Sie die Option **3**, wenn Sie zum Angeben des Ausgabeformats aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="8f811-130">For common use, the easiest output format default is the "table" format - select **3** when prompted for output format choices.</span></span> 

```
What default output format would you like?
 [1] json - JSON formatted output that most closely matches API responses
 [2] jsonc - Colored JSON formatted output that most closely matches API responses
 [3] table - Human-readable output format
 [4] tsv - Tab and Newline delimited, great for GREP, AWK, etc.
Please enter a choice [3]: 
```