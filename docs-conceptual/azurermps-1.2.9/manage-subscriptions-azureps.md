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
ms.sourcegitcommit: 5f0013981fcea1d689649b9a2b2ffe84ae842e56
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="manage-multiple-azure-subscriptions"></a>Meerdere Azure-abonnementen beheren

Als u nieuw bent bij Azure, hebt u waarschijnlijk slechts één abonnement. Maar als u Azure al een tijdje gebruikt, hebt u waarschijnlijk al meerdere Azure-abonnementen gemaakt. U kunt Azure PowerShell configureren voor het uitvoeren van opdrachten op basis van een bepaald abonnement.

1. Haal een lijst met alle abonnementen op in uw account.

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

2. Stel de standaardwaarde in.

    ```powershell
    Select-AzureRmSubscription -SubscriptionName "My Demos"
    ```

3. Controleer de wijziging door de cmdlet `Get-AzureRmContext` uit te voeren.

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

Nadat u uw standaardabonnement hebt ingesteld, worden alle volgende Azure PowerShell-opdrachten op basis van dit abonnement uitgevoerd.
