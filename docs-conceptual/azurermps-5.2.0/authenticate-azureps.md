---
title: Aanmelden met Azure PowerShell
description: Aanmelden met Azure PowerShell
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: 1af5aeffb8e87e916df3e2440a84805935136c0f
ms.sourcegitcommit: 72f56597f0329d35779a3ea4ccea6293f0fd2502
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/01/2018
---
# <a name="log-in-with-azure-powershell"></a><span data-ttu-id="a9e9c-103">Aanmelden met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="a9e9c-103">Log in with Azure PowerShell</span></span>

<span data-ttu-id="a9e9c-104">Azure PowerShell ondersteunt meerdere aanmeldingsmethoden.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-104">Azure PowerShell supports multiple login methods.</span></span> <span data-ttu-id="a9e9c-105">De eenvoudigste manier om aan de slag te gaan, is door u interactief aan te melden via de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-105">The simplest way to get started is to log in interactively at the command line.</span></span>

## <a name="interactive-log-in"></a><span data-ttu-id="a9e9c-106">Interactief aanmelden</span><span class="sxs-lookup"><span data-stu-id="a9e9c-106">Interactive log in</span></span>

1. <span data-ttu-id="a9e9c-107">Typ `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-107">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="a9e9c-108">U krijgt een dialoogvenster te zien waarin wordt gevraagd naar uw Azure-referenties.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-108">You will get dialog box asking for your Azure credentials.</span></span>

2. <span data-ttu-id="a9e9c-109">Typ het e-mailadres en het wachtwoord die bij uw account horen.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-109">Type the email address and password associated with your account.</span></span> <span data-ttu-id="a9e9c-110">Azure verifieert de referentiegegevens en slaat deze op. Vervolgens wordt het venster gesloten.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-110">Azure authenticates and saves the credential information, and then closes the window.</span></span>

## <a name="log-in-with-a-service-principal"></a><span data-ttu-id="a9e9c-111">Aanmelden met een service-principal</span><span class="sxs-lookup"><span data-stu-id="a9e9c-111">Log in with a service principal</span></span>

<span data-ttu-id="a9e9c-112">Service-principals stellen u in staat om niet-interactieve accounts te maken, die u vervolgens kunt gebruiken om bewerkingen uit te voeren op resources.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-112">Service principals provide a way for you to create non-interactive accounts that you can use to manipulate resources.</span></span> <span data-ttu-id="a9e9c-113">U kunt service-principals zien als gebruikersaccounts waarop u regels kunt toepassen met behulp van Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-113">Service principals are like user accounts to which you can apply rules using Azure Active Directory.</span></span> <span data-ttu-id="a9e9c-114">Door aan een service-principal het minimale aan machtigingen te verlenen, zorgt u ervoor dat uw automatiseringsscripts nog veiliger zijn.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-114">By granting the minimum permissions needed to a service principal, you can ensure your automation scripts are even more secure.</span></span>

1. <span data-ttu-id="a9e9c-115">Als u nog geen service-principal hebt, [maakt u er een](create-azure-service-principal-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="a9e9c-115">If you don't already have a service principal, [create one](create-azure-service-principal-azureps.md).</span></span>

2. <span data-ttu-id="a9e9c-116">Meld u aan met de service-principal.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-116">Log in with the service principal.</span></span>

    ```powershell
    Login-AzureRmAccount -ServicePrincipal -ApplicationId  "http://my-app" -Credential $pscredential -TenantId $tenantid
    ```

    <span data-ttu-id="a9e9c-117">U verkrijgt uw TenantId door u interactief aan te melden en vervolgens de TenantId uit uw abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-117">To get your TenantId, log in interactively and then get the TenantId from your subscription.</span></span>

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

### <a name="log-in-using-an-azure-vm-managed-service-identity"></a><span data-ttu-id="a9e9c-118">Aanmelden met een Managed Service Identity van Azure VM</span><span class="sxs-lookup"><span data-stu-id="a9e9c-118">Log in using an Azure VM Managed Service Identity</span></span>

<span data-ttu-id="a9e9c-119">Managed Service Identity (MSI) is een preview-functie van Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-119">Managed Service Identity (MSI) is a preview feature of Azure Active Directory.</span></span> <span data-ttu-id="a9e9c-120">U kunt een MSI-service-principal gebruiken om u aan te melden, waarna u een token ontvangt waarmee u alleen vanuit de app toegang kunt krijgen tot andere resources.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-120">You can use an MSI service principal for sign-in, and acquire an app-only access token to access other resources.</span></span>

<span data-ttu-id="a9e9c-121">Meer informatie over MSI leest u in [How to use an Azure VM Managed Service Identity (MSI) for sign-in and token acquisition](/azure/active-directory/msi-how-to-get-access-token-using-msi) (Een Managed Service Identity (MSI) van Azure VM gebruiken voor aanmelden en token ophalen).</span><span class="sxs-lookup"><span data-stu-id="a9e9c-121">For more information about MSI, see [How to use an Azure VM Managed Service Identity (MSI) for sign-in and token acquisition](/azure/active-directory/msi-how-to-get-access-token-using-msi).</span></span>

## <a name="log-in-to-another-cloud"></a><span data-ttu-id="a9e9c-122">Aanmelden bij een andere cloud</span><span class="sxs-lookup"><span data-stu-id="a9e9c-122">Log in to another Cloud</span></span>

<span data-ttu-id="a9e9c-123">Azure-cloudservices bieden verschillende omgevingen die voldoen aan de voorschriften voor gegevensverwerking van verschillende overheden.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-123">Azure cloud services provide different environments that adhere to the data-handling regulations of various governments.</span></span> <span data-ttu-id="a9e9c-124">Als uw Azure-account zich in een van de overheidsclouds bevindt, moet u de omgeving opgeven wanneer u zich aanmeldt.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-124">If your Azure account is in one the government clouds, you need to specify the environment when you sign in.</span></span> <span data-ttu-id="a9e9c-125">Als uw account zich bijvoorbeeld in de China-cloud bevindt, moet u zich aanmelden met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="a9e9c-125">For example, if you account is in the China cloud you sign on using the following command:</span></span>

```powershell
Login-AzureRmAccount -EnvironmentName AzureChinaCloud
```

<span data-ttu-id="a9e9c-126">Gebruik de volgende opdracht om een lijst met beschikbare omgevingen op te halen:</span><span class="sxs-lookup"><span data-stu-id="a9e9c-126">Use the following command to get a list of available environments:</span></span>

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

## <a name="learn-more-about-managing-azure-role-based-access"></a><span data-ttu-id="a9e9c-127">Meer informatie over toegangsbeheer op basis van rollen in Azure</span><span class="sxs-lookup"><span data-stu-id="a9e9c-127">Learn more about managing Azure role-based access</span></span>

<span data-ttu-id="a9e9c-128">Zie [Accounts, abonnementen en beheerdersrollen beheren](/azure/active-directory/role-based-access-control-configure) voor meer informatie over verificatie en het beheren van abonnementen in Azure.</span><span class="sxs-lookup"><span data-stu-id="a9e9c-128">For more information about authentication and subscription management in Azure, see [Manage Accounts, Subscriptions, and Administrative Roles](/azure/active-directory/role-based-access-control-configure).</span></span>

<span data-ttu-id="a9e9c-129">Azure PowerShell-cmdlets voor rollenbeheer</span><span class="sxs-lookup"><span data-stu-id="a9e9c-129">Azure PowerShell cmdlets for role management</span></span>

* [<span data-ttu-id="a9e9c-130">Get-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="a9e9c-130">Get-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleAssignment)
* [<span data-ttu-id="a9e9c-131">Get-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="a9e9c-131">Get-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Get-AzureRmRoleDefinition)
* [<span data-ttu-id="a9e9c-132">New-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="a9e9c-132">New-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleAssignment)
* [<span data-ttu-id="a9e9c-133">New-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="a9e9c-133">New-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/New-AzureRmRoleDefinition)
* [<span data-ttu-id="a9e9c-134">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="a9e9c-134">Remove-AzureRmRoleAssignment</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleAssignment)
* [<span data-ttu-id="a9e9c-135">Remove-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="a9e9c-135">Remove-AzureRmRoleDefinition</span></span>](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleDefinition)
* [<span data-ttu-id="a9e9c-136">Set-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="a9e9c-136">Set-AzureRmRoleDefinition</span></span>](/powershell/moduel/AzureRM.Resources/Set-AzureRmRoleDefinition)
