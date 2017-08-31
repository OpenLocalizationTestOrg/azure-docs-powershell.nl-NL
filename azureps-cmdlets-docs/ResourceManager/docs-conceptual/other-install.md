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
ms.openlocfilehash: 9cee582f74b7f3260c6ae167a8ac358d360ad8ab
ms.sourcegitcommit: 45587b5091293288e16cfae8ac412e0d42f8f450
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/15/2017
---
# <a name="other-installation-methods"></a><span data-ttu-id="7638c-103">Andere installatiemethoden</span><span class="sxs-lookup"><span data-stu-id="7638c-103">Other installation methods</span></span>

<span data-ttu-id="7638c-104">Azure PowerShell kent meerdere installatiemethoden.</span><span class="sxs-lookup"><span data-stu-id="7638c-104">Azure PowerShell has multiple installation methods.</span></span> <span data-ttu-id="7638c-105">Het gebruik van PowerShellGet met PowerShell Gallery verdient de voorkeur.</span><span class="sxs-lookup"><span data-stu-id="7638c-105">Using PowerShellGet with the PowerShell Gallery is the preferred method.</span></span> <span data-ttu-id="7638c-106">Azure PowerShell kan worden geïnstalleerd met het webplatforminstallatieprogramma (WebPI) of met het MSI-bestand dat beschikbaar is via [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="7638c-106">Azure PowerShell can be installed using the Web Platform Installer (WebPI) or by using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span>

## <a name="docker"></a><span data-ttu-id="7638c-107">Docker</span><span class="sxs-lookup"><span data-stu-id="7638c-107">Docker</span></span>

<span data-ttu-id="7638c-108">We onderhouden een Docker-installatiekopie die vooraf is geconfigureerd met Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7638c-108">We maintain a Docker image preconfigured with Azure PowerShell.</span></span>

<span data-ttu-id="7638c-109">Voer de container uit met `docker run`.</span><span class="sxs-lookup"><span data-stu-id="7638c-109">Run the container with `docker run`.</span></span>

```powershell
docker run azuresdk/azure-powershell
```

<span data-ttu-id="7638c-110">Bovendien onderhouden we een subset cmdlets als een PowerShell Core-container.</span><span class="sxs-lookup"><span data-stu-id="7638c-110">In addition, we maintain a subset of cmdlets as a PowerShell Core container.</span></span>

<span data-ttu-id="7638c-111">Voor Mac/Linux gebruikt u de installatiekopie `latest`.</span><span class="sxs-lookup"><span data-stu-id="7638c-111">For Mac/Linux, use the `latest` image.</span></span>

```bash
docker run azuresdk/azure-powershell-core:latest
```

<span data-ttu-id="7638c-112">Voor Windows gebruikt u de installatiekopie `nanoserver`.</span><span class="sxs-lookup"><span data-stu-id="7638c-112">For Windows, use the `nanoserver` image.</span></span>

```powershell
docker run azuresdk/azure-powershell-core:nanoserver
```

<span data-ttu-id="7638c-113">Azure PowerShell wordt geïnstalleerd in de installatiekopie met behulp van `Install-Module` uit de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="7638c-113">Azure PowerShell is installed on the image via `Install-Module` from the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

## <a name="install-using-the-web-platform-installer"></a><span data-ttu-id="7638c-114">Installeren met het webplatforminstallatieprogramma</span><span class="sxs-lookup"><span data-stu-id="7638c-114">Install using the Web Platform Installer</span></span>

<span data-ttu-id="7638c-115">Het installeren van de nieuwste versie van Azure PowerShell met WebPI gaat op dezelfde manier als bij vorige versies.</span><span class="sxs-lookup"><span data-stu-id="7638c-115">Installing the latest Azure PowerShell from WebPI is the same as it was for previous versions.</span></span>
<span data-ttu-id="7638c-116">Download het [Azure PowerShell WebPI-pakket](http://aka.ms/webpi-azps) en start de installatie.</span><span class="sxs-lookup"><span data-stu-id="7638c-116">Download the [Azure PowerShell WebPI package](http://aka.ms/webpi-azps) and start the install.</span></span>

> [!NOTE]
> <span data-ttu-id="7638c-117">Als u eerder Azure-modules hebt geïnstalleerd vanuit PowerShell Gallery, worden deze automatisch door het installatieprogramma verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7638c-117">If you have previously installed Azure modules from the PowerShell Gallery, the installer automatically removes them.</span></span> <span data-ttu-id="7638c-118">Dit maakt uw omgeving eenvoudiger door ervoor te zorgen dat er slechts één versie van Azure PowerShell is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7638c-118">This simplifies your environment by ensuring that only one version of Azure PowerShell is installed.</span></span> <span data-ttu-id="7638c-119">Er zijn echter scenario's denkbaar waarin het gewenst is dat er meerdere versies tegelijkertijd zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7638c-119">However, there are scenarios where you may need multiple versions installed at the same time.</span></span>
>
> <span data-ttu-id="7638c-120">Met PowerShell Gallery-modules worden modules geïnstalleerd in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="7638c-120">PowerShell Gallery modules install modules in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="7638c-121">Met het WebPI-installatieprogramma worden daarentegen Azure-modules geïnstalleerd in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="7638c-121">In contrast, the WebPI installer installs the Azure modules in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span></span>
>
> <span data-ttu-id="7638c-122">Als er tijdens de installatie een fout optreedt, kunt u handmatig de Azure*-mappen in de map `$env:ProgramFiles\WindowsPowerShell\Modules` verwijderen en de installatie opnieuw uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="7638c-122">If an error occurs during install, you can manually remove the Azure* folders in your `$env:ProgramFiles\WindowsPowerShell\Modules` folder, and try the installation again.</span></span>

<span data-ttu-id="7638c-123">Nadat de installatie is voltooid, moet uw instelling `$env:PSModulePath` de mappen bevatten waarin zich de Azure PowerShell-cmdlets bevinden.</span><span class="sxs-lookup"><span data-stu-id="7638c-123">Once the installation completes, your `$env:PSModulePath` setting should include the directories containing the Azure PowerShell cmdlets.</span></span> <span data-ttu-id="7638c-124">De volgende opdracht kan worden gebruikt om te controleren of Azure PowerShell juist is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7638c-124">The following command can be used to verify that the Azure PowerShell is installed properly.</span></span>

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> <span data-ttu-id="7638c-125">Er is een bekend probleem dat zich kan voordoen bij het installeren met WebPI.</span><span class="sxs-lookup"><span data-stu-id="7638c-125">There is a known issue that can occur when installing from WebPI.</span></span> <span data-ttu-id="7638c-126">Als de computer opnieuw moet worden opgestart vanwege systeemupdates of andere installaties, kan dit ertoe leiden dat tijdens het bijwerken van `$env:PSModulePath` het pad waar Azure PowerShell is geïnstalleerd, niet kan worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="7638c-126">If your computer requires a restart due to system updates or other installations, it may cause updates to `$env:PSModulePath` to fail to include the path where Azure PowerShell is installed.</span></span>

<span data-ttu-id="7638c-127">Wanneer u na een installatie cmdlets laadt of uitvoert, kunt u het volgende foutbericht ontvangen:</span><span class="sxs-lookup"><span data-stu-id="7638c-127">When attempting to load or execute cmdlets after installation, you can receive the following error message:</span></span>

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

<span data-ttu-id="7638c-128">Deze fout kan worden gecorrigeerd door de machine opnieuw op te starten of door de module te importeren en daarbij het volledig pad te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7638c-128">This error can be corrected by restarting the machine or importing the module using the fully qualified path.</span></span> <span data-ttu-id="7638c-129">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7638c-129">For example:</span></span>

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <a name="install-using-the-msi-package"></a><span data-ttu-id="7638c-130">Installeren met het MSI-pakket</span><span class="sxs-lookup"><span data-stu-id="7638c-130">Install using the MSI Package</span></span>

<span data-ttu-id="7638c-131">Azure PowerShell kan worden geïnstalleerd met het MSI-bestand dat beschikbaar is via [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="7638c-131">Azure PowerShell can be installed using the MSI file available from [GitHub](https://github.com/Azure/azure-powershell/releases/latest).</span></span> <span data-ttu-id="7638c-132">Als u vorige versies van Azure-modules hebt geïnstalleerd, worden deze automatisch door het installatieprogramma verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7638c-132">If you have installed previous versions of Azure modules, the installer automatically removes them.</span></span> <span data-ttu-id="7638c-133">Met het MSI-pakket worden er modules in `$env:ProgramFiles\WindowsPowerShell\Modules` geïnstalleerd, maar worden er geen mappen voor specifieke versies gemaakt.</span><span class="sxs-lookup"><span data-stu-id="7638c-133">The MSI package installs modules in `$env:ProgramFiles\WindowsPowerShell\Modules` but does not create version-specific folders.</span></span>
