# <a name="table-of-contents"></a><span data-ttu-id="78581-101">Inhoudsopgave</span><span class="sxs-lookup"><span data-stu-id="78581-101">Table of Contents</span></span>
1. [<span data-ttu-id="78581-102">Verwijdering van de Force-parameters</span><span class="sxs-lookup"><span data-stu-id="78581-102">Removal of Force parameters</span></span>](#removal-of-force-parameters)
2. [<span data-ttu-id="78581-103">Wijziging aan Tag-parameters</span><span class="sxs-lookup"><span data-stu-id="78581-103">Change of Tag parameters</span></span>](#change-of-tag-parameters)
3. [<span data-ttu-id="78581-104">Belangrijke wijzigingen voor Storage-cmdlets</span><span class="sxs-lookup"><span data-stu-id="78581-104">Breaking changes to Storage cmdlets</span></span>](#breaking-changes-to-storage-cmdlets)
4. [<span data-ttu-id="78581-105">Belangrijke wijzigingen voor AD-cmdlets</span><span class="sxs-lookup"><span data-stu-id="78581-105">Breaking changes to AD cmdlets</span></span>](#breaking-changes-to-ad-cmdlets)

## <a name="removal-of-force-parameters"></a><span data-ttu-id="78581-106">Verwijdering van de Force-parameters</span><span class="sxs-lookup"><span data-stu-id="78581-106">Removal of Force parameters</span></span>

<span data-ttu-id="78581-107">In deze release hebben we alle verouderde `Force`-parameters van de cmdlets verwijderd, evenals de bijbehorende waarschuwingen dat de parameter in een toekomstige release zal worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="78581-107">This release, we removed all Obsolete `Force` parameters from cmdlets and the corresponding warnings that the parameter would be removed in a future release.</span></span>

<span data-ttu-id="78581-108">De volgende cmdlets worden beïnvloed door deze wijziging:</span><span class="sxs-lookup"><span data-stu-id="78581-108">The following cmdlets are affected by this change:</span></span>

<span data-ttu-id="78581-109">**ApiManagement**</span><span class="sxs-lookup"><span data-stu-id="78581-109">**ApiManagement**</span></span>
- <span data-ttu-id="78581-110">Remove-AzureRmApiManagement</span><span class="sxs-lookup"><span data-stu-id="78581-110">Remove-AzureRmApiManagement</span></span>
- <span data-ttu-id="78581-111">Remove-AzureRmApiManagementApi</span><span class="sxs-lookup"><span data-stu-id="78581-111">Remove-AzureRmApiManagementApi</span></span>
- <span data-ttu-id="78581-112">Remove-AzureRmApiManagementGroup</span><span class="sxs-lookup"><span data-stu-id="78581-112">Remove-AzureRmApiManagementGroup</span></span>
- <span data-ttu-id="78581-113">Remove-AzureRmApiManagementLogger</span><span class="sxs-lookup"><span data-stu-id="78581-113">Remove-AzureRmApiManagementLogger</span></span>
- <span data-ttu-id="78581-114">Remove-AzureRmApiManagementOpenIdConnectProvider</span><span class="sxs-lookup"><span data-stu-id="78581-114">Remove-AzureRmApiManagementOpenIdConnectProvider</span></span>
- <span data-ttu-id="78581-115">Remove-AzureRmApiManagementOperation</span><span class="sxs-lookup"><span data-stu-id="78581-115">Remove-AzureRmApiManagementOperation</span></span>
- <span data-ttu-id="78581-116">Remove-AzureRmApiManagementPolicy</span><span class="sxs-lookup"><span data-stu-id="78581-116">Remove-AzureRmApiManagementPolicy</span></span>
- <span data-ttu-id="78581-117">Remove-AzureRmApiManagementProduct</span><span class="sxs-lookup"><span data-stu-id="78581-117">Remove-AzureRmApiManagementProduct</span></span>
- <span data-ttu-id="78581-118">Remove-AzureRmApiManagementProperty</span><span class="sxs-lookup"><span data-stu-id="78581-118">Remove-AzureRmApiManagementProperty</span></span>
- <span data-ttu-id="78581-119">Remove-AzureRmApiManagementSubscription</span><span class="sxs-lookup"><span data-stu-id="78581-119">Remove-AzureRmApiManagementSubscription</span></span>
- <span data-ttu-id="78581-120">Remove-AzureRmApiManagementUser</span><span class="sxs-lookup"><span data-stu-id="78581-120">Remove-AzureRmApiManagementUser</span></span>

<span data-ttu-id="78581-121">**Automatisering**</span><span class="sxs-lookup"><span data-stu-id="78581-121">**Automation**</span></span>
- <span data-ttu-id="78581-122">Remove-AzureRmAutomationCertificate</span><span class="sxs-lookup"><span data-stu-id="78581-122">Remove-AzureRmAutomationCertificate</span></span>
- <span data-ttu-id="78581-123">Remove-AzureRmAutomationCredential</span><span class="sxs-lookup"><span data-stu-id="78581-123">Remove-AzureRmAutomationCredential</span></span>
- <span data-ttu-id="78581-124">Remove-AzureRmAutomationVariable</span><span class="sxs-lookup"><span data-stu-id="78581-124">Remove-AzureRmAutomationVariable</span></span>
- <span data-ttu-id="78581-125">Remove-AzureRmAutomationWebhook</span><span class="sxs-lookup"><span data-stu-id="78581-125">Remove-AzureRmAutomationWebhook</span></span>

<span data-ttu-id="78581-126">**Batch**</span><span class="sxs-lookup"><span data-stu-id="78581-126">**Batch**</span></span>
- <span data-ttu-id="78581-127">Remove-AzureBatchCertificate</span><span class="sxs-lookup"><span data-stu-id="78581-127">Remove-AzureBatchCertificate</span></span>
- <span data-ttu-id="78581-128">Remove-AzureBatchComputeNode</span><span class="sxs-lookup"><span data-stu-id="78581-128">Remove-AzureBatchComputeNode</span></span>
- <span data-ttu-id="78581-129">Remove-AzureBatchComputeNodeUser</span><span class="sxs-lookup"><span data-stu-id="78581-129">Remove-AzureBatchComputeNodeUser</span></span>

<span data-ttu-id="78581-130">**DataFactories**</span><span class="sxs-lookup"><span data-stu-id="78581-130">**DataFactories**</span></span>
- <span data-ttu-id="78581-131">Resume-AzureRmDataFactoryPipeline</span><span class="sxs-lookup"><span data-stu-id="78581-131">Resume-AzureRmDataFactoryPipeline</span></span>
- <span data-ttu-id="78581-132">Set-AzureRmDataFactoryPipelineActivePeriod</span><span class="sxs-lookup"><span data-stu-id="78581-132">Set-AzureRmDataFactoryPipelineActivePeriod</span></span>
- <span data-ttu-id="78581-133">Suspend-AzureRmDataFactoryPipeline</span><span class="sxs-lookup"><span data-stu-id="78581-133">Suspend-AzureRmDataFactoryPipeline</span></span>

<span data-ttu-id="78581-134">**DataLakeStore**</span><span class="sxs-lookup"><span data-stu-id="78581-134">**DataLakeStore**</span></span>
- <span data-ttu-id="78581-135">Remove-AzureRmDataLakeStoreItemAclEntry</span><span class="sxs-lookup"><span data-stu-id="78581-135">Remove-AzureRmDataLakeStoreItemAclEntry</span></span>
- <span data-ttu-id="78581-136">Set-AzureRmDataLakeStoreItemAcl</span><span class="sxs-lookup"><span data-stu-id="78581-136">Set-AzureRmDataLakeStoreItemAcl</span></span>
- <span data-ttu-id="78581-137">Set-AzureRmDataLakeStoreItemAclEntry</span><span class="sxs-lookup"><span data-stu-id="78581-137">Set-AzureRmDataLakeStoreItemAclEntry</span></span>
- <span data-ttu-id="78581-138">Set-AzureRmDataLakeStoreItemOwner</span><span class="sxs-lookup"><span data-stu-id="78581-138">Set-AzureRmDataLakeStoreItemOwner</span></span>

<span data-ttu-id="78581-139">**OperationalInsights**</span><span class="sxs-lookup"><span data-stu-id="78581-139">**OperationalInsights**</span></span>
- <span data-ttu-id="78581-140">Remove-AzureRmOperationalInsightsSavedSearch</span><span class="sxs-lookup"><span data-stu-id="78581-140">Remove-AzureRmOperationalInsightsSavedSearch</span></span>

<span data-ttu-id="78581-141">**Profiel**</span><span class="sxs-lookup"><span data-stu-id="78581-141">**Profile**</span></span>
- <span data-ttu-id="78581-142">Remove-AzureRmEnvironment</span><span class="sxs-lookup"><span data-stu-id="78581-142">Remove-AzureRmEnvironment</span></span>

<span data-ttu-id="78581-143">**RedisCache**</span><span class="sxs-lookup"><span data-stu-id="78581-143">**RedisCache**</span></span>
- <span data-ttu-id="78581-144">Remove-AzureRmRedisCacheDiagnostics</span><span class="sxs-lookup"><span data-stu-id="78581-144">Remove-AzureRmRedisCacheDiagnostics</span></span>

<span data-ttu-id="78581-145">**Bronnen**</span><span class="sxs-lookup"><span data-stu-id="78581-145">**Resources**</span></span>
- <span data-ttu-id="78581-146">Register-AzureRmProviderFeature</span><span class="sxs-lookup"><span data-stu-id="78581-146">Register-AzureRmProviderFeature</span></span>
- <span data-ttu-id="78581-147">Register-AzureRmResourceProvider</span><span class="sxs-lookup"><span data-stu-id="78581-147">Register-AzureRmResourceProvider</span></span>
- <span data-ttu-id="78581-148">Remove-AzureRmADServicePrincipal</span><span class="sxs-lookup"><span data-stu-id="78581-148">Remove-AzureRmADServicePrincipal</span></span>
- <span data-ttu-id="78581-149">Remove-AzureRmPolicyAssignment</span><span class="sxs-lookup"><span data-stu-id="78581-149">Remove-AzureRmPolicyAssignment</span></span>
- <span data-ttu-id="78581-150">Remove-AzureRmResourceGroupDeployment</span><span class="sxs-lookup"><span data-stu-id="78581-150">Remove-AzureRmResourceGroupDeployment</span></span>
- <span data-ttu-id="78581-151">Remove-AzureRmRoleAssignment</span><span class="sxs-lookup"><span data-stu-id="78581-151">Remove-AzureRmRoleAssignment</span></span>
- <span data-ttu-id="78581-152">Stop-AzureRmResourceGroupDeployment</span><span class="sxs-lookup"><span data-stu-id="78581-152">Stop-AzureRmResourceGroupDeployment</span></span>
- <span data-ttu-id="78581-153">Unregister-AzureRmResourceProvider</span><span class="sxs-lookup"><span data-stu-id="78581-153">Unregister-AzureRmResourceProvider</span></span>

<span data-ttu-id="78581-154">**Storage**</span><span class="sxs-lookup"><span data-stu-id="78581-154">**Storage**</span></span>
- <span data-ttu-id="78581-155">Remove-AzureStorageContainerStoredAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="78581-155">Remove-AzureStorageContainerStoredAccessPolicy</span></span>
- <span data-ttu-id="78581-156">Remove-AzureStorageQueueStoredAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="78581-156">Remove-AzureStorageQueueStoredAccessPolicy</span></span>
- <span data-ttu-id="78581-157">Remove-AzureStorageShareStoredAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="78581-157">Remove-AzureStorageShareStoredAccessPolicy</span></span>
- <span data-ttu-id="78581-158">Remove-AzureStorageTableStoredAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="78581-158">Remove-AzureStorageTableStoredAccessPolicy</span></span>

<span data-ttu-id="78581-159">**StreamAnalytics**</span><span class="sxs-lookup"><span data-stu-id="78581-159">**StreamAnalytics**</span></span>
- <span data-ttu-id="78581-160">Remove-AzureRmStreamAnalyticsFunction</span><span class="sxs-lookup"><span data-stu-id="78581-160">Remove-AzureRmStreamAnalyticsFunction</span></span>
- <span data-ttu-id="78581-161">Remove-AzureRmStreamAnalyticsInput</span><span class="sxs-lookup"><span data-stu-id="78581-161">Remove-AzureRmStreamAnalyticsInput</span></span>
- <span data-ttu-id="78581-162">Remove-AzureRmStreamAnalyticsJob</span><span class="sxs-lookup"><span data-stu-id="78581-162">Remove-AzureRmStreamAnalyticsJob</span></span>
- <span data-ttu-id="78581-163">Remove-AzureRmStreamAnalyticsOutput</span><span class="sxs-lookup"><span data-stu-id="78581-163">Remove-AzureRmStreamAnalyticsOutput</span></span>

<span data-ttu-id="78581-164">**Tag**</span><span class="sxs-lookup"><span data-stu-id="78581-164">**Tag**</span></span>
- <span data-ttu-id="78581-165">Remove-AzureRmTag</span><span class="sxs-lookup"><span data-stu-id="78581-165">Remove-AzureRmTag</span></span>

<br>

<span data-ttu-id="78581-166">Als u een script hebt dat gebruikmaakt van een van de bovenstaande cmdlets, kunt u de gevolgen van deze belangrijke wijziging eenvoudig oplossen door de `Force`-parameter te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="78581-166">If you have a script that uses any of the above cmdlets, the breaking change can be fixed by simply removing the `Force` parameter.</span></span>

```powershell
# Old
New-AzureRmResourceGroup -Name $resourceGroupName -Location $location -Force

# New
New-AzureRmResourceGroup -Name $resourceGroupName -Location $location
```

<br>

## <a name="change-of-tag-parameters"></a><span data-ttu-id="78581-167">Wijziging aan Tag-parameters</span><span class="sxs-lookup"><span data-stu-id="78581-167">Change of Tag parameters</span></span>

<span data-ttu-id="78581-168">In deze release is de parameternaam `Tags` gewijzigd in `Tag` en is het type gewijzigd van `Hashtable[]` in `Hashtable`, wat gevolgen heeft voor de indeling van sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="78581-168">This release, the `Tags` parameter name was changed to `Tag`, and the type was changed from `Hashtable[]` to `Hashtable`, changing the format of the key-value pairings.</span></span>

<span data-ttu-id="78581-169">Voorheen werd elk item in de `Hashtable[]` weergegeven met een enkel sleutel-waardepaar:</span><span class="sxs-lookup"><span data-stu-id="78581-169">Previously, each entry in the `Hashtable[]` represented a single key-value pairing:</span></span>

```powershell
$tags = @{ Name = "test1"; Value = "testval1" }, @{ Name = "test2", Value = "testval2" }
$tags[0].Name  # Key for the first entry, "test1"
$tags[0].Value # Value for the first entry, "testval1"
$tags[1].Name  # Key for the second entry, "test2"
$tags[1].Value # Value for the second entry, "testval2"
```

<span data-ttu-id="78581-170">Nu zijn `Name` en `Value` niet langer nodig, waardoor sleutel-waardeparen kunnen worden gemaakt door `Key = "Value"` toe te wijzen in de `Hashtable`:</span><span class="sxs-lookup"><span data-stu-id="78581-170">Now, `Name` and `Value` are no longer necessary, allowing for key-value pairings to be created by assigning `Key = "Value"` in the `Hashtable`:</span></span>

```powershell
$tag = @{ test1 = "testval1"; test2 = "testval2" }
$tag["test1"] # Gets the value associated with the key "test1"
$tag["test2"] # Gets the value associated with the key "test2"
```

<span data-ttu-id="78581-171">De volgende cmdlets worden beïnvloed door deze wijziging:</span><span class="sxs-lookup"><span data-stu-id="78581-171">The following cmdlets are affected by this change:</span></span>

<span data-ttu-id="78581-172">**Batch**</span><span class="sxs-lookup"><span data-stu-id="78581-172">**Batch**</span></span>
- <span data-ttu-id="78581-173">Get-AzureRmBatchAccount</span><span class="sxs-lookup"><span data-stu-id="78581-173">Get-AzureRmBatchAccount</span></span>
- <span data-ttu-id="78581-174">New-AzureRmBatchAccount</span><span class="sxs-lookup"><span data-stu-id="78581-174">New-AzureRmBatchAccount</span></span>
- <span data-ttu-id="78581-175">Set-AzureRmBatchAccount</span><span class="sxs-lookup"><span data-stu-id="78581-175">Set-AzureRmBatchAccount</span></span>

<span data-ttu-id="78581-176">**Compute**</span><span class="sxs-lookup"><span data-stu-id="78581-176">**Compute**</span></span>
- <span data-ttu-id="78581-177">New-AzureRmVM</span><span class="sxs-lookup"><span data-stu-id="78581-177">New-AzureRmVM</span></span>
- <span data-ttu-id="78581-178">Update-AzureRmVM</span><span class="sxs-lookup"><span data-stu-id="78581-178">Update-AzureRmVM</span></span>

<span data-ttu-id="78581-179">**DataLakeAnalytics**</span><span class="sxs-lookup"><span data-stu-id="78581-179">**DataLakeAnalytics**</span></span>
- <span data-ttu-id="78581-180">New-AzureRmDataLakeAnalyticsAccount</span><span class="sxs-lookup"><span data-stu-id="78581-180">New-AzureRmDataLakeAnalyticsAccount</span></span>
- <span data-ttu-id="78581-181">Set-AzureRmDataLakeAnalyticsAccount</span><span class="sxs-lookup"><span data-stu-id="78581-181">Set-AzureRmDataLakeAnalyticsAccount</span></span>

<span data-ttu-id="78581-182">**DataLakeStore**</span><span class="sxs-lookup"><span data-stu-id="78581-182">**DataLakeStore**</span></span>
- <span data-ttu-id="78581-183">New-AzureRmDataLakeStoreAccount</span><span class="sxs-lookup"><span data-stu-id="78581-183">New-AzureRmDataLakeStoreAccount</span></span>
- <span data-ttu-id="78581-184">Set-AzureRmDataLakeStoreAccount</span><span class="sxs-lookup"><span data-stu-id="78581-184">Set-AzureRmDataLakeStoreAccount</span></span>

<span data-ttu-id="78581-185">**Dns**</span><span class="sxs-lookup"><span data-stu-id="78581-185">**Dns**</span></span>
- <span data-ttu-id="78581-186">New-AzureRmDnsZone</span><span class="sxs-lookup"><span data-stu-id="78581-186">New-AzureRmDnsZone</span></span>
- <span data-ttu-id="78581-187">Set-AzureRmDnsZone</span><span class="sxs-lookup"><span data-stu-id="78581-187">Set-AzureRmDnsZone</span></span>

<span data-ttu-id="78581-188">**KeyVault**</span><span class="sxs-lookup"><span data-stu-id="78581-188">**KeyVault**</span></span>
- <span data-ttu-id="78581-189">Get-AzureRmKeyVault</span><span class="sxs-lookup"><span data-stu-id="78581-189">Get-AzureRmKeyVault</span></span>
- <span data-ttu-id="78581-190">New-AzureRmKeyVault</span><span class="sxs-lookup"><span data-stu-id="78581-190">New-AzureRmKeyVault</span></span>

<span data-ttu-id="78581-191">**Netwerk**</span><span class="sxs-lookup"><span data-stu-id="78581-191">**Network**</span></span>
- <span data-ttu-id="78581-192">New-AzureRmApplicationGateway</span><span class="sxs-lookup"><span data-stu-id="78581-192">New-AzureRmApplicationGateway</span></span>
- <span data-ttu-id="78581-193">New-AzureRmExpressRouteCircuit</span><span class="sxs-lookup"><span data-stu-id="78581-193">New-AzureRmExpressRouteCircuit</span></span>
- <span data-ttu-id="78581-194">New-AzureRmLoadBalancer</span><span class="sxs-lookup"><span data-stu-id="78581-194">New-AzureRmLoadBalancer</span></span>
- <span data-ttu-id="78581-195">New-AzureRmLocalNetworkGateway</span><span class="sxs-lookup"><span data-stu-id="78581-195">New-AzureRmLocalNetworkGateway</span></span>
- <span data-ttu-id="78581-196">New-AzureRmNetworkInterface</span><span class="sxs-lookup"><span data-stu-id="78581-196">New-AzureRmNetworkInterface</span></span>
- <span data-ttu-id="78581-197">New-AzureRmNetworkSecurityGroup</span><span class="sxs-lookup"><span data-stu-id="78581-197">New-AzureRmNetworkSecurityGroup</span></span>
- <span data-ttu-id="78581-198">New-AzureRmPublicIpAddress</span><span class="sxs-lookup"><span data-stu-id="78581-198">New-AzureRmPublicIpAddress</span></span>
- <span data-ttu-id="78581-199">New-AzureRmRouteTable</span><span class="sxs-lookup"><span data-stu-id="78581-199">New-AzureRmRouteTable</span></span>
- <span data-ttu-id="78581-200">New-AzureRmVirtualNetwork</span><span class="sxs-lookup"><span data-stu-id="78581-200">New-AzureRmVirtualNetwork</span></span>
- <span data-ttu-id="78581-201">New-AzureRmVirtualNetworkGateway</span><span class="sxs-lookup"><span data-stu-id="78581-201">New-AzureRmVirtualNetworkGateway</span></span>
- <span data-ttu-id="78581-202">New-AzureRmVirtualNetworkGatewayConnection</span><span class="sxs-lookup"><span data-stu-id="78581-202">New-AzureRmVirtualNetworkGatewayConnection</span></span>
- <span data-ttu-id="78581-203">New-AzureRmVirtualNetworkPeering</span><span class="sxs-lookup"><span data-stu-id="78581-203">New-AzureRmVirtualNetworkPeering</span></span>

<span data-ttu-id="78581-204">**Bronnen**</span><span class="sxs-lookup"><span data-stu-id="78581-204">**Resources**</span></span>
- <span data-ttu-id="78581-205">Find-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="78581-205">Find-AzureRmResource</span></span>
- <span data-ttu-id="78581-206">Find-AzureRmResourceGroup</span><span class="sxs-lookup"><span data-stu-id="78581-206">Find-AzureRmResourceGroup</span></span>
- <span data-ttu-id="78581-207">New-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="78581-207">New-AzureRmResource</span></span>
- <span data-ttu-id="78581-208">New-AzureRmResourceGroup</span><span class="sxs-lookup"><span data-stu-id="78581-208">New-AzureRmResourceGroup</span></span>
- <span data-ttu-id="78581-209">Set-AzureRmResource</span><span class="sxs-lookup"><span data-stu-id="78581-209">Set-AzureRmResource</span></span>
- <span data-ttu-id="78581-210">Set-AzureRmResourceGroup</span><span class="sxs-lookup"><span data-stu-id="78581-210">Set-AzureRmResourceGroup</span></span>

<span data-ttu-id="78581-211">**SQL**</span><span class="sxs-lookup"><span data-stu-id="78581-211">**SQL**</span></span>
- <span data-ttu-id="78581-212">New-AzureRmSqlDatabase</span><span class="sxs-lookup"><span data-stu-id="78581-212">New-AzureRmSqlDatabase</span></span>
- <span data-ttu-id="78581-213">New-AzureRmSqlDatabaseCopy</span><span class="sxs-lookup"><span data-stu-id="78581-213">New-AzureRmSqlDatabaseCopy</span></span>
- <span data-ttu-id="78581-214">New-AzureRmSqlDatabaseSecondary</span><span class="sxs-lookup"><span data-stu-id="78581-214">New-AzureRmSqlDatabaseSecondary</span></span>
- <span data-ttu-id="78581-215">New-AzureRmSqlElasticPool</span><span class="sxs-lookup"><span data-stu-id="78581-215">New-AzureRmSqlElasticPool</span></span>
- <span data-ttu-id="78581-216">New-AzureRmSqlServer</span><span class="sxs-lookup"><span data-stu-id="78581-216">New-AzureRmSqlServer</span></span>
- <span data-ttu-id="78581-217">Set-AzureRmSqlDatabase</span><span class="sxs-lookup"><span data-stu-id="78581-217">Set-AzureRmSqlDatabase</span></span>
- <span data-ttu-id="78581-218">Set-AzureRmSqlElasticPool</span><span class="sxs-lookup"><span data-stu-id="78581-218">Set-AzureRmSqlElasticPool</span></span>
- <span data-ttu-id="78581-219">Set-AzureRmSqlServer</span><span class="sxs-lookup"><span data-stu-id="78581-219">Set-AzureRmSqlServer</span></span>

<span data-ttu-id="78581-220">**Storage**</span><span class="sxs-lookup"><span data-stu-id="78581-220">**Storage**</span></span>
- <span data-ttu-id="78581-221">New-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="78581-221">New-AzureRmStorageAccount</span></span>
- <span data-ttu-id="78581-222">Set-AzureRmStorageAccount</span><span class="sxs-lookup"><span data-stu-id="78581-222">Set-AzureRmStorageAccount</span></span>

<span data-ttu-id="78581-223">**TrafficManager**</span><span class="sxs-lookup"><span data-stu-id="78581-223">**TrafficManager**</span></span>
- <span data-ttu-id="78581-224">New-AzureRmTrafficManagerProfile</span><span class="sxs-lookup"><span data-stu-id="78581-224">New-AzureRmTrafficManagerProfile</span></span>

<br>

<span data-ttu-id="78581-225">Als u een script hebt dat gebruikmaakt van een van de bovenstaande cmdlets, kunt u de gevolgen van deze belangrijke wijziging eenvoudig oplossen door de `Tags`-parameter te wijzigen in `Tag` en `Tag` aan te passen aan de nieuwe indeling.</span><span class="sxs-lookup"><span data-stu-id="78581-225">If you have a script that uses any of the above cmdlets, the breaking change can be fixed by changing the `Tags` parameter to `Tag`, as well as changing the `Tag` to the new format.</span></span>

```powershell
# Old
New-AzureRmResourceGroup -Name $resourceGroupName -Location -location -Tags @{ Name = "testtag"; Value = "testval" }

# New
New-AzureRmResourceGroup -Name $resourceGroupName -Location -location -Tag @{ testtag = "testval" }
```

<br>

## <a name="breaking-changes-to-storage-cmdlets"></a><span data-ttu-id="78581-226">Belangrijke wijzigingen voor Storage-cmdlets</span><span class="sxs-lookup"><span data-stu-id="78581-226">Breaking changes to Storage cmdlets</span></span>

<span data-ttu-id="78581-227">De volgende cmdlets worden beïnvloed door deze release:</span><span class="sxs-lookup"><span data-stu-id="78581-227">The following cmdlets were affected this release:</span></span>

<span data-ttu-id="78581-228">**Get-AzureRmStorageAccountKey**</span><span class="sxs-lookup"><span data-stu-id="78581-228">**Get-AzureRmStorageAccountKey**</span></span>
- <span data-ttu-id="78581-229">De cmdlet retourneert nu een lijst met sleutels in plaats van een object met eigenschappen voor elke sleutel</span><span class="sxs-lookup"><span data-stu-id="78581-229">The cmdlet now returns a list of keys, rather than an object with properties for each key</span></span>

```powershell
# Old
$key = (Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName).Key1

# New
$key = (Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName)[0].Value
```

<span data-ttu-id="78581-230">**New-AzureRmStorageAccountKey**</span><span class="sxs-lookup"><span data-stu-id="78581-230">**New-AzureRmStorageAccountKey**</span></span>
- <span data-ttu-id="78581-231">Het veld `StorageAccountRegenerateKeyResponse` in de uitvoer van deze cmdlet is gewijzigd in `StorageAccountListKeysResults`, wat nu een lijst met sleutels is, in plaats van een object met eigenschappen voor elke sleutel</span><span class="sxs-lookup"><span data-stu-id="78581-231">`StorageAccountRegenerateKeyResponse` field in output of this cmdlet is renamed to `StorageAccountListKeysResults`, which is now a list of keys rather than an object with properties for each key</span></span>

```powershell
# Old
$key = (New-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName).StorageAccountKeys.Key1

# New
$key = (New-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $accountName).Keys[0].Value
```

<span data-ttu-id="78581-232">**New/Get/Set-AzureRmStorageAccount**</span><span class="sxs-lookup"><span data-stu-id="78581-232">**New/Get/Set-AzureRmStorageAccount**</span></span>
- <span data-ttu-id="78581-233">De naam van het veld `AccountType` in de uitvoer van deze cmdlet is gewijzigd in `Sku.Name`</span><span class="sxs-lookup"><span data-stu-id="78581-233">`AccountType` field in output of this cmdlet is renamed to `Sku.Name`</span></span>
- <span data-ttu-id="78581-234">Het uitvoertype voor primaire/secundaire eindpunten voor een blob/tabel/wachtrij/bestand is van `Uri` gewijzigd in `String`</span><span class="sxs-lookup"><span data-stu-id="78581-234">Output type for PrimaryEndpoints/Secondary endpoints blob/table/queue/file changed from `Uri` to `String`</span></span>

```powershell
# Old
$accountType = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).AccountType

# New
$accountType = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).Sku.Name
```

```powershell
# Old 
$blobEndpoint = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).PrimaryEndpoints.Blob.ToString()
$blobEndpoint = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).PrimaryEndpoints.Blob.AbsolutePath

# New
$blobEndpoint = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).PrimaryEndpoints.Blob.ToString()
$blobEndpoint = (Get-AzureRmStorageAccount -ResourceGroupName $resourceGroupName -Name $accountName).PrimaryEndpoints.Blob
```

<br>

## <a name="breaking-changes-to-ad-cmdlets"></a><span data-ttu-id="78581-235">Belangrijke wijzigingen voor AD-cmdlets</span><span class="sxs-lookup"><span data-stu-id="78581-235">Breaking changes to AD cmdlets</span></span>

<span data-ttu-id="78581-236">De volgende cmdlets worden beïnvloed door deze release:</span><span class="sxs-lookup"><span data-stu-id="78581-236">The following cmdlets were affected this release:</span></span>

<span data-ttu-id="78581-237">**Get-AzureRMADServicePrincipal**</span><span class="sxs-lookup"><span data-stu-id="78581-237">**Get-AzureRMADServicePrincipal**</span></span>
- <span data-ttu-id="78581-238">Het veld `ServicePrincipalName` in de uitvoer van deze cmdlet is gewijzigd in `ServicePrincipalNames` en is nu een verzameling.</span><span class="sxs-lookup"><span data-stu-id="78581-238">`ServicePrincipalName` field in output of this cmdlet is renamed to `ServicePrincipalNames` and is now a collection.</span></span> <span data-ttu-id="78581-239">Deze geeft nu `ApplicationId` ook weer als SPN-naam, samen met de identifierUri.</span><span class="sxs-lookup"><span data-stu-id="78581-239">It now displays `ApplicationId` also as one of the SPN, along with the identifierUri.</span></span>

```powershell
# Old
$servicePrincipals = Get-AzureRmADServicePrincipal -SearchString $displayName
$spn = $servicePrincipals[0].ServicePrincipalName

# New
$servicePrincipals = Get-AzureRmADServicePrincipal -SearchString $displayName
$spn = $servicePrincipals[0].ServicePrincipalNames[0]
```

<span data-ttu-id="78581-240">**Get-AzureRmADApplication**</span><span class="sxs-lookup"><span data-stu-id="78581-240">**Get-AzureRmADApplication**</span></span>
- <span data-ttu-id="78581-241">De naam van parameter `ApplicationObjectId` is gewijzigd in `ObjectId`.</span><span class="sxs-lookup"><span data-stu-id="78581-241">Parameter `ApplicationObjectId` is renamed to `ObjectId`.</span></span>
- <span data-ttu-id="78581-242">In de uitvoer van deze cmdlet is de naam van `ApplicationObjectId` gewijzigd in `ObjectId`.</span><span class="sxs-lookup"><span data-stu-id="78581-242">In output of this cmdlet, `ApplicationObjectId` is renamed to `ObjectId`.</span></span>

```powershell
# Old
$app = Get-AzureRmADApplication -ApplicationObjectId $applicationObjectId
$objectId = $app.ApplicationObjectId

# New
$app = Get-AzureRmADApplication -ObjectId $objectId
$objectId = $app.ObjectId
```

<span data-ttu-id="78581-243">**Remove-AzureRmADApplication**</span><span class="sxs-lookup"><span data-stu-id="78581-243">**Remove-AzureRmADApplication**</span></span>
- <span data-ttu-id="78581-244">De naam van parameter `ApplicationObjectId` is gewijzigd in `ObjectId`.</span><span class="sxs-lookup"><span data-stu-id="78581-244">Parameter `ApplicationObjectId` is renamed to `ObjectId`.</span></span>

```powershell
# Old
$app = Remove-AzureRmADApplication -ApplicationObjectId $applicationObjectId -Force

# New
$app = Remove-AzureRmADApplication -ObjectId $objectId -Force
```

<span data-ttu-id="78581-245">**New-AzureRmADApplication**</span><span class="sxs-lookup"><span data-stu-id="78581-245">**New-AzureRmADApplication**</span></span>
- <span data-ttu-id="78581-246">In de uitvoer van deze cmdlet is de naam van `ApplicationObjectId` gewijzigd in `ObjectId`.</span><span class="sxs-lookup"><span data-stu-id="78581-246">In output of this cmdlet, `ApplicationObjectId` is renamed to `ObjectId`.</span></span>
- <span data-ttu-id="78581-247">De parameters `KeyValue`, `KeyUsage` en `KeyType` zijn verwijderd.</span><span class="sxs-lookup"><span data-stu-id="78581-247">`KeyValue`, `KeyUsage`, `KeyType` parameters are removed.</span></span>

```powershell
# Old
$app = New-AzureRmADApplication -DisplayName $displayName -HomePage $homePage -IdentifierUris $identifierUris -KeyValue $kv -KeyType $kt -KeyUsage $ku
$id = $app.ApplicationObjectId

# New
$app = New-AzureRmADApplication -DisplayName $displayName -HomePage $homePage -IdentifierUris $identifierUris
$id = $app.ObjectId
New-AzureRmADAppCredential -ObjectId $id -Password $kv
```

<span data-ttu-id="78581-248">**Get-AzureRmADGroup**</span><span class="sxs-lookup"><span data-stu-id="78581-248">**Get-AzureRmADGroup**</span></span>
- <span data-ttu-id="78581-249">Het veld `Mail` is verwijderd uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="78581-249">`Mail` field is removed from the output.</span></span>

<span data-ttu-id="78581-250">**Get-AzureRmADUser**</span><span class="sxs-lookup"><span data-stu-id="78581-250">**Get-AzureRmADUser**</span></span>
- <span data-ttu-id="78581-251">Het veld `Mail` is verwijderd uit de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="78581-251">`Mail` field is removed from the output.</span></span>

<span data-ttu-id="78581-252">**New-AzureRmADServicePrincipal**</span><span class="sxs-lookup"><span data-stu-id="78581-252">**New-AzureRmADServicePrincipal**</span></span>
- <span data-ttu-id="78581-253">De parameter `DisableAccount` is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="78581-253">Removed `DisableAccount` parameter.</span></span>

```powershell
# Old
$servicePrincipal = New-AzureRmADServicePrincipal -DisplayName $displayName -Password $password -DisableAccount true

# New
$servicePrincipal = New-AzureRmADServicePrincipal -DisplayName $displayName -Password $password
Remove-AzureRmADServicePrincipal -ObjectId $servicePrincipal.ObjectId
```