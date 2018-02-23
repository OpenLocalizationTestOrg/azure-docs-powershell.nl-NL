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
ms.date: 01/12/2018
ms.openlocfilehash: 64a86dfd4af7f3f0a91501e9a096ff190f7100cb
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2018
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a><span data-ttu-id="fdcec-103">Azure PowerShell in MacOS en Linux installeren en configureren in MacOS en Linux</span><span class="sxs-lookup"><span data-stu-id="fdcec-103">Install and configure Azure PowerShell on macOS and Linux</span></span>

<span data-ttu-id="fdcec-104">Het is nu mogelijk om PowerShell Core v6 en Azure PowerShell te installeren op niet-Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="fdcec-104">It is now possible to install PowerShell Core v6 and Azure PowerShell on non-Windows platforms.</span></span>
<span data-ttu-id="fdcec-105">Het installatieproces van Azure PowerShell in macOS en Linux verschilt niet veel van dat voor Windows, maar u moet wel eerst PowerShell Core v6 installeren.</span><span class="sxs-lookup"><span data-stu-id="fdcec-105">The process of installing Azure PowerShell on macOS and Linux is not that different from Windows, however, you must first install PowerShell Core v6.</span></span>

> [!NOTE]

> <span data-ttu-id="fdcec-106">Op dit moment zijn PowerShell Core v6 en Azure PowerShell voor .NET Core beide nog bètaversies.</span><span class="sxs-lookup"><span data-stu-id="fdcec-106">At this time, both PowerShell Core v6 and Azure PowerShell for .NET Core are still in beta.</span></span>
> <span data-ttu-id="fdcec-107">De ondersteuning voor deze producten is beperkt.</span><span class="sxs-lookup"><span data-stu-id="fdcec-107">Support for these products is limited.</span></span> <span data-ttu-id="fdcec-108">U wordt vriendelijk verzocht Issues aan te maken op GitHub als u problemen of fouten ontdekt.</span><span class="sxs-lookup"><span data-stu-id="fdcec-108">If you have problems or discover bugs, please file Issues in GitHub.</span></span>
>
> * [<span data-ttu-id="fdcec-109">Problemen met PowerShell Core v6</span><span class="sxs-lookup"><span data-stu-id="fdcec-109">Issues for PowerShell Core v6</span></span>](https://github.com/PowerShell/PowerShell/issues)
> * [<span data-ttu-id="fdcec-110">Problemen met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdcec-110">Issues for Azure PowerShell</span></span>](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-core-v6"></a><span data-ttu-id="fdcec-111">Stap 1: PowerShell Core v6 installeren</span><span class="sxs-lookup"><span data-stu-id="fdcec-111">Step 1: Install PowerShell Core v6</span></span>

<span data-ttu-id="fdcec-112">Het installatieproces voor PowerShell Core v6 is afhankelijk van het gebruikte besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="fdcec-112">The process of installing PowerShell Core v6 on varies depending on the target operating system.</span></span>
<span data-ttu-id="fdcec-113">Het is mogelijk PowerShell Core v6 in Windows te installeren, maar in dit artikel wordt gekeken naar macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="fdcec-113">While it is possible to install PowerShell Core v6 on Windows, this article focuses on macOS and Linux.</span></span> <span data-ttu-id="fdcec-114">Raadpleeg het artikel over het [installatieproces](./install-azurerm-ps.md) voor Windows, indien u Azure PowerShell in Windows wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fdcec-114">If you want to use Azure PowerShell on Windows, see the [install](./install-azurerm-ps.md) article for Windows.</span></span>

<span data-ttu-id="fdcec-115">Het installatieproces voor **PowerShell Core v6** in Linux of Mac OS kan verschillen, afhankelijk van de Linux-distributie en de versie van het besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="fdcec-115">Installing **PowerShell Core v6** on Linux or macOS varies depending on the Linux distribution and OS version.</span></span>
<span data-ttu-id="fdcec-116">Gedetailleerde instructies vindt u in het volgende artikel:</span><span class="sxs-lookup"><span data-stu-id="fdcec-116">Detailed instructions can be found in the following article:</span></span>

- <span data-ttu-id="fdcec-117">[Installing PowerShell Core on macOS and Linux](/powershell/scripting/setup/installing-powershell-core-on-macos-and-linux) (PowerShell Core installeren in macOS en Linux)</span><span class="sxs-lookup"><span data-stu-id="fdcec-117">[Installing PowerShell Core on macOS and Linux](/powershell/scripting/setup/installing-powershell-core-on-macos-and-linux)</span></span>

## <a name="step-2-install-azure-powershell-for-net-core"></a><span data-ttu-id="fdcec-118">Stap 2: Azure PowerShell voor .NET Core installeren</span><span class="sxs-lookup"><span data-stu-id="fdcec-118">Step 2: Install Azure PowerShell for .NET Core</span></span>

<span data-ttu-id="fdcec-119">De PowerShellGet-module is standaard al geïnstalleerd in PowerShell Core v6.</span><span class="sxs-lookup"><span data-stu-id="fdcec-119">PowerShell Core v6 comes with the PowerShellGet module already installed.</span></span> <span data-ttu-id="fdcec-120">Hierdoor kunt u eenvoudig iedere module installeren die is gepubliceerd naar de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="fdcec-120">This makes it easy to install any module that is published to the PowerShell Gallery.</span></span> <span data-ttu-id="fdcec-121">Om Azure PowerShell te installeren, opent u een nieuwe PowerShell-sessie en voert u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="fdcec-121">To install Azure PowerShell, open a new PowerShell session and run the following command:</span></span>

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a><span data-ttu-id="fdcec-122">Stap 3: de AzureRM.Netcore-module laden</span><span class="sxs-lookup"><span data-stu-id="fdcec-122">Step 3: Load the AzureRM.Netcore module</span></span>

<span data-ttu-id="fdcec-123">Nadat de module is geïnstalleerd, moet u de module in uw PowerShell-sessie laden.</span><span class="sxs-lookup"><span data-stu-id="fdcec-123">Once the module is installed, you need to load the module into your PowerShell session.</span></span> <span data-ttu-id="fdcec-124">Modules worden geladen door de cmdlet `Import-Module` als volgt te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="fdcec-124">Modules are loaded using the `Import-Module` cmdlet, as follows:</span></span>

```powershell
Import-Module AzureRM.Netcore
Import-Module AzureRM.Profile.Netcore
```

<span data-ttu-id="fdcec-125">Nadat het importeren is voltooid, kunt u uw geïnstalleerde module testen door u bij Azure aan te melden met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="fdcec-125">After the import completes, you can test your newly installed and module by attempting to sign into Azure using the following command:</span></span>

```powershell
Login-AzureRMAccount
```

<span data-ttu-id="fdcec-126">De bovenstaande opdracht zou u naar `https://aka.ms/devicelogin` moeten leiden om de opgegeven code in te voeren.</span><span class="sxs-lookup"><span data-stu-id="fdcec-126">The above command should prompt you to go to `https://aka.ms/devicelogin` and enter the provided code.</span></span>

## <a name="available-cmdlets"></a><span data-ttu-id="fdcec-127">Beschikbare cmdlets</span><span class="sxs-lookup"><span data-stu-id="fdcec-127">Available cmdlets</span></span>

<span data-ttu-id="fdcec-128">De Azure PowerShell-modules voor .NET Standard zijn nog in ontwikkeling.</span><span class="sxs-lookup"><span data-stu-id="fdcec-128">The Azure PowerShell modules for .NET Standard are still in development.</span></span> <span data-ttu-id="fdcec-129">Deze modules bieden niet de volledige set cmdlets die beschikbaar is voor de Windows-versie van de modules.</span><span class="sxs-lookup"><span data-stu-id="fdcec-129">These modules do not provide the full set of cmdlets that are available for the Windows version of the modules.</span></span> <span data-ttu-id="fdcec-130">De volgende functies zijn geïmplementeerd in AzureRM.Netcore-modules:</span><span class="sxs-lookup"><span data-stu-id="fdcec-130">The following functions are implemented in AzureRM.Netcore modules:</span></span>

* <span data-ttu-id="fdcec-131">Accountbeheer</span><span class="sxs-lookup"><span data-stu-id="fdcec-131">Account management</span></span>
  - <span data-ttu-id="fdcec-132">Meld u aan met een Microsoft-account, organisatie-account of service-principal via Microsoft Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="fdcec-132">Login with Microsoft account, Organizational account, or Service Principal through Microsoft Azure Active Directory</span></span>
  - <span data-ttu-id="fdcec-133">Sla referenties op schijf op met Save-AzureRmContext en laad opgeslagen referenties met Import-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="fdcec-133">Save Credentials to disk with Save-AzureRmContext and load saved credentials using Import-AzureRmContext</span></span>
* <span data-ttu-id="fdcec-134">Omgeving</span><span class="sxs-lookup"><span data-stu-id="fdcec-134">Environment</span></span>
  - <span data-ttu-id="fdcec-135">Verkrijg de verschillende kant-en-klare omgevingen voor Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="fdcec-135">Get the different out-of-box Microsoft Azure environments</span></span>
  - <span data-ttu-id="fdcec-136">Aangepaste omgevingen toevoegen/instellen/verwijderen (zoals uw Azure Stack- of Windows Azure Pack-omgevingen)</span><span class="sxs-lookup"><span data-stu-id="fdcec-136">Add/Set/Remove customized environments (like your Azure Stack or Windows Azure Pack environments)</span></span>
* <span data-ttu-id="fdcec-137">Cmdlets voor beheer van Azure-services met behulp van Resource Manager- en Service Management-interfaces.</span><span class="sxs-lookup"><span data-stu-id="fdcec-137">Management plane cmdlets for Azure services using Resource Manager and Service Management interfaces.</span></span>
  - <span data-ttu-id="fdcec-138">Virtuele machine</span><span class="sxs-lookup"><span data-stu-id="fdcec-138">Virtual Machine</span></span>
  - <span data-ttu-id="fdcec-139">App Service (Websites)</span><span class="sxs-lookup"><span data-stu-id="fdcec-139">App Service (Websites)</span></span>
  - <span data-ttu-id="fdcec-140">SQL Database</span><span class="sxs-lookup"><span data-stu-id="fdcec-140">SQL Database</span></span>
  - <span data-ttu-id="fdcec-141">Storage</span><span class="sxs-lookup"><span data-stu-id="fdcec-141">Storage</span></span>
  - <span data-ttu-id="fdcec-142">Netwerk</span><span class="sxs-lookup"><span data-stu-id="fdcec-142">Network</span></span>

## <a name="next-steps"></a><span data-ttu-id="fdcec-143">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="fdcec-143">Next Steps</span></span>

<span data-ttu-id="fdcec-144">Raadpleeg voor meer informatie over het gebruik van Azure PowerShell het artikel [Aan de slag met Azure PowerShell](get-started-azureps.md).</span><span class="sxs-lookup"><span data-stu-id="fdcec-144">For more information about using Azure PowerShell, see the [Get started with Azure PowerShell](get-started-azureps.md) article.</span></span>
