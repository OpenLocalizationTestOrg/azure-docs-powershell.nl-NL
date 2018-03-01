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
ms.openlocfilehash: c11e4503c07b0a0c4a71021bc511da723098188e
ms.sourcegitcommit: 5fe9a579d2e0d1cb5a05aadaeba5db784f1b18fa
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/28/2018
---
# <a name="using-experimental-azure-powershell-modules"></a><span data-ttu-id="72fbb-103">Werken met experimentele Azure PowerShell-modules</span><span class="sxs-lookup"><span data-stu-id="72fbb-103">Using experimental Azure PowerShell modules</span></span>

<span data-ttu-id="72fbb-104">Gezien de nadruk op tools voor ontwikkelaars (met name CLI's) in Azure, is het team van Azure PowerShell druk aan het experimenteren met allerlei verbeteringen van Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="72fbb-104">With the emphasis on developer tools (especially CLIs) in Azure, the Azure PowerShell team is experimenting with many improvements to the Azure PowerShell experience.</span></span>

## <a name="experimentation-methodology"></a><span data-ttu-id="72fbb-105">Methodologie voor experimenten</span><span class="sxs-lookup"><span data-stu-id="72fbb-105">Experimentation methodology</span></span>

<span data-ttu-id="72fbb-106">Om dit proces van experimenteren te vergemakkelijken, maken we nieuwe Azure PowerShell-modules waarin bestaande functionaliteit uit de Azure SDK op nieuwe, eenvoudiger te gebruiken manieren wordt geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="72fbb-106">To facilitate experimentation, we are creating new Azure PowerShell modules that implement existing Azure SDK functionality in new, easier to use ways.</span></span> <span data-ttu-id="72fbb-107">In de meeste gevallen is de werking van deze cmdlets identiek aan die van bestaande cmdlets.</span><span class="sxs-lookup"><span data-stu-id="72fbb-107">In most cases, the cmdlets exactly mirror existing cmdlets.</span></span> <span data-ttu-id="72fbb-108">De experimentele cmdlets hebben echter een verkorte syntaxis en slimmere standaardwaarden, waardoor het eenvoudiger is om Azure-resources te maken en te beheren.</span><span class="sxs-lookup"><span data-stu-id="72fbb-108">However, the experimental cmdlets provide a shorthand notation and smarter default values that make it easier to create and manage Azure resources.</span></span>

<span data-ttu-id="72fbb-109">Deze modules kunnen zonder problemen naast bestaande Azure PowerShell-modules worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="72fbb-109">These modules can be installed side-by-side with existing Azure PowerShell modules.</span></span> <span data-ttu-id="72fbb-110">De namen van de cmdlets zijn ingekort om kortere namen mogelijk te maken en om naamconflicten met bestaande, niet-experimentele cmdlets te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="72fbb-110">The cmdlet names have been shortened to provide shorter names and avoid name conflicts with existing, non-experimental cmdlets.</span></span>

<span data-ttu-id="72fbb-111">Voor de experimentele modules wordt de volgende naamconventie gebruikt: `AzureRM.*.Experiments`.</span><span class="sxs-lookup"><span data-stu-id="72fbb-111">The experimental modules use the following naming convention: `AzureRM.*.Experiments`.</span></span> <span data-ttu-id="72fbb-112">Deze naamconventie is vergelijkbaar met de naamgeving van Preview-modules: `AzureRM.*.Preview`.</span><span class="sxs-lookup"><span data-stu-id="72fbb-112">This naming convention is similar to the naming of Preview modules: `AzureRM.*.Preview`.</span></span> <span data-ttu-id="72fbb-113">Preview-modules zijn iets anders dan experimentele modules.</span><span class="sxs-lookup"><span data-stu-id="72fbb-113">Preview modules differ from experimental modules.</span></span> <span data-ttu-id="72fbb-114">Preview-modules implementeren nieuwe functionaliteit van Azure-services die alleen beschikbaar is als een Preview-aanbieding.</span><span class="sxs-lookup"><span data-stu-id="72fbb-114">Preview modules implement new functionality of Azure services that is only available as a Preview offering.</span></span> <span data-ttu-id="72fbb-115">Preview-modules vervangen bestaande Azure PowerShell-modules en gebruiken dezelfde namen voor cmdlets en parameters.</span><span class="sxs-lookup"><span data-stu-id="72fbb-115">Preview modules replace existing Azure PowerShell modules and use the same cmdlet and parameter names.</span></span>

## <a name="how-to-install-an-experimental-module"></a><span data-ttu-id="72fbb-116">Een experimentele module installeren</span><span class="sxs-lookup"><span data-stu-id="72fbb-116">How to install an experimental module</span></span>

<span data-ttu-id="72fbb-117">Experimentele modules worden gepubliceerd in PowerShell Gallery, net als de bestaande Azure PowerShell-modules.</span><span class="sxs-lookup"><span data-stu-id="72fbb-117">Experimental modules are published to the PowerShell Gallery just like the existing Azure PowerShell modules.</span></span> <span data-ttu-id="72fbb-118">Voer de volgende opdracht uit om een overzicht met experimentele modules weer te geven:</span><span class="sxs-lookup"><span data-stu-id="72fbb-118">To see a list of experimental modules, run the following command:</span></span>

```powershell
Find-Module AzureRM.*.Experiments
```

```Output
Version Name                         Repository Description
------- ----                         ---------- -----------
1.0.25  AzureRM.Compute.Experiments  PSGallery  Azure Compute experiments for VM creation
1.0.0   AzureRM.Websites.Experiments PSGallery  Create and deploy web applications using Azure App Services.
```

<span data-ttu-id="72fbb-119">Als u een experimentele module wilt installeren, gebruikt u de volgende opdrachten vanuit een PowerShell-sessie met verhoogde bevoegdheden:</span><span class="sxs-lookup"><span data-stu-id="72fbb-119">To install the experimental module, use the following commands from an elevated PowerShell session:</span></span>

```powershell
Install-Module AzureRM.Compute.Experiments
Install-Module AzureRM.Websites.Experiments
```

### <a name="documentation-and-support"></a><span data-ttu-id="72fbb-120">Documentatie en ondersteuning</span><span class="sxs-lookup"><span data-stu-id="72fbb-120">Documentation and support</span></span>

<span data-ttu-id="72fbb-121">Documentatie is opgenomen in het installatiepakket en kan worden geraadpleegd via de cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="72fbb-121">Documentation is included in the install package and is accessed using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="72fbb-122">Er wordt geen officiële documentatie gepubliceerd voor experimentele modules.</span><span class="sxs-lookup"><span data-stu-id="72fbb-122">No official documentation is published for experimental modules.</span></span>

<span data-ttu-id="72fbb-123">We willen u vragen om deze modules te testen.</span><span class="sxs-lookup"><span data-stu-id="72fbb-123">We encourage you to test these modules.</span></span> <span data-ttu-id="72fbb-124">Aan de hand van uw feedback kunnen we de bruikbaarheid verbeteren en reageren op uw verzoeken.</span><span class="sxs-lookup"><span data-stu-id="72fbb-124">Your feedback allows us to improve usability and respond to your needs.</span></span> <span data-ttu-id="72fbb-125">Vanwege het experimentele karakter is de ondersteuning voor deze modules echter beperkt.</span><span class="sxs-lookup"><span data-stu-id="72fbb-125">However, being experimental, support for these modules is limited.</span></span> <span data-ttu-id="72fbb-126">Vragen of problemen kunt u melden door een [issue](https://github.com/Azure/azure-powershell/issues) toe te voegen op GitHub.</span><span class="sxs-lookup"><span data-stu-id="72fbb-126">Questions or problem reports can be submitted by creating an [issue](https://github.com/Azure/azure-powershell/issues) in the GitHub repository.</span></span>

## <a name="experiments-and-areas-of-improvement"></a><span data-ttu-id="72fbb-127">Experimenten en verbeterpunten</span><span class="sxs-lookup"><span data-stu-id="72fbb-127">Experiments and areas of improvement</span></span>

<span data-ttu-id="72fbb-128">Deze verbeteringen zijn geselecteerd op basis van belangrijke differentiators in concurrerende producten.</span><span class="sxs-lookup"><span data-stu-id="72fbb-128">These improvements were selected based on key differentiators in competing products.</span></span> <span data-ttu-id="72fbb-129">Zo is de verbetering in Azure CLI 2.0 bijvoorbeeld dat opdrachten worden gebaseerd op _scenario's_ in plaats van een _API surface area_.</span><span class="sxs-lookup"><span data-stu-id="72fbb-129">For example, Azure CLI 2.0 has made a point of basing commands on _scenarios_ rather than _API surface area_.</span></span>
<span data-ttu-id="72fbb-130">In Azure CLI 2.0 worden verschillende slimme standaardinstellingen gebruikt waardoor eindgebruikers de beschikking krijgen over scenario's waarmee ze snel aan de slag kunnen.</span><span class="sxs-lookup"><span data-stu-id="72fbb-130">Azure CLI 2.0 use a number of smart defaults that make "getting started" scenarios easier for end users.</span></span>

### <a name="core-improvements"></a><span data-ttu-id="72fbb-131">Essentiële verbeteringen</span><span class="sxs-lookup"><span data-stu-id="72fbb-131">Core improvements</span></span>

<span data-ttu-id="72fbb-132">De essentiële verbeteringen worden beschouwd als 'logisch', en er zijn weinig experimenten nodig om deze updates te implementeren.</span><span class="sxs-lookup"><span data-stu-id="72fbb-132">The core improvements are regarded as "common sense", and little experimentation is needed to move forward in implementing these updates.</span></span>

- <span data-ttu-id="72fbb-133">Op scenario's gebaseerde cmdlets: \**All*-cmdlets moeten worden gebaseerd op scenario's, niet op de REST-service van Azure.</span><span class="sxs-lookup"><span data-stu-id="72fbb-133">Scenario-based Cmdlets - \**All*- cmdlets should be designed around scenarios, not the Azure REST service.</span></span>

- <span data-ttu-id="72fbb-134">Kortere namen: geldt voor de namen van cmdlets (bijvoorbeeld `New-AzureRmVM` => `New-AzVm`) en van parameters (bijvoorbeeld `-ResourceGroupName` => `-Rg`).</span><span class="sxs-lookup"><span data-stu-id="72fbb-134">Shorter Names - Includes the names of cmdlets (for example, `New-AzureRmVM` => `New-AzVm`) and the names of parameters (for example, `-ResourceGroupName` => `-Rg`).</span></span> <span data-ttu-id="72fbb-135">Aliassen gebruiken voor compatibiliteit met 'oude' cmdlets.</span><span class="sxs-lookup"><span data-stu-id="72fbb-135">Use aliases for compatibility with "old" cmdlets.</span></span> <span data-ttu-id="72fbb-136">_Achterwaarts compatibele_ parametersets aanbieden.</span><span class="sxs-lookup"><span data-stu-id="72fbb-136">Provide _backwards compatible_ parameter sets.</span></span>

- <span data-ttu-id="72fbb-137">Slimme standaardwaarden: slimme standaardwaarden ontwikkelen om 'vereiste' gegevens automatisch in te vullen.</span><span class="sxs-lookup"><span data-stu-id="72fbb-137">Smart Defaults - Create smart defaults to fill in "required" information.</span></span> <span data-ttu-id="72fbb-138">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="72fbb-138">For example:</span></span>
  - <span data-ttu-id="72fbb-139">Resourcegroep</span><span class="sxs-lookup"><span data-stu-id="72fbb-139">Resource Group</span></span>
  - <span data-ttu-id="72fbb-140">Locatie</span><span class="sxs-lookup"><span data-stu-id="72fbb-140">Location</span></span>
  - <span data-ttu-id="72fbb-141">Afhankelijke resources</span><span class="sxs-lookup"><span data-stu-id="72fbb-141">Dependent resources</span></span>

### <a name="experimental-improvements"></a><span data-ttu-id="72fbb-142">Experimentele verbeteringen</span><span class="sxs-lookup"><span data-stu-id="72fbb-142">Experimental improvements</span></span>

<span data-ttu-id="72fbb-143">De experimentele verbeteringen vertegenwoordigen een ingrijpende wijziging die het team wil valideren via experimenten.</span><span class="sxs-lookup"><span data-stu-id="72fbb-143">The experimental improvements present a significant change that the team wants to validate via experimentation.</span></span>

- <span data-ttu-id="72fbb-144">Eenvoudige typen: maakscenario's moeten afstappen van complexe typen en configuratieobjecten.</span><span class="sxs-lookup"><span data-stu-id="72fbb-144">Simple types - Create scenarios should move away from complex types and config objects.</span></span> <span data-ttu-id="72fbb-145">Vereenvoudig de configuratie tot een of twee parameters.</span><span class="sxs-lookup"><span data-stu-id="72fbb-145">Simplify the configuration down to one or two parameters.</span></span>

- <span data-ttu-id="72fbb-146">'Slim maken': alle maakscenario's die worden geïmplementeerd met 'slim maken' hebben _geen_ vereiste parameters. Alle benodigde gegevens worden door Azure PowerShell gekozen.</span><span class="sxs-lookup"><span data-stu-id="72fbb-146">"Smart Create" - All create scenarios implementing "Smart Create" would have _no_ required parameters: all necessary information would be chosen by Azure PowerShell in an opinionated fashion.</span></span>

- <span data-ttu-id="72fbb-147">Grijze parameters: in veel gevallen kunnen bepaalde parameters 'grijs' of semi-optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="72fbb-147">Gray Parameters - In many cases, some parameters could be "gray" or semi-optional.</span></span> <span data-ttu-id="72fbb-148">Als de parameter niet is opgegeven, wordt de gebruiker gevraagd of de parameter moet worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="72fbb-148">If the parameter is not specified, the user is asked if they want the parameter generated for them.</span></span> <span data-ttu-id="72fbb-149">Het is ook logisch voor grijze parameters dat hiervoor een waarde wordt afgeleid op basis van de context, uiteraard met toestemming van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="72fbb-149">It also makes sense for gray parameters to infer a value based on context with the user's consent.</span></span>
  <span data-ttu-id="72fbb-150">Het is bijvoorbeeld mogelijk dat het logisch is dat voor een grijze parameter de meest recent gebruikte waarde wordt voorgesteld.</span><span class="sxs-lookup"><span data-stu-id="72fbb-150">For example, it may make sense to have the gray parameter suggest the most recently used value.</span></span>

- <span data-ttu-id="72fbb-151">Parameter `-Auto`: de parameter `-Auto` kan een manier zijn voor gebruikers om aan te geven dat ze _overal de standaardinstellingen_ willen gebruiken zonder dat dit ten koste gaat van de integriteit van vereiste hoofdparameters.</span><span class="sxs-lookup"><span data-stu-id="72fbb-151">`-Auto` Switch - The `-Auto` switch would provide an "opt-in" way for users to _default all the things_ while maintaining the integrity of required parameters in the mainline path.</span></span>

### <a name="feature-specific-switches"></a><span data-ttu-id="72fbb-152">Functiespecifieke parameters</span><span class="sxs-lookup"><span data-stu-id="72fbb-152">Feature-specific switches</span></span>

<span data-ttu-id="72fbb-153">Het scenario 'Web-app maken' kan bijvoorbeeld een parameter `-Git` of `-AddRemote` bevatten waarmee automatisch een 'azure' remote wordt toegevoegd aan een bestaande git-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="72fbb-153">For example, the "Create web app" scenario might have a `-Git` or `-AddRemote` switch that would automatically add an "azure" remote to an existing git repository.</span></span>

- <span data-ttu-id="72fbb-154">Instelbare standaardwaarden: gebruikers moeten de mogelijkheid hebben om standaardwaarden op te geven voor bepaalde veelgebruikte parameters, zoals `-ResourceGroupName` en `-Location`.</span><span class="sxs-lookup"><span data-stu-id="72fbb-154">Settable Defaults - Users should have the ability to default certain ubiquitous parameters like `-ResourceGroupName` and `-Location`.</span></span>

- <span data-ttu-id="72fbb-155">Standaardgrootten: de 'grootten' voor resources kunnen verwarrend zijn voor gebruikers, aangezien veel providers van resources verschillende namen gebruiken (bijvoorbeeld 'Standard\_DS1\_v2' of 'S1').</span><span class="sxs-lookup"><span data-stu-id="72fbb-155">Size Defaults - Resource "sizes" can be confusing to users since many Resource Providers use different names (for example, "Standard\_DS1\_v2" or "S1").</span></span> <span data-ttu-id="72fbb-156">De meeste gebruikers zijn echter meer geïnteresseerd in de kosten.</span><span class="sxs-lookup"><span data-stu-id="72fbb-156">However, most users care more about cost.</span></span> <span data-ttu-id="72fbb-157">Om die reden is het logisch om 'universele' grootten te definiëren op basis van een prijscategorie.</span><span class="sxs-lookup"><span data-stu-id="72fbb-157">Therefore, it makes sense to define "universal" sizes based on a pricing schedule.</span></span> <span data-ttu-id="72fbb-158">Gebruikers kunnen een specifieke grootte kiezen of Azure PowerShell de _beste optie_ laten kiezen op basis van de resource of het budget.</span><span class="sxs-lookup"><span data-stu-id="72fbb-158">Users can choose a specific size or let Azure PowerShell choose the _best option_ based on the resource the budget.</span></span>

- <span data-ttu-id="72fbb-159">Indeling van uitvoer: op dit moment retourneert Azure PowerShell een `PSObject` en verder is er weinig console-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="72fbb-159">Output Format - Azure PowerShell currently returns `PSObject`s and there is little console output.</span></span> <span data-ttu-id="72fbb-160">Azure PowerShell zal mogelijk bepaalde informatie moeten weergeven voor de gebruiker met betrekking tot de gebruikte 'slimme standaardinstellingen'.</span><span class="sxs-lookup"><span data-stu-id="72fbb-160">Azure PowerShell may need to display some information to the user regarding the "smart defaults" used.</span></span>
