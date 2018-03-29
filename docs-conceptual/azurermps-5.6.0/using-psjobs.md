---
title: Cmdlets gelijktijdig uitvoeren met behulp van PowerShell-taken
description: Leer hoe u cmdlets gelijktijdig uitvoert met de parameter -AsJob.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 12/11/2017
ms.openlocfilehash: 0a445a7db84c8deb6518b826b4096983669c5961
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="running-cmdlets-in-parallel-using-powershell-jobs"></a><span data-ttu-id="1bf91-103">Cmdlets gelijktijdig uitvoeren met behulp van PowerShell-taken</span><span class="sxs-lookup"><span data-stu-id="1bf91-103">Running cmdlets in parallel using PowerShell jobs</span></span>

<span data-ttu-id="1bf91-104">PowerShell ondersteunt asynchrone bewerkingen met [PowerShell-taken](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="1bf91-104">PowerShell supports asynchronous action with [PowerShell Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>
<span data-ttu-id="1bf91-105">Azure PowerShell is sterk afhankelijk van het uitvoeren van en wachten op netwerkaanroepen naar Azure.</span><span class="sxs-lookup"><span data-stu-id="1bf91-105">Azure PowerShell is heavily dependent on making, and waiting for, network calls to Azure.</span></span> <span data-ttu-id="1bf91-106">Als ontwikkelaar hebt u er waarschijnlijk regelmatig behoefte aan om meerdere niet-blokkerende aanroepen naar Azure op te nemen in een script of om Azure-resources te maken in de REPL zonder de huidige sessie te blokkeren.</span><span class="sxs-lookup"><span data-stu-id="1bf91-106">As a developer, you may often find yourself looking to make multiple non-blocking calls to Azure in a script, or you may find that you want to create Azure resources in the REPL without blocking the current session.</span></span> <span data-ttu-id="1bf91-107">Om in deze behoeften te voorzien, biedt Azure PowerShell uitstekende ondersteuning voor [PSJob](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="1bf91-107">To address these needs, Azure PowerShell provides first-class [PSJob](/powershell/module/microsoft.powershell.core/about/about_jobs) support.</span></span>

## <a name="context-persistence-and-psjobs"></a><span data-ttu-id="1bf91-108">Contextpersistentie en PSJobs</span><span class="sxs-lookup"><span data-stu-id="1bf91-108">Context Persistence and PSJobs</span></span>

<span data-ttu-id="1bf91-109">PSJobs worden in afzonderlijke processen uitgevoerd, wat betekent dat de gegevens van uw Azure-verbinding op correcte wijze moeten worden gedeeld met de taken die u maakt.</span><span class="sxs-lookup"><span data-stu-id="1bf91-109">PSJobs are run in separate processes, which means that information about your Azure connection must be properly shared with the jobs you create.</span></span> <span data-ttu-id="1bf91-110">Nadat u uw Azure-account met `Login-AzureRmAccount` aan uw PowerShell-sessie hebt gekoppeld, kunt u de context doorgeven aan een taak.</span><span class="sxs-lookup"><span data-stu-id="1bf91-110">Upon connecting your Azure account to your PowerShell session with `Login-AzureRmAccount`, you can pass the context to a job.</span></span>

```powershell
$creds = Get-Credential
$job = Start-Job { param($context,$vmadmin) New-AzureRmVM -Name MyVm -AzureRmContext $context -Credential $vmadmin} -Arguments (Get-AzureRmContext),$creds
```

<span data-ttu-id="1bf91-111">Als u er echter voor hebt gekozen om de context automatisch op te slaan met `Enable-AzureRmContextAutosave`, wordt de context automatisch gedeeld met alle taken die u maakt.</span><span class="sxs-lookup"><span data-stu-id="1bf91-111">However, if you have chosen to have your context automatically saved with `Enable-AzureRmContextAutosave`, the context is automatically shared with any jobs you create.</span></span>

```powershell
Enable-AzureRmContextAutosave
$creds = Get-Credential
$job = Start-Job { param($vmadmin) New-AzureRmVM -Name MyVm -Credential $vmadmin} -Arguments $creds
```

## <a name="automatic-jobs-with--asjob"></a><span data-ttu-id="1bf91-112">Automatische taken met `-AsJob`</span><span class="sxs-lookup"><span data-stu-id="1bf91-112">Automatic Jobs with `-AsJob`</span></span>

<span data-ttu-id="1bf91-113">Voor uw gemak biedt Azure PowerShell ook een `-AsJob`-schakelaar voor enkele cmdlets met lange uitvoeringstijd.</span><span class="sxs-lookup"><span data-stu-id="1bf91-113">As a convenience, Azure PowerShell also provides an `-AsJob` switch on some long-running cmdlets.</span></span>
<span data-ttu-id="1bf91-114">De `-AsJob`-switch maakt het nog gemakkelijker om PSJobs te maken.</span><span class="sxs-lookup"><span data-stu-id="1bf91-114">The `-AsJob` switch makes creating PSJobs even easier.</span></span>

```powershell
$creds = Get-Credential
$job = New-AzureRmVM -Name MyVm -Credential $creds -AsJob
```

<span data-ttu-id="1bf91-115">U kunt de taak en de voortgang op elk gewenst moment inspecteren met `Get-Job` en `Get-AzureRmVM`.</span><span class="sxs-lookup"><span data-stu-id="1bf91-115">You can inspect the job and progress at any time with `Get-Job` and `Get-AzureRmVM`.</span></span>

```powershell
Get-Job $job
Get-AzureRmVM MyVm
```

```Output
Id Name                                       PSJobTypeName         State   HasMoreData Location  Command
-- ----                                       -------------         -----   ----------- --------  -------
1  Long Running Operation for 'New-AzureRmVM' AzureLongRunningJob`1 Running True        localhost New-AzureRmVM

ResourceGroupName    Name Location          VmSize  OsType     NIC ProvisioningState Zone
-----------------    ---- --------          ------  ------     --- ----------------- ----
MyVm                 MyVm   eastus Standard_DS1_v2 Windows    MyVm          Creating
```

<span data-ttu-id="1bf91-116">Na voltooiing van de taak kunt u het resultaat hiervan met `Receive-Job` opvragen.</span><span class="sxs-lookup"><span data-stu-id="1bf91-116">Subsequently, upon completion, you can obtain the result of the job with `Receive-Job`.</span></span>

> [!NOTE]
> <span data-ttu-id="1bf91-117">`Receive-Job` retourneert het resultaat van de cmdlet alsof de `-AsJob`-vlag niet aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="1bf91-117">`Receive-Job` returns the result from the cmdlet as if the `-AsJob` flag were not present.</span></span>
> <span data-ttu-id="1bf91-118">Het `Receive-Job`-resultaat van `Do-Action -AsJob` is bijvoorbeeld van hetzelfde type als het resultaat van `Do-Action`.</span><span class="sxs-lookup"><span data-stu-id="1bf91-118">For example, the `Receive-Job` result of `Do-Action -AsJob` is of the same type as the result of `Do-Action`.</span></span>

```powershell
$vm = Receive-Job $job
$vm
```

```Output
ResourceGroupName        : MyVm
Id                       : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MyVm/providers/Microsoft.Compute/virtualMachines/MyVm
VmId                     : dff1f79e-a8f7-4664-ab72-0ec28b9fbb5b
Name                     : MyVm
Type                     : Microsoft.Compute/virtualMachines
Location                 : eastus
Tags                     : {}
HardwareProfile          : {VmSize}
NetworkProfile           : {NetworkInterfaces}
OSProfile                : {ComputerName, AdminUsername, WindowsConfiguration, Secrets}
ProvisioningState        : Succeeded
StorageProfile           : {ImageReference, OsDisk, DataDisks}
FullyQualifiedDomainName : myvmmyvm.eastus.cloudapp.azure.com
```

## <a name="example-scenarios"></a><span data-ttu-id="1bf91-119">Voorbeeldscenario's</span><span class="sxs-lookup"><span data-stu-id="1bf91-119">Example Scenarios</span></span>

<span data-ttu-id="1bf91-120">Maak meerdere virtuele machines tegelijk.</span><span class="sxs-lookup"><span data-stu-id="1bf91-120">Create multiple VMs at once.</span></span>

```powershell
$creds = Get-Credential
# Create 10 jobs.
for($k = 0; $k -lt 10; $k++) {
    New-AzureRmVm -Name MyVm$k  -Credential $creds -AsJob
}

# Get all jobs and wait on them.
Get-Job | Wait-Job
"All jobs completed"
Get-AzureRmVM
```

<span data-ttu-id="1bf91-121">In dit voorbeeld zorgt de cmdlet `Wait-Job` ervoor dat het script wordt onderbroken terwijl er taken worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1bf91-121">In this example, the `Wait-Job` cmdlet causes the script to pause while jobs run.</span></span> <span data-ttu-id="1bf91-122">De uitvoering van het script wordt hervat nadat alle taken zijn voltooid.</span><span class="sxs-lookup"><span data-stu-id="1bf91-122">The script continues executing once all of the jobs have completed.</span></span> <span data-ttu-id="1bf91-123">Op deze manier kunt u meerdere taken tegelijkertijd uitvoeren en wachten op voltooiing voordat u doorgaat.</span><span class="sxs-lookup"><span data-stu-id="1bf91-123">This allows you to create several jobs running in parallel then wait for completion before continuing.</span></span>

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
3      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
4      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
5      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
6      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
7      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
8      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
9      Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
10     Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
11     Long Running... AzureLongRun... Running       True            localhost            New-AzureRmVM
2      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
3      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
4      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
5      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
6      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
7      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
8      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
9      Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
10     Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
11     Long Running... AzureLongRun... Completed     True            localhost            New-AzureRmVM
All Jobs completed.

ResourceGroupName        Name   Location          VmSize  OsType           NIC ProvisioningState Zone
-----------------        ----   --------          ------  ------           --- ----------------- ----
MYVM                     MyVm     eastus Standard_DS1_v2 Windows          MyVm         Succeeded
MYVM0                   MyVm0     eastus Standard_DS1_v2 Windows         MyVm0         Succeeded
MYVM1                   MyVm1     eastus Standard_DS1_v2 Windows         MyVm1         Succeeded
MYVM2                   MyVm2     eastus Standard_DS1_v2 Windows         MyVm2         Succeeded
MYVM3                   MyVm3     eastus Standard_DS1_v2 Windows         MyVm3         Succeeded
MYVM4                   MyVm4     eastus Standard_DS1_v2 Windows         MyVm4         Succeeded
MYVM5                   MyVm5     eastus Standard_DS1_v2 Windows         MyVm5         Succeeded
MYVM6                   MyVm6     eastus Standard_DS1_v2 Windows         MyVm6         Succeeded
MYVM7                   MyVm7     eastus Standard_DS1_v2 Windows         MyVm7         Succeeded
MYVM8                   MyVm8     eastus Standard_DS1_v2 Windows         MyVm8         Succeeded
MYVM9                   MyVm9     eastus Standard_DS1_v2 Windows         MyVm9         Succeeded
```
