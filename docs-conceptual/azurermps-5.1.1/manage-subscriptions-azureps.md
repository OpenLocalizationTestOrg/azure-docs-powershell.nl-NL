---
title: Azure-abonnementen beheren met Azure PowerShell | Microsoft Docs
description: Azure-abonnementen beheren met Azure PowerShell
keywords: Azure PowerShell, abonnement
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/30/2017
ms.openlocfilehash: 68d03ec8d1a86fb3b270d02a4697bbf9af847f2d
ms.sourcegitcommit: c42c7176276ec4e1cc3360a93e6b15d32083bf9f
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2017
---
# <a name="manage-multiple-azure-subscriptions"></a><span data-ttu-id="90f60-104">Meerdere Azure-abonnementen beheren</span><span class="sxs-lookup"><span data-stu-id="90f60-104">Manage multiple Azure subscriptions</span></span>

<span data-ttu-id="90f60-105">Als u nieuw bent bij Azure, hebt u waarschijnlijk slechts één abonnement.</span><span class="sxs-lookup"><span data-stu-id="90f60-105">If you are brand new to Azure, you probably only have a single subscription.</span></span> <span data-ttu-id="90f60-106">Maar als u Azure al een tijdje gebruikt, hebt u waarschijnlijk al meerdere Azure-abonnementen gemaakt.</span><span class="sxs-lookup"><span data-stu-id="90f60-106">But if you have been using Azure for a while, you may have created multiple Azure subscriptions.</span></span> <span data-ttu-id="90f60-107">U kunt Azure PowerShell configureren voor het uitvoeren van opdrachten op basis van een bepaald abonnement.</span><span class="sxs-lookup"><span data-stu-id="90f60-107">You can configure Azure PowerShell to execute commands against a particular subscription.</span></span>

1. <span data-ttu-id="90f60-108">Haal een lijst met alle abonnementen op in uw account.</span><span class="sxs-lookup"><span data-stu-id="90f60-108">Get a list of all subscriptions in your account.</span></span>

    ```powershell
    Get-AzureRmSubscription
    ```

    ```
    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Production Subscription
    CurrentStorageAccount :

    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My DevTest Subscription
    CurrentStorageAccount :

    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Demos
    CurrentStorageAccount :
    ```

2. <span data-ttu-id="90f60-109">Stel de standaardwaarde in.</span><span class="sxs-lookup"><span data-stu-id="90f60-109">Set the default.</span></span>

    ```powershell
    Select-AzureRmSubscription -SubscriptionName "My Demos"
    ```

3. <span data-ttu-id="90f60-110">Controleer de wijziging door de cmdlet `Get-AzureRmContext` uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="90f60-110">Verify the change by running the `Get-AzureRmContext` cmdlet.</span></span>

    ```powershell
    Get-AzureRmContext
    ```

    ```
    Environment           : AzureCloud
    Account               : username@contoso.com
    TenantId              : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionId        : XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    SubscriptionName      : My Demos
    CurrentStorageAccount :
    ```

<span data-ttu-id="90f60-111">Nadat u uw standaardabonnement hebt ingesteld, worden alle volgende Azure PowerShell-opdrachten op basis van dit abonnement uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="90f60-111">Once you set your default subscription, all subsequent Azure PowerShell commands run against this subscription.</span></span>
