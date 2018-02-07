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
ms.date: 1/31/2018
ms.openlocfilehash: 8008da172a3d38ee7b07ff4a97a8cd0e0588b961
ms.sourcegitcommit: 72f56597f0329d35779a3ea4ccea6293f0fd2502
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/01/2018
---
# <a name="release-notes"></a>Releaseopmerkingen

Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.

---

## <a name="520---january-2018"></a>5.2.0 - januari 2018
#### <a name="azurermprofile"></a>AzureRM.Profile
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* Add-AzureRmAccount
  * Er is -MSI-aanmelding toegevoegd voor verificatie met behulp van de referenties van de beheerde service-identiteit van de huidige VM/service
  * Probleem met KeyVault-verificatie opgelost dat zich voordeed bij aanmelding met door gebruikers aangeleverde toegangstokens

#### <a name="azurestorage"></a>Azure.Storage
* Er zijn cmdlets toegevoegd om instellingen van de Storage-service op te halen en toe te passen
    - Get-AzureStorageServiceProperty
    - Update-AzureStorageServiceProperty

#### <a name="azurermanalysisservices"></a>AzureRM.AnalysisServices
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermapimanagement"></a>AzureRM.ApiManagement
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor New-AzureRmApiManagementProperty, Set-AzureRmApiManagementProperty en New-AzureRmApiManagement

#### <a name="azurermapplicationinsights"></a>AzureRM.ApplicationInsights
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermautomation"></a>AzureRM.Automation
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor Set-AzureRmAutomationRunbook

#### <a name="azurermbackup"></a>AzureRM.Backup
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermbatch"></a>AzureRM.Batch
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermcdn"></a>AzureRM.Cdn
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor New-AzureRmCdnEndpoint en New-AzureRmCdnProfile

#### <a name="azurermcognitiveservices"></a>AzureRM.CognitiveServices
* Integratie met versie 3.0.0 van Cognitive Services Management SDK.

#### <a name="azurermcompute"></a>AzureRM.Compute
* Er is een vereenvoudigde parameter toegevoegd, ingesteld op New-AzureRmVmss, die een virtuele-machineschaalset en alle vereiste resources maakt met slimme standaardinstellingen
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor New-AzureRmVm en Update-AzureRmVm
* Er is een probleem met de cmdlet Get-AzureRmComputeResourceSku hersteld dat zich voordeed wanneer Zone was opgenomen in de beperking.
* Het configuratieschema van Diagnostics Agent is bijgewerkt voor Azure Monitor-sinkondersteuning.

#### <a name="azurermcontainerinstance"></a>AzureRM.ContainerInstance
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermcontainerregistry"></a>AzureRM.ContainerRegistry
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermdatafactories"></a>AzureRM.DataFactories
* Azure Key Vault-ondersteuning is ingeschakeld voor alle gekoppelde gegevensopslagservices
* De licentietype-eigenschap is toegevoegd voor Azure SSIS-integratieruntime
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor New-AzureRmDataFactory

#### <a name="azurermdatafactoryv2"></a>AzureRM.DataFactoryV2
* Azure Key Vault-ondersteuning is ingeschakeld voor alle gekoppelde gegevensopslagservices
* De licentietype-eigenschap is toegevoegd voor Azure SSIS-integratieruntime
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* De parameter LicenseType voor de cmd Set-AzureRmDataFactoryV2IntegrationRuntime is toegevoegd om AHUB-functionaliteit in te schakelen

#### <a name="azurermdatalakeanalytics"></a>AzureRM.DataLakeAnalytics
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor New-AzureRmDataLakeAnalyticsAccount en Set-AzureRmDataLakeAnalyticsAccount

#### <a name="azurermdatalakestore"></a>AzureRM.DataLakeStore
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn vervangen door -Tag voor New-AzureRmDataLakeStoreAccount en Set-AzureRmDataLakeStoreAccount

#### <a name="azurermdevtestlabs"></a>AzureRM.DevTestLabs
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermdns"></a>AzureRM.Dns
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermeventgrid"></a>AzureRM.EventGrid
* De volgende nieuwe cmdlet is toegevoegd:
    - Update-AzureRmEventGridSubscription
        - De eigenschappen van een Event Grid-gebeurtenisabonnement zijn bijgewerkt.
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermeventhub"></a>AzureRM.EventHub
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermhdinsight"></a>AzureRM.HDInsight
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurerminsights"></a>AzureRM.Insights
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermiothub"></a>AzureRM.IotHub
* Er is certificaatondersteuning toegevoegd voor IoTHub-cmdlets
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermkeyvault"></a>AzureRM.KeyVault
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* Er is -AsJob-ondersteuning toegevoegd voor langlopende KeyVault-cmdlets. Hiermee kunt u geselecteerde cmdlets op de achtergrond uitvoeren en een taak retourneren om de voortgang te controleren en te beheren.
    * Het betreft de cmdlet Remove-AzureRmKeyVault
* De fout in Set-AzureRmKeyVaultAccessPolicy is hersteld waarbij het AAD-filter de SPN op de geleverde UPN instelde in plaats van de UPN in te stellen
   - Raadpleeg het volgende probleem voor meer informatie: https://github.com/Azure/azure-powershell/issues/5201

#### <a name="azurermlogicapp"></a>AzureRM.LogicApp
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermmachinelearning"></a>AzureRM.MachineLearning
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn vervangen door -Tag voor Update-AzureRmMlCommitmentPlan

#### <a name="azurermmachinelearningcompute"></a>AzureRM.MachineLearningCompute
* De parameter IncludeAllResources is toegevoegd aan de cmdlet Remove-AzureRmMlOpCluster
    - Met deze schakelparameter worden alle resources verwijderd die oorspronkelijk met het cluster zijn gemaakt
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermmedia"></a>AzureRM.Media
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor Set-AzureRmMediaService en New-AzureRmMediaService

#### <a name="azurermnetwork"></a>AzureRM.Network
* Er is -AsJob-ondersteuning toegevoegd voor langlopende Netwerk-cmdlets. Hiermee kunt u geselecteerde cmdlets op de achtergrond uitvoeren en een taak retourneren om de voortgang te controleren en te beheren.
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermnotificationhubs"></a>AzureRM.NotificationHubs
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor New-AzureRmNotificationHubsNamespace en Set-AzureRmNotificationHubsNamespace

#### <a name="azurermoperationalinsights"></a>AzureRM.OperationalInsights
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor New-AzureRmOperationalInsightsSavedSearch, Set-AzureRmOperationalInsightsSavedSearch, New-AzureRmOperationalInsightsWorkspace en Set-AzureRmOperationalInsightsWorkspace

#### <a name="azurermpowerbiembedded"></a>AzureRM.PowerBIEmbedded
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermrecoveryservices"></a>AzureRM.RecoveryServices
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermrecoveryservicesbackup"></a>AzureRM.RecoveryServices.Backup
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* De optie -UseOriginalStorageAccount is toegevoegd aan de cmdlet Restore-AzureRmRecoveryServicesBackupItem.
    - Als u deze vlag inschakelt, worden alle schijven naar hun oorspronkelijk opslagaccounts hersteld, zodat gebruikers de configuratie van herstelde VM's zo dicht mogelijk bij die van de oorspronkelijke VM's kunnen houden.
    - Ook worden hiermee de prestaties van de herstelbewerking verbeterd.

#### <a name="azurermrediscache"></a>AzureRM.RedisCache
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* Er zijn 3 nieuwe cmdlets voor firewallregels toegevoegd
* Er zijn 3 nieuwe cmdlets voor geo-replicatie toegevoegd
* Er is ondersteuning voor zones en tags toegevoegd
* ResourceGroup is waar mogelijk optioneel gemaakt.

#### <a name="azurermrelay"></a>AzureRM.Relay
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermresources"></a>AzureRM.Resources
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* Er is -AsJob-ondersteuning toegevoegd voor langlopende Resource-cmdlets. Hiermee kunt u geselecteerde cmdlets op de achtergrond uitvoeren en een taak retourneren om de voortgang te controleren en te beheren.
* Er is een alias toegevoegd van Get-AzureRmProviderOperation naar Get-AzureRmResourceProviderAction om te voldoen aan naamconventies

#### <a name="azurermscheduler"></a>AzureRM.Scheduler
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermservermanagement"></a>AzureRM.ServerManagement
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* -Tags zijn overbodig gemaakt en vervangen door -Tag voor New-AzureRmServerManagementNode en New-AzureRmServerManagementGateway

#### <a name="azurermservicebus"></a>AzureRM.ServiceBus
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermservicefabric"></a>AzureRM.ServiceFabric
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermsiterecovery"></a>AzureRM.SiteRecovery
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermsql"></a>AzureRM.Sql
* De parameterbeschrijving van controleopdrachten is bijgewerkt
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* Er is een -AsJob-parameter toegevoegd aan langlopende cmdlets
* De parameter -DatabaseName is overbodig gemaakt in Get-AzureRmSqlServiceObjective

#### <a name="azurermstorage"></a>AzureRM.Storage
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* Een probleem met een null-verwijzing is opgelost bij het uitvoeren van de cmdlet New-AzureRMStorageAccount met de parameter -EnableEncryptionService None
* Er is -AsJob-ondersteuning toegevoegd voor langlopende Storage-cmdlets. Hiermee kunt u geselecteerde cmdlets op de achtergrond uitvoeren en een taak retourneren om de voortgang te controleren en te beheren.
    - Het betreft de cmdlets New-, Remove-, Add- en Update- voor Storage Account en Storage Account Network Rule.

#### <a name="azurermstreamanalytics"></a>AzureRM.StreamAnalytics
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermtrafficmanager"></a>AzureRM.TrafficManager
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt

#### <a name="azurermwebsites"></a>AzureRM.Websites
* Er is een Location Completer toegevoegd aan Location-parameters, wat tabvoltooiing via geldige locaties mogelijk maakt
* Er is een ResourceGroup Completer toegevoegd aan -ResourceGroup-parameters, wat tabvoltooiing via resourcegroepen in het huidige abonnement mogelijk maakt
* Er is -AsJob-ondersteuning toegevoegd voor langlopende Websites-cmdlets. Hiermee kunt u geselecteerde cmdlets op de achtergrond uitvoeren en een taak retourneren om de voortgang te controleren en te beheren.
     - Het betreft de cmdlets New-, Remove-, Add- en Set- voor WebApps, AppServicePlan en Slots


## <a name="20171208-version-511"></a>08-12-2017 versie 5.1.1
* AnalysisServices
    - Valideren van ingestelde locatie gewijzigd in dynamisch opzoeken, zodat alle clouds worden ondersteund.
* Automatisering
    - Bijgewerkt naar Import-AzureRMAutomationRunbook
        - Er wordt nu ondersteuning geboden voor Python2-runbooks
* Batch
    - Er is een fout verholpen waarbij accountbewerkingen zonder resourcegroep niet automatisch een resourcegroep konden detecteren
* Compute
    - Get-AzureRmComputeResourceSku laat zone-informatie zien.
    - Disable-AzureRmVmssDiskEncryption is bijgewerkt om probleem https://github.com/Azure/azure-powershell/issues/5038 op te lossen
    - Er is -AsJob-ondersteuning toegevoegd voor langlopende Compute-cmdlets. Hiermee kunt u geselecteerde cmdlets op de achtergrond uitvoeren en een taak retourneren om de voortgang te controleren en te beheren.
        - Cmdlets waarop dit invloed heeft: New-, Update-, Set-, Remove-, Start-, Restart- en Stop- voor virtuele machines en virtuele-machineschaalsets
    - Er is een vereenvoudigde parameter toegevoegd, ingesteld op New-AzureRmVM, die een virtuele machine en alle vereiste resources maakt met gebruik van slimme standaardinstellingen
* ContainerInstance
    - Azure Container Instance-SDK 2017-10-01 is toegepast
        - Ondersteuning voor container uitvoeren tot voltooiing
        - Ondersteuning voor koppeling van Azure File-volumes
        - Ondersteuning voor het openen van meerdere poorten voor openbaar IP
* ContainerRegistry
    - Nieuwe cmdlets voor geo-replicatie en webhooks
        - Get/New/Remove-AzureRmContainerRegistryReplication
        - Get/New/Remove/Test/Update-AzureRmContainerRegistryWebhook
* DataFactories
    - Functionaliteit voor referentieversleuteling werkt nu zowel met Externe toegang ingeschakeld (via netwerk) als Externe toegang uitgeschakeld (lokale computer).
* DataFactoryV2
    - Er zijn twee nieuwe cmdlets toegevoegd: Update-AzureRmDataFactoryV2 en Stop-AzureRmDataFactoryV2PipelineRun
* DataLakeAnalytics
    - Er is een parameter met de naam ScriptParameter toegevoegd aan Submit-AzureRmDataLakeAnalyticsJob
        - Gedetailleerde informatie over ScriptParameter kan met Get-Help worden geraadpleegd in Submit-AzureRmDataLakeAnalyticsJob
    - Voor New-AzureRmDataLakeAnalyticsAccount is de parameter MaxDegreeOfParallelism gewijzigd in MaxAnalyticsUnits
        - Er is een alias toegevoegd voor de parameter MaxAnalyticsUnits: MaxDegreeOfParallelism
    - Voor New-AzureRmDataLakeAnalyticsComputePolicy is de parameter MaxDegreeOfParallelismPerJob gewijzigd in MaxAnalyticsUnitsPerJob
        - Er is een alias toegevoegd voor de parameter MaxAnalyticsUnitsPerJob: MaxDegreeOfParallelismPerJob
    - Voor Set-AzureRmDataLakeAnalyticsAccount is de parameter MaxDegreeOfParallelism gewijzigd in MaxAnalyticsUnits
        - Er is een alias toegevoegd voor de parameter MaxAnalyticsUnits: MaxDegreeOfParallelism
    - Voor Submit-AzureRmDataLakeAnalyticsJob is de parameter DegreeOfParallelism gewijzigd in AnalyticsUnits
        - Er is een alias toegevoegd voor de parameter AnalyticsUnits: DegreeOfParallelism
    - Voor Update-AzureRmDataLakeAnalyticsComputePolicy is de parameter MaxDegreeOfParallelismPerJob gewijzigd in MaxAnalyticsUnitsPerJob
        - Er is een alias toegevoegd voor de parameter MaxAnalyticsUnitsPerJob: MaxDegreeOfParallelismPerJob
* MachineLearningCompute
    - Set-AzureRmMlOpCluster toegevoegd
        - Het aantal agents of de SSL-configuratie van een cluster bijwerken
    - Orchestrator-eigenschappen zijn optioneel
        - De service maakt een service-principal als deze niet is opgegeven, waardoor de orchestrator-eigenschappen nu optioneel zijn
* PowerBIEmbedded
    - Ondersteuning voor cmdlets voor Power BI Embedded-capaciteit toegevoegd
    - Nieuwe cmdlet Get-AzureRmPowerBIEmbeddedCapacity - haalt de details van een Power BI Embedded-capaciteit op.
    - Nieuwe cmdlet New-AzureRmPowerBIEmbeddedCapacity - maakt een nieuwe Power BI Embedded-capaciteit
    - Nieuwe cmdlet Remove-AzureRmPowerBIEmbeddedCapacity - verwijdert een exemplaar van Power BI Embedded-capaciteit
    - Nieuwe cmdlet Resume-AzureRmPowerBIEmbeddedCapacity - hervat een exemplaar van een Power BI Embedded-capaciteit
    - Nieuwe cmdlet Suspend-AzureRmPowerBIEmbeddedCapacity - onderbreekt een exemplaar van een Power BI Embedded-capaciteit
    - Nieuwe cmdlet Test-AzureRmPowerBIEmbeddedCapacity - controleert het bestaan van een exemplaar van een Power BI Embedded-capaciteit
    - Nieuwe cmdlet Update-AzureRmPowerBIEmbeddedCapacity - wijzigt een exemplaar van een Power BI Embedded-capaciteit
* Profiel
    - USGovernmentActiveDirectoryEndpoint bijgewerkt naar https://login.microsoftonline.us/
        - Voor meer informatie over de toewijzingen van Azure Government-eindpunten: https://docs.microsoft.com/en-us/azure/azure-government/documentation-government-developer-guide#endpoint-mapping
    - Er is -AsJob-ondersteuning voor cmdlets toegevoegd, waardoor geselecteerde cmdlets op de achtergrond kunnen worden uitgevoerd en een taak kunnen retourneren om de voortgang te controleren en te beheren
    - -AsJob-parameter toegevoegd aan cmdlet Get-AzureRmSubscription
* RecoveryServices.Backup
    - Fout verholpen - Get-AzureRmRecoveryServicesBackupItem moet een niet-hoofdlettergevoelige vergelijking uitvoeren voor het containernaamfilter.
    - Fout verholpen - AzureVmItem heeft nu een eigenschap die laat zien wanneer er voor het laatst een back-up is uitgevoerd - LastBackupTime.
* Resources
    - Probleem opgelost waarbij Get-AzureRMRoleAssignment leidde tot toewijzingen zonder roldefinitie voor aangepaste rollen
        - Gebruikers kunnen nu Get-AzureRMRoleAssignment gebruiken met toewijzingen die roldefinitienamen hebben, ongeacht het soort rol
    - Probleem opgelost waarbij Set-AzureRMRoleRoleDefinition de foutmelding 'RD niet gevonden' genereerde wanneer er een nieuwe scope was in assignablescopes
        - Gebruikers kunnen nu Set-AzureRMRoleRoleDefinition gebruiken met toewijsbare scopes, met inbegrip van nieuwe scopes, ongeacht de positie van de scope
    - Het is nu toegestaan dat scopes eindigen op '/'
        - Gebruikers kunnen nu RoleDefinition- en RoleAssignment-cmdlets gebruiken met scopes die eindigen op '/', consistent met API en CLI
    - Het is nu toegestaan dat gebruikers RoleAssignment kunnen maken met behulp van een overdrachtsvlag
        - Gebruikers kunnen nu New-AzureRMRoleAssignment gebruiken met de optie voor het toevoegen van een overdrachtsvlag
    - Er is een probleem met RoleAssignment opgelost om de scopeparameter na te leven
    - Er is een alias toegevoegd voor ServicePrincipalName in de cmdlet New-AzureRmRoleAssignment
        - Gebruikers kunnen nu ApplicationId gebruiken in plaats van ServicePrincipalName bij het gebruik van de cmdlet New-AzureRmRoleAssignment
* SiteRecovery
    - Er zijn afschaffingswaarschuwingen toegevoegd voor alle cmdlets in deze module ter voorbereiding op de volgende belangrijke update.
        - Raadpleeg de gids met toekomstige belangrijke wijzigingen voor meer informatie over het migreren van uw cmdlets uit AzureRM.
* SQL
    - De mogelijkheid is toegevoegd om de naam van de database te wijzigen met behulp van Set-AzureRmSqlDatabase
    - Het probleem https://github.com/Azure/azure-powershell/issues/4974 is opgelost
        - Opgave van een ongeldige AUDIT_CHANGED_GROUP-waarde om cmdlets te controleren, genereert niet langer een fout en wordt verwijderd in een toekomstige release.
    - Het probleem https://github.com/Azure/azure-powershell/issues/5046 is opgelost
        - De AuditAction-parameter bij het controleren van cmdlets wordt niet langer genegeerd
    - Probleem opgelost bij het controleren van cmdlets wanneer er voor StorageKeyType een 'Secondary'-waarde wordt opgegeven
        - Bij het instellen van blob-controle werd de primaire opslagaccountsleutel gebruikt in plaats van de secundaire sleutel wanneer er een 'Secondary'-waarde voor de parameter StorageKeyType werd opgegeven.
    - Het bevestigingsbericht van Set-AzureRmSqlServerTransparentDataEncryptionProtector is gewijzigd
* Azure (RDFE)
    - Alle RemoteApp-cmdlets zijn verwijderd
* Azure.Storage
    - Upgrade naar Azure Storage Client Library 8.6.0 en Azure Storage DataMovement Library 0.6.5

Wijzigingen sinds de laatste versie: wijzigingen sinds de laatste versie: https://github.com/azure/azure-powershell/compare/v5.0.1-November2017...v5.1.1-December2017

## <a name="20171110-version-501"></a>10-11-2017 Versie 5.0.1
* Probleem opgelost bij het laden van assembly, waardoor het uitvoeren van enkele cmdlets mislukt in de volgende modules:
    - AzureRM.ApiManagement
    - AzureRM.Backup
    - AzureRM.Batch
    - AzureRM.Compute
    - AzureRM.DataFactories
    - AzureRM.HDInsight
    - AzureRM.KeyVault
    - AzureRM.RecoveryServices
    - AzureRM.RecoveryServices.Backup
    - AzureRM.RecoveryServices.SiteRecovery
    - AzureRM.RedisCache
    - AzureRM.SiteRecovery
    - AzureRM.Sql
    - AzureRM.Storage
    - AzureRM.StreamAnalytics

## <a name="2017118---version-500"></a>08-11-2017 - Versie 5.0.0
* OPMERKING: Deze release bevat belangrijke wijzigingen. Raadpleeg de migratiehandleiding (https://aka.ms/azps-migration-guide) voor een volledige lijst met belangrijke wijzigingen.
* Alle cmdlets in AzureRM bieden nu ondersteuning voor online Help
    - Voer Get-Help uit met de parameter -Online om de online Help in uw standaardinternetbrowser te openen
* AnalysisServices
    * Probleem met de opdracht Synchronize-AzureAsInstance opgelost, zodat deze werkt met de nieuwe AsAzure REST API voor synchronisatie
* ApiManagement
    * Raadpleeg de migratiehandleiding voor deze release voor belangrijke wijzigingen in ApiManagement
    * Cmdlet Get-AzureRmApiManagementUser is bijgewerkt om dit probleem op te lossen: https://github.com/Azure/azure-powershell/issues/4510
    * Cmdlet New-AzureRmApiManagementApi is bijgewerkt om een API met een leeg pad te maken: https://github.com/Azure/azure-powershell/issues/4069
* ApplicationInsights
    * Opdrachten toegevoegd voor het ophalen/maken/verwijderen van Application Insights-resources
        - Get-AzureRmApplicationInsights
        - New-AzureRmApplicationInsights
        - Remove-AzureRmApplicationInsights
    * Opdrachten toegevoegd voor het ophalen/bijwerken van de prijzen/dagelijkse limiet van Application Insights-resources
        - Get-AzureRmApplicationInsights -IncludeDailyCap
        - Set-AzureRmApplicationInsightsPricingPlan
        - Set-AzureRmApplicationInsightsDailyCap
    * Opdrachten toegevoegd voor het ophalen/maken/bijwerken/verwijderen van continue export van Application Insights-resources
        - Get-AzureRmApplicationInsightsContinuousExport
        - Set-AzureRmApplicationInsightsContinuousExport
        - New-AzureRmApplicationInsightsContinuousExport
        - Remove-AzureRmApplicationInsightsContinuousExport
    * Opdrachten toegevoegd voor het ophalen/maken/verwijderen van API-sleutels van Application Insights-resources
        - Get-AzureRmApplicationInsightsApiKey
        - New-AzureRmApplicationInsightsApiKey
        - Remove-AzureRmApplicationInsightsApiKey
* AzureBatch
    * Er zij nieuwe parameters aan `New-AzureRmBatchAccount` toegevoegd.
        - `PoolAllocationMode`: De toewijzingsmodus die moet worden gebruikt om pools te maken in het Batch-account. Als u een Batch-account wilt maken dat poolknooppunten in het abonnement van de gebruiker toewijst, stelt u dit in op `UserSubscription`.
        - `KeyVaultId`: De resource-id van de Azure-sleutelkluis die is gekoppeld aan het Batch-account.
        - `KeyVaultUrl`: De URL van de Azure-sleutelkluis die is gekoppeld aan het Batch-account.
    * Parameters zijn bijgewerkt naar `New-AzureBatchTask`.
        - De schakeloptie `RunElevated` is verwijderd. De parameter `UserIdentity` is toegevoegd ter vervanging van `RunElevated` en equivalent gedrag is in te stellen door een `PSUserIdentity` op te stellen, zoals hieronder wordt weergegeven:
            - $autoUser = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoUserSpecification -ArgumentList @("Taak", "Beheerder")
            - $userIdentity = New-Object Microsoft.Azure.Commands.Batch.Models.PSUserIdentity $autoUser
        - De parameter `AuthenticationTokenSettings` is toegevoegd. Met deze parameter kunt u de Batch-service verzoeken een verificatietoken aan de taak toe te kennen wanneer deze wordt uitgevoerd, zodat er geen Batch-accountsleutels aan de taak hoeven te worden doorgegeven om verzoeken bij de Batch-service in te kunnen dienen.
        - De parameter `ContainerSettings` is toegevoegd.
            - Met deze parameter kunt u de Batch-service verzoeken de taak binnen een container uit te voeren.
        - De parameter `OutputFiles` is toegevoegd.
            - Met deze parameter kunt u configureren dat de taak na voltooiing bestanden uploadt naar Azure Storage.
    * Parameters zijn bijgewerkt naar `New-AzureBatchPool`.
        - De parameter `UserAccounts` is toegevoegd.
            - Deze parameter definieert gebruikersaccounts die worden gemaakt op elk knooppunt in de pool.
        - `TargetLowPriorityComputeNodes` is toegevoegd en de naam van `TargetDedicated` is gewijzigd in `TargetDedicatedComputeNodes`.
            - Er is een `TargetDedicated`-alias gemaakt voor de parameter `TargetDedicatedComputeNodes`.
        - De parameter `NetworkConfiguration` is toegevoegd.
            - Met deze parameter kunt u de netwerkinstellingen van de pools configureren.
    * Parameters zijn bijgewerkt naar `New-AzureBatchCertificate`.
        - De `Password` parameter is nu een `SecureString`.
    * Parameters zijn bijgewerkt naar `New-AzureBatchComputeNodeUser`.
        - De `Password` parameter is nu een `SecureString`.
    * Parameters zijn bijgewerkt naar `Set-AzureBatchComputeNodeUser`.
        - De `Password` parameter is nu een `SecureString`.
    * De naam van de parameter `Name` is gewijzigd in `Path` op `Get-AzureBatchNodeFile`, `Get-AzureBatchNodeFileContent` en `Remove-AzureBatchNodeFile`.
        - Er is een `Name`-alias gemaakt voor de parameter `Path`.
    * Wijzigingen in objecten
        - Raadpleeg het Batch-wijzigingenlogboek voor een volledige lijst met wijzigingen
    * Ondersteuning toegevoegd voor verificatie op basis van Azure Active Directory.
        - Om verificatie op basis van Azure Active Directory te gebruiken, moet u een `BatchAccountContext`-object ophalen met de cmdlet `Get-AzureRmBatchAccount` en deze `BatchAccountContext` doorgeven aan de parameter `-BatchContext` van een Batch-service-cmdlet. Azure Active Directory-verificatie is verplicht voor accounts met `PoolAllocationMode = UserSubscription`.
        - Voor bestaande accounts of voor nieuwe accounts die zijn gemaakt met `PoolAllocationMode = BatchService`, kunt u gedeelde sleutelverificatie blijven gebruiken door een `BatchAccountContext`-object op te halen met de cmdlet `Get-AzureRmBatchAccoutKeys`.
* Compute
    * Extensie-opdrachten voor Azure Disk Encryption
        - Nieuwe parameter voor 'Set-AzureRmVmDiskEncryptionExtension': '-EncryptFormatAll' versleutelt en formatteert alle gegevensschijven
        - Nieuwe parameters voor 'Set-AzureRmVmDiskEncryptionExtension': '-ExtensionPublisherName' en '-ExtensionType' staan nu toe dat wordt overgeschakeld naar andere versies van de extensie
        - Nieuwe parameters voor 'Disable-AzureRmVmDiskEncryption': '-ExtensionPublisherName' en '-ExtensionType' staan nu toe dat wordt overgeschakeld naar andere versies van de extensie
        - Nieuwe parameters voor 'Get-AzureRmVmDiskEncryptionStatus': '-ExtensionPublisherName' en '-ExtensionType' staan nu toe dat wordt overgeschakeld naar andere versies van de extensie
* DataLakeAnalytics
    * Raadpleeg de migratiehandleiding voor deze release voor belangrijke wijzigingen in DataLakeAnalytics
    * Een van de twee OutputTypes van Get-AzureRmDataLakeAnalyticsAccount is gewijzigd
        - List\<DataLakeAnalyticsAccount> is nu List\<PSDataLakeAnalyticsAccountBasic>
        - De eigenschappen van PSDataLakeAnalyticsAccountBasic vormen een strikte subset van de eigenschappen van DataLakeAnalyticsAccount
        - De aanvullende eigenschappen in DataLakeAnalyticsAccount worden niet geretourneerd door de service.  Deze wijziging is bedoeld om dit beter weer te geven. De aanvullende eigenschappen zijn nog wel aanwezig in PSDataLakeAnalyticsAccountBasic, maar gelabeld als Verouderd.
    * Een van de twee OutputTypes van Get-AzureRmDataLakeAnalyticsJob is gewijzigd
        - List\<JobInformation> is nu List\<PSJobInformationBasic>
        - De eigenschappen van PSJobInformationBasic vormen een strikte subset van de eigenschappen van JobInformation
        - De aanvullende eigenschappen in JobInformation worden niet geretourneerd door de service.  Deze wijziging is bedoeld om dit beter weer te geven. De aanvullende eigenschappen zijn nog wel aanwezig in PSJobInformationBasic, maar gelabeld als Verouderd.
* DataLakeStore
    * Raadpleeg de migratiehandleiding voor deze release voor belangrijke wijzigingen in DataLakeStore
    * Een van de twee OutputTypes van Get-AzureRmDataLakeStoreAccount is gewijzigd
        - List\<PSDataLakeStoreAccount> is nu List\<PSDataLakeStoreAccountBasic>
        - De eigenschappen van PSDataLakeStoreAccountBasic vormen een strikte subset van de eigenschappen van PSDataLakeStoreAccount
        - De aanvullende eigenschappen in PSDataLakeStoreAccount worden niet geretourneerd door de service.  Deze wijziging is bedoeld om dit beter weer te geven. De aanvullende eigenschappen zijn nog wel aanwezig in PSDataLakeStoreAccountBasic, maar gelabeld als Verouderd.
* DNS
    * Ondersteuning voor CAA-recordtypen in Azure DNS
       - Biedt ondersteuning voor alle bewerkingen op het CAA-recordtype
* EventHub
    * Raadpleeg de migratiehandleiding voor deze release voor belangrijke wijzigingen in EventHub
* Inzichten
    * Raadpleeg de migratiehandleiding voor deze release voor belangrijke wijzigingen in Insights
* Netwerk
    * Raadpleeg de migratiehandleiding voor deze release voor belangrijke wijzigingen in Network
    * Cmdlet toegevoegd om een lijst weer te geven met beschikbare internetserviceproviders voor een opgegeven Azure-regio
        - Get-AzureRmNetworkWatcherReachabilityProvidersList
    * Cmdlet toegevoegd om de relatieve latentiescore weer te geven voor internetserviceproviders van een opgegeven locatie naar Azure-regio's
        - Get-AzureRmNetworkWatcherReachabilityReport
* Profiel
    - Set-AzureRmDefault
        - Gebruik deze cmdlet om een standaardresourcegroep in te stellen.  Dit maakt de parameter -ResourceGroup optioneel voor enkele cmdlets en zorgt ervoor dat de standaardwaarde wordt gebruikt wanneer er geen resourcegroep is opgegeven.
        - ```Set-AzureRmDefault -ResourceGroupName "ExampleResourceGroup"```
        - Als de opgegeven resourcegroep bestaat in het abonnement, wordt deze resourcegroep ingesteld als standaardwaarde.  Anders wordt de resourcegroep gemaakt en vervolgens ingesteld als standaardwaarde.
    - Get-AzureRmDefault
        - U kunt deze cmdlet gebruiken om de huidige standaardresourcegroep op te halen (en later ook andere standaardinstellingen).
        - ```Get-AzureRmDefault -ResourceGroup```
    - Clear-AzureRmDefault
        - U kunt deze cmdlet gebruiken om de huidige standaardresourcegroep te verwijderen
        - ```Clear-AzureRmDefault -ResourceGroup```
    - Add-AzureRmEnvironment en Set-AzureRmEnvironment
        - Voegt de parameter BatchAudience toe, waarmee u de Azure Batch Active Directory kunt opgeven die gebruikers gebruiken wanneer zij verificatietokens ophalen voor de Batch-service.
* RecoveryServices.Backup
    * Cmdlets toegevoegd om direct bestandsherstel uit te voeren.
        - Get-AzureRmRecoveryServicesBackupRPMountScript
        - Disable-AzureRmRecoveryServicesBackupRPMountScript
    * SDK-versie RecoveryServices.Backup bijgewerkt naar de nieuwste versie
    * Tests voor de virtuele Azure-machinewerkbelasting bijgewerkt, zodat alle instellingen die voor de tests nodig zijn, door de tests zelf worden ingesteld.
    * Oplossing voor https://github.com/Azure/azure-powershell/issues/3164
* RecoveryServices.SiteRecovery
    * Wijzigingen voor ASR VMware in Azure Site Recovery (cmdlets ondersteunen momenteel bewerkingen voor Enterprise-naar-Enterprise, Enterprise-naar-Azure en Hyper-V-naar-Azure)
        - New-AzureRmRecoveryServicesAsrPolicy
        - New-AzureRmRecoveryServicesAsrProtectedItem
        - Update-AzureRmRecoveryServicesAsrPolicy
        - Update-AzureRmRecoveryServicesAsrProtectionDirection
    * Ondersteuning toegevoegd voor kluis op basis van AAD
    * Cmdlets toegevoegd voor het beheren van VCenter-resources
        - Get-AzureRmRecoveryServicesAsrVCenter
        - New-AzureRmRecoveryServicesAsrVCenter
        - Remove-AzureRmRecoveryServicesAsrVCenter
        - Update-AzureRmRecoveryServicesAsrVCenter
    * Andere cmdlets toegevoegd
        - Get-AzureRmRecoveryServicesAsrAlertSetting
        - Get-AzureRmRecoveryServicesAsrEvent
        - New-AzureRmRecoveryServicesAsrProtectableItem
        - Set-AzureRmRecoveryServicesAsrAlertSetting
        - Start-AzureRmRecoveryServicesAsrResynchronizeReplicationJob
        - Start-AzureRmRecoveryServicesAsrSwitchProcessServerJob
        - Start-AzureRmRecoveryServicesAsrTestFailoverCleanupJob
        - Update-AzureRmRecoveryServicesAsrMobilityService
* ServiceBus
    - Raadpleeg de migratiehandleiding voor deze release voor belangrijke wijzigingen in ServiceBus
* SQL
    * Ondersteuning toegevoegd voor lijstweergave en annuleren van asynchrone updateslo-bewerking op de database
        - De bestaande cmdlet Get-AzureRmSqlDatabaseActivity is bijgewerkt om een bewerkingsstatus updateslo voor de database te retourneren.
        - Nieuwe cmdlet Stop-AzureRmSqlDatabaseActivity toegevoegd om de asynchrone updateslo-bewerking op de database te annuleren.
    * Ondersteuning toegevoegd voor zoneredundantie voor databases en elastische pools
        - Switch-parameter ZoneRedundant toegevoegd aan New-AzureRmSqlDatabase
        - Switch-parameter ZoneRedundant toegevoegd aan Set-AzureRmSqlDatabase
        - Switch-parameter ZoneRedundant toegevoegd aan New-AzureRmSqlElasticPool
        - Switch-parameter ZoneRedundant toegevoegd aan Set-AzureRmSqlElasticPool
    * Ondersteuning voor server-DNS-aliassen toegevoegd
        - Cmdlet Get-AzureRmSqlServerDnsAlias toegevoegd, waarmee de server-DNS-aliassen worden opgehaald op basis van server en aliasnaam of een lijst met server-DNS-aliassen voor een Azure SQL-server.
        - Cmdlet New-AzureRmSqlServerDnsAlias toegevoegd, waarmee een nieuwe server-DNS-alias wordt gemaakt voor een opgegeven Azure SQL-server
        - Cmdlet Set-AzurermSqlServerDnsAlias toegevoegd, waarmee een Azure SQL-server kan worden bijgewerkt afhankelijk van naar welke server-DNS-server wordt verwezen
        - Cmdlet Remove-AzureRmSqlServerDnsAlias toegevoegd, waarmee een server-DNS-alias wordt verwijderd voor een Azure SQL-server
* Azure.Storage
    * Upgrade naar Azure Storage Client Library 8.5.0 en Azure Storage DataMovement Library 0.6.3
    * Ondersteuningsfunctie voor momentopnames van de bestandsshare toegevoegd
        - Parameter SnapshotTime toegevoegd aan Get-AzureStorageShare
        - Parameter IncludeAllSnapshot toegevoegd aan Remove-AzureStorageShare
