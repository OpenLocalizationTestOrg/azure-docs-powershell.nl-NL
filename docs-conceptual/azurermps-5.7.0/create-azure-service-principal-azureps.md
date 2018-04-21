---
title: Een Azure-service-principal maken met Azure PowerShell
description: Lees hoe u met Azure PowerShell een service-principal voor uw app of service maakt.
keywords: Azure PowerShell, Azure Active Directory, Azure Active directory, AD, RBAC
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: fb192583ccb47ce790b305cf1ac5a687ff811d1d
ms.sourcegitcommit: 5f0013981fcea1d689649b9a2b2ffe84ae842e56
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="create-an-azure-service-principal-with-azure-powershell"></a>Een Azure-service-principal maken met Azure PowerShell

Als u van plan bent om uw app of service met Azure PowerShell te beheren, moet u deze uitvoeren met behulp van een AAD-service-principal (Azure Active Directory) in plaats van met uw eigen referenties. In dit onderwerp wordt stapsgewijs uitgelegd hoe u met Azure PowerShell een beveiligingsprincipal maakt.

> [!NOTE]
> U kunt ook een service-principal maken via Azure Portal. Lees [Portal gebruiken voor het maken van een Active Directory-toepassing en -service-principal die toegang hebben tot resources](/azure/azure-resource-manager/resource-group-create-service-principal-portal) voor meer informatie.

## <a name="what-is-a-service-principal"></a>Wat is een service-principal?

Een Azure-service-principal is een beveiligings-id die wordt gebruikt door apps, services en automatiseringsprogramma's die door gebruikers zijn gemaakt voor het verkrijgen van toegang tot specifieke Azure-resources. U kunt een service-principal vergelijken met een gebruikers-id (gebruikersnaam en wachtwoord of certificaat) die een specifieke rol heeft en over nauwkeurig omschreven machtigingen beschikt. Anders dan een algemene gebruikers-id, hoeft een service-principal slechts enkele specifieke handelingen uit te kunnen voeren. De beveiliging verbetert erdoor als u er net voldoende machtigingen aan verleent om de beheertaken te kunnen uitvoeren.

## <a name="verify-your-own-permission-level"></a>Uw eigen machtigingsniveau controleren

In de eerste plaats moet u over voldoende machtigingen beschikken in uw Azure Active Directory en uw Azure-abonnement. Meer specifiek moet u een app in de Active Directory kunnen maken en een rol kunnen toewijzen aan de service-principal.

De eenvoudigste manier om te controleren of uw account over de juiste machtigingen beschikt, verloopt via de portal. Zie [Check required permission in portal](/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) (Vereiste machtigingen controleren in de portal).

## <a name="create-a-service-principal-for-your-app"></a>Een service-principal voor uw app maken

U kunt de service-principal maken nadat u zich hebt aangemeld bij uw Azure-account. U moet met een van de volgende methoden de door u geïmplementeerde app kunnen identificeren:

* de unieke naam van de door u geïmplementeerde app, zoals 'MyDemoWebApp' in de volgende voorbeelden of
* de toepassings-id, de unieke GUID die is gekoppeld aan de door u geïmplementeerde app of service, of het door u geïmplementeerde object

### <a name="get-information-about-your-application"></a>Informatie over uw toepassing verzamelen

De cmdlet `Get-AzureRmADApplication` kan worden gebruikt om informatie over uw toepassing te achterhalen.

```powershell
Get-AzureRmADApplication -DisplayNameStartWith MyDemoWebApp
```

```
DisplayName             : MyDemoWebApp
ObjectId                : 775f64cd-0ec8-4b9b-b69a-8b8946022d9f
IdentifierUris          : {http://MyDemoWebApp}
HomePage                : http://www.contoso.com
Type                    : Application
ApplicationId           : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
AvailableToOtherTenants : False
AppPermissions          :
ReplyUrls               : {}
```

### <a name="create-a-service-principal-for-your-application"></a>Een service-principal voor uw toepassing maken

De cmdlet `New-AzureRmADServicePrincipal` wordt gebruikt om de service-principal te maken.

```powershell
Add-Type -Assembly System.Web
$password = [System.Web.Security.Membership]::GeneratePassword(16,3)
New-AzureRmADServicePrincipal -ApplicationId 00c01aaa-1603-49fc-b6df-b78c4e5138b4 -Password $password
```

```
DisplayName                    Type                           ObjectId
-----------                    ----                           --------
MyDemoWebApp                   ServicePrincipal               698138e7-d7b6-4738-a866-b4e3081a69e4
```

### <a name="get-information-about-the-service-principal"></a>Informatie over de service-principal verzamelen

```powershell
$svcprincipal = Get-AzureRmADServicePrincipal -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4
$svcprincipal | Select-Object *
```

```
ServicePrincipalNames : {http://MyDemoWebApp, 00c01aaa-1603-49fc-b6df-b78c4e5138b4}
ApplicationId         : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
DisplayName           : MyDemoWebApp
Id                    : 698138e7-d7b6-4738-a866-b4e3081a69e4
Type                  : ServicePrincipal
```

### <a name="sign-in-using-the-service-principal"></a>U aanmelden met de service principal

U kunt u nu aanmelden als de nieuwe service-principal voor uw app met behulp van de *appId* en het *wachtwoord* die u hebt opgegeven. U moet de tenant-id voor uw account opgeven. Uw tenant-id wordt weergegeven als u zich bij Azure met uw persoonlijke referenties aanmeldt.

```powershell
$cred = Get-Credential -UserName $svcprincipal.ApplicationId -Message "Enter Password"
Connect-AzureRmAccount -Credential $cred -ServicePrincipal -TenantId XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

Voer deze opdracht uit vanuit een nieuwe PowerShell-sessie. Als de aanmelding is gelukt, krijgt u uitvoer te zien die er ongeveer als volgt uitziet:

```
Environment           : AzureCloud
Account               : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
SubscriptionId        :
SubscriptionName      :
CurrentStorageAccount :
```

Gefeliciteerd. U kunt deze referenties gebruiken om uw app uit te voeren. De volgende stap bestaat eruit dat u de machtigingen van de service-principal gaat aanpassen.

## <a name="managing-roles"></a>Rollen beheren

> [!NOTE]
> Toegangsbeheer op basis van rollen in Azure (RBAC) is een model voor het definiëren en beheren van rollen voor principals van gebruikers en voor service-principals. Aan rollen zijn machtigingensets gekoppeld, die bepalen welke resources een principal kan lezen, waar hij toegang tot heeft, waarvoor hij schrijfrechten heeft en welke hij kan beheren. Zie [RBAC: ingebouwde rollen](/azure/active-directory/role-based-access-built-in-roles) voor meer informatie over RBAC en rollen.

Azure PowerShell biedt de volgende cmdlets voor het beheren van roltoewijzingen:

* [Get-AzureRmRoleAssignment](/powershell/module/azurerm.resources/get-azurermroleassignment)
* [New-AzureRmRoleAssignment](/powershell/module/azurerm.resources/new-azurermroleassignment)
* [Remove-AzureRmRoleAssignment](/powershell/module/azurerm.resources/remove-azurermroleassignment)

De standaardrol van een service-principal is die van **Inzender**. Op basis van het bereik van de interacties van uw app met de services van Azure-services is dit misschien niet de beste keuze, omdat de machtigingen van deze rol nogal uitgebreid zijn.
De rol van **Lezer** is een beperktere rol en daardoor een goede keuze voor alleen-lezen apps. U kunt details weergeven over rolspecifieke machtigingen of aangepaste machtigingen maken via Azure Portal.

In dit voorbeeld voegen we de rol van **Lezer** toe aan ons eerdere voorbeeld en verwijderen we de rol **Inzender**:

```powershell
New-AzureRmRoleAssignment -ResourceGroupName myRG -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4 -RoleDefinitionName Reader
```

```
RoleAssignmentId   : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG/providers/Microsoft.Authorization/roleAssignments/818892f2-d075-46a1-a3a2-3a4e1a12fcd5
Scope              : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG
DisplayName        : MyDemoWebApp
SignInName         :
RoleDefinitionName : Reader
RoleDefinitionId   : b24988ac-6180-42a0-ab88-20f7382dd24c
ObjectId           : 698138e7-d7b6-4738-a866-b4e3081a69e4
ObjectType         : ServicePrincipal
```

```powershell
Remove-AzureRmRoleAssignment -ResourceGroupName myRG -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4 -RoleDefinitionName Contributor
```

De rollen die momenteel zijn toegewezen:

```powershell
Get-AzureRmRoleAssignment -ResourceGroupName myRG -ObjectId 698138e7-d7b6-4738-a866-b4e3081a69e4
```

```
RoleAssignmentId   : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG/providers/Microsoft.Authorization/roleAssignments/0906bbd8-9982-4c03-8dae-aeaae8b13f9e
Scope              : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myRG
DisplayName        : MyDemoWebApp
SignInName         :
RoleDefinitionName : Reader
RoleDefinitionId   : acdd72a7-3385-48ef-bd42-f606fba81ae7
ObjectId           : 698138e7-d7b6-4738-a866-b4e3081a69e4
ObjectType         : ServicePrincipal
```

Andere Azure PowerShell-cmdlets voor rollenbeheer:

* [Get-AzureRmRoleDefinition](/powershell/module/azurerm.resources/Get-AzureRmRoleDefinition)
* [New-AzureRmRoleDefinition](/powershell/module/azurerm.resources/New-AzureRmRoleDefinition)
* [Remove-AzureRmRoleDefinition](/powershell/module/azurerm.resources/Remove-AzureRmRoleDefinition)
* [Set-AzureRmRoleDefinition](/powershell/module/azurerm.resources/Set-AzureRmRoleDefinition)

## <a name="change-the-credentials-of-the-security-principal"></a>De referenties van de beveiligingsprincipal wijzigen

Het is een goede gewoonte om regelmatig de machtigingen te controleren en het wachtwoord te wijzigen. Misschien wilt u naarmate de app verandert, de beveiligingsreferenties ervan ook wel beheren of wijzigen. We kunnen bijvoorbeeld het wachtwoord van de service-principal wijzigen door een nieuw wachtwoord te maken en het oude te verwijderen.

### <a name="add-a-new-password-for-the-service-principal"></a>Een nieuw wachtwoord voor de service-principal toevoegen

```powershell
$password = [System.Web.Security.Membership]::GeneratePassword(16,3)
New-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -Password $password
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```

### <a name="get-a-list-of-credentials-for-the-service-principal"></a>Een lijst met referenties voor de service-principal ophalen

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
5/5/2016 4:55:27 PM 5/5/2017 4:55:27 PM ca9d4846-4972-4c70-b6f5-a4effa60b9bc Password
```

### <a name="remove-the-old-password-from-the-service-principal"></a>Het oude wachtwoord uit de service-principal verwijderen

```powershell
Remove-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -KeyId ca9d4846-4972-4c70-b6f5-a4effa60b9bc
```

```
Confirm
Are you sure you want to remove credential with keyId '6f801c3e-6fcd-42b9-be8e-320b17ba1d36' for
service principal objectId '698138e7-d7b6-4738-a866-b4e3081a69e4'.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

### <a name="verify-the-list-of-credentials-for-the-service-principal"></a>De lijst met referenties voor de service-principal verifiëren

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```
