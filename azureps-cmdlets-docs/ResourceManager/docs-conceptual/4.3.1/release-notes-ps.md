Installatieprogramma voor Azure PowerShell 4.3.1: [koppeling](https://github.com/Azure/azure-powershell/releases/download/v4.3.1-August2017/azure-powershell.4.3.1.msi)

Galeriemodule voor ARM-cmdlets: [koppeling](https://www.powershellgallery.com/packages/AzureRM/4.3.1)

Galeriemodule voor Legacy-cmdlets voor Service Management (RDFE): [koppeling](https://www.powershellgallery.com/packages/Azure/4.3.1)

## <a name="changes-in-431"></a>Wijzigingen in 4.3.1

- Probleem opgelost met bepaalde assembly's die niet worden ondertekend, wat resulteert in de fout `could not load file or assembly` bij het importeren van modules

## <a name="changes-in-430"></a>Wijzigingen in 4.3.0

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
    * Ondersteuning voor NodeConfiguration build-versiebeheer toegevoegd aan StartAzureAutomationDscCompilationJob en ImportAzureAutomationDscNodeConfiguration.
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
    * Commandlets bijgewerkt met nieuwe parameter en parameteralias
        - Onderstaande cmdlets bijgewerkt met parametersets voor naamruimte en EventHub voor de werking van AuthorizationRule
        - New-AzureRmEventHubAuthorizationRule
            + Voegt een nieuwe AuthorizationRule toe aan de bestaande naamruimte of EventHub.
        - Get-AzureRmEventHubAuthorizationRule
            + Haalt een AuthorizationRule/lijst AuthorizationRules op voor de bestaande naamruimte of EventHub.
        - Set-AzureRmEventHubAuthorizationRule
            + Werkt eigenschappen bij van de bestaande AuthorizationRule of EventHub-naamruimte.
        - Remove-AzureRmEventHubAuthorizationRule
            + Verwijdert een bestaande AuthorizationRule of een bestaande naamruimte of EventHub.
        - New-AzureRmEventHubKey
            + Genereert een nieuwe primaire/secundaire sleutel voor AuthorizationRule van bestaande naamruimte of EventHub.
        - Get-AzureRmEventHubKey
            + Haalt een primaire/secundaire sleutel op voor AuthorizationRule van bestaande naamruimte of EventHub.
* Netwerk
    * New-AzureRmExpressRouteCircuitPeeringConfig: IPv6-ondersteuning toegevoegd. Nieuwe optionele parameter toegevoegd
        - PeerAddressType
    * Set-AzureRmExpressRouteCircuitPeeringConfig: IPv6-ondersteuning toegevoegd. Nieuwe optionele parameter toegevoegd
        - PeerAddressType
    * Remove-AzureRmExpressRouteCircuitPeeringConfig: IPv6-ondersteuning toegevoegd. Nieuwe optionele parameter toegevoegd
        - PeerAddressType
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
     - New-AzureRmServiceBusAuthorizationRule
       - Voegt een nieuwe AuthorizationRule toe aan bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - Get-AzureRmServiceBusAuthorizationRule
       - Haalt een AuthorizationRule/lijst AuthorizationRules op voor bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - Set-AzureRmServiceBusAuthorizationRule
       - Werkt de eigenschappen bij van een bestaande AuthorizationRule of bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - New-AzureRmServiceBusKey
       - Genereert een nieuwe primaire/secundaire sleutel voor AuthorizationRule van bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - Get-AzureRmServiceBusKey
       - Haalt primaire/secundaire sleutel op voor AuthorizationRule van bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
     - Remove-AzureRmServiceBusNamespaceAuthorizationRule
       - Verwijdert een bestaande AuthorizationRule of bestaande naamruimte/wachtrij/onderwerp van ServiceBus.
    * ResourceGroup-eigenschap toegevoegd aan NamespaceAttributes
* SQL
    * Bijwerken van Set-AzureRmSqlServerTransparentDataEncryptionProtector geeft een waarschuwing weer en vereist bevestiging indien het type Encryption Protector Type wordt ingesteld op AzureKeyVault
    * Bijgewerkte cmdlets toegevoegd voor controle-instellingen
        - Cmdlet Get-AzureRmSqlDatabaseAuditing toegevoegd, waarmee de controle-instellingen van een Azure SQL-database worden opgehaald.
        - Cmdlet Get-AzureRmSqlServerAuditing toegevoegd, waarmee de controle-instellingen van een Azure SQL-server worden opgehaald.
        - Cmdlet Set-AzureRmSqlDatabaseAuditing toegevoegd, waarmee de controle-instellingen van een Azure SQL-database worden gewijzigd.
        - Cmdlet Set-AzureRmSqlServerAuditing toegevoegd, waarmee de controle-instellingen van een Azure SQL-server worden gewijzigd.
    * De bestaande cmdlets voor controlebeleid worden hiermee niet langer ondersteund
        - Get-AzureRmSqlDatabaseAuditingPolicy wordt niet langer ondersteund
        - Get-AzureRmSqlServerAuditingPolicy wordt niet langer ondersteund
        - Set-AzureRmSqlDatabaseAuditingPolicy wordt niet langer ondersteund
        - Set-AzureRmSqlServerAuditingPolicy wordt niet langer ondersteund
        - Use-AzureRmSqlServerAuditingPolicy wordt niet langer ondersteund
        - Remove-AzureRmSqlDatabaseAuditing wordt niet langer ondersteund
        - Remove-AzureRmSqlServerAuditing wordt niet langer ondersteund
    * Parseren van schemabestanden voor de Update-AzureRmSqlSyncGroup is niet meer hoofdlettergevoelig.
* Storage
    * Er is ondersteuning voor NeworkRule toegevoegd aan de cmdlets voor opslagaccounts in resourcemodus
        - New-AzureRmStorageAccount
        - Set-AzureRmStorageAccount
        - Get-AzureRmStorageAccountNetworkRuleSet
        - Update-AzureRmStorageAccountNetworkRuleSet
        - Add-AzureRmStorageAccountNetworkRule
        - Remove-AzureRmStorageAccountNetworkRule

[Wijzigingen sinds de laatste versie](https://github.com/Azure/azure-powershell/compare/v4.2.1-July2017...v4.3.1-August2017) weergeven
