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
ms.openlocfilehash: 2a03697e0f3e80d63c48f2dc5615f6c99b9ef716
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/29/2017
---
# <a name="azure-stack-powershell"></a>PowerShell voor Azure Stack 

Voor Azure Stack zijn de volgende twee PowerShell-modules vereist:  

1. De Azure Stack-compatibele module **AzureRM**. Deze is beschikbaar na installatie van API-versieprofiel **Profiel 2017 03-09**. De cmdlets die met behulp van dit profiel zijn geïnstalleerd, kunnen worden gebruikt door Azure Stack-cloudbeheerders en door tenants. Voor meer informatie over de PowerShell-cmdlets die in dit profiel beschikbaar zijn, raadpleegt u het PowerShell-referentiemateriaal voor [versie 1.2.9 van de AzureRM-module](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-1.2.9).  

2. Versie **1.2.9** van de **AzureStack**-module. De cmdlets die met behulp van deze module zijn geïnstalleerd, kunnen uitsluitend worden gebruikt door Azure Stack-cloudbeheerders. Met de in deze module beschikbare PowerShell-cmdlets kunnen beheerders bewerkingen uitvoeren als het beheren van aanbiedingen, plannen, services, quota enz. Voor informatie over de PowerShell-cmdlets die in deze module beschikbaar zijn, raadpleegt u het referentiemateriaal voor [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.9#azurerm.azurestackadmin) en [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.9#azurerm.azurestackstorage).

## <a name="next-steps"></a>Volgende stappen

* [PowerShell voor Azure Stack installeren](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
* [PowerShell configureren voor gebruik met Azure Stack](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)


