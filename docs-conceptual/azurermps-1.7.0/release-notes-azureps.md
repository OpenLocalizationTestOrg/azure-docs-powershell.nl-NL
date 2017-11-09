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
ms.openlocfilehash: 0a3f152751fee569d3ac5fba6bcff8c1737f7b8c
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a>Releaseopmerkingen

Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.

## <a name="version-170"></a>Versie 1.7.0

* **Gedragswijziging voor de parameters -Force, –Confirm en $ConfirmPreference voor alle cmdlets. We wijzigen deze implementatie, zodat deze in overeenstemming is met de PowerShell-richtlijnen. Dit betekent voor de meeste cmdlets dat de parameter Force wordt verwijderd en de prompt ShouldProcess wordt overgeslagen. Gebruikers moeten de parameter -Confirm:$false in de PowerShell-scripts opnemen.** Deze wijzigingen hebben betrekking op de volgende problemen:
  - De correcte implementatie van de –WhatIf-functionaliteit, zodat een gebruiker de gevolgen van een cmdlet of script kan bepalen zonder daadwerkelijk wijzigingen door te voeren
  - Controle over prompts met behulp van een sessiebrede $ConfirmPreference, zodat aan de gebruiker vragen worden gesteld op basis van de impact van een potentiële wijziging (zoals aangegeven in de ConfirmImpact-instelling in de cmdlet)
  - Cmdlet-specifieke controle over bevestigingsprompts met de parameter –Confirm
  - Consistent gebruik van ShouldContinue en de parameter –Force tussen cmdlets voor acties die alleen het stellen van vragen door de gebruiker vereisen vanwege de speciale aard van de wijzigingen (bijvoorbeeld het verwijderen van verborgen bestanden)
  - Consistentie met andere PowerShell-cmdlets, zodat PowerShell-scriptkennis van andere cmdlets direct toepasbaar is op de Azure PowerShell-cmdlets.

**Houd er rekening mee dat er nu bij het *automatisch overslaan van alle prompts in alle gevallen* Azure PowerShell-cmdlets van de gebruiker vereisen dat deze twee parameters opgeeft:**
```powershell
My-CmdletWithConfirmation –Confirm:$false -Force
```
* Azure Compute
  - Set-AzureRmVMADDomainExtension
  - Get-AzureRmVMADDomainExtension
  - Parameter -Redeploy voor Restart-AzureVM
  - Parameter -Validate voor Move-AzureService, Move-AzureStorageAccount en Move-AzureVirtualNetwork
  - Naam- en versieparameters voor extensie-cmdlets zijn, zoals voorheen, optioneel.
  - New-AzureVM kan een licentietype van het VM-object krijgen.
* Azure Storage
  - De parameter Tags is gewijzigd in Tag en de parameteralias Tags is toegevoegd
    + New-AzureRmStorageAccount
    + Set-AzureRmStorageAccount
* Azure-netwerk
  - Er is een nieuwe cmdlet toegevoegd voor peering in virtuele netwerken
* Azure Redis-cache
  - Er is een nieuwe cmdlet toegevoegd voor Reset-AzureRmRedisCache
  - Er is een nieuwe cmdlet toegevoegd voor Export-AzureRmRedisCache
  - Er is een nieuwe cmdlet toegevoegd voor Import-AzureRmRedisCache
  - De cmdlet New-AzureRmRedisCache is gewijzigd en bevat nu een parameterwijziging voor VNet's
* Azure SQL DB Backup/Restore
  - Cmdlets voor back-upfunctie voor langetermijnbewaarperiode
  - Get-AzureRmSqlServerBackupLongTermRetentionVault
  - Get-AzureRmSqlDatabaseBackupLongTermRetentionPolicy
  - Set-AzureRmSqlServerBackupLongTermRetentionVault
  - Set-AzureRmSqlDatabaseBackupLongTermRetentionPolicy
  - Restore-AzureRmSqlDatabase ondersteunt nu het terugzetten van een verwijderde database naar een eerder tijdstip
  - Restore-AzureRmSqlDatabase ondersteunt nu het terugzetten van een back-up die voor de lange termijn wordt bewaard
* Azure LogicApp
  - LogicApp-integratieaccount-cmdlets zijn toegevoegd.
  - Get-AzureRmIntegrationAccountAgreement
  - Get-AzureRmIntegrationAccountCallbackUrl
  - Get-AzureRmIntegrationAccountCertificate
  - Get-AzureRmIntegrationAccount
  - Get-AzureRmIntegrationAccountMap
  - Get-AzureRmIntegrationAccountPartner
  - Get-AzureRmIntegrationAccountSchema
  - New-AzureRmIntegrationAccountAgreement
  - New-AzureRmIntegrationAccountCertificate
  - New-AzureRmIntegrationAccount
  - New-AzureRmIntegrationAccountMap
  - New-AzureRmIntegrationAccountPartner
  - New-AzureRmIntegrationAccountSchema
  - Remove-AzureRmIntegrationAccountAgreement
  - Remove-AzureRmIntegrationAccountCertificate
  - Remove-AzureRmIntegrationAccount
  - Remove-AzureRmIntegrationAccountMap
  - Remove-AzureRmIntegrationAccountPartner
  - Remove-AzureRmIntegrationAccountSchema
  - Set-AzureRmIntegrationAccountAgreement
  - Set-AzureRmIntegrationAccountCertificate
  - Set-AzureRmIntegrationAccount
  - Set-AzureRmIntegrationAccountMap
  - Set-AzureRmIntegrationAccountPartner
  - Set-AzureRmIntegrationAccountSchema
* Azure Data Lake Store
  - De prestaties met betrekking tot het uploaden en downloaden van bestanden en mappen zijn aanzienlijk verbeterd.
  - Dit omvat een kleine wijziging met betrekking tot de parameternamen voor het downloaden en de opname van twee nieuwe parameters voor het uploaden:
    + NumThreads -> PerFileThreadCount: deze parameter wordt gebruikt om het aantal threads aan te geven die in een enkel bestand moeten worden gebruikt
    + ConcurrentFileCount: deze parameter wordt gebruikt om het aantal bestanden aan te geven dat samen met het uploaden/downloaden van een map moet worden geüpload/gedownload.
  - Er zijn nu standaardthreadingwaarden ontworpen om een betere gehele doorvoer voor de meeste bestandsgrootten te bieden. Als de prestaties niet aan uw wensen voldoen, kunnen de bovenstaande waarden worden gewijzigd om aan de vereisten te voldoen.
* Azure Data Lake Analytics
  - Get-AzureRMDataLakeAnalyticsDataSource retourneert nu alle gegevensbronnen wanneer deze worden aangeroepen zonder argumenten.
  - Deze wijziging verwijdert ook het type gegevensbronparameter van de cmdlet.
  - Deze wijziging resulteert in een nieuw object dat voor de lijstbewerking wordt geretourneerd en de volgende eigenschappen heeft:
    + Type: het type gegevensbron
    + Name: de naam van de gegevensbron
    + IsDefault is ingesteld op 'true' als dit de standaardgegevensbron voor het account is
  - Het probleem met Get-AzureRMDataLakeAnalyticsJob is verholpen voor een lijst met bepaalde offsetwaarden voor datum en tijd wanneer er op submittedBefore en submittedAfter wordt gefilterd.
* Web Apps
  - Swap-AzureRmWebAppSlot-cmdlet voor regulier wisselen en wisselen met preview is toegevoegd
  - Set-AzureRmWebAppSlot-cmdlet om automatisch wisselen te ondersteunen, is uitgebreid
* Azure API Management
  - Het probleem met de Azure API Management Deployment-cmdlets voor AzureChinaCloud is verholpen.
  - De cmdlet Set-AzureRmApiManagementTenantGitAccess is verwijderd, aangezien Git Access standaard is ingeschakeld.
* Azure Recovery Services Backup
  - Er is ondersteuning toegevoegd voor de Azure SQL-workload
  - Er is ondersteuning toegevoegd voor het herstellen en het maken van back-ups van versleutelde virtuele Azure-machines
  - Backup-AzureRmRecoveryServicesBackupItem: er is een optionele bewaartijdfunctie voor herstelpunten toegevoegd
  - Oplossingen voor kleine filtergerelateerde problemen in de cmdlets Get-AzureRmRecoveryServicesBackupContainer en Get-AzureRmRecoveryServicesBackupItem
* Azure Automation
  - Get-AzureRmAutomationHybridWorkerGroup is toegevoegd
