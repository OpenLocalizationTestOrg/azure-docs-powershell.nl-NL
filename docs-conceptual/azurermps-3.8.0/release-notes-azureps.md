---
title: Azure PowerShell-wijzigingenlogboek | Microsoft Docs
description: Dit is de geschiedenis van de wijzigingen die in de nieuwste release van Azure PowerShell zijn doorgevoerd.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.service: azure-powershell
ms.product: azure
ms.devlang: powershell
ms.topic: conceptual
ms.workload: 
ms.date: 05/18/2017
ms.openlocfilehash: 04f89e8d47d0825d46cb1b8817efbcc0cafa0acd
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a>Releaseopmerkingen

Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.

## <a name="version-380"></a>Versie 3.8.0
* Compute
  - De fout in de Get-*-cmdlets is verholpen, zodat er nu ook meerdere pagina's met gegevens (meer dan 120 items) kunnen worden opgehaald
* DataLakeAnalytics
  - Fouten in de Help-informatie voor bepaalde opdrachten zijn verholpen, zodat hier nu de correcte teksten en voorbeelden worden weergegeven.
* DataLakeStore
  - Er is ondersteuning toegevoegd voor de kop en staart van de cmdlet `Get-AzureRMDataLakeStoreItemContent`. Hierdoor kunnen de geretourneerde bovenste N of laatste N door nieuwe regels gescheiden rijen worden weergegeven.
* HDInsight
  - Er is ondersteuning toegevoegd voor het RServer-clustertype
    + De VM-grootte van het edge-knooppunt kan worden opgegeven voor het RServer-cluster in New-AzureRmHDInsightCluster of New-AzureRmHDInsightClusterConfig
    + RServer is nu een configuratieoptie in Add-AzureRmHDInsightConfigValues. Hierdoor kan de RStudio-vlag zo worden ingesteld dat wordt aangegeven dat de installatie van RStudio moet worden uitgevoerd.
* LogicApp
  - Het contentlink-probleem met de cmdlets Set-AzureRmIntegrationAccountSchema en Set-AzureRmIntegrationAccountMap is verholpen (zowel content als contentlink was ingesteld, wat resulteerde in een mislukte update).
* Netwerk
  - Aan toepassingsgateways is ondersteuning toegevoegd voor nieuwe firewallfuncties voor webtoepassingen
    + New-AzureRmApplicationGatewayFirewallDisabledRuleGroupConfig is toegevoegd
    + Get-AzureRmApplicationGatewayAvailableWafRuleSets (alias: List-AzureRmApplicationGatewayAvailableWafRuleSets) is toegevoegd
    + New-AzureRmApplicationGatewayWebApplicationFirewallConfiguration is bijgewerkt. De parameters -RuleSetType, -RuleSetVersion en -DisabledRuleGroups zijn toegevoegd
    + Set-AzureRmApplicationGatewayWebApplicationFirewallConfiguration is bijgewerkt. De parameters -RuleSetType, -RuleSetVersion en -DisabledRuleGroups zijn toegevoegd
  - Aan virtuele netwerkgatewayverbindingen is ondersteuning toegevoegd voor IPSec-beleid
  - New-AzureRmIpsecPolicy is toegevoegd
  - New-AzureRmVirtualNetworkGatewayConnection is bijgewerkt. De parameters -IpsecPolicies en -UsePolicyBasedTrafficSelectors zijn toegevoegd
* Profiel
  - *Verouderd*: Save-AzureRmProfile is gewijzigd in Save-AzureRmContext. Er is een alias voor de oude cmdlet-naam. De alias wordt in de volgende release verwijderd.
  - *Verouderd*: Select-AzureRmProfile is gewijzigd in Import-AzureRmContext. Er is een alias voor de oude cmdlet-naam. De alias wordt in de volgende release verwijderd.
  - De PSAzureContext- en PSAzureProfile-uitvoertypen van profiel-cmdlets worden in de volgende release gewijzigd.
  - De Save-AzureRmContext-cmdlet heeft geen uitvoertype in de volgende release.
  - De fout in de gezamenlijke cmdlet-code om het FIPS-compatibele algoritme voor gegevenshashes te gebruiken, is verholpen: https://github.com/Azure/azure-powershell/issues/3651
* SQL
  - De problemen met failovergroep-cmdlets van Azure zijn verholpen
  - Het probleem met bewerkingspolling is verholpen
  - Het probleem met de GracePeriodWithDataLossHour-waarde wanneer FailoverPolicy naar Handmatig wordt ingesteld, is verholpen
* TrafficManager
  - Ondersteuning voor de geografische verkeersrouteringsmethode
    + Nieuwe waarde Geografisch voor de TrafficRoutingMethod-parameter van New-AzureRmTrafficManagerProfile
    + Nieuwe parameter GeoMapping voor New-AzureRmTrafficManagerEndpoint en Add-AzureRmTrafficManagerEndpointConfig
    + Het probleem met het doorsluizen voor Get-AzureRmTrafficManagerProfile wanneer dit een verzameling profielen retourneert, is verholpen
* ServiceManagement
  - Restart-AzureVM: er is een InitiateMaintenance-parameter toegevoegd voor het uitvoeren van onderhoud tijdens het opnieuw opstarten van de virtuele machine.
  - Get-AzureVM: er is een onderhoudsstatusveld toegevoegd.
  - Er zijn nieuwe cmdlets toegevoegd ter ondersteuning van een upgrade voor de Recovery Services-kluis
    + Test-AzureRecoveryServicesVaultUpgrade
    + Invoke-AzureRecoveryServicesVaultUpgrade
