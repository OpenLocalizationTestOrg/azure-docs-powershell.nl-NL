---
title: <span data-ttu-id="fd232-101">De Azure PowerShell Service Management-module installeren en configureren | Microsoft Docs</span><span class="sxs-lookup"><span data-stu-id="fd232-101">Install and configure the Azure PowerShell Service Management module | Microsoft Docs</span></span>
description: <span data-ttu-id="fd232-102">Azure PowerShell voor het eerst installeren en configureren.</span><span class="sxs-lookup"><span data-stu-id="fd232-102">How to install and configure Azure PowerShell for first time use.</span></span>
services: azure
author: sdwheeler
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/06/2017
ms.openlocfilehash: c51c727c1cb022eca59f819c7f24d8e058c677da
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="fd232-103">De Azure PowerShell Service Management-module installeren</span><span class="sxs-lookup"><span data-stu-id="fd232-103">Installing the Azure PowerShell Service Management module</span></span>
<a id="installing-the-azure-powershell-service-management-module" class="xliff"></a>

<span data-ttu-id="fd232-104">Installatie van Azure PowerShell via de [PowerShell Gallery](https://www.powershellgallery.com/) heeft de voorkeur.</span><span class="sxs-lookup"><span data-stu-id="fd232-104">Installing Azure PowerShell from the [PowerShell Gallery](https://www.powershellgallery.com/) is the preferred method of installation.</span></span>

## <span data-ttu-id="fd232-105">Stap 1: PowerShellGet installeren</span><span class="sxs-lookup"><span data-stu-id="fd232-105">Step 1: Install PowerShellGet</span></span>
<a id="step-1-install-powershellget" class="xliff"></a>

<span data-ttu-id="fd232-106">Als u items uit de PowerShell Gallery wilt installeren, hebt u de PowerShellGet-module nodig.</span><span class="sxs-lookup"><span data-stu-id="fd232-106">Installing items from the PowerShell Gallery requires the PowerShellGet module.</span></span> <span data-ttu-id="fd232-107">Zorg ervoor dat u de juiste versie van PowerShellGet hebt en ook voldoet aan de overige systeemvereisten.</span><span class="sxs-lookup"><span data-stu-id="fd232-107">Make sure you have the appropriate version of PowerShellGet and other system requirements.</span></span> <span data-ttu-id="fd232-108">Voer de volgende opdracht uit om na te gaan of PowerShellGet op uw systeem is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="fd232-108">Run the following command to see if you have PowerShellGet installed on your system.</span></span>

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

<span data-ttu-id="fd232-109">De uitvoer moet er ongeveer uitzien als hieronder is weergegeven:</span><span class="sxs-lookup"><span data-stu-id="fd232-109">You should see something similar to the following output:</span></span>

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

<span data-ttu-id="fd232-110">Zie [PowerShellGet ophalen](install-azurerm-ps.md#how-to-get-powershellget) als PowerShellGet niet is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="fd232-110">If you do not have PowerShellGet installed, see the [How to get PowerShellGet](install-azurerm-ps.md#how-to-get-powershellget).</span></span>

## <span data-ttu-id="fd232-111">Stap 2: Azure PowerShell installeren</span><span class="sxs-lookup"><span data-stu-id="fd232-111">Step 2: Install Azure PowerShell</span></span>
<a id="step-2-install-azure-powershell" class="xliff"></a>

<span data-ttu-id="fd232-112">Voer de volgende opdracht uit vanuit de Windows PowerShell-console die als beheerder wordt uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="fd232-112">Run the following command from the Windows PowerShell console running as Administrator:</span></span>

```powershell
Install-Module Azure
```

<span data-ttu-id="fd232-113">De Azure-module is een updatepakketmodule voor de Azure Resource Manager-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fd232-113">The Azure module is a rollup module for the Azure Resource Manager cmdlets.</span></span> <span data-ttu-id="fd232-114">Wanneer u de AzureRM-module installeert, worden alle overige Azure-modules die niet eerder zijn geïnstalleerd, gedownload en geïnstalleerd vanuit de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="fd232-114">When you install the AzureRM module, any other Azure modules that have not previously been installed will be downloaded and installed from the PowerShell Gallery.</span></span>

<span data-ttu-id="fd232-115">De Azure Service Management-module deelt afhankelijkheden met de Azure PowerShell Resource Manager-modules.</span><span class="sxs-lookup"><span data-stu-id="fd232-115">The Azure Service Management module shares dependencies with the Azure PowerShell Resource Manager modules.</span></span> <span data-ttu-id="fd232-116">Als u de Azure PowerShell Resource Manager-modules hebt geïnstalleerd, moet u de parameter `-AllowClobber` aan de installatieopdracht toevoegen.</span><span class="sxs-lookup"><span data-stu-id="fd232-116">If you have installed the Azure PowerShell Resource Manager modules, you will need to add the `-AllowClobber` parameter to the install command.</span></span> <span data-ttu-id="fd232-117">Hiermee worden de huidige gedeelde afhankelijkheden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="fd232-117">This allows this existing shared dependencies to be updated.</span></span> <span data-ttu-id="fd232-118">Zonder deze parameter kan de module niet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="fd232-118">Without this parameter, installation of the module fails.</span></span>

```powershell
Install-Module Azure -AllowClobber
```

<span data-ttu-id="fd232-119">Nadat u deze module hebt geïnstalleerd, kunt u de module importeren door de volgende opdracht uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="fd232-119">After you install this module, you can import the module by running the following command:</span></span>

```powershell
Import-Module Azure
```

## <span data-ttu-id="fd232-120">De cmdlets gebruiken</span><span class="sxs-lookup"><span data-stu-id="fd232-120">To use the cmdlets</span></span>
<a id="to-use-the-cmdlets" class="xliff"></a>

<span data-ttu-id="fd232-121">Als u wilt gaan werken met de cmdlets van Azure Service Management, moet u zich eerst aanmelden bij uw Azure-account.</span><span class="sxs-lookup"><span data-stu-id="fd232-121">To start working with the Azure Service Management cmdlets, first log on to your Azure account.</span></span> <span data-ttu-id="fd232-122">Voer de volgende opdracht uit als u zich wilt aanmelden bij uw account:</span><span class="sxs-lookup"><span data-stu-id="fd232-122">To log on to your account, run the following command:</span></span>

```powershell
Add-AzureAccount
```

<span data-ttu-id="fd232-123">Nadat u zich bij Azure hebt aangemeld, maakt Azure PowerShell een context voor de opgegeven sessie.</span><span class="sxs-lookup"><span data-stu-id="fd232-123">After logging into Azure, Azure PowerShell creates a context for the given session.</span></span> <span data-ttu-id="fd232-124">Die context bevat de Azure PowerShell-omgeving, het account, de tenant en het abonnement die worden gebruikt voor alle cmdlets binnen de betreffende sessie.</span><span class="sxs-lookup"><span data-stu-id="fd232-124">That context contains the Azure PowerShell environment, account, tenant, and subscription that will be used for all cmdlets within that session.</span></span> <span data-ttu-id="fd232-125">U bent nu klaar om de onderstaande modules te gaan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="fd232-125">Now you are ready to use the modules below.</span></span>

## <span data-ttu-id="fd232-126">Cmdlets van Azure Service Management</span><span class="sxs-lookup"><span data-stu-id="fd232-126">Azure Service Management cmdlets</span></span>
<a id="azure-service-management-cmdlets" class="xliff"></a>

<span data-ttu-id="fd232-127">Azure PowerShell-modules worden regelmatig bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="fd232-127">Azure PowerShell modules are updated frequently.</span></span> <span data-ttu-id="fd232-128">Als u merkt dat de online Help bij de cmdlet betrekking heeft op cmdlets of parameters die zich niet in uw module bevinden, moet u de nieuwste versie van de module downloaden en installeren.</span><span class="sxs-lookup"><span data-stu-id="fd232-128">If you notice that the online cmdlet help includes cmdlets or parameters that are not in your module, download and install the latest version of the module.</span></span> <span data-ttu-id="fd232-129">Als wilt weten wat de versie van uw module is, typt u: `(Get-Module Azure).Version`.</span><span class="sxs-lookup"><span data-stu-id="fd232-129">To find the version of your module, type: `(Get-Module Azure).Version`.</span></span>

<span data-ttu-id="fd232-130">Als u op zoek bent naar voorbeeldscripts waarmee u een aantal veelvoorkomende taken in Azure kunt automatiseren, kunt u het [Scriptcentrum van Windows Azure](http://www.windowsazure.com/documentation/scripts/) raadplegen.</span><span class="sxs-lookup"><span data-stu-id="fd232-130">For sample scripts that can help you automate some of the common tasks in Azure, see the [Windows Azure Script Center](http://www.windowsazure.com/documentation/scripts/).</span></span>

<span data-ttu-id="fd232-131">Zie [Scripting with Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210) (Werken met scripts in Windows PowerShell) voor algemene informatie over hoe u Windows PowerShell installeert en aanpast, ermee werkt en er meer over leert.</span><span class="sxs-lookup"><span data-stu-id="fd232-131">For general information about installing, learning, using, and customizing Windows PowerShell, see [Scripting with Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210).</span></span>
