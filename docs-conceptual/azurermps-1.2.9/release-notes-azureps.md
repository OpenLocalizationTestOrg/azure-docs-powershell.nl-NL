---
title: Azure PowerShell-wijzigingenlogboek | Microsoft Docs
description: Dit is de geschiedenis van de wijzigingen die in de nieuwste release van Azure PowerShell zijn doorgevoerd.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.service: azure-powershell
ms.product: azure
ms.devlang: powershell
ms.topic: conceptual
ms.workload: 
ms.date: 05/18/2017
ms.openlocfilehash: 5fe7591855577e083aad5923aed37b18d0b2a40c
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a>Releaseopmerkingen

Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.

## <a name="version-129"></a>Versie 1.2.9

Wijzigingen in deze release

* AzureRm.AzureStackAdmin-module
    + Wijzigingen in de cmdlet Add-AzureRmResourceProviderRegistration voor ondersteuning van Admin Azure Resource Manager en tenant Azure Resource Manager-splitsing. Er is een nieuwe parameter -ResourceManagerType toegevoegd.
    + De parameters -AdminUri, -ApiVersion, -SubscriptionId en -Token zijn uit alle cmdlets verwijderd. Nadat we al eerder bekend hadden gemaakt dat deze parameters zouden worden afgeschaft, is dat nu gebeurd.
* AzureStackStorage-module
    + Er zijn nieuwe cmdlets toegevoegd ter ondersteuning van containermigratiescenario's.
    + Cmdlets die naar interne onderdelen en onderliggende functies verwijzen, zijn verwijderd.
* AzureRM.BootStrapper
    + Er is een nieuwe module gemaakt voor het beheren van de versies van Azure PowerShell-cmdlets met behulp van versieprofielen