---
title: Azure PowerShell in MacOS en Linux installeren en configureren in MacOS en Linux | Microsoft Docs
description: Azure PowerShell voor het eerst installeren en configureren in MacOS en Linux.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 09/06/2017
ms.openlocfilehash: 94b39c18acaca7a4b17b5207feed025442665acc
ms.sourcegitcommit: 202ec2df66c40a60f47ea06b30a6701ad444d229
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a><span data-ttu-id="a492a-103">Azure PowerShell in MacOS en Linux installeren en configureren in MacOS en Linux</span><span class="sxs-lookup"><span data-stu-id="a492a-103">Install and configure Azure PowerShell on macOS and Linux</span></span>

<span data-ttu-id="a492a-104">Het is nu mogelijk om PowerShell 6 (bèta) en Azure PowerShell te installeren op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="a492a-104">It is now possible to install PowerShell 6 (beta) and Azure PowerShell on non-Windows platforms.</span></span>
<span data-ttu-id="a492a-105">Het installatieproces van Azure PowerShell in MacOS en Linux verschilt niet veel van dat voor Windows, maar u dient eerst PowerShell 6 (bèta) te installeren.</span><span class="sxs-lookup"><span data-stu-id="a492a-105">The process of installing Azure PowerShell on macOS and Linux is not that different from Windows, however, you must first install PowerShell 6 (beta).</span></span>

> [!NOTE]

> <span data-ttu-id="a492a-106">Op dit moment zijn PowerShell 6 (bèta) en Azure PowerShell voor .NET Core beide nog bètaversies.</span><span class="sxs-lookup"><span data-stu-id="a492a-106">At this time, both PowerShell 6 (beta) and Azure PowerShell for .NET Core are still in beta.</span></span>
> <span data-ttu-id="a492a-107">De ondersteuning voor deze producten is beperkt.</span><span class="sxs-lookup"><span data-stu-id="a492a-107">Support for these products is limited.</span></span> <span data-ttu-id="a492a-108">U wordt vriendelijk verzocht Issues aan te maken op GitHub als u problemen of fouten ontdekt.</span><span class="sxs-lookup"><span data-stu-id="a492a-108">If you have problems or discover bugs, please file Issues in GitHub.</span></span>
>
> * [<span data-ttu-id="a492a-109">Problemen met PowerShell 6 (bèta)</span><span class="sxs-lookup"><span data-stu-id="a492a-109">Issues for PowerShell 6 (beta)</span></span>](https://github.com/PowerShell/PowerShell/issues)
> * [<span data-ttu-id="a492a-110">Problemen met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="a492a-110">Issues for Azure PowerShell</span></span>](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-6-beta"></a><span data-ttu-id="a492a-111">Stap 1: PowerShell 6 (bèta) installeren</span><span class="sxs-lookup"><span data-stu-id="a492a-111">Step 1: Install PowerShell 6 (beta)</span></span>

<span data-ttu-id="a492a-112">Het installatieproces voor PowerShell 6 (bèta) is afhankelijk van het gebruikte besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="a492a-112">The process of installing PowerShell 6 (beta) on varies depending on the target operating system.</span></span>
<span data-ttu-id="a492a-113">Het is mogelijk PowerShell 6 (bèta) in Windows te installeren, maar in dit artikel wordt gekeken naar MacOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="a492a-113">While it is possible to install PowerShell 6 (beta) on Windows, this article focuses on macOS and Linux.</span></span> <span data-ttu-id="a492a-114">Raadpleeg het artikel over het [installatieproces](./install-azurerm-ps.md) voor Windows, indien u Azure PowerShell in Windows wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a492a-114">If you want to use Azure PowerShell on Windows, see the [install](./install-azurerm-ps.md) article for Windows.</span></span>

<span data-ttu-id="a492a-115">Om **PowerShell 6** (bèta) te installeren in Linux of MacOS, dient u:</span><span class="sxs-lookup"><span data-stu-id="a492a-115">To install **PowerShell 6** (beta) on Linux or macOS, you need to:</span></span>

1. <span data-ttu-id="a492a-116">PowerShell te downloaden van [GitHub](https://github.com/powershell/powershell#get-powershell), voor uw specifieke besturingssystemen en versie</span><span class="sxs-lookup"><span data-stu-id="a492a-116">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
2. <span data-ttu-id="a492a-117">de installatie-instructies te volgen</span><span class="sxs-lookup"><span data-stu-id="a492a-117">Follow the installation instructions</span></span>
   - [<span data-ttu-id="a492a-118">Linux</span><span class="sxs-lookup"><span data-stu-id="a492a-118">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
   - [<span data-ttu-id="a492a-119">MacOS</span><span class="sxs-lookup"><span data-stu-id="a492a-119">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)

## <a name="step-2-install-azure-powershell-for-net-core"></a><span data-ttu-id="a492a-120">Stap 2: Azure PowerShell voor .NET Core installeren</span><span class="sxs-lookup"><span data-stu-id="a492a-120">Step 2: Install Azure PowerShell for .NET Core</span></span>

<span data-ttu-id="a492a-121">De PowerShellGet is standaard al geïnstalleerd bij PowerShell 6 (bèta).</span><span class="sxs-lookup"><span data-stu-id="a492a-121">PowerShell 6 (beta) comes with the PowerShellGet module already installed.</span></span> <span data-ttu-id="a492a-122">Hierdoor kunt u eenvoudig iedere module installeren die is gepubliceerd naar de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a492a-122">This makes it easy to install any module that is published to the PowerShell Gallery.</span></span> <span data-ttu-id="a492a-123">Om Azure PowerShell te installeren, opent u een nieuwe PowerShell-sessie en voert u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="a492a-123">To install Azure PowerShell, open a new PowerShell session and run the following command:</span></span>

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a><span data-ttu-id="a492a-124">Stap 3: de AzureRM.Netcore-module laden</span><span class="sxs-lookup"><span data-stu-id="a492a-124">Step 3: Load the AzureRM.Netcore module</span></span>

<span data-ttu-id="a492a-125">Nadat de module is geïnstalleerd, moet u de module in uw PowerShell-sessie laden.</span><span class="sxs-lookup"><span data-stu-id="a492a-125">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="a492a-126">Modules worden geladen door de cmdlet `Import-Module` als volgt te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="a492a-126">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM.Netcore
```

<span data-ttu-id="a492a-127">Nadat het importeren is voltooid, kunt u uw geïnstalleerde module testen door u bij Azure aan te melden met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="a492a-127">After the import completes, you can test your newly installed and module by attempting to sign into Azure using the following command:</span></span>

```powershell
Login-AzureRMAccount
```

<span data-ttu-id="a492a-128">De bovenstaande opdracht zou u naar `https://aka.ms/devicelogin` moeten leiden om de opgegeven code in te voeren.</span><span class="sxs-lookup"><span data-stu-id="a492a-128">The above command should prompt you to go to `https://aka.ms/devicelogin` and enter the provided code.</span></span>

## <a name="available-cmdlets"></a><span data-ttu-id="a492a-129">Beschikbare cmdlets</span><span class="sxs-lookup"><span data-stu-id="a492a-129">Available cmdlets</span></span>

<span data-ttu-id="a492a-130">De Azure PowerShell-modules voor .NET Standard zijn nog in ontwikkeling.</span><span class="sxs-lookup"><span data-stu-id="a492a-130">The Azure PowerShell modules for .NET Standard are still in development.</span></span> <span data-ttu-id="a492a-131">Deze modules bieden niet de volledige set cmdlets die beschikbaar is voor de Windows-versie van de modules.</span><span class="sxs-lookup"><span data-stu-id="a492a-131">These modules do not provide the full set of cmdlets that are available for the Windows version of the modules.</span></span> <span data-ttu-id="a492a-132">De volgende functies zijn geïmplementeerd in AzureRM.Netcore-modules:</span><span class="sxs-lookup"><span data-stu-id="a492a-132">The following functions are implemented in AzureRM.Netcore modules:</span></span>

* <span data-ttu-id="a492a-133">Accountbeheer</span><span class="sxs-lookup"><span data-stu-id="a492a-133">Account management</span></span>
  - <span data-ttu-id="a492a-134">Meld u aan met een Microsoft-account, organisatie-account of service-principal via Microsoft Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="a492a-134">Login with Microsoft account, Organizational account, or Service Principal through Microsoft Azure Active Directory</span></span>
  - <span data-ttu-id="a492a-135">Sla referenties op schijf op met Save-AzureRmContext en laad opgeslagen referenties met Import-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="a492a-135">Save Credentials to disk with Save-AzureRmContext and load saved credentials using Import-AzureRmContext</span></span>
* <span data-ttu-id="a492a-136">Omgeving</span><span class="sxs-lookup"><span data-stu-id="a492a-136">Environment</span></span>
  - <span data-ttu-id="a492a-137">Verkrijg de verschillende kant-en-klare omgevingen voor Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="a492a-137">Get the different out-of-box Microsoft Azure environments</span></span>
  - <span data-ttu-id="a492a-138">Aangepaste omgevingen toevoegen/instellen/verwijderen (zoals uw Azure Stack- of Windows Azure Pack-omgevingen)</span><span class="sxs-lookup"><span data-stu-id="a492a-138">Add/Set/Remove customized environments (like your Azure Stack or Windows Azure Pack environments)</span></span>
* <span data-ttu-id="a492a-139">Cmdlets voor beheer van Azure-services met behulp van Resource Manager- en Service Management-interfaces.</span><span class="sxs-lookup"><span data-stu-id="a492a-139">Management plane cmdlets for Azure services using Resource Manager and Service Management interfaces.</span></span>
  - <span data-ttu-id="a492a-140">Virtuele machine</span><span class="sxs-lookup"><span data-stu-id="a492a-140">Virtual Machine</span></span>
  - <span data-ttu-id="a492a-141">App Service (Websites)</span><span class="sxs-lookup"><span data-stu-id="a492a-141">App Service (Websites)</span></span>
  - <span data-ttu-id="a492a-142">SQL Database</span><span class="sxs-lookup"><span data-stu-id="a492a-142">SQL Database</span></span>
  - <span data-ttu-id="a492a-143">Storage</span><span class="sxs-lookup"><span data-stu-id="a492a-143">Storage</span></span>
  - <span data-ttu-id="a492a-144">Netwerk</span><span class="sxs-lookup"><span data-stu-id="a492a-144">Network</span></span>

## <a name="next-steps"></a><span data-ttu-id="a492a-145">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="a492a-145">Next Steps</span></span>

<span data-ttu-id="a492a-146">Raadpleeg voor meer informatie over het gebruik van Azure PowerShell het artikel [Aan de slag met Azure PowerShell](get-started-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="a492a-146">For more information about using Azure PowerShell, see the [Get started with Azure PowerShell](get-started-azureps.md) article.</span></span>
