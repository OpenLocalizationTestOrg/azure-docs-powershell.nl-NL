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
# <a name="azure-stack-powershell"></a><span data-ttu-id="23d51-103">PowerShell voor Azure Stack</span><span class="sxs-lookup"><span data-stu-id="23d51-103">Azure Stack PowerShell</span></span> 

<span data-ttu-id="23d51-104">Voor Azure Stack zijn de volgende twee PowerShell-modules vereist:</span><span class="sxs-lookup"><span data-stu-id="23d51-104">Azure Stack requires the following two PowerShell modules:</span></span>  

1. <span data-ttu-id="23d51-105">De Azure Stack-compatibele module **AzureRM**. Deze is beschikbaar na installatie van API-versieprofiel **Profiel 2017 03-09**.</span><span class="sxs-lookup"><span data-stu-id="23d51-105">The Azure Stack compatible **AzureRM** module which is available by installing the **2017-03-09-profile** API Version Profile.</span></span> <span data-ttu-id="23d51-106">De cmdlets die met behulp van dit profiel zijn geïnstalleerd, kunnen worden gebruikt door Azure Stack-cloudbeheerders en door tenants.</span><span class="sxs-lookup"><span data-stu-id="23d51-106">The cmdlets installed by using this profile can be used by the Azure Stack cloud administrators and the tenants.</span></span> <span data-ttu-id="23d51-107">Voor meer informatie over de PowerShell-cmdlets die in dit profiel beschikbaar zijn, raadpleegt u het PowerShell-referentiemateriaal voor [versie 1.2.9 van de AzureRM-module](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-1.2.9).</span><span class="sxs-lookup"><span data-stu-id="23d51-107">To learn about the PowerShell cmdlets that are available in this profile, see the PowerShell reference content for the [1.2.9 version of AzureRM](https://docs.microsoft.com/en-us/powershell/azure/overview?view=azurermps-1.2.9) module.</span></span>  

2. <span data-ttu-id="23d51-108">Versie **1.2.9** van de **AzureStack**-module.</span><span class="sxs-lookup"><span data-stu-id="23d51-108">The **1.2.9** version of the **AzureStack** module.</span></span> <span data-ttu-id="23d51-109">De cmdlets die met behulp van deze module zijn geïnstalleerd, kunnen uitsluitend worden gebruikt door Azure Stack-cloudbeheerders.</span><span class="sxs-lookup"><span data-stu-id="23d51-109">The cmdlets installed by using this module can be used by Azure Stack cloud administrators only.</span></span> <span data-ttu-id="23d51-110">Met de in deze module beschikbare PowerShell-cmdlets kunnen beheerders bewerkingen uitvoeren als het beheren van aanbiedingen, plannen, services, quota enz.</span><span class="sxs-lookup"><span data-stu-id="23d51-110">Administrator can perform operations such as manage offers, plans, services, quotas, etc. by using the PowerShell cmdlets provided by this module.</span></span> <span data-ttu-id="23d51-111">Voor informatie over de PowerShell-cmdlets die in deze module beschikbaar zijn, raadpleegt u het referentiemateriaal voor [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.9#azurerm.azurestackadmin) en [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.9#azurerm.azurestackstorage).</span><span class="sxs-lookup"><span data-stu-id="23d51-111">To learn about the PowerShell cmdlets available in this module, see the [AzureStackAdmin](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackadmin/?view=azurestackps-1.2.9#azurerm.azurestackadmin) and [AzureStackStorage](https://docs.microsoft.com/en-us/powershell/module/azurerm.azurestackstorage/?view=azurestackps-1.2.9#azurerm.azurestackstorage) Reference content.</span></span>

## <a name="next-steps"></a><span data-ttu-id="23d51-112">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="23d51-112">Next Steps</span></span>

* [<span data-ttu-id="23d51-113">PowerShell voor Azure Stack installeren</span><span class="sxs-lookup"><span data-stu-id="23d51-113">Install PowerShell for Azure Stack</span></span>](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-install?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)
* [<span data-ttu-id="23d51-114">PowerShell configureren voor gebruik met Azure Stack</span><span class="sxs-lookup"><span data-stu-id="23d51-114">Configure PowerShell for use with Azure Stack</span></span>](https://docs.microsoft.com/en-us/azure/azure-stack/azure-stack-powershell-configure?view=azurestackps-1.2.9&toc=%2fpowershell%2fmodule%2ftoc.json%3fview%3dazurestackps-1.2.9&view=azurestackps-1.2.9)


