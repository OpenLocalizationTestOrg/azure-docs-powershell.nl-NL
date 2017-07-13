---
title: Andere manieren om Azure PowerShell te installeren | Microsoft Docs
description: Azure PowerShell installeren met het MSI-pakket of het webplatforminstallatieprogramma.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 05/15/2017
ms.openlocfilehash: 368404bcb5218814b4965bb1bcda1e2876441d2a
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="17ab1-103">Andere installatiemethoden</span><span class="sxs-lookup"><span data-stu-id="17ab1-103">Other installation methods</span></span>
<a id="other-installation-methods" class="xliff"></a>

<span data-ttu-id="17ab1-104">Azure PowerShell kent meerdere installatiemethoden.</span><span class="sxs-lookup"><span data-stu-id="17ab1-104">Azure PowerShell has multiple installation methods.</span></span> <span data-ttu-id="17ab1-105">Het gebruik van PowerShellGet met PowerShell Gallery verdient de voorkeur.</span><span class="sxs-lookup"><span data-stu-id="17ab1-105">Using PowerShellGet with the PowerShell Gallery is the preferred method.</span></span> <span data-ttu-id="17ab1-106">Azure PowerShell kan worden geïnstalleerd met het webplatforminstallatieprogramma (WebPI) of met het MSI-bestand dat beschikbaar is via [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="17ab1-106">Azure PowerShell can be installed using the Web Platform Installer (WebPI) or by using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span>

## <span data-ttu-id="17ab1-107">Installeren met het webplatforminstallatieprogramma</span><span class="sxs-lookup"><span data-stu-id="17ab1-107">Install using the Web Platform Installer</span></span>
<a id="install-using-the-web-platform-installer" class="xliff"></a>

<span data-ttu-id="17ab1-108">Het installeren van de nieuwste versie van Azure PowerShell met WebPI gaat op dezelfde manier als bij vorige versies.</span><span class="sxs-lookup"><span data-stu-id="17ab1-108">Installing the latest Azure PowerShell from WebPI is the same as it was for previous versions.</span></span>
<span data-ttu-id="17ab1-109">Download het [Azure PowerShell WebPI-pakket](http://aka.ms/webpi-azps) en start de installatie.</span><span class="sxs-lookup"><span data-stu-id="17ab1-109">Download the [Azure PowerShell WebPI package](http://aka.ms/webpi-azps) and start the install.</span></span>

> [!NOTE]
> <span data-ttu-id="17ab1-110">Als u eerder Azure-modules hebt geïnstalleerd vanuit PowerShell Gallery, worden deze automatisch door het installatieprogramma verwijderd.</span><span class="sxs-lookup"><span data-stu-id="17ab1-110">If you have previously installed Azure modules from the PowerShell Gallery, the installer automatically removes them.</span></span> <span data-ttu-id="17ab1-111">Dit maakt uw omgeving eenvoudiger door ervoor te zorgen dat er slechts één versie van Azure PowerShell is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="17ab1-111">This simplifies your environment by ensuring that only one version of Azure PowerShell is installed.</span></span> <span data-ttu-id="17ab1-112">Er zijn echter scenario's denkbaar waarin het gewenst is dat er meerdere versies tegelijkertijd zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="17ab1-112">However, there are scenarios where you may need multiple versions installed at the same time.</span></span>
>
> <span data-ttu-id="17ab1-113">Met PowerShell Gallery-modules worden modules geïnstalleerd in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="17ab1-113">PowerShell Gallery modules install modules in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="17ab1-114">Met het WebPI-installatieprogramma worden daarentegen Azure-modules geïnstalleerd in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="17ab1-114">In contrast, the WebPI installer installs the Azure modules in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span></span>
>
> <span data-ttu-id="17ab1-115">Als er tijdens de installatie een fout optreedt, kunt u handmatig de Azure*-mappen in de map `$env:ProgramFiles\WindowsPowerShell\Modules` verwijderen en de installatie opnieuw uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="17ab1-115">If an error occurs during install, you can manually remove the Azure* folders in your `$env:ProgramFiles\WindowsPowerShell\Modules` folder, and try the installation again.</span></span>

<span data-ttu-id="17ab1-116">Nadat de installatie is voltooid, moet uw instelling `$env:PSModulePath` de mappen bevatten waarin zich de Azure PowerShell-cmdlets bevinden.</span><span class="sxs-lookup"><span data-stu-id="17ab1-116">Once the installation completes, your `$env:PSModulePath` setting should include the directories containing the Azure PowerShell cmdlets.</span></span> <span data-ttu-id="17ab1-117">De volgende opdracht kan worden gebruikt om te controleren of Azure PowerShell juist is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="17ab1-117">The following command can be used to verify that the Azure PowerShell is installed properly.</span></span>

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> <span data-ttu-id="17ab1-118">Er is een bekend probleem dat zich kan voordoen bij het installeren met WebPI.</span><span class="sxs-lookup"><span data-stu-id="17ab1-118">There is a known issue that can occur when installing from WebPI.</span></span> <span data-ttu-id="17ab1-119">Als de computer opnieuw moet worden opgestart vanwege systeemupdates of andere installaties, kan dit ertoe leiden dat tijdens het bijwerken van `$env:PSModulePath` het pad waar Azure PowerShell is geïnstalleerd, niet kan worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="17ab1-119">If your computer requires a restart due to system updates or other installations, it may cause updates to `$env:PSModulePath` to fail to include the path where Azure PowerShell is installed.</span></span>

<span data-ttu-id="17ab1-120">Wanneer u na een installatie cmdlets laadt of uitvoert, kunt u het volgende foutbericht ontvangen:</span><span class="sxs-lookup"><span data-stu-id="17ab1-120">When attempting to load or execute cmdlets after installation, you can receive the following error message:</span></span>

```
PS C:\> Login-AzureRmAccount
Login-AzureRmAccount : The term 'Login-AzureRmAccount' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:1
+ Login-AzureRmAccount
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Login-AzureRmAccount:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="17ab1-121">Deze fout kan worden gecorrigeerd door de machine opnieuw op te starten of door de module te importeren en daarbij het volledig pad te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="17ab1-121">This error can be corrected by restarting the machine or importing the module using the fully qualified path.</span></span> <span data-ttu-id="17ab1-122">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="17ab1-122">For example:</span></span>

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <span data-ttu-id="17ab1-123">Installeren met het MSI-pakket</span><span class="sxs-lookup"><span data-stu-id="17ab1-123">Install using the MSI Package</span></span>
<a id="install-using-the-msi-package" class="xliff"></a>

<span data-ttu-id="17ab1-124">Azure PowerShell kan worden geïnstalleerd met het MSI-bestand dat beschikbaar is via [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="17ab1-124">Azure PowerShell can be installed using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span> <span data-ttu-id="17ab1-125">Als u vorige versies van Azure-modules hebt geïnstalleerd, worden deze automatisch door het installatieprogramma verwijderd.</span><span class="sxs-lookup"><span data-stu-id="17ab1-125">If you have installed previous versions of Azure modules, the installer automatically removes them.</span></span> <span data-ttu-id="17ab1-126">Met het MSI-pakket worden er modules in `$env:ProgramFiles\WindowsPowerShell\Modules` geïnstalleerd, maar worden er geen mappen voor specifieke versies gemaakt.</span><span class="sxs-lookup"><span data-stu-id="17ab1-126">The MSI package installs modules in `$env:ProgramFiles\WindowsPowerShell\Modules` but does not create version-specific folders.</span></span>
