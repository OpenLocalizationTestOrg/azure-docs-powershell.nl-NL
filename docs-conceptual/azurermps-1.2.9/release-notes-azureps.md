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
# <a name="release-notes"></a><span data-ttu-id="089be-103">Releaseopmerkingen</span><span class="sxs-lookup"><span data-stu-id="089be-103">Release notes</span></span>

<span data-ttu-id="089be-104">Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="089be-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <a name="version-129"></a><span data-ttu-id="089be-105">Versie 1.2.9</span><span class="sxs-lookup"><span data-stu-id="089be-105">Version 1.2.9</span></span>

<span data-ttu-id="089be-106">Wijzigingen in deze release</span><span class="sxs-lookup"><span data-stu-id="089be-106">Changes This Release</span></span>

* <span data-ttu-id="089be-107">AzureRm.AzureStackAdmin-module</span><span class="sxs-lookup"><span data-stu-id="089be-107">AzureRm.AzureStackAdmin Module</span></span>
    + <span data-ttu-id="089be-108">Wijzigingen in de cmdlet Add-AzureRmResourceProviderRegistration voor ondersteuning van Admin Azure Resource Manager en tenant Azure Resource Manager-splitsing.</span><span class="sxs-lookup"><span data-stu-id="089be-108">Changes in the Add-AzureRmResourceProviderRegistration cmdlet for the support of Admin Azure resource manager and tenant azure resource manager split.</span></span> <span data-ttu-id="089be-109">Er is een nieuwe parameter -ResourceManagerType toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="089be-109">A new parameter -ResourceManagerType has been added.</span></span>
    + <span data-ttu-id="089be-110">De parameters -AdminUri, -ApiVersion, -SubscriptionId en -Token zijn uit alle cmdlets verwijderd.</span><span class="sxs-lookup"><span data-stu-id="089be-110">Removal of the parameters -AdminUri, -ApiVersion, -SubscriptionId and -Token from each cmdlets.</span></span> <span data-ttu-id="089be-111">Nadat we al eerder bekend hadden gemaakt dat deze parameters zouden worden afgeschaft, is dat nu gebeurd.</span><span class="sxs-lookup"><span data-stu-id="089be-111">We have been printing warnings that these parameters will be deprecated and now they got removed.</span></span>
* <span data-ttu-id="089be-112">AzureStackStorage-module</span><span class="sxs-lookup"><span data-stu-id="089be-112">AzureStackStorage module</span></span>
    + <span data-ttu-id="089be-113">Er zijn nieuwe cmdlets toegevoegd ter ondersteuning van containermigratiescenario's.</span><span class="sxs-lookup"><span data-stu-id="089be-113">Added new cmdlets to support container migration scenarios.</span></span>
    + <span data-ttu-id="089be-114">Cmdlets die naar interne onderdelen en onderliggende functies verwijzen, zijn verwijderd.</span><span class="sxs-lookup"><span data-stu-id="089be-114">Removed cmdlets referring to internal components and underlying features.</span></span>
* <span data-ttu-id="089be-115">AzureRM.BootStrapper</span><span class="sxs-lookup"><span data-stu-id="089be-115">AzureRM.BootStrapper</span></span>
    + <span data-ttu-id="089be-116">Er is een nieuwe module gemaakt voor het beheren van de versies van Azure PowerShell-cmdlets met behulp van versieprofielen</span><span class="sxs-lookup"><span data-stu-id="089be-116">Created new module to manage versions of Azure PowerShell cmdlets through the use of version profiles</span></span>