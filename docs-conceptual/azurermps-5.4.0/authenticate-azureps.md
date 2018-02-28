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
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2018
---
# <a name="log-in-with-azure-powershell"></a>Aanmelden met Azure PowerShell

Azure PowerShell ondersteunt meerdere aanmeldingsmethoden. De eenvoudigste manier om aan de slag te gaan, is door u interactief aan te melden via de opdrachtregel.

## <a name="interactive-log-in"></a>Interactief aanmelden

1. Typ `Login-AzureRmAccount`. U krijgt een dialoogvenster te zien waarin wordt gevraagd naar uw Azure-referenties.

2. Typ het e-mailadres en het wachtwoord die bij uw account horen. Azure verifieert de referentiegegevens en slaat deze op. Vervolgens wordt het venster gesloten.

## <a name="log-in-with-a-service-principal"></a>Aanmelden met een service-principal

Service-principals stellen u in staat om niet-interactieve accounts te maken, die u vervolgens kunt gebruiken om bewerkingen uit te voeren op resources. U kunt service-principals zien als gebruikersaccounts waarop u regels kunt toepassen met behulp van Azure Active Directory. Door aan een service-principal het minimale aan machtigingen te verlenen, zorgt u ervoor dat uw automatiseringsscripts nog veiliger zijn.

1. Als u nog geen service-principal hebt, [maakt u er een](create-azure-service-principal-azureps.md).

2. Meld u aan met de service-principal.

    ```powershell
    Login-AzureRmAccount -ServicePrincipal -ApplicationId  "http://my-app" -Credential $pscredential -TenantId $tenantid
    ```

    U verkrijgt uw TenantId door u interactief aan te melden en vervolgens de TenantId uit uw abonnement op te halen.

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

### <a name="log-in-using-an-azure-vm-managed-service-identity"></a>Aanmelden met een Managed Service Identity van Azure VM

Managed Service Identity (MSI) is een preview-functie van Azure Active Directory. U kunt een MSI-service-principal gebruiken om u aan te melden, waarna u een token ontvangt waarmee u alleen vanuit de app toegang kunt krijgen tot andere resources.

Meer informatie over MSI leest u in [How to use an Azure VM Managed Service Identity (MSI) for sign-in and token acquisition](/azure/active-directory/msi-how-to-get-access-token-using-msi) (Een Managed Service Identity (MSI) van Azure VM gebruiken voor aanmelden en token ophalen).

## <a name="log-in-to-another-cloud"></a>Aanmelden bij een andere cloud

Azure-cloudservices bieden verschillende omgevingen die voldoen aan de voorschriften voor gegevensverwerking van verschillende overheden. Als uw Azure-account zich in een van de overheidsclouds bevindt, moet u de omgeving opgeven wanneer u zich aanmeldt. Als uw account zich bijvoorbeeld in de China-cloud bevindt, moet u zich aanmelden met de volgende opdracht:

```powershell
Login-AzureRmAccount -EnvironmentName AzureChinaCloud
```

Gebruik de volgende opdracht om een lijst met beschikbare omgevingen op te halen:

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

## <a name="learn-more-about-managing-azure-role-based-access"></a>Meer informatie over toegangsbeheer op basis van rollen in Azure

Zie [Accounts, abonnementen en beheerdersrollen beheren](/azure/active-directory/role-based-access-control-configure) voor meer informatie over verificatie en het beheren van abonnementen in Azure.

Azure PowerShell-cmdlets voor rollenbeheer

* [Get-AzureRmRoleAssignment](/powershell/module/AzureRM.Resources/Get-AzureRmRoleAssignment)
* [Get-AzureRmRoleDefinition](/powershell/module/AzureRM.Resources/Get-AzureRmRoleDefinition)
* [New-AzureRmRoleAssignment](/powershell/module/AzureRM.Resources/New-AzureRmRoleAssignment)
* [New-AzureRmRoleDefinition](/powershell/module/AzureRM.Resources/New-AzureRmRoleDefinition)
* [Remove-AzureRmRoleAssignment](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleAssignment)
* [Remove-AzureRmRoleDefinition](/powershell/module/AzureRM.Resources/Remove-AzureRmRoleDefinition)
* [Set-AzureRmRoleDefinition](/powershell/moduel/AzureRM.Resources/Set-AzureRmRoleDefinition)
