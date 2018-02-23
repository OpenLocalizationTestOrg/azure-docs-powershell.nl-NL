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
ms.date: 01/12/2018
ms.openlocfilehash: 64a86dfd4af7f3f0a91501e9a096ff190f7100cb
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2018
---
# <a name="install-and-configure-azure-powershell-on-macos-and-linux"></a>Azure PowerShell in MacOS en Linux installeren en configureren in MacOS en Linux

Het is nu mogelijk om PowerShell Core v6 en Azure PowerShell te installeren op niet-Windows-platforms.
Het installatieproces van Azure PowerShell in macOS en Linux verschilt niet veel van dat voor Windows, maar u moet wel eerst PowerShell Core v6 installeren.

> [!NOTE]

> Op dit moment zijn PowerShell Core v6 en Azure PowerShell voor .NET Core beide nog bètaversies.
> De ondersteuning voor deze producten is beperkt. U wordt vriendelijk verzocht Issues aan te maken op GitHub als u problemen of fouten ontdekt.
>
> * [Problemen met PowerShell Core v6](https://github.com/PowerShell/PowerShell/issues)
> * [Problemen met Azure PowerShell](https://github.com/azure/azure-docs-powershell/issues)

## <a name="step-1-install-powershell-core-v6"></a>Stap 1: PowerShell Core v6 installeren

Het installatieproces voor PowerShell Core v6 is afhankelijk van het gebruikte besturingssysteem.
Het is mogelijk PowerShell Core v6 in Windows te installeren, maar in dit artikel wordt gekeken naar macOS en Linux. Raadpleeg het artikel over het [installatieproces](./install-azurerm-ps.md) voor Windows, indien u Azure PowerShell in Windows wilt gebruiken.

Het installatieproces voor **PowerShell Core v6** in Linux of Mac OS kan verschillen, afhankelijk van de Linux-distributie en de versie van het besturingssysteem.
Gedetailleerde instructies vindt u in het volgende artikel:

- [Installing PowerShell Core on macOS and Linux](/powershell/scripting/setup/installing-powershell-core-on-macos-and-linux) (PowerShell Core installeren in macOS en Linux)

## <a name="step-2-install-azure-powershell-for-net-core"></a>Stap 2: Azure PowerShell voor .NET Core installeren

De PowerShellGet-module is standaard al geïnstalleerd in PowerShell Core v6. Hierdoor kunt u eenvoudig iedere module installeren die is gepubliceerd naar de PowerShell Gallery. Om Azure PowerShell te installeren, opent u een nieuwe PowerShell-sessie en voert u de volgende opdracht uit:

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
