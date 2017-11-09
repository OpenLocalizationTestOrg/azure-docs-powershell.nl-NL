---
title: De Azure PowerShell Service Management-module installeren en configureren | Microsoft Docs
description: Azure PowerShell voor het eerst installeren en configureren.
services: azure
author: sdwheeler
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/06/2017
ms.openlocfilehash: 164af369d49e3044e5409c28d8b6145ebc067313
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2017
---
# <a name="installing-the-azure-powershell-service-management-module"></a><span data-ttu-id="efe3a-103">De Azure PowerShell Service Management-module installeren</span><span class="sxs-lookup"><span data-stu-id="efe3a-103">Installing the Azure PowerShell Service Management module</span></span>

<span data-ttu-id="efe3a-104">Installatie van Azure PowerShell via de [PowerShell Gallery](https://www.powershellgallery.com/) heeft de voorkeur.</span><span class="sxs-lookup"><span data-stu-id="efe3a-104">Installing Azure PowerShell from the [PowerShell Gallery](https://www.powershellgallery.com/) is the preferred method of installation.</span></span>

## <a name="step-1-install-powershellget"></a><span data-ttu-id="efe3a-105">Stap 1: PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="efe3a-105">Step 1: Install PowerShellGet</span></span>

<span data-ttu-id="efe3a-106">Als u items uit de PowerShell Gallery wilt installeren, hebt u de PowerShellGet-module nodig.</span><span class="sxs-lookup"><span data-stu-id="efe3a-106">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="efe3a-107">Zorg ervoor dat u de juiste versie van PowerShellGet hebt en ook voldoet aan de overige systeemvereisten.</span><span class="sxs-lookup"><span data-stu-id="efe3a-107">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="efe3a-108">Voer de volgende opdracht uit om na te gaan of PowerShellGet op uw systeem is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="efe3a-108">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

<span data-ttu-id="efe3a-109">De uitvoer moet er ongeveer uitzien als hieronder is weergegeven:</span><span class="sxs-lookup"><span data-stu-id="efe3a-109">You should see something similar to the following output:</span></span>

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="efe3a-110">Zie [PowerShellGet ophalen](#how-to-get-powershellget) als PowerShellGet niet is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="efe3a-110">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](#how-to-get-powershellget).</span></span>

## <a name="step-2-install-azure-powershell"></a><span data-ttu-id="efe3a-111">Stap 2: Azure PowerShell installeren</span><span class="sxs-lookup"><span data-stu-id="efe3a-111">Step 2: Install Azure PowerShell</span></span>

<span data-ttu-id="efe3a-112">Voer de volgende opdracht uit vanuit de Windows PowerShell-console die als beheerder wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="efe3a-112">Run the following command from the Windows PowerShell console running as Administrator:</span></span>

```powershell
Install-Module Azure
```

<span data-ttu-id="efe3a-113">De Azure-module is een updatepakketmodule voor de Azure Resource Manager-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="efe3a-113">The Azure module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="efe3a-114">Wanneer u de AzureRM-module installeert, worden alle overige Azure-modules die niet eerder zijn geïnstalleerd, gedownload en geïnstalleerd vanuit de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="efe3a-114">When you install the AzureRM module, any other Azure modules that have not previously been installed will be downloaded and installed from the PowerShell Gallery.</span></span>

<span data-ttu-id="efe3a-115">De Azure Service Management-module deelt afhankelijkheden met de Azure PowerShell Resource Manager-modules.</span><span class="sxs-lookup"><span data-stu-id="efe3a-115">The Azure Service Management module shares dependencies with the Azure PowerShell Resource Manager modules.</span></span> <span data-ttu-id="efe3a-116">Als u de Azure PowerShell Resource Manager-modules hebt geïnstalleerd, moet u de parameter `-AllowClobber` aan de installatieopdracht toevoegen.</span><span class="sxs-lookup"><span data-stu-id="efe3a-116">If you have installed the Azure PowerShell Resource Manager modules, you will need to add the `-AllowClobber` parameter to the install command.</span></span> <span data-ttu-id="efe3a-117">Hiermee worden de huidige gedeelde afhankelijkheden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="efe3a-117">This allows this existing shared dependencies to be updated.</span></span> <span data-ttu-id="efe3a-118">Zonder deze parameter kan de module niet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="efe3a-118">Without this parameter, installation of the module fails.</span></span>

```powershell
Install-Module Azure -AllowClobber
```

<span data-ttu-id="efe3a-119">Nadat u deze module hebt geïnstalleerd, kunt u de module importeren door de volgende opdracht uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="efe3a-119">After you install this module, you can import the module by running the following command:</span></span>

```powershell
Import-Module Azure
```

## <a name="to-use-the-cmdlets"></a><span data-ttu-id="efe3a-120">De cmdlets gebruiken</span><span class="sxs-lookup"><span data-stu-id="efe3a-120">To use the cmdlets</span></span>

<span data-ttu-id="efe3a-121">Als u wilt gaan werken met de cmdlets van Azure Service Management, moet u zich eerst aanmelden bij uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="efe3a-121">To start working with the Azure Service Management cmdlets, first log on to your Azure account.</span></span> <span data-ttu-id="efe3a-122">Voer de volgende opdracht uit als u zich wilt aanmelden bij uw account:</span><span class="sxs-lookup"><span data-stu-id="efe3a-122">To log on to your account, run the following command:</span></span>

```powershell
Add-AzureAccount
```

<span data-ttu-id="efe3a-123">Nadat u zich bij Azure hebt aangemeld, maakt Azure PowerShell een context voor de opgegeven sessie.</span><span class="sxs-lookup"><span data-stu-id="efe3a-123">After logging into Azure, Azure PowerShell creates a context for the given session.</span></span> <span data-ttu-id="efe3a-124">Die context bevat de Azure PowerShell-omgeving, het account, de tenant en het abonnement die worden gebruikt voor alle cmdlets binnen de betreffende sessie.</span><span class="sxs-lookup"><span data-stu-id="efe3a-124">That context contains the Azure PowerShell environment, account, tenant, and subscription that will be used for all cmdlets within that session.</span></span> <span data-ttu-id="efe3a-125">U bent nu klaar om de onderstaande modules te gaan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="efe3a-125">Now you are ready to use the modules below.</span></span>

## <a name="azure-service-management-cmdlets"></a><span data-ttu-id="efe3a-126">Cmdlets van Azure Service Management</span><span class="sxs-lookup"><span data-stu-id="efe3a-126">Azure Service Management cmdlets</span></span>

<span data-ttu-id="efe3a-127">Azure PowerShell-modules worden regelmatig bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="efe3a-127">Azure PowerShell modules are updated frequently.</span></span> <span data-ttu-id="efe3a-128">Als u merkt dat de online Help bij de cmdlet betrekking heeft op cmdlets of parameters die zich niet in uw module bevinden, moet u de nieuwste versie van de module downloaden en installeren.</span><span class="sxs-lookup"><span data-stu-id="efe3a-128">If you notice that the online cmdlet help includes cmdlets or parameters that are not in your module, download and install the latest version of the module.</span></span> <span data-ttu-id="efe3a-129">Als wilt weten wat de versie van uw module is, typt u: `(Get-Module Azure).Version`.</span><span class="sxs-lookup"><span data-stu-id="efe3a-129">To find the version of your module, type: `(Get-Module Azure).Version`.</span></span>

<span data-ttu-id="efe3a-130">Als u op zoek bent naar voorbeeldscripts waarmee u een aantal veelvoorkomende taken in Azure kunt automatiseren, kunt u het [Scriptcentrum van Windows Azure](http://www.windowsazure.com/documentation/scripts/) raadplegen.</span><span class="sxs-lookup"><span data-stu-id="efe3a-130">For sample scripts that can help you automate some of the common tasks in Azure, see the [Windows Azure Script Center](http://www.windowsazure.com/documentation/scripts/).</span></span>

<span data-ttu-id="efe3a-131">Zie [Scripting with Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210) (Werken met scripts in Windows PowerShell) voor algemene informatie over hoe u Windows PowerShell installeert en aanpast, ermee werkt en er meer over leert.</span><span class="sxs-lookup"><span data-stu-id="efe3a-131">For general information about installing, learning, using, and customizing Windows PowerShell, see [Scripting with Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210).</span></span>

### <a name="how-to-get-powershellget"></a><span data-ttu-id="efe3a-132">PowerShellGet ophalen</span><span class="sxs-lookup"><span data-stu-id="efe3a-132">How to get PowerShellGet</span></span>

|<span data-ttu-id="efe3a-133">Versie van het besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="efe3a-133">OS Version</span></span>|<span data-ttu-id="efe3a-134">Installatie-instructies</span><span class="sxs-lookup"><span data-stu-id="efe3a-134">Install instructions</span></span>|
|---|---|
|<span data-ttu-id="efe3a-135">Ik heb Windows 10 of Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="efe3a-135">I have Windows 10 or Windows Server 2016</span></span>|<span data-ttu-id="efe3a-136">Ingebouwd in Windows Management Framework 5.0 (WMF), dat is opgenomen in het besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="efe3a-136">Built into Windows Management Framework (WMF) 5.0 included in the OS</span></span>|
|<span data-ttu-id="efe3a-137">Ik wil een upgrade naar PowerShell 5 uitvoeren</span><span class="sxs-lookup"><span data-stu-id="efe3a-137">I want to upgrade to PowerShell 5</span></span>|[<span data-ttu-id="efe3a-138">Installeer de meest recente versie van WMF</span><span class="sxs-lookup"><span data-stu-id="efe3a-138">Install the latest version of WMF</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)|
|<span data-ttu-id="efe3a-139">Ik heb een versie van Windows met PowerShell 3 of PowerShell 4</span><span class="sxs-lookup"><span data-stu-id="efe3a-139">I am running on a version of Windows with PowerShell 3 or PowerShell 4</span></span>|[<span data-ttu-id="efe3a-140">Haal de PackageManagement-modules op</span><span class="sxs-lookup"><span data-stu-id="efe3a-140">Get the PackageManagement modules</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217)|

<a id="helpmechoose"></a>
### <a name="checking-the-version-of-azure-powershell"></a><span data-ttu-id="efe3a-141">De versie van Azure PowerShell controleren</span><span class="sxs-lookup"><span data-stu-id="efe3a-141">Checking the version of Azure PowerShell</span></span>

<span data-ttu-id="efe3a-142">Hoewel we u aanraden om zo snel mogelijk een upgrade naar de meest recente versie uit te voeren, worden er meerdere versies van Azure PowerShell ondersteund.</span><span class="sxs-lookup"><span data-stu-id="efe3a-142">Although we encourage you to upgrade to the latest version as early as possible, several versions of Azure PowerShell are support.</span></span> <span data-ttu-id="efe3a-143">Voer `Get-Module AzureRM` vanaf de opdrachtregel uit om te bepalen welke versie van Azure PowerShell er op uw systeem is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="efe3a-143">To determine the version of Azure PowerShell you have installed, run `Get-Module AzureRM` from your command line.</span></span>

```powershell
Get-Module AzureRM -list | Select-Object Name,Version,Path
```
