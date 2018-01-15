---
title: Azure PowerShell in MacOS en Linux installeren en configureren in MacOS en Linux | Microsoft Docs
description: Azure PowerShell voor het eerst installeren en configureren in MacOS en Linux.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 09/06/2017
ms.openlocfilehash: 2357bb5d71c221a782a297c41e7a6d08cd3f2952
ms.sourcegitcommit: 4ebdeea3c472d94c1aedb10b9d85bf2e76826e83
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2018
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a>Azure PowerShell in MacOS en Linux installeren en configureren in MacOS en Linux

Het is nu mogelijk om PowerShell 6 (bèta) en Azure PowerShell te installeren op niet-Windows-platforms.
Het installatieproces van Azure PowerShell in MacOS en Linux verschilt niet veel van dat voor Windows, maar u dient eerst PowerShell 6 (bèta) te installeren.

> [!NOTE]

> Op dit moment zijn PowerShell 6 (bèta) en Azure PowerShell voor .NET Core beide nog bètaversies.
> De ondersteuning voor deze producten is beperkt. U wordt vriendelijk verzocht Issues aan te maken op GitHub als u problemen of fouten ontdekt.
>
> * [Problemen met PowerShell 6 (bèta)](https://github.com/PowerShell/PowerShell/issues)
> * [Problemen met Azure PowerShell](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-6-beta"></a>Stap 1: PowerShell 6 (bèta) installeren

Het installatieproces voor PowerShell 6 (bèta) is afhankelijk van het gebruikte besturingssysteem.
Het is mogelijk PowerShell 6 (bèta) in Windows te installeren, maar in dit artikel wordt gekeken naar MacOS en Linux. Raadpleeg het artikel over het [installatieproces](./install-azurerm-ps.md) voor Windows, indien u Azure PowerShell in Windows wilt gebruiken.

Om **PowerShell 6** (bèta) te installeren in Linux of MacOS, dient u:

1. PowerShell te downloaden van [GitHub](https://github.com/powershell/powershell#get-powershell), voor uw specifieke besturingssystemen en versie
2. de installatie-instructies te volgen
   - [Linux](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
   - [MacOS](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)

## <a name="step-2-install-azure-powershell-for-net-core"></a>Stap 2: Azure PowerShell voor .NET Core installeren

De PowerShellGet is standaard al geïnstalleerd bij PowerShell 6 (bèta). Hierdoor kunt u eenvoudig iedere module installeren die is gepubliceerd naar de PowerShell Gallery. Om Azure PowerShell te installeren, opent u een nieuwe PowerShell-sessie en voert u de volgende opdracht uit:

```powershell
Install-Module AzureRM.NetCore
```

## <a name="step-3-load-the-azurermnetcore-module"></a>Stap 3: de AzureRM.Netcore-module laden

Nadat de module is geïnstalleerd, moet u de module in uw PowerShell-sessie laden. Modules worden geladen door de cmdlet `Import-Module` als volgt te gebruiken:

```powershell
Import-Module AzureRM.Netcore
Import-Module AzureRM.Profile.Netcore
```

Nadat het importeren is voltooid, kunt u uw geïnstalleerde module testen door u bij Azure aan te melden met de volgende opdracht:

```powershell
Login-AzureRMAccount
```

De bovenstaande opdracht zou u naar `https://aka.ms/devicelogin` moeten leiden om de opgegeven code in te voeren.

## <a name="available-cmdlets"></a>Beschikbare cmdlets

De Azure PowerShell-modules voor .NET Standard zijn nog in ontwikkeling. Deze modules bieden niet de volledige set cmdlets die beschikbaar is voor de Windows-versie van de modules. De volgende functies zijn geïmplementeerd in AzureRM.Netcore-modules:

* Accountbeheer
  - Meld u aan met een Microsoft-account, organisatie-account of service-principal via Microsoft Azure Active Directory
  - Sla referenties op schijf op met Save-AzureRmContext en laad opgeslagen referenties met Import-AzureRmContext
* Omgeving
  - Verkrijg de verschillende kant-en-klare omgevingen voor Microsoft Azure
  - Aangepaste omgevingen toevoegen/instellen/verwijderen (zoals uw Azure Stack- of Windows Azure Pack-omgevingen)
* Cmdlets voor beheer van Azure-services met behulp van Resource Manager- en Service Management-interfaces.
  - Virtuele machine
  - App Service (Websites)
  - SQL Database
  - Storage
  - Netwerk

## <a name="next-steps"></a>Volgende stappen

Raadpleeg voor meer informatie over het gebruik van Azure PowerShell het artikel [Aan de slag met Azure PowerShell](get-started-azureps.md).
