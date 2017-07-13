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
ms.openlocfilehash: 143d92384fd270711378f6741ba59e88c12833d1
ms.sourcegitcommit: 226527be7cb647acfe2ea9ab151185053ab3c6db
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/29/2017
---
# <span data-ttu-id="cf2b9-103">Releaseopmerkingen</span><span class="sxs-lookup"><span data-stu-id="cf2b9-103">Release notes</span></span>
<a id="release-notes" class="xliff"></a>

<span data-ttu-id="cf2b9-104">Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cf2b9-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <span data-ttu-id="cf2b9-105">Versie 2.2.0</span><span class="sxs-lookup"><span data-stu-id="cf2b9-105">Version 2.2.0</span></span>
<a id="version-220" class="xliff"></a>
* <span data-ttu-id="cf2b9-106">Compute</span><span class="sxs-lookup"><span data-stu-id="cf2b9-106">Compute</span></span>
  - <span data-ttu-id="cf2b9-107">Er is ondersteuning toegevoegd voor het uitvoeren van query's over de versleutelingsstatus van de AzureDiskEncryptionForLinux-extensie</span><span class="sxs-lookup"><span data-stu-id="cf2b9-107">Add support for querying encryption status from the AzureDiskEncryptionForLinux extension</span></span>
* <span data-ttu-id="cf2b9-108">DataFactory</span><span class="sxs-lookup"><span data-stu-id="cf2b9-108">DataFactory</span></span>
  - <span data-ttu-id="cf2b9-109">Er is een nieuwe cmdlet toegevoegd voor het maken van een lijst met activiteitenvensters</span><span class="sxs-lookup"><span data-stu-id="cf2b9-109">Added new cmdlet for listing activity windows</span></span>
    + <span data-ttu-id="cf2b9-110">Get-AzureRmDataFactoryActivityWindow</span><span class="sxs-lookup"><span data-stu-id="cf2b9-110">Get-AzureRmDataFactoryActivityWindow</span></span>
* <span data-ttu-id="cf2b9-111">DataLake</span><span class="sxs-lookup"><span data-stu-id="cf2b9-111">DataLake</span></span>
  - <span data-ttu-id="cf2b9-112">De parameter `Host` is gewijzigd in `DatabaseHost` en er is een alias toegevoegd aan `Host`</span><span class="sxs-lookup"><span data-stu-id="cf2b9-112">Changed parameter `Host` to `DatabaseHost` and added alias to `Host`</span></span>
    + <span data-ttu-id="cf2b9-113">New-AzureRmDataLakeAnalyticsCatalogSecret</span><span class="sxs-lookup"><span data-stu-id="cf2b9-113">New-AzureRmDataLakeAnalyticsCatalogSecret</span></span>
    + <span data-ttu-id="cf2b9-114">Set-AzureRmDataLakeAnalyticsCatalogSecret</span><span class="sxs-lookup"><span data-stu-id="cf2b9-114">Set-AzureRmDataLakeAnalyticsCatalogSecret</span></span>
  - <span data-ttu-id="cf2b9-115">Er is ondersteuning toegevoegd voor het verwijderen van ACL en standaard-ACL</span><span class="sxs-lookup"><span data-stu-id="cf2b9-115">Add support for ACL and Default ACL removal</span></span>
  - <span data-ttu-id="cf2b9-116">Er is ondersteuning toegevoegd voor het ophalen en instellen van naamloze machtigingen voor bestanden en mappen</span><span class="sxs-lookup"><span data-stu-id="cf2b9-116">Add support for getting and setting unnamed permissions on files and folders</span></span>
* <span data-ttu-id="cf2b9-117">KeyVault</span><span class="sxs-lookup"><span data-stu-id="cf2b9-117">KeyVault</span></span>
  - <span data-ttu-id="cf2b9-118">Er is ondersteuning voor certificaten toegevoegd</span><span class="sxs-lookup"><span data-stu-id="cf2b9-118">Add support for certificates</span></span>
    + <span data-ttu-id="cf2b9-119">Add-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="cf2b9-119">Add-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="cf2b9-120">Add-AzureKeyVaultCertificateContact</span><span class="sxs-lookup"><span data-stu-id="cf2b9-120">Add-AzureKeyVaultCertificateContact</span></span>
    + <span data-ttu-id="cf2b9-121">Get-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="cf2b9-121">Get-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="cf2b9-122">Get-AzureKeyVaultCertificateContact</span><span class="sxs-lookup"><span data-stu-id="cf2b9-122">Get-AzureKeyVaultCertificateContact</span></span>
    + <span data-ttu-id="cf2b9-123">Get-AzureKeyVaultCertificateIssuer</span><span class="sxs-lookup"><span data-stu-id="cf2b9-123">Get-AzureKeyVaultCertificateIssuer</span></span>
    + <span data-ttu-id="cf2b9-124">Get-AzureKeyVaultCertificateOperation</span><span class="sxs-lookup"><span data-stu-id="cf2b9-124">Get-AzureKeyVaultCertificateOperation</span></span>
    + <span data-ttu-id="cf2b9-125">Get-AzureKeyVaultCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="cf2b9-125">Get-AzureKeyVaultCertificatePolicy</span></span>
    + <span data-ttu-id="cf2b9-126">Import-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="cf2b9-126">Import-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="cf2b9-127">New-AzureKeyVaultCertificateAdministratorDetails</span><span class="sxs-lookup"><span data-stu-id="cf2b9-127">New-AzureKeyVaultCertificateAdministratorDetails</span></span>
    + <span data-ttu-id="cf2b9-128">New-AzureKeyVaultCertificateOrganizationDetails</span><span class="sxs-lookup"><span data-stu-id="cf2b9-128">New-AzureKeyVaultCertificateOrganizationDetails</span></span>
    + <span data-ttu-id="cf2b9-129">New-AzureKeyVaultCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="cf2b9-129">New-AzureKeyVaultCertificatePolicy</span></span>
    + <span data-ttu-id="cf2b9-130">Remove-AzureKeyVaultCertificate</span><span class="sxs-lookup"><span data-stu-id="cf2b9-130">Remove-AzureKeyVaultCertificate</span></span>
    + <span data-ttu-id="cf2b9-131">Remove-AzureKeyVaultCertificateContact</span><span class="sxs-lookup"><span data-stu-id="cf2b9-131">Remove-AzureKeyVaultCertificateContact</span></span>
    + <span data-ttu-id="cf2b9-132">Remove-AzureKeyVaultCertificateIssuer</span><span class="sxs-lookup"><span data-stu-id="cf2b9-132">Remove-AzureKeyVaultCertificateIssuer</span></span>
    + <span data-ttu-id="cf2b9-133">Remove-AzureKeyVaultCertificateOperation</span><span class="sxs-lookup"><span data-stu-id="cf2b9-133">Remove-AzureKeyVaultCertificateOperation</span></span>
    + <span data-ttu-id="cf2b9-134">Set-AzureKeyVaultCertificateAttribute</span><span class="sxs-lookup"><span data-stu-id="cf2b9-134">Set-AzureKeyVaultCertificateAttribute</span></span>
    + <span data-ttu-id="cf2b9-135">Set-AzureKeyVaultCertificateIssuer</span><span class="sxs-lookup"><span data-stu-id="cf2b9-135">Set-AzureKeyVaultCertificateIssuer</span></span>
    + <span data-ttu-id="cf2b9-136">Set-AzureKeyVaultCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="cf2b9-136">Set-AzureKeyVaultCertificatePolicy</span></span>
    + <span data-ttu-id="cf2b9-137">Stop-AzureKeyVaultCertificateOperation</span><span class="sxs-lookup"><span data-stu-id="cf2b9-137">Stop-AzureKeyVaultCertificateOperation</span></span>
* <span data-ttu-id="cf2b9-138">Netwerk</span><span class="sxs-lookup"><span data-stu-id="cf2b9-138">Network</span></span>

  - <span data-ttu-id="cf2b9-139">Er is een nieuwe switchparameter toegevoegd voor de netwerkinterface om versnelde netwerken in of uit te schakelen: +New-AzureRmNetworkInterface -EnableAcceleratedNetworking</span><span class="sxs-lookup"><span data-stu-id="cf2b9-139">New switch parameter added for network interface to enable/disable accelerated networking +New-AzureRmNetworkInterface -EnableAcceleratedNetworking</span></span>
  - <span data-ttu-id="cf2b9-140">De PowerShell-cmdlets voor de Active-Active-gatewayfunctie zijn ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="cf2b9-140">Enable Active-Active gateway feature PowerShell cmdlets</span></span>
    + <span data-ttu-id="cf2b9-141">Add-AzureRmVirtualNetworkGatewayIpConfig</span><span class="sxs-lookup"><span data-stu-id="cf2b9-141">Add-AzureRmVirtualNetworkGatewayIpConfig</span></span>
    + <span data-ttu-id="cf2b9-142">Remove-AzureRmVirtualNetworkGatewayIpConfig</span><span class="sxs-lookup"><span data-stu-id="cf2b9-142">Remove-AzureRmVirtualNetworkGatewayIpConfig</span></span>
  - <span data-ttu-id="cf2b9-143">Er is een nieuwe cmdlet toegevoegd</span><span class="sxs-lookup"><span data-stu-id="cf2b9-143">Added new cmdlet</span></span>
    + <span data-ttu-id="cf2b9-144">Test-AzureRmPrivateIpAddressAvailability</span><span class="sxs-lookup"><span data-stu-id="cf2b9-144">Test-AzureRmPrivateIpAddressAvailability</span></span>
* <span data-ttu-id="cf2b9-145">Resources</span><span class="sxs-lookup"><span data-stu-id="cf2b9-145">Resources</span></span>
  - <span data-ttu-id="cf2b9-146">Er is ondersteuning toegevoegd voor zones in provider- en resource-cmdlets</span><span class="sxs-lookup"><span data-stu-id="cf2b9-146">Support zones in provider and resource cmdlets</span></span>
    + <span data-ttu-id="cf2b9-147">Get-AzureRmProvider</span><span class="sxs-lookup"><span data-stu-id="cf2b9-147">Get-AzureRmProvider</span></span>
    + <span data-ttu-id="cf2b9-148">New-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="cf2b9-148">New-AzureRmResource</span></span>
    + <span data-ttu-id="cf2b9-149">Set-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="cf2b9-149">Set-AzureRmResource</span></span>
* <span data-ttu-id="cf2b9-150">SQL</span><span class="sxs-lookup"><span data-stu-id="cf2b9-150">Sql</span></span>
  - <span data-ttu-id="cf2b9-151">Er zijn nieuwe cmdlets voor beleidsbeheer toegevoegd met betrekking tot detectie in Azure SQL van bedreigingen op serverniveau</span><span class="sxs-lookup"><span data-stu-id="cf2b9-151">Added new cmdlets for Azure SQL threat detection policy management at server level</span></span>
    + <span data-ttu-id="cf2b9-152">Get-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="cf2b9-152">Get-AzureRmSqlServerThreatDetectionPolicy</span></span>
    + <span data-ttu-id="cf2b9-153">Remove-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="cf2b9-153">Remove-AzureRmSqlServerThreatDetectionPolicy</span></span>
    + <span data-ttu-id="cf2b9-154">Set-AzureRmSqlServerThreatDetectionPolicy</span><span class="sxs-lookup"><span data-stu-id="cf2b9-154">Set-AzureRmSqlServerThreatDetectionPolicy</span></span>
  - <span data-ttu-id="cf2b9-155">Er zijn nieuwe cmdlets toegevoegd ter ondersteuning van het in-/uitschakelen van de GeoBackupPolicy voor SQL Azure DataWarehouses</span><span class="sxs-lookup"><span data-stu-id="cf2b9-155">Added new cmdlets to support enabling/disabling GeoBackupPolicy for Sql Azure DataWarehouses</span></span>
    + <span data-ttu-id="cf2b9-156">Get-AzureRmSqlDatabaseGeoBackupPolicy</span><span class="sxs-lookup"><span data-stu-id="cf2b9-156">Get-AzureRmSqlDatabaseGeoBackupPolicy</span></span>
    + <span data-ttu-id="cf2b9-157">Set-AzureRmSqlDatabaseGeoBackupPolicy</span><span class="sxs-lookup"><span data-stu-id="cf2b9-157">Set-AzureRmSqlDatabaseGeoBackupPolicy</span></span>
  - <span data-ttu-id="cf2b9-158">Er zijn nieuwe cmdlets toegevoegd voor Azure SQL-Advisors en aanbevolen API's voor acties</span><span class="sxs-lookup"><span data-stu-id="cf2b9-158">Added new cmdlets for Azure Sql Advisors and Recommended Actions APIs</span></span>
    + <span data-ttu-id="cf2b9-159">Get-AzureRmSqlDatabaseAdvisor</span><span class="sxs-lookup"><span data-stu-id="cf2b9-159">Get-AzureRmSqlDatabaseAdvisor</span></span>
    + <span data-ttu-id="cf2b9-160">Get-AzureRmSqlElasticPoolAdvisor</span><span class="sxs-lookup"><span data-stu-id="cf2b9-160">Get-AzureRmSqlElasticPoolAdvisor</span></span>
    + <span data-ttu-id="cf2b9-161">Get-AzureRmSqlServerAdvisor</span><span class="sxs-lookup"><span data-stu-id="cf2b9-161">Get-AzureRmSqlServerAdvisor</span></span>
    + <span data-ttu-id="cf2b9-162">Get-AzureRmSqlDatabaseRecommendedActions</span><span class="sxs-lookup"><span data-stu-id="cf2b9-162">Get-AzureRmSqlDatabaseRecommendedActions</span></span>
    + <span data-ttu-id="cf2b9-163">Get-AzureRmSqlElasticPoolRecommendedActions</span><span class="sxs-lookup"><span data-stu-id="cf2b9-163">Get-AzureRmSqlElasticPoolRecommendedActions</span></span>
    + <span data-ttu-id="cf2b9-164">Get-AzureRmSqlServerRecommendedActions</span><span class="sxs-lookup"><span data-stu-id="cf2b9-164">Get-AzureRmSqlServerRecommendedActions</span></span>
    + <span data-ttu-id="cf2b9-165">Set-AzureRmSqlDatabaseAdvisorAutoExecuteStatus</span><span class="sxs-lookup"><span data-stu-id="cf2b9-165">Set-AzureRmSqlDatabaseAdvisorAutoExecuteStatus</span></span>
    + <span data-ttu-id="cf2b9-166">Set-AzureRmSqlElasticPoolAdvisorAutoExecuteStatus</span><span class="sxs-lookup"><span data-stu-id="cf2b9-166">Set-AzureRmSqlElasticPoolAdvisorAutoExecuteStatus</span></span>
    + <span data-ttu-id="cf2b9-167">Set-AzureRmSqlServerAdvisorAutoExecuteStatus</span><span class="sxs-lookup"><span data-stu-id="cf2b9-167">Set-AzureRmSqlServerAdvisorAutoExecuteStatus</span></span>
    + <span data-ttu-id="cf2b9-168">Set-AzureRmSqlDatabaseRecommendedActionState</span><span class="sxs-lookup"><span data-stu-id="cf2b9-168">Set-AzureRmSqlDatabaseRecommendedActionState</span></span>
    + <span data-ttu-id="cf2b9-169">Set-AzureRmSqlElasticPoolRecommendedActionState</span><span class="sxs-lookup"><span data-stu-id="cf2b9-169">Set-AzureRmSqlElasticPoolRecommendedActionState</span></span>
    + <span data-ttu-id="cf2b9-170">Set-AzureRmSqlServerRecommendedActionState</span><span class="sxs-lookup"><span data-stu-id="cf2b9-170">Set-AzureRmSqlServerRecommendedActionState</span></span>
