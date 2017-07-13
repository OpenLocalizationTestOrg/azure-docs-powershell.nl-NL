---
title: <span data-ttu-id="3f232-101">Aanmelden met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f232-101">Log in with Azure PowerShell</span></span>
description: <span data-ttu-id="3f232-102">Aanmelden met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f232-102">Log in with Azure PowerShell</span></span>
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: f6d249ca5bb09c4fe8445ba5b339ffa6012815ed
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="3f232-103">Aanmelden met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f232-103">Log in with Azure PowerShell</span></span>
<a id="log-in-with-azure-powershell" class="xliff"></a>

<span data-ttu-id="3f232-104">Azure PowerShell ondersteunt meerdere aanmeldingsmethoden.</span><span class="sxs-lookup"><span data-stu-id="3f232-104">Azure PowerShell supports multiple login methods.</span></span> <span data-ttu-id="3f232-105">De eenvoudigste manier om aan de slag te gaan, is door u interactief aan te melden via de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="3f232-105">The simplest way to get started is to log in interactively at the command line.</span></span>

## <span data-ttu-id="3f232-106">Interactief aanmelden</span><span class="sxs-lookup"><span data-stu-id="3f232-106">Interactive log in</span></span>
<a id="interactive-log-in" class="xliff"></a>

1. <span data-ttu-id="3f232-107">Typ `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="3f232-107">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="3f232-108">U krijgt een dialoogvenster te zien waarin wordt gevraagd naar uw Azure-referenties.</span><span class="sxs-lookup"><span data-stu-id="3f232-108">You will get dialog box asking for your Azure credentials.</span></span>

2. <span data-ttu-id="3f232-109">Typ het e-mailadres en het wachtwoord die bij uw account horen.</span><span class="sxs-lookup"><span data-stu-id="3f232-109">Type the email address and password associated with your account.</span></span> <span data-ttu-id="3f232-110">Azure verifieert de referentiegegevens en slaat deze op. Vervolgens wordt het venster gesloten.</span><span class="sxs-lookup"><span data-stu-id="3f232-110">Azure authenticates and saves the credential information, and then closes the window.</span></span>

## <span data-ttu-id="3f232-111">Aanmelden met een service-principal</span><span class="sxs-lookup"><span data-stu-id="3f232-111">Log in with a service principal</span></span>
<a id="log-in-with-a-service-principal" class="xliff"></a>

<span data-ttu-id="3f232-112">Service-principals stellen u in staat om niet-interactieve accounts te maken, die u vervolgens kunt gebruiken om bewerkingen uit te voeren op resources.</span><span class="sxs-lookup"><span data-stu-id="3f232-112">Service principals provide a way for you to create non-interactive accounts that you can use to manipulate resources.</span></span> <span data-ttu-id="3f232-113">U kunt service-principals zien als gebruikersaccounts waarop u regels kunt toepassen met behulp van Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="3f232-113">Service principals are like user accounts to which you can apply rules using Azure Active Directory.</span></span> <span data-ttu-id="3f232-114">Door aan een service-principal het minimale aan machtigingen te verlenen, zorgt u ervoor dat uw automatiseringsscripts nog veiliger zijn.</span><span class="sxs-lookup"><span data-stu-id="3f232-114">By granting the minimum permissions needed to a service principal, you can ensure your automation scripts are even more secure.</span></span>

1. <span data-ttu-id="3f232-115">Als u nog geen service-principal hebt, [maakt u er een](create-azure-service-principal-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="3f232-115">If you don't already have a service principal, [create one](create-azure-service-principal-azureps.md).</span></span>

2. <span data-ttu-id="3f232-116">Meld u aan met de service-principal.</span><span class="sxs-lookup"><span data-stu-id="3f232-116">Log in with the service principal.</span></span>

    ```powershell
    Login-AzureRmAccount -ServicePrincipal -ApplicationId  "http://my-app" -Credential $pscredential -TenantId $tenantid
    ```

    <span data-ttu-id="3f232-117">U verkrijgt uw TenantId door u interactief aan te melden en vervolgens de TenantId uit uw abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="3f232-117">To get your TenantId, log in interactively and then get the TenantId from your subscription.</span></span>

    ```powershell
    Get-AzureRmSubscription
    ```

    ```
    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Production Subscription
    CurrentStorageAccount :
    ```

## <span data-ttu-id="3f232-118">Aanmelden bij een andere cloud</span><span class="sxs-lookup"><span data-stu-id="3f232-118">Log in to another Cloud</span></span>
<a id="log-in-to-another-cloud" class="xliff"></a>

<span data-ttu-id="3f232-119">Azure-cloudservices bieden verschillende omgevingen die voldoen aan de voorschriften voor gegevensverwerking van verschillende overheden.</span><span class="sxs-lookup"><span data-stu-id="3f232-119">Azure cloud services provide different environments that adhere to the data-handling regulations of various governments.</span></span> <span data-ttu-id="3f232-120">Als uw Azure-account zich in een van de overheidsclouds bevindt, moet u de omgeving opgeven wanneer u zich aanmeldt.</span><span class="sxs-lookup"><span data-stu-id="3f232-120">If your Azure account is in one the government clouds, you need to specify the environment when you sign in.</span></span> <span data-ttu-id="3f232-121">Als uw account zich bijvoorbeeld in de China-cloud bevindt, moet u zich aanmelden met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="3f232-121">For example, if you account is in the China cloud you sign on using the following command:</span></span>

```powershell
Login-AzureRmAccount -EnvironmentName AzureChinaCloud
```

<span data-ttu-id="3f232-122">Gebruik de volgende opdracht om een lijst met beschikbare omgevingen op te halen:</span><span class="sxs-lookup"><span data-stu-id="3f232-122">Use the following command to get a list of available environments:</span></span>

```powershell
Get-AzureRmEnvironment | Select-Object Name
```

```
Name
----
AzureCloud
AzureChinaCloud
AzureUSGovernment
AzureGermanCloud
```

## <span data-ttu-id="3f232-123">Meer informatie over toegangsbeheer op basis van rollen in Azure</span><span class="sxs-lookup"><span data-stu-id="3f232-123">Learn more about managing Azure role-based access</span></span>
<a id="learn-more-about-managing-azure-role-based-access" class="xliff"></a>

<span data-ttu-id="3f232-124">Zie [Accounts, abonnementen en beheerdersrollen beheren](/azure/active-directory/role-based-access-control-configure) voor meer informatie over verificatie en het beheren van abonnementen in Azure.</span><span class="sxs-lookup"><span data-stu-id="3f232-124">For more information about authentication and subscription management in Azure, see [Manage Accounts, Subscriptions, and Administrative Roles](/azure/active-directory/role-based-access-control-configure).</span></span>

<span data-ttu-id="3f232-125">Azure PowerShell-cmdlets voor rollenbeheer</span><span class="sxs-lookup"><span data-stu-id="3f232-125">Azure PowerShell cmdlets for role management</span></span>

* [<span data-ttu-id="3f232-126">Get-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="3f232-126">Get-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleAssignment)
* [<span data-ttu-id="3f232-127">Get-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="3f232-127">Get-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleDefinition)
* [<span data-ttu-id="3f232-128">New-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="3f232-128">New-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleAssignment)
* [<span data-ttu-id="3f232-129">New-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="3f232-129">New-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleDefinition)
* [<span data-ttu-id="3f232-130">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="3f232-130">Remove-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleAssignment)
* [<span data-ttu-id="3f232-131">Remove-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="3f232-131">Remove-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleDefinition)
* [<span data-ttu-id="3f232-132">Set-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="3f232-132">Set-AzureRmRoleDefinition</span></span>](/powershell/moduel/AzureRM.Resources/Set-AzureRmRoleDefinition)
