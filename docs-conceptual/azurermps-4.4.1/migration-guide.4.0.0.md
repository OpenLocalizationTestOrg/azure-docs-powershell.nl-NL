# <a name="breaking-changes-for-microsoft-azure-powershell-400"></a>Belangrijke wijzigingen voor Microsoft Azure PowerShell 4.0.0

Dit document dient niet alleen als melding van een belangrijke wijziging, maar ook als migratiehandleiding voor gebruikers van de Microsoft Azure PowerShell-cmdlets. Elke sectie beschrijft zowel de reden voor de belangrijke wijziging als het eenvoudigste migratiepad. Raadpleeg voor een uitgebreidere context de pull-aanvraag die bij elke wijziging hoort.

## <a name="table-of-contents"></a>Inhoudsopgave

- [Belangrijke wijzigingen voor Compute-cmdlets](#breaking-changes-to-compute-cmdlets)
- [Belangrijke wijzigingen voor EventHub-cmdlets](#breaking-changes-to-eventhub-cmdlets)
- [Belangrijke wijzigingen voor Insights-cmdlets](#breaking-changes-to-insights-cmdlets)
- [Belangrijke wijzigingen voor Network-cmdlets](#breaking-changes-to-network-cmdlets)
- [Belangrijke wijzigingen voor ServiceBus-cmdlets](#breaking-changes-to-servicebus-cmdlets)
- [Belangrijke wijzigingen voor SQL-cmdlets](#breaking-changes-to-sql-cmdlets)
- [Belangrijke wijzigingen voor Storage-cmdlets](#breaking-changes-to-storage-cmdlets)
- [Belangrijke wijzigingen voor Profile-cmdlets](#breaking-changes-to-profile-cmdlets)
## <a name="breaking-changes-to-compute-cmdlets"></a>Belangrijke wijzigingen voor Compute-cmdlets

De volgende uitvoertypen worden beïnvloed door deze release:

### <a name="psvirtualmachine"></a>PSVirtualMachine
- De eigenschappen van `DataDiskNames` en `NetworkInterfaceIDs` op het hoogste niveau van het `PSVirtualMachine`-object zijn verwijderd uit het uitvoertype. Deze eigenschappen zijn altijd al beschikbaar geweest in de eigenschappen `StorageProfile` en `NetworkProfile` van het `PSVirtualMachine`-object. Dit is voortaan dan ook de manier om deze aan te spreken.
- Deze wijziging is van invloed op de volgende cmdlets:
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

## <a name="breaking-changes-to-eventhub-cmdlets"></a>Belangrijke wijzigingen voor EventHub-cmdlets

De volgende cmdlets worden beïnvloed door deze release:

### <a name="get-azurermeventhubnamespace"></a>Get-AzureRmEventHubNamespace
- De eigenschap `ResourceGroupName` is verwijderd uit het uitvoertype `NamespaceAttributes`

### <a name="new-azurermeventhubnamespace"></a>New-AzureRmEventHubNamespace
- De eigenschap `ResourceGroupName` is verwijderd uit het uitvoertype `NamespaceAttributes`

## <a name="breaking-changes-to-insights-cmdlets"></a>Belangrijke wijzigingen voor Insights-cmdlets

De volgende cmdlets worden beïnvloed door deze release:
    
### <a name="get-azurermusage"></a>Get-AzureRmUsage
- Deze cmdlet is afgeschaft.

### <a name="remove-azurermalertrule"></a>Remove-AzureRmAlertRule
- De uitvoer van deze cmdlet is gewijzigd van een lijst met een enkel object in een enkel object. Dit object bevat de requestId en een statuscode.
    
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
    
### <a name="add-azurermlogalertrule"></a>Add-AzureRmLogAlertRule
- Deze cmdlet is afgeschaft.
    
### <a name="get-azurermalertrule"></a>Get-AzureRmAlertRule
- Elk element van de uitvoer (een lijst met objecten) van deze cmdlet is afgevlakt. Dit houdt in dat er geen objecten meer worden geretourneerd met de structuur `{ Id, Location, Name, Tags, Properties }`, maar met de structuur `{ Id, Location, Name, Tags, Type, Description, IsEnabled, Condition, Actions, LastUpdatedTime, ...}`. Deze bestaat uit alle kenmerken van een Azure-resource plus alle kenmerken van een AlertRuleResource op het hoogste niveau.
    
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
    
### <a name="get-azurermautoscalesetting"></a>Get-AzureRmAutoscaleSetting
- Het veld `AutoscaleSettingResourceName` is afgeschaft, omdat dit altijd dezelfde waarde heeft als het veld `Name`.

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
    
### <a name="remove-azurermlogprofile"></a>Remove-AzureRmLogProfile
- De uitvoer van deze cmdlet is gewijzigd van `Boolean` in een object dat `RequestId` en `StatusCode` bevat.

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
    
### <a name="add-azurermlogprofile"></a>Add-AzureRmLogProfile
- De uitvoer van deze cmdlet is gewijzigd van een object dat de requestId, de statuscode en de bijgewerkte of de zojuist gemaakte resource bevat
    
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
    
### <a name="set-azurermdiagnosticsettings"></a>Set-AzureRmDiagnosticSettings
- De naam van deze opdracht wordt gewijzigd in `Update-AzureRmDiagnsoticSettings`.

```powershell
# Old
Set-AzureRmDiagnosticSettings

# New
Update-AzureRmDiagnosticSettings
```

## <a name="breaking-changes-to-network-cmdlets"></a>Belangrijke wijzigingen voor Network-cmdlets

De volgende cmdlets worden beïnvloed door deze release:

### <a name="new-azurermvirtualnetworkgatewayconnection"></a>New-AzureRmVirtualNetworkGatewayConnection
- De parameter `EnableBgp` is gewijzigd om een `boolean` te accepteren in plaats van een `string`.

```powershell
# Old
New-AzureRmVirtualNetworkGatewayConnection -ResourceGroupName "RG" -name "conn1" -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localnetGateway -ConnectionType IPsec -SharedKey "key" -EnableBgp "true"

# New
New-AzureRmVirtualNetworkGatewayConnection -ResourceGroupName "RG" -name "conn1" -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localnetGateway -ConnectionType IPsec -SharedKey "key" -EnableBgp $true
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a>Belangrijke wijzigingen voor ServiceBus-cmdlets

De volgende cmdlets worden beïnvloed door deze release:

### <a name="get-azurermservicebusnamespace"></a>Get-AzureRmServiceBusNamespace
- De eigenschap `ResourceGroupName` is verwijderd uit het uitvoertype `NamespaceAttributes`

### <a name="new-azurermservicebusnamespace"></a>New-AzureRmServiceBusNamespace

- De eigenschap `ResourceGroupName` is verwijderd uit het uitvoertype `NamespaceAttributes`

## <a name="breaking-changes-to-sql-cmdlets"></a>Belangrijke wijzigingen voor SQL-cmdlets

De volgende cmdlets worden beïnvloed door deze release:

### <a name="new-azurermsqldatabasefailovergroup"></a>New-AzureRmSqlDatabaseFailoverGroup
- De parameter `Tag` is verwijderd
- De naam van de parameter `GracePeriodWithDataLossHour` is gewijzigd in `GracePeriodWithDataLossHours`

```powershell
# Old
New-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -FailoverPolicy Automatic -GracePeriodWithDataLossHour 1 -Tag @{ Environment="Test" }

# New
New-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -FailoverPolicy Automatic -GracePeriodWithDataLossHours 1
```

### <a name="set-azurermsqldatabasefailovergroup"></a>Set-AzureRmSqlDatabaseFailoverGroup
- De parameter `Tag` is verwijderd
- De naam van de parameter `GracePeriodWithDataLossHour` is gewijzigd in `GracePeriodWithDataLossHours`

```powershell
# Old
Set-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -FailoverPolicy Automatic -GracePeriodWithDataLossHour 1 -Tag @{ Environment="Test" }

# New
Set-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -FailoverPolicy Automatic -GracePeriodWithDataLossHours 1
```

### <a name="add-azurermsqldatabasetofailovergroup"></a>Add-AzureRmSqlDatabaseToFailoverGroup
- De parameter `Tag` is verwijderd

```powershell
# Old
Add-AzureRmSqlDatabaseToFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1 -Tag @{ Environment="Test" }

# New
Add-AzureRmSqlDatabaseToFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1
```

###  <a name="remove-azurermsqldatabasefromfailovergroup"></a>Remove-AzureRmSqlDatabaseFromFailoverGroup
- De parameter `Tag` is verwijderd

```powershell
# Old
Remove-AzureRmSqlDatabaseFromFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1 -Tag @{ Environment="Test" }

# New
Remove-AzureRmSqlDatabaseFromFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -Database $db1
```

### <a name="remove-azurermsqldatabasefailovergroup"></a>Remove-AzureRmSqlDatabaseFailoverGroup
- De parameter `PartnerResourceGroupName` is verwijderd
- De parameter `PartnerServerName` is verwijderd

```powershell
# Old
Remove-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg -PartnerServerName server2 -PartnerResourceGroupName rg

# New
Remove-AzureRmSqlDatabaseFailoverGroup -ResourceGroupName rg -ServerName server1 -FailoverGroupName fg
```

### <a name="set-azurermsqldatabasethreatdetectionpolicy"></a>Set-AzureRmSqlDatabaseThreatDetectionPolicy
- De waarde `Usage_Anomaly` is niet meer geldig voor de parameter `ExcludedDetectionType`

### <a name="set-azurermsqlserverthreatdetectionpolicy"></a>Set-AzureRmSqlServerThreatDetectionPolicy
- De waarde `Usage_Anomaly` is niet meer geldig voor de parameter `ExcludedDetectionType`

## <a name="breaking-changes-to-storage-cmdlets"></a>Belangrijke wijzigingen voor Storage-cmdlets

De volgende eigenschappen van uitvoertypen worden beïnvloed door deze release:

### <a name="azurestorageblobicloudblobserviceclient"></a>AzureStorageBlob.ICloudBlob.ServiceClient
- De volgende eigenschappen van dit type zijn verwijderd (_opmerking_: ze zijn nog wel aanwezig in de eigenschap `DefaultRequestOptions`):
    - `LocationMode`
    - `MaximumExecutionTime`
    - `ServerTimeout`
    - `ParallelOperationThreadCount`
    - `SingleBlobUploadThresholdInBytes`
- Deze wijziging is van invloed op de volgende cmdlets:
    - `Get-AzureStorageBlob`
    - `Get-AzureStorageBlobContent`
    - `Get-AzureStorageBlobCopyState`
    - `Set-AzureStorageBlobContent`
    - `Start-AzureStorageBlobCopy`
    - `Stop-AzureStorageBlobCopy`
    
### <a name="azurestoragecontainercloudblobcontainerserviceclient"></a>AzureStorageContainer.CloudBlobContainer.ServiceClient
- De volgende eigenschappen van dit type zijn verwijderd (_opmerking_: ze zijn nog wel aanwezig in de eigenschap `DefaultRequestOptions`):
    - `LocationMode`
    - `MaximumExecutionTime`
    - `ServerTimeout`
    - `ParallelOperationThreadCount`
    - `SingleBlobUploadThresholdInBytes`
- Deze wijziging is van invloed op de volgende cmdlets:
    - `Get-AzureStorageContainer`
    - `New-AzureStorageContainer`
    - `Set-AzureStorageContainerAcl`
    
### <a name="azurestoragequeuecloudqueueserviceclient"></a>AzureStorageQueue.CloudQueue.ServiceClient
- De volgende eigenschappen van dit type zijn verwijderd (_opmerking_: ze zijn nog wel aanwezig in de eigenschap `DefaultRequestOptions`):
    - `LocationMode`
    - `MaximumExecutionTime`
    - `RetryPolicy`
    - `ServerTimeout`
- Deze wijziging is van invloed op de volgende cmdlets:
    - `Get-AzureStorageQueue`
    - `New-AzureStorageQueue`
    
### <a name="azurestoragetablecloudtableserviceclient"></a>AzureStorageTable.CloudTable.ServiceClient
- De volgende eigenschappen van dit type zijn verwijderd (_opmerking_: ze zijn nog wel aanwezig in de eigenschap `DefaultRequestOptions`):
    - `LocationMode`
    - `MaximumExecutionTime`
    - `PayloadFormat`
    - `RetryPolicy`
    - `ServerTimeout`
- Deze wijziging is van invloed op de volgende cmdlets:
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

## <a name="breaking-changes-to-profile-cmdlets"></a>Belangrijke wijzigingen voor Profile-cmdlets

De volgende cmdlets en uitvoertypen voor cmdlet zijn gewijzigd in deze release.

### <a name="add-azurermaccount-breaking-changes"></a>Belangrijke wijzigingen voor Add-AzureRmAccount

- De parameter ```EnvironmentName``` is verwijderd en vervangen door ```Environment```. De ```Environment``` accepteert nu een tekenreeks en geen ```AzureEnvironment```-object

```powershell
# Old
Add-AzureRmAccount -EnvironmentName AzureChinaCloud

# New
Add-AzureRmAccount -Environment AzureChinaCloud
```

### <a name="select-azurermprofile-was-renamed-to-import-azurermcontext"></a>De naam van Select-AzureRmProfile is gewijzigd in Import-AzureRmContext

Naam van ```Select-AzureRmProfile``` gewijzigd in ```Import-AzureRmContext```

```powershell
# Old
Select-AzureRmProfile -Path c:\mydir\myprofile.json

# New
Import-AzureRmContext -Path c:\mydir\myprofile.json
```

### <a name="save-azurermprofile-was-renamed-to-save-azurermcontext"></a>De naam van Save-AzureRmProfile is gewijzigd in Save-AzureRmContext

Naam van ```Save-AzureRmProfile``` gewijzigd in ```Save-AzureRmContext```

```powershell
# Old
Save-AzureRmProfile -Path c:\mydir\myprofile.json

# New
Save-AzureRmContext -Path c:\mydir\myprofile.json
```
### <a name="breaking-changes-to-output-psazurecontext-type"></a>Belangrijke wijzigingen in het uitvoertype van PSAzureContext

- De eigenschap ```TokenCache``` is gewijzigd in een type dat ```IAzureTokenCache``` implementeert, in plaats van een ```byte[]```

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

### <a name="breaking-changes-to-the-output-psazureaccount-type"></a>Belangrijke wijzigingen in het uitvoertype van PSAzureAccount

- De eigenschap ```AccountType``` is gewijzigd in ```Type```

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

### <a name="breaking-changes-to-the-output-psazuresubscription-type"></a>Belangrijke wijzigingen in het uitvoertype van PSAzureSubscription
- De eigenschap ```SubscriptionId``` is gewijzigd in ```Id```

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

- De eigenschap ```SubscriptionName``` is gewijzigd in ```Name```

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

### <a name="breaking-changes-to-the-output-psazuretenant-type"></a>Belangrijke wijzigingen in het uitvoertype van PSAzureTenant

- De eigenschap ```TenantId``` is gewijzigd in ```Id```

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

- De eigenschap ```Domain``` is gewijzigd in ```Directory```

```powershell
# Old
$tenantName =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Domain

# New
$tenantName =(Get-AzureRmTenant -TenantId xxxx-xxxx-xxxx-xxxx).Directory
```
