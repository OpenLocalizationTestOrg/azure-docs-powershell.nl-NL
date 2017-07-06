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
ms.openlocfilehash: 97a23180a1fc65d96fdc9dbdffcbe3501a4c4c2a
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/29/2017
---
# <a name="release-notes"></a>Releaseopmerkingen

Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.

## <a name="version-400"></a>Versie 4.0.0

* Deze release bevat belangrijke wijzigingen. Raadpleeg [de migratiehandleiding](https://aka.ms/azps-migration-guide) voor meer informatie over de wijzigingen en de gevolgen ervan voor bestaande scripts.
* ApiManagement
  - Er is ondersteuning toegevoegd voor het configureren van externe groepen in New-AzureRmApiManagementGroup.
* Facturering
  - Nieuwe cmdlet Get-AzureRmBillingPeriod
    + cmdlet voor het ophalen van Azure-factureringsperioden van het abonnement.
  - Update van cmdlet Get-AzureRmBillingInvoice
  - nieuwe eigenschap BillingPeriodNames
  - uitvoer in lijstweergave
* Compute
  - De cmdlets Set-AzureRmVMAEMExtension en Test-AzureRmVMAEMExtension zijn bijgewerkt en ondersteunen nu Premium-beheerde schijven
  - Back-upversleutelingsinstellingen voor IaaS-VM's en herstel na een fout
  - De naam van de optie ChefServiceInterval is gewijzigd in ChefDaemonInterval. De oude naam kan echter nog steeds worden gebruikt.
  - De dubbele eigenschappen DataDiskNames en NetworkInterfaceIDs zijn uit het PS-VM-object verwijderd.
  - De parameters DataDiskNames en NetworkInterfaceIDs in respectievelijk Remove-AzureRmVMDataDisk en Remove-AzureRmVMNetworkInterface zijn optioneel gemaakt.
  - Het probleem met Get-cmdlets waarbij de Get-cmdlets worden geretourneerd als een lijstobject, is opgelost.
  - De namen van cmdlets die conflicteerden met RDFE-cmdlets, zijn gewijzigd. Bekijk het probleem https://github.com/Azure/azure-powershell/issues/2917 voor meer informatie
    + De naam van `New-AzureVMSqlServerAutoBackupConfig` is gewijzigd in `New-AzureRmVMSqlServerAutoBackupConfig`
    + De naam van `New-AzureVMSqlServerAutoPatchingConfig` is gewijzigd in `New-AzureRmVMSqlServerAutoPatchingConfig`
    + De naam van `New-AzureVMSqlServerKeyVaultCredentialConfig` is gewijzigd in `New-AzureRmVMSqlServerKeyVaultCredentialConfig`
* Verbruik
  - Nieuwe cmdlet Get-AzureRmConsumptionUsageDetail
    + cmdlet voor het ophalen van de gebruiksdetails van het abonnement.
* ContainerRegistry
  - PowerShell-cmdlets voor Azure Container Registry zijn toegevoegd
    + New-AzureRmContainerRegistry
    + Get-AzureRmContainerRegistry
    + Update-AzureRmContainerRegistry
    + Remove-AzureRmContainerRegistry
    + Get-AzureRmContainerRegistryCredential
    + Update-AzureRmContainerRegistryCredential
    + Test-AzureRmContainerRegistryNameAvailability
* DataLakeAnalytics
  - Er is ondersteuning toegevoegd voor het ophalen en in een lijst opnemen van cataloguspakketten
  - Er is ondersteuning toegevoegd voor het in een lijst opnemen van de volgende catalogusitems uit diepere bovenliggende elementen:
    + Tabel
    + TVF
    + Weergave
    + statistieken
* DataLakeStore
  - Traceerlogboekregistratie is standaard uitgeschakeld voor `Import-AzureRMDataLakeStoreItem` en `Export-AzureRMDataLakeStoreItem` om de prestaties te verbeteren. Gebruik de parameters `-DiagnosticLogLevel` en `-DiagnosticLogPath` als traceerlogboekregistratie wel gewenst is
  - Er is een probleem opgelost waardoor PowerShell soms vastliep tijdens het uploaden van grote hoeveelheden kleine bestanden naar ADLS.
* EventHub
  - Opgelost probleem:
    + Fix voor cmdlet-fout Set-AzureRmEventHubNamespace: Laag mag niet null zijn, waar deze SkuName moet zijn
    + Set-AzureRmEventHub: opgeloste fout 'Objectverwijzing niet ingesteld op een exemplaar van een object' bij het bijwerken van EventHub
* Inzichten
  - Add-AzureRm*AlertRule
    + Retourneert een enkel object: newResource, statusCode, requestId
  - Get-AzureRmAlertRule
    + De uitvoer wordt nu opgesomd en niet meer beschouwd als één enkel object. Het type is niet gewijzigd en is nog steeds een lijst.
  - Remove-AzureRmAlertRule
    + De statuscode volgt de statuscode die wordt geretourneerd na de aanvraag. Voorheen was de statuscode altijd OK.
  - Add-AzureRmAutoscaleSetting
    + Hiermee wordt nu één enkel object geretourneerd (en geen lijst, zoals voorheen), dat statusCode, requestId en de zojuist gemaakte of bijgewerkte resource bevat.
    + De statuscode volgt de status die wordt geretourneerd na de aanvraag. Voorheen was de statuscode altijd OK.
  - New-AzureRmAutoscaleRule
    + De parameter ScaleActionType is uitgebreid en ontvangt nu de volgende waarden: ChangeCount, PercentChangeCount en ExactCount.
  - Remove-AzureRmAutoscaleSetting
    + De statuscode in de uitvoer volgt de statuscode die wordt geretourneerd na de aanvraag. Voorheen was de statuscode altijd OK.
  - Get-AzureRMLogProfile
    + De uitvoer wordt nu opgesomd. Voorheen werd de uitvoer beschouwd als één enkel object. Het type van de uitvoer blijft een lijst, net als voorheen.
  - Remove-AzureRmLogProfile
    + De parameter PassThru is geïmplementeerd.
  - API voor metrische gegevens
    + Met de SDK worden nu metrische gegevens opgehaald uit MDM.
  - Get-AzureRmMetricDefinition
    + De uitvoer is nog steeds een lijst, maar de structuur van de lijst is gewijzigd.
  - Get-AzureRmMetric
    + De aanroep is gewijzigd. Dit is de nieuwe syntaxis: Get-AzureRmMetric ResourceId [MetricNames [TimeGrain] [AggregationType] [StartTime] [EndTime]] [DetailedOutput]
    + De uitvoer is een lijst en de structuur van de elementen in de lijst is gewijzigd.
* KeyVault
  - Er is ondersteuning toegevoegd voor het maken en terugzetten van back-ups voor KeyVault-geheimen
    + Er kunnen back-ups van geheimen worden gemaakt en teruggezet, overeenkomstig de functionaliteit die wordt ondersteund voor sleutels

  - Backup-cmdlets voor sleutels en geheimen accepteren nu een corresponderend object als invoerparameter
    + De aanroeper kan ophaal- en back-upbewerkingen koppelen: Get-AzureKeyVaultKey -VaultName myVault -Name myKey | Backup-AzureKeyVaultKey

  - Backup-cmdlets bieden nu ondersteuning voor de schakeloptie /force voor het overschrijven van een bestaand bestand
    + Let op: een poging om een bestaand bestand te overschrijven, leidt niet meer tot een fout. De gebruiker wordt nu gevraagd een optie te kiezen om aan te geven hoe verder te gaan.
* LogicApp
  - Er zijn nieuwe parameters toegevoegd voor cmdlets voor herstel na een noodgeval die gebruikmaken van een uitwisselingscontrolenummer:
    + Er is een optionele parameter -AgreementType (X12 of Edifact) beschikbaar om de relevante controlenummers op te geven
* MachineLearning
  - Er wordt een nieuwe versie van de Azure Machine Learning .Net-SDK gebruikt en er is een nieuwe cmdlet toegevoegd
    + Add-AzureRmMlWebServiceRegionalProperty
  - Er zijn kleine verbeteringen aangebracht in de Help-tekst.
* Netwerk
  - De cmdlet Test-AzureRmNetworkWatcherConnectivity is toegevoegd
    + Hiermee worden verbindingsgegevens geretourneerd voor een opgegeven bron-VM en een bestemming
    + Als de verbinding tussen de bron en de bestemming niet tot stand kan worden gebracht, retourneert de cmdlet informatie over het probleem
* Profiel
  - De cmdlet Send-Feedback is toegevoegd: hiermee kan een gebruiker een set prompts starten waarmee feedback naar het Azure PowerShell-team wordt verzonden.
  - De volgende aliassen zijn verwijderd, omdat ze in conflict zijn met bestaande cmdlet-namen in de Azure-module:
    + `Enable-AzureDataCollection` (ondersteund met `Enable-AzureRmDataCollection`)
    + `Disable-AzureDataCollection` (ondersteund met `Disable-AzureRmDataCollection`)
* Relay
  - Hiermee worden cmdlets toegevoegd voor Azure Relay waarmee gebruikers alle Azure Relay-resources kunnen maken en beheren.
    + `New-AzureRmRelayNamespace`
    + `Get-AzureRmRelayNamespace`
    + `Set-AzureRmRelayNamespace`
    + `Remove-AzureRmRelayNamespace`
    + `New-AzureRmWcfRelay`
    + `Get-AzureRmWcfRelay`
    + `Set-AzureRmWcfRelay`
    + `Remove-AzureRmWcfRelay`
    + `New-AzureRmRelayHybridConnection`
    + `Get-AzureRmRelayHybridConnection`
    + `Set-AzureRmRelayHybridConnection`
    + `Remove-AzureRmRelayHybridConnection`
    + `Test-AzureRmRelayName`
    + `Get-AzureRmRelayOperation`
    + `New-AzureRmRelayKey`
    + `Get-AzureRmRelayKey`
    + `New-AzureRmRelayAuthorizationRule`
    + `Get-AzureRmRelayAuthorizationRule`
    + `Set-AzureRmRelayAuthorizationRule`
    + `Remove-AzureRmRelayAuthorizationRule`
* Resources
  - Ondersteuning voor implementaties die meerdere resourcegroepen beslaan voor New-AzureRmResourceGroupDeployment
    + Gebruikers kunnen nu geneste implementaties gebruiken voor implementatie in verschillende resourcegroepen.
* ServiceBus

  - Het probleem dat de eigenschapswaarden van het ServiceBus-wachtrijobject op null werden ingesteld, is opgelost. Het object wordt gebruikt als invoerparameter in de cmdlet Set-AzureRmServiceBusQueue om de wachtrij bij te werken.
   - De eigenschappen waarop dit invloed heeft, zijn LockDuration, EntityAvailabilityStatus, DuplicateDetectionHistoryTimeWindow, MaxDeliveryCount en MessageCount
* ServiceFabric

  - Er zijn cmdlets toegevoegd voor Service Fabric
    + Add-AzureRmServiceFabricApplicationCertificate       Hiermee kan een certificaat worden toegevoegd dat wordt gebruikt als toepassingscertificaat
    + Add-AzureRmServiceFabricClientCertificate       Hiermee kan een algemene naam of vingerafdruk worden toegevoegd aan de clusterinstellingen voor clientverificatie
    + Add-AzureRmServiceFabricClusterCertificate       Hiermee kan een secundair clustercertificaat worden toegevoegd aan het cluster voor het verlengen van het bestaande certificaat
    + Add-AzureRmServiceFabricNodes       Hiermee kunnen knooppunten/virtuele machines van een specifiek knooppunttype aan een cluster worden toegevoegd
    + Add-AzureRmServiceFabricNodeType       Hiermee kunnen een knooppunttype/virtuele machines aan een bestaand cluster worden toegevoegd
    + Get-AzureRmServiceFabricCluster       Hiermee kan informatie van de clusterbron worden opgehaald
    + New-AzureRmServiceFabricCluster Hiermee kan een nieuw ServiceFabric-cluster worden gemaakt. Deze opdracht heeft vele overloads voor verschillende scenario's
    + Remove-AzureRmServiceFabricClientCertificate       Hiermee kan een clientcertificaat worden verwijderd, zodat het niet meer kan worden gebruikt om toegang te krijgen tot een cluster
    + Remove-AzureRmServiceFabricClusterCertificate       Hiermee kan een clustercertificaat worden verwijderd, zodat het niet meer kan worden gebruikt voor clusterbeveiliging
    + Remove-AzureRmServiceFabricNodes       Hiermee kunnen knooppunten van een specifiek knooppunttype uit een cluster worden verwijderd
    + Remove-AzureRmServiceFabricNodeType       Hiermee kan een knooppunttype uit een cluster worden verwijderd
    + Remove-AzureRmServiceFabricSettings       Hiermee kunnen een of meer ServiceFabric-instellingen uit een cluster worden verwijderd
    + Set-AzureRmServiceFabricSettings       Hiermee kunnen een of meer ServiceFabric-instellingen aan een cluster worden toegevoegd of worden bijgewerkt
    + Set-AzureRmServiceFabricUpgradeType       Hiermee kan het ServiceFabric-upgradetype van een cluster worden gewijzigd
    + Update-AzureRmServiceFabricDurability       Hiermee kan de duurzaamheidslaag van een cluster worden gewijzigd
    + Update-AzureRmServiceFabricReliability       Hiermee kan de betrouwbaarheid van een cluster worden gewijzigd
* SQL
  - De parameter -SampleName is toegevoegd aan New-AzureRmSqlDatabase
  - Er zijn updates beschikbaar voor de failovergroep-cmdlets
  - Tag-parameters zijn verwijderd
  - De parameters PartnerResourceGroupName en PartnerServerName zijn uit de cmdlet Remove-AzureRmSqlDatabaseFailoverGroup verwijderd
  - De parameter GracePeriodWithDataLossHours is toegevoegd aan New- en Set-cmdlets en vervangt uiteindelijk de parameter GracePeriodWithDataLossHour
  - De documentatie is uitgebreid en bijgewerkt
  - De opmaak van geretourneerde objecten is gewijzigd en er zijn enkele problemen opgelost met velden die niet altijd werden ingevuld
  - De eigenschappen DatabaseNames en PartnerLocation zijn aan het failovergroepsobject toegevoegd
  - Het probleem dat ertoe leidde dat de Switch-cmdlet onmiddellijk resultaten retourneerde, in plaats van te wachten tot de bewerking was voltooid, is opgelost
  - Het probleem dat er een overloop bij een geheel getal optreedt bij respijtperioden met hoge waarden, is opgelost
  - De respijtperiode wordt nu ingesteld op een minimum van 1 uur als er een lagere waarde wordt opgegeven
  - Usage_Anomaly is verwijderd uit de geaccepteerde waarden voor de parameter ExcludedDetectionType van de cmdlets Set-AzureRmSqlDatabaseThreatDetectionPolicy en Set-AzureRmSqlServerThreatDetectionPolicy.
* Storage
  - De SRP-SDK is geüpgraded naar 6.3.0
  - New/Set-AzureRmStorageAccount: er is een nieuwe parameter toegevoegd ter ondersteuning van EnableHttpsTrafficOnly
  - New/Set/Get-AzureRmStorageAccount: het geretourneerde opslagaccount bevat een nieuw kenmerk EnableHttpsTrafficOnly
* Azure.Storage
  - Er is een upgrade uitgevoerd naar Azure Storage Client Library 8.1.1 en Azure Storage DataMovement Library 0.5.1
  - Er is een nieuwe cmdlet toegevoegd ter ondersteuning van de functie blob Incremental Copy
