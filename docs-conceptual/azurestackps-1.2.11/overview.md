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
ms.openlocfilehash: f895992b4200f260189b3dbc541452e73a377b00
ms.sourcegitcommit: 8446ae373ac6928871ec8f10d3a4918b4601d5b2
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/27/2018
---
# <a name="azure-stack-powershell"></a><span data-ttu-id="76fa2-103">PowerShell voor Azure Stack</span><span class="sxs-lookup"><span data-stu-id="76fa2-103">Azure Stack PowerShell</span></span>

<span data-ttu-id="76fa2-104">Voor Azure Stack zijn de volgende twee PowerShell-modules vereist:</span><span class="sxs-lookup"><span data-stu-id="76fa2-104">Azure Stack requires the following two PowerShell modules:</span></span>  

1. <span data-ttu-id="76fa2-105">De Azure Stack-compatibele module **AzureRM**. Deze is beschikbaar na installatie van API-versieprofiel **Profiel 2017 03-09**.</span><span class="sxs-lookup"><span data-stu-id="76fa2-105">The Azure Stack compatible **AzureRM** module which is available by installing the **2017-03-09-profile** API Version Profile.</span></span> <span data-ttu-id="76fa2-106">De cmdlets die met behulp van dit profiel zijn geïnstalleerd, kunnen worden gebruikt door Azure Stack-operators en -gebruikers.</span><span class="sxs-lookup"><span data-stu-id="76fa2-106">The cmdlets installed by using this profile can be used by Azure Stack operators and users.</span></span>

2. <span data-ttu-id="76fa2-107">De module **AzureStack**. De meest recente versie hiervan is **1.2.11**.</span><span class="sxs-lookup"><span data-stu-id="76fa2-107">The most current version is the **1.2.11** install of the **AzureStack** module.</span></span> <span data-ttu-id="76fa2-108">De cmdlets die met behulp van deze module zijn geïnstalleerd, kunnen uitsluitend worden gebruikt door Azure Stack-operators.</span><span class="sxs-lookup"><span data-stu-id="76fa2-108">The cmdlets installed by using this module can be used by Azure Stack operators only.</span></span> <span data-ttu-id="76fa2-109">Met de in deze module beschikbare PowerShell-cmdlets kunnen operators bewerkingen uitvoeren zoals het beheren van aanbiedingen, plannen, services, quota enz.</span><span class="sxs-lookup"><span data-stu-id="76fa2-109">Operators can perform operations such as manage offers, plans, services, quotas, etc. by using the PowerShell cmdlets provided by this module.</span></span> <span data-ttu-id="76fa2-110">Voor informatie over de PowerShell-cmdlets die in deze module beschikbaar zijn, raadpleegt u het referentiemateriaal voor [AzureStackAdmin](https://docs.microsoft.com/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) en [AzureStackStorage](https://docs.microsoft.com/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage).</span><span class="sxs-lookup"><span data-stu-id="76fa2-110">To learn about the PowerShell cmdlets available in this module, see the [AzureStackAdmin](https://docs.microsoft.com/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.11#azurerm.azurestackadmin) and [AzureStackStorage](https://docs.microsoft.com/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.11#azurerm.azurestackstorage) Reference content.</span></span>

## <a name="next-steps"></a><span data-ttu-id="76fa2-111">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="76fa2-111">Next Steps</span></span>

* [<span data-ttu-id="76fa2-112">PowerShell voor Azure Stack installeren</span><span class="sxs-lookup"><span data-stu-id="76fa2-112">Install PowerShell for Azure Stack</span></span>](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
* [<span data-ttu-id="76fa2-113">PowerShell configureren voor gebruik met Azure Stack</span><span class="sxs-lookup"><span data-stu-id="76fa2-113">Configure PowerShell for use with Azure Stack</span></span>](https://docs.microsoft.com/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
