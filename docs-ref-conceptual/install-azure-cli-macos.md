---
title: "Installieren der Azure-Befehlszeilenschnittstelle für macOS"
description: Installieren der Azure CLI 2.0 unter macOS
keywords: Azure CLI,Azure CLI installieren,Azure macOS, Azure installieren macOS
author: sptramer
ms.author: sttramer
manager: routlaw
ms.date: 01/29/18
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ms.openlocfilehash: 36fd2604677db0b7f820ee11884bf790fb1d75cb
ms.sourcegitcommit: 8606f36963e8daa6448d637393d1e4ef2c9859a0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="install-azure-cli-20-on-macos"></a>Installieren der Azure CLI 2.0 unter macOS

Bei Verwendung der macOS-Plattform können Sie die Azure CLI über den [Homebrew-Paket-Manager](http://brew.sh) installieren. Mit Homebrew können Sie Ihre CLI-Installation ganz einfach auf dem neuesten Stand halten. Das CLI-Paket wurde ab der macOS-Version 10.9 getestet.

## <a name="install"></a>Installieren

Homebrew ist die einfachste Möglichkeit zum Verwalten der CLI-Installation. Homebrew bietet praktische Optionen zum Installieren, Aktualisieren und Deinstallieren. Falls Homebrew auf Ihrem System nicht verfügbar ist, [installieren Sie Homebrew](https://docs.brew.sh/Installation.html), bevor Sie fortfahren.

Sie können die CLI installieren, indem Sie die Homebrew-Repositoryinformationen aktualisieren und dann den Befehl `install` ausführen:

```bash
brew update && brew install azure-cli
```

Sie können dann die Azure CLI mit dem Befehl `az` ausführen.

## <a name="troubleshooting"></a>Problembehandlung

In diesem Abschnitt finden Sie einige allgemeine Fehler, die zu Problemen bei der Homebrew-basierten CLI-Installation führen können. Sollte Ihr Problem hier nicht aufgeführt sein, [melden Sie es über GitHub](https://github.com/Azure/azure-cli/issues).

### <a name="unable-to-find-python-or-installed-packages"></a>Python und installierte Pakete können nicht gefunden werden.

Sollten Python oder installierte Pakete bei der Installation nicht gefunden werden, weichen die Versionen unter Umständen geringfügig voneinander ab, oder es liegt ein anderes Problem vor, das während der Homebrew-Installation aufgetreten ist. Da die CLI keine virtuelle Python-Umgebung verwendet, muss sie die korrekte Python-Version finden können. Zur Behebung dieser Probleme können Sie ggf. die Python-Installation neu verknüpfen.

```bash
brew link --overwrite python3
```

### <a name="cli-version-1x-is-installed"></a>CLI-Version 1.x wird installiert.

Die Installation einer veralteten Version kann auf einen veralteten Homebrew-Cache zurückzuführen sein. Gehen Sie gemäß der [Aktualisierungsanleitung](#Update) vor.

## <a name="update"></a>Aktualisieren

Die CLI wird regelmäßig mit Fehlerbehebungen, Verbesserungen, neuen Features und Vorschaufunktionen aktualisiert. Ein neues Release ist ungefähr alle zwei Wochen verfügbar. Aktualisieren Sie Ihre lokalen Repositoryinformationen, und upgraden Sie anschließend das Paket `azure-cli`.

```bash
brew update && brew upgrade azure-cli
```

## <a name="uninstall"></a>Deinstallieren

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

Verwenden Sie Homebrew, um das Paket `azure-cli` zu deinstallieren.

```bash
brew uninstall azure-cli
```
