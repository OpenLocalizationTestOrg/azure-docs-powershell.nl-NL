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
ms.openlocfilehash: 0a3f152751fee569d3ac5fba6bcff8c1737f7b8c
ms.sourcegitcommit: b256bf48e15ee98865de0fae50e7b81878b03a54
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2017
---
# <a name="release-notes"></a><span data-ttu-id="3a295-103">Releaseopmerkingen</span><span class="sxs-lookup"><span data-stu-id="3a295-103">Release notes</span></span>

<span data-ttu-id="3a295-104">Dit is een overzicht van de wijzigingen die in deze release van Azure PowerShell zijn doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3a295-104">This is a list of changes made to Azure PowerShell in this release.</span></span>

## <a name="version-170"></a><span data-ttu-id="3a295-105">Versie 1.7.0</span><span class="sxs-lookup"><span data-stu-id="3a295-105">Version 1.7.0</span></span>

* <span data-ttu-id="3a295-106">**Gedragswijziging voor de parameters -Force, –Confirm en $ConfirmPreference voor alle cmdlets. We wijzigen deze implementatie, zodat deze in overeenstemming is met de PowerShell-richtlijnen. Dit betekent voor de meeste cmdlets dat de parameter Force wordt verwijderd en de prompt ShouldProcess wordt overgeslagen. Gebruikers moeten de parameter -Confirm:$false in de PowerShell-scripts opnemen.**</span><span class="sxs-lookup"><span data-stu-id="3a295-106">**Behavioral change for -Force, –Confirm and $ConfirmPreference parameters for all cmdlets. We are changing this implementation to be in line with PowerShell guidelines. For most cmdlets, this means removing the Force parameter and to skip the ShouldProcess prompt, users will need to include the parameter: ‘-Confirm:$false’ in their PowerShell scripts.**</span></span> <span data-ttu-id="3a295-107">Deze wijzigingen hebben betrekking op de volgende problemen:</span><span class="sxs-lookup"><span data-stu-id="3a295-107">This changes are addressing following issues:</span></span>
  - <span data-ttu-id="3a295-108">De correcte implementatie van de –WhatIf-functionaliteit, zodat een gebruiker de gevolgen van een cmdlet of script kan bepalen zonder daadwerkelijk wijzigingen door te voeren</span><span class="sxs-lookup"><span data-stu-id="3a295-108">Correct implementation of –WhatIf functionality, allowing a user to determine the effects of a cmdlet or script without making any actual changes</span></span>
  - <span data-ttu-id="3a295-109">Controle over prompts met behulp van een sessiebrede $ConfirmPreference, zodat aan de gebruiker vragen worden gesteld op basis van de impact van een potentiële wijziging (zoals aangegeven in de ConfirmImpact-instelling in de cmdlet)</span><span class="sxs-lookup"><span data-stu-id="3a295-109">Control over prompting using a session-wide $ConfirmPreference, so that the user is prompted based on the impact of a prospective change (as reported in the ConfirmImpact setting in the cmdlet)</span></span>
  - <span data-ttu-id="3a295-110">Cmdlet-specifieke controle over bevestigingsprompts met de parameter –Confirm</span><span class="sxs-lookup"><span data-stu-id="3a295-110">Cmdlet-specific control over confirmation prompts using the –Confirm parameter</span></span>
  - <span data-ttu-id="3a295-111">Consistent gebruik van ShouldContinue en de parameter –Force tussen cmdlets voor acties die alleen het stellen van vragen door de gebruiker vereisen vanwege de speciale aard van de wijzigingen (bijvoorbeeld het verwijderen van verborgen bestanden)</span><span class="sxs-lookup"><span data-stu-id="3a295-111">Consistent use of ShouldContinue and the –Force parameter across cmdlets, for only those actions that would require prompting from the user due to the special nature of the changes (for example, deleting hidden files)</span></span>
  - <span data-ttu-id="3a295-112">Consistentie met andere PowerShell-cmdlets, zodat PowerShell-scriptkennis van andere cmdlets direct toepasbaar is op de Azure PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3a295-112">Consistency with other PowerShell cmdlets, so that PowerShell scripting knowledge from other cmdlets is immediately applicable to the Azure PowerShell cmdlets.</span></span>

<span data-ttu-id="3a295-113">**Houd er rekening mee dat er nu bij het *automatisch overslaan van alle prompts in alle gevallen* Azure PowerShell-cmdlets van de gebruiker vereisen dat deze twee parameters opgeeft:**</span><span class="sxs-lookup"><span data-stu-id="3a295-113">**Notice that now to *automatically skip all Prompts in all Circumstances* Azure PowerShell cmdlets require the user to supply two parameters:**</span></span>
```powershell
My-CmdletWithConfirmation –Confirm:$false -Force
```
* <span data-ttu-id="3a295-114">Azure Compute</span><span class="sxs-lookup"><span data-stu-id="3a295-114">Azure Compute</span></span>
  - <span data-ttu-id="3a295-115">Set-AzureRmVMADDomainExtension</span><span class="sxs-lookup"><span data-stu-id="3a295-115">Set-AzureRmVMADDomainExtension</span></span>
  - <span data-ttu-id="3a295-116">Get-AzureRmVMADDomainExtension</span><span class="sxs-lookup"><span data-stu-id="3a295-116">Get-AzureRmVMADDomainExtension</span></span>
  - <span data-ttu-id="3a295-117">Parameter -Redeploy voor Restart-AzureVM</span><span class="sxs-lookup"><span data-stu-id="3a295-117">-Redeploy parameter for Restart-AzureVM</span></span>
  - <span data-ttu-id="3a295-118">Parameter -Validate voor Move-AzureService, Move-AzureStorageAccount en Move-AzureVirtualNetwork</span><span class="sxs-lookup"><span data-stu-id="3a295-118">-Validate parameter for Move-AzureService, Move-AzureStorageAccount, and Move-AzureVirtualNetwork</span></span>
  - <span data-ttu-id="3a295-119">Naam- en versieparameters voor extensie-cmdlets zijn, zoals voorheen, optioneel.</span><span class="sxs-lookup"><span data-stu-id="3a295-119">Name and version parameters for extension cmdlets are optional as before.</span></span>
  - <span data-ttu-id="3a295-120">New-AzureVM kan een licentietype van het VM-object krijgen.</span><span class="sxs-lookup"><span data-stu-id="3a295-120">New-AzureVM can get a license type from VM object.</span></span>
* <span data-ttu-id="3a295-121">Azure Storage</span><span class="sxs-lookup"><span data-stu-id="3a295-121">Azure Storage</span></span>
  - <span data-ttu-id="3a295-122">De parameter Tags is gewijzigd in Tag en de parameteralias Tags is toegevoegd</span><span class="sxs-lookup"><span data-stu-id="3a295-122">Change Tags Parameter to Tag, and add parameter alias Tags</span></span>
    + <span data-ttu-id="3a295-123">New-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="3a295-123">New-AzureRmStorageAccount</span></span>
    + <span data-ttu-id="3a295-124">Set-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="3a295-124">Set-AzureRmStorageAccount</span></span>
* <span data-ttu-id="3a295-125">Azure-netwerk</span><span class="sxs-lookup"><span data-stu-id="3a295-125">Azure Network</span></span>
  - <span data-ttu-id="3a295-126">Er is een nieuwe cmdlet toegevoegd voor peering in virtuele netwerken</span><span class="sxs-lookup"><span data-stu-id="3a295-126">New cmdlet added for Virtual Network Peering</span></span>
* <span data-ttu-id="3a295-127">Azure Redis-cache</span><span class="sxs-lookup"><span data-stu-id="3a295-127">Azure Redis Cache</span></span>
  - <span data-ttu-id="3a295-128">Er is een nieuwe cmdlet toegevoegd voor Reset-AzureRmRedisCache</span><span class="sxs-lookup"><span data-stu-id="3a295-128">New cmdlet added for Reset-AzureRmRedisCache</span></span>
  - <span data-ttu-id="3a295-129">Er is een nieuwe cmdlet toegevoegd voor Export-AzureRmRedisCache</span><span class="sxs-lookup"><span data-stu-id="3a295-129">New cmdlet added for Export-AzureRmRedisCache</span></span>
  - <span data-ttu-id="3a295-130">Er is een nieuwe cmdlet toegevoegd voor Import-AzureRmRedisCache</span><span class="sxs-lookup"><span data-stu-id="3a295-130">New cmdlet added for Import-AzureRmRedisCache</span></span>
  - <span data-ttu-id="3a295-131">De cmdlet New-AzureRmRedisCache is gewijzigd en bevat nu een parameterwijziging voor VNet's</span><span class="sxs-lookup"><span data-stu-id="3a295-131">Modified cmdlet New-AzureRmRedisCache to include parameter change for vNet</span></span>
* <span data-ttu-id="3a295-132">Azure SQL DB Backup/Restore</span><span class="sxs-lookup"><span data-stu-id="3a295-132">Azure SQL DB Backup/Restore</span></span>
  - <span data-ttu-id="3a295-133">Cmdlets voor back-upfunctie voor langetermijnbewaarperiode</span><span class="sxs-lookup"><span data-stu-id="3a295-133">Cmdlets for LTR (Long Term Retention) backup feature</span></span>
  - <span data-ttu-id="3a295-134">Get-AzureRmSqlServerBackupLongTermRetentionVault</span><span class="sxs-lookup"><span data-stu-id="3a295-134">Get-AzureRmSqlServerBackupLongTermRetentionVault</span></span>
  - <span data-ttu-id="3a295-135">Get-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span><span class="sxs-lookup"><span data-stu-id="3a295-135">Get-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span></span>
  - <span data-ttu-id="3a295-136">Set-AzureRmSqlServerBackupLongTermRetentionVault</span><span class="sxs-lookup"><span data-stu-id="3a295-136">Set-AzureRmSqlServerBackupLongTermRetentionVault</span></span>
  - <span data-ttu-id="3a295-137">Set-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span><span class="sxs-lookup"><span data-stu-id="3a295-137">Set-AzureRmSqlDatabaseBackupLongTermRetentionPolicy</span></span>
  - <span data-ttu-id="3a295-138">Restore-AzureRmSqlDatabase ondersteunt nu het terugzetten van een verwijderde database naar een eerder tijdstip</span><span class="sxs-lookup"><span data-stu-id="3a295-138">Restore-AzureRmSqlDatabase now supports point-in-time restore of a deleted database</span></span>
  - <span data-ttu-id="3a295-139">Restore-AzureRmSqlDatabase ondersteunt nu het terugzetten van een back-up die voor de lange termijn wordt bewaard</span><span class="sxs-lookup"><span data-stu-id="3a295-139">Restore-AzureRmSqlDatabase now supports restoring from a Long Term Retention backup</span></span>
* <span data-ttu-id="3a295-140">Azure LogicApp</span><span class="sxs-lookup"><span data-stu-id="3a295-140">Azure LogicApp</span></span>
  - <span data-ttu-id="3a295-141">LogicApp-integratieaccount-cmdlets zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3a295-141">Added LogicApp Integration accounts cmdlets.</span></span>
  - <span data-ttu-id="3a295-142">Get-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="3a295-142">Get-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="3a295-143">Get-AzureRmIntegrationAccountCallbackUrl</span><span class="sxs-lookup"><span data-stu-id="3a295-143">Get-AzureRmIntegrationAccountCallbackUrl</span></span>
  - <span data-ttu-id="3a295-144">Get-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="3a295-144">Get-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="3a295-145">Get-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="3a295-145">Get-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="3a295-146">Get-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="3a295-146">Get-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="3a295-147">Get-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="3a295-147">Get-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="3a295-148">Get-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="3a295-148">Get-AzureRmIntegrationAccountSchema</span></span>
  - <span data-ttu-id="3a295-149">New-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="3a295-149">New-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="3a295-150">New-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="3a295-150">New-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="3a295-151">New-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="3a295-151">New-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="3a295-152">New-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="3a295-152">New-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="3a295-153">New-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="3a295-153">New-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="3a295-154">New-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="3a295-154">New-AzureRmIntegrationAccountSchema</span></span>
  - <span data-ttu-id="3a295-155">Remove-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="3a295-155">Remove-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="3a295-156">Remove-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="3a295-156">Remove-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="3a295-157">Remove-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="3a295-157">Remove-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="3a295-158">Remove-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="3a295-158">Remove-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="3a295-159">Remove-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="3a295-159">Remove-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="3a295-160">Remove-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="3a295-160">Remove-AzureRmIntegrationAccountSchema</span></span>
  - <span data-ttu-id="3a295-161">Set-AzureRmIntegrationAccountAgreement</span><span class="sxs-lookup"><span data-stu-id="3a295-161">Set-AzureRmIntegrationAccountAgreement</span></span>
  - <span data-ttu-id="3a295-162">Set-AzureRmIntegrationAccountCertificate</span><span class="sxs-lookup"><span data-stu-id="3a295-162">Set-AzureRmIntegrationAccountCertificate</span></span>
  - <span data-ttu-id="3a295-163">Set-AzureRmIntegrationAccount</span><span class="sxs-lookup"><span data-stu-id="3a295-163">Set-AzureRmIntegrationAccount</span></span>
  - <span data-ttu-id="3a295-164">Set-AzureRmIntegrationAccountMap</span><span class="sxs-lookup"><span data-stu-id="3a295-164">Set-AzureRmIntegrationAccountMap</span></span>
  - <span data-ttu-id="3a295-165">Set-AzureRmIntegrationAccountPartner</span><span class="sxs-lookup"><span data-stu-id="3a295-165">Set-AzureRmIntegrationAccountPartner</span></span>
  - <span data-ttu-id="3a295-166">Set-AzureRmIntegrationAccountSchema</span><span class="sxs-lookup"><span data-stu-id="3a295-166">Set-AzureRmIntegrationAccountSchema</span></span>
* <span data-ttu-id="3a295-167">Azure Data Lake Store</span><span class="sxs-lookup"><span data-stu-id="3a295-167">Azure Data Lake Store</span></span>
  - <span data-ttu-id="3a295-168">De prestaties met betrekking tot het uploaden en downloaden van bestanden en mappen zijn aanzienlijk verbeterd.</span><span class="sxs-lookup"><span data-stu-id="3a295-168">Drastically improve performance of file and folder upload and download.</span></span>
  - <span data-ttu-id="3a295-169">Dit omvat een kleine wijziging met betrekking tot de parameternamen voor het downloaden en de opname van twee nieuwe parameters voor het uploaden:</span><span class="sxs-lookup"><span data-stu-id="3a295-169">This includes a slight change to the parameter names for download and inclusion of two new parameters for upload:</span></span>
    + <span data-ttu-id="3a295-170">NumThreads -> PerFileThreadCount: deze parameter wordt gebruikt om het aantal threads aan te geven die in een enkel bestand moeten worden gebruikt</span><span class="sxs-lookup"><span data-stu-id="3a295-170">NumThreads -> PerFileThreadCount, used to indicate the number of threads to use in a single file</span></span>
    + <span data-ttu-id="3a295-171">ConcurrentFileCount: deze parameter wordt gebruikt om het aantal bestanden aan te geven dat samen met het uploaden/downloaden van een map moet worden geüpload/gedownload.</span><span class="sxs-lookup"><span data-stu-id="3a295-171">ConcurrentFileCount, used to indicate the number of files to upload/download in parallel for folder upload/download.</span></span>
  - <span data-ttu-id="3a295-172">Er zijn nu standaardthreadingwaarden ontworpen om een betere gehele doorvoer voor de meeste bestandsgrootten te bieden.</span><span class="sxs-lookup"><span data-stu-id="3a295-172">Default threading values are now designed to give a better all around throughput for most file sizes.</span></span> <span data-ttu-id="3a295-173">Als de prestaties niet aan uw wensen voldoen, kunnen de bovenstaande waarden worden gewijzigd om aan de vereisten te voldoen.</span><span class="sxs-lookup"><span data-stu-id="3a295-173">If performance is not as desired, the values above can be modified to meet requirements.</span></span>
* <span data-ttu-id="3a295-174">Azure Data Lake Analytics</span><span class="sxs-lookup"><span data-stu-id="3a295-174">Azure Data Lake Analytics</span></span>
  - <span data-ttu-id="3a295-175">Get-AzureRMDataLakeAnalyticsDataSource retourneert nu alle gegevensbronnen wanneer deze worden aangeroepen zonder argumenten.</span><span class="sxs-lookup"><span data-stu-id="3a295-175">Get-AzureRMDataLakeAnalyticsDataSource now returns all data sources when called with no arguments.</span></span>
  - <span data-ttu-id="3a295-176">Deze wijziging verwijdert ook het type gegevensbronparameter van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a295-176">This change also removes the data source type parameter from the cmdlet.</span></span>
  - <span data-ttu-id="3a295-177">Deze wijziging resulteert in een nieuw object dat voor de lijstbewerking wordt geretourneerd en de volgende eigenschappen heeft:</span><span class="sxs-lookup"><span data-stu-id="3a295-177">This change results in a new object being returned for the list operation with the following properties:</span></span>
    + <span data-ttu-id="3a295-178">Type: het type gegevensbron</span><span class="sxs-lookup"><span data-stu-id="3a295-178">Type, the type of data source</span></span>
    + <span data-ttu-id="3a295-179">Name: de naam van de gegevensbron</span><span class="sxs-lookup"><span data-stu-id="3a295-179">Name, the name of the data source</span></span>
    + <span data-ttu-id="3a295-180">IsDefault is ingesteld op 'true' als dit de standaardgegevensbron voor het account is</span><span class="sxs-lookup"><span data-stu-id="3a295-180">IsDefault, set to true if this is the default data source for the account</span></span>
  - <span data-ttu-id="3a295-181">Het probleem met Get-AzureRMDataLakeAnalyticsJob is verholpen voor een lijst met bepaalde offsetwaarden voor datum en tijd wanneer er op submittedBefore en submittedAfter wordt gefilterd.</span><span class="sxs-lookup"><span data-stu-id="3a295-181">Get-AzureRMDataLakeAnalyticsJob fixed for list for certain date time offset values when filtering on submittedBefore and submittedAfter.</span></span>
* <span data-ttu-id="3a295-182">Web Apps</span><span class="sxs-lookup"><span data-stu-id="3a295-182">Web Apps</span></span>
  - <span data-ttu-id="3a295-183">Swap-AzureRmWebAppSlot-cmdlet voor regulier wisselen en wisselen met preview is toegevoegd</span><span class="sxs-lookup"><span data-stu-id="3a295-183">Add Swap-AzureRmWebAppSlot cmdlet for regular swap and swap with preview</span></span>
  - <span data-ttu-id="3a295-184">Set-AzureRmWebAppSlot-cmdlet om automatisch wisselen te ondersteunen, is uitgebreid</span><span class="sxs-lookup"><span data-stu-id="3a295-184">Extend Set-AzureRmWebAppSlot cmdlet to support auto swap</span></span>
* <span data-ttu-id="3a295-185">Azure API Management</span><span class="sxs-lookup"><span data-stu-id="3a295-185">Azure API Management</span></span>
  - <span data-ttu-id="3a295-186">Het probleem met de Azure API Management Deployment-cmdlets voor AzureChinaCloud is verholpen.</span><span class="sxs-lookup"><span data-stu-id="3a295-186">Fixed Azure Api Management Deployment cmdlets for AzureChinaCloud.</span></span>
  - <span data-ttu-id="3a295-187">De cmdlet Set-AzureRmApiManagementTenantGitAccess is verwijderd, aangezien Git Access standaard is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="3a295-187">Removed cmdlet Set-AzureRmApiManagementTenantGitAccess as Git Access is enabled by Default.</span></span>
* <span data-ttu-id="3a295-188">Azure Recovery Services Backup</span><span class="sxs-lookup"><span data-stu-id="3a295-188">Azure Recovery Services Backup</span></span>
  - <span data-ttu-id="3a295-189">Er is ondersteuning toegevoegd voor de Azure SQL-workload</span><span class="sxs-lookup"><span data-stu-id="3a295-189">Added support for the Azure SQL workload</span></span>
  - <span data-ttu-id="3a295-190">Er is ondersteuning toegevoegd voor het herstellen en het maken van back-ups van versleutelde virtuele Azure-machines</span><span class="sxs-lookup"><span data-stu-id="3a295-190">Added support for backing up and restoring encrypted Azure VMs</span></span>
  - <span data-ttu-id="3a295-191">Backup-AzureRmRecoveryServicesBackupItem: er is een optionele bewaartijdfunctie voor herstelpunten toegevoegd</span><span class="sxs-lookup"><span data-stu-id="3a295-191">Backup-AzureRmRecoveryServicesBackupItem - Added optional retention time feature for recovery points</span></span>
  - <span data-ttu-id="3a295-192">Oplossingen voor kleine filtergerelateerde problemen in de cmdlets Get-AzureRmRecoveryServicesBackupContainer en Get-AzureRmRecoveryServicesBackupItem</span><span class="sxs-lookup"><span data-stu-id="3a295-192">Minor filter-related bug fixes in Get-AzureRmRecoveryServicesBackupContainer and Get-AzureRmRecoveryServicesBackupItem cmdlets</span></span>
* <span data-ttu-id="3a295-193">Azure Automation</span><span class="sxs-lookup"><span data-stu-id="3a295-193">Azure Automation</span></span>
  - <span data-ttu-id="3a295-194">Get-AzureRmAutomationHybridWorkerGroup is toegevoegd</span><span class="sxs-lookup"><span data-stu-id="3a295-194">Added Get-AzureRmAutomationHybridWorkerGroup</span></span>
