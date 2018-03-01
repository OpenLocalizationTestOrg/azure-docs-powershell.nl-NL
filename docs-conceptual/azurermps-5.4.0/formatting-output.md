---
title: Queryresultaten opmaken| Microsoft Docs
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
ms.openlocfilehash: 916cf8590de89762bade4f01ce5a502383d51796
ms.sourcegitcommit: 5fe9a579d2e0d1cb5a05aadaeba5db784f1b18fa
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/28/2018
---
# <a name="formatting-query-results"></a><span data-ttu-id="8f05c-103">Queryresultaten opmaken</span><span class="sxs-lookup"><span data-stu-id="8f05c-103">Formatting query results</span></span>

<span data-ttu-id="8f05c-104">Standaard heeft de uitvoer van elke PowerShell-cmdlet een voorgedefinieerde opmaak, zodat deze gemakkelijk leesbaar is.</span><span class="sxs-lookup"><span data-stu-id="8f05c-104">By default each PowerShell cmdlet has predefined formatting of output making it easy to read.</span></span>  <span data-ttu-id="8f05c-105">PowerShell biedt ook de flexibiliteit om de uitvoer aan te passen of de uitvoer van de cmdlet te converteren naar een andere opmaak met de volgende cmdlets:</span><span class="sxs-lookup"><span data-stu-id="8f05c-105">PowerShell also provides the flexibility to adjust the output or convert the cmdlet output to a different format with the following cmdlets:</span></span>

| <span data-ttu-id="8f05c-106">Opmaak</span><span class="sxs-lookup"><span data-stu-id="8f05c-106">Formatting</span></span>      | <span data-ttu-id="8f05c-107">Conversie</span><span class="sxs-lookup"><span data-stu-id="8f05c-107">Conversion</span></span>       |
|-----------------|------------------|
| `Format-Custom` | `ConvertTo-Csv`  |
| `Format-List`   | `ConvertTo-Html` |
| `Format-Table`  | `ConvertTo-Json` |
| `Format-Wide`   | `ConvertTo-Xml`  |

## <a name="formatting-examples"></a><span data-ttu-id="8f05c-108">Voorbeelden van opmaak</span><span class="sxs-lookup"><span data-stu-id="8f05c-108">Formatting examples</span></span>

<span data-ttu-id="8f05c-109">In dit voorbeeld halen we een lijst met virtuele Azure-machines in ons standaardabonnement op.</span><span class="sxs-lookup"><span data-stu-id="8f05c-109">In this example we get a list of Azure VMs in our default subscription.</span></span>  <span data-ttu-id="8f05c-110">Met de opdracht Get-AzureRmVM wordt uitvoer standaard als een tabel opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="8f05c-110">The Get-AzureRmVM command defaults output into a table format.</span></span>

```powershell
Get-AzureRmVM
```

```
ResourceGroupName          Name   Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----   --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610 westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```

<span data-ttu-id="8f05c-111">Als u het aantal kolommen wilt beperken dat wordt geretourneerd, kunt u de cmdlet `Format-Table` gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8f05c-111">If you would like to limit the columns returned you can use the `Format-Table` cmdlet.</span></span> <span data-ttu-id="8f05c-112">In het volgende voorbeeld krijgen we dezelfde lijst met virtuele machines te zien, maar wordt de uitvoer beperkt tot alleen de naam van de virtuele machine, de resourcegroep en de locatie van de virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="8f05c-112">In the following example we get the same list of virtual machines but restrict the output to just the name of the VM, the resource group, and the location of the VM.</span></span>  <span data-ttu-id="8f05c-113">Met de parameter `-Autosize` wordt de grootte van de kolommen aangepast op basis van de grootte van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="8f05c-113">The `-Autosize` parameter sizes the columns according to the size of the data.</span></span>

```powershell
Get-AzureRmVM | Format-Table Name,ResourceGroupName,Location -AutoSize
```

```
Name          ResourceGroupName Location
----          ----------------- --------
MyUnbuntu1610 MYWESTEURG        westeurope
MyWin2016VM   MYWESTEURG        westeurope
```

<span data-ttu-id="8f05c-114">U kunt de gegevens ook in de vorm van een lijst bekijken als u daar de voorkeur aan geeft.</span><span class="sxs-lookup"><span data-stu-id="8f05c-114">If you would prefer you can view information in a list format.</span></span> <span data-ttu-id="8f05c-115">Het volgende voorbeeld laat dit zien met behulp van de cmdlet `Format-List`.</span><span class="sxs-lookup"><span data-stu-id="8f05c-115">The following example shows this using the`Format-List` cmdlet.</span></span>

```powershell
Get-AzureRmVM | Format-List Name,VmId,Location,ResourceGroupName
```

```
Name              : MyUnbuntu1610
VmId              : 33422f9b-e339-4704-bad8-dbe094585496
Location          : westeurope
ResourceGroupName : MYWESTEURG

Name              : MyWin2016VM
VmId              : 4650c755-fc2b-4fc7-a5bc-298d5c00808f
Location          : westeurope
ResourceGroupName : MYWESTEURG
```

## <a name="converting-to-other-data-types"></a><span data-ttu-id="8f05c-116">Converteren naar andere gegevenstypen</span><span class="sxs-lookup"><span data-stu-id="8f05c-116">Converting to other data types</span></span>

<span data-ttu-id="8f05c-117">PowerShell biedt ook de mogelijkheid uitvoer op meerdere manieren op te maken, overeenkomstig uw behoeften.</span><span class="sxs-lookup"><span data-stu-id="8f05c-117">PowerShell also offers multiple output format you can use to meet your needs.</span></span>  <span data-ttu-id="8f05c-118">In het volgende voorbeeld gebruiken we de cmdlet `Select-Object` om kenmerken van de virtuele machines in ons abonnement op te halen en wordt de uitvoer geconverteerd naar een CSV-indeling, zodat deze eenvoudig in een database of spreadsheet kan worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="8f05c-118">In the following example we use the `Select-Object` cmdlet to get attributes of the virtual machines in our subscription and and convert the output to CSV format for easy import into a database or spreadsheet.</span></span>

```powershell
Get-AzureRmVM | Select-Object ResourceGroupName,Id,VmId,Name,Location,ProvisioningState | ConvertTo-Csv -NoTypeInformation
```

```
"ResourceGroupName","Id","VmId","Name","Location","ProvisioningState"
"MYWESTUERG","/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTUERG/providers/Microsoft.Compute/virtualMachines/MyUnbuntu1610","33422f9b-e339-4704-bad8-dbe094585496","MyUnbuntu1610","westeurope","Succeeded"
"MYWESTUERG","/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTUERG/providers/Microsoft.Compute/virtualMachines/MyWin2016VM","4650c755-fc2b-4fc7-a5bc-298d5c00808f","MyWin2016VM","westeurope","Succeeded"
```

<span data-ttu-id="8f05c-119">U kunt de uitvoer ook naar een JSON-indeling converteren.</span><span class="sxs-lookup"><span data-stu-id="8f05c-119">You can also convert the output into JSON format.</span></span>  <span data-ttu-id="8f05c-120">In het volgende voorbeeld wordt dezelfde lijst met virtuele machines gemaakt, maar wordt voor de uitvoer de indeling in JSON gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8f05c-120">The following example creates the same list of VMs but changes the output format to JSON.</span></span>

```powershell
Get-AzureRmVM | Select-Object ResourceGroupName,Id,VmId,Name,Location,ProvisioningState | ConvertTo-Json
```

```
[
    {
        "ResourceGroupName":  "MYWESTEURG",
        "Id":  "/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTEURG/providers/Microsoft.Compute/virtualMachines/MyUnbuntu1610",
        "VmId":  "33422f9b-e339-4704-bad8-dbe094585496",
        "Name":  "MyUnbuntu1610",
        "Location":  "westeurope",
        "ProvisioningState":  "Succeeded"
    },
    {
        "ResourceGroupName":  "MYWESTEURG",
        "Id":  "/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/MYWESTEURG/providers/Microsoft.Compute/virtualMachines/MyWin2016VM",
        "VmId":  "4650c755-fc2b-4fc7-a5bc-298d5c00808f",
        "Name":  "MyWin2016VM",
        "Location":  "westeurope",
        "ProvisioningState":  "Succeeded"
    }
]
```
