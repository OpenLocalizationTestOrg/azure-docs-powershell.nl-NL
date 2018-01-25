# <a name="breaking-changes-for-microsoft-azure-powershell-300"></a>Belangrijke wijzigingen voor Microsoft Azure PowerShell 3.0.0.

Dit document dient niet alleen als melding van een belangrijke wijziging, maar ook als migratiehandleiding voor gebruikers van de Microsoft Azure PowerShell-cmdlets.  Elke sectie beschrijft zowel de reden voor de belangrijke wijziging als het eenvoudigste migratiepad.  Raadpleeg voor een uitgebreidere context de pull-aanvraag die bij elke wijziging hoort.

## <a name="table-of-contents"></a>Inhoudsopgave
1. [Belangrijke wijzigingen voor Data Lake Store-cmdlets](#breaking-changes-to-data-lake-store-cmdlets)
2. [Belangrijke wijzigingen voor ApiManagement-cmdlets](#breaking-changes-to-apimanagement-cmdlets)
3. [Belangrijke wijzigingen voor Network-cmdlets](#breaking-changes-to-network-cmdlets)

## <a name="breaking-changes-to-data-lake-store-cmdlets"></a>Belangrijke wijzigingen voor Data Lake Store-cmdlets

De volgende cmdlets worden beïnvloed door deze release ([PR 2965](https://github.com/Azure/azure-powershell/pull/2965)):

**Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)**
- Deze cmdlet is verwijderd en vervangen door ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.
- De oude cmdlet retourneerde een complex object dat de toegangsbeheerlijst (ACL) vertegenwoordigde. De nieuwe cmdlet retourneert een eenvoudige lijst met vermeldingen in het gekozen pad van de toegangsbeheerlijst.

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

**Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)**
- Deze cmdlet vervangt de oude cmdlet ``Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)``.
- De nieuwe cmdlet retourneert een eenvoudige lijst met vermeldingen in het gekozen pad van de toegangsbeheerlijst, met het type ``DataLakeStoreItemAce[]``.
- De uitvoer van deze cmdlet kan worden doorgegeven aan de parameter ``-Acl`` van de volgende cmdlets:
   - ``Remove-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAclEntry``

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

**Remove-AzureRmDataLakeStoreItemAcl (Remove-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAcl (Set-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAclEntry (Set-AdlStoreItemAclEntry)**
- Deze cmdlets accepteren nu ``DataLakeStoreItemAce[]`` voor de parameter ``-Acl``.
- ``DataLakeStoreItemAce[]`` wordt geretourneerd door ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.

```powershell
# Old
$acl = Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $acl

# New
$aclEntries = Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $aclEntries
```

## <a name="breaking-changes-to-apimanagement-cmdlets"></a>Belangrijke wijzigingen voor ApiManagement-cmdlets

De volgende cmdlets worden beïnvloed door deze release ([PR 2971](https://github.com/Azure/azure-powershell/pull/2971)):

**New-AzureRmApiManagementVirtualNetwork**
- De vereiste parameters om te verwijzen naar een virtueel netwerk zijn gewijzigd van SubnetName en VnetId in SubnetResourceId, in de indeling ``/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ClassicNetwork/virtualNetworks/{virtualNetworkName}/subnets/{subnetName}``.

```powershell
# Old
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetName <String> -VnetId <Guid>

# New
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>

```

**De cmdlet Set-AzureRmApiManagementVirtualNetworks wordt niet langer ondersteund**
- Deze cmdlet wordt niet langer ondersteund omdat er meer dan één manier was om een virtueel netwerk in te stellen in relatie tot de ApiManagement-implementatie.

```powershell
# Old
$networksList = @()
$networksList += New-AzureRmApiManagementVirtualNetwork -Location $vnetLocation -VnetId $vnetId -SubnetName $subnetName
Set-AzureRmApiManagementVirtualNetworks -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetworks $networksList

# New
$masterRegionVirtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>
Update-AzureRmApiManagementDeployment -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetwork $masterRegionVirtualNetwork
```

## <a name="breaking-changes-to-network-cmdlets"></a>Belangrijke wijzigingen voor Network-cmdlets

De volgende cmdlets worden beïnvloed door deze release ([PR 2982](https://github.com/Azure/azure-powershell/pull/2982)):

**New-AzureRmVirtualNetworkGateway**
- Beschrijving van wat is er gewijzigd: ``:- Bool parameter:-ActiveActive`` is verwijderd en ``SwitchParameter:-EnableActiveActiveFeature`` is toegevoegd om de functie Actief/Actief in te schakelen voor een nieuw gemaakte virtuele netwerkgateway.

```powershell
# Old 
# Sample of how the cmdlet was previously called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -ActiveActive $true

# New
# Sample of how the cmdlet should now be called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -EnableActiveActiveFeature
```

Set-AzureRmVirtualNetworkGateway
- Beschrijving van wat er is gewijzigd: ``:- Bool parameter:-ActiveActive`` is verwijderd en 2 ``SwitchParameters:-EnableActiveActiveFeature`` / ``DisableActiveActiveFeature`` zijn toegevoegd om de functie Actief/Actief in en uit te schakelen voor een virtuele netwerkgateway.

```powershell
# Old
# Sample of how the cmdlet was previously called
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -ActiveActive $true
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -ActiveActive $false  

# New
# Sample of how the cmdlet should now be called
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -EnableActiveActiveFeature
Set-AzureRmVirtualNetworkGateway -VirtualNetworkGateway $gw -DisableActiveActiveFeature
```