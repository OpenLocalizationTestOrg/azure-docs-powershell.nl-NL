---
title: Azure PowerShell installeren en configureren | Microsoft Docs
description: Azure PowerShell voor het eerst installeren en configureren
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 08/31/2017
ms.openlocfilehash: 1a1a2e3d69252c8461284e6ec8e26fa838e773f7
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="install-and-configure-azure-powershell"></a>Azure PowerShell installeren en configureren

In dit artikel worden de stappen beschreven voor het installeren van de Azure PowerShell-modules in een Windows-omgeving.  
Als u Azure PowerShell wilt gebruiken in macOS of Linux, raadpleegt u het volgende artikel:  
[Azure PowerShell in macOS en Linux installeren en configureren](install-azurermps-maclinux.md).

Installatie van Azure PowerShell via PowerShell Gallery heeft de voorkeur.

## <a name="step-1-install-powershellget"></a>Stap 1: PowerShellGet installeren

Als u items uit de PowerShell Gallery wilt installeren, hebt u de PowerShellGet-module nodig. Zorg ervoor dat u de juiste versie van PowerShellGet hebt en ook voldoet aan de overige systeemvereisten. Voer de volgende opdracht uit om na te gaan of PowerShellGet op uw systeem is geïnstalleerd.

```powershell
Get-Module -Name PowerShellGet -ListAvailable | Select-Object -Property Name,Version,Path
```

De uitvoer moet er ongeveer uitzien als hieronder is weergegeven:

```Output
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```
U kunt bovendien PowerShellGet bijwerken met de onderstaande opdracht:
```powershell
Install-Module PowerShellGet -Force
```

Zie de sectie [PowerShellGet ophalen](#how-to-get-powershellget) van dit artikel als PowerShellGet niet is geïnstalleerd.

> [!NOTE]
> Als u PowerShellGet gebruikt, hebt u een uitvoeringsbeleid nodig waarmee u scripts kunt uitvoeren. Zie [About Execution Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies) (Informatie over uitvoeringsbeleid) voor meer informatie over het uitvoeringsbeleid van PowerShell.

## <a name="step-2-install-azure-powershell"></a>Stap 2: Azure PowerShell installeren

Als u Azure PowerShell via de PowerShell Gallery wilt installeren, hebt u verhoogde bevoegdheden nodig. Voer de volgende opdracht uit vanuit een PowerShell-sessie met verhoogde bevoegdheden:

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module -Name AzureRM -AllowClobber
```

PowerShell Gallery is standaard niet geconfigureerd als een vertrouwde opslagplaats voor PowerShellGet. De eerste keer dat u PSGallery gebruikt, ziet u het volgende bericht:

```Output
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
```

Antwoord Ja of Ja op alles om door te gaan met de installatie.

> [!NOTE]
> Als u een versie van NuGet hebt die ouder is dan 2.8.5.201, wordt u gevraagd om de meest recente versie van NuGet te downloaden en installeren.

De AzureRM-module is een updatepakketmodule voor de Azure Resource Manager-cmdlets. Als u de AzureRM-module installeert, wordt een niet eerder geïnstalleerde Azure PowerShell-module gedownload vanuit PowerShell Gallery.

Als er een eerdere versie van Azure PowerShell is geïnstalleerd, kunt u een foutmelding krijgen. Zie de sectie [Bijwerken naar een nieuwe versie van Azure PowerShell](#update-azps) in dit artikel om dit probleem op te lossen.

## <a name="step-3-load-the-azurerm-module"></a>Stap 3: de AzureRM-module laden
Nadat de module is geïnstalleerd, moet u de module in uw PowerShell-sessie laden. Doe dit tijdens een normale (niet-verhoogde) PowerShell-sessie. Modules worden geladen door de cmdlet `Import-Module` als volgt te gebruiken:

```powershell
Import-Module -Name AzureRM
```

## <a name="next-steps"></a>Volgende stappen

Zie de volgende artikelen voor meer informatie over het gebruik van Azure PowerShell:

* [Aan de slag met Azure PowerShell](get-started-azureps.md)

## <a name="reporting-issues-and-feedback"></a>Problemen melden en feedback geven

Als er fouten optreden bij het gebruik van het hulpprogramma, kunt u dit melden via de sectie [Issues](https://github.com/Azure/azure-powershell/issues) van onze GitHub-repo. Als u feedback wilt geven vanaf de opdrachtregel, gebruikt u de cmdlet `Send-Feedback`.

## <a name="frequently-asked-questions"></a>Veelgestelde vragen

### <a name="how-to-get-powershellget"></a>PowerShellGet ophalen

|Scenario|Installatie-instructies|
|---|---|
|Windows 10<br/>Windows Server 2016|Ingebouwd in Windows Management Framework 5.0 (WMF), dat is opgenomen in het besturingssysteem|
|Ik wil een upgrade naar PowerShell 5 uitvoeren|<ol><li>[Installeer de meest recente versie van WMF](https://www.microsoft.com/en-us/download/details.aspx?id=54616)</li><li>Voer de volgende opdracht uit:<br/>```Install-Module PowerShellGet -Force```</li></ol>|
|Ik heb een versie van Windows met PowerShell 3 of PowerShell 4|<ol><il>[Haal de PackageManagement-modules op](http://go.microsoft.com/fwlink/?LinkID=746217)</il><li>Voer de volgende opdracht uit:<br/>```Install-Module PowerShellGet -Force```</li></ol>|

<a id="helpmechoose"></a>
### <a name="checking-the-version-of-azure-powershell"></a>De versie van Azure PowerShell controleren

Hoewel we u aanraden om zo snel mogelijk een upgrade naar de meest recente versie uit te voeren, worden er meerdere versies van Azure PowerShell ondersteund. Voer `Get-Module AzureRM` vanaf de opdrachtregel uit om te bepalen welke versie van Azure PowerShell er op uw systeem is geïnstalleerd.

```powershell
Get-Module AzureRM -ListAvailable | Select-Object -Property Name,Version,Path
```

### <a name="support-for-classic-deployment-methods"></a>Ondersteuning voor klassieke implementatiemethoden

Als u implementaties hebt die het klassieke implementatiemodel volgen, kunt u de Service Management-versie van Azure PowerShell installeren. Zie [Installing the Azure PowerShell Service Management module](/powershell/azure/servicemanagement/install-azure-ps) (De Azure PowerShell Service Management-module installeren) voor meer informatie. De Azure- en AzureRM-modules delen algemene afhankelijkheden. Als u zowel de Azure- als de AzureRM-module gebruikt, moet u dezelfde versie van elk pakket installeren.

### <a id="update-azps"></a>Bijwerken naar een nieuwe versie van Azure PowerShell

Als er een eerdere versie van Azure PowerShell is geïnstalleerd, met de module Service Management, kunt u de volgende foutmelding krijgen:

```Output
PackageManagement\Install-Package : A command with name 'Get-AzureStorageContainerAcl' is already
available on this system. This module 'Azure.Storage' may override the existing commands. If you
still want to install this module 'Azure.Storage', use -AllowClobber parameter.

At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1772 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
    + FullyQualifiedErrorId : CommandAlreadyAvailable,Validate-ModuleCommandAlreadyAvailable,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

Zoals in de foutmelding wordt aangegeven, moet u de parameter -AllowClobber gebruiken om de module te installeren. Gebruik de volgende opdracht:

```powershell
# Install the Azure Resource Manager modules from the PowerShell Gallery
Install-Module -Name AzureRM -AllowClobber
```

Zie het Help-onderwerp voor [Install-Module](https://msdn.microsoft.com/powershell/reference/5.1/PowerShellGet/install-module) voor meer informatie.

### <a name="installing-module-versions-side-by-side"></a>Moduleversies naast elkaar installeren

De PowerShellGet-installatiemethode is de enige methode die ondersteuning biedt voor de installatie van meerdere versies. U hebt bijvoorbeeld scripts die zijn geschreven met behulp van een eerdere versie van Azure PowerShell, maar onvoldoende tijd of resources om ze bij te werken. De volgende opdrachten laten zien hoe u meerdere versies van Azure PowerShell installeert:

```powershell
Install-Module -Name AzureRM -RequiredVersion 3.7.0
Install-Module -Name AzureRM -RequiredVersion 1.2.9
```

Slechts één versie van de module kan in een PowerShell-sessie worden geladen. U moet een nieuw PowerShell-venster openen en `Import-Module` gebruiken om een specifieke versie van de AzureRM-cmdlets te importeren:

```powershell
Import-Module -Name AzureRM -RequiredVersion 1.2.9
```

> [!NOTE]
> Versie 2.1.0 en versie 1.2.6 zijn de eerste moduleversies die zijn ontworpen om naast elkaar te worden geïnstalleerd en gebruikt. Bij het laden van een eerdere versie van de Azure PowerShell worden incompatibele versies van de module **AzureRM.Profile** geladen. Dit leidt ertoe dat u wordt gevraagd u aan te melden telkens als u een cmdlet uitvoert.

### <a name="other-installation-methods"></a>Andere installatiemethoden

Zie [Andere installatiemethoden](other-install.md) voor meer informatie over installatie met het webplatforminstallatieprogramma of het MSI-pakket
