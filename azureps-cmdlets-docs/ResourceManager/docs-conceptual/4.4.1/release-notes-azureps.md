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
ms.date: 07/26/2017
ms.openlocfilehash: d8a891673df343551cbd805016c2d25ee4e31c8c
ms.sourcegitcommit: e6b7e20bbd04eda51416c56b13f867102b602d1a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/07/2017
---
# <a name="release-notes"></a>Releaseopmerkingen

Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.

## <a name="20170925---version-440"></a>2017.09.25 - Versie 4.4.0
* AnalysisServices
  * Er is een nieuwe dataplane-cmdlet toegevoegd om synchronisatie van databases mogelijk te maken van instanties met het kenmerk lezen-schrijven naar instanties met het kenmerk alleen-lezen.
    - Help-bestand toegevoegd voor de cmdlet
    - Geheugentests en een scenariotest (alleen live) toegevoegd
  * Fouten verholpen in de cmdlet Add-AzureAsAccount
* Automatisering
  * Help-documenten aangepast voor cmdlets die in de eerdere versie zijn aangepast.
  * Vier nieuwe cmdlets toegevoegd voor ondersteuning van gefaseerde uitrol van DSC-knooppuntconfiguraties.
    - Start-AzureRmAutomationDscNodeConfigurationDeployment
    - Stop-AzureRmAutomationDscNodeConfigurationDeployment
    - Get-AzureRmAutomationDscNodeConfigurationDeployment
    - Get-AzureRmAutomationDscNodeConfigurationDeploymentSchedule
* CognitiveServices
  * Integratie met versie 2.0.0 van Cognitive Services Management SDK.
  * Get-AzureRmCognitiveServicesAccount biedt nu juiste ondersteuning voor paginering.
* Compute
  * RunCommand-functie:
    - Nieuwe cmdlet: 'Invoke-AzureRmVMRunCommand' roept een RunCommand aan op een VM
    - Nieuwe cmdlet: 'Get-AzureRmVMRunCommandDocument' toont de beschikbare RunCommand-documenten
  * Parameter 'StorageAccountType toegevoegd aan Set-AzureRmDataDisk
  * Ondersteuning van beschikbaarheidszone voor virtuele machine, VM-schaalset en schijf
    - Nieuwe parameter: 'Zone' toegevoegd aan New-AzureRmVM, New-AzureRmVMConfig, New-AzureRmVmssConfig, New-AzureRmDiskConfig
  * Rolling upgrade voor VM-schaalset:
    - Nieuwe cmdlet: 'Start-AzureRmVmssRollingOSUpgrade' start de rolling upgrade door het OS van de VM-schaalset
    - Nieuwe cmdlet: 'Set-AzureRmVmssRollingUpgradePolicy' stelt het upgradebeleid in voor de rolling upgrade van de VM-schaalset
    - Nieuwe cmdlet: 'Stop-AzureRmVmssRollingUpgrade' annuleert de rolling upgrade van de VM-schaalset
    - Nieuwe cmdlet: 'Get-AzureRmVmssRollingUpgrade' toont de status van de rolling upgrade van de VM-schaalset
  * Nieuwe parameter AssignIdentity toegevoegd voor door het systeem toegewezen identiteit.
    - Nieuwe parameter: 'AssignIdentity' toegevoegd aan New-AzureRmVMConfig, New-AzureRmVmssConfig en Update-AzureRmVM
  * Versleuteling voor Vmss-schijf toegevoegd:
    - Nieuwe cmdlet: 'Set-AzureRmVmssDiskEncryptionExtension' schakelt schijfversleuteling voor de VM-schaalset in
    - Nieuwe cmdlet: 'Disable-AzureRmVmssDiskEncryption' schakelt schijfversleuteling voor de VM-schaalset uit
    - Nieuwe cmdlet: 'Get-AzureRmVmssDiskEncryptionStatus' toont de status voor schijfversleuteling van een VM-schaalset
    - Nieuwe cmdlet: 'Get-AzureRmVmssVMDiskEncryptionStatus' toont de status voor schijfversleuteling van VM's in een VM-schaalset
* ContainerInstance
  * PowerShell-cmdlets toegevoegd voor Azure Container Instance
    - New-AzureRmContainerGroup
    - Get-AzureRmContainerGroup
    - Remove-AzureRmContainerGroup
    - Get-AzureRmContainerInstanceLog
* Inzichten
  * Nieuwe cmdlet Disable-AzureRmActivityLogAlert
    - Een nieuwe cmdlet om een bestaande waarschuwing in het activiteitenlogboek uit te schakelen.
    - De tags kunnen desgewenst ook worden ingesteld met deze cmdlet.
  * Nieuwe cmdlet Enable-AzureRmActivityLogAlert
    - Een nieuwe cmdlet om een bestaande waarschuwing in het activiteitenlogboek in te schakelen.
    - De tags kunnen desgewenst ook worden ingesteld met deze cmdlet.
  * Nieuwe cmdlet Get-AzureRmActivityLogAlert
    - Een nieuwe cmdlet om een of meer waarschuwingen in het activiteitenlogboek op te halen.
    - De waarschuwingen kunnen worden opgehaald door de naam, de resourcegroep of het abonnement op te geven.
  * Nieuwe cmdlet New-AzureRmActionGroup
    - Een nieuwe cmdlet om in het geheugen een ActionGroup-object te maken (geen aanvraag nodig.)
  * Nieuwe cmdlet New-AzureRmActivityLogAlertCondition
    - Een nieuwe cmdlet om in het geheugen een object te maken met de leaf-voorwaarde voor een waarschuwing in het activiteitenlogboek (geen aanvraag nodig.)
  * Nieuwe cmdlet Set-AzureRmActivityLogAlert
    - Een nieuwe cmdlet voor het maken of bijwerken van een waarschuwing in het activiteitenlogboek.
  * Nieuwe cmdlet Remove-AzureRmActivityLogAlert
    - Een nieuwe cmdlet voor het verwijderen van een waarschuwing uit het activiteitenlogboek.
  * Nieuwe cmdlet Set-AzureRmActionGroup
    - Een nieuwe cmdlet om een nieuwe actiegroep te maken of een bestaande actiegroep bij te werken.
  * Nieuwe cmdlet Get-AzureRmActionGroup
    - Een nieuwe cmdlet om een of meer actiegroepen op te halen.
    - De actiegroepen kunnen worden opgehaald door de naam, de resourcegroep of het abonnement op te geven.
  * Nieuwe cmdlet Remove-AzureRmActionGroup
    - Een nieuwe cmdlet voor het verwijderen van een actiegroep.
  * Nieuwe cmdlet New-AzureRmActionGroupReceiver
    - Een nieuwe cmdlet om in het geheugen een nieuwe actiegroepontvanger te maken.
* KeyVault
  * Nieuwe/bijgewerkte cmdlets voor het voorlopig verwijderen van KeyVault-certificaten
    * Get-AzureKeyVaultCertificate
    * Remove-AzureKeyVaultCertificate
    * Undo-AzureKeyVaultCertificateRemoval
* Netwerk
  * Ondersteuning toegevoegd voor eindpuntservices voor subnetten van virtueel netwerk
    - Add-AzureRmVirtualSubnetConfig bijgewerkt: optionele parameter -ServiceEndpoint toegevoegd
    - New-AzureRmVirtualSubnetConfig bijgewerkt: optionele parameter -ServiceEndpoint toegevoegd
    - Set-AzureRmVirtualSubnetConfig bijgewerkt: optionele parameter -ServiceEndpoint toegevoegd
  * Cmdlet toegevoegd om beschikbare eindpuntservices op de locatie op te vragen
    - Get-AzureRmVirtualNetworkAvailableEndpointService
  * De volgende cmdlets uitgebreid met de mogelijkheid voor het configureren van P2S-verificatie via een externe RADIUS-server
    - New-AzureVirtualNetworkGateway
    - Set-AzureVirtualNetworkGateway
    - Set-AzureRmVirtualNetworkGatewayVpnClientConfig
  * Cmdlet toegevoegd waarmee VPN-profielen kunnen worden gegenereerd voor P2S-verificatie via een externe RADIUS-server
    - New-AzureRmVpnClientConfiguration
    - Get-AzureRmVpnClientConfiguration
  * Ondersteuning toegevoegd voor SKU-parameter voor openbare IP-adressen en load balancers
    - New-AzureRMLoadBalancer bijgewerkt: optionele parameter -Sku toegevoegd
    - New-AzureRMPublicIpAddress bijgewerkt: optionele parameter -Sku toegevoegd
  * Ondersteuning voor DisableOutboundSNAT toegevoegd aan regels voor load balancers
    - New-AzureRMLoadBalancerRuleConfig bijgewerkt: optionele parameter DisableOutboundSNAT toegevoegd
    - Add-AzureRMLoadBalancerRuleConfig bijgewerkt: optionele parameter DisableOutboundSNAT toegevoegd
    - Set-AzureRMLoadBalancerRuleConfig bijgewerkt: optionele parameter DisableOutboundSNAT toegevoegd
  * Ondersteuning voor IKEv2 P2S toegevoegd
    - New-AzureRmVirtualNetworkGateway bijgewerkt: optionele parameter -VpnClientProtocol toegevoegd, standaardinstelling is [ 'SSTP', 'IkeV2' ]
    - Set-AzureRmVirtualNetworkGateway bijgewerkt: optionele parameter -VpnClientProtocol toegevoegd
  * Ondersteuning toegevoegd voor regels met meerdere waarden in netwerkbeveiligingsregels en effectieve netwerkbeveiligingsregels
    - Add-AzureRmNetworkSecurityRuleConfig bijgewerkt: parameters SourcePortRange, DestinationPortRange en SourceAddressPrefix bijgewerkt voor ondersteuning van een lijst met tekenreeksen
    - New-AzureRmNetworkSecurityRuleConfig bijgewerkt: parameters SourcePortRange, DestinationPortRange en SourceAddressPrefix bijgewerkt voor ondersteuning van een lijst met tekenreeksen
    - Set-AzureRmNetworkSecurityRuleConfig bijgewerkt: parameters SourcePortRange, DestinationPortRange en SourceAddressPrefix bijgewerkt voor ondersteuning van een lijst met tekenreeksen
    - Add-AzureRmNetworkSecurityRuleConfig bijgewerkt: parameters SourcePortRange, DestinationPortRange en SourceAddressPrefix bijgewerkt voor ondersteuning van een lijst met tekenreeksen
    - New-AzureRmNetworkSecurityGroup bijgewerkt: parameter SecurityRules bijgewerkt voor ondersteuning van de parameters SourcePortRange, DestinationPortRange en SourceAddressPrefix, die bestaan uit een lijst met tekenreeksen in het PSSecurityRule-object
    - Get-AzureRmEffectiveNetworkSecurityGroup bijgewerkt: parameter TagMap toegevoegd
    - Get-AzureRmEffectiveNetworkSecurityGroup bijgewerkt: geretourneerd PSEffectiveSecurityRule-object bijgewerkt met de parameters SourcePortRange, DestinationPortRange en SourceAddressPrefix, die bestaan uit een lijst met tekenreeksen.
  * Ondersteuning toegevoegd voor DDoS-bescherming voor virtuele netwerken
    - New-AzureRmVirtualNetwork bijgewerkt: parameters EnableDDoSProtection en EnableVmProtection toegevoegd
    - Eigenschappen EnableDDoSProtection en EnableVmProtection toegevoegd aan PSVirtualNetwork-object
  * Ondersteuning toegevoegd voor maximaal beschikbare interne load balancer
    - Add-AzureRmLoadBalancerRuleConfig bijgewerkt: 'All' toegevoegd als waarde voor de parameter Protocol
    - New-AzureRmLoadBalancerRuleConfig bijgewerkt: 'All' toegevoegd als waarde voor de parameter Protocol
    - Set-AzureRmLoadBalancerRuleConfig bijgewerkt: 'All' toegevoegd als waarde voor de parameter Protocol
  * Ondersteuning toegevoegd voor beveiligingsgroepen voor toepassing
    - New-AzureRmApplicationSecurityGroup toegevoegd
    - Get-AzureRmApplicationSecurityGroup toegevoegd
    - Remove-AzureRmApplicationSecurityGroup toegevoegd
    - New-AzureRmNetworkInterface bijgewerkt: optionele parameters ApplicationSecurityGroup en ApplicationSecurityGroupId toegevoegd
    - New-AzureRmNetworkInterfaceIpConfig bijgewerkt: optionele parameters ApplicationSecurityGroup en ApplicationSecurityGroupId toegevoegd
    - Add-AzureRmNetworkInterfaceIpConfig bijgewerkt: optionele parameters ApplicationSecurityGroup en ApplicationSecurityGroupId toegevoegd
    - Set-AzureRmNetworkInterfaceIpConfig bijgewerkt: optionele parameters ApplicationSecurityGroup en ApplicationSecurityGroupId toegevoegd
    - New-AzureRmNetworkSecurityRuleConfig bijgewerkt: optionele parameters SourceApplicationSecurityGroup, SourceApplicationSecurityGroupId, DestinationApplicationSecurityGroup en DestinationApplicationSecurityGroupId toegevoegd
    - Add-AzureRmNetworkSecurityRuleConfig bijgewerkt: optionele parameters SourceApplicationSecurityGroup, SourceApplicationSecurityGroupId, DestinationApplicationSecurityGroup en DestinationApplicationSecurityGroupId toegevoegd
    - Set-AzureRmNetworkSecurityRuleConfig bijgewerkt: optionele parameters SourceApplicationSecurityGroup, SourceApplicationSecurityGroupId, DestinationApplicationSecurityGroup en DestinationApplicationSecurityGroupId toegevoegd
  * Nieuwe opdrachten toegevoegd voor VpnDeviceConfiguration-scripts
    - Get-AzureRmVirtualNetworkGatewaySupportedVpnDevices
    - Get-AzureRmVirtualNetworkGatewayConnectionVpnDeviceConfigScript
* Profiel
  * Start-Job-ondersteuning voor AzureRm-cmdlets
    * Voor alle AzureRm-cmdlets de parameter -AzureRmContext toegevoegd, die ondersteuning biedt voor een context (uitvoer van een Context-cmdlet).
      - Algemeen patroon voor taken met context-persistentie UITGESCHAKELD:`Start-Job {param ($context) New-AzureRmVM -AzureRmContext $context [... other parameters]} -ArgumentList (Get-AzureRmContext)`
      - Algemeen patroon voor taken met context-persistentie INGESCHAKELD:`Start-Job {New-AzureRmVM [... other parameters]}`
  * Aanmeldingsgegevens blijven behouden tussen sessies, nieuwe cmdlets:
    - Enable-AzureRmContextAutosave: aanmeldingsgegevens behouden tussen sessies.
    - Disable-AzureRmContextAutosave: aanmeldingsgegevens niet behouden tussen sessies.
  * Beheren van contextgegevens, nieuwe cmdlets
    - Select-AzureRmContext: de actieve benoemde context selecteren.
    - Rename-AzureRmContext: de naam van een bestaande context wijzigen voor eenvoudige verwijzing.
    - Remove-AzureRmContext: een bestaande context verwijderen.
    - Remove-AzureRmAccount: alle referenties, abonnementen en tenants verwijderen die aan een account zijn gekoppeld.
  * Beheren van contextgegevens, gewijzigde cmdlets
    - 'Scope = (Process | CurrentUser)' toegevoegd aan alle cmdlets die referenties wijzigen
    - Get-AzureRmContext: parameter ListAvailable toegevoegd om alle opgeslagen contexten op te vragen
* Resources
  * PolicySetDefinition-cmdlets toegevoegd
    - Cmdlet New-AzureRmPolicySetDefinition om een definitie van een beleidsset te maken
    - Cmdlet Get-AzureRmPolicySetDefinition om een lijst weer te geven met alle beleidssetdefinities of om de definitie van een specifieke beleidsset op te vragen
    - Cmdlet Remove-AzureRmPolicySetDefinition om de definitie van een beleidsset te verwijderen
    - Cmdlet Set-AzureRmPolicySetDefinition om de bestaande definitie van een beleidsset bij te werken
  * Parameters -PolicySetDefinition, -Sku en -NotScope toegevoegd aan de cmdlets New-AzureRmPolicyAssignment en Set-AzureRmPolicyAssignment
  * Ondersteuning toegevoegd voor doorgeven van beleids-URL aan de cmdlets New-AzureRmPolicyDefinition en Set-AzureRmPolicyDefinition
  * Parameter -Mode toegevoegd aan de cmdlet New-AzureRmPolicyDefinition
  * Ondersteuning toegevoegd voor verwijderen van roltoewijzing met behulp van PSRoleAssignment-object
    - Gebruikers kunnen nu het invoerobject PSRoleassignmnet gebruiken met de cmdlet Remove-AzureRMRoleAssignment om de roltoewijzing te verwijderen.
  * ManagedApplication-cmdlets toegevoegd
    - Cmdlet New-AzureRmManagedApplication voor het maken van een beheerde toepassing
    - Cmdlet Get-AzureRmManagedApplication voor het weergeven van een lijst met alle beheerde toepassingen van een abonnement of het opvragen van een specifieke beheerde toepassing
    - Cmdlet Remove-AzureRmManagedApplication voor het verwijderen van een beheerde toepassing
    - Cmdlet Set-AzureRmManagedApplication voor het bijwerken van een bestaande beheerde toepassing
  * ManagedApplicationDefinition-cmdlets toegevoegd
    - Cmdlet New-AzureRmManagedApplicationDefinition voor het maken van een definitie van een beheerde toepassing met behulp van een URI voor een ZIP-bestand of de Json-bestanden mainTemplate en createUiDefinition
    - Cmdlet Get-AzureRmManagedApplicationDefinition voor het weergeven van een lijst met alle beheerde toepassingen van een resourcegroep of het opvragen van de definitie van een specifieke beheerde toepassing
    - Cmdlet Remove-AzureRmManagedApplicationDefinition voor het verwijderen van de definitie van een beheerde toepassing
    - Cmdlet Set-AzureRmManagedApplicationDefinition voor het bijwerken van de definitie van een bestaande beheerde toepassing
* SQL
  * Ondersteuning toegevoegd voor regels voor virtuele netwerken
    - Cmdlet Get-AzureRmSqlServerVirtualNetworkRule toegevoegd om de regels voor een virtueel netwerk op te vragen die zijn vastgelegd onder een bepaalde naam of die beschikbaar zijn op een Azure SQL-server.
    - Cmdlet Set-AzureRmSqlServerVirtualNetworkRule toegevoegd om het virtuele netwerk te wijzigen waarnaar de regel verwijst.
    - Cmdlet Remove-AzureRmSqlServerVirtualNetworkRule toegevoegd om een regel voor een virtueel netwerk te verwijderen voor een Azure SQL-server.
    - Cmdlet New-AzureRmSqlServerVirtualNetworkRule toegevoegd om een regel voor een virtueel netwerk toe te voegen voor een Azure SQL-server.
* Websites
  * PremiumV2-laag toegevoegd voor App Service-abonnementen
* Azure.Storage
  * Upgrade naar Azure Storage Client Library 8.4.0 en Azure Storage DataMovement Library 0.6.1
  * Ondersteuning voor PremiumPageBlobTier toegevoegd aan de API voor het uploaden en kopiëren van blobs
    - Set-AzureStorageBlobContent
    - Start-AzureStorageBlobCopy
  * Indeling van console-uitvoer verfijnd voor AzureStorageContainer, AzureStorageBlob, AzureStorageQueue en AzureStorageTable
    - Get-AzureStorageContainer
    - Get-AzureStorageBlob
    - Get-AzureStorageQueue
    - Get-AzureStorageTable

## <a name="20170810---version-431"></a>2017.08.10 - Versie 4.3.1
  * Update om probleem met ondertekening van de assembly op te lossen

## <a name="20170807---version-430"></a>2017.08.07 - Versie 4.3.0
* AnalysisServices
  * Bug verholpen in Set-AzureRmAnalysisServciesServer
    - Wanneer er geen beheerder wordt opgegeven, wordt de beheerder verwijderd.
  * BackupBlobContainerUri toegevoegd in New-AzureRmAnalysisServicesServer en Set-AzureRmAnalysisServicesServer
    - Hierdoor kan een back-up-blobcontainer worden in-/uitgeschakeld voor back-up/herstel van Azure Analysis Services Server
  * Opzoeken van SKU’s toegevoegd in New-AzureRmAnalysisServicesServer en Set-AzureRmAnalysisServicesServer
    - Vastgelegde SKU gewijzigd in dynamische zoekactie.
  * Add-AzureAnalysisServicesAccount biedt nu ondersteuning voor inloggen met service-principal
* Automatisering
  * AutomationDSC*-cmdlets gewijzigd, zodat deze nu meer dan 100 records retourneren
  * Het probleem opgelost waarbij de uitgebreide streams niet meer werken na het aanroepen van enkele Automation-cmdlets (zoals Get-AzureRmAutomationVariable, Get-AzureRmAutomationJob).
  * Ondersteuning voor NodeConfiguration build-versiebeheer toegevoegd aan StartAzureAutomationDscCompilationJob en ImportAzureAutomationDscNodeConfiguration
  * Oplossingen voor bestaande problemen - lost aliasprobleem nummer #3775 en probleem met runOn-alias op en introduceert ondersteuning voor HybridWorkers.
* Compute
  * Set-AzureRmVMAEMExtension: ondersteuning toegevoegd voor nieuwe Premium Disk-groottes
  * Set-AzureRmVMAEMExtension: ondersteuning toegevoegd voor M-serie
  * ForceUpdateTag-parameter toegevoegd aan Add-AzureRmVmssExtension
  * Primaire parameter toegevoegd aan New-AzureRmVmssIpConfig
  * EnableAcceleratedNetworking-parameter toegevoegd aan Add-AzureRmVmssNetworkInterfaceConfig
  * InstanceId toegevoegd aan Set-AzureRmVmss
  * MaintenanceRedeployStatus beschikbaar maken voor uitvoer Get-AzureRmVM -Status
  * Beperkingen en mogelijkheden beschikbaar maken voor tabelindeling van Get-AzureRmComputeResourceSku
* DataLakeStore
  * Oplossing voor het volgende probleem: https://github.com/Azure/azure-powershell/issues/4323
* EventHub
  * ResourceGroup-eigenschap toegevoegd aan NamespaceAttributes
    - 'ResourceGroup' haalt de naam op van de resourcegroep waar de naamruimte zich in bevindt
  * Cmdlets bijgewerkt met parametersets voor naamruimte en EventHub voor de werking van AuthorizationRule
    - New-AzureRmEventHubAuthorizationRule - voegt een nieuwe AuthorizationRule toe aan de bestaande naamruimte of EventHub.
    - Get-AzureRmEventHubAuthorizationRule - haalt een AuthorizationRule/lijst AuthorizationRules op voor de bestaande naamruimte of EventHub.
    - Set-AzureRmEventHubAuthorizationRule - werkt eigenschappen bij van de bestaande AuthorizationRule of EventHub-naamruimte.
    - Remove-AzureRmEventHubAuthorizationRule - verwijdert een bestaande AuthorizationRule of een bestaande naamruimte of EventHub.
    - New-AzureRmEventHubKey - genereert een nieuwe primaire/secundaire sleutel voor AuthorizationRule van bestaande naamruimte of EventHub.
    - Get-AzureRmEventHubKey - haalt een primaire/secundaire sleutel op voor AuthorizationRule van bestaande naamruimte of EventHub.
* Netwerk
    * IPv6-ondersteuning en nieuwe optionele parameter - PeerAddressType toegevoegd
      * New-AzureRmExpressRouteCircuitPeeringConfig:
      * Set-AzureRmExpressRouteCircuitPeeringConfig: IPv6-ondersteuning toegevoegd. Nieuwe optionele parameter toegevoegd
      * Remove-AzureRmExpressRouteCircuitPeeringConfig: IPv6-ondersteuning toegevoegd. Nieuwe optionele parameter toegevoegd
    * Parameter - ProbeEnabled als verouderd gemarkeerd
      - Add-AzureRmApplicationGatewayBackendHttpSettings
      - New-AzureRmApplicationGatewayBackendHttpSettings
      - Set-AzureRmApplicationGatewayBackendHttpSettings
* Profiel
    * Gegevensverzameling is standaard ingeschakeld. Gebruiksgegevens worden door Microsoft verzameld om de gebruikerservaring te verbeteren. De gegevens zijn anoniem en bevatten geen waarden voor opdrachtregelargumenten.
      - Gebruik de cmdlet Disable-AzureRmDataCollection om de functie uit te schakelen
      - Gebruik de cmdlet Enable-AzureRmDataCollection om de functie in te schakelen
* Resources
    * Ondersteuning toegevoegd voor validatie van de bereiken voor de volgende roledefinition- en roleassignment-commandlets voordat de aanvraag wordt verzonden naar ARM
      - Get-AzureRMRoleAssignment
      - New-AzureRMRoleAssignment
      - Remove-AzureRMRoleAssignment
      - Get-AzureRMRoleDefinition
      - New-AzureRMRoleDefinition
      - Remove-AzureRMRoleDefinition
      - Set-AzureRMRoleDefinition
* ServiceBus
    * Onderstaande commandlets toegevoegd voor AuthorizationRules voor naamruimte, wachtrij en onderwerp. geordend op basis van de parameterset waarin de autorisatieregelhandelingen worden uitgevoerd.
     - New-AzureRmServiceBusAuthorizationRule - voegt een nieuwe AuthorizationRule toe aan bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - Get-AzureRmServiceBusAuthorizationRule - haalt een AuthorizationRule/lijst AuthorizationRules op voor bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - Set-AzureRmServiceBusAuthorizationRule - werkt de eigenschappen bij van een bestaande AuthorizationRule of bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - New-AzureRmServiceBusKey - genereert een nieuwe primaire/secundaire sleutel voor AuthorizationRule van bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - Get-AzureRmServiceBusKey - haalt primaire/secundaire sleutel op voor AuthorizationRule van bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - Remove-AzureRmServiceBusNamespaceAuthorizationRule - verwijdert de bestaande AuthorizationRule of naamruimte/wachtrij/onderwerp van ServiceBus.
    * ResourceGroup-eigenschap toegevoegd aan NamespaceAttributes
* SQL
    * Bijwerken van Set-AzureRmSqlServerTransparentDataEncryptionProtector geeft een waarschuwing weer en vereist bevestiging indien het type Encryption Protector Type wordt ingesteld op AzureKeyVault
    * Bijgewerkte cmdlets toegevoegd voor controle-instellingen
      - De cmdlet Get-AzureRmSqlDatabaseAuditing waarmee de controle-instellingen van een Azure SQL-database worden opgehaald.
      - De cmdlet Get-AzureRmSqlServerAuditing waarmee de controle-instellingen van een Azure SQL-server worden opgehaald.
      - De cmdlet Set-AzureRmSqlDatabaseAuditing waarmee de controle-instellingen van een Azure SQL-database worden gewijzigd.
      - De cmdlet Set-AzureRmSqlServerAuditing waarmee de controle-instellingen van een Azure SQL-server worden gewijzigd.
    * De bestaande cmdlets voor controlebeleid worden hiermee niet langer ondersteund
      - Get-AzureRmSqlDatabaseAuditingPolicy
      - Get-AzureRmSqlServerAuditingPolicy
      - Set-AzureRmSqlDatabaseAuditingPolicy
      - Set-AzureRmSqlServerAuditingPolicy
      - Use-AzureRmSqlServerAuditingPolicy
      - Remove-AzureRmSqlDatabaseAuditing
      - Remove-AzureRmSqlServerAuditing
    * Parseren van schemabestanden voor de Update-AzureRmSqlSyncGroup is niet meer hoofdlettergevoelig.
* Storage
    * Er is ondersteuning voor NeworkRule toegevoegd aan de cmdlets voor opslagaccounts in resourcemodus
      - New-AzureRmStorageAccount
      - Set-AzureRmStorageAccount
      - Get-AzureRmStorageAccountNetworkRuleSet
      - Update-AzureRmStorageAccountNetworkRuleSet
      - Add-AzureRmStorageAccountNetworkRule
      - Remove-AzureRmStorageAccountNetworkRule

## <a name="20170717---version-421"></a>2017.07.17 - Versie 4.2.1
* Compute
    - Probleem opgelost met de cmdlets voor het maken en bijwerken van de VM-schijf en VM-schijfmomentopname (koppeling) [https://github.com/azure/azure-powershell/issues/4309]
      - New-AzureRmDisk
      - New-AzureRmSnapshot
      - Update-AzureRmDisk
      - Update-AzureRmSnapshot
* Profiel
    - Probleem opgelost met niet-interactieve gebruikersverificatie in RDFE (koppeling) [https://github.com/Azure/azure-powershell/issues/4299]
* ServiceManagement
    - Probleem opgelost met niet-interactieve gebruikersverificatie (koppeling) [https://github.com/Azure/azure-powershell/issues/4299]

## <a name="2017711---version-420"></a>2017.7.11 - Versie 4.2.0
* AnalysisServices
    * Nieuwe dataplane-API toegevoegd
        - API geïntroduceerd voor het ophalen van serverlogboeken, Export-AzureAnalysisServicesInstanceLog
* Automatisering
    * Correcte instelling TimeZone-waarde voor wekelijkse en maandelijkse schema's voor New-AzureRmAutomationSchedule
        - Zie voor meer informatie: https://github.com/Azure/azure-powershell/issues/3043
* AzureBatch
    - Nieuwe cmdlet Get-AzureBatchJobPreparationAndReleaseTaskStatus toegevoegd.
    - Bytebereik voor begin en einde toegevoegd voor parameters voor Get-AzureBatchNodeFileContent.
* CognitiveServices
    * Integratie met versie 1.0.0 van Cognitive Services Management SDK.
    * Fix voor een bug in de lengtecontrole van accountnamen.
* Compute
    * Ondersteuning voor opslagaccounttype voor installatiekopieschijf:
        - De parameter StorageAccountType is toegevoegd aan Set-AzureRmImageOsDisk en Add-AzureRmImageDataDisk
    * De functies PrivateIP en PublicIP in Vmss IP-configuratie:
        - PrivateIPAddressVersion, PublicIPAddressConfigurationName, PublicIPAddressConfigurationIdleTimeoutInMinutes en DnsSetting zijn toegevoegd aan New-AzureRmVmssIpConfig
        - De parameter PrivateIPAddressVersion voor het opgeven van IPv4 of IPv6 is toegevoegd aan New-AzureRmVmssIpConfig
    * Functie voor prestatieonderhoud:
        - De switchparameter PerformMaintenance is toegevoegd aan Restart-AzureRmVM.
        - Get-AzureRmVM -Status toont informatie over het prestatieonderhoud van de opgegeven virtuele machine
    * De functie Virtual Machine Identity:
        - De parameter IdentityType is toegevoegd aan New-AzureRmVMConfig en UpdateAzureRmVM
        - Get-AzureRmVM toont de identiteitsinformatie van de opgegeven virtuele machine
    * De functie Vmss Identity:
        - De parameter IdentityType is toegevoegd aan New-AzureRmVmssConfig
        - Get-AzureRmVmss toont de identiteitsinformatie van de opgegeven Vmss
    * De functie Vmss Boot Diagnostics:
        - Nieuwe cmdlet voor het instellen van diagnostische gegevens over opstarten van Vmss-object: Set-AzureRmVmssBootDiagnostics
        - De parameter BootDiagnostic is toegevoegd aan New-AzureRmVmssConfig
    * De functie Vmss LicenseType:
        - De parameter LicenseType is toegevoegd aan New-AzureRmVmssConfig
    * Ondersteuning voor RecoveryPolicyMode:
        - De parameter RecoveryPolicyMode is toegevoegd aan New-AzureRmVmssConfig
    * De functie Compute Resource SKU:
        - De nieuwe cmdlet Get-AzureRmComputeResourceSku toont een lijst met alle Compute Resource-SKU's
* DataFactories
    * New-AzureRmDataFactoryGatewayKey is vervangen
    * Introductie van een functie voor gateway-verificatie door toevoeging van New-AzureRmDataFactoryGatewayAuthKey en Get-AzureRmDataFactoryGatewayAuthKey
* DataLakeAnalytics
    * Toevoeging van ondersteuning voor Compute Policy CRUD aan de hand van de volgende opdrachten:
        - New-AzureRMDataLakeAnalyticsComputePolicy
        - Get-AzureRMDataLakeAnalyticsComputePolicy
        - Remove-AzureRMDataLakeAnalyticsComputePolicy
        - Update-AzureRMDataLakeAnalyticsComputePolicy
    * Toevoeging van ondersteuning voor metagegevens over taakrelaties voor gebruik bij terugkerende taken en taakpijplijnen. De volgende opdrachten zijn bijgewerkt of toegevoegd:
        - Submit-AzureRMDataLakeAnalyticsJob
        - Get-AzureRMDataLakeAnalyticsJob
        - Get-AzureRMDataLakeAnalyticsJobRecurrence
        - Get-AzureRMDataLakeAnalyticsJobPipeline
    * De tokendoelgroep voor taak- en catalogus-API's is bijgewerkt, zodat gebruik wordt gemaakt van de juiste Data Lake-specifieke doelgroep in plaats van de Azure Resource-doelgroep.
* DataLakeStore
    * Er is ondersteuning toegevoegd voor door gebruiker beheerde KeyVault-rotatie in de cmdlet Set-AzureRMDataLakeStoreAccount
    * Het gebruiksgemak is vergroot door toevoeging van een functie om automatisch `enableKeyVault` aan te roepen wanneer een door een gebruiker beheerde KeyVault wordt toegevoegd of een sleutel wordt geroteerd.
    * De tokendoelgroep voor taak- en catalogus-API's is bijgewerkt, zodat gebruik wordt gemaakt van de juiste Data Lake-specifieke doelgroep in plaats van de Azure Resource-doelgroep.
    * Er is een probleem verholpen dat de grootte beperkte van bestanden die werden gemaakt/toegevoegd met de volgende cmdlets:
        - New-AzureRmDataLakeStoreItem
        - Add-AzureRmDataLakeStoreItemContent
* DNS
    * Er is een probleem opgelost in het pijpleidingscenario voor Get-AzureRmDnsZone
        - Zie voor meer informatie: https://github.com/Azure/azure-powershell/issues/4203
* HDInsight
    * Er is ondersteuning toegevoegd voor het inschakelen/uitschakelen van Operations Management Suite (OMS)
    * Nieuwe cmdLets
        - Enable-AzureRmHDInsightOperationsManagementSuite
        - Disable-AzureRmHDInsightOperationsManagementSuite
        - Get-AzureRmHDInsightOperationsManagementSuite
    * Er zijn nieuwe parameters toegevoegd om aangepaste Spark-configuraties in te stellen voor Add-AzureRmHDInsightConfigValues
        - SparkDefaults- en SparkThriftConf-parameters voor Spark 1.6
        - Spark2Defaults- en Spark2ThriftConf-parameters voor Spark 2.0
* Inzichten
    * Probleem #4215 (wijzigingsaanvraag): verwijderen van de limiet van 15 dagen voor de cmdlet Get-AzureRmLog. Er zijn ook kleine wijzigingen in de namen van moduletests doorgevoerd.
    * Probleem #3957 opgelost voor Get-AzureRmLog
        - Probleem #1: de back-end retourneert de records op pagina's met 200 records, door middel van een vervolgtoken gekoppeld naar de volgende pagina. Klanten zagen de cmdlet slechts 200 records retourneren, terwijl ze wisten dat er meer waren. Dit gebeurde ongeacht de ingestelde waarde voor MaxEvents, tenzij die waarde kleiner was dan 200.
        - Probleem #2: de documentatie bevatte onjuiste gegevens over deze cmdlet, zoals: de standaardwaarde voor het tijdvenster is 1 uur.
        - Oplossing #1: de cmdlet volgt nu het vervolgtoken dat wordt geretourneerd door de back-end totdat MaxEvents of het einde van de set wordt bereikt.<br>De standaardwaarde voor MaxEvents is 1000 en de maximumwaarde is 100.000. Indien er voor MaxEvents een waarde wordt ingevoerd die kleiner is dan 1, wordt deze genegeerd en wordt in plaats daarvan de standaardwaarde gebruikt. Deze waarden en dit gedrag zijn niet veranderd, maar nu wel correct gedocumenteerd.<br>Er is een alias toegevoegd voor MaxEvents (MaxRecords), omdat de naam van de cmdlet geen gebeurtenissen meer noemt, maar alleen logboeken.
        - Oplossing #2: de documentatie bevat juiste en gedetailleerdere informatie: een nieuwe alias, een correct tijdvenster, een juiste standaardwaarde, en juiste minimale en maximale waarden.
* KeyVault
    * Het e-mailadres maakt geen deel meer uit van de directory-query als -UserPrincipalName is opgegeven voor de cmdlets Set-AzureRMKeyVaultAccessPolicy en Remove-AzureRMKeyVaultAccessPolicy.
      - Beide Cmdlets hebben nu een parameter -EmailAddress die kan worden gebruikt in plaats van de parameter -UserPrincipalName wanneer het opvragen van een e-mailadres wenselijk is.  Als er in de directory meer dan één resultaat voor het e-mailadres wordt gevonden, retourneert de cmdlet een fout.
* Netwerk
    * New-AzureRmIpsecPolicy: SALifeTimeSeconds en SADataSizeKilobytes zijn niet langer verplichte parameters
        - De standaardwaarde voor SALifeTimeSeconds is 27.000 seconden
        - De standaardwaarde voor SADataSizeKilobytes is 102.400.000 KB
    * Er is ondersteuning toegevoegd voor aangepaste coderingssuiteconfiguratie met SSL-beleid en het weergeven van alle SSL-opties-API’s in Application Gateway
        - Er zijn optionele parameters toegevoegd: -PolicyType, -PolicyName, -MinProtocolVersion, -Ciphersuite
            - Add-AzureRmApplicationGatewaySslPolicy
            - New-AzureRmApplicationGatewaySslPolicy
            - Set-AzureRmApplicationGatewaySslPolicy
        - Get-AzureRmApplicationGatewayAvailableSslOptions toegevoegd (alias: List-AzureRmApplicationGatewayAvailableSslOptions) is toegevoegd
        - Get-AzureRmApplicationGatewaySslPredefinedPolicy toegevoegd (alias: List-AzureRmApplicationGatewaySslPredefinedPolicy) is toegevoegd
    * Er is omleidingsondersteuning toegevoegd voor Application Gateway
        - Add-AzureRmApplicationGatewayRedirectConfiguration is toegevoegd
        - Get-AzureRmApplicationGatewayRedirectConfiguration is toegevoegd
        - New-AzureRmApplicationGatewayRedirectConfiguration is toegevoegd
        - Remove-AzureRmApplicationGatewayRedirectConfiguration is toegevoegd
        - Set-AzureRmApplicationGatewayRedirectConfiguration is toegevoegd
        - De optionele parameter -RedirectConfiguration is toegevoegd
            - Add-AzureRmApplicationGatewayRequestRoutingRule
            - New-AzureRmApplicationGatewayRequestRoutingRule
            - Set-AzureRmApplicationGatewayRequestRoutingRule
        - De optionele parameter -DefaultRedirectConfiguration is toegevoegd
            - Add-AzureRmApplicationGatewayUrlPathMapConfig
            - New-AzureRmApplicationGatewayUrlPathMapConfig
            - Set-AzureRmApplicationGatewayUrlPathMapConfig
        - De optionele parameter -RedirectConfiguration is toegevoegd
            - Add-AzureRmApplicationGatewayPathRuleConfig
            - New-AzureRmApplicationGatewayPathRuleConfig
            - Set-AzureRmApplicationGatewayPathRuleConfig
        - De optionele parameter -RedirectConfigurations is toegevoegd
            - New-AzureRmApplicationGateway
            - Set-AzureRmApplicationGateway
    * Er is ondersteuning toegevoegd voor Azure-websites in Application Gateway
        - New-AzureRmApplicationGatewayProbeHealthResponseMatch is toegevoegd
        - De optionele parameters -PickHostNameFromBackendHttpSettings, -MinServers, -Match zijn toegevoegd
            - Add-AzureRmApplicationGatewayProbeConfig
            - New-AzureRmApplicationGatewayProbeConfig
            - Set-AzureRmApplicationGatewayProbeConfig
        - De optionele parameters -PickHostNameFromBackendAddress, -AffinityCookieName, -ProbeEnabled, -Path zijn toegevoegd
            - Add-AzureRmApplicationGatewayBackendHttpSettings
            - New-AzureRmApplicationGatewayBackendHttpSettings
            - Set-AzureRmApplicationGatewayBackendHttpSettings
    * Get-AzureRmPublicIPaddress is bijgewerkt om publicipaddress-resources op te halen die zijn gemaakt via een VM-schaalset
    * Er is een cmdlet toegevoegd om het huidige gebruik van het virtuele netwerk op te halen
        - Get-AzureRmVirtualNetworkUsageList
* Profiel
    * Er is een probleem opgelost dat zich voordeed bij het gebruik van Import-AzureRmContext of Save-AzureRmContext
        - Zie voor meer informatie: https://github.com/Azure/azure-powershell/issues/3954
* RecoveryServices.SiteRecovery
    * Introductie van een nieuwe module voor Azure Site Recovery-bewerkingen.
        - Alle cmdlets beginnen met AzureRmRecoveryServicesAsr*
* SQL
    * Data Sync PowerShell-cmdlets zijn toegevoegd aan AzureRM.Sql
    * AzureRmSqlServer-cmdlets is bijgewerkt om de nieuwe REST-API-versie te gebruiken, die time-outs voorkomt bij het maken van de server.
    * De cmdlets voor het upgraden van servers zijn verwijderd omdat de oude serverversie (2.0) niet meer bestaat.
    * De nieuwe optionele schakelparameter AssignIdentity is toegevoegd aan de cmdlets New-AzureRmSqlServer en Set-AzureRmSqlServer ter ondersteuning van het inrichten van een resource-identiteit voor de SQL Server-resource
    * De parameter ResourceGroupName is nu optioneel voor Get-AzureRmSqlServer
        - Zie voor meer informatie: https://github.com/Azure/azure-powershell/issues/635
* ServiceManagement voor ExpressRoute:
    * De cmdlet New-AzureBgpPeering is bijgewerkt om de volgende nieuwe opties toe te voegen:
        - PeerAddressType: de waarde IPv4 of IPv6 kan worden opgegeven voor het maken van een BGP-peering van het bijbehorende type adresfamilie
    * De cmdlet Set-AzureBgpPeering is bijgewerkt om de volgende nieuwe opties toe te voegen:
        - PeerAddressType: de waarde IPv4 of IPv6 kan worden opgegeven voor het bijwerken van een BGP-peering van het bijbehorende type adresfamilie
    * De cmdlet Remove-AzureBgpPeering is bijgewerkt om de volgende nieuwe opties toe te voegen:
        - PeerAddressType: de waarde IPv4, IPv6 of All kan worden opgegeven voor het verwijderen van een BGP-peering van het bijbehorende type adresfamilie of van alle typen

## <a name="20170607---version-410"></a>2017.06.07 - Versie 4.1.0
* AnalysisServices
    * Er zijn nieuwe SKU's toegevoegd: B1, B2, S0
    * Er is ondersteuning voor omhoog/omlaag schalen toegevoegd
* CognitiveServices
    * De gedetailleerde weergave van licentieovereenkomsten bij het maken van Cognitive Services-resources is bijgewerkt
* Compute
    * Oplossing voor Test-AzureRmVMAEMExtension voor virtuele machines met meerdere beheerde schijven
    * Set-AzureRmVMAEMExtension is bijgewerkt: opslaan van cache-informatie voor Premium Managed Disks is toegevoegd
    * Add-AzureRmVhd: de maximale grootte van een virtuele harde schijf wordt verhoogd tot 4 TB.
    * Stop-AzureRmVM: de documentatie voor de parameter STayProvisioned is verduidelijkt
    * New-AzureRmDiskUpdateConfig
      * Afgeschafte parameters: CreateOption, StorageAccountId, ImageReference, SourceUri, SourceResourceId
    * Set-AzureRmDiskUpdateImageReference: afgeschafte cmdlet
    * New-AzureRmSnapshotUpdateConfig
      * Afgeschafte parameters: CreateOption, StorageAccountId, ImageReference, SourceUri, SourceResourceId
    * Set-AzureRmSnapshotUpdateImageReference: afgeschafte cmdlet
* DataLakeStore
    * Enable-AzureRmDataLakeStoreKeyVault (Enable-AdlStoreKeyVault)
      * Door Key Vault beheerde versleuteling inschakelen voor DataLake Store
* DevTestLabs
    * De cmdlets voor het werken met de huidige en bijgewerkte DevTest Labs API-versie zijn bijgewerkt.
* IotHub
    * Er is routeringsondersteuning toegevoegd voor IoTHub-cmdlets
* KeyVault
  * Nieuwe cmdlets voor de ondersteuning van door KeyVault beheerde opslagaccountsleutels
    * Get-AzureKeyVaultManagedStorageAccount
    * Add-AzureKeyVaultManagedStorageAccount
    * Remove-AzureKeyVaultManagedStorageAccount
    * Update-AzureKeyVaultManagedStorageAccount
    * Update-AzureKeyVaultManagedStorageAccountKey
    * Get-AzureKeyVaultManagedStorageSasDefinition
    * Set-AzureKeyVaultManagedStorageSasDefinition
    * Remove-AzureKeyVaultManagedStorageSasDefinition
* Netwerk
    * Get-AzureRmNetworkUsage: nieuwe cmdlet om netwerkgebruik en capaciteitsgegevens weer te geven
    * Er zijn nieuwe GatewaySku-opties toegevoegd voor VirtualNetworkGateways
        * VpnGw1, VpnGw2, VpnGw3 zijn de nieuwe SKU's die zijn toegevoegd voor VPN-gateways
    * Set-AzureRmNetworkWatcherConfigFlowLog
      * De problemen met de Help-voorbeelden zijn opgelost
* NotificationHubs
    * Transparante update voor NotificationHubs-cmdlets voor de nieuwe API
* Profiel
    * Resolve-AzureRmError
      * Nieuwe cmdlet om foutgegevens en uitzonderingen van cmdlets weer te geven, inclusief vraag-/antwoordgegevens van de server
    * Send-Feedback
      * Feedback verzenden zonder in te loggen is mogelijk gemaakt
    * Get-AzureRmSubscription
      * De fout bij het ophalen van CSP-abonnementen is opgelost
* Resources
    * Het probleem is opgelost waarbij Get-AzureRMRoleAssignment resulteerde in een ongeldige aanvraag als het aantal roleassignments groter was dan 1000
        * Gebruikers kunnen Get-AzureRMRoleAssignment nu ook gebruiken als het aantal te retourneren roleassignments groter is dan 1000
* SQL
    * Restore-AzureRmSqlDatabase: documentatievoorbeeld bijgewerkt
* Storage
    * Er is ondersteuning voor AssignIdentity-instelling toegevoegd aan de cmdlets voor opslagaccounts in resourcemodus
        * New-AzureRmStorageAccount
        * Set-AzureRmStorageAccount
    * Er is ondersteuning voor Customer Key toegevoegd aan de cmdlets voor opslagaccounts in resourcemodus
        * Set-AzureRmStorageAccount
        * New-AzureRmStorageAccountEncryptionKeySource
* TrafficManager

    * Nieuwe monitorinstellingen MonitorIntervalInSeconds, MonitorTimeoutInSeconds, MonitorToleratedNumberOfFailures
    * Nieuw monitorprotocol TCP
* ServiceManagement
    * Add-AzureVhd: de maximale grootte van een virtuele harde schijf is verhoogd tot 4 TB.
    * New-AzureBGPPeering: ondersteuning voor LegacyMode
* Azure.Storage
    * De Help is bijgewerkt voor parameters die jokertekens accepteren en StorageContext-type is bijgewerkt

## <a name="20170523---version-402"></a>2017.05.23 - Versie 4.0.2
* Profiel
    * Add-AzureRmAccount
      * De parameteralias `-EnvironmentName` is toegevoegd voor achterwaartse compatibiliteit met 2.x-versies van AzureRM.profile

## <a name="20170512---version-401"></a>2017.05.12 - Versie 4.0.1
 * Het probleem met New-AzureStorageContext in offline-scenario's is opgelost: https://github.com/Azure/azure-powershell/issues/3939

## <a name="20170510---version-400"></a>2017.05.10 - Versie 4.0.0


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
