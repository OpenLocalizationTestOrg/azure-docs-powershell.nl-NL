---
title: <span data-ttu-id="62f1f-101">Azure PowerShell installeren en configureren | Microsoft Docs</span><span class="sxs-lookup"><span data-stu-id="62f1f-101">Install and configure Azure PowerShell | Microsoft Docs</span></span>
description: <span data-ttu-id="62f1f-102">Azure PowerShell voor het eerst installeren en configureren</span><span class="sxs-lookup"><span data-stu-id="62f1f-102">How to install and configure Azure PowerShell for first time use.</span></span>
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/17/2017
ms.openlocfilehash: 86bf3ab84b706d44b46f420d07570069f65bde72
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="62f1f-103">Azure PowerShell installeren en configureren</span><span class="sxs-lookup"><span data-stu-id="62f1f-103">Install and configure Azure PowerShell</span></span>
<a id="install-and-configure-azure-powershell" class="xliff"></a>

<span data-ttu-id="62f1f-104">Installatie van Azure PowerShell via PowerShell Gallery heeft de voorkeur.</span><span class="sxs-lookup"><span data-stu-id="62f1f-104">Installing Azure PowerShell from the PowerShell Gallery is the preferred method of installation.</span></span>

## <span data-ttu-id="62f1f-105">Stap 1: PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="62f1f-105">Step 1: Install PowerShellGet</span></span>
<a id="step-1-install-powershellget" class="xliff"></a>

<span data-ttu-id="62f1f-106">Als u items uit de PowerShell Gallery wilt installeren, hebt u de PowerShellGet-module nodig.</span><span class="sxs-lookup"><span data-stu-id="62f1f-106">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="62f1f-107">Zorg ervoor dat u de juiste versie van PowerShellGet hebt en ook voldoet aan de overige systeemvereisten.</span><span class="sxs-lookup"><span data-stu-id="62f1f-107">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="62f1f-108">Voer de volgende opdracht uit om na te gaan of PowerShellGet op uw systeem is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="62f1f-108">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

<span data-ttu-id="62f1f-109">De uitvoer moet er ongeveer uitzien als hieronder is weergegeven:</span><span class="sxs-lookup"><span data-stu-id="62f1f-109">You should see something similar to the following output:</span></span>

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="62f1f-110">Zie de sectie [PowerShellGet ophalen](#how-to-get-powershellget) van dit artikel als PowerShellGet niet is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="62f1f-110">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](#how-to-get-powershellget) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="62f1f-111">Als u PowerShellGet gebruikt, hebt u een uitvoeringsbeleid nodig waarmee u scripts kunt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="62f1f-111">Using PowerShellGet requires an Execution Policy that allows you to run scripts.</span></span> <span data-ttu-id="62f1f-112">Zie [About Execution Policies](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) (Informatie over uitvoeringsbeleid) voor meer informatie over het uitvoeringsbeleid van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62f1f-112">For more information about PowerShell's Execution Policy, see [About Execution Policies](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <span data-ttu-id="62f1f-113">Stap 2: Azure PowerShell installeren</span><span class="sxs-lookup"><span data-stu-id="62f1f-113">Step 2: Install Azure PowerShell</span></span>
<a id="step-2-install-azure-powershell" class="xliff"></a>

<span data-ttu-id="62f1f-114">Als u Azure PowerShell via de PowerShell Gallery wilt installeren, hebt u verhoogde bevoegdheden nodig.</span><span class="sxs-lookup"><span data-stu-id="62f1f-114">Installing Azure PowerShell from the PowerShell Gallery requires elevated privileges.</span></span> <span data-ttu-id="62f1f-115">Voer de volgende opdracht uit vanuit een PowerShell-sessie met verhoogde bevoegdheden:</span><span class="sxs-lookup"><span data-stu-id="62f1f-115">Run the following command from an elevated PowerShell session:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM
```

<span data-ttu-id="62f1f-116">PowerShell Gallery is standaard niet geconfigureerd als een vertrouwde opslagplaats voor PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="62f1f-116">By default, the PowerShell gallery is not configured as a Trusted repository for PowerShellGet.</span></span> <span data-ttu-id="62f1f-117">De eerste keer dat u PSGallery gebruikt, ziet u het volgende bericht:</span><span class="sxs-lookup"><span data-stu-id="62f1f-117">The first time you use the PSGallery you see the following prompt:</span></span>

```
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
```

<span data-ttu-id="62f1f-118">Antwoord Ja of Ja op alles om door te gaan met de installatie.</span><span class="sxs-lookup"><span data-stu-id="62f1f-118">Answer 'Yes' or 'Yes to All' to continue with the installation.</span></span>

> [!NOTE]
> <span data-ttu-id="62f1f-119">Als u een versie van NuGet hebt die ouder is dan 2.8.5.201, wordt u gevraagd om de meest recente versie van NuGet te downloaden en installeren.</span><span class="sxs-lookup"><span data-stu-id="62f1f-119">If you have a version older than 2.8.5.201 of NuGet, you are prompted to download and install the latest version of NuGet.</span></span>

<span data-ttu-id="62f1f-120">De AzureRM-module is een updatepakketmodule voor de Azure Resource Manager-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="62f1f-120">The AzureRM module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="62f1f-121">Als u de AzureRM-module installeert, wordt een niet eerder geïnstalleerde Azure PowerShell-module gedownload vanuit PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="62f1f-121">When you install the AzureRM module, any Azure PowerShell module not previously installed is downloaded and from the PowerShell Gallery.</span></span>

<span data-ttu-id="62f1f-122">Als er een eerdere versie van Azure PowerShell is geïnstalleerd, kunt u een foutmelding krijgen.</span><span class="sxs-lookup"><span data-stu-id="62f1f-122">If you have a previous version of Azure PowerShell installed you may receive an error.</span></span> <span data-ttu-id="62f1f-123">Zie de sectie [Bijwerken naar een nieuwe versie van Azure PowerShell](#update-azps) in dit artikel om dit probleem op te lossen.</span><span class="sxs-lookup"><span data-stu-id="62f1f-123">To resolve this issue, see the [Updating to a new version of Azure PowerShell](#update-azps) section of this article.</span></span>

## <span data-ttu-id="62f1f-124">Stap 3: de AzureRM-module laden</span><span class="sxs-lookup"><span data-stu-id="62f1f-124">Step 3: Load the AzureRM module</span></span>
<a id="step-3-load-the-azurerm-module" class="xliff"></a>
<span data-ttu-id="62f1f-125">Nadat de module is geïnstalleerd, moet u de module in uw PowerShell-sessie laden.</span><span class="sxs-lookup"><span data-stu-id="62f1f-125">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="62f1f-126">Doe dit tijdens een normale (niet-verhoogde) PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="62f1f-126">You should do this in a normal (non-elevated) PowerShell session.</span></span> <span data-ttu-id="62f1f-127">Modules worden geladen door de cmdlet `Import-Module` als volgt te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="62f1f-127">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM
```

## <span data-ttu-id="62f1f-128">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="62f1f-128">Next Steps</span></span>
<a id="next-steps" class="xliff"></a>

<span data-ttu-id="62f1f-129">Zie de volgende artikelen voor meer informatie over het gebruik van Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="62f1f-129">For more information about using Azure PowerShell, see the following articles:</span></span>

* [<span data-ttu-id="62f1f-130">Aan de slag met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="62f1f-130">Get started with Azure PowerShell</span></span>](get-started-azureps.md)

## <span data-ttu-id="62f1f-131">Problemen melden en feedback geven</span><span class="sxs-lookup"><span data-stu-id="62f1f-131">Reporting issues and feedback</span></span>
<a id="reporting-issues-and-feedback" class="xliff"></a>

<span data-ttu-id="62f1f-132">Als er fouten optreden bij het gebruik van het hulpprogramma, kunt u dit melden via de sectie [Issues](https://github.com/Azure/azure-powershell/issues) van onze GitHub-repo.</span><span class="sxs-lookup"><span data-stu-id="62f1f-132">If you encounter any bugs with the tool, file an issue in the [Issues](https://github.com/Azure/azure-powershell/issues) section of our GitHub repo.</span></span> <span data-ttu-id="62f1f-133">Als u feedback wilt geven vanaf de opdrachtregel, gebruikt u de cmdlet `Send-Feedback`.</span><span class="sxs-lookup"><span data-stu-id="62f1f-133">To provide feedback from the command line, use the `Send-Feedback` cmdlet.</span></span>

## <span data-ttu-id="62f1f-134">Veelgestelde vragen</span><span class="sxs-lookup"><span data-stu-id="62f1f-134">Frequently asked questions</span></span>
<a id="frequently-asked-questions" class="xliff"></a>

### <span data-ttu-id="62f1f-135">PowerShellGet ophalen</span><span class="sxs-lookup"><span data-stu-id="62f1f-135">How to get PowerShellGet</span></span>
<a id="how-to-get-powershellget" class="xliff"></a>

|<span data-ttu-id="62f1f-136">Versie van het besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="62f1f-136">OS Version</span></span>|<span data-ttu-id="62f1f-137">Installatie-instructies</span><span class="sxs-lookup"><span data-stu-id="62f1f-137">Install instructions</span></span>|
|---|---|
|<span data-ttu-id="62f1f-138">Ik heb Windows 10 of Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="62f1f-138">I have Windows 10 or Windows Server 2016</span></span>|<span data-ttu-id="62f1f-139">Ingebouwd in Windows Management Framework 5.0 (WMF), dat is opgenomen in het besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="62f1f-139">Built into Windows Management Framework (WMF) 5.0 included in the OS</span></span>|
|<span data-ttu-id="62f1f-140">Ik wil een upgrade naar PowerShell 5 uitvoeren</span><span class="sxs-lookup"><span data-stu-id="62f1f-140">I want to upgrade to PowerShell 5</span></span>|[<span data-ttu-id="62f1f-141">Installeer de meest recente versie van WMF</span><span class="sxs-lookup"><span data-stu-id="62f1f-141">Install the latest version of WMF</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)|
|<span data-ttu-id="62f1f-142">Ik heb een versie van Windows met PowerShell 3 of PowerShell 4</span><span class="sxs-lookup"><span data-stu-id="62f1f-142">I am running on a version of Windows with PowerShell 3 or PowerShell 4</span></span>|[<span data-ttu-id="62f1f-143">Haal de PackageManagement-modules op</span><span class="sxs-lookup"><span data-stu-id="62f1f-143">Get the PackageManagement modules</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217)|

<a id="helpmechoose"></a>
### <span data-ttu-id="62f1f-144">De versie van Azure PowerShell controleren</span><span class="sxs-lookup"><span data-stu-id="62f1f-144">Checking the version of Azure PowerShell</span></span>
<a id="checking-the-version-of-azure-powershell" class="xliff"></a>

<span data-ttu-id="62f1f-145">Hoewel we u aanraden om zo snel mogelijk een upgrade naar de meest recente versie uit te voeren, worden er meerdere versies van Azure PowerShell ondersteund.</span><span class="sxs-lookup"><span data-stu-id="62f1f-145">Although we encourage you to upgrade to the latest version as early as possible, several versions of Azure PowerShell are support.</span></span> <span data-ttu-id="62f1f-146">Voer `Get-Module AzureRM` vanaf de opdrachtregel uit om te bepalen welke versie van Azure PowerShell er op uw systeem is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="62f1f-146">To determine the version of Azure PowerShell you have installed, run `Get-Module AzureRM` from your command line.</span></span>

```powershell
Get-Module AzureRM -list | Select-Object Name,Version,Path
```

### <span data-ttu-id="62f1f-147">Ondersteuning voor klassieke implementatiemethoden</span><span class="sxs-lookup"><span data-stu-id="62f1f-147">Support for classic deployment methods</span></span>
<a id="support-for-classic-deployment-methods" class="xliff"></a>

<span data-ttu-id="62f1f-148">Als u implementaties hebt die het klassieke implementatiemodel volgen, kunt u de Service Management-versie van Azure PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="62f1f-148">If you have deployments that use the classic deployment model you can install the Service Management version of Azure PowerShell.</span></span> <span data-ttu-id="62f1f-149">Zie [Installing the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps) (De Azure PowerShell Service Management-module installeren) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="62f1f-149">For more information, see [Install the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps).</span></span> <span data-ttu-id="62f1f-150">De Azure- en AzureRM-modules delen algemene afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="62f1f-150">The Azure and AzureRM modules share common dependencies.</span></span> <span data-ttu-id="62f1f-151">Als u zowel de Azure- als de AzureRM-module gebruikt, moet u dezelfde versie van elk pakket installeren.</span><span class="sxs-lookup"><span data-stu-id="62f1f-151">If you use both the Azure and AzureRM modules, you should install the same version of each package.</span></span>

### <span data-ttu-id="62f1f-152"><a id="update-azps"></a>Bijwerken naar een nieuwe versie van Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="62f1f-152"><a id="update-azps"></a>Updating to a new version of Azure PowerShell</span></span>

<span data-ttu-id="62f1f-153">Als er een eerdere versie van Azure PowerShell is geïnstalleerd, met de module Service Management, kunt u de volgende foutmelding krijgen:</span><span class="sxs-lookup"><span data-stu-id="62f1f-153">If you have a previous version of Azure PowerShell installed that includes the Service Management module, you may receive the following error:</span></span>

```
PackageManagement\Install-Package : A command with name 'Get-AzureStorageContainerAcl' is already
available on this system. This module 'Azure.Storage' may override the existing commands. If you
still want to install this module 'Azure.Storage', use -AllowClobber parameter.

At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1772 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
    + FullyQualifiedErrorId : CommandAlreadyAvailable,Validate-ModuleCommandAlreadyAvailable,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

<span data-ttu-id="62f1f-154">Zoals in de foutmelding wordt aangegeven, moet u de parameter -AllowClobber gebruiken om de module te installeren.</span><span class="sxs-lookup"><span data-stu-id="62f1f-154">As the error message states, you need to use the -AllowClobber parameter to install the module.</span></span> <span data-ttu-id="62f1f-155">Gebruik de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="62f1f-155">Use the following command:</span></span>

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module AzureRM -AllowClobber
```

<span data-ttu-id="62f1f-156">Zie het Help-onderwerp voor [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="62f1f-156">For more information, see the help topic for [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module).</span></span>

### <span data-ttu-id="62f1f-157">Moduleversies naast elkaar installeren</span><span class="sxs-lookup"><span data-stu-id="62f1f-157">Installing module versions side by side</span></span>
<a id="installing-module-versions-side-by-side" class="xliff"></a>

<span data-ttu-id="62f1f-158">De PowerShellGet-installatiemethode is de enige methode die ondersteuning biedt voor de installatie van meerdere versies.</span><span class="sxs-lookup"><span data-stu-id="62f1f-158">The PowerShellGet method of installation is the only method that supports the installation of multiple versions.</span></span> <span data-ttu-id="62f1f-159">U hebt bijvoorbeeld scripts die zijn geschreven met behulp van een eerdere versie van Azure PowerShell, maar onvoldoende tijd of resources om ze bij te werken.</span><span class="sxs-lookup"><span data-stu-id="62f1f-159">For example, you may have scripts written using a previous version of Azure PowerShell that you don't have the time or resources to updated.</span></span> <span data-ttu-id="62f1f-160">De volgende opdrachten laten zien hoe u meerdere versies van Azure PowerShell installeert:</span><span class="sxs-lookup"><span data-stu-id="62f1f-160">The following commands illustrate how to install multiple versions of Azure PowerShell:</span></span>

```powershell
Install-Module -Name AzureRM -RequiredVersion 3.7.0
Install-Module -Name AzureRM -RequiredVersion 1.2.9
```

<span data-ttu-id="62f1f-161">Slechts één versie van de module kan in een PowerShell-sessie worden geladen.</span><span class="sxs-lookup"><span data-stu-id="62f1f-161">Only one version of the module can be loaded in a PowerShell session.</span></span> <span data-ttu-id="62f1f-162">U moet een nieuw PowerShell-venster openen en `Import-Module` gebruiken om een specifieke versie van de AzureRM-cmdlets te importeren:</span><span class="sxs-lookup"><span data-stu-id="62f1f-162">You must open a new PowerShell window and use `Import-Module` to import a specific version of the AzureRM cmdlets:</span></span>

```powershell
Import-Module AzureRM -RequiredVersion 1.2.9
```

> [!NOTE]
> <span data-ttu-id="62f1f-163">Versie 2.1.0 en versie 1.2.6 zijn de eerste moduleversies die zijn ontworpen om naast elkaar te worden geïnstalleerd en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="62f1f-163">Version 2.1.0 and version 1.2.6 are the first module versions designed to be installed and used side by side.</span></span> <span data-ttu-id="62f1f-164">Bij het laden van een eerdere versie van de Azure PowerShell worden incompatibele versies van de module **AzureRM.Profile** geladen.</span><span class="sxs-lookup"><span data-stu-id="62f1f-164">When loading an earlier version of the Azure PowerShell, incompatible versions of the **AzureRM.Profile** module are loaded.</span></span> <span data-ttu-id="62f1f-165">Dit leidt ertoe dat u wordt gevraagd u aan te melden telkens als u een cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="62f1f-165">This results in the cmdlets prompting you to log in whenever you execute a cmdlet.</span></span>

### <span data-ttu-id="62f1f-166">Andere installatiemethoden</span><span class="sxs-lookup"><span data-stu-id="62f1f-166">Other installation methods</span></span>
<a id="other-installation-methods" class="xliff"></a>

<span data-ttu-id="62f1f-167">Zie [Andere installatiemethoden](other-install.md) voor meer informatie over installatie met het webplatforminstallatieprogramma of het MSI-pakket</span><span class="sxs-lookup"><span data-stu-id="62f1f-167">For information about installing using the Web Platform Installer or the MSI Package, see [Other installation methods](other-install.md)</span></span>
