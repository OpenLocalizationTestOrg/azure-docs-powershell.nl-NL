---
title: Werken met experimentele Azure PowerShell-modules
description: Lees hier meer over de achterliggende filosofie en het gebruik van experimentele Azure PowerShell-modules.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 09/05/2017
ms.openlocfilehash: 7a01957040be7c0498ef4f0e9b8f7297119221a5
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2017
---
# <a name="using-experimental-azure-powershell-modules"></a><span data-ttu-id="27f69-103">Werken met experimentele Azure PowerShell-modules</span><span class="sxs-lookup"><span data-stu-id="27f69-103">Using experimental Azure PowerShell modules</span></span>

<span data-ttu-id="27f69-104">Gezien de nadruk op tools voor ontwikkelaars (met name CLI's) in Azure, is het team van Azure PowerShell druk aan het experimenteren met allerlei verbeteringen van Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27f69-104">With the emphasis on developer tools (especially CLIs) in Azure, the Azure PowerShell team is experimenting with many improvements to the Azure PowerShell experience.</span></span>

## <a name="experimentation-methodology"></a><span data-ttu-id="27f69-105">Methodologie voor experimenten</span><span class="sxs-lookup"><span data-stu-id="27f69-105">Experimentation methodology</span></span>

<span data-ttu-id="27f69-106">Om dit proces van experimenteren te vergemakkelijken, maken we nieuwe Azure PowerShell-modules waarin bestaande functionaliteit uit de Azure SDK op nieuwe, eenvoudiger te gebruiken manieren wordt geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="27f69-106">To facilitate experimentation, we are creating new Azure PowerShell modules that implement existing Azure SDK functionality in new, easier to use ways.</span></span> <span data-ttu-id="27f69-107">In de meeste gevallen is de werking van deze cmdlets identiek aan die van bestaande cmdlets.</span><span class="sxs-lookup"><span data-stu-id="27f69-107">In most cases, the cmdlets exactly mirror existing cmdlets.</span></span> <span data-ttu-id="27f69-108">De experimentele cmdlets hebben echter een verkorte syntaxis en slimmere standaardwaarden, waardoor het eenvoudiger is om Azure-resources te maken en te beheren.</span><span class="sxs-lookup"><span data-stu-id="27f69-108">However, the experimental cmdlets provide a shorthand notation and smarter default values that make it easier to create and manage Azure resources.</span></span>

<span data-ttu-id="27f69-109">Deze modules kunnen zonder problemen naast bestaande Azure PowerShell-modules worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="27f69-109">These modules can be installed side-by-side with existing Azure PowerShell modules.</span></span> <span data-ttu-id="27f69-110">De namen van de cmdlets zijn ingekort om kortere namen mogelijk te maken en om naamconflicten met bestaande, niet-experimentele cmdlets te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="27f69-110">The cmdlet names have been shortened to provide shorter names and avoid name conflicts with existing, non-experimental cmdlets.</span></span>

<span data-ttu-id="27f69-111">De experimentele modules gebruiken de volgende naamconventie:</span><span class="sxs-lookup"><span data-stu-id="27f69-111">The experimental modules use the following naming convention:</span></span>

- <span data-ttu-id="27f69-112">AzureRM.Compute.Experiments</span><span class="sxs-lookup"><span data-stu-id="27f69-112">AzureRM.Compute.Experiments</span></span>
- <span data-ttu-id="27f69-113">AzureRM.Websites.Experiments</span><span class="sxs-lookup"><span data-stu-id="27f69-113">AzureRM.Websites.Experiments</span></span>

<span data-ttu-id="27f69-114">Deze naamconventie is vergelijkbaar met de naamgeving van Preview-modules: `AzureRM.*.Preview`.</span><span class="sxs-lookup"><span data-stu-id="27f69-114">This naming convention is similar to the naming of Preview modules: `AzureRM.*.Preview`.</span></span> <span data-ttu-id="27f69-115">Preview-modules zijn iets anders dan experimentele modules.</span><span class="sxs-lookup"><span data-stu-id="27f69-115">Preview modules differ from experimental modules.</span></span> <span data-ttu-id="27f69-116">Preview-modules implementeren nieuwe functionaliteit van Azure-services die alleen beschikbaar is als een Preview-aanbieding.</span><span class="sxs-lookup"><span data-stu-id="27f69-116">Preview modules implement new functionality of Azure services that is only available as a Preview offering.</span></span> <span data-ttu-id="27f69-117">Preview-modules vervangen bestaande Azure PowerShell-modules en gebruiken dezelfde namen voor cmdlets en parameters.</span><span class="sxs-lookup"><span data-stu-id="27f69-117">Preview modules replace existing Azure PowerShell modules and use the same cmdlet and parameter names.</span></span>

## <a name="how-to-install-an-experimental-module"></a><span data-ttu-id="27f69-118">Een experimentele module installeren</span><span class="sxs-lookup"><span data-stu-id="27f69-118">How to install an experimental module</span></span>

<span data-ttu-id="27f69-119">Experimentele modules worden gepubliceerd in PowerShell Gallery, net als de bestaande Azure PowerShell-modules.</span><span class="sxs-lookup"><span data-stu-id="27f69-119">Experimental modules are published to the PowerShell Gallery just like the existing Azure PowerShell modules.</span></span> <span data-ttu-id="27f69-120">Voer de volgende opdracht uit om een overzicht met experimentele modules weer te geven:</span><span class="sxs-lookup"><span data-stu-id="27f69-120">To see a list of experimental modules, run the following command:</span></span>

```powershell
Find-Module AzureRM.*.Experiments
```

```Output
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      AzureRM.Websites.Experiments        PSGallery            Create and deploy web applications using Azure Ap...
1.0.25     AzureRM.Compute.Experiments         PSGallery            Azure Compute experiments for VM creation
```

<span data-ttu-id="27f69-121">Als u een experimentele module wilt installeren, gebruikt u de volgende opdrachten vanuit een PowerShell-sessie met verhoogde bevoegdheden:</span><span class="sxs-lookup"><span data-stu-id="27f69-121">To install the experimental module, use the following commands from an elevated PowerShell session:</span></span>

```powershell
Install-Module AzureRM.Compute.Experiments
Install-Module AzureRM.Websites.Experiments
```

### <a name="documentation-and-support"></a><span data-ttu-id="27f69-122">Documentatie en ondersteuning</span><span class="sxs-lookup"><span data-stu-id="27f69-122">Documentation and support</span></span>

<span data-ttu-id="27f69-123">Documentatie is opgenomen in het installatiepakket en kan worden geraadpleegd via de cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="27f69-123">Documentation is included in the install package and is accessed using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="27f69-124">Er wordt geen officiële documentatie gepubliceerd voor experimentele modules.</span><span class="sxs-lookup"><span data-stu-id="27f69-124">No official documentation is published for experimental modules.</span></span>

<span data-ttu-id="27f69-125">We willen u vragen om deze modules te testen.</span><span class="sxs-lookup"><span data-stu-id="27f69-125">We encourage you to test these modules.</span></span> <span data-ttu-id="27f69-126">Aan de hand van uw feedback kunnen we de bruikbaarheid verbeteren en reageren op uw verzoeken.</span><span class="sxs-lookup"><span data-stu-id="27f69-126">Your feedback allows us to improve usability and respond to your needs.</span></span> <span data-ttu-id="27f69-127">Vanwege het experimentele karakter is de ondersteuning voor deze modules echter beperkt.</span><span class="sxs-lookup"><span data-stu-id="27f69-127">However, being experimental, support for these modules is limited.</span></span> <span data-ttu-id="27f69-128">Vragen of problemen kunt u melden door een [issue](https://github.com/Azure/azure-powershell/issues) toe te voegen op GitHub.</span><span class="sxs-lookup"><span data-stu-id="27f69-128">Questions or problem reports can be submitted by creating an [issue](https://github.com/Azure/azure-powershell/issues) in the GitHub repository.</span></span>

## <a name="experiments-and-areas-of-improvement"></a><span data-ttu-id="27f69-129">Experimenten en verbeterpunten</span><span class="sxs-lookup"><span data-stu-id="27f69-129">Experiments and areas of improvement</span></span>

<span data-ttu-id="27f69-130">Deze verbeteringen zijn geselecteerd op basis van belangrijke differentiators in concurrerende producten.</span><span class="sxs-lookup"><span data-stu-id="27f69-130">These improvements were selected based on key differentiators in competing products.</span></span> <span data-ttu-id="27f69-131">Zo is de verbetering in Azure CLI 2.0 bijvoorbeeld dat opdrachten worden gebaseerd op _scenario's_ in plaats van een _API surface area_.</span><span class="sxs-lookup"><span data-stu-id="27f69-131">For example, Azure CLI 2.0 has made a point of basing commands on _scenarios_ rather than _API surface area_.</span></span>
<span data-ttu-id="27f69-132">In Azure CLI 2.0 worden verschillende slimme standaardinstellingen gebruikt waardoor eindgebruikers de beschikking krijgen over scenario's waarmee ze snel aan de slag kunnen.</span><span class="sxs-lookup"><span data-stu-id="27f69-132">Azure CLI 2.0 use a number of smart defaults that make "getting started" scenarios easier for end users.</span></span>

### <a name="core-improvements"></a><span data-ttu-id="27f69-133">Essentiële verbeteringen</span><span class="sxs-lookup"><span data-stu-id="27f69-133">Core improvements</span></span>

<span data-ttu-id="27f69-134">De essentiële verbeteringen worden beschouwd als 'logisch', en er zijn weinig experimenten nodig om deze updates te implementeren.</span><span class="sxs-lookup"><span data-stu-id="27f69-134">The core improvements are regarded as "common sense", and little experimentation is needed to move forward in implementing these updates.</span></span>

- <span data-ttu-id="27f69-135">Op scenario's gebaseerde cmdlets: **All*-cmdlets moeten worden gebaseerd op scenario's, niet op de REST-service van Azure.</span><span class="sxs-lookup"><span data-stu-id="27f69-135">Scenario-based Cmdlets - **All*- cmdlets should be designed around scenarios, not the Azure REST service.</span></span>

- <span data-ttu-id="27f69-136">Kortere namen: geldt voor de namen van cmdlets (bijvoorbeeld `New-AzureRmVM` => `New-AzVm`) en van parameters (bijvoorbeeld `-ResourceGroupName` => `-Rg`).</span><span class="sxs-lookup"><span data-stu-id="27f69-136">Shorter Names - Includes the names of cmdlets (for example, `New-AzureRmVM` => `New-AzVm`) and the names of parameters (for example, `-ResourceGroupName` => `-Rg`).</span></span> <span data-ttu-id="27f69-137">Aliassen gebruiken voor compatibiliteit met 'oude' cmdlets.</span><span class="sxs-lookup"><span data-stu-id="27f69-137">Use aliases for compatibility with "old" cmdlets.</span></span> <span data-ttu-id="27f69-138">_Achterwaarts compatibele_ parametersets aanbieden.</span><span class="sxs-lookup"><span data-stu-id="27f69-138">Provide _backwards compatible_ parameter sets.</span></span>

- <span data-ttu-id="27f69-139">Slimme standaardwaarden: slimme standaardwaarden ontwikkelen om 'vereiste' gegevens automatisch in te vullen.</span><span class="sxs-lookup"><span data-stu-id="27f69-139">Smart Defaults - Create smart defaults to fill in "required" information.</span></span> <span data-ttu-id="27f69-140">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="27f69-140">For example:</span></span>
  - <span data-ttu-id="27f69-141">Resourcegroep</span><span class="sxs-lookup"><span data-stu-id="27f69-141">Resource Group</span></span>
  - <span data-ttu-id="27f69-142">Locatie</span><span class="sxs-lookup"><span data-stu-id="27f69-142">Location</span></span>
  - <span data-ttu-id="27f69-143">Afhankelijke resources</span><span class="sxs-lookup"><span data-stu-id="27f69-143">Dependent resources</span></span>

### <a name="experimental-improvements"></a><span data-ttu-id="27f69-144">Experimentele verbeteringen</span><span class="sxs-lookup"><span data-stu-id="27f69-144">Experimental improvements</span></span>

<span data-ttu-id="27f69-145">De experimentele verbeteringen vertegenwoordigen een ingrijpende wijziging die het team wil valideren via experimenten.</span><span class="sxs-lookup"><span data-stu-id="27f69-145">The experimental improvements present a significant change that the team wants to validate via experimentation.</span></span>

- <span data-ttu-id="27f69-146">Eenvoudige typen: maakscenario's moeten afstappen van complexe typen en configuratieobjecten.</span><span class="sxs-lookup"><span data-stu-id="27f69-146">Simple types - Create scenarios should move away from complex types and config objects.</span></span> <span data-ttu-id="27f69-147">Vereenvoudig de configuratie tot een of twee parameters.</span><span class="sxs-lookup"><span data-stu-id="27f69-147">Simplify the configuration down to one or two parameters.</span></span>

- <span data-ttu-id="27f69-148">'Slim maken': alle maakscenario's die worden geïmplementeerd met 'slim maken' hebben _geen_ vereiste parameters. Alle benodigde gegevens worden door Azure PowerShell gekozen.</span><span class="sxs-lookup"><span data-stu-id="27f69-148">"Smart Create" - All create scenarios implementing "Smart Create" would have _no_ required parameters: all necessary information would be chosen by Azure PowerShell in an opinionated fashion.</span></span>

- <span data-ttu-id="27f69-149">Grijze parameters: in veel gevallen kunnen bepaalde parameters 'grijs' of semi-optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="27f69-149">Gray Parameters - In many cases, some parameters could be "gray" or semi-optional.</span></span> <span data-ttu-id="27f69-150">Als de parameter niet is opgegeven, wordt de gebruiker gevraagd of de parameter moet worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="27f69-150">If the parameter is not specified, the user is asked if they want the parameter generated for them.</span></span> <span data-ttu-id="27f69-151">Het is ook logisch voor grijze parameters dat hiervoor een waarde wordt afgeleid op basis van de context, uiteraard met toestemming van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="27f69-151">It also makes sense for gray parameters to infer a value based on context with the user's consent.</span></span>
  <span data-ttu-id="27f69-152">Het is bijvoorbeeld mogelijk dat het logisch is dat voor een grijze parameter de meest recent gebruikte waarde wordt voorgesteld.</span><span class="sxs-lookup"><span data-stu-id="27f69-152">For example, it may make sense to have the gray parameter suggest the most recently used value.</span></span>

- <span data-ttu-id="27f69-153">Parameter `-Auto`: de parameter `-Auto` kan een manier zijn voor gebruikers om aan te geven dat ze _overal de standaardinstellingen_ willen gebruiken zonder dat dit ten koste gaat van de integriteit van vereiste hoofdparameters.</span><span class="sxs-lookup"><span data-stu-id="27f69-153">`-Auto` Switch - The `-Auto` switch would provide an "opt-in" way for users to _default all the things_ while maintaining the integrity of required parameters in the mainline path.</span></span>

### <a name="feature-specific-switches"></a><span data-ttu-id="27f69-154">Functiespecifieke parameters</span><span class="sxs-lookup"><span data-stu-id="27f69-154">Feature-specific switches</span></span>

<span data-ttu-id="27f69-155">Het scenario 'Web-app maken' kan bijvoorbeeld een parameter `-Git` of `-AddRemote` bevatten waarmee automatisch een 'azure' remote wordt toegevoegd aan een bestaande git-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="27f69-155">For example, the "Create web app" scenario might have a `-Git` or `-AddRemote` switch that would automatically add an "azure" remote to an existing git repository.</span></span>

- <span data-ttu-id="27f69-156">Instelbare standaardwaarden: gebruikers moeten de mogelijkheid hebben om standaardwaarden op te geven voor bepaalde veelgebruikte parameters, zoals `-ResourceGroupName` en `-Location`.</span><span class="sxs-lookup"><span data-stu-id="27f69-156">Settable Defaults - Users should have the ability to default certain ubiquitous parameters like `-ResourceGroupName` and `-Location`.</span></span>

- <span data-ttu-id="27f69-157">Standaardgrootten: de 'grootten' voor resources kunnen verwarrend zijn voor gebruikers, aangezien veel providers van resources verschillende namen gebruiken (bijvoorbeeld 'Standard\_DS1\_v2' of 'S1').</span><span class="sxs-lookup"><span data-stu-id="27f69-157">Size Defaults - Resource "sizes" can be confusing to users since many Resource Providers use different names (for example, "Standard\_DS1\_v2" or "S1").</span></span> <span data-ttu-id="27f69-158">De meeste gebruikers zijn echter meer geïnteresseerd in de kosten.</span><span class="sxs-lookup"><span data-stu-id="27f69-158">However, most users care more about cost.</span></span> <span data-ttu-id="27f69-159">Om die reden is het logisch om 'universele' grootten te definiëren op basis van een prijscategorie.</span><span class="sxs-lookup"><span data-stu-id="27f69-159">Therefore, it makes sense to define "universal" sizes based on a pricing schedule.</span></span> <span data-ttu-id="27f69-160">Gebruikers kunnen een specifieke grootte kiezen of Azure PowerShell de _beste optie_ laten kiezen op basis van de resource of het budget.</span><span class="sxs-lookup"><span data-stu-id="27f69-160">Users can choose a specific size or let Azure PowerShell choose the _best option_ based on the resource the budget.</span></span>

- <span data-ttu-id="27f69-161">Indeling van uitvoer: op dit moment retourneert Azure PowerShell een `PSObject` en verder is er weinig console-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="27f69-161">Output Format - Azure PowerShell currently returns `PSObject`s and there is little console output.</span></span> <span data-ttu-id="27f69-162">Azure PowerShell zal mogelijk bepaalde informatie moeten weergeven voor de gebruiker met betrekking tot de gebruikte 'slimme standaardinstellingen'.</span><span class="sxs-lookup"><span data-stu-id="27f69-162">Azure PowerShell may need to display some information to the user regarding the "smart defaults" used.</span></span>

## <a name="try-using-the-experiments"></a><span data-ttu-id="27f69-163">Experimenteren</span><span class="sxs-lookup"><span data-stu-id="27f69-163">Try using the experiments</span></span>

### <a name="install"></a><span data-ttu-id="27f69-164">Installeren</span><span class="sxs-lookup"><span data-stu-id="27f69-164">Install</span></span>

```powershell
Install-Module AzureRM.Compute.Experiments
```

### <a name="create-a-vm"></a><span data-ttu-id="27f69-165">Een virtuele machine maken</span><span class="sxs-lookup"><span data-stu-id="27f69-165">Create a VM</span></span>

```powershell
$job = New-AzVm -Name MyVm -AsJob
Receive-Job $job
```

### <a name="send-us-feedback"></a><span data-ttu-id="27f69-166">Feedback versturen</span><span class="sxs-lookup"><span data-stu-id="27f69-166">Send us feedback</span></span>

```powershell
Send-Feedback
```

### <a name="uninstall-the-experimental-modules"></a><span data-ttu-id="27f69-167">De experimentele modules verwijderen</span><span class="sxs-lookup"><span data-stu-id="27f69-167">Uninstall the experimental modules</span></span>

```powershell
Uninstall-Module AzureRM.Compute.Experiments
```