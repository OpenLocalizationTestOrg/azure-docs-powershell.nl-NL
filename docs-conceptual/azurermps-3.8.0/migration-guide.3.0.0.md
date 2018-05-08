# <a name="breaking-changes-for-microsoft-azure-powershell-300"></a><span data-ttu-id="513b3-101">Belangrijke wijzigingen voor Microsoft Azure PowerShell 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="513b3-101">Breaking changes for Microsoft Azure PowerShell 3.0.0.</span></span>

<span data-ttu-id="513b3-102">Dit document dient niet alleen als melding van een belangrijke wijziging, maar ook als migratiehandleiding voor gebruikers van de Microsoft Azure PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="513b3-102">This document serves as both a breaking change notification and migration guide for consumers of the Microsoft Azure PowerShell cmdlets.</span></span>  <span data-ttu-id="513b3-103">Elke sectie beschrijft zowel de reden voor de belangrijke wijziging als het eenvoudigste migratiepad.</span><span class="sxs-lookup"><span data-stu-id="513b3-103">Each section describes both the impetus for the breaking change and the migration path of least resistance.</span></span>  <span data-ttu-id="513b3-104">Raadpleeg voor een uitgebreidere context de pull-aanvraag die bij elke wijziging hoort.</span><span class="sxs-lookup"><span data-stu-id="513b3-104">For in-depth context, please refer to the pull request associated with each change.</span></span>

## <a name="table-of-contents"></a><span data-ttu-id="513b3-105">Inhoudsopgave</span><span class="sxs-lookup"><span data-stu-id="513b3-105">Table of Contents</span></span>
1. [<span data-ttu-id="513b3-106">Belangrijke wijzigingen voor Data Lake Store-cmdlets</span><span class="sxs-lookup"><span data-stu-id="513b3-106">Breaking changes to Data Lake Store cmdlets</span></span>](#breaking-changes-to-data-lake-store-cmdlets)
2. [<span data-ttu-id="513b3-107">Belangrijke wijzigingen voor ApiManagement-cmdlets</span><span class="sxs-lookup"><span data-stu-id="513b3-107">Breaking changes to ApiManagement cmdlets</span></span>](#breaking-changes-to-apimanagement-cmdlets)
3. [<span data-ttu-id="513b3-108">Belangrijke wijzigingen voor Network-cmdlets</span><span class="sxs-lookup"><span data-stu-id="513b3-108">Breaking changes to Network cmdlets</span></span>](#breaking-changes-to-network-cmdlets)

## <a name="breaking-changes-to-data-lake-store-cmdlets"></a><span data-ttu-id="513b3-109">Belangrijke wijzigingen voor Data Lake Store-cmdlets</span><span class="sxs-lookup"><span data-stu-id="513b3-109">Breaking changes to Data Lake Store cmdlets</span></span>

<span data-ttu-id="513b3-110">De volgende cmdlets worden beïnvloed door deze release ([PR 2965](https://github.com/Azure/azure-powershell/pull/2965)):</span><span class="sxs-lookup"><span data-stu-id="513b3-110">The following cmdlets were affected this release ([PR 2965](https://github.com/Azure/azure-powershell/pull/2965)):</span></span>

<span data-ttu-id="513b3-111">**Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)**</span><span class="sxs-lookup"><span data-stu-id="513b3-111">**Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)**</span></span>
- <span data-ttu-id="513b3-112">Deze cmdlet is verwijderd en vervangen door ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span><span class="sxs-lookup"><span data-stu-id="513b3-112">This cmdlet was removed and replaced with ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span></span>
- <span data-ttu-id="513b3-113">De oude cmdlet retourneerde een complex object dat de toegangsbeheerlijst (ACL) vertegenwoordigde.</span><span class="sxs-lookup"><span data-stu-id="513b3-113">The old cmdlet returned a complex object representing the access control list (ACL).</span></span> <span data-ttu-id="513b3-114">De nieuwe cmdlet retourneert een eenvoudige lijst met vermeldingen in het gekozen pad van de toegangsbeheerlijst.</span><span class="sxs-lookup"><span data-stu-id="513b3-114">The new cmdlet returns a simple list of entries in the chosen path's ACL.</span></span>

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

<span data-ttu-id="513b3-115">**Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)**</span><span class="sxs-lookup"><span data-stu-id="513b3-115">**Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)**</span></span>
- <span data-ttu-id="513b3-116">Deze cmdlet vervangt de oude cmdlet ``Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)``.</span><span class="sxs-lookup"><span data-stu-id="513b3-116">This cmdlet replaces the old cmdlet ``Get-AzureRmDataLakeStoreItemAcl (Get-AdlStoreItemAcl)``.</span></span>
- <span data-ttu-id="513b3-117">De nieuwe cmdlet retourneert een eenvoudige lijst met vermeldingen in het gekozen pad van de toegangsbeheerlijst, met het type ``DataLakeStoreItemAce[]``.</span><span class="sxs-lookup"><span data-stu-id="513b3-117">This new cmdlet returns a simple list of entries in the chosen path's ACL, with type ``DataLakeStoreItemAce[]``.</span></span>
- <span data-ttu-id="513b3-118">De uitvoer van deze cmdlet kan worden doorgegeven aan de parameter ``-Acl`` van de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="513b3-118">The output of this cmdlet can be passed in to the ``-Acl`` parameter of the following cmdlets:</span></span>
   - ``Remove-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAcl``
   - ``Set-AzureRmDataLakeStoreItemAclEntry``

```powershell
# Old
Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo

# New
Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
```

<span data-ttu-id="513b3-119">**Remove-AzureRmDataLakeStoreItemAcl (Remove-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAcl (Set-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAclEntry (Set-AdlStoreItemAclEntry)**</span><span class="sxs-lookup"><span data-stu-id="513b3-119">**Remove-AzureRmDataLakeStoreItemAcl (Remove-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAcl (Set-AdlStoreItemAcl)**, **Set-AzureRmDataLakeStoreItemAclEntry (Set-AdlStoreItemAclEntry)**</span></span>
- <span data-ttu-id="513b3-120">Deze cmdlets accepteren nu ``DataLakeStoreItemAce[]`` voor de parameter ``-Acl``.</span><span class="sxs-lookup"><span data-stu-id="513b3-120">These cmdlets now accept ``DataLakeStoreItemAce[]`` for the ``-Acl`` parameter.</span></span>
- <span data-ttu-id="513b3-121">``DataLakeStoreItemAce[]`` wordt geretourneerd door ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span><span class="sxs-lookup"><span data-stu-id="513b3-121">``DataLakeStoreItemAce[]`` is returned by ``Get-AzureRmDataLakeStoreItemAclEntry (Get-AdlStoreItemAclEntry)``.</span></span>

```powershell
# Old
$acl = Get-AdlStoreItemAcl -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $acl

# New
$aclEntries = Get-AdlStoreItemAclEntry -Account myadlsaccount -Path /foo
Set-AdlStoreItemAcl -Account myadlsaccount -Path /foo -Acl $aclEntries
```

## <a name="breaking-changes-to-apimanagement-cmdlets"></a><span data-ttu-id="513b3-122">Belangrijke wijzigingen voor ApiManagement-cmdlets</span><span class="sxs-lookup"><span data-stu-id="513b3-122">Breaking changes to ApiManagement cmdlets</span></span>

<span data-ttu-id="513b3-123">De volgende cmdlets worden beïnvloed door deze release ([PR 2971](https://github.com/Azure/azure-powershell/pull/2971)):</span><span class="sxs-lookup"><span data-stu-id="513b3-123">The following cmdlets were affected this release ([PR 2971](https://github.com/Azure/azure-powershell/pull/2971)):</span></span>

<span data-ttu-id="513b3-124">**New-AzureRmApiManagementVirtualNetwork**</span><span class="sxs-lookup"><span data-stu-id="513b3-124">**New-AzureRmApiManagementVirtualNetwork**</span></span>
- <span data-ttu-id="513b3-125">De vereiste parameters om te verwijzen naar een virtueel netwerk zijn gewijzigd van SubnetName en VnetId in SubnetResourceId, in de indeling ``/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ClassicNetwork/virtualNetworks/{virtualNetworkName}/subnets/{subnetName}``.</span><span class="sxs-lookup"><span data-stu-id="513b3-125">The required parameters to reference a virtual network changed from requiring SubnetName and VnetId to SubnetResourceId in format ``/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ClassicNetwork/virtualNetworks/{virtualNetworkName}/subnets/{subnetName}``</span></span>

```powershell
# Old
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetName <String> -VnetId <Guid>

# New
$virtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>

```

<span data-ttu-id="513b3-126">**De cmdlet Set-AzureRmApiManagementVirtualNetworks wordt niet langer ondersteund**</span><span class="sxs-lookup"><span data-stu-id="513b3-126">**Deprecating Cmdlet Set-AzureRmApiManagementVirtualNetworks**</span></span>
- <span data-ttu-id="513b3-127">Deze cmdlet wordt niet langer ondersteund omdat er meer dan één manier was om een virtueel netwerk in te stellen in relatie tot de ApiManagement-implementatie.</span><span class="sxs-lookup"><span data-stu-id="513b3-127">The Cmdlet is getting deprecated as there was more than one way to Set Virtual Network associated to ApiManagement deployment.</span></span>

```powershell
# Old
$networksList = @()
$networksList += New-AzureRmApiManagementVirtualNetwork -Location $vnetLocation -VnetId $vnetId -SubnetName $subnetName
Set-AzureRmApiManagementVirtualNetworks -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetworks $networksList

# New
$masterRegionVirtualNetwork = New-AzureRmApiManagementVirtualNetwork -Location <String> -SubnetResourceId <String>
Update-AzureRmApiManagementDeployment -ResourceGroupName "ContosoGroup" -Name "ContosoApi" -VirtualNetwork $masterRegionVirtualNetwork
```

## <a name="breaking-changes-to-network-cmdlets"></a><span data-ttu-id="513b3-128">Belangrijke wijzigingen voor Network-cmdlets</span><span class="sxs-lookup"><span data-stu-id="513b3-128">Breaking changes to Network cmdlets</span></span>

<span data-ttu-id="513b3-129">De volgende cmdlets worden beïnvloed door deze release ([PR 2982](https://github.com/Azure/azure-powershell/pull/2982)):</span><span class="sxs-lookup"><span data-stu-id="513b3-129">The following cmdlets were affected this release ([PR 2982](https://github.com/Azure/azure-powershell/pull/2982)):</span></span>

<span data-ttu-id="513b3-130">**New-AzureRmVirtualNetworkGateway**</span><span class="sxs-lookup"><span data-stu-id="513b3-130">**New-AzureRmVirtualNetworkGateway**</span></span>
- <span data-ttu-id="513b3-131">Beschrijving van wat is er gewijzigd: ``:- Bool parameter:-ActiveActive`` is verwijderd en ``SwitchParameter:-EnableActiveActiveFeature`` is toegevoegd om de functie Actief/Actief in te schakelen voor een nieuw gemaakte virtuele netwerkgateway.</span><span class="sxs-lookup"><span data-stu-id="513b3-131">Description of what has changed ``:- Bool parameter:-ActiveActive`` is removed and ``SwitchParameter:-EnableActiveActiveFeature`` is added for enabling Active-Active feature on newly creating virtual network gateway.</span></span>

```powershell
# Old 
# Sample of how the cmdlet was previously called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -ActiveActive $true

# New
# Sample of how the cmdlet should now be called
New-AzureRmVirtualNetworkGateway -ResourceGroupName $rgname -name $rname -Location $location -IpConfigurations $vnetIpConfig1,$vnetIpConfig2 -GatewayType Vpn -VpnType RouteBased -EnableBgp $false -GatewaySku HighPerformance -EnableActiveActiveFeature
```

<span data-ttu-id="513b3-132">Set-AzureRmVirtualNetworkGateway</span><span class="sxs-lookup"><span data-stu-id="513b3-132">Set-AzureRmVirtualNetworkGateway</span></span>
- <span data-ttu-id="513b3-133">Beschrijving van wat er is gewijzigd: ``:- Bool parameter:-ActiveActive`` is verwijderd en 2 ``SwitchParameters:-EnableActiveActiveFeature`` / ``DisableActiveActiveFeature`` zijn toegevoegd om de functie Actief/Actief in en uit te schakelen voor een virtuele netwerkgateway.</span><span class="sxs-lookup"><span data-stu-id="513b3-133">Description of what has changed ``:- Bool parameter:-ActiveActive`` is removed and 2 ``SwitchParameters:-EnableActiveActiveFeature`` / ``DisableActiveActiveFeature`` are added for enabling and disabling Active-Active feature on virtual network gateway.</span></span>

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