---
title: Anmelden mit Azure CLI 2.0
description: Melden Sie sich mit Azure 2.0 CLI unter Linux, MacOS oder Windows an.
keywords: Azure CLI 2.0, Linux, MacOS, Windows, OS X, Ubuntu, Debian, CentOS, RHEL, SUSE, CoreOS, Docker, Windows, Python, PIP
author: rloutlaw
ms.author: routlaw
manager: douge
ms.date: 02/27/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ms.assetid: 65becd3a-9d69-4415-8a30-777d13a0e7aa
ms.openlocfilehash: fea893ebd55811527e0e92375ffc081a52cdbb57
ms.sourcegitcommit: bcf93ad8ed8802072249cd8187cd4420da89b4c6
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="log-in-with-azure-cli-20"></a><span data-ttu-id="68984-104">Anmelden mit Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="68984-104">Log in with Azure CLI 2.0</span></span>

<span data-ttu-id="68984-105">Es gibt mehrere Möglichkeiten, sich mit der Azure-CLI anzumelden und zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="68984-105">There are several ways to log in and authenticate with the Azure CLI.</span></span> <span data-ttu-id="68984-106">Der einfachste erste Ansatz ist die interaktive Anmeldung per Browser oder über die Befehlszeile.</span><span class="sxs-lookup"><span data-stu-id="68984-106">The simplest way to get started is to log in interactively through your browser, or to log in at the command line.</span></span> <span data-ttu-id="68984-107">Wir empfehlen die Verwendung von Dienstprinzipalen. Dies ermöglicht die Erstellung nicht interaktiver Konten für die Ressourcenbearbeitung.</span><span class="sxs-lookup"><span data-stu-id="68984-107">Our recommended approach is to use service principals, which provide a way for you to create non-interactive accounts that you can use to manipulate resources.</span></span> <span data-ttu-id="68984-108">Indem Sie einem Dienstprinzipal nur die erforderlichen Mindestberechtigungen erteilen, können Sie Ihre Automatisierungsskripts noch sicherer machen.</span><span class="sxs-lookup"><span data-stu-id="68984-108">By granting just the appropriate permissions needed to a service principal, you can ensure your automation scripts are even more secure.</span></span>

<span data-ttu-id="68984-109">Befehle, die Sie mit der CLI ausführen, werden für Ihr Standardabonnement ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="68984-109">Commands that you run with the CLI are run against your default subscription.</span></span>  <span data-ttu-id="68984-110">Wenn Sie über mehr als ein Abonnement verfügen, ist es ratsam, das [Standardabonnement zu bestätigen](manage-azure-subscriptions-azure-cli.md) und entsprechend zu ändern.</span><span class="sxs-lookup"><span data-stu-id="68984-110">If you have more than one subscription, you may want to [confirm your default subscription](manage-azure-subscriptions-azure-cli.md) and change it appropriately.</span></span>

## <a name="interactive-log-in"></a><span data-ttu-id="68984-111">Interaktive Anmeldung</span><span class="sxs-lookup"><span data-stu-id="68984-111">Interactive log-in</span></span>

<span data-ttu-id="68984-112">Melden Sie sich interaktiv über den Webbrowser an.</span><span class="sxs-lookup"><span data-stu-id="68984-112">Log in interactively from your web browser.</span></span>

[!INCLUDE [interactive_login](includes/interactive-login.md)]

## <a name="command-line"></a><span data-ttu-id="68984-113">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="68984-113">Command line</span></span>

<span data-ttu-id="68984-114">Geben Sie Ihre Anmeldeinformationen in der Befehlszeile an.</span><span class="sxs-lookup"><span data-stu-id="68984-114">Provide your credentials on the command line.</span></span>

> [!Note]
> <span data-ttu-id="68984-115">Dieser Ansatz funktioniert nicht für Microsoft-Konten oder Konten, für die die Authentifizierung in zwei Schritten aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="68984-115">This approach doesn't work with Microsoft accounts or accounts that have two-factor authentication enabled.</span></span>

```azurecli
az login -u <username> -p <password>
```

## <a name="logging-in-with-a-service-principal"></a><span data-ttu-id="68984-116">Anmelden mit einem Dienstprinzipal</span><span class="sxs-lookup"><span data-stu-id="68984-116">Logging in with a service principal</span></span>

<span data-ttu-id="68984-117">Dienstprinzipale sind vergleichbar mit Benutzerkonten, auf die Sie mithilfe von Azure Active Directory Regeln anwenden können.</span><span class="sxs-lookup"><span data-stu-id="68984-117">Service principals are like user accounts to which you can apply rules using Azure Active Directory.</span></span>
<span data-ttu-id="68984-118">Die Authentifizierung mit einem Dienstprinzipal ist die beste Möglichkeit, die Verwendung Ihrer Azure-Ressourcen mithilfe Ihrer Skripts oder Anwendungen zu schützen, mit denen Ressourcen bearbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="68984-118">Authenticating with a service principal is the best way to secure the usage of your Azure resources from either your scripts or applications that manipulate resources.</span></span>
<span data-ttu-id="68984-119">Sie definieren die gewünschten Rollen für Ihre Benutzer mit dem Befehlssatz von `az role`.</span><span class="sxs-lookup"><span data-stu-id="68984-119">You define the roles you want your users to have via the `az role` set of commands.</span></span>
<span data-ttu-id="68984-120">Weitere Informationen und Beispiele für Dienstprinzipalrollen finden Sie unter den [Referenzartikeln zu „az role“](https://docs.microsoft.com/cli/azure/role.md).</span><span class="sxs-lookup"><span data-stu-id="68984-120">You can learn more and see examples of service principal roles in our [az role reference articles](https://docs.microsoft.com/cli/azure/role.md).</span></span>

1. <span data-ttu-id="68984-121">Falls Sie noch nicht über einen Dienstprinzipal verfügen, [können Sie einen erstellen](create-an-azure-service-principal-azure-cli.md).</span><span class="sxs-lookup"><span data-stu-id="68984-121">If you don't already have a service principal, [create one](create-an-azure-service-principal-azure-cli.md).</span></span>

1. <span data-ttu-id="68984-122">Melden Sie sich mit dem Dienstprinzipal an.</span><span class="sxs-lookup"><span data-stu-id="68984-122">Log in with the service principal.</span></span>

   ```azurecli
   az login --service-principal -u "http://my-app" -p <password> --tenant <tenant>
   ```

   <span data-ttu-id="68984-123">Um Ihren Mandanten zu ermitteln, melden Sie sich interaktiv an und rufen anschließend die Mandanten-ID aus Ihrem Abonnement ab.</span><span class="sxs-lookup"><span data-stu-id="68984-123">To get your tenant, log in interactively and then get the tenantId from your subscription.</span></span>

   ```azurecli
   az login
   az account show
   ```

   ```json
   {
       "environmentName": "AzureCloud",
       "id": "********-****-****-****-************",
       "isDefault": true,
       "name": "Pay-As-You-Go",
       "state": "Enabled",
       "tenantId": "********-****-****-****-************",
       "user": {
       "name": "********",
       "type": "user"
       }
   }
   ```