---
title: Aliaserweiterung der Azure CLI 2.0
description: Verwenden der Aliaserweiterung der Azure CLI 2.0
author: sptramer
ms.author: sttramer
manager: carmonm
ms.date: 03/14/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ms.openlocfilehash: e457d78b1009fe573554df36db18f525516e0b4a
ms.sourcegitcommit: 335c11e6c34f7907e61a43507745ba84ed4e7469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2018
---
# <a name="the-azure-cli-20-alias-extension"></a>Aliaserweiterung der Azure CLI 2.0

Dank der Aliaserweiterung können Benutzer mithilfe von vorhandenen Befehlen benutzerdefinierte Befehle für die Azure CLI definieren. Mit Aliasen können Sie durch die Bereitstellung von Verknüpfungen und die Verwendung von positionellen Argumenten prägnante, einfache Workflows erstellen. Aliase werden von der Jinja2-Vorlagenengine unterstützt und bieten daher sogar erweiterte Argumentverarbeitung.

> [!NOTE]
> Die Aliaserweiterung ist als öffentliche Vorschauversion verfügbar. Die Funktionen und das Konfigurationsdateiformat können sich ändern.

## <a name="install-the-alias-extension"></a>Installieren der Aliaserweiterung

Damit Sie die Aliaserweiterung verwenden können, ist mindestens Version **2.0.28** der Azure CLI erforderlich. Führen Sie zum Überprüfen der CLI-Version `az --version` aus. Falls Sie die Installation aktualisieren müssen, befolgen Sie die Anweisungen unter [Installieren von Azure CLI 2.0](./install-azure-cli.md).

Installieren Sie die Erweiterung mit dem Befehl [az extension add](/cli/azure/extension#az-extension-add).

```azurecli
az extension add --name alias
```

Überprüfen Sie die Installation der Erweiterung mithilfe von [az extension list](/cli/azure/extension#az-extension-list). Wenn die Aliaserweiterung ordnungsgemäß installiert wurde, ist sie in der Befehlsausgabe aufgeführt.

```azurecli
az extension list --output table
```

```output
ExtensionType    Name                       Version
---------------  -------------------------  ---------
whl              alias                      0.2.0
```

## <a name="keep-the-extension-up-to-date"></a>Sicherstellen, dass die Erweiterung immer auf dem neuesten Stand ist

Die Aliaserweiterung befindet sich in der aktiven Entwicklung, und es werden regelmäßig neue Versionen veröffentlicht. Beim Aktualisieren der CLI werden neue Versionen nicht automatisch installiert. Installieren Sie die Updates für die Erweiterung mithilfe von [az extension update](/cli/azure/extension#az-extension-update).

```azurecli
az extension update --name alias
```

## <a name="alias-commands-file-format"></a>Dateiformat für Aliasbefehle

Aliasbefehlsdefinitionen werden in eine Konfigurationsdatei unter `$AZURE_USER_CONFIG/alias` geschrieben. `AZURE_USER_CONFIG` hat standardmäßig den Wert `$HOME/.azure` (macOS und Linux) bzw. `%USERPROFILE%\.azure` (Windows). Die Aliaskonfigurationsdatei wird im INI-Konfigurationsdateiformat geschrieben. Das allgemeine Format der Aliasbefehle ist wie folgt:

```
[command_name]
command = invoked_commands
```

Nehmen Sie `az` nicht als Teil des Befehls auf.

## <a name="create-simple-alias-commands"></a>Erstellen einfacher Aliasbefehle

Zum einen werden Aliase zum Kürzen vorhandener Befehlsgruppen oder Befehlsnamen verwendet. Beispielsweise können Sie die Befehlsgruppe `group` auf `rg` und den Befehl `list` auf `ls` verkürzen.

```
[rg]
command = group

[ls]
command = list
```

Diese neu definierten Aliase können nun anstelle ihrer Definition verwendet werden.

```azurecli
az rg list
az rg ls
az vm ls
```

Aliase können auch als Verknüpfungen für vollständige Befehle fungieren. Im nächsten Beispiel werden verfügbare Ressourcengruppen und ihre Speicherorte in der Tabellenausgabe aufgeführt:

```
[ls-groups]
command = group list --query '[].{Name:name, Location:location}' --output table
```

`ls-groups` kann nun wie jeder andere CLI-Befehl ausgeführt werden.

```azurecli
az ls-groups
```

## <a name="create-an-alias-command-with-arguments"></a>Erstellen eines Aliasbefehls mit Argumenten

Sie können positionelle Argumente auch zu einem Aliasbefehl hinzufügen, indem Sie sie als `{{ arg_name }}` in den Aliasnamen aufnehmen. Das Leerzeichen in den Klammern ist erforderlich.

```
[alias_name {{ arg1 }} {{ arg2 }} ...]
command = invoke_including_args
```

Das nächste Beispiel zeigt, wie Sie mithilfe von positionellen Argumenten die öffentliche IP-Adresse für einen virtuellen Computer abrufen.

```
[get-vm-ip {{ resourceGroup }} {{ vmName }}]
command = vm list-ip-addresses --resource-group {{ resourceGroup }} --name {{ vmName }} --query [0].virtualMachine.network.publicIpAddresses[0].ipAddress
```

Beim Ausführen dieses Befehls übergeben Sie Werte an die positionellen Argumente.

```azurecli
az get-vm-ip MyResourceGroup MyVM
```

Sie können in von Aliasen aufgerufenen Befehlen auch Umgebungsvariablen verwenden, die zur Laufzeit ausgewertet werden. Im nächsten Beispiel wird der Alias `create-rg` hinzugefügt, der eine Ressourcengruppe in `eastus` erstellt und ein `owner`-Tag hinzufügt. Diesem Tag wird der Wert der lokalen Umgebungsvariablen `USER` zugewiesen.

```
[create-rg {{ groupName }}]
command = group create --name {{ groupName }} --location eastus --tags owner=$USER
```

## <a name="process-arguments-using-jinja2-templates"></a>Verarbeiten von Argumenten mithilfe von Jinja2-Vorlagen

Die Argumentersetzung in der Aliaserweiterung wird von [Jinja2](http://jinja.pocoo.org/docs/2.10/) durchgeführt. Somit haben Sie Vollzugriff auf die Funktionen der Jinja2-Vorlagenengine. Vorlagen ermöglichen die Ausführung von Aktionen wie Datenextraktion und -ersetzung für Zeichenfolgen.

Mit Jinja2-Vorlagen können Sie Aliase schreiben, die andere Argumenttypen akzeptieren als der zugrunde liegende Befehl. Beispielsweise können Sie einen Alias erstellen, der eine Speicher-URL übernimmt. Anschließend wird diese URL analysiert, um den Konto- und Containernamen an den Speicherbefehl zu übergeben.

```
[storage-ls {{ url }}]
command = storage blob list --account-name {{ url.replace('https://', '').split('.')[0] }} --container-name {{ url.replace('https://', '').split('/')[1] }}
```

Informationen zur Jinja2-Vorlagenengine finden Sie in der [Jinja2-Dokumentation](http://jinja.pocoo.org/docs/2.10/templates/).

## <a name="uninstall-the-alias-extension"></a>Deinstallieren der Aliaserweiterung

Verwenden Sie zum Deinstallieren der Erweiterung den Befehl [az extension remove](/cli/azure/extension#az-extension-remove).

```azurecli
az extension remove --name alias
```

Falls Sie die Erweiterung aufgrund eines Fehlers oder eines anderen Problems deinstalliert haben, melden Sie das Problem über [GitHub](https://github.com/Azure/azure-cli-extensions/issues), damit wir eine Lösung bereitstellen können.
