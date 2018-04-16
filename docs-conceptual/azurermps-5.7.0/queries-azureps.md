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
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="querying-for-azure-resources"></a>Query's uitvoeren op Azure-resources

In PowerShell kunnen query's worden uitgevoerd met behulp van ingebouwde cmdlets. De namen van de cmdlets in PowerShell hebben de indeling **_werkwoord-zelfstandig naamwoord_**. De cmdlets met het werkwoord **_Get_** zijn de query-cmdlets. De zelfstandige naamwoorden in de namen van de cmdlets zijn de soorten Azure-resources waarop de werkwoorden van de cmdlets hun bewerkingen uitvoeren.


## <a name="selecting-simple-properties"></a>Eenvoudige eigenschappen selecteren

In Azure PowerShell is voor elke cmdlet een standaardopmaak gedefinieerd. De meest algemene eigenschappen voor elk resourcetype worden automatisch weergegeven in een tabel- of lijstweergave. Zie [Queryresultaten opmaken](formatting-output.md) voor meer informatie over het opmaken van uitvoer.

Gebruik de cmdlet `Get-AzureRmVM` om een query uit te voeren op een lijst met virtuele machines in uw account.

```powershell
Get-AzureRmVM
```

De standaarduitvoer wordt automatisch opgemaakt als een tabel.

```
ResourceGroupName          Name   Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----   --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610 westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```

De cmdlet `Select-Object` kan worden gebruikt om de specifieke eigenschappen te selecteren die voor u interessant zijn.

```powershell
Get-AzureRmVM | Select Name,ResourceGroupName,Location
```

```
Name          ResourceGroupName Location
----          ----------------- --------
MyUnbuntu1610 MYWESTEURG        westeurope
MyWin2016VM   MYWESTEURG        westeurope
```

## <a name="selecting-complex-nested-properties"></a>Complexe geneste eigenschappen selecteren

Als de eigenschap die u wilt selecteren, diep is genest in de JSON-uitvoer, moet u het volledige pad naar die geneste eigenschap opgeven. Het volgende voorbeeld laat zien hoe de VM-naam en het besturingssysteemtype voor de cmdlet `Get-AzureRmVM` kunnen worden geselecteerd.

```powershell
Get-AzureRmVM | Select Name,@{Name='OSType'; Expression={$_.StorageProfile.OSDisk.OSType}}
```

```
Name           OSType
----           ------
MyUnbuntu1610   Linux
MyWin2016VM   Windows
```

## <a name="filter-result-using-the-where-object-cmdlet"></a>Filterresultaat van de cmdlet Where-Object

Met de cmdlet `Where-Object` kunt u het resultaat op basis van een eigenschapswaarde filteren. In het volgende voorbeeld worden met het filter alleen de virtuele machines geselecteerd die de tekst 'RGD' in hun naam hebben.

```powershell
Get-AzureRmVM | Where ResourceGroupName -like RGD* | Select ResourceGroupName,Name
```

```
ResourceGroupName  Name
-----------------  ----
RGDEMO001          KBDemo001VM
RGDEMO001          KBDemo020
```

In het volgende voorbeeld worden als resultaat de virtuele machines geretourneerd die als vmSize 'Standard_DS1_V2' hebben.

```powershell
Get-AzureRmVM | Where vmSize -eq Standard_DS1_V2
```

```
ResourceGroupName          Name     Location          VmSize  OsType              NIC ProvisioningState
-----------------          ----     --------          ------  ------              --- -----------------
MYWESTEURG        MyUnbuntu1610   westeurope Standard_DS1_v2   Linux myunbuntu1610980         Succeeded
MYWESTEURG          MyWin2016VM   westeurope Standard_DS1_v2 Windows   mywin2016vm880         Succeeded
```
