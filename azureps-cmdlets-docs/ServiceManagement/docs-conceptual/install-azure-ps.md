---
title: De Azure PowerShell Service Management-module installeren en configureren | Microsoft Docs
description: Azure PowerShell voor het eerst installeren en configureren.
services: azure
author: sdwheeler
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/06/2017
ms.openlocfilehash: c51c727c1cb022eca59f819c7f24d8e058c677da
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/29/2017
---
# <a name="installing-the-azure-powershell-service-management-module"></a>De Azure PowerShell Service Management-module installeren

Installatie van Azure PowerShell via de [PowerShell Gallery](https://www.powershellgallery.com/) heeft de voorkeur.

## <a name="step-1-install-powershellget"></a>Stap 1: PowerShellGet installeren

Als u items uit de PowerShell Gallery wilt installeren, hebt u de PowerShellGet-module nodig. Zorg ervoor dat u de juiste versie van PowerShellGet hebt en ook voldoet aan de overige systeemvereisten. Voer de volgende opdracht uit om na te gaan of PowerShellGet op uw systeem is geïnstalleerd.

```powershell
Get-Module PowerShellGet -list | Select-Object Name,Version,Path
```

De uitvoer moet er ongeveer uitzien als hieronder is weergegeven:

```
Name          Version Path
----          ------- ----
PowerShellGet 1.0.0.1 C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1
```

Zie [PowerShellGet ophalen](install-azurerm-ps.md#how-to-get-powershellget) als PowerShellGet niet is geïnstalleerd.

## <a name="step-2-install-azure-powershell"></a>Stap 2: Azure PowerShell installeren

Voer de volgende opdracht uit vanuit de Windows PowerShell-console die als beheerder wordt uitgevoerd:

```powershell
Install-Module Azure
```

De Azure-module is een updatepakketmodule voor de Azure Resource Manager-cmdlets. Wanneer u de AzureRM-module installeert, worden alle overige Azure-modules die niet eerder zijn geïnstalleerd, gedownload en geïnstalleerd vanuit de PowerShell Gallery.

De Azure Service Management-module deelt afhankelijkheden met de Azure PowerShell Resource Manager-modules. Als u de Azure PowerShell Resource Manager-modules hebt geïnstalleerd, moet u de parameter `-AllowClobber` aan de installatieopdracht toevoegen. Hiermee worden de huidige gedeelde afhankelijkheden bijgewerkt. Zonder deze parameter kan de module niet worden geïnstalleerd.

```powershell
Install-Module Azure -AllowClobber
```

Nadat u deze module hebt geïnstalleerd, kunt u de module importeren door de volgende opdracht uit te voeren:

```powershell
Import-Module Azure
```

## <a name="to-use-the-cmdlets"></a>De cmdlets gebruiken

Als u wilt gaan werken met de cmdlets van Azure Service Management, moet u zich eerst aanmelden bij uw Azure-account. Voer de volgende opdracht uit als u zich wilt aanmelden bij uw account:

```powershell
Add-AzureAccount
```

Nadat u zich bij Azure hebt aangemeld, maakt Azure PowerShell een context voor de opgegeven sessie. Die context bevat de Azure PowerShell-omgeving, het account, de tenant en het abonnement die worden gebruikt voor alle cmdlets binnen de betreffende sessie. U bent nu klaar om de onderstaande modules te gaan gebruiken.

## <a name="azure-service-management-cmdlets"></a>Cmdlets van Azure Service Management

Azure PowerShell-modules worden regelmatig bijgewerkt. Als u merkt dat de online Help bij de cmdlet betrekking heeft op cmdlets of parameters die zich niet in uw module bevinden, moet u de nieuwste versie van de module downloaden en installeren. Als wilt weten wat de versie van uw module is, typt u: `(Get-Module Azure).Version`.

Als u op zoek bent naar voorbeeldscripts waarmee u een aantal veelvoorkomende taken in Azure kunt automatiseren, kunt u het [Scriptcentrum van Windows Azure](http://www.windowsazure.com/documentation/scripts/) raadplegen.

Zie [Scripting with Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=320210) (Werken met scripts in Windows PowerShell) voor algemene informatie over hoe u Windows PowerShell installeert en aanpast, ermee werkt en er meer over leert.
