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
ms.openlocfilehash: 143d92384fd270711378f6741ba59e88c12833d1
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a>Releaseopmerkingen

Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.

## <a name="version-220"></a>Versie 2.2.0
* Compute
  - Er is ondersteuning toegevoegd voor het uitvoeren van query's over de versleutelingsstatus van de AzureDiskEncryptionForLinux-extensie
* DataFactory
  - Er is een nieuwe cmdlet toegevoegd voor het maken van een lijst met activiteitenvensters
    + Get-AzureRmDataFactoryActivityWindow
* DataLake
  - De parameter `Host` is gewijzigd in `DatabaseHost` en er is een alias toegevoegd aan `Host`
    + New-AzureRmDataLakeAnalyticsCatalogSecret
    + Set-AzureRmDataLakeAnalyticsCatalogSecret
  - Er is ondersteuning toegevoegd voor het verwijderen van ACL en standaard-ACL
  - Er is ondersteuning toegevoegd voor het ophalen en instellen van naamloze machtigingen voor bestanden en mappen
* KeyVault
  - Er is ondersteuning voor certificaten toegevoegd
    + Add-AzureKeyVaultCertificate
    + Add-AzureKeyVaultCertificateContact
    + Get-AzureKeyVaultCertificate
    + Get-AzureKeyVaultCertificateContact
    + Get-AzureKeyVaultCertificateIssuer
    + Get-AzureKeyVaultCertificateOperation
    + Get-AzureKeyVaultCertificatePolicy
    + Import-AzureKeyVaultCertificate
    + New-AzureKeyVaultCertificateAdministratorDetails
    + New-AzureKeyVaultCertificateOrganizationDetails
    + New-AzureKeyVaultCertificatePolicy
    + Remove-AzureKeyVaultCertificate
    + Remove-AzureKeyVaultCertificateContact
    + Remove-AzureKeyVaultCertificateIssuer
    + Remove-AzureKeyVaultCertificateOperation
    + Set-AzureKeyVaultCertificateAttribute
    + Set-AzureKeyVaultCertificateIssuer
    + Set-AzureKeyVaultCertificatePolicy
    + Stop-AzureKeyVaultCertificateOperation
* Netwerk

  - Er is een nieuwe switchparameter toegevoegd voor de netwerkinterface om versnelde netwerken in of uit te schakelen: +New-AzureRmNetworkInterface -EnableAcceleratedNetworking
  - De PowerShell-cmdlets voor de Active-Active-gatewayfunctie zijn ingeschakeld
    + Add-AzureRmVirtualNetworkGatewayIpConfig
    + Remove-AzureRmVirtualNetworkGatewayIpConfig
  - Er is een nieuwe cmdlet toegevoegd
    + Test-AzureRmPrivateIpAddressAvailability
* Resources
  - Er is ondersteuning toegevoegd voor zones in provider- en resource-cmdlets
    + Get-AzureRmProvider
    + New-AzureRmResource
    + Set-AzureRmResource
* SQL
  - Er zijn nieuwe cmdlets voor beleidsbeheer toegevoegd met betrekking tot detectie in Azure SQL van bedreigingen op serverniveau
    + Get-AzureRmSqlServerThreatDetectionPolicy
    + Remove-AzureRmSqlServerThreatDetectionPolicy
    + Set-AzureRmSqlServerThreatDetectionPolicy
  - Er zijn nieuwe cmdlets toegevoegd ter ondersteuning van het in-/uitschakelen van de GeoBackupPolicy voor SQL Azure DataWarehouses
    + Get-AzureRmSqlDatabaseGeoBackupPolicy
    + Set-AzureRmSqlDatabaseGeoBackupPolicy
  - Er zijn nieuwe cmdlets toegevoegd voor Azure SQL-Advisors en aanbevolen API's voor acties
    + Get-AzureRmSqlDatabaseAdvisor
    + Get-AzureRmSqlElasticPoolAdvisor
    + Get-AzureRmSqlServerAdvisor
    + Get-AzureRmSqlDatabaseRecommendedActions
    + Get-AzureRmSqlElasticPoolRecommendedActions
    + Get-AzureRmSqlServerRecommendedActions
    + Set-AzureRmSqlDatabaseAdvisorAutoExecuteStatus
    + Set-AzureRmSqlElasticPoolAdvisorAutoExecuteStatus
    + Set-AzureRmSqlServerAdvisorAutoExecuteStatus
    + Set-AzureRmSqlDatabaseRecommendedActionState
    + Set-AzureRmSqlElasticPoolRecommendedActionState
    + Set-AzureRmSqlServerRecommendedActionState
