---
title: Overzicht van PowerShell voor Azure Stack | Microsoft Docs
description: Overzicht van de installatie en configuratie van PowerShell voor Azure Stack.
author: SnehaGunda
manager: Byronr
ms.product: azure-stack
ms.service: powershell
ms.devlang: powershell
ms.topic: reference
ms.author: sngun
ms.manager: byronr
ms.openlocfilehash: 49980b361c580a1a00f07c2002241e71f2c0b654
ms.sourcegitcommit: df44d5d9874b55455ec745f1846e06a4b3266d13
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/06/2017
---
# <a name="azure-stack-powershell"></a>PowerShell voor Azure Stack

Voor Azure Stack zijn de volgende twee PowerShell-modules vereist:  

1. De Azure Stack-compatibele module **AzureRM**. Deze is beschikbaar na installatie van API-versieprofiel **Profiel 2017 03-09**. De cmdlets die met behulp van dit profiel zijn geïnstalleerd, kunnen worden gebruikt door Azure Stack-operators en -gebruikers.

2. De module **AzureStack**. De meest recente versie hiervan is **1.2.11**. De cmdlets die met behulp van deze module zijn geïnstalleerd, kunnen uitsluitend worden gebruikt door Azure Stack-operators. Met de in deze module beschikbare PowerShell-cmdlets kunnen operators bewerkingen uitvoeren zoals het beheren van aanbiedingen, plannen, services, quota enz. Voor informatie over de PowerShell-cmdlets die in deze module beschikbaar zijn, raadpleegt u het referentiemateriaal voor [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) en [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage).

## <a name="next-steps"></a>Volgende stappen

* [PowerShell voor Azure Stack installeren](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
* [PowerShell configureren voor gebruik met Azure Stack](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
