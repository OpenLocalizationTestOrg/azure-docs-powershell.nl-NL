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
ms.date: 11/14/2017
ms.openlocfilehash: ab35cbc4ec1a0bd4e7ee40e1864bd7941f5bca87
ms.sourcegitcommit: 79dd3700b5cb4cb90b268778b482082052160093
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/14/2017
---
# <a name="release-notes"></a>Releaseopmerkingen

Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.

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
* Insights
    * Raadpleeg de migratiehandleiding voor deze release voor belangrijke wijzigingen in Insights
* Network
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