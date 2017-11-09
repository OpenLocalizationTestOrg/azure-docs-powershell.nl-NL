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
# <a name="release-notes"></a><span data-ttu-id="cce71-103">Releaseopmerkingen</span><span class="sxs-lookup"><span data-stu-id="cce71-103">Release notes</span></span>

<span data-ttu-id="cce71-104">Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cce71-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <a name="version-380"></a><span data-ttu-id="cce71-105">Versie 3.8.0</span><span class="sxs-lookup"><span data-stu-id="cce71-105">Version 3.8.0</span></span>
* <span data-ttu-id="cce71-106">Compute</span><span class="sxs-lookup"><span data-stu-id="cce71-106">Compute</span></span>
  - <span data-ttu-id="cce71-107">De fout in de Get-*-cmdlets is verholpen, zodat er nu ook meerdere pagina's met gegevens (meer dan 120 items) kunnen worden opgehaald</span><span class="sxs-lookup"><span data-stu-id="cce71-107">Fix bug in Get-* cmdlets, to allow retrieving multiple pages of data (more than 120 items)</span></span>
* <span data-ttu-id="cce71-108">DataLakeAnalytics</span><span class="sxs-lookup"><span data-stu-id="cce71-108">DataLakeAnalytics</span></span>
  - <span data-ttu-id="cce71-109">Fouten in de Help-informatie voor bepaalde opdrachten zijn verholpen, zodat hier nu de correcte teksten en voorbeelden worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cce71-109">Fix help for some commands to have the proper verbage and examples.</span></span>
* <span data-ttu-id="cce71-110">DataLakeStore</span><span class="sxs-lookup"><span data-stu-id="cce71-110">DataLakeStore</span></span>
  - <span data-ttu-id="cce71-111">Er is ondersteuning toegevoegd voor de kop en staart van de cmdlet `Get-AzureRMDataLakeStoreItemContent`.</span><span class="sxs-lookup"><span data-stu-id="cce71-111">Add support for head and tail to the `Get-AzureRMDataLakeStoreItemContent` cmdlet.</span></span> <span data-ttu-id="cce71-112">Hierdoor kunnen de geretourneerde bovenste N of laatste N door nieuwe regels gescheiden rijen worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cce71-112">This enables returning the top N or last N new line delimited rows to be displayed.</span></span>
* <span data-ttu-id="cce71-113">HDInsight</span><span class="sxs-lookup"><span data-stu-id="cce71-113">HDInsight</span></span>
  - <span data-ttu-id="cce71-114">Er is ondersteuning toegevoegd voor het RServer-clustertype</span><span class="sxs-lookup"><span data-stu-id="cce71-114">Added support for RServer cluster type</span></span>
    + <span data-ttu-id="cce71-115">De VM-grootte van het edge-knooppunt kan worden opgegeven voor het RServer-cluster in New-AzureRmHDInsightCluster of New-AzureRmHDInsightClusterConfig</span><span class="sxs-lookup"><span data-stu-id="cce71-115">Edgenode VM size can be specified for RServer cluster in New-AzureRmHDInsightCluster or New-AzureRmHDInsightClusterConfig</span></span>
    + <span data-ttu-id="cce71-116">RServer is nu een configuratieoptie in Add-AzureRmHDInsightConfigValues.</span><span class="sxs-lookup"><span data-stu-id="cce71-116">RServer is now a configuration option in Add-AzureRmHDInsightConfigValues.</span></span> <span data-ttu-id="cce71-117">Hierdoor kan de RStudio-vlag zo worden ingesteld dat wordt aangegeven dat de installatie van RStudio moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cce71-117">It allows for RStudio flag to be set to indicate that R Studio installation should be done.</span></span>
* <span data-ttu-id="cce71-118">LogicApp</span><span class="sxs-lookup"><span data-stu-id="cce71-118">LogicApp</span></span>
  - <span data-ttu-id="cce71-119">Het contentlink-probleem met de cmdlets Set-AzureRmIntegrationAccountSchema en Set-AzureRmIntegrationAccountMap is verholpen (zowel content als contentlink was ingesteld, wat resulteerde in een mislukte update).</span><span class="sxs-lookup"><span data-stu-id="cce71-119">Set-AzureRmIntegrationAccountSchema and Set-AzureRmIntegrationAccountMap cmdlets are fixed for the contentlink issue(Both content and contentlink were set resulting in update failure).</span></span>
* <span data-ttu-id="cce71-120">Netwerk</span><span class="sxs-lookup"><span data-stu-id="cce71-120">Network</span></span>
  - <span data-ttu-id="cce71-121">Aan toepassingsgateways is ondersteuning toegevoegd voor nieuwe firewallfuncties voor webtoepassingen</span><span class="sxs-lookup"><span data-stu-id="cce71-121">Added support for new web application firewall features to Application Gateways</span></span>
    + <span data-ttu-id="cce71-122">New-AzureRmApplicationGatewayFirewallDisabledRuleGroupConfig is toegevoegd</span><span class="sxs-lookup"><span data-stu-id="cce71-122">Added New-AzureRmApplicationGatewayFirewallDisabledRuleGroupConfig</span></span>
    + <span data-ttu-id="cce71-123">Get-AzureRmApplicationGatewayAvailableWafRuleSets (alias: List-AzureRmApplicationGatewayAvailableWafRuleSets) is toegevoegd</span><span class="sxs-lookup"><span data-stu-id="cce71-123">Added Get-AzureRmApplicationGatewayAvailableWafRuleSets (Alias: List-AzureRmApplicationGatewayAvailableWafRuleSets)</span></span>
    + <span data-ttu-id="cce71-124">New-AzureRmApplicationGatewayWebApplicationFirewallConfiguration is bijgewerkt. De parameters -RuleSetType, -RuleSetVersion en -DisabledRuleGroups zijn toegevoegd</span><span class="sxs-lookup"><span data-stu-id="cce71-124">Updated New-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Added parameter -RuleSetType -RuleSetVersion and -DisabledRuleGroups</span></span>
    + <span data-ttu-id="cce71-125">Set-AzureRmApplicationGatewayWebApplicationFirewallConfiguration is bijgewerkt. De parameters -RuleSetType, -RuleSetVersion en -DisabledRuleGroups zijn toegevoegd</span><span class="sxs-lookup"><span data-stu-id="cce71-125">Updated Set-AzureRmApplicationGatewayWebApplicationFirewallConfiguration: Added parameter -RuleSetType -RuleSetVersion and -DisabledRuleGroups</span></span>
  - <span data-ttu-id="cce71-126">Aan virtuele netwerkgatewayverbindingen is ondersteuning toegevoegd voor IPSec-beleid</span><span class="sxs-lookup"><span data-stu-id="cce71-126">Added support for IPSec policies to Virtual Network Gateway Connections</span></span>
  - <span data-ttu-id="cce71-127">New-AzureRmIpsecPolicy is toegevoegd</span><span class="sxs-lookup"><span data-stu-id="cce71-127">Added New-AzureRmIpsecPolicy</span></span>
  - <span data-ttu-id="cce71-128">New-AzureRmVirtualNetworkGatewayConnection is bijgewerkt. De parameters -IpsecPolicies en -UsePolicyBasedTrafficSelectors zijn toegevoegd</span><span class="sxs-lookup"><span data-stu-id="cce71-128">Updated New-AzureRmVirtualNetworkGatewayConnection: Added parameter -IpsecPolicies and -UsePolicyBasedTrafficSelectors</span></span>
* <span data-ttu-id="cce71-129">Profiel</span><span class="sxs-lookup"><span data-stu-id="cce71-129">Profile</span></span>
  - <span data-ttu-id="cce71-130">*Verouderd*: Save-AzureRmProfile is gewijzigd in Save-AzureRmContext. Er is een alias voor de oude cmdlet-naam. De alias wordt in de volgende release verwijderd.</span><span class="sxs-lookup"><span data-stu-id="cce71-130">*Obsolete*: Save-AzureRmProfile is renamed to Save-AzureRmContext, there is an alias to the old cmdlet name, the alias will be removed in the next release.</span></span>
  - <span data-ttu-id="cce71-131">*Verouderd*: Select-AzureRmProfile is gewijzigd in Import-AzureRmContext. Er is een alias voor de oude cmdlet-naam. De alias wordt in de volgende release verwijderd.</span><span class="sxs-lookup"><span data-stu-id="cce71-131">*Obsolete*: Select-AzureRmProfile is renamed to Import-AzureRmContext, there is an alias to the old cmdlet name, the alias will be removed in the next release.</span></span>
  - <span data-ttu-id="cce71-132">De PSAzureContext- en PSAzureProfile-uitvoertypen van profiel-cmdlets worden in de volgende release gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="cce71-132">The PSAzureContext and PSAzureProfile output types of profile cmdlets will be changed in the next release.</span></span>
  - <span data-ttu-id="cce71-133">De Save-AzureRmContext-cmdlet heeft geen uitvoertype in de volgende release.</span><span class="sxs-lookup"><span data-stu-id="cce71-133">The Save-AzureRmContext cmdlet will have no OutputType in the next release.</span></span>
  - <span data-ttu-id="cce71-134">De fout in de gezamenlijke cmdlet-code om het FIPS-compatibele algoritme voor gegevenshashes te gebruiken, is verholpen: https://github.com/Azure/azure-powershell/issues/3651</span><span class="sxs-lookup"><span data-stu-id="cce71-134">Fix bug in cmdlet common code to use FIPS-compliant algorithm for data hashes: https://github.com/Azure/azure-powershell/issues/3651</span></span>
* <span data-ttu-id="cce71-135">SQL</span><span class="sxs-lookup"><span data-stu-id="cce71-135">Sql</span></span>
  - <span data-ttu-id="cce71-136">De problemen met failovergroep-cmdlets van Azure zijn verholpen</span><span class="sxs-lookup"><span data-stu-id="cce71-136">Bug fixes on Azure Failover Group Cmdlets</span></span>
  - <span data-ttu-id="cce71-137">Het probleem met bewerkingspolling is verholpen</span><span class="sxs-lookup"><span data-stu-id="cce71-137">Fix for operation polling</span></span>
  - <span data-ttu-id="cce71-138">Het probleem met de GracePeriodWithDataLossHour-waarde wanneer FailoverPolicy naar Handmatig wordt ingesteld, is verholpen</span><span class="sxs-lookup"><span data-stu-id="cce71-138">Fix GracePeriodWithDataLossHour value when setting FailoverPolicy to Manual</span></span>
* <span data-ttu-id="cce71-139">TrafficManager</span><span class="sxs-lookup"><span data-stu-id="cce71-139">TrafficManager</span></span>
  - <span data-ttu-id="cce71-140">Ondersteuning voor de geografische verkeersrouteringsmethode</span><span class="sxs-lookup"><span data-stu-id="cce71-140">Support for the Geographic traffic routing method</span></span>
    + <span data-ttu-id="cce71-141">Nieuwe waarde Geografisch voor de TrafficRoutingMethod-parameter van New-AzureRmTrafficManagerProfile</span><span class="sxs-lookup"><span data-stu-id="cce71-141">New value 'Geographic' for the TrafficRoutingMethod parameter of New-AzureRmTrafficManagerProfile</span></span>
    + <span data-ttu-id="cce71-142">Nieuwe parameter GeoMapping voor New-AzureRmTrafficManagerEndpoint en Add-AzureRmTrafficManagerEndpointConfig</span><span class="sxs-lookup"><span data-stu-id="cce71-142">New parameter 'GeoMapping' for the New-AzureRmTrafficManagerEndpoint and Add-AzureRmTrafficManagerEndpointConfig</span></span>
    + <span data-ttu-id="cce71-143">Het probleem met het doorsluizen voor Get-AzureRmTrafficManagerProfile wanneer dit een verzameling profielen retourneert, is verholpen</span><span class="sxs-lookup"><span data-stu-id="cce71-143">Fix piping for Get-AzureRmTrafficManagerProfile when it returns a collection of profiles</span></span>
* <span data-ttu-id="cce71-144">ServiceManagement</span><span class="sxs-lookup"><span data-stu-id="cce71-144">ServiceManagement</span></span>
  - <span data-ttu-id="cce71-145">Restart-AzureVM: er is een InitiateMaintenance-parameter toegevoegd voor het uitvoeren van onderhoud tijdens het opnieuw opstarten van de virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="cce71-145">Restart-AzureVM: Added InitiateMaintenance parameter for performing maintenance during VM restart.</span></span>
  - <span data-ttu-id="cce71-146">Get-AzureVM: er is een onderhoudsstatusveld toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="cce71-146">Get-AzureVM: Added Maintenance Status field.</span></span>
  - <span data-ttu-id="cce71-147">Er zijn nieuwe cmdlets toegevoegd ter ondersteuning van een upgrade voor de Recovery Services-kluis</span><span class="sxs-lookup"><span data-stu-id="cce71-147">Added new cmdlets to support Recovery Services vault upgrade</span></span>
    + <span data-ttu-id="cce71-148">Test-AzureRecoveryServicesVaultUpgrade</span><span class="sxs-lookup"><span data-stu-id="cce71-148">Test-AzureRecoveryServicesVaultUpgrade</span></span>
    + <span data-ttu-id="cce71-149">Invoke-AzureRecoveryServicesVaultUpgrade</span><span class="sxs-lookup"><span data-stu-id="cce71-149">Invoke-AzureRecoveryServicesVaultUpgrade</span></span>
