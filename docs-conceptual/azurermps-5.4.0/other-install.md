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
ms.date: 09/06/2017
ms.openlocfilehash: 8a88cce312b4cca002c342c04e1f97b966ae3d2f
ms.sourcegitcommit: 5fe9a579d2e0d1cb5a05aadaeba5db784f1b18fa
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/28/2018
---
# <a name="other-installation-methods"></a><span data-ttu-id="a1255-103">Andere installatiemethoden</span><span class="sxs-lookup"><span data-stu-id="a1255-103">Other installation methods</span></span>

<span data-ttu-id="a1255-104">Azure PowerShell kent meerdere installatiemethoden.</span><span class="sxs-lookup"><span data-stu-id="a1255-104">Azure PowerShell has multiple installation methods.</span></span> <span data-ttu-id="a1255-105">Het gebruik van PowerShellGet met PowerShell Gallery verdient de voorkeur.</span><span class="sxs-lookup"><span data-stu-id="a1255-105">Using PowerShellGet with the PowerShell Gallery is the preferred method.</span></span> <span data-ttu-id="a1255-106">Azure PowerShell kan in Windows worden geïnstalleerd met het webplatforminstallatieprogramma (WebPI) of met het MSI-bestand dat beschikbaar is via GitHub.</span><span class="sxs-lookup"><span data-stu-id="a1255-106">Azure PowerShell can be installed on Windows using the Web Platform Installer (WebPI) or by using the MSI file available from GitHub.</span></span> <span data-ttu-id="a1255-107">Azure PowerShell kan ook worden geïnstalleerd in een Docker-container.</span><span class="sxs-lookup"><span data-stu-id="a1255-107">Azure PowerShell can also be installed in a Docker container.</span></span>

## <a name="install-on-windows-using-the-web-platform-installer"></a><span data-ttu-id="a1255-108">In Windows installeren met het webplatforminstallatieprogramma</span><span class="sxs-lookup"><span data-stu-id="a1255-108">Install on Windows using the Web Platform Installer</span></span>

<span data-ttu-id="a1255-109">Het installeren van de nieuwste versie van Azure PowerShell met WebPI gaat op dezelfde manier als bij vorige versies.</span><span class="sxs-lookup"><span data-stu-id="a1255-109">Installing the latest Azure PowerShell from WebPI is the same as it was for previous versions.</span></span>
<span data-ttu-id="a1255-110">Download het [Azure PowerShell WebPI-pakket](http://aka.ms/webpi-azps) en start de installatie.</span><span class="sxs-lookup"><span data-stu-id="a1255-110">Download the [Azure PowerShell WebPI package](http://aka.ms/webpi-azps) and start the install.</span></span>

> [!NOTE]
> <span data-ttu-id="a1255-111">Als u eerder Azure-modules hebt geïnstalleerd vanuit PowerShell Gallery, worden deze automatisch door het installatieprogramma verwijderd.</span><span class="sxs-lookup"><span data-stu-id="a1255-111">If you have previously installed Azure modules from the PowerShell Gallery, the installer automatically removes them.</span></span> <span data-ttu-id="a1255-112">Dit maakt uw omgeving eenvoudiger door ervoor te zorgen dat er slechts één versie van Azure PowerShell is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a1255-112">This simplifies your environment by ensuring that only one version of Azure PowerShell is installed.</span></span> <span data-ttu-id="a1255-113">Er zijn echter scenario's denkbaar waarin het gewenst is dat er meerdere versies tegelijkertijd zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a1255-113">However, there are scenarios where you may need multiple versions installed at the same time.</span></span>
>
> <span data-ttu-id="a1255-114">Met PowerShell Gallery-modules worden modules geïnstalleerd in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="a1255-114">PowerShell Gallery modules install modules in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="a1255-115">Met het WebPI-installatieprogramma worden daarentegen Azure-modules geïnstalleerd in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="a1255-115">In contrast, the WebPI installer installs the Azure modules in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.</span></span>
>
> <span data-ttu-id="a1255-116">Als er tijdens de installatie een fout optreedt, kunt u handmatig de Azure\*-mappen in de map `$env:ProgramFiles\WindowsPowerShell\Modules` verwijderen en de installatie opnieuw uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a1255-116">If an error occurs during install, you can manually remove the Azure\* folders in your `$env:ProgramFiles\WindowsPowerShell\Modules` folder, and try the installation again.</span></span>

<span data-ttu-id="a1255-117">Nadat de installatie is voltooid, moet uw instelling `$env:PSModulePath` de mappen bevatten waarin zich de Azure PowerShell-cmdlets bevinden.</span><span class="sxs-lookup"><span data-stu-id="a1255-117">Once the installation completes, your `$env:PSModulePath` setting should include the directories containing the Azure PowerShell cmdlets.</span></span> <span data-ttu-id="a1255-118">De volgende opdracht kan worden gebruikt om te controleren of Azure PowerShell juist is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a1255-118">The following command can be used to verify that the Azure PowerShell is installed properly.</span></span>

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> <span data-ttu-id="a1255-119">Er is een bekend probleem dat zich kan voordoen bij het installeren met WebPI.</span><span class="sxs-lookup"><span data-stu-id="a1255-119">There is a known issue that can occur when installing from WebPI.</span></span> <span data-ttu-id="a1255-120">Als de computer opnieuw moet worden opgestart vanwege systeemupdates of andere installaties, kan dit ertoe leiden dat tijdens het bijwerken van `$env:PSModulePath` het pad waar Azure PowerShell is geïnstalleerd, niet kan worden opgenomen.</span><span class="sxs-lookup"><span data-stu-id="a1255-120">If your computer requires a restart due to system updates or other installations, it may cause updates to `$env:PSModulePath` to fail to include the path where Azure PowerShell is installed.</span></span>

<span data-ttu-id="a1255-121">Wanneer u na een installatie cmdlets laadt of uitvoert, kunt u het volgende foutbericht ontvangen:</span><span class="sxs-lookup"><span data-stu-id="a1255-121">When attempting to load or execute cmdlets after installation, you can receive the following error message:</span></span>

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

<span data-ttu-id="a1255-122">Deze fout kan worden gecorrigeerd door de machine opnieuw op te starten of door de module te importeren en daarbij het volledig pad te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a1255-122">This error can be corrected by restarting the machine or importing the module using the fully qualified path.</span></span> <span data-ttu-id="a1255-123">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a1255-123">For example:</span></span>

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <a name="install-on-windows-using-the-msi-package"></a><span data-ttu-id="a1255-124">In Windows installeren met het MSI-pakket</span><span class="sxs-lookup"><span data-stu-id="a1255-124">Install on Windows using the MSI Package</span></span>

<span data-ttu-id="a1255-125">Azure PowerShell kan worden geïnstalleerd met het MSI-bestand dat beschikbaar is via [GitHub](https://aka.ms/azps-release).</span><span class="sxs-lookup"><span data-stu-id="a1255-125">Azure PowerShell can be installed using the MSI file available from [GitHub](https://aka.ms/azps-release).</span></span> <span data-ttu-id="a1255-126">Als u vorige versies van Azure-modules hebt geïnstalleerd, worden deze automatisch door het installatieprogramma verwijderd.</span><span class="sxs-lookup"><span data-stu-id="a1255-126">If you have installed previous versions of Azure modules, the installer automatically removes them.</span></span> <span data-ttu-id="a1255-127">Met het MSI-pakket worden er modules in `$env:ProgramFiles\WindowsPowerShell\Modules` geïnstalleerd, maar worden er geen mappen voor specifieke versies gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a1255-127">The MSI package installs modules in `$env:ProgramFiles\WindowsPowerShell\Modules` but does not create version-specific folders.</span></span>

## <a name="install-in-a-docker-container"></a><span data-ttu-id="a1255-128">Installeren in een Docker-container</span><span class="sxs-lookup"><span data-stu-id="a1255-128">Install in a Docker container</span></span>

<span data-ttu-id="a1255-129">We onderhouden een Docker-installatiekopie die vooraf is geconfigureerd met Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a1255-129">We maintain a Docker image preconfigured with Azure PowerShell.</span></span>

<span data-ttu-id="a1255-130">Voer de container uit met `docker run`.</span><span class="sxs-lookup"><span data-stu-id="a1255-130">Run the container with `docker run`.</span></span>

```powershell
docker run azuresdk/azure-powershell
```

<span data-ttu-id="a1255-131">Bovendien onderhouden we een subset cmdlets als een PowerShell Core-container.</span><span class="sxs-lookup"><span data-stu-id="a1255-131">In addition, we maintain a subset of cmdlets as a PowerShell Core container.</span></span>

<span data-ttu-id="a1255-132">Voor Mac/Linux gebruikt u de installatiekopie `latest`.</span><span class="sxs-lookup"><span data-stu-id="a1255-132">For Mac/Linux, use the `latest` image.</span></span>

```bash
docker run azuresdk/azure-powershell-core:latest
```

<span data-ttu-id="a1255-133">Voor Windows gebruikt u de installatiekopie `nanoserver`.</span><span class="sxs-lookup"><span data-stu-id="a1255-133">For Windows, use the `nanoserver` image.</span></span>

```powershell
docker run azuresdk/azure-powershell-core:nanoserver
```

<span data-ttu-id="a1255-134">Azure PowerShell wordt geïnstalleerd in de installatiekopie met behulp van `Install-Module` uit de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="a1255-134">Azure PowerShell is installed on the image via `Install-Module` from the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
