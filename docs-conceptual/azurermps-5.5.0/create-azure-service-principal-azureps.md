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
ms.openlocfilehash: 6eda2d2a729331b212938aa2681d0188a25b734a
ms.sourcegitcommit: 20af779cd523c758d40e23d60eb989a4ef982d5c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="create-an-azure-service-principal-with-azure-powershell"></a><span data-ttu-id="e8c49-104">Een Azure-service-principal maken met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8c49-104">Create an Azure service principal with Azure PowerShell</span></span>

<span data-ttu-id="e8c49-105">Als u van plan bent om uw app of service met Azure PowerShell te beheren, moet u deze uitvoeren met behulp van een AAD-service-principal (Azure Active Directory) in plaats van met uw eigen referenties.</span><span class="sxs-lookup"><span data-stu-id="e8c49-105">If you plan to manage your app or service with Azure PowerShell, you should run it under an Azure Active Directory (AAD) service principal, rather than your own credentials.</span></span> <span data-ttu-id="e8c49-106">In dit onderwerp wordt stapsgewijs uitgelegd hoe u met Azure PowerShell een beveiligingsprincipal maakt.</span><span class="sxs-lookup"><span data-stu-id="e8c49-106">This topic steps you through creating a security principal with Azure PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="e8c49-107">U kunt ook een service-principal maken via Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="e8c49-107">You can also create a service principal through the Azure portal.</span></span> <span data-ttu-id="e8c49-108">Lees [Portal gebruiken voor het maken van een Active Directory-toepassing en -service-principal die toegang hebben tot resources](/azure/azure-resource-manager/resource-group-create-service-principal-portal) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e8c49-108">Read [Use portal to create Active Directory application and service principal that can access resources](/azure/azure-resource-manager/resource-group-create-service-principal-portal) for more details.</span></span>

## <a name="what-is-a-service-principal"></a><span data-ttu-id="e8c49-109">Wat is een service-principal?</span><span class="sxs-lookup"><span data-stu-id="e8c49-109">What is a 'service principal'?</span></span>

<span data-ttu-id="e8c49-110">Een Azure-service-principal is een beveiligings-id die wordt gebruikt door apps, services en automatiseringsprogramma's die door gebruikers zijn gemaakt voor het verkrijgen van toegang tot specifieke Azure-resources.</span><span class="sxs-lookup"><span data-stu-id="e8c49-110">An Azure service principal is a security identity used by user-created apps, services, and automation tools to access specific Azure resources.</span></span> <span data-ttu-id="e8c49-111">U kunt een service-principal vergelijken met een gebruikers-id (gebruikersnaam en wachtwoord of certificaat) die een specifieke rol heeft en over nauwkeurig omschreven machtigingen beschikt.</span><span class="sxs-lookup"><span data-stu-id="e8c49-111">Think of it as a 'user identity' (username and password or certificate) with a specific role, and tightly controlled permissions.</span></span> <span data-ttu-id="e8c49-112">Anders dan een algemene gebruikers-id, hoeft een service-principal slechts enkele specifieke handelingen uit te kunnen voeren.</span><span class="sxs-lookup"><span data-stu-id="e8c49-112">It only needs to be able to do specific things, unlike a general user identity.</span></span> <span data-ttu-id="e8c49-113">De beveiliging verbetert erdoor als u er net voldoende machtigingen aan verleent om de beheertaken te kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e8c49-113">It improves security if you only grant it the minimum permissions level needed to perform its management tasks.</span></span>

## <a name="verify-your-own-permission-level"></a><span data-ttu-id="e8c49-114">Uw eigen machtigingsniveau controleren</span><span class="sxs-lookup"><span data-stu-id="e8c49-114">Verify your own permission level</span></span>

<span data-ttu-id="e8c49-115">In de eerste plaats moet u over voldoende machtigingen beschikken in uw Azure Active Directory en uw Azure-abonnement.</span><span class="sxs-lookup"><span data-stu-id="e8c49-115">First, you must have sufficient permissions in both your Azure Active Directory and your Azure subscription.</span></span> <span data-ttu-id="e8c49-116">Meer specifiek moet u een app in de Active Directory kunnen maken en een rol kunnen toewijzen aan de service-principal.</span><span class="sxs-lookup"><span data-stu-id="e8c49-116">Specifically, you must be able to create an app in the Active Directory, and assign a role to the service principal.</span></span>

<span data-ttu-id="e8c49-117">De eenvoudigste manier om te controleren of uw account over de juiste machtigingen beschikt, verloopt via de portal.</span><span class="sxs-lookup"><span data-stu-id="e8c49-117">The easiest way to check whether your account has adequate permissions is through the portal.</span></span> <span data-ttu-id="e8c49-118">Zie [Check required permission in portal](/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) (Vereiste machtigingen controleren in de portal).</span><span class="sxs-lookup"><span data-stu-id="e8c49-118">See [Check required permission in portal](/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions).</span></span>

## <a name="create-a-service-principal-for-your-app"></a><span data-ttu-id="e8c49-119">Een service-principal voor uw app maken</span><span class="sxs-lookup"><span data-stu-id="e8c49-119">Create a service principal for your app</span></span>

<span data-ttu-id="e8c49-120">U kunt de service-principal maken nadat u zich hebt aangemeld bij uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="e8c49-120">Once you are signed into your Azure account, you can create the service principal.</span></span> <span data-ttu-id="e8c49-121">U moet met een van de volgende methoden de door u geïmplementeerde app kunnen identificeren:</span><span class="sxs-lookup"><span data-stu-id="e8c49-121">You must have one of the following ways to identify your deployed app:</span></span>

* <span data-ttu-id="e8c49-122">de unieke naam van de door u geïmplementeerde app, zoals 'MyDemoWebApp' in de volgende voorbeelden of</span><span class="sxs-lookup"><span data-stu-id="e8c49-122">The unique name of your deployed app, such as "MyDemoWebApp" in the following examples, or</span></span>
* <span data-ttu-id="e8c49-123">de toepassings-id, de unieke GUID die is gekoppeld aan de door u geïmplementeerde app of service, of het door u geïmplementeerde object</span><span class="sxs-lookup"><span data-stu-id="e8c49-123">the Application ID, the unique GUID associated with your deployed app, service, or object</span></span>

### <a name="get-information-about-your-application"></a><span data-ttu-id="e8c49-124">Informatie over uw toepassing verzamelen</span><span class="sxs-lookup"><span data-stu-id="e8c49-124">Get information about your application</span></span>

<span data-ttu-id="e8c49-125">De cmdlet `Get-AzureRmADApplication` kan worden gebruikt om informatie over uw toepassing te achterhalen.</span><span class="sxs-lookup"><span data-stu-id="e8c49-125">The `Get-AzureRmADApplication` cmdlet can be used to discover information about your application.</span></span>

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

### <a name="create-a-service-principal-for-your-application"></a><span data-ttu-id="e8c49-126">Een service-principal voor uw toepassing maken</span><span class="sxs-lookup"><span data-stu-id="e8c49-126">Create a service principal for your application</span></span>

<span data-ttu-id="e8c49-127">De cmdlet `New-AzureRmADServicePrincipal` wordt gebruikt om de service-principal te maken.</span><span class="sxs-lookup"><span data-stu-id="e8c49-127">The `New-AzureRmADServicePrincipal` cmdlet is used to create the service principal.</span></span>

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

### <a name="get-information-about-the-service-principal"></a><span data-ttu-id="e8c49-128">Informatie over de service-principal verzamelen</span><span class="sxs-lookup"><span data-stu-id="e8c49-128">Get information about the service principal</span></span>

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

### <a name="sign-in-using-the-service-principal"></a><span data-ttu-id="e8c49-129">U aanmelden met de service principal</span><span class="sxs-lookup"><span data-stu-id="e8c49-129">Sign in using the service principal</span></span>

<span data-ttu-id="e8c49-130">U kunt u nu aanmelden als de nieuwe service-principal voor uw app met behulp van de *appId* en het *wachtwoord* die u hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e8c49-130">You can now sign in as the new service principal for your app using the *appId* and *password* you provided.</span></span> <span data-ttu-id="e8c49-131">U moet de tenant-id voor uw account opgeven.</span><span class="sxs-lookup"><span data-stu-id="e8c49-131">You need to supply the Tenant Id for your account.</span></span> <span data-ttu-id="e8c49-132">Uw tenant-id wordt weergegeven als u zich bij Azure met uw persoonlijke referenties aanmeldt.</span><span class="sxs-lookup"><span data-stu-id="e8c49-132">Your Tenant Id is displayed when you sign into Azure with your personal credentials.</span></span>

```powershell
$cred = Get-Credential -UserName $svcprincipal.ApplicationId -Message "Enter Password"
Login-AzureRmAccount -Credential $cred -ServicePrincipal -TenantId XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="e8c49-133">Voer deze opdracht uit vanuit een nieuwe PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="e8c49-133">Run this command from a new PowerShell session.</span></span> <span data-ttu-id="e8c49-134">Als de aanmelding is gelukt, krijgt u uitvoer te zien die er ongeveer als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="e8c49-134">After a successfully signing on you see output something like this:</span></span>

```
Environment           : AzureCloud
Account               : 00c01aaa-1603-49fc-b6df-b78c4e5138b4
TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
SubscriptionId        :
SubscriptionName      :
CurrentStorageAccount :
```

<span data-ttu-id="e8c49-135">Gefeliciteerd.</span><span class="sxs-lookup"><span data-stu-id="e8c49-135">Congratulations!</span></span> <span data-ttu-id="e8c49-136">U kunt deze referenties gebruiken om uw app uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="e8c49-136">You can use these credentials to run your app.</span></span> <span data-ttu-id="e8c49-137">De volgende stap bestaat eruit dat u de machtigingen van de service-principal gaat aanpassen.</span><span class="sxs-lookup"><span data-stu-id="e8c49-137">Next, you need to adjust the permissions of the service principal.</span></span>

## <a name="managing-roles"></a><span data-ttu-id="e8c49-138">Rollen beheren</span><span class="sxs-lookup"><span data-stu-id="e8c49-138">Managing roles</span></span>

> [!NOTE]
> <span data-ttu-id="e8c49-139">Toegangsbeheer op basis van rollen in Azure (RBAC) is een model voor het definiëren en beheren van rollen voor principals van gebruikers en voor service-principals.</span><span class="sxs-lookup"><span data-stu-id="e8c49-139">Azure Role-Based Access Control (RBAC) is a model for defining and managing roles for user and service principals.</span></span> <span data-ttu-id="e8c49-140">Aan rollen zijn machtigingensets gekoppeld, die bepalen welke resources een principal kan lezen, waar hij toegang tot heeft, waarvoor hij schrijfrechten heeft en welke hij kan beheren.</span><span class="sxs-lookup"><span data-stu-id="e8c49-140">Roles have sets of permissions associated with them, which determine the resources a principal can read, access, write, or manage.</span></span> <span data-ttu-id="e8c49-141">Zie [RBAC: ingebouwde rollen](/azure/active-directory/role-based-access-built-in-roles) voor meer informatie over RBAC en rollen.</span><span class="sxs-lookup"><span data-stu-id="e8c49-141">For more information on RBAC and roles, see [RBAC: Built-in roles](/azure/active-directory/role-based-access-built-in-roles).</span></span>

<span data-ttu-id="e8c49-142">Azure PowerShell biedt de volgende cmdlets voor het beheren van roltoewijzingen:</span><span class="sxs-lookup"><span data-stu-id="e8c49-142">Azure PowerShell provides the following cmdlets to manage role assignments:</span></span>

* [<span data-ttu-id="e8c49-143">Get-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="e8c49-143">Get-AzureRmRoleAssignment</span></span>](/powershell/module/azurerm.resources/get-azurermroleassignment)
* [<span data-ttu-id="e8c49-144">New-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="e8c49-144">New-AzureRmRoleAssignment</span></span>](/powershell/module/azurerm.resources/new-azurermroleassignment)
* [<span data-ttu-id="e8c49-145">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="e8c49-145">Remove-AzureRmRoleAssignment</span></span>](/powershell/module/azurerm.resources/remove-azurermroleassignment)

<span data-ttu-id="e8c49-146">De standaardrol van een service-principal is die van **Inzender**.</span><span class="sxs-lookup"><span data-stu-id="e8c49-146">The default role for a service principal is **Contributor**.</span></span> <span data-ttu-id="e8c49-147">Op basis van het bereik van de interacties van uw app met de services van Azure-services is dit misschien niet de beste keuze, omdat de machtigingen van deze rol nogal uitgebreid zijn.</span><span class="sxs-lookup"><span data-stu-id="e8c49-147">It may not be the best choice depending on the scope of your app's interactions with Azure services, given its broad permissions.</span></span>
<span data-ttu-id="e8c49-148">De rol van **Lezer** is een beperktere rol en daardoor een goede keuze voor alleen-lezen apps.</span><span class="sxs-lookup"><span data-stu-id="e8c49-148">The **Reader** role is more restrictive and can be a good choice for read-only apps.</span></span> <span data-ttu-id="e8c49-149">U kunt details weergeven over rolspecifieke machtigingen of aangepaste machtigingen maken via Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="e8c49-149">You can view details on role-specific permissions or create custom ones through the Azure portal.</span></span>

<span data-ttu-id="e8c49-150">In dit voorbeeld voegen we de rol van **Lezer** toe aan ons eerdere voorbeeld en verwijderen we de rol **Inzender**:</span><span class="sxs-lookup"><span data-stu-id="e8c49-150">In this example, we add the **Reader** role to our prior example, and delete the **Contributor** one:</span></span>

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

<span data-ttu-id="e8c49-151">De rollen die momenteel zijn toegewezen:</span><span class="sxs-lookup"><span data-stu-id="e8c49-151">To view the current roles assigned:</span></span>

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

<span data-ttu-id="e8c49-152">Andere Azure PowerShell-cmdlets voor rollenbeheer:</span><span class="sxs-lookup"><span data-stu-id="e8c49-152">Other Azure PowerShell cmdlets for role management:</span></span>

* [<span data-ttu-id="e8c49-153">Get-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="e8c49-153">Get-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/Get-AzureRmRoleDefinition)
* [<span data-ttu-id="e8c49-154">New-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="e8c49-154">New-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/New-AzureRmRoleDefinition)
* [<span data-ttu-id="e8c49-155">Remove-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="e8c49-155">Remove-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/Remove-AzureRmRoleDefinition)
* [<span data-ttu-id="e8c49-156">Set-AzureRmRoleDefinition</span><span class="sxs-lookup"><span data-stu-id="e8c49-156">Set-AzureRmRoleDefinition</span></span>](/powershell/module/azurerm.resources/Set-AzureRmRoleDefinition)

## <a name="change-the-credentials-of-the-security-principal"></a><span data-ttu-id="e8c49-157">De referenties van de beveiligingsprincipal wijzigen</span><span class="sxs-lookup"><span data-stu-id="e8c49-157">Change the credentials of the security principal</span></span>

<span data-ttu-id="e8c49-158">Het is een goede gewoonte om regelmatig de machtigingen te controleren en het wachtwoord te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e8c49-158">It's a good security practice to review the permissions and update the password regularly.</span></span> <span data-ttu-id="e8c49-159">Misschien wilt u naarmate de app verandert, de beveiligingsreferenties ervan ook wel beheren of wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e8c49-159">You may also want to manage and modify the security credentials as your app changes.</span></span> <span data-ttu-id="e8c49-160">We kunnen bijvoorbeeld het wachtwoord van de service-principal wijzigen door een nieuw wachtwoord te maken en het oude te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e8c49-160">For example, we can change the password of the service principal by creating a new password and removing the old one.</span></span>

### <a name="add-a-new-password-for-the-service-principal"></a><span data-ttu-id="e8c49-161">Een nieuw wachtwoord voor de service-principal toevoegen</span><span class="sxs-lookup"><span data-stu-id="e8c49-161">Add a new password for the service principal</span></span>

```powershell
$password = [System.Web.Security.Membership]::GeneratePassword(16,3)
New-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -Password $password
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```

### <a name="get-a-list-of-credentials-for-the-service-principal"></a><span data-ttu-id="e8c49-162">Een lijst met referenties voor de service-principal ophalen</span><span class="sxs-lookup"><span data-stu-id="e8c49-162">Get a list of credentials for the service principal</span></span>

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
5/5/2016 4:55:27 PM 5/5/2017 4:55:27 PM ca9d4846-4972-4c70-b6f5-a4effa60b9bc Password
```

### <a name="remove-the-old-password-from-the-service-principal"></a><span data-ttu-id="e8c49-163">Het oude wachtwoord uit de service-principal verwijderen</span><span class="sxs-lookup"><span data-stu-id="e8c49-163">Remove the old password from the service principal</span></span>

```powershell
Remove-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp -KeyId ca9d4846-4972-4c70-b6f5-a4effa60b9bc
```

```
Confirm
Are you sure you want to remove credential with keyId '6f801c3e-6fcd-42b9-be8e-320b17ba1d36' for
service principal objectId '698138e7-d7b6-4738-a866-b4e3081a69e4'.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

### <a name="verify-the-list-of-credentials-for-the-service-principal"></a><span data-ttu-id="e8c49-164">De lijst met referenties voor de service-principal verifiëren</span><span class="sxs-lookup"><span data-stu-id="e8c49-164">Verify the list of credentials for the service principal</span></span>

```powershell
Get-AzureRmADSpCredential -ServicePrincipalName http://MyDemoWebApp
```

```
StartDate           EndDate             KeyId                                Type
---------           -------             -----                                ----
3/8/2017 5:58:24 PM 3/8/2018 5:58:24 PM 6f801c3e-6fcd-42b9-be8e-320b17ba1d36 Password
```
