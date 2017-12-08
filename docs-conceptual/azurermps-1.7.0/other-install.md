---
title: Andere manieren om Azure PowerShell te installeren | Microsoft Docs
description: Azure PowerShell installeren met het MSI-pakket of het webplatforminstallatieprogramma.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 09/06/2017
ms.openlocfilehash: 73c099375cecc8abdd5d6179109513946e7e793b
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2017
---
# <a name="other-installation-methods"></a>Andere installatiemethoden

Azure PowerShell kent meerdere installatiemethoden. Het gebruik van PowerShellGet met PowerShell Gallery verdient de voorkeur. Azure PowerShell kan in Windows worden geïnstalleerd met het webplatforminstallatieprogramma (WebPI) of met het MSI-bestand dat beschikbaar is via GitHub. Azure PowerShell kan ook worden geïnstalleerd in een Docker-container.

## <a name="install-on-windows-using-the-web-platform-installer"></a>In Windows installeren met het webplatforminstallatieprogramma

Het installeren van de nieuwste versie van Azure PowerShell met WebPI gaat op dezelfde manier als bij vorige versies.
Download het [Azure PowerShell WebPI-pakket](http://aka.ms/webpi-azps) en start de installatie.

> [!NOTE]
> Als u eerder Azure-modules hebt geïnstalleerd vanuit PowerShell Gallery, worden deze automatisch door het installatieprogramma verwijderd. Dit maakt uw omgeving eenvoudiger door ervoor te zorgen dat er slechts één versie van Azure PowerShell is geïnstalleerd. Er zijn echter scenario's denkbaar waarin het gewenst is dat er meerdere versies tegelijkertijd zijn geïnstalleerd.
>
> Met PowerShell Gallery-modules worden modules geïnstalleerd in `$env:ProgramFiles\WindowsPowerShell\Modules`. Met het WebPI-installatieprogramma worden daarentegen Azure-modules geïnstalleerd in `$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\`.
>
> Als er tijdens de installatie een fout optreedt, kunt u handmatig de Azure*-mappen in de map `$env:ProgramFiles\WindowsPowerShell\Modules` verwijderen en de installatie opnieuw uitvoeren.

Nadat de installatie is voltooid, moet uw instelling `$env:PSModulePath` de mappen bevatten waarin zich de Azure PowerShell-cmdlets bevinden. De volgende opdracht kan worden gebruikt om te controleren of Azure PowerShell juist is geïnstalleerd.

```powershell
# To make sure the Azure PowerShell module is available after you install
Get-Module -ListAvailable Azure* | Select-Object Name, Version, Path
```

> [!NOTE]
> Er is een bekend probleem dat zich kan voordoen bij het installeren met WebPI. Als de computer opnieuw moet worden opgestart vanwege systeemupdates of andere installaties, kan dit ertoe leiden dat tijdens het bijwerken van `$env:PSModulePath` het pad waar Azure PowerShell is geïnstalleerd, niet kan worden opgenomen.

Wanneer u na een installatie cmdlets laadt of uitvoert, kunt u het volgende foutbericht ontvangen:

```
PS C:\> Login-AzureRmAccount
Login-AzureRmAccount : The term 'Login-AzureRmAccount' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:1
+ Login-AzureRmAccount
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Login-AzureRmAccount:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Deze fout kan worden gecorrigeerd door de machine opnieuw op te starten of door de module te importeren en daarbij het volledig pad te gebruiken. Bijvoorbeeld:

```powershell
Import-Module "$env:ProgramFiles(x86)\Microsoft SDKs\Azure\PowerShell\AzureRM.psd1"
```

## <a name="install-on-windows-using-the-msi-package"></a>In Windows installeren met het MSI-pakket

Azure PowerShell kan worden geïnstalleerd met het MSI-bestand dat beschikbaar is via [GitHub](https://github.com/Azure/azure-powershell/releases/latest). Als u vorige versies van Azure-modules hebt geïnstalleerd, worden deze automatisch door het installatieprogramma verwijderd. Met het MSI-pakket worden er modules in `$env:ProgramFiles\WindowsPowerShell\Modules` geïnstalleerd, maar worden er geen mappen voor specifieke versies gemaakt.

## <a name="install-in-a-docker-container"></a>Installeren in een Docker-container

We onderhouden een Docker-installatiekopie die vooraf is geconfigureerd met Azure PowerShell.

Voer de container uit met `docker run`.

```powershell
docker run azuresdk/azure-powershell
```

Bovendien onderhouden we een subset cmdlets als een PowerShell Core-container.

Voor Mac/Linux gebruikt u de installatiekopie `latest`.

```bash
docker run azuresdk/azure-powershell-core:latest
```

Voor Windows gebruikt u de installatiekopie `nanoserver`.

```powershell
docker run azuresdk/azure-powershell-core:nanoserver
```

Azure PowerShell wordt geïnstalleerd in de installatiekopie met behulp van `Install-Module` uit de [PowerShell Gallery](https://www.powershellgallery.com/).