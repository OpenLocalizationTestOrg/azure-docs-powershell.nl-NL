---
title: Query's uitvoeren op Azure-resources en resultaten opmaken | Microsoft Docs
description: Query's uitvoeren op Azure-resources en resultaten opmaken.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/30/2017
ms.openlocfilehash: 93a031ce90352286bb1a5e01dc65e6db7cbe5c7e
ms.sourcegitcommit: be8389f126196e50b513f26c296e08a59601ecc6
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/28/2017
---
# <a name="querying-for-azure-resources"></a><span data-ttu-id="e6451-103">Query's uitvoeren op Azure-resources</span><span class="sxs-lookup"><span data-stu-id="e6451-103">Querying for Azure resources</span></span>

<span data-ttu-id="e6451-104">In PowerShell kunnen query's worden uitgevoerd met behulp van ingebouwde cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e6451-104">Querying in PowerShell can be completed by using built-in cmdlets.</span></span> <span data-ttu-id="e6451-105">De namen van de cmdlets in PowerShell hebben de indeling **_werkwoord-zelfstandig naamwoord_**.</span><span class="sxs-lookup"><span data-stu-id="e6451-105">In PowerShell, cmdlet names take the form of **_Verb-Noun_**.</span></span> <span data-ttu-id="e6451-106">De cmdlets met het werkwoord **_Get_** zijn de query-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e6451-106">The cmdlets using the verb **_Get_** are the query cmdlets.</span></span> <span data-ttu-id="e6451-107">De zelfstandige naamwoorden in de namen van de cmdlets zijn de soorten Azure-resources waarop de werkwoorden van de cmdlets hun bewerkingen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e6451-107">The cmdlet nouns are the types of Azure resources that are acted upon by the cmdlet verbs.</span></span>


## <a name="selecting-simple-properties"></a><span data-ttu-id="e6451-108">Eenvoudige eigenschappen selecteren</span><span class="sxs-lookup"><span data-stu-id="e6451-108">Selecting simple properties</span></span>

<span data-ttu-id="e6451-109">In Azure PowerShell is voor elke cmdlet een standaardopmaak gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e6451-109">Azure PowerShell has default formatting defined for each cmdlet.</span></span> <span data-ttu-id="e6451-110">De meest algemene eigenschappen voor elk resourcetype worden automatisch weergegeven in een tabel- of lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="e6451-110">The most common properties for each resource type are displayed in a table or list format automatically.</span></span> <span data-ttu-id="e6451-111">Zie [Queryresultaten opmaken](formatting-output.md) voor meer informatie over het opmaken van uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e6451-111">For more information about formatting output, see [Formatting query results](formatting-output.md).</span></span>

<span data-ttu-id="e6451-112">Gebruik de cmdlet `Get-AzureRmVM` om een query uit te voeren op een lijst met virtuele machines in uw account.</span><span class="sxs-lookup"><span data-stu-id="e6451-112">Use the `Get-AzureRmVM` cmdlet to query for a list of VMs in your account.</span></span>

```powershell
Get-AzureRmVM
```

<span data-ttu-id="e6451-113">De standaarduitvoer wordt automatisch opgemaakt als een tabel.</span><span class="sxs-lookup"><span data-stu-id="e6451-113">The default output is automatically formatted as a table.</span></span>

```
ResourceGroupName          Name   Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----   --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610 westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```

<span data-ttu-id="e6451-114">De cmdlet `Select-Object` kan worden gebruikt om de specifieke eigenschappen te selecteren die voor u interessant zijn.</span><span class="sxs-lookup"><span data-stu-id="e6451-114">The `Select-Object` cmdlet can be used to select the specific properties that are interesting to you.</span></span>

```powershell
Get-AzureRmVM | Select Name,ResourceGroupName,Location
```

```
Name          ResourceGroupName Location
----          ----------------- --------
MyUnbuntu1610 MYWESTEURG        westeurope
MyWin2016VM   MYWESTEURG        westeurope
```

## <a name="selecting-complex-nested-properties"></a><span data-ttu-id="e6451-115">Complexe geneste eigenschappen selecteren</span><span class="sxs-lookup"><span data-stu-id="e6451-115">Selecting complex nested properties</span></span>

<span data-ttu-id="e6451-116">Als de eigenschap die u wilt selecteren, diep is genest in de JSON-uitvoer, moet u het volledige pad naar die geneste eigenschap opgeven.</span><span class="sxs-lookup"><span data-stu-id="e6451-116">If the property you want to select is nested deep in the JSON output you need to supply the full path to that nested property.</span></span> <span data-ttu-id="e6451-117">Het volgende voorbeeld laat zien hoe de VM-naam en het besturingssysteemtype voor de cmdlet `Get-AzureRmVM` kunnen worden geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="e6451-117">The following example shows how to select the VM Name and the OS type from the `Get-AzureRmVM` cmdlet.</span></span>

```powershell
Get-AzureRmVM | Select Name,@{Name='OSType'; Expression={$_.StorageProfile.OSDisk.OSType}}
```

```
Name           OSType
----           ------
MyUnbuntu1610   Linux
MyWin2016VM   Windows
```

## <a name="filter-result-using-the-where-object-cmdlet"></a><span data-ttu-id="e6451-118">Filterresultaat van de cmdlet Where-Object</span><span class="sxs-lookup"><span data-stu-id="e6451-118">Filter result using the Where-Object cmdlet</span></span>

<span data-ttu-id="e6451-119">Met de cmdlet `Where-Object` kunt u het resultaat op basis van een eigenschapswaarde filteren.</span><span class="sxs-lookup"><span data-stu-id="e6451-119">The `Where-Object` cmdlet allows you to filter the result based on any property value.</span></span> <span data-ttu-id="e6451-120">In het volgende voorbeeld worden met het filter alleen de virtuele machines geselecteerd die de tekst 'RGD' in hun naam hebben.</span><span class="sxs-lookup"><span data-stu-id="e6451-120">In the following example, the filter selects only VMs that have the text "RGD" in their name.</span></span>

```powershell
Get-AzureRmVM | Where ResourceGroupName -like RGD* | Select ResourceGroupName,Name
```

```
ResourceGroupName  Name
-----------------  ----
RGDEMO001          KBDemo001VM
RGDEMO001          KBDemo020
```

<span data-ttu-id="e6451-121">In het volgende voorbeeld worden als resultaat de virtuele machines geretourneerd die als vmSize 'Standard_DS1_V2' hebben.</span><span class="sxs-lookup"><span data-stu-id="e6451-121">With the next example, the results will return the VMs that have the vmSize 'Standard_DS1_V2'.</span></span>

```powershell
Get-AzureRmVM | Where vmSize -eq Standard_DS1_V2
```

```
ResourceGroupName          Name     Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----     --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610   westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM   westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```
