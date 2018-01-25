# <a name="breaking-changes-for-microsoft-azure-powershell-400"></a><span data-ttu-id="2dd0c-101">Belangrijke wijzigingen voor Microsoft Azure PowerShell 4.0.0</span><span class="sxs-lookup"><span data-stu-id="2dd0c-101">Breaking changes for Microsoft Azure PowerShell 4.0.0</span></span>

<span data-ttu-id="2dd0c-102">Dit document dient niet alleen als melding van een belangrijke wijziging, maar ook als migratiehandleiding voor gebruikers van de Microsoft Azure PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-102">This document serves as both a breaking change notification and migration guide for consumers of the Microsoft Azure PowerShell cmdlets.</span></span> <span data-ttu-id="2dd0c-103">Elke sectie beschrijft zowel de reden voor de belangrijke wijziging als het eenvoudigste migratiepad.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-103">Each section describes both the impetus for the breaking change and the migration path of least resistance.</span></span> <span data-ttu-id="2dd0c-104">Raadpleeg voor een uitgebreidere context de pull-aanvraag die bij elke wijziging hoort.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-104">For in-depth context, please refer to the pull request associated with each change.</span></span>

## <a name="table-of-contents"></a><span data-ttu-id="2dd0c-105">Inhoudsopgave</span><span class="sxs-lookup"><span data-stu-id="2dd0c-105">Table of Contents</span></span>

- [<span data-ttu-id="2dd0c-106">Belangrijke wijzigingen voor Compute-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-106">Breaking changes to Compute cmdlets</span></span>](#breaking-changes-to-compute-cmdlets)
- [<span data-ttu-id="2dd0c-107">Belangrijke wijzigingen voor EventHub-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-107">Breaking changes to EventHub cmdlets</span></span>](#breaking-changes-to-eventhub-cmdlets)
- [<span data-ttu-id="2dd0c-108">Belangrijke wijzigingen voor Insights-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-108">Breaking changes to Insights cmdlets</span></span>](#breaking-changes-to-insights-cmdlets)
- [<span data-ttu-id="2dd0c-109">Belangrijke wijzigingen voor Network-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-109">Breaking changes to Network cmdlets</span></span>](#breaking-changes-to-network-cmdlets)
- [<span data-ttu-id="2dd0c-110">Belangrijke wijzigingen voor ServiceBus-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-110">Breaking changes to ServiceBus cmdlets</span></span>](#breaking-changes-to-servicebus-cmdlets)
- [<span data-ttu-id="2dd0c-111">Belangrijke wijzigingen voor SQL-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-111">Breaking changes to Sql cmdlets</span></span>](#breaking-changes-to-sql-cmdlets)
- [<span data-ttu-id="2dd0c-112">Belangrijke wijzigingen voor Storage-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-112">Breaking changes to Storage cmdlets</span></span>](#breaking-changes-to-storage-cmdlets)
- [<span data-ttu-id="2dd0c-113">Belangrijke wijzigingen voor Profile-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-113">Breaking Changes to Profile Cmdlets</span></span>](#breaking-changes-to-profile-cmdlets)
## <a name="breaking-changes-to-compute-cmdlets"></a><span data-ttu-id="2dd0c-114">Belangrijke wijzigingen voor Compute-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-114">Breaking changes to Compute cmdlets</span></span>

<span data-ttu-id="2dd0c-115">De volgende uitvoertypen worden beïnvloed door deze release:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-115">The following output types were affected this release:</span></span>

### <a name="psvirtualmachine"></a><span data-ttu-id="2dd0c-116">PSVirtualMachine</span><span class="sxs-lookup"><span data-stu-id="2dd0c-116">PSVirtualMachine</span></span>
- <span data-ttu-id="2dd0c-117">De eigenschappen van `DataDiskNames` en `NetworkInterfaceIDs` op het hoogste niveau van het `PSVirtualMachine`-object zijn verwijderd uit het uitvoertype.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-117">Top level properties `DataDiskNames` and `NetworkInterfaceIDs` of nthe `PSVirtualMachine` object have been removed from the output type.</span></span> <span data-ttu-id="2dd0c-118">Deze eigenschappen zijn altijd al beschikbaar geweest in de eigenschappen `StorageProfile` en `NetworkProfile` van het `PSVirtualMachine`-object. Dit is voortaan dan ook de manier om deze aan te spreken.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-118">These properties have always been available in the `StorageProfile` and `NetworkProfile` properties of the `PSVirtualMachine` object and will be the way they will need to be accessed going forward.</span></span>
- <span data-ttu-id="2dd0c-119">Deze wijziging is van invloed op de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-119">This change affects the following cmdlets:</span></span>
    - `Add-AzureRmVMDataDisk`
    - `Add-AzureRmVMNetworkInterface`
    - `Get-AzureRmVM`
    - `Remove-AzureRmVMDataDisk`
    - `Remove-AzureRmVMNetworkInterface`
    - `Set-AzureRmVMDataDisk`

```powershell
# Old
$vm.DataDiskNames
$vm.NetworkInterfaceIDs

# New
$vm.StorageProfile.DataDisks | Select -Property Name
$vm.NetworkProfile.NetworkInterfaces | Select -Property Id
```

## <a name="breaking-changes-to-eventhub-cmdlets"></a><span data-ttu-id="2dd0c-120">Belangrijke wijzigingen voor EventHub-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-120">Breaking changes to EventHub cmdlets</span></span>

<span data-ttu-id="2dd0c-121">De volgende cmdlets worden beïnvloed door deze release:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-121">The following cmdlets were affected this release:</span></span>

### <a name="get-azurermeventhubnamespace"></a><span data-ttu-id="2dd0c-122">Get-AzureRmEventHubNamespace</span><span class="sxs-lookup"><span data-stu-id="2dd0c-122">Get-AzureRmEventHubNamespace</span></span>
- <span data-ttu-id="2dd0c-123">De eigenschap `ResourceGroupName` is verwijderd uit het uitvoertype `NamespaceAttributes`</span><span class="sxs-lookup"><span data-stu-id="2dd0c-123">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

### <a name="new-azurermeventhubnamespace"></a><span data-ttu-id="2dd0c-124">New-AzureRmEventHubNamespace</span><span class="sxs-lookup"><span data-stu-id="2dd0c-124">New-AzureRmEventHubNamespace</span></span>
- <span data-ttu-id="2dd0c-125">De eigenschap `ResourceGroupName` is verwijderd uit het uitvoertype `NamespaceAttributes`</span><span class="sxs-lookup"><span data-stu-id="2dd0c-125">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

## <a name="breaking-changes-to-insights-cmdlets"></a><span data-ttu-id="2dd0c-126">Belangrijke wijzigingen voor Insights-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-126">Breaking changes to Insights cmdlets</span></span>

<span data-ttu-id="2dd0c-127">De volgende cmdlets worden beïnvloed door deze release:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-127">The following cmdlets were affected this release:</span></span>
    
### <a name="get-azurermusage"></a><span data-ttu-id="2dd0c-128">Get-AzureRmUsage</span><span class="sxs-lookup"><span data-stu-id="2dd0c-128">Get-AzureRmUsage</span></span>
- <span data-ttu-id="2dd0c-129">Deze cmdlet is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-129">This cmdlet has been deprecated.</span></span>

### <a name="remove-azurermalertrule"></a><span data-ttu-id="2dd0c-130">Remove-AzureRmAlertRule</span><span class="sxs-lookup"><span data-stu-id="2dd0c-130">Remove-AzureRmAlertRule</span></span>
- <span data-ttu-id="2dd0c-131">De uitvoer van deze cmdlet is gewijzigd van een lijst met een enkel object in een enkel object. Dit object bevat de requestId en een statuscode.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-131">The output of this cmdlet has changed from a list with a single object to a single object; this object includes the requestId, and status code.</span></span>
    
```powershell
# Old  
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name chiricutin
if ($s1 -ne $null)
{
    $r = $s1(0).RequestId
    $s = $s1(0).StatusCode
}

# New
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name chiricutin
$r = $s1.RequestId
$s = $s1.StatusCode
```
    
### <a name="add-azurermlogalertrule"></a><span data-ttu-id="2dd0c-132">Add-AzureRmLogAlertRule</span><span class="sxs-lookup"><span data-stu-id="2dd0c-132">Add-AzureRmLogAlertRule</span></span>
- <span data-ttu-id="2dd0c-133">Deze cmdlet is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-133">This cmdlet has been deprecated.</span></span>
    
### <a name="get-azurermalertrule"></a><span data-ttu-id="2dd0c-134">Get-AzureRmAlertRule</span><span class="sxs-lookup"><span data-stu-id="2dd0c-134">Get-AzureRmAlertRule</span></span>
- <span data-ttu-id="2dd0c-135">Elk element van de uitvoer (een lijst met objecten) van deze cmdlet is afgevlakt. Dit houdt in dat er geen objecten meer worden geretourneerd met de structuur `{ Id, Location, Name, Tags, Properties }`, maar met de structuur `{ Id, Location, Name, Tags, Type, Description, IsEnabled, Condition, Actions, LastUpdatedTime, ...}`. Deze bestaat uit alle kenmerken van een Azure-resource plus alle kenmerken van een AlertRuleResource op het hoogste niveau.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-135">Each element of the the output (a list of objects) of this cmdlet is flattened, i.e. instead of returning objects with the structure `{ Id, Location, Name, Tags, Properties }` it will return objects with the structure `{ Id, Location, Name, Tags, Type, Description, IsEnabled, Condition, Actions, LastUpdatedTime, ...}`, which is all of the attributes of an Azure Resource plus all of the attributes of an AlertRuleResource at the top level.</span></span>
    
```powershell
# Old
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -fore red "Error updating alert rule"
      
    Write-Host $rules(0).Id
    Write-Host $rules(0).Properties.IsEnabled
    Write-Host $rules(0).Properties.Condition
}

# New
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -fore red "Error updating alert rule"
 
    Write-Host $rules(0).Id
      
    # Properties will remain for a while
    Write-Host $rules(0).Properties.IsEnabled
      
    # But the properties will be at the top level too. Later Properties will be removed
    Write-Host $rules(0).IsEnabled
    Write-Host $rules(0).Condition
}
```
    
### <a name="get-azurermautoscalesetting"></a><span data-ttu-id="2dd0c-136">Get-AzureRmAutoscaleSetting</span><span class="sxs-lookup"><span data-stu-id="2dd0c-136">Get-AzureRmAutoscaleSetting</span></span>
- <span data-ttu-id="2dd0c-137">Het veld `AutoscaleSettingResourceName` is afgeschaft, omdat dit altijd dezelfde waarde heeft als het veld `Name`.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-137">The `AutoscaleSettingResourceName` field is deprecated since it always has the same value as the `Name` field.</span></span>

```powershell
# Old  
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
if ($s1.AutoscaleSettingResourceName -ne $s1.Name)
{
    Write-Host "There is something wrong with the name"
}

# New
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
    
# There won't be a AutoscaleSettingResourceName
Write-Host $s1.Name
```
    
### <a name="remove-azurermlogprofile"></a><span data-ttu-id="2dd0c-138">Remove-AzureRmLogProfile</span><span class="sxs-lookup"><span data-stu-id="2dd0c-138">Remove-AzureRmLogProfile</span></span>
- <span data-ttu-id="2dd0c-139">De uitvoer van deze cmdlet is gewijzigd van `Boolean` in een object dat `RequestId` en `StatusCode` bevat.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-139">The output of this cmdlet will change from `Boolean` to and object containing `RequestId` and `StatusCode`</span></span>

```powershell
# Old  
$s1 = Remove-AzureRmLogProfile -Name myLogProfile
if ($s1 -eq $true)
{
    Write-Host "Removed"
}
else
{
    Write-Host "Failed"
}

# New
$s1 = Remove-AzureRmLogProfile -Name myLogProfile
$r = $s1.RequestId
$s = $s1.StatusCode
```
    
### <a name="add-azurermlogprofile"></a><span data-ttu-id="2dd0c-140">Add-AzureRmLogProfile</span><span class="sxs-lookup"><span data-stu-id="2dd0c-140">Add-AzureRmLogProfile</span></span>
- <span data-ttu-id="2dd0c-141">De uitvoer van deze cmdlet is gewijzigd van een object dat de requestId, de statuscode en de bijgewerkte of de zojuist gemaakte resource bevat</span><span class="sxs-lookup"><span data-stu-id="2dd0c-141">The output of this cmdlet will change from an object that includes the requestId, status code, and the updated or newly created resource</span></span>
    
```powershell
# Old  
$s1 = Add-AzureRmLogProfile -Name default -StorageAccountId /subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162 -Locations Global -categ Delete, Write, Action -retention 3
$r = $s1.ServiceBusRuleId

# New
$s1 = Add-AzureRmLogProfile -Name default -StorageAccountId /subscriptions/df602c9c-7aa0-407d-a6fb-eb20c8bd1192/resourceGroups/JohnKemTest/providers/Microsoft.Storage/storageAccounts/johnkemtest8162 -Locations Global -categ Delete, Write, Action -retention 3
$r = $s1.RequestId
$s = $s1.StatusCode
$a = $s1.NewResource.ServiceBusRuleId
    
```
    
### <a name="set-azurermdiagnosticsettings"></a><span data-ttu-id="2dd0c-142">Set-AzureRmDiagnosticSettings</span><span class="sxs-lookup"><span data-stu-id="2dd0c-142">Set-AzureRmDiagnosticSettings</span></span>
- <span data-ttu-id="2dd0c-143">De naam van deze opdracht wordt gewijzigd in `Update-AzureRmDiagnsoticSettings`.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-143">The command is going to be renamed to `Update-AzureRmDiagnsoticSettings`</span></span>

```powershell
# Old
Set-AzureRmDiagnosticSettings

# New
Update-AzureRmDiagnosticSettings
```

## <a name="breaking-changes-to-network-cmdlets"></a><span data-ttu-id="2dd0c-144">Belangrijke wijzigingen voor Network-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-144">Breaking changes to Network cmdlets</span></span>

<span data-ttu-id="2dd0c-145">De volgende cmdlets worden beïnvloed door deze release:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-145">The following cmdlets were affected this release:</span></span>

### <a name="new-azurermvirtualnetworkgatewayconnection"></a><span data-ttu-id="2dd0c-146">New-AzureRmVirtualNetworkGatewayConnection</span><span class="sxs-lookup"><span data-stu-id="2dd0c-146">New-AzureRmVirtualNetworkGatewayConnection</span></span>
- <span data-ttu-id="2dd0c-147">De parameter `EnableBgp` is gewijzigd om een `boolean` te accepteren in plaats van een `string`.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-147">`EnableBgp` parameter has been changed to take a `boolean` instead of a `string`</span></span>

```powershell
# Old
New-AzureRmVirtualNetworkGatewayConnection -ResourceGroupName "RG" -name "conn1" -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localnetGateway -ConnectionType IPsec -SharedKey "key" -EnableBgp "true"

# New
New-AzureRmVirtualNetworkGatewayConnection -ResourceGroupName "RG" -name "conn1" -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localnetGateway -ConnectionType IPsec -SharedKey "key" -EnableBgp $true
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a><span data-ttu-id="2dd0c-148">Belangrijke wijzigingen voor ServiceBus-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-148">Breaking changes to ServiceBus cmdlets</span></span>

<span data-ttu-id="2dd0c-149">De volgende cmdlets worden beïnvloed door deze release:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-149">The following cmdlets were affected this release:</span></span>

### <a name="get-azurermservicebusnamespace"></a><span data-ttu-id="2dd0c-150">Get-AzureRmServiceBusNamespace</span><span class="sxs-lookup"><span data-stu-id="2dd0c-150">Get-AzureRmServiceBusNamespace</span></span>
- <span data-ttu-id="2dd0c-151">De eigenschap `ResourceGroupName` is verwijderd uit het uitvoertype `NamespaceAttributes`</span><span class="sxs-lookup"><span data-stu-id="2dd0c-151">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

### <a name="new-azurermservicebusnamespace"></a><span data-ttu-id="2dd0c-152">New-AzureRmServiceBusNamespace</span><span class="sxs-lookup"><span data-stu-id="2dd0c-152">New-AzureRmServiceBusNamespace</span></span>

- <span data-ttu-id="2dd0c-153">De eigenschap `ResourceGroupName` is verwijderd uit het uitvoertype `NamespaceAttributes`</span><span class="sxs-lookup"><span data-stu-id="2dd0c-153">The property `ResourceGroupName` has been removed from the output type `NamespaceAttributes`</span></span>

## <a name="breaking-changes-to-sql-cmdlets"></a><span data-ttu-id="2dd0c-154">Belangrijke wijzigingen voor SQL-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-154">Breaking changes to Sql cmdlets</span></span>

<span data-ttu-id="2dd0c-155">De volgende cmdlets worden beïnvloed door deze release:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-155">The following cmdlets were affected this release:</span></span>

### <a name="new-azurermsqldatabasefailovergroup"></a><span data-ttu-id="2dd0c-156">New-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="2dd0c-156">New-AzureRmSqlDatabaseFailoverGroup</span></span>
- <span data-ttu-id="2dd0c-157">De parameter `Tag` is verwijderd</span><span class="sxs-lookup"><span data-stu-id="2dd0c-157">`Tag` parameter has been removed</span></span>
- <span data-ttu-id="2dd0c-158">De naam van de parameter `GracePeriodWithDataLossHour` is gewijzigd in `GracePeriodWithDataLossHours`</span><span class="sxs-lookup"><span data-stu-id="2dd0c-158">`GracePeriodWithDataLossHour` parameter has been renamed to `GracePeriodWithDataLossHours`</span></span>

```powershell
# Old
New-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -FailoverPolicy Automatic -GracePeriodWithDataLossHour 1 -Tag @{ Environment="Test" }

# New
New-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -FailoverPolicy Automatic -GracePeriodWithDataLossHours 1
```

### <a name="set-azurermsqldatabasefailovergroup"></a><span data-ttu-id="2dd0c-159">Set-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="2dd0c-159">Set-AzureRmSqlDatabaseFailoverGroup</span></span>
- <span data-ttu-id="2dd0c-160">De parameter `Tag` is verwijderd</span><span class="sxs-lookup"><span data-stu-id="2dd0c-160">`Tag` parameter has been removed</span></span>
- <span data-ttu-id="2dd0c-161">De naam van de parameter `GracePeriodWithDataLossHour` is gewijzigd in `GracePeriodWithDataLossHours`</span><span class="sxs-lookup"><span data-stu-id="2dd0c-161">`GracePeriodWithDataLossHour` parameter has been renamed to `GracePeriodWithDataLossHours`</span></span>

```powershell
# Old
Set-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -FailoverPolicy Automatic -GracePeriodWithDataLossHour 1 -Tag @{ Environment="Test" }

# New
Set-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -FailoverPolicy Automatic -GracePeriodWithDataLossHours 1
```

### <a name="add-azurermsqldatabasetofailovergroup"></a><span data-ttu-id="2dd0c-162">Add-AzureRmSqlDatabaseToFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="2dd0c-162">Add-AzureRmSqlDatabaseToFailoverGroup</span></span>
- <span data-ttu-id="2dd0c-163">De parameter `Tag` is verwijderd</span><span class="sxs-lookup"><span data-stu-id="2dd0c-163">`Tag` parameter has been removed</span></span>

```powershell
# Old
Add-AzureRmSqlDatabaseToFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1 -Tag @{ Environment="Test" }

# New
Add-AzureRmSqlDatabaseToFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1
```

###  <a name="remove-azurermsqldatabasefromfailovergroup"></a><span data-ttu-id="2dd0c-164">Remove-AzureRmSqlDatabaseFromFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="2dd0c-164">Remove-AzureRmSqlDatabaseFromFailoverGroup</span></span>
- <span data-ttu-id="2dd0c-165">De parameter `Tag` is verwijderd</span><span class="sxs-lookup"><span data-stu-id="2dd0c-165">`Tag` parameter has been removed</span></span>

```powershell
# Old
Remove-AzureRmSqlDatabaseFromFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1 -Tag @{ Environment="Test" }

# New
Remove-AzureRmSqlDatabaseFromFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1
```

### <a name="remove-azurermsqldatabasefailovergroup"></a><span data-ttu-id="2dd0c-166">Remove-AzureRmSqlDatabaseFailoverGroup</span><span class="sxs-lookup"><span data-stu-id="2dd0c-166">Remove-AzureRmSqlDatabaseFailoverGroup</span></span>
- <span data-ttu-id="2dd0c-167">De parameter `PartnerResourceGroupName` is verwijderd</span><span class="sxs-lookup"><span data-stu-id="2dd0c-167">`PartnerResourceGroupName` parameter has been removed</span></span>
- <span data-ttu-id="2dd0c-168">De parameter `PartnerServerName` is verwijderd</span><span class="sxs-lookup"><span data-stu-id="2dd0c-168">`PartnerServerName` parameter has been removed</span></span>

```powershell
# Old
Remove-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -PartnerResourceGroupName rg

# New
Remove-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg
```

### <a name="set-azurermsqldatabasethreatdetectionpolicy"></a><span data-ttu-id="2dd0c-169">Set-AzureRmSqlDatabaseThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="2dd0c-169">Set-AzureRmSqlDatabaseThreatDetectionPolicy</span></span>
- <span data-ttu-id="2dd0c-170">De waarde `Usage_Anomaly` is niet meer geldig voor de parameter `ExcludedDetectionType`</span><span class="sxs-lookup"><span data-stu-id="2dd0c-170">The value `Usage_Anomaly` is no longer valid for the parameter `ExcludedDetectionType`</span></span>

### <a name="set-azurermsqlserverthreatdetectionpolicy"></a><span data-ttu-id="2dd0c-171">Set-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="2dd0c-171">Set-AzureRmSqlServerThreatDetectionPolicy</span></span>
- <span data-ttu-id="2dd0c-172">De waarde `Usage_Anomaly` is niet meer geldig voor de parameter `ExcludedDetectionType`</span><span class="sxs-lookup"><span data-stu-id="2dd0c-172">The value `Usage_Anomaly` is no longer valid for the parameter `ExcludedDetectionType`</span></span>

## <a name="breaking-changes-to-storage-cmdlets"></a><span data-ttu-id="2dd0c-173">Belangrijke wijzigingen voor Storage-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-173">Breaking changes to Storage cmdlets</span></span>

<span data-ttu-id="2dd0c-174">De volgende eigenschappen van uitvoertypen worden beïnvloed door deze release:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-174">The following output type properties were affected this release:</span></span>

### <a name="azurestorageblobicloudblobserviceclient"></a><span data-ttu-id="2dd0c-175">AzureStorageBlob.ICloudBlob.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="2dd0c-175">AzureStorageBlob.ICloudBlob.ServiceClient</span></span>
- <span data-ttu-id="2dd0c-176">De volgende eigenschappen van dit type zijn verwijderd (_opmerking_: ze zijn nog wel aanwezig in de eigenschap `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="2dd0c-176">The following properties were removed from this type (_note_: they can still be found in `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `ServerTimeout`
    - `ParallelOperationThreadCount`
    - `SingleBlobUploadThresholdInBytes`
- <span data-ttu-id="2dd0c-177">Deze wijziging is van invloed op de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-177">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageBlob`
    - `Get-AzureStorageBlobContent`
    - `Get-AzureStorageBlobCopyState`
    - `Set-AzureStorageBlobContent`
    - `Start-AzureStorageBlobCopy`
    - `Stop-AzureStorageBlobCopy`
    
### <a name="azurestoragecontainercloudblobcontainerserviceclient"></a><span data-ttu-id="2dd0c-178">AzureStorageContainer.CloudBlobContainer.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="2dd0c-178">AzureStorageContainer.CloudBlobContainer.ServiceClient</span></span>
- <span data-ttu-id="2dd0c-179">De volgende eigenschappen van dit type zijn verwijderd (_opmerking_: ze zijn nog wel aanwezig in de eigenschap `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="2dd0c-179">The following properties were removed from this type (_note_: they can still be found in the `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `ServerTimeout`
    - `ParallelOperationThreadCount`
    - `SingleBlobUploadThresholdInBytes`
- <span data-ttu-id="2dd0c-180">Deze wijziging is van invloed op de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-180">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageContainer`
    - `New-AzureStorageContainer`
    - `Set-AzureStorageContainerAcl`
    
### <a name="azurestoragequeuecloudqueueserviceclient"></a><span data-ttu-id="2dd0c-181">AzureStorageQueue.CloudQueue.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="2dd0c-181">AzureStorageQueue.CloudQueue.ServiceClient</span></span>
- <span data-ttu-id="2dd0c-182">De volgende eigenschappen van dit type zijn verwijderd (_opmerking_: ze zijn nog wel aanwezig in de eigenschap `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="2dd0c-182">The following properties were removed from this type (_note_: they can still be found in the `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `RetryPolicy`
    - `ServerTimeout`
- <span data-ttu-id="2dd0c-183">Deze wijziging is van invloed op de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-183">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageQueue`
    - `New-AzureStorageQueue`
    
### <a name="azurestoragetablecloudtableserviceclient"></a><span data-ttu-id="2dd0c-184">AzureStorageTable.CloudTable.ServiceClient</span><span class="sxs-lookup"><span data-stu-id="2dd0c-184">AzureStorageTable.CloudTable.ServiceClient</span></span>
- <span data-ttu-id="2dd0c-185">De volgende eigenschappen van dit type zijn verwijderd (_opmerking_: ze zijn nog wel aanwezig in de eigenschap `DefaultRequestOptions`):</span><span class="sxs-lookup"><span data-stu-id="2dd0c-185">The following properties were removed from this type (_note_: they can still be found in the `DefaultRequestOptions` property):</span></span>
    - `LocationMode`
    - `MaximumExecutionTime`
    - `PayloadFormat`
    - `RetryPolicy`
    - `ServerTimeout`
- <span data-ttu-id="2dd0c-186">Deze wijziging is van invloed op de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="2dd0c-186">This change affects the following cmdlets:</span></span>
    - `Get-AzureStorageTable`
    - `New-AzureStorageTable`
    
```powershell
# Old
$LocationMode = (Get-AzureStorageBlob -Container $containername)[0].ICloudBlob.ServiceClient.LocationMode       
$ParallelOperationThreadCount = (Get-AzureStorageContainer -Container $containername).CloudBlobContainer.ServiceClient.ParallelOperationThreadCount
$PayloadFormat = (Get-AzureStorageTable -Name $tablename).CloudTable.ServiceClient.PayloadFormat
$RetryPolicy = (Get-AzureStorageQueue -Name $queuename).CloudQueue.ServiceClient.RetryPolicy

# New
$LocationMode = (Get-AzureStorageBlob -Container $containername)[0].ICloudBlob.ServiceClient.DefaultRequestOptions.LocationMode     
$ParallelOperationThreadCount = (Get-AzureStorageContainer -Container $containername).CloudBlobContainer.ServiceClient.DefaultRequestOptions.ParallelOperationThreadCount
$PayloadFormat = (Get-AzureStorageTable -Name $tablename).CloudTable.ServiceClient.DefaultRequestOptions.PayloadFormat
$RetryPolicy = (Get-AzureStorageQueue -Name $queuename).CloudQueue.ServiceClient.DefaultRequestOptions.RetryPolicy
```

## <a name="breaking-changes-to-profile-cmdlets"></a><span data-ttu-id="2dd0c-187">Belangrijke wijzigingen voor Profile-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2dd0c-187">Breaking Changes to Profile Cmdlets</span></span>

<span data-ttu-id="2dd0c-188">De volgende cmdlets en uitvoertypen voor cmdlet zijn gewijzigd in deze release.</span><span class="sxs-lookup"><span data-stu-id="2dd0c-188">The following cmdlets and cmdlet output types were changed in this release.</span></span>

### <a name="add-azurermaccount-breaking-changes"></a><span data-ttu-id="2dd0c-189">Belangrijke wijzigingen voor Add-AzureRmAccount</span><span class="sxs-lookup"><span data-stu-id="2dd0c-189">Add-AzureRmAccount breaking changes</span></span>

- <span data-ttu-id="2dd0c-190">De parameter ```EnvironmentName``` is verwijderd en vervangen door ```Environment```. De ```Environment``` accepteert nu een tekenreeks en geen ```AzureEnvironment```-object</span><span class="sxs-lookup"><span data-stu-id="2dd0c-190">```EnvironmentName``` parameter has been removed and replaced with ```Environment```, the ```Environment``` now takes a string and not an ```AzureEnvironment``` object</span></span>

```powershell
# Old
Add-AzureRmAccount -EnvironmentName AzureChinaCloud

# New
Add-AzureRmAccount -Environment AzureChinaCloud
```

### <a name="select-azurermprofile-was-renamed-to-import-azurermcontext"></a><span data-ttu-id="2dd0c-191">De naam van Select-AzureRmProfile is gewijzigd in Import-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="2dd0c-191">Select-AzureRmProfile was renamed to Import-AzureRmContext</span></span>

<span data-ttu-id="2dd0c-192">Naam van ```Select-AzureRmProfile``` gewijzigd in ```Import-AzureRmContext```</span><span class="sxs-lookup"><span data-stu-id="2dd0c-192">```Select-AzureRmProfile``` was renamed to ```Import-AzureRmContext```</span></span>

```powershell
# Old
Select-AzureRmProfile -Path c:\mydir\myprofile.json

# New
Import-AzureRmContext -Path c:\mydir\myprofile.json
```

### <a name="save-azurermprofile-was-renamed-to-save-azurermcontext"></a><span data-ttu-id="2dd0c-193">De naam van Save-AzureRmProfile is gewijzigd in Save-AzureRmContext</span><span class="sxs-lookup"><span data-stu-id="2dd0c-193">Save-AzureRmProfile was renamed to Save-AzureRmContext</span></span>

<span data-ttu-id="2dd0c-194">Naam van ```Save-AzureRmProfile``` gewijzigd in ```Save-AzureRmContext```</span><span class="sxs-lookup"><span data-stu-id="2dd0c-194">```Save-AzureRmProfile``` was renamed to ```Save-AzureRmContext```</span></span>

```powershell
# Old
Save-AzureRmProfile -Path c:\mydir\myprofile.json

# New
Save-AzureRmContext -Path c:\mydir\myprofile.json
```
### <a name="breaking-changes-to-output-psazurecontext-type"></a><span data-ttu-id="2dd0c-195">Belangrijke wijzigingen in het uitvoertype van PSAzureContext</span><span class="sxs-lookup"><span data-stu-id="2dd0c-195">Breaking Changes to output PSAzureContext Type</span></span>

- <span data-ttu-id="2dd0c-196">De eigenschap ```TokenCache``` is gewijzigd in een type dat ```IAzureTokenCache``` implementeert, in plaats van een ```byte[]```</span><span class="sxs-lookup"><span data-stu-id="2dd0c-196">The ```TokenCache``` property changed to a type that implements ```IAzureTokenCache``` instead of a ```byte[]```</span></span>

```powershell
# Old
$bytes = (Get-AzureRmContext).TokenCache
$bytes = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).TokenCache
$bytes = (Add-AzureRmAccount).Context.TokenCache

# New
$bytes = (Get-AzureRmContext).TokenCache.CacheData
$bytes = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).TokenCache.CacheData
$bytes = (Add-AzureRmAccount).Context.TokenCache.CacheData
```

### <a name="breaking-changes-to-the-output-psazureaccount-type"></a><span data-ttu-id="2dd0c-197">Belangrijke wijzigingen in het uitvoertype van PSAzureAccount</span><span class="sxs-lookup"><span data-stu-id="2dd0c-197">Breaking Changes to the output PSAzureAccount Type</span></span>

- <span data-ttu-id="2dd0c-198">De eigenschap ```AccountType``` is gewijzigd in ```Type```</span><span class="sxs-lookup"><span data-stu-id="2dd0c-198">The ```AccountType``` property was changed to ```Type```</span></span>

```powershell
# Old
$type = (Get-AzureRmContext).Account.AccountType
$type = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).Account.AccountType
$type = (Add-AzureRmAccount).Context.Account.AccountType

# New 
$type = (Get-AzureRmContext).Account.Type
$type = (Set-AzureRmContext -SubscriptionId xxx-xxx-xxx-xxx).Account.Type
$type = (Add-AzureRmAccount).Context.Account.Type
```

### <a name="breaking-changes-to-the-output-psazuresubscription-type"></a><span data-ttu-id="2dd0c-199">Belangrijke wijzigingen in het uitvoertype van PSAzureSubscription</span><span class="sxs-lookup"><span data-stu-id="2dd0c-199">Breaking Changes to the output PSAzureSubscription Type</span></span>
- <span data-ttu-id="2dd0c-200">De eigenschap ```SubscriptionId``` is gewijzigd in ```Id```</span><span class="sxs-lookup"><span data-stu-id="2dd0c-200">The ```SubscriptionId``` property was changed to ```Id```</span></span>

```powershell
# Old
$id =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).SubscriptionId
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.SubscriptionId
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionId
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionId

# New
$id =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).Id
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.Id
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Id
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Id
```

- <span data-ttu-id="2dd0c-201">De eigenschap ```SubscriptionName``` is gewijzigd in ```Name```</span><span class="sxs-lookup"><span data-stu-id="2dd0c-201">The ```SubscriptionName``` property was changed to ```Name```</span></span>

```powershell
# Old
$name =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).SubscriptionName
$name =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.SubscriptionName
$name =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionName
$name =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.SubscriptionName

# New
$name =(Get-AzureRmSubscription -SubscriptionId xxxx-xxxx-xxxx-xxxx).Name
$name =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Subscription.Name
$name =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Name
$name =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Subscription.Name
```

### <a name="breaking-changes-to-the-output-psazuretenant-type"></a><span data-ttu-id="2dd0c-202">Belangrijke wijzigingen in het uitvoertype van PSAzureTenant</span><span class="sxs-lookup"><span data-stu-id="2dd0c-202">Breaking Changes to the output PSAzureTenant Type</span></span>

- <span data-ttu-id="2dd0c-203">De eigenschap ```TenantId``` is gewijzigd in ```Id```</span><span class="sxs-lookup"><span data-stu-id="2dd0c-203">The ```TenantId``` property was changed to ```Id```</span></span>

```powershell
# Old
$id =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).TenantId
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Tenant.TenantId
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.TenantId
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.TenantId

# New
$id =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Id
$id =(Add-AzureRmAccount -SubscriptionId xxxx-xxxx-xxxx-xxxx).Context.Tenant.Id
$id =(Get-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.Id
$id =(Set-AzureRmContext -SubscriptionId xxxx-xxxx-xxxx-xxxx).Tenant.Id
```

- <span data-ttu-id="2dd0c-204">De eigenschap ```Domain``` is gewijzigd in ```Directory```</span><span class="sxs-lookup"><span data-stu-id="2dd0c-204">The ```Domain``` property was changed to ```Directory```</span></span>

```powershell
# Old
$tenantName =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Domain

# New
$tenantName =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Directory
```
