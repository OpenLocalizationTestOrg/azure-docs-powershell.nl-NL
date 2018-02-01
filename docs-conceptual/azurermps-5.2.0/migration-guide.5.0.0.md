# <a name="breaking-changes-for-microsoft-azure-powershell-500"></a><span data-ttu-id="34c68-101">Belangrijke wijzigingen voor Microsoft Azure PowerShell 5.0.0</span><span class="sxs-lookup"><span data-stu-id="34c68-101">Breaking changes for Microsoft Azure PowerShell 5.0.0</span></span>

<span data-ttu-id="34c68-102">Dit document dient niet alleen als melding van een belangrijke wijziging, maar ook als migratiehandleiding voor gebruikers van de Microsoft Azure PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="34c68-102">This document serves as both a breaking change notification and migration guide for consumers of the Microsoft Azure PowerShell cmdlets.</span></span> <span data-ttu-id="34c68-103">Elke sectie beschrijft zowel de reden voor de belangrijke wijziging als het eenvoudigste migratiepad.</span><span class="sxs-lookup"><span data-stu-id="34c68-103">Each section describes both the impetus for the breaking change and the migration path of least resistance.</span></span> <span data-ttu-id="34c68-104">Raadpleeg voor een uitgebreidere context de pull-aanvraag die bij elke wijziging hoort.</span><span class="sxs-lookup"><span data-stu-id="34c68-104">For in-depth context, please refer to the pull request associated with each change.</span></span>

## <a name="table-of-contents"></a><span data-ttu-id="34c68-105">Inhoudsopgave</span><span class="sxs-lookup"><span data-stu-id="34c68-105">Table of Contents</span></span>

- [<span data-ttu-id="34c68-106">Belangrijke wijzigingen voor ApiManagement-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-106">Breaking changes to ApiManagement cmdlets</span></span>](#breaking-changes-to-apimanagement-cmdlets)
- [<span data-ttu-id="34c68-107">Belangrijke wijzigingen voor Batch-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-107">Breaking changes to Batch cmdlets</span></span>](#breaking-changes-to-batch-cmdlets)
- [<span data-ttu-id="34c68-108">Belangrijke wijzigingen voor Compute-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-108">Breaking changes to Compute cmdlets</span></span>](#breaking-changes-to-compute-cmdlets)
- [<span data-ttu-id="34c68-109">Belangrijke wijzigingen voor EventHub-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-109">Breaking changes to EventHub cmdlets</span></span>](#breaking-changes-to-eventhub-cmdlets)
- [<span data-ttu-id="34c68-110">Belangrijke wijzigingen voor Insights-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-110">Breaking changes to Insights cmdlets</span></span>](#breaking-changes-to-insights-cmdlets)
- [<span data-ttu-id="34c68-111">Belangrijke wijzigingen voor Network-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-111">Breaking changes to Network cmdlets</span></span>](#breaking-changes-to-network-cmdlets)
- [<span data-ttu-id="34c68-112">Belangrijke wijzigingen voor Resources-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-112">Breaking changes to Resources cmdlets</span></span>](#breaking-changes-to-resources-cmdlets)
- [<span data-ttu-id="34c68-113">Belangrijke wijzigingen voor ServiceBus-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-113">Breaking Changes to ServiceBus Cmdlets</span></span>](#breaking-changes-to-servicebus-cmdlets)

## <a name="breaking-changes-to-apimanagement-cmdlets"></a><span data-ttu-id="34c68-114">Belangrijke wijzigingen voor ApiManagement-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-114">Breaking changes to ApiManagement cmdlets</span></span>

### <a name="new-azurermapimanagementbackendproxy"></a><span data-ttu-id="34c68-115">**New-AzureRmApiManagementBackendProxy**</span><span class="sxs-lookup"><span data-stu-id="34c68-115">**New-AzureRmApiManagementBackendProxy**</span></span>
- <span data-ttu-id="34c68-116">De parameters UserName en Password worden vervangen door een PSCredential</span><span class="sxs-lookup"><span data-stu-id="34c68-116">Parameters "UserName" and "Password" are being replaced in favor of a PSCredential</span></span>

```powershell
# Old
New-AzureRmApiManagementBackendProxy [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
New-AzureRmApiManagementBackendProxy [other required parameters] -Credential $PSCredentialVariable
```

### <a name="new-azurermapimanagementuser"></a><span data-ttu-id="34c68-117">**New-AzureRmApiManagementUser**</span><span class="sxs-lookup"><span data-stu-id="34c68-117">**New-AzureRmApiManagementUser**</span></span>
- <span data-ttu-id="34c68-118">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-118">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapimanagementuser"></a><span data-ttu-id="34c68-119">**Set-AzureRmApiManagementUser**</span><span class="sxs-lookup"><span data-stu-id="34c68-119">**Set-AzureRmApiManagementUser**</span></span>
- <span data-ttu-id="34c68-120">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-120">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Set-AzureRmApiManagementUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApiManagementUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-batch-cmdlets"></a><span data-ttu-id="34c68-121">Belangrijke wijzigingen voor Batch-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-121">Breaking changes to Batch cmdlets</span></span>

### <a name="new-azurebatchcertificate"></a><span data-ttu-id="34c68-122">**New-AzureBatchCertificate**</span><span class="sxs-lookup"><span data-stu-id="34c68-122">**New-AzureBatchCertificate**</span></span>
- <span data-ttu-id="34c68-123">De parameter `Password` wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-123">Parameter `Password` being replaced in favor of a Secure string</span></span>

```powershell
# Old
New-AzureBatchCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureBatchCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchcomputenodeuser"></a><span data-ttu-id="34c68-124">**New-AzureBatchComputeNodeUser**</span><span class="sxs-lookup"><span data-stu-id="34c68-124">**New-AzureBatchComputeNodeUser**</span></span>
- <span data-ttu-id="34c68-125">De parameter `Password` wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-125">Parameter `Password` being replaced in favor of a Secure string</span></span>

```powershell
# Old
New-AzureBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
New-AzureBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermbatchcomputenodeuser"></a><span data-ttu-id="34c68-126">**Set-AzureRmBatchComputeNodeUser**</span><span class="sxs-lookup"><span data-stu-id="34c68-126">**Set-AzureRmBatchComputeNodeUser**</span></span>
- <span data-ttu-id="34c68-127">De parameter `Password` wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-127">Parameter `Password` being replaced in favor of a Secure string</span></span>

```powershell
# Old
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmBatchComputeNodeUser [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurebatchtask"></a><span data-ttu-id="34c68-128">**New-AzureBatchTask**</span><span class="sxs-lookup"><span data-stu-id="34c68-128">**New-AzureBatchTask**</span></span>
 - <span data-ttu-id="34c68-129">De switch `RunElevated` is verwijderd en vervangen door `UserIdentity`.</span><span class="sxs-lookup"><span data-stu-id="34c68-129">Removed the `RunElevated` switch and replaced it with `UserIdentity`.</span></span>

```powershell
# Old
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -RunElevated $TRUE

# New
$autoUser = New-Object Microsoft.Azure.Commands.Batch.Models.PSAutoUserSpecification -ArgumentList @("Task", "Admin")
$userIdentity = New-Object Microsoft.Azure.Commands.Batch.Models.PSUserIdentity $autoUser
New-AzureBatchTask -Id $taskId1 -JobId $jobId -CommandLine "cmd /c echo hello" -UserIdentity $userIdentity
```

<span data-ttu-id="34c68-130">Dit is ook van invloed op de eigenschap `RunElevated` voor `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` en `PSJobReleaseTask`.</span><span class="sxs-lookup"><span data-stu-id="34c68-130">This additionally impacts the `RunElevated` property on `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask`, and `PSJobReleaseTask`.</span></span>

### <a name="psmultiinstancesettings"></a><span data-ttu-id="34c68-131">**PSMultiInstanceSettings**</span><span class="sxs-lookup"><span data-stu-id="34c68-131">**PSMultiInstanceSettings**</span></span>

- <span data-ttu-id="34c68-132">De constructor `PSMultiInstanceSettings` verwacht niet langer een vereiste parameter `numberOfInstances`, maar verwacht nu een vereiste parameter `coordinationCommandLine`.</span><span class="sxs-lookup"><span data-stu-id="34c68-132">`PSMultiInstanceSettings` constructor no longer takes a required `numberOfInstances` parameter, instead it takes a required `coordinationCommandLine` parameter.</span></span>

```powershell
# Old
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @(2)
$settings.CoordinationCommandLine = "cmd /c echo hello"
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings

# New
$settings = New-Object Microsoft.Azure.Commands.Batch.Models.PSMultiInstanceSettings -ArgumentList @("cmd /c echo hello", 2)
New-AzureBatchTask [other parameters] -MultiInstanceSettings $settings
```

### <a name="get-azurebatchtask"></a><span data-ttu-id="34c68-133">**Get-AzureBatchTask**</span><span class="sxs-lookup"><span data-stu-id="34c68-133">**Get-AzureBatchTask**</span></span>
 - <span data-ttu-id="34c68-134">De eigenschap `RunElevated` voor `PSCloudTask` is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-134">Removed the `RunElevated` property on `PSCloudTask`.</span></span> <span data-ttu-id="34c68-135">De eigenschap `UserIdentity` is toegevoegd ter vervanging van `RunElevated`.</span><span class="sxs-lookup"><span data-stu-id="34c68-135">The `UserIdentity` property has been added to replace `RunElevated`.</span></span>

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.RunElevated

# New
$task = Get-AzureBatchTask [parameters]
$task.UserIdentity.AutoUser.ElevationLevel
```

<span data-ttu-id="34c68-136">Dit is ook van invloed op de eigenschap `RunElevated` voor `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask` en `PSJobReleaseTask`.</span><span class="sxs-lookup"><span data-stu-id="34c68-136">This additionally impacts the `RunElevated` property on `PSCloudTask`, `PSStartTask`, `PSJobManagerTask`, `PSJobPreparationTask`, and `PSJobReleaseTask`.</span></span>

### <a name="multiple-types"></a><span data-ttu-id="34c68-137">**Meerdere typen**</span><span class="sxs-lookup"><span data-stu-id="34c68-137">**Multiple types**</span></span>

- <span data-ttu-id="34c68-138">De naam van de eigenschap `SchedulingError` is voor `PSExitConditions` gewijzigd in `PreProcessingError`.</span><span class="sxs-lookup"><span data-stu-id="34c68-138">Renamed the `SchedulingError` property on `PSExitConditions` to `PreProcessingError`.</span></span>

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExitConditions.PreProcessingError
```

### <a name="multiple-types"></a><span data-ttu-id="34c68-139">**Meerdere typen**</span><span class="sxs-lookup"><span data-stu-id="34c68-139">**Multiple types**</span></span>

- <span data-ttu-id="34c68-140">De naam van de eigenschap `SchedulingError` is voor `PSJobPreparationTaskExecutionInformation`, `PSJobReleaseTaskExecutionInformation`, `PSStartTaskInformation`, `PSSubtaskInformation` en `PSTaskExecutionInformation` gewijzigd in `FailureInformation`.</span><span class="sxs-lookup"><span data-stu-id="34c68-140">Renamed the `SchedulingError` property on `PSJobPreparationTaskExecutionInformation`, `PSJobReleaseTaskExecutionInformation`, `PSStartTaskInformation`, `PSSubtaskInformation`, and `PSTaskExecutionInformation` to `FailureInformation`.</span></span>
  - <span data-ttu-id="34c68-141">Telkens wanneer een taak mislukt, wordt `FailureInformation` geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="34c68-141">`FailureInformation` is returned any time there is a task failure.</span></span> <span data-ttu-id="34c68-142">Dit omvat alle voorgaande gevallen van planningsfouten, 'nonzero'-taakafsluitcodes en fouten bij het uploaden van bestanden door de nieuwe functie voor uitvoerbestanden.</span><span class="sxs-lookup"><span data-stu-id="34c68-142">This includes all previous scheduling error cases, as well as nonzero task exit codes, and file upload failures from the new output files feature.</span></span>
  - <span data-ttu-id="34c68-143">Dit is op dezelfde manier gestructureerd als voorheen, dus er zijn geen codewijzigingen nodig voor het gebruik van dit type.</span><span class="sxs-lookup"><span data-stu-id="34c68-143">This is structured the same as before, so no code change is needed when using this type.</span></span>

```powershell
# Old
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.SchedulingError

# New
$task = Get-AzureBatchTask [parameters]
$task.ExecutionInformation.FailureInformation
```

<span data-ttu-id="34c68-144">Deze wijziging heeft ook invloed op: Get-AzureBatchPool, Get-AzureBatchSubtask en Get-AzureBatchJobPreparationAndReleaseTaskStatus</span><span class="sxs-lookup"><span data-stu-id="34c68-144">This additionally impacts: Get-AzureBatchPool, Get-AzureBatchSubtask, and Get-AzureBatchJobPreparationAndReleaseTaskStatus</span></span>

### <a name="new-azurebatchpool"></a><span data-ttu-id="34c68-145">**New-AzureBatchPool**</span><span class="sxs-lookup"><span data-stu-id="34c68-145">**New-AzureBatchPool**</span></span>
 - <span data-ttu-id="34c68-146">`TargetDedicated` is verwijderd en vervangen door `TargetDedicatedComputeNodes` en `TargetLowPriorityComputeNodes`.</span><span class="sxs-lookup"><span data-stu-id="34c68-146">Removed `TargetDedicated` and replaced it with `TargetDedicatedComputeNodes` and `TargetLowPriorityComputeNodes`.</span></span>
 - <span data-ttu-id="34c68-147">`TargetDedicatedComputeNodes` heeft de alias `TargetDedicated`.</span><span class="sxs-lookup"><span data-stu-id="34c68-147">`TargetDedicatedComputeNodes` has an alias `TargetDedicated`.</span></span>

```powershell
# Old
New-AzureBatchPool [other parameters] [-TargetDedicated <Int32>]

# New
New-AzureBatchPool [other parameters] [-TargetDedicatedComputeNodes <Int32>] [-TargetLowPriorityComputeNodes <Int32>]
```

<span data-ttu-id="34c68-148">Dit is ook van invloed op: Start-AzureBatchPoolResize</span><span class="sxs-lookup"><span data-stu-id="34c68-148">This also impacts: Start-AzureBatchPoolResize</span></span>

### <a name="get-azurebatchpool"></a><span data-ttu-id="34c68-149">**Get-AzureBatchPool**</span><span class="sxs-lookup"><span data-stu-id="34c68-149">**Get-AzureBatchPool**</span></span>
 - <span data-ttu-id="34c68-150">De namen van de eigenschappen `TargetDedicated` en `CurrentDedicated` zijn voor `PSCloudPool` gewijzigd in `TargetDedicatedComputeNodes` en `CurrentDedicatedComputeNodes`.</span><span class="sxs-lookup"><span data-stu-id="34c68-150">Renamed the `TargetDedicated` and `CurrentDedicated` properties on `PSCloudPool` to `TargetDedicatedComputeNodes` and `CurrentDedicatedComputeNodes`.</span></span>

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

### <a name="type-pscloudpool"></a><span data-ttu-id="34c68-151">**Type PSCloudPool**</span><span class="sxs-lookup"><span data-stu-id="34c68-151">**Type PSCloudPool**</span></span>

- <span data-ttu-id="34c68-152">De naam van `ResizeError` is voor `PSCloudPool` gewijzigd in `ResizeErrors` en dit is nu een verzameling.</span><span class="sxs-lookup"><span data-stu-id="34c68-152">Renamed `ResizeError` to `ResizeErrors` on `PSCloudPool`, and it is now a collection.</span></span>

```powershell
# Old
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeError

# New
$pool = Get-AzureBatchPool [parameters]
$pool.ResizeErrors[0]
```

### <a name="new-azurebatchjob"></a><span data-ttu-id="34c68-153">**New-AzureBatchJob**</span><span class="sxs-lookup"><span data-stu-id="34c68-153">**New-AzureBatchJob**</span></span>
- <span data-ttu-id="34c68-154">De naam van de eigenschap `TargetDedicated` is voor `PSPoolSpecification` gewijzigd in `TargetDedicatedComputeNodes`.</span><span class="sxs-lookup"><span data-stu-id="34c68-154">Renamed the `TargetDedicated` property on `PSPoolSpecification` to `TargetDedicatedComputeNodes`.</span></span>

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

### <a name="get-azurebatchnodefile"></a><span data-ttu-id="34c68-155">**Get-AzureBatchNodeFile**</span><span class="sxs-lookup"><span data-stu-id="34c68-155">**Get-AzureBatchNodeFile**</span></span>
 - <span data-ttu-id="34c68-156">`Name` is verwijderd en vervangen door `Path`.</span><span class="sxs-lookup"><span data-stu-id="34c68-156">Removed `Name` and replaced it with `Path`.</span></span>
 - <span data-ttu-id="34c68-157">`Path` heeft de alias `Name`.</span><span class="sxs-lookup"><span data-stu-id="34c68-157">`Path` has an alias `Name`.</span></span>

```powershell
# Old
Get-AzureBatchNodeFile [other parameters] [[-Name] <String>]

# New
Get-AzureBatchNodeFile [other parameters] [[-Path] <String>]
```

<span data-ttu-id="34c68-158">Dit is ook van invloed op: Get-AzureBatchNodeFileContent, Remove-AzureBatchNodeFile</span><span class="sxs-lookup"><span data-stu-id="34c68-158">This also impacts: Get-AzureBatchNodeFileContent, Remove-AzureBatchNodeFile</span></span>

### <a name="type-psnodefile"></a><span data-ttu-id="34c68-159">Type **PSNodeFile**</span><span class="sxs-lookup"><span data-stu-id="34c68-159">Type **PSNodeFile**</span></span>

 - <span data-ttu-id="34c68-160">De naam van de eigenschap `Name` is voor `PSNodeFile` gewijzigd in `Path`.</span><span class="sxs-lookup"><span data-stu-id="34c68-160">Renamed the `Name` property on `PSNodeFile` to `Path`.</span></span>

```powershell
# Old
$file = Get-AzureBatchNodeFile [parameters]
$file.Name

# New
$file = Get-AzureBatchNodeFile [parameters]
$file.Path
```

### <a name="get-azurebatchsubtask"></a><span data-ttu-id="34c68-161">**Get-AzureBatchSubtask**</span><span class="sxs-lookup"><span data-stu-id="34c68-161">**Get-AzureBatchSubtask**</span></span>
- <span data-ttu-id="34c68-162">De eigenschappen `PreviousState` en `State` zijn voor `PSSubtaskInformation` niet langer van het type `TaskState`, maar zijn nu van het type `SubtaskState`.</span><span class="sxs-lookup"><span data-stu-id="34c68-162">The `PreviousState` and `State` properties of `PSSubtaskInformation` are no longer of type `TaskState`, instead they are of type `SubtaskState`.</span></span>
  - <span data-ttu-id="34c68-163">In tegenstelling tot `TaskState` heeft `SubtaskState` geen `Active`-waarde, omdat het niet mogelijk is dat subtaken zich in een `Active`-status bevinden.</span><span class="sxs-lookup"><span data-stu-id="34c68-163">Unlike `TaskState`, `SubtaskState` has no `Active` value, since it is not possible for subtasks to be in an `Active` state.</span></span>

```powershell
# Old
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.TaskState.Running) { }

# New
$subtask = Get-AzureBatchSubtask [parameters]
if ($subtask.State -eq Microsoft.Azure.Batch.Common.SubtaskState.Running) { }
```

## <a name="breaking-changes-to-compute-cmdlets"></a><span data-ttu-id="34c68-164">Belangrijke wijzigingen voor Compute-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-164">Breaking changes to Compute cmdlets</span></span>

### <a name="set-azurermvmaccessextension"></a><span data-ttu-id="34c68-165">**Set-AzureRmVMAccessExtension**</span><span class="sxs-lookup"><span data-stu-id="34c68-165">**Set-AzureRmVMAccessExtension**</span></span>
- <span data-ttu-id="34c68-166">De parameters UserName en Password worden vervangen door een PSCredential</span><span class="sxs-lookup"><span data-stu-id="34c68-166">Parameters "UserName" and "Password" are being replaced in favor of a PSCredential</span></span>

```powershell
# Old
Set-AzureRmVMAccessExtension [other required parameters] -UserName "plain-text string" -Password "plain-text string"

# New
Set-AzureRmVMAccessExtension [other required parameters] -Credential $PSCredential
```

## <a name="breaking-changes-to-eventhub-cmdlets"></a><span data-ttu-id="34c68-167">Belangrijke wijzigingen voor EventHub-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-167">Breaking changes to EventHub cmdlets</span></span>

### <a name="new-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="34c68-168">**New-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-168">**New-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-169">De cmdlet New-AzureRmEventHubNamespaceAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-169">The 'New-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-170">Gebruik de cmdlet New-AzureRmEventHubAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="34c68-170">Please use the 'New-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="get-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="34c68-171">**Get-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-171">**Get-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-172">De cmdlet Get-AzureRmEventHubNamespaceAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-172">The 'Get-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-173">Gebruik de cmdlet Get-AzureRmEventHubAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="34c68-173">Please use the 'Get-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="set-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="34c68-174">**Set-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-174">**Set-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-175">De cmdlet Set-AzureRmEventHubNamespaceAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-175">The 'Set-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-176">Gebruik de cmdlet Set-AzureRmEventHubAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="34c68-176">Please use the 'Set-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="remove-azurermeventhubnamespaceauthorizationrule"></a><span data-ttu-id="34c68-177">**Remove-AzureRmEventHubNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-177">**Remove-AzureRmEventHubNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-178">De cmdlet Remove-AzureRmEventHubNamespaceAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-178">The 'Remove-AzureRmEventHubNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-179">Gebruik de cmdlet Remove-AzureRmEventHubAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="34c68-179">Please use the 'Remove-AzureRmEventHubAuthorizationRule' cmdlet</span></span>
    
### <a name="new-azurermeventhubnamespacekey"></a><span data-ttu-id="34c68-180">**New-AzureRmEventHubNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="34c68-180">**New-AzureRmEventHubNamespaceKey**</span></span>
- <span data-ttu-id="34c68-181">De cmdlet New-AzureRmEventHubNamespaceKey is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-181">The 'New-AzureRmEventHubNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-182">Gebruik de cmdlet New-AzureRmEventHubKey</span><span class="sxs-lookup"><span data-stu-id="34c68-182">Please use the 'New-AzureRmEventHubKey' cmdlet</span></span>
    
### <a name="get-azurermeventhubnamespacekey"></a><span data-ttu-id="34c68-183">**Get-AzureRmEventHubNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="34c68-183">**Get-AzureRmEventHubNamespaceKey**</span></span>
- <span data-ttu-id="34c68-184">De cmdlet Get-AzureRmEventHubNamespaceKey is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-184">The 'Get-AzureRmEventHubNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-185">Gebruik de cmdlet Get-AzureRmEventHubKey</span><span class="sxs-lookup"><span data-stu-id="34c68-185">Please use the 'Get-AzureRmEventHubKey' cmdlet</span></span>
    
### <a name="new-azurermeventhubnamespace"></a><span data-ttu-id="34c68-186">**New-AzureRmEventHubNamespace**</span><span class="sxs-lookup"><span data-stu-id="34c68-186">**New-AzureRmEventHubNamespace**</span></span>
- <span data-ttu-id="34c68-187">De eigenschappen Status en Enabled worden verwijderd voor NamespceAttributes.</span><span class="sxs-lookup"><span data-stu-id="34c68-187">The property 'Status' and 'Enabled' from the NamespceAttributes will be removed.</span></span> 

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
    
### <a name="get-azurermeventhubnamespace"></a><span data-ttu-id="34c68-188">**Get-AzureRmEventHubNamespace**</span><span class="sxs-lookup"><span data-stu-id="34c68-188">**Get-AzureRmEventHubNamespace**</span></span>
- <span data-ttu-id="34c68-189">De eigenschappen Status en Enabled worden verwijderd voor NamespceAttributes.</span><span class="sxs-lookup"><span data-stu-id="34c68-189">The property 'Status' and 'Enabled' from the NamespceAttributes will be removed.</span></span> 

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
    
### <a name="set-azurermeventhubnamespace"></a><span data-ttu-id="34c68-190">**Set-AzureRmEventHubNamespace**</span><span class="sxs-lookup"><span data-stu-id="34c68-190">**Set-AzureRmEventHubNamespace**</span></span>
- <span data-ttu-id="34c68-191">De eigenschappen Status en Enabled worden verwijderd voor NamespceAttributes.</span><span class="sxs-lookup"><span data-stu-id="34c68-191">The property 'Status' and 'Enabled' from the NamespceAttributes will be removed.</span></span> 

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
  
### <a name="new-azurermeventhubconsumergroup"></a><span data-ttu-id="34c68-192">**New-AzureRmEventHubConsumerGroup**</span><span class="sxs-lookup"><span data-stu-id="34c68-192">**New-AzureRmEventHubConsumerGroup**</span></span>
- <span data-ttu-id="34c68-193">De eigenschap EventHubPath wordt verwijderd voor ConsumerGroupAttributes.</span><span class="sxs-lookup"><span data-stu-id="34c68-193">The property 'EventHubPath' from the ConsumerGroupAttributes will be removed.</span></span>

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = New-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="set-azurermeventhubconsumergroup"></a><span data-ttu-id="34c68-194">**Set-AzureRmEventHubConsumerGroup**</span><span class="sxs-lookup"><span data-stu-id="34c68-194">**Set-AzureRmEventHubConsumerGroup**</span></span>
- <span data-ttu-id="34c68-195">De eigenschap EventHubPath wordt verwijderd voor ConsumerGroupAttributes.</span><span class="sxs-lookup"><span data-stu-id="34c68-195">The property 'EventHubPath' from the ConsumerGroupAttributes will be removed.</span></span>

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Set-AzureRmEventHubConsumerGroup <parameters>
```
    
### <a name="get-azurermeventhubconsumergroup"></a><span data-ttu-id="34c68-196">**Get-AzureRmEventHubConsumerGroup**</span><span class="sxs-lookup"><span data-stu-id="34c68-196">**Get-AzureRmEventHubConsumerGroup**</span></span>
- <span data-ttu-id="34c68-197">De eigenschap EventHubPath wordt verwijderd voor ConsumerGroupAttributes.</span><span class="sxs-lookup"><span data-stu-id="34c68-197">The property 'EventHubPath' from the ConsumerGroupAttributes will be removed.</span></span>

```powershell
# Old
# The $consumergroup has EventHubPath property 
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
$consumergroup.EventHubPath

# New
# The call remains the same, but the returned values ConsumerGroup object will not have the EventHubPath property    
$consumergroup = Get-AzureRmEventHubConsumerGroup <parameters>
```

## <a name="breaking-changes-to-insights-cmdlets"></a><span data-ttu-id="34c68-198">Belangrijke wijzigingen voor Insights-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-198">Breaking changes to Insights cmdlets</span></span>

### <a name="add-azurermlogalertrule"></a><span data-ttu-id="34c68-199">**Add-AzureRMLogAlertRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-199">**Add-AzureRMLogAlertRule**</span></span>
- <span data-ttu-id="34c68-200">De cmdlet **Add-AzureRMLogAlertRule** is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="34c68-200">The **Add-AzureRMLogAlertRule** cmdlet has been deprecated</span></span>
- <span data-ttu-id="34c68-201">Na 1 oktober zal het gebruik van deze cmdlet niet langer effect hebben, omdat deze functionaliteit wordt overgedragen naar Waarschuwingen voor activiteitenlogboeken.</span><span class="sxs-lookup"><span data-stu-id="34c68-201">After October 1st using this cmdlet will no longer have any effect as this functionality is being transitioned to Activity Log Alerts.</span></span> <span data-ttu-id="34c68-202">Raadpleeg https://aka.ms/migratemealerts voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="34c68-202">Please see https://aka.ms/migratemealerts for more information.</span></span>

### <a name="get-azurermusage"></a><span data-ttu-id="34c68-203">**Get-AzureRMUsage**</span><span class="sxs-lookup"><span data-stu-id="34c68-203">**Get-AzureRMUsage**</span></span>
- <span data-ttu-id="34c68-204">De cmdlet **Get-AzureRMUsage** is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="34c68-204">The **Get-AzureRMUsage** cmdlet has been deprecated</span></span>

### <a name="get-azurermalerthistory--get-azurermautoscalehistory--get-azurermlogs"></a><span data-ttu-id="34c68-205">**Get-AzureRmAlertHistory** / **Get-AzureRmAutoscaleHistory** / **Get-AzureRmLogs**</span><span class="sxs-lookup"><span data-stu-id="34c68-205">**Get-AzureRmAlertHistory** / **Get-AzureRmAutoscaleHistory** / **Get-AzureRmLogs**</span></span>
- <span data-ttu-id="34c68-206">Uitvoerwijziging: het veld EventChannels van het EventData-object (geretourneerd door deze cmdlets) wordt afgeschaft omdat dit nu een constante waarde retourneert (Admin,Operation.)</span><span class="sxs-lookup"><span data-stu-id="34c68-206">Output change: The field EventChannels from the EventData object (returned by these cmdlets) is being deprecated since it now returns a constant value (Admin,Operation.)</span></span>

### <a name="get-azurermalertrule"></a><span data-ttu-id="34c68-207">**Get-AzureRmAlertRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-207">**Get-AzureRmAlertRule**</span></span>
- <span data-ttu-id="34c68-208">Uitvoerwijziging: de uitvoer van deze cmdlet wordt afgevlakt (dat wil zeggen: het eigenschappenveld wordt verwijderd) om zo de gebruikerservaring te verbeteren.</span><span class="sxs-lookup"><span data-stu-id="34c68-208">Output change: The output of this cmdlet will be flattened, i.e. elimination of the properties field, to improve the user experience.</span></span>

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

### <a name="get-azurermautoscalesetting"></a><span data-ttu-id="34c68-209">**Get-AzureRmAutoscaleSetting**</span><span class="sxs-lookup"><span data-stu-id="34c68-209">**Get-AzureRmAutoscaleSetting**</span></span>
- <span data-ttu-id="34c68-210">Uitvoerwijziging: het veld AutoscaleSettingResourceName wordt afgeschaft omdat dit altijd gelijk is aan het veld Name.</span><span class="sxs-lookup"><span data-stu-id="34c68-210">Output change: The AutoscaleSettingResourceName field will be deprecated since it always equals the Name field.</span></span>

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

### <a name="remove-azurermalertrule--remove-azurermlogprofile"></a><span data-ttu-id="34c68-211">**Remove-AzureRmAlertRule** / **Remove-AzureRmLogProfile**</span><span class="sxs-lookup"><span data-stu-id="34c68-211">**Remove-AzureRmAlertRule** / **Remove-AzureRmLogProfile**</span></span>
- <span data-ttu-id="34c68-212">Uitvoerwijziging: het type uitvoer wordt gewijzigd, zodat er een enkel object wordt geretourneerd met de aanvraag-id en de statuscode.</span><span class="sxs-lookup"><span data-stu-id="34c68-212">Output change: The type of the output will change to return a single object containing the request Id and the status code.</span></span>

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

## <a name="breaking-changes-to-network-cmdlets"></a><span data-ttu-id="34c68-213">Belangrijke wijzigingen voor Network-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-213">Breaking changes to Network cmdlets</span></span>

### <a name="add-azurermapplicationgatewaysslcertificate"></a><span data-ttu-id="34c68-214">**Add-AzureRmApplicationGatewaySslCertificate**</span><span class="sxs-lookup"><span data-stu-id="34c68-214">**Add-AzureRmApplicationGatewaySslCertificate**</span></span>
- <span data-ttu-id="34c68-215">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-215">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Add-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermapplicationgatewaysslcertificate"></a><span data-ttu-id="34c68-216">**New-AzureRmApplicationGatewaySslCertificate**</span><span class="sxs-lookup"><span data-stu-id="34c68-216">**New-AzureRmApplicationGatewaySslCertificate**</span></span>
- <span data-ttu-id="34c68-217">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-217">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
New-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermapplicationgatewaysslcertificate"></a><span data-ttu-id="34c68-218">**Set-AzureRmApplicationGatewaySslCertificate**</span><span class="sxs-lookup"><span data-stu-id="34c68-218">**Set-AzureRmApplicationGatewaySslCertificate**</span></span>
- <span data-ttu-id="34c68-219">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-219">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password "plain-text string"

# New
Set-AzureRmApplicationGatewaySslCertificate [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-resources-cmdlets"></a><span data-ttu-id="34c68-220">Belangrijke wijzigingen voor Resources-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-220">Breaking changes to Resources cmdlets</span></span>

### <a name="new-azurermadappcredential"></a><span data-ttu-id="34c68-221">**New-AzureRmADAppCredential**</span><span class="sxs-lookup"><span data-stu-id="34c68-221">**New-AzureRmADAppCredential**</span></span>
- <span data-ttu-id="34c68-222">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-222">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADAppCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADAppCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadapplication"></a><span data-ttu-id="34c68-223">**New-AzureRmADApplication**</span><span class="sxs-lookup"><span data-stu-id="34c68-223">**New-AzureRmADApplication**</span></span>
- <span data-ttu-id="34c68-224">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-224">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADApplication [other required parameters] -Password "plain-text string"

# New
New-AzureRmADApplication [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadserviceprincipal"></a><span data-ttu-id="34c68-225">**New-AzureRmADServicePrincipal**</span><span class="sxs-lookup"><span data-stu-id="34c68-225">**New-AzureRmADServicePrincipal**</span></span>
- <span data-ttu-id="34c68-226">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-226">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADServicePrincipal [other required parameters] -Password "plain-text string"

# New
New-AzureRmADServicePrincipal [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermadspcredential"></a><span data-ttu-id="34c68-227">**New-AzureRmADSpCredential**</span><span class="sxs-lookup"><span data-stu-id="34c68-227">**New-AzureRmADSpCredential**</span></span>
- <span data-ttu-id="34c68-228">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-228">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADSpCredential [other required parameters] -Password "plain-text string"

# New
New-AzureRmADSpCredential [other required parameters] -Password $SecureStringVariable
```

### <a name="new-azurermaduser"></a><span data-ttu-id="34c68-229">**New-AzureRmADUser**</span><span class="sxs-lookup"><span data-stu-id="34c68-229">**New-AzureRmADUser**</span></span>
- <span data-ttu-id="34c68-230">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-230">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
New-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
New-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

### <a name="set-azurermaduser"></a><span data-ttu-id="34c68-231">**Set-AzureRmADUser**</span><span class="sxs-lookup"><span data-stu-id="34c68-231">**Set-AzureRmADUser**</span></span>
- <span data-ttu-id="34c68-232">De parameter Password wordt vervangen door een SecureString</span><span class="sxs-lookup"><span data-stu-id="34c68-232">Parameter "Password" being replaced in favor of a SecureString</span></span>

```powershell
# Old
Set-AzureRmADUser [other required parameters] -Password "plain-text string"

# New
Set-AzureRmADUser [other required parameters] -Password $SecureStringVariable
```

## <a name="breaking-changes-to-servicebus-cmdlets"></a><span data-ttu-id="34c68-233">Belangrijke wijzigingen voor ServiceBus-cmdlets</span><span class="sxs-lookup"><span data-stu-id="34c68-233">Breaking changes to ServiceBus cmdlets</span></span>

### <a name="get-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="34c68-234">**Get-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-234">**Get-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-235">De cmdlet Get-AzureRmServiceBusTopicAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-235">The 'Get-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-236">Gebruik de cmdlet Get-AzureRmServiceBusAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="34c68-236">Please use the 'Get-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>    

### <a name="get-azurermservicebustopickey"></a><span data-ttu-id="34c68-237">**Get-AzureRmServiceBusTopicKey**</span><span class="sxs-lookup"><span data-stu-id="34c68-237">**Get-AzureRmServiceBusTopicKey**</span></span>
- <span data-ttu-id="34c68-238">De cmdlet Get-AzureRmServiceBusTopicKey is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-238">The 'Get-AzureRmServiceBusTopicKey' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-239">Gebruik de cmdlet Get-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="34c68-239">Please use the 'Get-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="new-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="34c68-240">**New-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-240">**New-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-241">De cmdlet New-AzureRmServiceBusTopicAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-241">The 'New-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-242">Gebruik de cmdlet New-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="34c68-242">Please use the 'New-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="new-azurermservicebustopickey"></a><span data-ttu-id="34c68-243">**New-AzureRmServiceBusTopicKey**</span><span class="sxs-lookup"><span data-stu-id="34c68-243">**New-AzureRmServiceBusTopicKey**</span></span>
- <span data-ttu-id="34c68-244">De cmdlet New-AzureRmServiceBusTopicKey is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-244">The 'New-AzureRmServiceBusTopicKey' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-245">Gebruik de cmdlet New-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="34c68-245">Please use the 'New-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="remove-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="34c68-246">**Remove-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-246">**Remove-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-247">De cmdlet Remove-AzureRmServiceBusTopicAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-247">The 'Remove-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-248">Gebruik de cmdlet Remove-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="34c68-248">Please use the 'Remove-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="set-azurermservicebustopicauthorizationrule"></a><span data-ttu-id="34c68-249">**Set-AzureRmServiceBusTopicAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-249">**Set-AzureRmServiceBusTopicAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-250">De cmdlet Set-AzureRmServiceBusTopicAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-250">The 'Set-AzureRmServiceBusTopicAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-251">Gebruik de cmdlet Set-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="34c68-251">Please use the 'Set-AzureRmServiceBusAuthorizationRule'cmdlet.</span></span>

### <a name="new-azurermservicebusnamespacekey"></a><span data-ttu-id="34c68-252">**New-AzureRmServiceBusNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="34c68-252">**New-AzureRmServiceBusNamespaceKey**</span></span>
- <span data-ttu-id="34c68-253">De cmdlet New-AzureRmServiceBusNamespaceKey is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-253">The 'New-AzureRmServiceBusNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-254">Gebruik de cmdlet New-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="34c68-254">Please use the 'New-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="get-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="34c68-255">**Get-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-255">**Get-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-256">De cmdlet Get-AzureRmServiceBusQueueAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-256">The 'Get-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-257">Gebruik de cmdlet Get-AzureRmServiceBusAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="34c68-257">Please use the 'Get-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="get-azurermservicebusqueuekey"></a><span data-ttu-id="34c68-258">**Get-AzureRmServiceBusQueueKey**</span><span class="sxs-lookup"><span data-stu-id="34c68-258">**Get-AzureRmServiceBusQueueKey**</span></span>
- <span data-ttu-id="34c68-259">De cmdlet Get-AzureRmServiceBusQueueKey is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-259">The 'Get-AzureRmServiceBusQueueKey' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-260">Gebruik de cmdlet Get-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="34c68-260">Please use the 'Get-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="new-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="34c68-261">**New-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-261">**New-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-262">De cmdlet New-AzureRmServiceBusQueueAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-262">The 'New-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-263">Gebruik de cmdlet New-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="34c68-263">Please use the 'New-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="new-azurermservicebusqueuekey"></a><span data-ttu-id="34c68-264">**New-AzureRmServiceBusQueueKey**</span><span class="sxs-lookup"><span data-stu-id="34c68-264">**New-AzureRmServiceBusQueueKey**</span></span>
- <span data-ttu-id="34c68-265">De cmdlet New-AzureRmServiceBusQueueKey is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-265">The 'New-AzureRmServiceBusQueueKey' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-266">Gebruik de cmdlet New-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="34c68-266">Please use the 'New-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="remove-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="34c68-267">**Remove-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-267">**Remove-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-268">De cmdlet Remove-AzureRmServiceBusQueueAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-268">The 'Remove-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-269">Gebruik de cmdlet Remove-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="34c68-269">Please use the 'GRemove-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="set-azurermservicebusqueueauthorizationrule"></a><span data-ttu-id="34c68-270">**Set-AzureRmServiceBusQueueAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-270">**Set-AzureRmServiceBusQueueAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-271">De cmdlet Set-AzureRmServiceBusQueueAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-271">The 'Set-AzureRmServiceBusQueueAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-272">Gebruik de cmdlet Set-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="34c68-272">Please use the 'Set-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="get-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="34c68-273">**Get-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-273">**Get-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-274">De cmdlet Get-AzureRmServiceBusNamespaceAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-274">The 'Get-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-275">Gebruik de cmdlet Get-AzureRmServiceBusAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="34c68-275">Please use the 'Get-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="get-azurermservicebusnamespacekey"></a><span data-ttu-id="34c68-276">**Get-AzureRmServiceBusNamespaceKey**</span><span class="sxs-lookup"><span data-stu-id="34c68-276">**Get-AzureRmServiceBusNamespaceKey**</span></span>
- <span data-ttu-id="34c68-277">De cmdlet Get-AzureRmServiceBusNamespaceKey is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-277">The 'Get-AzureRmServiceBusNamespaceKey' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-278">Gebruik de cmdlet Get-AzureRmServiceBusKey.</span><span class="sxs-lookup"><span data-stu-id="34c68-278">Please use the 'Get-AzureRmServiceBusKey' cmdlet.</span></span>

### <a name="new-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="34c68-279">**New-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-279">**New-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-280">De cmdlet New-AzureRmServiceBusNamespaceAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-280">The 'New-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-281">Gebruik de cmdlet New-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="34c68-281">Please use the 'New-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="remove-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="34c68-282">**Remove-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-282">**Remove-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-283">De cmdlet Remove-AzureRmServiceBusNamespaceAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-283">The 'Remove-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-284">Gebruik de cmdlet Remove-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="34c68-284">Please use the 'Remove-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="set-azurermservicebusnamespaceauthorizationrule"></a><span data-ttu-id="34c68-285">**Set-AzureRmServiceBusNamespaceAuthorizationRule**</span><span class="sxs-lookup"><span data-stu-id="34c68-285">**Set-AzureRmServiceBusNamespaceAuthorizationRule**</span></span>
- <span data-ttu-id="34c68-286">De cmdlet Set-AzureRmServiceBusNamespaceAuthorizationRule is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="34c68-286">The 'Set-AzureRmServiceBusNamespaceAuthorizationRule' cmdlet has been removed.</span></span> <span data-ttu-id="34c68-287">Gebruik de cmdlet Set-AzureRmServiceBusAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="34c68-287">Please use the 'Set-AzureRmServiceBusAuthorizationRule' cmdlet.</span></span>

### <a name="type-namespaceattributes"></a><span data-ttu-id="34c68-288">**Type NamespaceAttributes**</span><span class="sxs-lookup"><span data-stu-id="34c68-288">**Type NamespaceAttributes**</span></span>
- <span data-ttu-id="34c68-289">De volgende eigenschappen zijn verwijderd</span><span class="sxs-lookup"><span data-stu-id="34c68-289">The following properties have been removed</span></span>
    - <span data-ttu-id="34c68-290">Ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="34c68-290">Enabled</span></span>
    - <span data-ttu-id="34c68-291">Status</span><span class="sxs-lookup"><span data-stu-id="34c68-291">Status</span></span>
   
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

### <a name="type-queueattribute"></a><span data-ttu-id="34c68-292">**Type QueueAttribute**</span><span class="sxs-lookup"><span data-stu-id="34c68-292">**Type QueueAttribute**</span></span>
- <span data-ttu-id="34c68-293">De volgende eigenschappen zijn gemarkeerd als verouderd:</span><span class="sxs-lookup"><span data-stu-id="34c68-293">The following properties are marked as obsolete:</span></span>
    - <span data-ttu-id="34c68-294">EnableBatchedOperations</span><span class="sxs-lookup"><span data-stu-id="34c68-294">EnableBatchedOperations</span></span>
    - <span data-ttu-id="34c68-295">EntityAvailabilityStatus</span><span class="sxs-lookup"><span data-stu-id="34c68-295">EntityAvailabilityStatus</span></span>
    - <span data-ttu-id="34c68-296">IsAnonymousAccessible</span><span class="sxs-lookup"><span data-stu-id="34c68-296">IsAnonymousAccessible</span></span>
    - <span data-ttu-id="34c68-297">SupportOrdering</span><span class="sxs-lookup"><span data-stu-id="34c68-297">SupportOrdering</span></span>

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
   
### <a name="type-topicattribute"></a><span data-ttu-id="34c68-298">**Type TopicAttribute**</span><span class="sxs-lookup"><span data-stu-id="34c68-298">**Type TopicAttribute**</span></span>
- <span data-ttu-id="34c68-299">De volgende eigenschappen zijn gemarkeerd als verouderd:</span><span class="sxs-lookup"><span data-stu-id="34c68-299">The following properties are marked as obsolete:</span></span>
    - <span data-ttu-id="34c68-300">Locatie</span><span class="sxs-lookup"><span data-stu-id="34c68-300">Location</span></span>
    - <span data-ttu-id="34c68-301">IsExpress</span><span class="sxs-lookup"><span data-stu-id="34c68-301">IsExpress</span></span>
    - <span data-ttu-id="34c68-302">IsAnonymousAccessible</span><span class="sxs-lookup"><span data-stu-id="34c68-302">IsAnonymousAccessible</span></span>
    - <span data-ttu-id="34c68-303">FilteringMessagesBeforePublishing</span><span class="sxs-lookup"><span data-stu-id="34c68-303">FilteringMessagesBeforePublishing</span></span>
    - <span data-ttu-id="34c68-304">EnableSubscriptionPartitioning</span><span class="sxs-lookup"><span data-stu-id="34c68-304">EnableSubscriptionPartitioning</span></span>
    - <span data-ttu-id="34c68-305">EntityAvailabilityStatus</span><span class="sxs-lookup"><span data-stu-id="34c68-305">EntityAvailabilityStatus</span></span>

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
   
### <a name="type-subscriptionattribute"></a><span data-ttu-id="34c68-306">**Type SubscriptionAttribute**</span><span class="sxs-lookup"><span data-stu-id="34c68-306">**Type SubscriptionAttribute**</span></span>
- <span data-ttu-id="34c68-307">De volgende eigenschappen zijn gemarkeerd als verouderd:</span><span class="sxs-lookup"><span data-stu-id="34c68-307">The following properties are marked as obsolete</span></span>
    - <span data-ttu-id="34c68-308">DeadLetteringOnFilterEvaluationExceptions</span><span class="sxs-lookup"><span data-stu-id="34c68-308">DeadLetteringOnFilterEvaluationExceptions</span></span>
    - <span data-ttu-id="34c68-309">EntityAvailabilityStatus</span><span class="sxs-lookup"><span data-stu-id="34c68-309">EntityAvailabilityStatus</span></span>
    - <span data-ttu-id="34c68-310">IsReadOnly</span><span class="sxs-lookup"><span data-stu-id="34c68-310">IsReadOnly</span></span>
    - <span data-ttu-id="34c68-311">Locatie</span><span class="sxs-lookup"><span data-stu-id="34c68-311">Location</span></span>
   
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