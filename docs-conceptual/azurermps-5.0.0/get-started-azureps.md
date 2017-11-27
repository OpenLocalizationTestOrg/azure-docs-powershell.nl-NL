<span data-ttu-id="e444e-101">-- titel: Aan de slag met Azure PowerShell | Microsoft Docs description: services: azure author: sdwheeler ms.author: sewhee manager: carmonm ms.product: azure ms.service: azure-powershell ms.devlang: powershell ms.topic: get-started-article ms.date: 11/15/2017</span><span class="sxs-lookup"><span data-stu-id="e444e-101">-- title: Get started with Azure PowerShell | Microsoft Docs description: services: azure author: sdwheeler ms.author: sewhee manager: carmonm ms.product: azure ms.service: azure-powershell ms.devlang: powershell ms.topic: get-started-article ms.date: 11/15/2017</span></span>
---
# <a name="getting-started-with-azure-powershell"></a><span data-ttu-id="e444e-102">Aan de slag met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e444e-102">Getting started with Azure PowerShell</span></span>

<span data-ttu-id="e444e-103">Azure PowerShell is ontworpen om Azure-resources te beheren vanaf de opdrachtregel en voor het bouwen van automatiseringsscripts die op basis van Azure Resource Manager werken.</span><span class="sxs-lookup"><span data-stu-id="e444e-103">Azure PowerShell is designed for managing and administering Azure resources from the command line, and for building automation scripts that work against the Azure Resource Manager.</span></span> <span data-ttu-id="e444e-104">U kunt PowerShell in uw browser gebruiken met [Azure Cloud Shell](/azure/cloud-shell/overview), of installeren op uw lokale computer en dan gebruiken in een PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="e444e-104">You can use it in your browser with [Azure Cloud Shell](/azure/cloud-shell/overview), or you can install it on your local machine and use it in any PowerShell session.</span></span> <span data-ttu-id="e444e-105">Dit artikel helpt u op weg met het gebruik ervan en leert u wat de belangrijkste concepten zijn die eraan ten grondslag liggen.</span><span class="sxs-lookup"><span data-stu-id="e444e-105">This article helps get you started using it, and teaches you the core concepts behind it.</span></span>

## <a name="connect"></a><span data-ttu-id="e444e-106">Verbinding maken</span><span class="sxs-lookup"><span data-stu-id="e444e-106">Connect</span></span>

<span data-ttu-id="e444e-107">De eenvoudigste manier om te beginnen is door [Cloud Shell te openen](/azure/cloud-shell/quickstart).</span><span class="sxs-lookup"><span data-stu-id="e444e-107">The simplest way to get started is to [launch Cloud Shell](/azure/cloud-shell/quickstart).</span></span>

1. <span data-ttu-id="e444e-108">Open Cloud Shell via de bovenste navigatiebalk van de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="e444e-108">Launch Cloud Shell from the top navigation of the Azure portal.</span></span>

   ![Shell-pictogram](/media/get-started-azureps/shell-icon.png)

2. <span data-ttu-id="e444e-110">Kies het abonnement dat u wilt gebruiken en maak een opslagaccount.</span><span class="sxs-lookup"><span data-stu-id="e444e-110">Choose the subscription you want to use and create a storage account.</span></span>

   ![Een opslagaccount maken](/media/get-started-azureps/storage-prompt.png)

<span data-ttu-id="e444e-112">Zodra de opslag is gemaakt, wordt er door Cloud Shell een PowerShell-sessie geopend in de browser.</span><span class="sxs-lookup"><span data-stu-id="e444e-112">Once your storage has been created, the Cloud Shell will open a PowerShell session in the browser.</span></span>

![Cloud Shell voor PowerShell](/media/get-started-azureps/cloud-powershell.png)

<span data-ttu-id="e444e-114">U kunt ook Azure PowerShell installeren en lokaal gebruiken in een PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="e444e-114">You can also install Azure PowerShell and use it locally in a PowerShell session.</span></span>

## <a name="install-azure-powershell"></a><span data-ttu-id="e444e-115">Azure PowerShell installeren</span><span class="sxs-lookup"><span data-stu-id="e444e-115">Install Azure PowerShell</span></span>

<span data-ttu-id="e444e-116">De eerste stap bestaat eruit dat u moet controleren of de nieuwste versie van Azure PowerShell is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e444e-116">The first step is to make sure you have the latest version of the Azure PowerShell installed.</span></span> <span data-ttu-id="e444e-117">Zie de [opmerkingen bij de release](./release-notes-azureps.md) voor meer informatie over de nieuwste release.</span><span class="sxs-lookup"><span data-stu-id="e444e-117">For information about the latest release, see the [release notes](./release-notes-azureps.md).</span></span>

1. <span data-ttu-id="e444e-118">[Installeer Azure PowerShell](install-azurerm-ps.md).</span><span class="sxs-lookup"><span data-stu-id="e444e-118">[Install Azure PowerShell](install-azurerm-ps.md).</span></span>

2. <span data-ttu-id="e444e-119">Voer `Get-Module AzureRM -ListAvailable` uit vanaf de opdrachtregel om te controleren of de installatie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="e444e-119">To verify the installation was successful, run `Get-Module AzureRM -ListAvailable` from your command line.</span></span>

## <a name="log-in-to-azure"></a><span data-ttu-id="e444e-120">Meld u aan bij Azure.</span><span class="sxs-lookup"><span data-stu-id="e444e-120">Log in to Azure</span></span>

<span data-ttu-id="e444e-121">Interactief aanmelden:</span><span class="sxs-lookup"><span data-stu-id="e444e-121">Sign on interactively:</span></span>

1. <span data-ttu-id="e444e-122">Typ `Login-AzureRmAccount`.</span><span class="sxs-lookup"><span data-stu-id="e444e-122">Type `Login-AzureRmAccount`.</span></span> <span data-ttu-id="e444e-123">U krijgt een dialoogvenster te zien waarin wordt gevraagd naar uw Azure-referenties.</span><span class="sxs-lookup"><span data-stu-id="e444e-123">You will get dialog box asking for your Azure credentials.</span></span> <span data-ttu-id="e444e-124">Met behulp van de optie '-EnvironmentName' kunt u zich aanmelden bij Azure China of Azure Duitsland.</span><span class="sxs-lookup"><span data-stu-id="e444e-124">Option '-EnvironmentName' can let you login in Azure China or Azure Germany.</span></span>

   <span data-ttu-id="e444e-125">bijvoorbeeld: Login-AzureRmAccount - EnvironmentName AzureChinaCloud</span><span class="sxs-lookup"><span data-stu-id="e444e-125">e.g. Login-AzureRmAccount -EnvironmentName AzureChinaCloud</span></span>

2. <span data-ttu-id="e444e-126">Typ het e-mailadres en het wachtwoord die bij uw account horen.</span><span class="sxs-lookup"><span data-stu-id="e444e-126">Type the email address and password associated with your account.</span></span> <span data-ttu-id="e444e-127">Azure verifieert de referentiegegevens en slaat deze op. Vervolgens wordt het venster gesloten.</span><span class="sxs-lookup"><span data-stu-id="e444e-127">Azure authenticates and saves the credential information, and then closes the window.</span></span>

<span data-ttu-id="e444e-128">Nadat u zich hebt aangemeld bij een Azure-account, kunt u de Azure PowerShell-cmdlets gebruiken om toegang te krijgen tot de resources in uw abonnement en om deze te beheren.</span><span class="sxs-lookup"><span data-stu-id="e444e-128">Once you have signed in to an Azure account, you can use the Azure PowerShell cmdlets to access and manager the resources in your subscription.</span></span>

## <a name="create-a-resource-group"></a><span data-ttu-id="e444e-129">Een resourcegroep maken</span><span class="sxs-lookup"><span data-stu-id="e444e-129">Create a resource group</span></span>

<span data-ttu-id="e444e-130">Nu alles is ingesteld, gaan we Azure PowerShell gebruiken om resources binnen Azure te maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-130">Now that we've got everything set up, let's use Azure PowerShell to create resources within Azure.</span></span>

<span data-ttu-id="e444e-131">Eerst maakt u een resourcegroep.</span><span class="sxs-lookup"><span data-stu-id="e444e-131">First, create a Resource Group.</span></span> <span data-ttu-id="e444e-132">Resourcegroepen in Azure bieden u een manier voor het beheren van meerdere resources die u op een logische wijze wilt groeperen.</span><span class="sxs-lookup"><span data-stu-id="e444e-132">Resource Groups in Azure provide a way to manage multiple resources that you want to logically group together.</span></span> <span data-ttu-id="e444e-133">U kunt bijvoorbeeld een resourcegroep voor een toepassing of project maken, en een virtuele machine, een database en een CDN-service aan deze resourcegroep toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e444e-133">For example, you might create a Resource Group for an application or project and add a virtual machine, a database and a CDN service within it.</span></span>

<span data-ttu-id="e444e-134">Laten we een resourcegroep maken met de naam 'MyResourceGroup' in de Azure-regio Europa West.</span><span class="sxs-lookup"><span data-stu-id="e444e-134">Let's create a resource group named "MyResourceGroup" in the westeurope region of Azure.</span></span> <span data-ttu-id="e444e-135">Typ daartoe de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="e444e-135">To do so type the following command:</span></span>

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

## <a name="create-a-windows-virtual-machine"></a><span data-ttu-id="e444e-136">Een virtuele Windows-machine maken</span><span class="sxs-lookup"><span data-stu-id="e444e-136">Create a Windows Virtual Machine</span></span>

<span data-ttu-id="e444e-137">Nu deze resourcegroep is gemaakt, maken we een virtuele Windows-machine binnen deze groep.</span><span class="sxs-lookup"><span data-stu-id="e444e-137">Now that we have our resource group, let's create a Windows VM within it.</span></span> <span data-ttu-id="e444e-138">Als we een nieuwe virtuele machine maken, moeten we eerst de vereiste resources maken en deze toewijzen aan een configuratie.</span><span class="sxs-lookup"><span data-stu-id="e444e-138">To create a new VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="e444e-139">Vervolgens gebruiken we die configuratie om de virtuele machine te maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-139">Then we can use that configuration to create the VM.</span></span>

### <a name="create-the-required-network-resources"></a><span data-ttu-id="e444e-140">De vereiste netwerkresources maken</span><span class="sxs-lookup"><span data-stu-id="e444e-140">Create the required network resources</span></span>

<span data-ttu-id="e444e-141">Eerst moet er een subnetconfiguratie worden gemaakt die wordt gebruikt bij het maken van het virtuele netwerk.</span><span class="sxs-lookup"><span data-stu-id="e444e-141">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="e444e-142">We gaan ook een openbaar IP-adres maken, zodat er verbinding met deze virtuele machine kan worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e444e-142">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="e444e-143">We maken een netwerkbeveiligingsgroep voor beveiligde toegang tot het openbare adres.</span><span class="sxs-lookup"><span data-stu-id="e444e-143">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="e444e-144">Ten slotte maken we de virtuele NIC met alle voorgaande resources.</span><span class="sxs-lookup"><span data-stu-id="e444e-144">Finally we create the virtual NIC using all of the previous resources.</span></span>

```powershell
# Variables for common values
$resourceGroup = "myResourceGroup"
$location = "westeurope"
$vmName = "myWindowsVM"

# Create a subnet configuration
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet1 -AddressPrefix 192.168.1.0/24

# Create a virtual network
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName $resourceGroup -Location $location `
  -Name MYvNET1 -AddressPrefix 192.168.0.0/16 -Subnet $subnetConfig

# Create a public IP address and specify a DNS name
$publicIp = New-AzureRmPublicIpAddress -ResourceGroupName $resourceGroup -Location $location `
  -Name "mypublicdns$(Get-Random)" -AllocationMethod Static -IdleTimeoutInMinutes 4
$publicIp | Select-Object Name,IpAddress

# Create an inbound network security group rule for port 3389
$nsgRuleRDP = New-AzureRmNetworkSecurityRuleConfig -Name myNetworkSecurityGroupRuleRDP  -Protocol Tcp `
  -Direction Inbound -Priority 1000 -SourceAddressPrefix * -SourcePortRange * -DestinationAddressPrefix * `
  -DestinationPortRange 3389 -Access Allow

# Create a network security group
$nsg = New-AzureRmNetworkSecurityGroup -ResourceGroupName $resourceGroup -Location $location `
  -Name myNetworkSecurityGroup1 -SecurityRules $nsgRuleRDP

# Create a virtual network card and associate with public IP address and NSG
$nic = New-AzureRmNetworkInterface -Name myNic1 -ResourceGroupName $resourceGroup -Location $location `
  -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $publicIp.Id -NetworkSecurityGroupId $nsg.Id
```

### <a name="create-the-virtual-machine"></a><span data-ttu-id="e444e-145">De virtuele machine maken</span><span class="sxs-lookup"><span data-stu-id="e444e-145">Create the virtual machine</span></span>

<span data-ttu-id="e444e-146">Eerst hebben we een set referenties nodig voor het besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="e444e-146">First we need a set of credentials for the OS.</span></span>

```powershell
# Create user object
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

<span data-ttu-id="e444e-147">Nu we de vereiste resources hebben, kunnen we de virtuele machine maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-147">Now that we have the required resources we can create the VM.</span></span> <span data-ttu-id="e444e-148">Voor deze stap maken we een VM-configuratieobject. Vervolgens gebruiken we de configuratie om de virtuele machine te maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-148">For this step, we create a VM configuration object, then we use the configuration to create the VM.</span></span>

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Windows -ComputerName $vmName -Credential $cred |
  Set-AzureRmVMSourceImage -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Create a virtual machine
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

<span data-ttu-id="e444e-149">De opdracht `New-AzureRmVM` produceert resultaten wanneer de virtuele machine geheel klaar is en gereed is voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="e444e-149">The `New-AzureRmVM` command outputs results once the VM has been fully created and is ready to be used.</span></span>

```Output
RequestId IsSuccessStatusCode StatusCode ReasonPhrase
--------- ------------------- ---------- ------------
                         True         OK OK
```

<span data-ttu-id="e444e-150">Meld u nu aan bij uw nieuwe virtuele Windows Server-machine en gebruik daarvoor Extern bureaublad en het openbare IP-adres van de virtuele machine.</span><span class="sxs-lookup"><span data-stu-id="e444e-150">Now log on to your newly created Windows Server VM using Remote Desktop and the public IP address of the VM.</span></span> <span data-ttu-id="e444e-151">Met de volgende opdracht kan het openbare IP-adres worden weergegeven dat in het vorige script is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e444e-151">The following command displays the public IP address created in the previous script.</span></span>

```powershell
$publicIp | Select-Object Name,IpAddress
```

```Output
Name                  IpAddress
----                  ---------
mypublicdns1400512543 xx.xx.xx.xx
```

<span data-ttu-id="e444e-152">Als u met een Windows-computer werkt, kunt u dit vanaf de opdrachtregel doen met de mstsc-opdracht:</span><span class="sxs-lookup"><span data-stu-id="e444e-152">If you are on a Windows-based system, you can do this from the command line using the mstsc command:</span></span>

```powershell
mstsc /v:xx.xxx.xx.xxx
```

<span data-ttu-id="e444e-153">Gebruik om u aan te melden dezelfde combinatie van gebruikersnaam en wachtwoord die u hebt gebruikt toen u de virtuele machine maakte.</span><span class="sxs-lookup"><span data-stu-id="e444e-153">Supply the same username/password combination you used when creating the VM to log in.</span></span>

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="e444e-154">Een virtuele Linux-machine maken</span><span class="sxs-lookup"><span data-stu-id="e444e-154">Create a Linux Virtual Machine</span></span>

<span data-ttu-id="e444e-155">Als we een nieuwe virtuele Linux-machine maken, moeten we eerst de vereiste resources maken en deze toewijzen aan een configuratie.</span><span class="sxs-lookup"><span data-stu-id="e444e-155">To create a new Linux VM we must first create the other required resources and assign them to a configuration.</span></span> <span data-ttu-id="e444e-156">Vervolgens gebruiken we die configuratie om de virtuele machine te maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-156">Then we can use that configuration to create the VM.</span></span> <span data-ttu-id="e444e-157">Hierbij wordt ervan uitgegaan dat u de resourcegroep al hebt gemaakt zoals eerder is getoond.</span><span class="sxs-lookup"><span data-stu-id="e444e-157">This assumes that you have already created the resource group as previously shown.</span></span> <span data-ttu-id="e444e-158">Er moet zich ook een openbare SSH-sleutel met de naam `id_rsa.pub` in de map .ssh van uw gebruikersprofiel bevinden.</span><span class="sxs-lookup"><span data-stu-id="e444e-158">Also, you will need to have an SSH public key named `id_rsa.pub` in the .ssh directory of your user profile.</span></span>

### <a name="create-the-required-network-resources"></a><span data-ttu-id="e444e-159">De vereiste netwerkresources maken</span><span class="sxs-lookup"><span data-stu-id="e444e-159">Create the required network resources</span></span>

<span data-ttu-id="e444e-160">Eerst moet er een subnetconfiguratie worden gemaakt die wordt gebruikt bij het maken van het virtuele netwerk.</span><span class="sxs-lookup"><span data-stu-id="e444e-160">First we need to create a subnet configuration to be used with the virtual network creation process.</span></span> <span data-ttu-id="e444e-161">We gaan ook een openbaar IP-adres maken, zodat er verbinding met deze virtuele machine kan worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e444e-161">We also create a public IP address so that we can connect to this VM.</span></span> <span data-ttu-id="e444e-162">We maken een netwerkbeveiligingsgroep voor beveiligde toegang tot het openbare adres.</span><span class="sxs-lookup"><span data-stu-id="e444e-162">We create a network security group to secure access to the public address.</span></span> <span data-ttu-id="e444e-163">Ten slotte maken we de virtuele NIC met alle voorgaande resources.</span><span class="sxs-lookup"><span data-stu-id="e444e-163">Finally we create the virtual NIC using all of the previous resources.</span></span>

```powershell
# Variables for common values
$resourceGroup = "myResourceGroup"
$location = "westeurope"
$vmName = "myLinuxVM"

# Definer user name and blank password
$securePassword = ConvertTo-SecureString ' ' -AsPlainText -Force
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

### <a name="create-the-virtual-machine"></a><span data-ttu-id="e444e-164">De virtuele machine maken</span><span class="sxs-lookup"><span data-stu-id="e444e-164">Create the virtual machine</span></span>

<span data-ttu-id="e444e-165">Nu we de vereiste resources hebben, kunnen we de virtuele machine maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-165">Now that we have the required resources we can create the VM.</span></span> <span data-ttu-id="e444e-166">Voor deze stap maken we een VM-configuratieobject. Vervolgens gebruiken we de configuratie om de virtuele machine te maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-166">For this step, we create a VM configuration object, then we use the configuration to create the VM.</span></span>

```powershell
# Create a virtual machine configuration
$vmConfig = New-AzureRmVMConfig -VMName $vmName -VMSize Standard_D1 |
  Set-AzureRmVMOperatingSystem -Linux -ComputerName $vmName -Credential $cred -DisablePasswordAuthentication |
  Set-AzureRmVMSourceImage -PublisherName Canonical -Offer UbuntuServer -Skus 14.04.2-LTS -Version latest |
  Add-AzureRmVMNetworkInterface -Id $nic.Id

# Configure SSH Keys
$sshPublicKey = Get-Content "$env:USERPROFILE\.ssh\id_rsa.pub"
Add-AzureRmVMSshPublicKey -VM $vmConfig -KeyData $sshPublicKey -Path "/home/azureuser/.ssh/authorized_keys"

# Create a virtual machine
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

<span data-ttu-id="e444e-167">Nu de virtuele machine is gemaakt, kunt u zich aanmelden bij uw nieuwe virtuele Linux-machine via SSH, met het openbare IP-adres van de virtuele machine die u hebt gemaakt:</span><span class="sxs-lookup"><span data-stu-id="e444e-167">Now that the VM has been created, you can log on to your new Linux VM using SSH with the public IP address of the VM you created:</span></span>

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

## <a name="creating-other-resources-in-azure"></a><span data-ttu-id="e444e-168">Andere resources in Azure maken</span><span class="sxs-lookup"><span data-stu-id="e444e-168">Creating other resources in Azure</span></span>

<span data-ttu-id="e444e-169">We hebben u nu laten zien welke stappen u moet uitvoeren om een resourcegroep, een virtuele Linux-machine en een virtuele Windows Server-machine te maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-169">We've now walked through how to create a Resource Group, a Linux VM, and a Windows Server VM.</span></span> <span data-ttu-id="e444e-170">U kunt ook nog vele andere typen Azure-resources maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-170">You can create many other types of Azure resources as well.</span></span>

<span data-ttu-id="e444e-171">Als we bijvoorbeeld een Azure Network Load Balancer willen maken die we vervolgens gaan koppelen aan de nieuwe virtuele machines, kunnen we daarvoor de volgende opdracht gebruiken:</span><span class="sxs-lookup"><span data-stu-id="e444e-171">For example, to create an Azure Network Load Balancer that we could then associate with our newly created VMs, we can use the following create command:</span></span>

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

<span data-ttu-id="e444e-172">We kunnen voor onze infrastructuur ook een nieuw privé virtueel netwerk (dat binnen Azure doorgaans 'VNet' wordt genoemd) maken en wel met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="e444e-172">We could also create a new private Virtual Network (commonly referred to as a "VNet" within Azure) for our infrastructure using the following command:</span></span>

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

<span data-ttu-id="e444e-173">Wat Azure en Azure PowerShell zo krachtig maakt, is dat ze niet alleen kunnen worden gebruikt in de cloudinfrastructuur, maar ook voor het maken van beheerde platformservices.</span><span class="sxs-lookup"><span data-stu-id="e444e-173">What makes Azure and the Azure PowerShell powerful is that we can use it not just to get cloud-based infrastructure but also to create managed platform services.</span></span> <span data-ttu-id="e444e-174">De beheerde platformservices kunnen bovendien worden gecombineerd met de infrastructuur om nog krachtigere oplossingen te maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-174">The managed platform services can also be combined with infrastructure to build even more powerful solutions.</span></span>

<span data-ttu-id="e444e-175">U kunt bijvoorbeeld Azure PowerShell gebruiken om een Azure AppService te maken.</span><span class="sxs-lookup"><span data-stu-id="e444e-175">For example, you can use the Azure PowerShell to create an Azure AppService.</span></span> <span data-ttu-id="e444e-176">Azure AppService is een beheerde platformservice die uitstekend kan worden gebruikt om web-apps te hosten zonder dat u zich zorgen hoeft te maken over de infrastructuur.</span><span class="sxs-lookup"><span data-stu-id="e444e-176">Azure AppService is a managed platform service that provides a great way to host web apps without having to worry about infrastructure.</span></span> <span data-ttu-id="e444e-177">Nadat de Azure AppService is gemaakt, kunt u binnen de AppService twee nieuwe Azure-web-apps maken en wel met de volgende opdrachten:</span><span class="sxs-lookup"><span data-stu-id="e444e-177">After creating the Azure AppService, you can create two new Azure Web Apps within the AppService using the following commands:</span></span>

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <a name="listing-deployed-resources"></a><span data-ttu-id="e444e-178">Geïmplementeerde resources in een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="e444e-178">Listing deployed resources</span></span>

<span data-ttu-id="e444e-179">U kunt de cmdlet `Get-AzureRmResource` gebruiken om de resources weer te geven die in Azure worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e444e-179">You can use the `Get-AzureRmResource` cmdlet to list the resources running in Azure.</span></span> <span data-ttu-id="e444e-180">In het volgende voorbeeld worden de resources weergegeven die we zojuist in de nieuwe resourcegroep hebben gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e444e-180">The following example shows the resources we just created in the new resource group.</span></span>

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

## <a name="deleting-resources"></a><span data-ttu-id="e444e-181">Resources verwijderen</span><span class="sxs-lookup"><span data-stu-id="e444e-181">Deleting resources</span></span>

<span data-ttu-id="e444e-182">Als u uw Azure-account wilt opschonen, moet u de resources verwijderen die in dit voorbeeld zijn gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e444e-182">To clean up your Azure account, you want to remove the resources we created in this example.</span></span> <span data-ttu-id="e444e-183">U kunt de cmdlets `Remove-AzureRm*` gebruiken om de resources te verwijderen die u niet meer nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="e444e-183">You can use the `Remove-AzureRm*` cmdlets to delete the resources you no longer need.</span></span> <span data-ttu-id="e444e-184">Als u de virtuele Windows-machine wilt verwijderen die we hebben gemaakt, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="e444e-184">To remove the Windows VM we created, using the following command:</span></span>

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

<span data-ttu-id="e444e-185">U wordt gevraagd om te bevestigen dat u de resource wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e444e-185">You will be prompted to confirm that you want to remove the resource.</span></span>

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="e444e-186">U kunt ook een opdracht gebruiken om veel resources in één keer te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e444e-186">You can also use the delete many resources at one time.</span></span> <span data-ttu-id="e444e-187">Met de volgende opdracht wordt bijvoorbeeld de volledige resourcegroep 'MyResourceGroup' verwijderd die we hebben gebruikt in alle voorbeelden in deze Aan de slag-zelfstudie.</span><span class="sxs-lookup"><span data-stu-id="e444e-187">For example, the following command deletes all the resource group "MyResourceGroup" that we've used for all the samples in this Get Started tutorial.</span></span> <span data-ttu-id="e444e-188">Hiermee verwijdert u de resourcegroep en alle resources die deze bevat.</span><span class="sxs-lookup"><span data-stu-id="e444e-188">This removes the resource group and all of the resources in it.</span></span>

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

<span data-ttu-id="e444e-189">Dit kan enkele minuten in beslag nemen.</span><span class="sxs-lookup"><span data-stu-id="e444e-189">This can take several minutes to complete.</span></span>

## <a name="get-samples"></a><span data-ttu-id="e444e-190">Voorbeelden ophalen</span><span class="sxs-lookup"><span data-stu-id="e444e-190">Get samples</span></span>

<span data-ttu-id="e444e-191">Voor meer informatie over het gebruik van Azure PowerShell kunt u onze meest voorkomende scripts voor [virtuele Linux-machines](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [virtuele Windows-machines](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) en [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) raadplegen.</span><span class="sxs-lookup"><span data-stu-id="e444e-191">To learn more about ways to use the Azure PowerShell, check out our most common scripts for [Linux VMs](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Windows VMs](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), and [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e444e-192">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="e444e-192">Next steps</span></span>

* [<span data-ttu-id="e444e-193">Aanmelden met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e444e-193">Login with Azure PowerShell</span></span>](authenticate-azureps.md)
* [<span data-ttu-id="e444e-194">Azure-abonnementen beheren met Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e444e-194">Manage Azure subscriptions with Azure PowerShell</span></span>](manage-subscriptions-azureps.md)
* [<span data-ttu-id="e444e-195">Azure PowerShell gebruiken om service-principals in Azure te maken</span><span class="sxs-lookup"><span data-stu-id="e444e-195">Create service principals in Azure using Azure PowerShell</span></span>](create-azure-service-principal-azureps.md)
* <span data-ttu-id="e444e-196">Lees de opmerkingen bij de release over het migreren van een oudere versie: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span><span class="sxs-lookup"><span data-stu-id="e444e-196">Read the Release notes about migrating from an older release: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).</span></span>
* <span data-ttu-id="e444e-197">Hulp van de community:</span><span class="sxs-lookup"><span data-stu-id="e444e-197">Get help from the community:</span></span>
  * [<span data-ttu-id="e444e-198">Azure-forum op MSDN</span><span class="sxs-lookup"><span data-stu-id="e444e-198">Azure forum on MSDN</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  * [<span data-ttu-id="e444e-199">Stackoverflow</span><span class="sxs-lookup"><span data-stu-id="e444e-199">stackoverflow</span></span>](http://go.microsoft.com/fwlink/?LinkId=320213)
