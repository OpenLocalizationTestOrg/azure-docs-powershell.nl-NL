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
ms.sourcegitcommit: 7e77fe7ecd2112d6b4515517509c5c723e750e27
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/19/2018
---
# <a name="manage-multiple-azure-subscriptions"></a><span data-ttu-id="bef6e-104">Meerdere Azure-abonnementen beheren</span><span class="sxs-lookup"><span data-stu-id="bef6e-104">Manage multiple Azure subscriptions</span></span>

<span data-ttu-id="bef6e-105">Als u nieuw bent bij Azure, hebt u waarschijnlijk slechts één abonnement.</span><span class="sxs-lookup"><span data-stu-id="bef6e-105">If you are brand new to Azure, you probably only have a single subscription.</span></span> <span data-ttu-id="bef6e-106">Maar als u Azure al een tijdje gebruikt, hebt u waarschijnlijk al meerdere Azure-abonnementen gemaakt.</span><span class="sxs-lookup"><span data-stu-id="bef6e-106">But if you have been using Azure for a while, you may have created multiple Azure subscriptions.</span></span> <span data-ttu-id="bef6e-107">U kunt Azure PowerShell configureren voor het uitvoeren van opdrachten op basis van een bepaald abonnement.</span><span class="sxs-lookup"><span data-stu-id="bef6e-107">You can configure Azure PowerShell to execute commands against a particular subscription.</span></span>

1. <span data-ttu-id="bef6e-108">Haal een lijst met alle abonnementen op in uw account.</span><span class="sxs-lookup"><span data-stu-id="bef6e-108">Get a list of all subscriptions in your account.</span></span>

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

2. <span data-ttu-id="bef6e-109">Stel de standaardwaarde in.</span><span class="sxs-lookup"><span data-stu-id="bef6e-109">Set the default.</span></span>

    ```powershell
    Select-AzureRmSubscription -SubscriptionName "My Demos"
    ```

3. <span data-ttu-id="bef6e-110">Controleer de wijziging door de cmdlet `Get-AzureRmContext` uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="bef6e-110">Verify the change by running the `Get-AzureRmContext` cmdlet.</span></span>

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

<span data-ttu-id="bef6e-111">Nadat u uw standaardabonnement hebt ingesteld, worden alle volgende Azure PowerShell-opdrachten op basis van dit abonnement uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bef6e-111">Once you set your default subscription, all subsequent Azure PowerShell commands run against this subscription.</span></span>
