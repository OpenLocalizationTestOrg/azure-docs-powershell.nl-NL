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
ms.sourcegitcommit: 9d2d35944106bdb6758853b050089bc804e6b9d2
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2017
---
# <a name="using-experimental-azure-powershell-modules"></a>Werken met experimentele Azure PowerShell-modules

Gezien de nadruk op tools voor ontwikkelaars (met name CLI's) in Azure, is het team van Azure PowerShell druk aan het experimenteren met allerlei verbeteringen van Azure PowerShell.

## <a name="experimentation-methodology"></a>Methodologie voor experimenten

Om dit proces van experimenteren te vergemakkelijken, maken we nieuwe Azure PowerShell-modules waarin bestaande functionaliteit uit de Azure SDK op nieuwe, eenvoudiger te gebruiken manieren wordt geïmplementeerd. In de meeste gevallen is de werking van deze cmdlets identiek aan die van bestaande cmdlets. De experimentele cmdlets hebben echter een verkorte syntaxis en slimmere standaardwaarden, waardoor het eenvoudiger is om Azure-resources te maken en te beheren.

Deze modules kunnen zonder problemen naast bestaande Azure PowerShell-modules worden geïnstalleerd. De namen van de cmdlets zijn ingekort om kortere namen mogelijk te maken en om naamconflicten met bestaande, niet-experimentele cmdlets te voorkomen.

De experimentele modules gebruiken de volgende naamconventie:

- AzureRM.Compute.Experiments
- AzureRM.Websites.Experiments

Deze naamconventie is vergelijkbaar met de naamgeving van Preview-modules: `AzureRM.*.Preview`. Preview-modules zijn iets anders dan experimentele modules. Preview-modules implementeren nieuwe functionaliteit van Azure-services die alleen beschikbaar is als een Preview-aanbieding. Preview-modules vervangen bestaande Azure PowerShell-modules en gebruiken dezelfde namen voor cmdlets en parameters.

## <a name="how-to-install-an-experimental-module"></a>Een experimentele module installeren

Experimentele modules worden gepubliceerd in PowerShell Gallery, net als de bestaande Azure PowerShell-modules. Voer de volgende opdracht uit om een overzicht met experimentele modules weer te geven:

```powershell
Find-Module AzureRM.*.Experiments
```

```Output
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      AzureRM.Websites.Experiments        PSGallery            Create and deploy web applications using Azure Ap...
1.0.25     AzureRM.Compute.Experiments         PSGallery            Azure Compute experiments for VM creation
```

Als u een experimentele module wilt installeren, gebruikt u de volgende opdrachten vanuit een PowerShell-sessie met verhoogde bevoegdheden:

```powershell
Install-Module AzureRM.Compute.Experiments
Install-Module AzureRM.Websites.Experiments
```

### <a name="documentation-and-support"></a>Documentatie en ondersteuning

Documentatie is opgenomen in het installatiepakket en kan worden geraadpleegd via de cmdlet `Get-Help`. Er wordt geen officiële documentatie gepubliceerd voor experimentele modules.

We willen u vragen om deze modules te testen. Aan de hand van uw feedback kunnen we de bruikbaarheid verbeteren en reageren op uw verzoeken. Vanwege het experimentele karakter is de ondersteuning voor deze modules echter beperkt. Vragen of problemen kunt u melden door een [issue](https://github.com/Azure/azure-powershell/issues) toe te voegen op GitHub.

## <a name="experiments-and-areas-of-improvement"></a>Experimenten en verbeterpunten

Deze verbeteringen zijn geselecteerd op basis van belangrijke differentiators in concurrerende producten. Zo is de verbetering in Azure CLI 2.0 bijvoorbeeld dat opdrachten worden gebaseerd op _scenario's_ in plaats van een _API surface area_.
In Azure CLI 2.0 worden verschillende slimme standaardinstellingen gebruikt waardoor eindgebruikers de beschikking krijgen over scenario's waarmee ze snel aan de slag kunnen.

### <a name="core-improvements"></a>Essentiële verbeteringen

De essentiële verbeteringen worden beschouwd als 'logisch', en er zijn weinig experimenten nodig om deze updates te implementeren.

- Op scenario's gebaseerde cmdlets: **All*-cmdlets moeten worden gebaseerd op scenario's, niet op de REST-service van Azure.

- Kortere namen: geldt voor de namen van cmdlets (bijvoorbeeld `New-AzureRmVM` => `New-AzVm`) en van parameters (bijvoorbeeld `-ResourceGroupName` => `-Rg`). Aliassen gebruiken voor compatibiliteit met 'oude' cmdlets. _Achterwaarts compatibele_ parametersets aanbieden.

- Slimme standaardwaarden: slimme standaardwaarden ontwikkelen om 'vereiste' gegevens automatisch in te vullen. Bijvoorbeeld:
  - Resourcegroep
  - Locatie
  - Afhankelijke resources

### <a name="experimental-improvements"></a>Experimentele verbeteringen

De experimentele verbeteringen vertegenwoordigen een ingrijpende wijziging die het team wil valideren via experimenten.

- Eenvoudige typen: maakscenario's moeten afstappen van complexe typen en configuratieobjecten. Vereenvoudig de configuratie tot een of twee parameters.

- 'Slim maken': alle maakscenario's die worden geïmplementeerd met 'slim maken' hebben _geen_ vereiste parameters. Alle benodigde gegevens worden door Azure PowerShell gekozen.

- Grijze parameters: in veel gevallen kunnen bepaalde parameters 'grijs' of semi-optioneel zijn. Als de parameter niet is opgegeven, wordt de gebruiker gevraagd of de parameter moet worden gegenereerd. Het is ook logisch voor grijze parameters dat hiervoor een waarde wordt afgeleid op basis van de context, uiteraard met toestemming van de gebruiker.
  Het is bijvoorbeeld mogelijk dat het logisch is dat voor een grijze parameter de meest recent gebruikte waarde wordt voorgesteld.

- Parameter `-Auto`: de parameter `-Auto` kan een manier zijn voor gebruikers om aan te geven dat ze _overal de standaardinstellingen_ willen gebruiken zonder dat dit ten koste gaat van de integriteit van vereiste hoofdparameters.

### <a name="feature-specific-switches"></a>Functiespecifieke parameters

Het scenario 'Web-app maken' kan bijvoorbeeld een parameter `-Git` of `-AddRemote` bevatten waarmee automatisch een 'azure' remote wordt toegevoegd aan een bestaande git-opslagplaats.

- Instelbare standaardwaarden: gebruikers moeten de mogelijkheid hebben om standaardwaarden op te geven voor bepaalde veelgebruikte parameters, zoals `-ResourceGroupName` en `-Location`.

- Standaardgrootten: de 'grootten' voor resources kunnen verwarrend zijn voor gebruikers, aangezien veel providers van resources verschillende namen gebruiken (bijvoorbeeld 'Standard\_DS1\_v2' of 'S1'). De meeste gebruikers zijn echter meer geïnteresseerd in de kosten. Om die reden is het logisch om 'universele' grootten te definiëren op basis van een prijscategorie. Gebruikers kunnen een specifieke grootte kiezen of Azure PowerShell de _beste optie_ laten kiezen op basis van de resource of het budget.

- Indeling van uitvoer: op dit moment retourneert Azure PowerShell een `PSObject` en verder is er weinig console-uitvoer. Azure PowerShell zal mogelijk bepaalde informatie moeten weergeven voor de gebruiker met betrekking tot de gebruikte 'slimme standaardinstellingen'.

## <a name="try-using-the-experiments"></a>Experimenteren

### <a name="install"></a>Installeren

```powershell
Install-Module AzureRM.Compute.Experiments
```

### <a name="create-a-vm"></a>Een virtuele machine maken

```powershell
$job = New-AzVm -Name MyVm -AsJob
Receive-Job $job
```

### <a name="send-us-feedback"></a>Feedback versturen

```powershell
Send-Feedback
```

### <a name="uninstall-the-experimental-modules"></a>De experimentele modules verwijderen

```powershell
Uninstall-Module AzureRM.Compute.Experiments
```