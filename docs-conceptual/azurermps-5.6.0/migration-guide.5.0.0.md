# <a name="breaking-changes-for-microsoft-azure-powershell-500"></a>Belangrijke wijzigingen voor Microsoft Azure PowerShell 5.0.0

Dit document dient niet alleen als melding van een belangrijke wijziging, maar ook als migratiehandleiding voor gebruikers van de Microsoft Azure PowerShell-cmdlets. Elke sectie beschrijft zowel de reden voor de belangrijke wijziging als het eenvoudigste migratiepad. Raadpleeg voor een uitgebreidere context de pull-aanvraag die bij elke wijziging hoort.

## <a name="table-of-contents"></a>Inhoudsopgave

- [Belangrijke wijzigingen voor ApiManagement-cmdlets](#breaking-changes-to-apimanagement-cmdlets)
- [Belangrijke wijzigingen voor Batch-cmdlets](#breaking-changes-to-batch-cmdlets)
- [Belangrijke wijzigingen voor Compute-cmdlets](#breaking-changes-to-compute-cmdlets)
- [Belangrijke wijzigingen voor EventHub-cmdlets](#breaking-changes-to-eventhub-cmdlets)
- [Belangrijke wijzigingen voor Insights-cmdlets](#breaking-changes-to-insights-cmdlets)
- [Belangrijke wijzigingen voor Network-cmdlets](#breaking-changes-to-network-cmdlets)
- [Belangrijke wijzigingen voor Resources-cmdlets](#breaking-changes-to-resources-cmdlets)
- [Belangrijke wijzigingen voor ServiceBus-cmdlets](#breaking-changes-to-servicebus-cmdlets)

## <a name="breaking-changes-to-apimanagement-cmdlets"></a>Belangrijke wijzigingen voor ApiManagement-cmdlets

### <a name="new-azurermapimanagementbackendproxy"></a>**New-AzureRmApiManagementBackendProxy**
- De parameters UserName en Password worden vervangen door een PSCredential

```powershell
# Old
New-AzureRmApiManagementBackendProxy [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
New-AzureRmApiManagementBackendProxy [other required parameters] -Credential $PSCredentialVariable
```

### <a name="new-azurermapimanagementuser"></a>**New-AzureRmApiManagementUser**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
New-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapimanagementuser"></a>**Set-AzureRmApiManagementUser**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
Set-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-batch-cmdlets"></a>Belangrijke wijzigingen voor Batch-cmdlets

### <a name="new-azurebatchcertificate"></a>**New-AzureBatchCertificate**
- De parameter `Password` wordt vervangen door een SecureString

```powershell
# Old
New-AzureBatchCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureBatchCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchcomputenodeuser"></a>**New-AzureBatchComputeNodeUser**
- De parameter `Password` wordt vervangen door een SecureString

```powershell
# Old
New-AzureBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
New-AzureBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermbatchcomputenodeuser"></a>**Set-AzureRmBatchComputeNodeUser**
- De parameter `Password` wordt vervangen door een SecureString

```powershell
# Old
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchtask"></a>**New-AzureBatchTask**
 - De switch `RunElevated` is verwijderd en vervangen door `UserIdentity`.

```powershell
# Old
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -RunElevated $TRUE

# New
$autoUser = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoUserSpecification -ArgumentList @("Task", "Admin")
$userIdentity = New-Object Microsoft.Azure.Commands.Batch.Models.PSUserIdentity $autoUser
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -UserIdentity $userIdentity
```

Dit is ook van invloed op de eigenschap `RunElevated` voor `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` en `PSJobReleaseTask`.

### <a name="psmultiinstancesettings"></a>**PSMultiInstanceSettings**

- De constructor `PSMultiInstanceSettings` verwacht niet langer een vereiste parameter `numberOfInstances`, maar verwacht nu een vereiste parameter `coordinationCommandLine`.

```powershell
# Old
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @(2)
$settings.CoordinationCommandLine = "cmd /c echo hello"
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings

# New
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @("cmd /c echo hello", 2)
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings
```

### <a name="get-azurebatchtask"></a>**Get-AzureBatchTask**
 - De eigenschap `RunElevated` voor `PSCloudTask` is verwijderd. De eigenschap `UserIdentity` is toegevoegd ter vervanging van `RunElevated`.

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.RunElevated

# New
$task = Get-AzureBatchTask [parameters]
$task.UserIdentity.AutoUser.ElevationLevel
```

Dit is ook van invloed op de eigenschap `RunElevated` voor `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` en `PSJobReleaseTask`.

### <a name="multiple-types"></a>**Meerdere typen**

- De naam van de eigenschap `SchedulingError` is voor `PSExitConditions` gewijzigd in `PreProcessingError`.

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.PreProcessingError
```

### <a name="multiple-types"></a>**Meerdere typen**

- De naam van de eigenschap `SchedulingError` is voor `PSJobPreparationTaskExecutionInformation`, `PSJobReleaseTaskExecutionInformation`, `PSStartTaskInformation`, `PSSubtaskInformation` en `PSTaskExecutionInformation` gewijzigd in `FailureInformation`.
  - Telkens wanneer een taak mislukt, wordt `FailureInformation` geretourneerd. Dit omvat alle voorgaande gevallen van planningsfouten, 'nonzero'-taakafsluitcodes en fouten bij het uploaden van bestanden door de nieuwe functie voor uitvoerbestanden.
  - Dit is op dezelfde manier gestructureerd als voorheen, dus er zijn geen codewijzigingen nodig voor het gebruik van dit type.

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.FailureInformation
```

Deze wijziging heeft ook invloed op: Get-AzureBatchPool, Get-AzureBatchSubtask en Get-AzureBatchJobPreparationAndReleaseTaskStatus

### <a name="new-azurebatchpool"></a>**New-AzureBatchPool**
 - `TargetDedicated` is verwijderd en vervangen door `TargetDedicatedComputeNodes` en `TargetLowPriorityComputeNodes`.
 - `TargetDedicatedComputeNodes` heeft de alias `TargetDedicated`.

```powershell
# Old
New-AzureBatchPool [other parameters] [-TargetDedicated <Int32>]

# New
New-AzureBatchPool [other parameters] [-TargetDedicatedComputeNodes <Int32>] [-TargetLowPriorityComputeNodes <Int32>]
```

Dit is ook van invloed op: Start-AzureBatchPoolResize

### <a name="get-azurebatchpool"></a>**Get-AzureBatchPool**
 - De namen van de eigenschappen `TargetDedicated` en `CurrentDedicated` zijn voor `PSCloudPool` gewijzigd in `TargetDedicatedComputeNodes` en `CurrentDedicatedComputeNodes`.

```powershell
# Old
$pool = Get-AzureBatchPool [parameters]
$pool.TargetDedicated
$pool.CurrentDedicated

# New
$pool = Get-AzureBatchPool [parameters]
$pool.TargetDedicatedComputeNodes
$pool.CurrentDedicatedComputeNodes
```

### <a name="type-pscloudpool"></a>**Type PSCloudPool**

- De naam van `ResizeError` is voor `PSCloudPool` gewijzigd in `ResizeErrors` en dit is nu een verzameling.

```powershell
# Old
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeError

# New
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeErrors[0]
```

### <a name="new-azurebatchjob"></a>**New-AzureBatchJob**
- De naam van de eigenschap `TargetDedicated` is voor `PSPoolSpecification` gewijzigd in `TargetDedicatedComputeNodes`.

```powershell
# Old
$poolInfo = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolInformation
$poolInfo.AutoPoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification.TargetDedicated = 5
New-AzureBatchJob [other parameters] -PoolInformation $poolInfo

# New
$poolInfo = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolInformation
$poolInfo.AutoPoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification = New-Object Microsoft.Azure.Commands.Batch.Models.PSPoolSpecification
$poolInfo.AutoPoolSpecification.PoolSpecification.TargetDedicatedComputeNodes = 5
New-AzureBatchJob [other parameters] -PoolInformation $poolInfo
```

### <a name="get-azurebatchnodefile"></a>**Get-AzureBatchNodeFile**
 - `Name` is verwijderd en vervangen door `Path`.
 - `Path` heeft de alias `Name`.

```powershell
# Old
Get-AzureBatchNodeFile [other parameters] [[-Name] <String>]

# New
Get-AzureBatchNodeFile [other parameters] [[-Path] <String>]
```

Dit is ook van invloed op: Get-AzureBatchNodeFileContent, Remove-AzureBatchNodeFile

### <a name="type-psnodefile"></a>Type **PSNodeFile**

 - De naam van de eigenschap `Name` is voor `PSNodeFile` gewijzigd in `Path`.

```powershell
# Old
$file = Get-AzureBatchNodeFile [parameters]
$file.Name

# New
$file = Get-AzureBatchNodeFile [parameters]
$file.Path
```

### <a name="get-azurebatchsubtask"></a>**Get-AzureBatchSubtask**
- De eigenschappen `PreviousState` en `State` zijn voor `PSSubtaskInformation` niet langer van het type `TaskState`, maar zijn nu van het type `SubtaskState`.
  - In tegenstelling tot `TaskState` heeft `SubtaskState` geen `Active`-waarde, omdat het niet mogelijk is dat subtaken zich in een `Active`-status bevinden.

```powershell
# Old
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.TaskState.Running) { }

# New
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.SubtaskState.Running) { }
```

## <a name="breaking-changes-to-compute-cmdlets"></a>Belangrijke wijzigingen voor Compute-cmdlets

### <a name="set-azurermvmaccessextension"></a>**Set-AzureRmVMAccessExtension**
- De parameters UserName en Password worden vervangen door een PSCredential

```powershell
# Old
Set-AzureRmVMAccessExtension [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
Set-AzureRmVMAccessExtension [other required parameters] -Credential $PSCredential
```

## <a name="breaking-changes-to-eventhub-cmdlets"></a>Belangrijke wijzigingen voor EventHub-cmdlets

### <a name="new-azurermeventhubnamespaceauthorizationrule"></a>**New-AzureRmEventHubNamespaceAuthorizationRule**
- De cmdlet New-AzureRmEventHubNamespaceAuthorizationRule is verwijderd. Gebruik de cmdlet New-AzureRmEventHubAuthorizationRule
    
### <a name="get-azurermeventhubnamespaceauthorizationrule"></a>**Get-AzureRmEventHubNamespaceAuthorizationRule**
- De cmdlet Get-AzureRmEventHubNamespaceAuthorizationRule is verwijderd. Gebruik de cmdlet Get-AzureRmEventHubAuthorizationRule
    
### <a name="set-azurermeventhubnamespaceauthorizationrule"></a>**Set-AzureRmEventHubNamespaceAuthorizationRule**
- De cmdlet Set-AzureRmEventHubNamespaceAuthorizationRule is verwijderd. Gebruik de cmdlet Set-AzureRmEventHubAuthorizationRule
    
### <a name="remove-azurermeventhubnamespaceauthorizationrule"></a>**Remove-AzureRmEventHubNamespaceAuthorizationRule**
- De cmdlet Remove-AzureRmEventHubNamespaceAuthorizationRule is verwijderd. Gebruik de cmdlet Remove-AzureRmEventHubAuthorizationRule
    
### <a name="new-azurermeventhubnamespacekey"></a>**New-AzureRmEventHubNamespaceKey**
- De cmdlet New-AzureRmEventHubNamespaceKey is verwijderd. Gebruik de cmdlet New-AzureRmEventHubKey
    
### <a name="get-azurermeventhubnamespacekey"></a>**Get-AzureRmEventHubNamespaceKey**
- De cmdlet Get-AzureRmEventHubNamespaceKey is verwijderd. Gebruik de cmdlet Get-AzureRmEventHubKey
    
### <a name="new-azurermeventhubnamespace"></a>**New-AzureRmEventHubNamespace**
- De eigenschappen Status en Enabled worden verwijderd voor NamespceAttributes. 

```powershell
# Old
# The $namespace has Status and Enabled property  
$namespace = New-AzureRmEventHubNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Status and Enabled property    
$namespace = Get-AzureRmEventHubNamespace <parameters>
```
    
### <a name="get-azurermeventhubnamespace"></a>**Get-AzureRmEventHubNamespace**
- De eigenschappen Status en Enabled worden verwijderd voor NamespceAttributes. 

```powershell
# Old
# The $namespace has Status and Enabled property 
$namespace = Get-AzureRmEventHubNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Status and Enabled property    
$namespace = Get-AzureRmEventHubNamespace <parameters>
```
    
### <a name="set-azurermeventhubnamespace"></a>**Set-AzureRmEventHubNamespace**
- De eigenschappen Status en Enabled worden verwijderd voor NamespceAttributes. 

```powershell
# Old
# The $namespace has Status and Enabled property 
$namespace = Set-AzureRmEventHubNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Status and Enabled property    
$namespace = Set-AzureRmEventHubNamespace <parameters>
``` 
  
### <a name="new-azurermeventhubconsumergroup"></a>**New-AzureRmEventHubConsumerGroup**
- De eigenschap EventHubPath wordt verwijderd voor ConsumerGroupAttributes.

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="set-azurermeventhubconsumergroup"></a>**Set-AzureRmEventHubConsumerGroup**
- De eigenschap EventHubPath wordt verwijderd voor ConsumerGroupAttributes.

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="get-azurermeventhubconsumergroup"></a>**Get-AzureRmEventHubConsumerGroup**
- De eigenschap EventHubPath wordt verwijderd voor ConsumerGroupAttributes.

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
```

## <a name="breaking-changes-to-insights-cmdlets"></a>Belangrijke wijzigingen voor Insights-cmdlets

### <a name="add-azurermlogalertrule"></a>**Add-AzureRMLogAlertRule**
- De cmdlet **Add-AzureRMLogAlertRule** is afgeschaft.
- Na 1 oktober zal het gebruik van deze cmdlet niet langer effect hebben, omdat deze functionaliteit wordt overgedragen naar Waarschuwingen voor activiteitenlogboeken. Zie https://aka.ms/migratemealerts voor meer informatie.

### <a name="get-azurermusage"></a>**Get-AzureRMUsage**
- De cmdlet **Get-AzureRMUsage** is afgeschaft.

### <a name="get-azurermalerthistory--get-azurermautoscalehistory--get-azurermlogs"></a>**Get-AzureRmAlertHistory** / **Get-AzureRmAutoscaleHistory** / **Get-AzureRmLogs**
- Uitvoerwijziging: het veld EventChannels van het EventData-object (geretourneerd door deze cmdlets) wordt afgeschaft omdat dit nu een constante waarde retourneert (Admin,Operation.)

### <a name="get-azurermalertrule"></a>**Get-AzureRmAlertRule**
- Uitvoerwijziging: de uitvoer van deze cmdlet wordt afgevlakt (dat wil zeggen: het eigenschappenveld wordt verwijderd) om zo de gebruikerservaring te verbeteren.

```powershell
# Old
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -Foreground Red "Error updating alert rule"
    Write-Host $rules[0].Id
    Write-Host $rules[0].Properties.IsEnabled
    Write-Host $rules[0].Properties.Condition
}

# New
$rules = Get-AzureRmAlertRule -ResourceGroup $resourceGroup
if ($rules -and $rules.count -ge 1)
{
    Write-Host -Foreground red "Error updating alert rule"
    Write-Host $rules[0].Id

    # Properties will remain for a while
    Write-Host $rules[0].Properties.IsEnabled
      
    # But the properties will be at the top level too. Later Properties will be removed
    Write-Host $rules[0].IsEnabled
    Write-Host $rules[0].Condition
}
```

### <a name="get-azurermautoscalesetting"></a>**Get-AzureRmAutoscaleSetting**
- Uitvoerwijziging: het veld AutoscaleSettingResourceName wordt afgeschaft omdat dit altijd gelijk is aan het veld Name.

```powershell
# Old
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
if ($s1.AutoscaleSettingResourceName -ne $s1.Name)
{
    Write-Host "There is something wrong with the name"
}

# New
$s1 = Get-AzureRmAutoscaleSetting -ResourceGroup $resourceGroup -Name MySetting
    
# there won't be a AutoscaleSettingResourceName
Write-Host $s1.Name    
```

### <a name="remove-azurermalertrule--remove-azurermlogprofile"></a>**Remove-AzureRmAlertRule** / **Remove-AzureRmLogProfile**
- Uitvoerwijziging: het type uitvoer wordt gewijzigd, zodat er een enkel object wordt geretourneerd met de aanvraag-id en de statuscode.

```powershell
# Old
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name $ruleName
if ($s1 -ne $null)
{
    $r = $s1[0].RequestId
    $s = $s1[0].StatusCode
}

# New
$s1 = Remove-AzureRmAlertRule -ResourceGroup $resourceGroup -name $ruleName
$r = $s1.RequestId
$s = $s1.StatusCode
```

## <a name="breaking-changes-to-network-cmdlets"></a>Belangrijke wijzigingen voor Network-cmdlets

### <a name="add-azurermapplicationgatewaysslcertificate"></a>**Add-AzureRmApplicationGatewaySslCertificate**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermapplicationgatewaysslcertificate"></a>**New-AzureRmApplicationGatewaySslCertificate**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapplicationgatewaysslcertificate"></a>**Set-AzureRmApplicationGatewaySslCertificate**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-resources-cmdlets"></a>Belangrijke wijzigingen voor Resources-cmdlets

### <a name="new-azurermadappcredential"></a>**New-AzureRmADAppCredential**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
New-AzureRmADAppCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADAppCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadapplication"></a>**New-AzureRmADApplication**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
New-AzureRmADApplication [other required parameters] -Password "plain-text string"

# New
New-AzureRmADApplication [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadserviceprincipal"></a>**New-AzureRmADServicePrincipal**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
New-AzureRmADServicePrincipal [other required parameters] -Password "plain-text string"

# New
New-AzureRmADServicePrincipal [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadspcredential"></a>**New-AzureRmADSpCredential**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
New-AzureRmADSpCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADSpCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermaduser"></a>**New-AzureRmADUser**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
New-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermaduser"></a>**Set-AzureRmADUser**
- De parameter Password wordt vervangen door een SecureString

```powershell
# Old
Set-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a>Belangrijke wijzigingen voor ServiceBus-cmdlets

### <a name="get-azurermservicebustopicauthorizationrule"></a>**Get-AzureRmServiceBusTopicAuthorizationRule**
- De cmdlet Get-AzureRmServiceBusTopicAuthorizationRule is verwijderd. Gebruik de cmdlet Get-AzureRmServiceBusAuthorizationRule    

### <a name="get-azurermservicebustopickey"></a>**Get-AzureRmServiceBusTopicKey**
- De cmdlet Get-AzureRmServiceBusTopicKey is verwijderd. Gebruik de cmdlet Get-AzureRmServiceBusKey.

### <a name="new-azurermservicebustopicauthorizationrule"></a>**New-AzureRmServiceBusTopicAuthorizationRule**
- De cmdlet New-AzureRmServiceBusTopicAuthorizationRule is verwijderd. Gebruik de cmdlet New-AzureRmServiceBusAuthorizationRule.

### <a name="new-azurermservicebustopickey"></a>**New-AzureRmServiceBusTopicKey**
- De cmdlet New-AzureRmServiceBusTopicKey is verwijderd. Gebruik de cmdlet New-AzureRmServiceBusKey.

### <a name="remove-azurermservicebustopicauthorizationrule"></a>**Remove-AzureRmServiceBusTopicAuthorizationRule**
- De cmdlet Remove-AzureRmServiceBusTopicAuthorizationRule is verwijderd. Gebruik de cmdlet Remove-AzureRmServiceBusAuthorizationRule.

### <a name="set-azurermservicebustopicauthorizationrule"></a>**Set-AzureRmServiceBusTopicAuthorizationRule**
- De cmdlet Set-AzureRmServiceBusTopicAuthorizationRule is verwijderd. Gebruik de cmdlet Set-AzureRmServiceBusAuthorizationRule.

### <a name="new-azurermservicebusnamespacekey"></a>**New-AzureRmServiceBusNamespaceKey**
- De cmdlet New-AzureRmServiceBusNamespaceKey is verwijderd. Gebruik de cmdlet New-AzureRmServiceBusKey.

### <a name="get-azurermservicebusqueueauthorizationrule"></a>**Get-AzureRmServiceBusQueueAuthorizationRule**
- De cmdlet Get-AzureRmServiceBusQueueAuthorizationRule is verwijderd. Gebruik de cmdlet Get-AzureRmServiceBusAuthorizationRule

### <a name="get-azurermservicebusqueuekey"></a>**Get-AzureRmServiceBusQueueKey**
- De cmdlet Get-AzureRmServiceBusQueueKey is verwijderd. Gebruik de cmdlet Get-AzureRmServiceBusKey.

### <a name="new-azurermservicebusqueueauthorizationrule"></a>**New-AzureRmServiceBusQueueAuthorizationRule**
- De cmdlet New-AzureRmServiceBusQueueAuthorizationRule is verwijderd. Gebruik de cmdlet New-AzureRmServiceBusAuthorizationRule.

### <a name="new-azurermservicebusqueuekey"></a>**New-AzureRmServiceBusQueueKey**
- De cmdlet New-AzureRmServiceBusQueueKey is verwijderd. Gebruik de cmdlet New-AzureRmServiceBusKey.

### <a name="remove-azurermservicebusqueueauthorizationrule"></a>**Remove-AzureRmServiceBusQueueAuthorizationRule**
- De cmdlet Remove-AzureRmServiceBusQueueAuthorizationRule is verwijderd. Gebruik de cmdlet Remove-AzureRmServiceBusAuthorizationRule.

### <a name="set-azurermservicebusqueueauthorizationrule"></a>**Set-AzureRmServiceBusQueueAuthorizationRule**
- De cmdlet Set-AzureRmServiceBusQueueAuthorizationRule is verwijderd. Gebruik de cmdlet Set-AzureRmServiceBusAuthorizationRule.

### <a name="get-azurermservicebusnamespaceauthorizationrule"></a>**Get-AzureRmServiceBusNamespaceAuthorizationRule**
- De cmdlet Get-AzureRmServiceBusNamespaceAuthorizationRule is verwijderd. Gebruik de cmdlet Get-AzureRmServiceBusAuthorizationRule

### <a name="get-azurermservicebusnamespacekey"></a>**Get-AzureRmServiceBusNamespaceKey**
- De cmdlet Get-AzureRmServiceBusNamespaceKey is verwijderd. Gebruik de cmdlet Get-AzureRmServiceBusKey.

### <a name="new-azurermservicebusnamespaceauthorizationrule"></a>**New-AzureRmServiceBusNamespaceAuthorizationRule**
- De cmdlet New-AzureRmServiceBusNamespaceAuthorizationRule is verwijderd. Gebruik de cmdlet New-AzureRmServiceBusAuthorizationRule.

### <a name="remove-azurermservicebusnamespaceauthorizationrule"></a>**Remove-AzureRmServiceBusNamespaceAuthorizationRule**
- De cmdlet Remove-AzureRmServiceBusNamespaceAuthorizationRule is verwijderd. Gebruik de cmdlet Remove-AzureRmServiceBusAuthorizationRule.

### <a name="set-azurermservicebusnamespaceauthorizationrule"></a>**Set-AzureRmServiceBusNamespaceAuthorizationRule**
- De cmdlet Set-AzureRmServiceBusNamespaceAuthorizationRule is verwijderd. Gebruik de cmdlet Set-AzureRmServiceBusAuthorizationRule.

### <a name="type-namespaceattributes"></a>**Type NamespaceAttributes**
- De volgende eigenschappen zijn verwijderd
    - Ingeschakeld
    - Status
   
```powershell
# Old
# The $namespace has Status and Enabled property 
$namespace = Get-AzureRmServiceBusNamespace <parameters>
$namespace.Status
$namespace.Enabled

# New
# The call remains the same, but the returned values NameSpace object will not have the Enabled and Status properties    
$namespace = Get-AzureRmServiceBusNamespace <parameters>
```

### <a name="type-queueattribute"></a>**Type QueueAttribute**
- De volgende eigenschappen zijn gemarkeerd als verouderd:
    - EnableBatchedOperations
    - EntityAvailabilityStatus
    - IsAnonymousAccessible
    - SupportOrdering

```powershell
# Old
# The $queue has EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties
$queue = Get-AzureRmServiceBusQueue <parameters>
$queue.EntityAvailabilityStatus
$queue.EnableBatchedOperations
$queue.IsAnonymousAccessible
$queue.SupportOrdering  

# New
# The call remains the same, but the returned values Queue object will not have the EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties    
$queue = Get-AzureRmServiceBusQueue <parameters>
```
   
### <a name="type-topicattribute"></a>**Type TopicAttribute**
- De volgende eigenschappen zijn gemarkeerd als verouderd:
    - Locatie
    - IsExpress
    - IsAnonymousAccessible
    - FilteringMessagesBeforePublishing
    - EnableSubscriptionPartitioning
    - EntityAvailabilityStatus

```powershell
# Old
# The $topic has EntityAvailabilityStatus, EnableSubscriptionPartitioning, IsAnonymousAccessible, IsExpress, Location and FilteringMessagesBeforePublishing properties
$topic = Get-AzureRmServiceBusTopic <parameters>
$topic.EntityAvailabilityStatus
$topic.EnableSubscriptionPartitioning
$topic.IsAnonymousAccessible
$topic.IsExpress
$topic.FilteringMessagesBeforePublishing
$topic.Location

# New
# The call remains the same, but the returned values Topic object will not have the EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties    
$topic = Get-AzureRmServiceBusTopic <parameters>
```
   
### <a name="type-subscriptionattribute"></a>**Type SubscriptionAttribute**
- De volgende eigenschappen zijn gemarkeerd als verouderd:
    - DeadLetteringOnFilterEvaluationExceptions
    - EntityAvailabilityStatus
    - IsReadOnly
    - Locatie
   
```powershell
# Old
# The $subscription has EntityAvailabilityStatus, EnableSubscriptionPartitioning, IsAnonymousAccessible, IsExpress, Location and FilteringMessagesBeforePublishing properties
$subscription = Get-AzureRmServiceBussubscription <parameters>
$subscription.EntityAvailabilityStatus
$subscription.EnableSubscriptionPartitioning
$subscription.IsAnonymousAccessible
$subscription.IsExpress
$subscription.FilteringMessagesBeforePublishing
$subscription.Location

# New
# The call remains the same, but the returned values Topic object will not have the EntityAvailabilityStatus, EnableBatchedOperations, IsAnonymousAccessible and SupportOrdering properties    
$subscription = Get-AzureRmServiceBussubscription <parameters>
```