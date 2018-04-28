---
title: Installieren der Azure CLI 2.0 unter Linux mit zypper
description: Installieren der Azure CLI 2.0 mit zypper
author: sptramer
ms.author: sttramer
manager: carmonm
ms.date: 01/29/2018
ms.topic: conceptual
ms.prod: azure
ms.technology: azure-cli
ms.devlang: azure-cli
ms.openlocfilehash: 3a1e82dc666cd034d0cc4320a8b99dd6a9a14b6d
ms.sourcegitcommit: ae72b6c8916aeb372a92188090529037e63930ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2018
---
# <a name="install-azure-cli-20-with-zypper"></a><span data-ttu-id="7e2fa-103">Installieren der Azure CLI 2.0 mit zypper</span><span class="sxs-lookup"><span data-stu-id="7e2fa-103">Install Azure CLI 2.0 with zypper</span></span>

<span data-ttu-id="7e2fa-104">Wenn Sie eine Distribution mit `zypper` verwenden (etwa openSUSE oder SLES), steht ein Paket für die Azure CLI zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="7e2fa-104">If you are running a distribution that comes with `zypper`, such as openSUSE or SLES, there is a package available for the Azure CLI.</span></span> <span data-ttu-id="7e2fa-105">Dieses Paket wurde mit openSUSE 42.2 und SLES 12 SP 2 getestet.</span><span class="sxs-lookup"><span data-stu-id="7e2fa-105">This package has been tested with openSUSE 42.2 and SLES 12 SP 2.</span></span>

[!INCLUDE [linux-install-requirements.md](includes/linux-install-requirements.md)]

## <a name="install"></a><span data-ttu-id="7e2fa-106">Installieren</span><span class="sxs-lookup"><span data-stu-id="7e2fa-106">Install</span></span>

1. <span data-ttu-id="7e2fa-107">Installieren Sie `curl`:</span><span class="sxs-lookup"><span data-stu-id="7e2fa-107">Install `curl`:</span></span>

   ```bash
   sudo zypper refresh
   sudo zypper install -y curl
   ```

2. <span data-ttu-id="7e2fa-108">Importieren Sie den Microsoft-Repositoryschlüssel:</span><span class="sxs-lookup"><span data-stu-id="7e2fa-108">Import the Microsoft repository key:</span></span>

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. <span data-ttu-id="7e2fa-109">Erstellen Sie lokale `azure-cli`-Repositoryinformationen:</span><span class="sxs-lookup"><span data-stu-id="7e2fa-109">Create local `azure-cli` repository information:</span></span>

   ```bash
   sudo sh -c 'echo -e "[azure-cli]\nname=Azure CLI\nbaseurl=https://packages.microsoft.com/yumrepos/azure-cli\nenabled=1\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/azure-cli.repo'
   ```

4. <span data-ttu-id="7e2fa-110">Aktualisieren Sie den `zypper`-Paketindex, und führen Sie die Installation durch:</span><span class="sxs-lookup"><span data-stu-id="7e2fa-110">Update the `zypper` package index and install:</span></span>

   ```bash
   sudo zypper refresh
   sudo zypper install -y azure-cli
   ```

<span data-ttu-id="7e2fa-111">Sie können dann die Azure CLI mit dem Befehl `az` ausführen.</span><span class="sxs-lookup"><span data-stu-id="7e2fa-111">You can then run the Azure CLI with the `az` command.</span></span> <span data-ttu-id="7e2fa-112">Führen Sie den Befehl `az login` aus, um sich anzumelden.</span><span class="sxs-lookup"><span data-stu-id="7e2fa-112">To log in, run the `az login` command.</span></span>

```azurecli
az login
```

<span data-ttu-id="7e2fa-113">Weitere Informationen zu verschiedenen Anmeldemethoden finden Sie unter [Anmelden mit Azure CLI 2.0](authenticate-azure-cli.md).</span><span class="sxs-lookup"><span data-stu-id="7e2fa-113">To learn more about different login methods, see [Log in with Azure CLI 2.0](authenticate-azure-cli.md).</span></span>

## <a name="update"></a><span data-ttu-id="7e2fa-114">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="7e2fa-114">Update</span></span>

<span data-ttu-id="7e2fa-115">Sie können das Paket mit dem Befehl `zypper update` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="7e2fa-115">You can update the package with the `zypper update` command.</span></span>

```bash
sudo zypper refresh
sudo zypper update azure-cli
```

## <a name="uninstall"></a><span data-ttu-id="7e2fa-116">Deinstallieren</span><span class="sxs-lookup"><span data-stu-id="7e2fa-116">Uninstall</span></span>

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

1. <span data-ttu-id="7e2fa-117">Entfernen Sie das Paket aus Ihrem System.</span><span class="sxs-lookup"><span data-stu-id="7e2fa-117">Remove the package from your system.</span></span>

    ```bash
    sudo zypper remove -y azure-cli
    ```

2. <span data-ttu-id="7e2fa-118">Entfernen Sie die Repositoryinformationen, wenn Sie nicht planen, die CLI neu zu installieren.</span><span class="sxs-lookup"><span data-stu-id="7e2fa-118">If you do not plan to reinstall the CLI, remove the repository information.</span></span>

  ```bash
  sudo rm /etc/zypp/repos.d/azure-cli.repo
  ```

3. <span data-ttu-id="7e2fa-119">Entfernen Sie auch den Microsoft GPG-Signaturschlüssel, falls Sie die Repositoryinformationen entfernt haben.</span><span class="sxs-lookup"><span data-stu-id="7e2fa-119">If you removed the repository information, also remove the Microsoft GPG signature key.</span></span>

  ```bash
  MSFT_KEY=`rpm -qa gpg-pubkey /* --qf "%{version}-%{release} %{summary}\n" | grep Microsoft | awk '{print $1}'`
  sudo rpm -e --allmatches gpg-pubkey-$MSFT_KEY
  ```

