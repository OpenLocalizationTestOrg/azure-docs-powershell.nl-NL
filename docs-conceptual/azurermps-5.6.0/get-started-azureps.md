---
title: Aan de slag met Azure PowerShell | Microsoft Docs
description: ''
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: get-started-article
ms.date: 11/15/2017
ms.openlocfilehash: 24eb3cf1a58ac87d437d3471639cd9c8cec4070e
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="getting-started-with-azure-powershell"></a><span data-ttu-id="6441d-102">Aan de slag met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="6441d-102">Getting started with Azure PowerShell</span></span>

<span data-ttu-id="6441d-103">Azure PowerShell is ontworpen om Azure-resources te beheren vanaf de opdrachtregel en voor het bouwen van automatiseringsscripts die op basis van Azure Resource Manager werken.</span><span class="sxs-lookup"><span data-stu-id="6441d-103">Azure PowerShell is designed for managing and administering Azure resources from the command line, and for building automation scripts that work against the Azure Resource Manager.</span></span> <span data-ttu-id="6441d-104">U kunt PowerShell in uw browser gebruiken met [Azure Cloud Shell](/azure/cloud-shell/overview), of installeren op uw lokale computer en dan gebruiken in een PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="6441d-104">You can use it in your browser with [Azure Cloud Shell](/azure/cloud-shell/overview), or you can install it on your local machine and use it in any PowerShell session.</span></span> <span data-ttu-id="6441d-105">Dit artikel helpt u op weg met het gebruik ervan en leert u wat de belangrijkste concepten zijn die eraan ten grondslag liggen.</span><span class="sxs-lookup"><span data-stu-id="6441d-105">This article helps get you started using it, and teaches you the core concepts behind it.</span></span>

## <a name="connect"></a><span data-ttu-id="6441d-106">Verbinding maken</span><span class="sxs-lookup"><span data-stu-id="6441d-106">Connect</span></span>

<span data-ttu-id="6441d-107">De eenvoudigste manier om te beginnen is door [Cloud Shell te openen](/azure/cloud-shell/quickstart).</span><span class="sxs-lookup"><span data-stu-id="6441d-107">The simplest way to get started is to [launch Cloud Shell](/azure/cloud-shell/quickstart).</span></span>

1. <span data-ttu-id="6441d-108">Open Cloud Shell via de bovenste navigatiebalk van de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="6441d-108">Launch Cloud Shell from the top navigation of the Azure portal.</span></span>

   ![Shell-pictogram](~/media/get-started-azureps/shell-icon.png)

2. <span data-ttu-id="6441d-110">Kies het abonnement dat u wilt gebruiken en maak een opslagaccount.</span><span class="sxs-lookup"><span data-stu-id="6441d-110">Choose the subscription you want to use and create a storage account.</span></span>

   ![Een opslagaccount maken](~/media/get-started-azureps/storage-prompt.png)

<span data-ttu-id="6441d-112">Zodra de opslag is gemaakt, wordt er door Cloud Shell een PowerShell-sessie geopend in de browser.</span><span class="sxs-lookup"><span data-stu-id="6441d-112">Once your storage has been created, the Cloud Shell will open a PowerShell session in the browser.</span></span>

![Cloud Shell voor PowerShell](~/media/get-started-azureps/cloud-powershell.png)

<span data-ttu-id="6441d-114">U kunt ook Azure PowerShell installeren en lokaal gebruiken in een PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="6441d-114">You can also install Azure PowerShell and use it locally in a PowerShell session.</span></span>

## <a name="install-azure-powershell"></a><span data-ttu-id="6441d-115">Azure PowerShell installeren</span><span class="sxs-lookup"><span data-stu-id="6441d-115">Install Azure PowerShell</span></span>

<span data-ttu-id="6441d-116">De eerste stap bestaat eruit dat u moet controleren of de nieuwste versie van Azure PowerShell is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="6441d-116">The first step is to make sure you have the latest version of the Azure PowerShell installed.</span></span> <span data-ttu-id="6441d-117">Zie de [opmerkingen bij de release](./release-notes-azureps.md) voor meer informatie over de nieuwste release.</span><span class="sxs-lookup"><span data-stu-id="6441d-117">For information about the latest release, see the [release notes](./release-notes-azureps.md).</span></span>

1. <span data-ttu-id="6441d-118">[Installeer Azure PowerShell](install-azurerm-ps.md).</span><span class="sxs-lookup"><span data-stu-id="6441d-118">[Install Azure PowerShell](install-azurerm-ps.md).</span></span>

2. <span data-ttu-id="6441d-119">Voer `Get-Module AzureRM -ListAvailable` uit vanaf de opdrachtregel om te controleren of de installatie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="6441d-119">To verify the installation was successful, run `Get-Module AzureRM -ListAvailable` from your command line.</span></span>

## <a name="log-in-to-azure"></a><span data-ttu-id="6441d-120">Meld u aan bij Azure.</span><span class="sxs-lookup"><span data-stu-id="6441d-120">Log in to Azure</span></span>

<span data-ttu-id="6441d-121">Interactief aanmelden:</span><span class="sxs-lookup"><span data-stu-id="6441d-121">Sign on interactively:</span></span>

1. <span data-ttu-id="6441d-122">Typ `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="6441d-122">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="6441d-123">U krijgt een dialoogvenster te zien waarin wordt gevraagd naar uw Azure-referenties.</span><span class="sxs-lookup"><span data-stu-id="6441d-123">You will get dialog box asking for your Azure credentials.</span></span> <span data-ttu-id="6441d-124">Met behulp van de optie '-EnvironmentName' kunt u zich aanmelden bij Azure China of Azure Duitsland.</span><span class="sxs-lookup"><span data-stu-id="6441d-124">Option '-EnvironmentName' can let you login in Azure China or Azure Germany.</span></span>

   <span data-ttu-id="6441d-125">bijvoorbeeld: Login-AzureRmAccount - EnvironmentName AzureChinaCloud</span><span class="sxs-lookup"><span data-stu-id="6441d-125">e.g. Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span></span>

2. <span data-ttu-id="6441d-126">Typ het e-mailadres en het wachtwoord die bij uw account horen.</span><span class="sxs-lookup"><span data-stu-id="6441d-126">Type the email address and password associated with your account.</span></span> <span data-ttu-id="6441d-127">Azure verifieert de referentiegegevens en slaat deze op. Vervolgens wordt het venster gesloten.</span><span class="sxs-lookup"><span data-stu-id="6441d-127">Azure authenticates and saves the credential information, and then closes the window.</span></span>

<span data-ttu-id="6441d-128">Nadat u zich hebt aangemeld bij een Azure-account, kunt u de Azure PowerShell-cmdlets gebruiken om toegang te krijgen tot de resources in uw abonnement en om deze te beheren.</span><span class="sxs-lookup"><span data-stu-id="6441d-128">Once you have signed in to an Azure account, you can use the Azure PowerShell cmdlets to access and manager the resources in your subscription.</span></span>

## <a name="create-a-windows-virtual-machine-using-simple-defaults"></a><span data-ttu-id="6441d-129">Een virtuele Windows-machine maken met behulp van eenvoudige standaardwaarden</span><span class="sxs-lookup"><span data-stu-id="6441d-129">Create a Windows virtual machine using simple defaults</span></span>

<span data-ttu-id="6441d-130">De cmdlet `New-AzureRmVM` biedt een vereenvoudigde syntaxis waarmee u gemakkelijk een nieuwe virtuele machine maakt.</span><span class="sxs-lookup"><span data-stu-id="6441d-130">The `New-AzureRmVM` cmdlet provides a simplified syntax making it easy to create a new virtual machine.</span></span> <span data-ttu-id="6441d-131">Er zijn slechts twee parameterwaarden die u moet opgeven: de naam van de VM en een set referenties voor het lokale beheerdersaccount op de VM.</span><span class="sxs-lookup"><span data-stu-id="6441d-131">There are only two parameter values you must provide: the name of the VM and a set of credentials for the local administrator account on the VM.</span></span>

<span data-ttu-id="6441d-132">Maak eerst het referentieobject.</span><span class="sxs-lookup"><span data-stu-id="6441d-132">First, create the credential object.</span></span>

```powershell
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

```Output
Windows PowerShell credential request.
Enter a username and password for the virtual machine.
User: localAdmin
Password for user localAdmin: *********
```
<span data-ttu-id="6441d-133">Maak vervolgens de VM.</span><span class="sxs-lookup"><span data-stu-id="6441d-133">Next, create the VM.</span></span>

```powershell
New-AzureRmVM -Name SampleVM -Credential $cred
```

```Output
ResourceGroupName        : SampleVM
Id                       : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/SampleVM/providers/Microsoft.Compute/virtualMachines/SampleVM
VmId                     : 43f6275d-ce50-49c8-a831-5d5974006e63
Name                     : SampleVM
Type                     : Microsoft.Compute/virtualMachines
Location                 : eastus
Tags                     : {}
HardwareProfile          : {VmSize}
NetworkProfile           : {NetworkInterfaces}
OSProfile                : {ComputerName, AdminUsername, WindowsConfiguration, Secrets}
ProvisioningState        : Succeeded
StorageProfile           : {ImageReference, OsDisk, DataDisks}
FullyQualifiedDomainName : samplevm-2c0867.eastus.cloudapp.azure.com
```

<span data-ttu-id="6441d-134">Dat was makkelijk.</span><span class="sxs-lookup"><span data-stu-id="6441d-134">That was easy.</span></span> <span data-ttu-id="6441d-135">Maar misschien vraagt u zich af wat er nog meer is gemaakt en hoe de VM is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="6441d-135">But, you may wonder what else is created and how is the VM configured.</span></span> <span data-ttu-id="6441d-136">Bekijk eerst uw resourcegroepen.</span><span class="sxs-lookup"><span data-stu-id="6441d-136">First, let's look at our resource groups.</span></span>

```powershell
Get-AzureRmResourceGroup | Select-Object ResourceGroupName,Location
```

```Output
ResourceGroupName          Location
-----------------          --------
cloud-shell-storage-westus westus
SampleVM                   eastus
```

<span data-ttu-id="6441d-137">De resourcegroep **cloud-shell-storage-westus** wordt gemaakt wanneer u Cloud Shell voor het eerst gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6441d-137">The **cloud-shell-storage-westus** resource group is created the first time you use the Cloud Shell.</span></span> <span data-ttu-id="6441d-138">De resourcegroep **SampleVM** is door de cmdlet `New-AzureRmVM` gemaakt.</span><span class="sxs-lookup"><span data-stu-id="6441d-138">The **SampleVM** resource group was created by the `New-AzureRmVM` cmdlet.</span></span>

<span data-ttu-id="6441d-139">Maar welke andere resources zijn er gemaakt in deze nieuwe resourcegroep?</span><span class="sxs-lookup"><span data-stu-id="6441d-139">Now, what other resources were created in this new resource group?</span></span>

```powershell
Get-AzureRmResource |
  Where ResourceGroupName -eq SampleVM |
    Select-Object ResourceGroupName,Location,ResourceType,Name
```

```Output
ResourceGroupName          Location ResourceType                            Name
-----------------          -------- ------------                            ----
SAMPLEVM                   eastus   Microsoft.Compute/disks                 SampleVM_OsDisk_1_9b286c54b168457fa1f8c47...
SampleVM                   eastus   Microsoft.Compute/virtualMachines       SampleVM
SampleVM                   eastus   Microsoft.Network/networkInterfaces     SampleVM
SampleVM                   eastus   Microsoft.Network/networkSecurityGroups SampleVM
SampleVM                   eastus   Microsoft.Network/publicIPAddresses     SampleVM
SampleVM                   eastus   Microsoft.Network/virtualNetworks       SampleVM
```

<span data-ttu-id="6441d-140">Laten we wat meer informatie ophalen over de VM.</span><span class="sxs-lookup"><span data-stu-id="6441d-140">Let's get some more details about the VM.</span></span> <span data-ttu-id="6441d-141">Deze voorbeelden laten zien hoe u informatie over de installatiekopie van het besturingssysteem ophaalt die is gebruikt om de VM te maken.</span><span class="sxs-lookup"><span data-stu-id="6441d-141">This examples shows how to retrieve information about the OS Image used to create the VM.</span></span>

```powershell
Get-AzureRmVM -Name SampleVM -ResourceGroupName SampleVM |
  Select-Object -ExpandProperty StorageProfile |
    Select-Object -ExpandProperty ImageReference
```

```Output
Publisher : MicrosoftWindowsServer
Offer     : WindowsServer
Sku       : 2016-Datacenter
Version   : latest
Id        :
```

## <a name="create-a-fully-configured-linux-virtual-machine"></a><span data-ttu-id="6441d-142">Een volledig geconfigureerde virtuele Linux-machine maken</span><span class="sxs-lookup"><span data-stu-id="6441d-142">Create a fully configured Linux Virtual Machine</span></span>

<span data-ttu-id="6441d-143">In het vorige voorbeeld werden de vereenvoudigde syntaxis en standaardparameterwaarden gebruikt om een virtuele Windows-machine te maken.</span><span class="sxs-lookup"><span data-stu-id="6441d-143">The previous example used the simplified syntax and default parameter values to create a Windows virtual machine.</span></span> <span data-ttu-id="6441d-144">In dit voorbeeld geven we waarden voor alle opties van de virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="6441d-144">In this example, we provide values for all options of the virtual machine.</span></span>

### <a name="create-a-resource-group"></a><span data-ttu-id="6441d-145">Een resourcegroep maken</span><span class="sxs-lookup"><span data-stu-id="6441d-145">Create a resource group</span></span>

<span data-ttu-id="6441d-146">In dit voorbeeld maken we een resourcegroep.</span><span class="sxs-lookup"><span data-stu-id="6441d-146">For this example we want to create a Resource Group.</span></span> <span data-ttu-id="6441d-147">Resourcegroepen in Azure bieden u een manier voor het beheren van meerdere resources die u op een logische wijze wilt groeperen.</span><span class="sxs-lookup"><span data-stu-id="6441d-147">Resource Groups in Azure provide a way to manage multiple resources that you want to logically group together.</span></span> <span data-ttu-id="6441d-148">U kunt bijvoorbeeld een resourcegroep voor een toepassing of project maken, en een virtuele machine, een database en een CDN-service aan deze resourcegroep toevoegen.</span><span class="sxs-lookup"><span data-stu-id="6441d-148">For example, you might create a Resource Group for an application or project and add a virtual machine, a database and a CDN service within it.</span></span>

<span data-ttu-id="6441d-149">Laten we een resourcegroep maken met de naam 'MyResourceGroup' in de Azure-regio Europa West.</span><span class="sxs-lookup"><span data-stu-id="6441d-149">Let's create a resource group named "MyResourceGroup" in the westeurope region of Azure.</span></span> <span data-ttu-id="6441d-150">Typ daartoe de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="6441d-150">To do so type the following command:</span></span>

```powershell
New-AzureRmResourceGroup -Name 'myResourceGroup' -Location 'westeurope'
```

```Output
ResourceGroupName : myResourceGroup
Location          : westeurope
ProvisioningState : Succeeded
Tags              :
ResourceId        : /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/myResourceGroup
```

<span data-ttu-id="6441d-151">Deze nieuwe resourcegroep wordt gebruikt om alle benodigde resources voor het maken van een nieuwe VM op te slaan.</span><span class="sxs-lookup"><span data-stu-id="6441d-151">This new resource group will be used to contain all of the resources needed for the new VM we create.</span></span> <span data-ttu-id="6441d-152">Als we een nieuwe virtuele Linux-machine maken, moeten we eerst de vereiste resources maken en deze toewijzen aan een configuratie.</span><span class="sxs-lookup"><span data-stu-id="6441d-152">To create a new Linux VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="6441d-153">Vervolgens gebruiken we die configuratie om de virtuele machine te maken.</span><span class="sxs-lookup"><span data-stu-id="6441d-153">Then we can use that configuration to create the VM.</span></span> <span data-ttu-id="6441d-154">Er moet zich ook een openbare SSH-sleutel met de naam `id_rsa.pub` in de map .ssh van uw gebruikersprofiel bevinden.</span><span class="sxs-lookup"><span data-stu-id="6441d-154">Also, you will need to have an SSH public key named `id_rsa.pub` in the .ssh directory of your user profile.</span></span>

#### <a name="create-the-required-network-resources"></a><span data-ttu-id="6441d-155">De vereiste netwerkresources maken</span><span class="sxs-lookup"><span data-stu-id="6441d-155">Create the required network resources</span></span>

<span data-ttu-id="6441d-156">Eerst moet er een subnetconfiguratie worden gemaakt die wordt gebruikt bij het maken van het virtuele netwerk.</span><span class="sxs-lookup"><span data-stu-id="6441d-156">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="6441d-157">We gaan ook een openbaar IP-adres maken, zodat er verbinding met deze virtuele machine kan worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="6441d-157">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="6441d-158">We maken een netwerkbeveiligingsgroep voor beveiligde toegang tot het openbare adres.</span><span class="sxs-lookup"><span data-stu-id="6441d-158">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="6441d-159">Ten slotte maken we de virtuele NIC met alle voorgaande resources.</span><span class="sxs-lookup"><span data-stu-id="6441d-159">Finally we create the virtual NIC using all of the previous resources.</span></span>

```powershell
# Variables for common values
$resourceGroup = "myResourceGroup"
$location = "westeurope"
$vmName = "myLinuxVM"

# Definer user name and blank password
$securePassword = ConvertTo-SecureString 'azurepassword' -AsPlainText -Force
$cred = New-Object System.Management.Automation.PSCredential ("azureuser", $securePassword)

# Create a subnet configuration
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 192.168.2.0/24

# Create a virtual network
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName $resourceGroup -Location $location `
  -Name MYvNET2 -AddressPrefix 192.168.0.0/16 -Subnet $subnetConfig

# Create a public IP address and specify a DNS name
$publicIp = New-AzureRmPublicIpAddress -ResourceGroupName $resourceGroup -Location $location `
  -Name "mypublicdns$(Get-Random)" -AllocationMethod Static -IdleTimeoutInMinutes 4
$publicIp | Select-Object Name,IpAddress

# Create an inbound network security group rule for port 22
$nsgRuleSSH = New-AzureRmNetworkSecurityRuleConfig -Name myNetworkSecurityGroupRuleSSH  -Protocol Tcp `
  -Direction Inbound -Priority 1000 -SourceAddressPrefix * -SourcePortRange * -DestinationAddressPrefix * `
  -DestinationPortRange 22 -Access Allow

# Create a network security group
$nsg = New-AzureRmNetworkSecurityGroup -ResourceGroupName $resourceGroup -Location $location `
  -Name myNetworkSecurityGroup2 -SecurityRules $nsgRuleSSH

# Create a virtual network card and associate with public IP address and NSG
$nic = New-AzureRmNetworkInterface -Name myNic2 -ResourceGroupName $resourceGroup -Location $location `
  -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $publicIp.Id -NetworkSecurityGroupId $nsg.Id
```

### <a name="create-the-vm-configuration"></a><span data-ttu-id="6441d-160">De VM-configuratie maken</span><span class="sxs-lookup"><span data-stu-id="6441d-160">Create the VM configuration</span></span>

<span data-ttu-id="6441d-161">Nu u de vereiste resources hebt, kunt u het VM-configuratieobject maken.</span><span class="sxs-lookup"><span data-stu-id="6441d-161">Now that we have the required resources we can create the VM configuration oboject.</span></span>

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Linux -ComputerName $vmName -Credential $cred -DisablePasswordAuthentication |
  Set-AzureRmVMSourceImage -PublisherName Canonical -Offer UbuntuServer -Skus 14.04.2-LTS -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Configure SSH Keys
$sshPublicKey = Get-Content "$env:USERPROFILE\.ssh\id_rsa.pub"
Add-AzureRmVMSshPublicKey -VM $vmConfig -KeyData $sshPublicKey -Path "/home/azureuser/.ssh/authorized_keys"
```

### <a name="create-the-virtual-machine"></a><span data-ttu-id="6441d-162">De virtuele machine maken</span><span class="sxs-lookup"><span data-stu-id="6441d-162">Create the virtual machine</span></span>

<span data-ttu-id="6441d-163">Nu kunt u de VM maken met behulp van het VM-configuratieobject.</span><span class="sxs-lookup"><span data-stu-id="6441d-163">Now we can create the VM using the VM configuration object.</span></span>

```powershell
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

<span data-ttu-id="6441d-164">Nu de virtuele machine is gemaakt, kunt u zich aanmelden bij uw nieuwe virtuele Linux-machine via SSH, met het openbare IP-adres van de virtuele machine die u hebt gemaakt:</span><span class="sxs-lookup"><span data-stu-id="6441d-164">Now that the VM has been created, you can log on to your new Linux VM using SSH with the public IP address of the VM you created:</span></span>

```bash
ssh xx.xxx.xxx.xxx
```

```Output
Welcome to Ubuntu 14.04.4 LTS (GNU/Linux 3.19.0-65-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sun Feb 19 00:32:28 UTC 2017

  System load: 0.31              Memory usage: 3%   Processes:       89
  Usage of /:  39.6% of 1.94GB   Swap usage:   0%   Users logged in: 0

  Graph this data and manage this system at:
    https://landscape.canonical.com/

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 packages can be updated.
0 updates are security updates.



The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

my-login@MyLinuxVM:../../..$
```

## <a name="creating-other-resources-in-azure"></a><span data-ttu-id="6441d-165">Andere resources in Azure maken</span><span class="sxs-lookup"><span data-stu-id="6441d-165">Creating other resources in Azure</span></span>

<span data-ttu-id="6441d-166">We hebben u nu laten zien welke stappen u moet uitvoeren om een resourcegroep, een virtuele Linux-machine en een virtuele Windows Server-machine te maken.</span><span class="sxs-lookup"><span data-stu-id="6441d-166">We've now walked through how to create a Resource Group, a Linux VM, and a Windows Server VM.</span></span> <span data-ttu-id="6441d-167">U kunt ook nog vele andere typen Azure-resources maken.</span><span class="sxs-lookup"><span data-stu-id="6441d-167">You can create many other types of Azure resources as well.</span></span>

<span data-ttu-id="6441d-168">Als we bijvoorbeeld een Azure Network Load Balancer willen maken die we vervolgens gaan koppelen aan de nieuwe virtuele machines, kunnen we daarvoor de volgende opdracht gebruiken:</span><span class="sxs-lookup"><span data-stu-id="6441d-168">For example, to create an Azure Network Load Balancer that we could then associate with our newly created VMs, we can use the following create command:</span></span>

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

<span data-ttu-id="6441d-169">We kunnen voor onze infrastructuur ook een nieuw privé virtueel netwerk (dat binnen Azure doorgaans 'VNet' wordt genoemd) maken en wel met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="6441d-169">We could also create a new private Virtual Network (commonly referred to as a "VNet" within Azure) for our infrastructure using the following command:</span></span>

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

<span data-ttu-id="6441d-170">Wat Azure en Azure PowerShell zo krachtig maakt, is dat ze niet alleen kunnen worden gebruikt in de cloudinfrastructuur, maar ook voor het maken van beheerde platformservices.</span><span class="sxs-lookup"><span data-stu-id="6441d-170">What makes Azure and the Azure PowerShell powerful is that we can use it not just to get cloud-based infrastructure but also to create managed platform services.</span></span> <span data-ttu-id="6441d-171">De beheerde platformservices kunnen bovendien worden gecombineerd met de infrastructuur om nog krachtigere oplossingen te maken.</span><span class="sxs-lookup"><span data-stu-id="6441d-171">The managed platform services can also be combined with infrastructure to build even more powerful solutions.</span></span>

<span data-ttu-id="6441d-172">U kunt bijvoorbeeld Azure PowerShell gebruiken om een Azure AppService te maken.</span><span class="sxs-lookup"><span data-stu-id="6441d-172">For example, you can use the Azure PowerShell to create an Azure AppService.</span></span> <span data-ttu-id="6441d-173">Azure AppService is een beheerde platformservice die uitstekend kan worden gebruikt om web-apps te hosten zonder dat u zich zorgen hoeft te maken over de infrastructuur.</span><span class="sxs-lookup"><span data-stu-id="6441d-173">Azure AppService is a managed platform service that provides a great way to host web apps without having to worry about infrastructure.</span></span> <span data-ttu-id="6441d-174">Nadat de Azure AppService is gemaakt, kunt u binnen de AppService twee nieuwe Azure-web-apps maken en wel met de volgende opdrachten:</span><span class="sxs-lookup"><span data-stu-id="6441d-174">After creating the Azure AppService, you can create two new Azure Web Apps within the AppService using the following commands:</span></span>

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <a name="listing-deployed-resources"></a><span data-ttu-id="6441d-175">Geïmplementeerde resources in een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="6441d-175">Listing deployed resources</span></span>

<span data-ttu-id="6441d-176">U kunt de cmdlet `Get-AzureRmResource` gebruiken om de resources weer te geven die in Azure worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6441d-176">You can use the `Get-AzureRmResource` cmdlet to list the resources running in Azure.</span></span> <span data-ttu-id="6441d-177">In het volgende voorbeeld worden de resources weergegeven die we zojuist in de nieuwe resourcegroep hebben gemaakt.</span><span class="sxs-lookup"><span data-stu-id="6441d-177">The following example shows the resources we just created in the new resource group.</span></span>

```powershell
Get-AzureRmResource |
  Where-Object ResourceGroupName -eq myResourceGroup |
    Select-Object Name,Location,ResourceType
```

```Output
Name                                                  Location   ResourceType
----                                                  --------   ------------
myLinuxVM_OsDisk_1_36ca038791f642ba91270879088c249a   westeurope Microsoft.Compute/disks
myWindowsVM_OsDisk_1_f627e6e2bb454c72897d72e9632adf9a westeurope Microsoft.Compute/disks
myLinuxVM                                             westeurope Microsoft.Compute/virtualMachines
myWindowsVM                                           westeurope Microsoft.Compute/virtualMachines
myWindowsVM/BGInfo                                    westeurope Microsoft.Compute/virtualMachines/extensions
myNic1                                                westeurope Microsoft.Network/networkInterfaces
myNic2                                                westeurope Microsoft.Network/networkInterfaces
myNetworkSecurityGroup1                               westeurope Microsoft.Network/networkSecurityGroups
myNetworkSecurityGroup2                               westeurope Microsoft.Network/networkSecurityGroups
mypublicdns245369171                                  westeurope Microsoft.Network/publicIPAddresses
mypublicdns779537141                                  westeurope Microsoft.Network/publicIPAddresses
MYvNET1                                               westeurope Microsoft.Network/virtualNetworks
MYvNET2                                               westeurope Microsoft.Network/virtualNetworks
micromyresomywi032907510                              westeurope Microsoft.Storage/storageAccounts
```

## <a name="deleting-resources"></a><span data-ttu-id="6441d-178">Resources verwijderen</span><span class="sxs-lookup"><span data-stu-id="6441d-178">Deleting resources</span></span>

<span data-ttu-id="6441d-179">Als u uw Azure-account wilt opschonen, moet u de resources verwijderen die in dit voorbeeld zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="6441d-179">To clean up your Azure account, you want to remove the resources we created in this example.</span></span> <span data-ttu-id="6441d-180">U kunt de cmdlets `Remove-AzureRm*` gebruiken om de resources te verwijderen die u niet meer nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="6441d-180">You can use the `Remove-AzureRm*` cmdlets to delete the resources you no longer need.</span></span> <span data-ttu-id="6441d-181">Als u de virtuele Windows-machine wilt verwijderen die we hebben gemaakt, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="6441d-181">To remove the Windows VM we created, using the following command:</span></span>

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

<span data-ttu-id="6441d-182">U wordt gevraagd om te bevestigen dat u de resource wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="6441d-182">You will be prompted to confirm that you want to remove the resource.</span></span>

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="6441d-183">U kunt ook een opdracht gebruiken om veel resources in één keer te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="6441d-183">You can also use the delete many resources at one time.</span></span> <span data-ttu-id="6441d-184">Met de volgende opdracht wordt bijvoorbeeld de volledige resourcegroep 'MyResourceGroup' verwijderd die we hebben gebruikt in alle voorbeelden in deze Aan de slag-zelfstudie.</span><span class="sxs-lookup"><span data-stu-id="6441d-184">For example, the following command deletes all the resource group "MyResourceGroup" that we've used for all the samples in this Get Started tutorial.</span></span> <span data-ttu-id="6441d-185">Hiermee verwijdert u de resourcegroep en alle resources die deze bevat.</span><span class="sxs-lookup"><span data-stu-id="6441d-185">This removes the resource group and all of the resources in it.</span></span>

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="6441d-186">Dit kan enkele minuten in beslag nemen.</span><span class="sxs-lookup"><span data-stu-id="6441d-186">This can take several minutes to complete.</span></span>

## <a name="get-samples"></a><span data-ttu-id="6441d-187">Voorbeelden ophalen</span><span class="sxs-lookup"><span data-stu-id="6441d-187">Get samples</span></span>

<span data-ttu-id="6441d-188">Voor meer informatie over het gebruik van Azure PowerShell kunt u onze meest voorkomende scripts voor [virtuele Linux-machines](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [virtuele Windows-machines](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) en [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) raadplegen.</span><span class="sxs-lookup"><span data-stu-id="6441d-188">To learn more about ways to use the Azure PowerShell, check out our most common scripts for [Linux VMs](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Windows VMs](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), and [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6441d-189">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="6441d-189">Next steps</span></span>

* [<span data-ttu-id="6441d-190">Aanmelden met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="6441d-190">Login with Azure PowerShell</span></span>](authenticate-azureps.md)
* [<span data-ttu-id="6441d-191">Azure-abonnementen beheren met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="6441d-191">Manage Azure subscriptions with Azure PowerShell</span></span>](manage-subscriptions-azureps.md)
* [<span data-ttu-id="6441d-192">Azure PowerShell gebruiken om service-principals in Azure te maken</span><span class="sxs-lookup"><span data-stu-id="6441d-192">Create service principals in Azure using Azure PowerShell</span></span>](create-azure-service-principal-azureps.md)
* <span data-ttu-id="6441d-193">Lees de Releaseopmerkingen over het migreren van een oudere versie: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span><span class="sxs-lookup"><span data-stu-id="6441d-193">Read the Release notes about migrating from an older release: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span></span>
* <span data-ttu-id="6441d-194">Hulp van de community:</span><span class="sxs-lookup"><span data-stu-id="6441d-194">Get help from the community:</span></span>
  * [<span data-ttu-id="6441d-195">Azure-forum op MSDN</span><span class="sxs-lookup"><span data-stu-id="6441d-195">Azure forum on MSDN</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  * [<span data-ttu-id="6441d-196">Stackoverflow</span><span class="sxs-lookup"><span data-stu-id="6441d-196">stackoverflow</span></span>](http://go.microsoft.com/fwlink/?LinkId=320213)
