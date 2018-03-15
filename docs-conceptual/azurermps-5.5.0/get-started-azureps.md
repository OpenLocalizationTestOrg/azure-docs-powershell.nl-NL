---
title: Aan de slag met Azure PowerShell | Microsoft Docs
description: 
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: get-started-article
ms.date: 11/15/2017
ms.openlocfilehash: af1eccfffed551e6025014e2fd9287f3e6ebf425
ms.sourcegitcommit: 20af779cd523c758d40e23d60eb989a4ef982d5c
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="getting-started-with-azure-powershell"></a>Aan de slag met Azure PowerShell

Azure PowerShell is ontworpen om Azure-resources te beheren vanaf de opdrachtregel en voor het bouwen van automatiseringsscripts die op basis van Azure Resource Manager werken. U kunt PowerShell in uw browser gebruiken met [Azure Cloud Shell](/azure/cloud-shell/overview), of installeren op uw lokale computer en dan gebruiken in een PowerShell-sessie. Dit artikel helpt u op weg met het gebruik ervan en leert u wat de belangrijkste concepten zijn die eraan ten grondslag liggen.

## <a name="connect"></a>Verbinding maken

De eenvoudigste manier om te beginnen is door [Cloud Shell te openen](/azure/cloud-shell/quickstart).

1. Open Cloud Shell via de bovenste navigatiebalk van de Azure Portal.

   ![Shell-pictogram](~/media/get-started-azureps/shell-icon.png)

2. Kies het abonnement dat u wilt gebruiken en maak een opslagaccount.

   ![Een opslagaccount maken](~/media/get-started-azureps/storage-prompt.png)

Zodra de opslag is gemaakt, wordt er door Cloud Shell een PowerShell-sessie geopend in de browser.

![Cloud Shell voor PowerShell](~/media/get-started-azureps/cloud-powershell.png)

U kunt ook Azure PowerShell installeren en lokaal gebruiken in een PowerShell-sessie.

## <a name="install-azure-powershell"></a>Azure PowerShell installeren

De eerste stap bestaat eruit dat u moet controleren of de nieuwste versie van Azure PowerShell is geïnstalleerd. Zie de [opmerkingen bij de release](./release-notes-azureps.md) voor meer informatie over de nieuwste release.

1. [Installeer Azure PowerShell](install-azurerm-ps.md).

2. Voer `Get-Module AzureRM -ListAvailable` uit vanaf de opdrachtregel om te controleren of de installatie is geslaagd.

## <a name="log-in-to-azure"></a>Meld u aan bij Azure.

Interactief aanmelden:

1. Typ `Login-AzureRmAccount`. U krijgt een dialoogvenster te zien waarin wordt gevraagd naar uw Azure-referenties. Met behulp van de optie '-EnvironmentName' kunt u zich aanmelden bij Azure China of Azure Duitsland.

   bijvoorbeeld: Login-AzureRmAccount - EnvironmentName AzureChinaCloud

2. Typ het e-mailadres en het wachtwoord die bij uw account horen. Azure verifieert de referentiegegevens en slaat deze op. Vervolgens wordt het venster gesloten.

Nadat u zich hebt aangemeld bij een Azure-account, kunt u de Azure PowerShell-cmdlets gebruiken om toegang te krijgen tot de resources in uw abonnement en om deze te beheren.

## <a name="create-a-windows-virtual-machine-using-simple-defaults"></a>Een virtuele Windows-machine maken met behulp van eenvoudige standaardwaarden

De cmdlet `New-AzureRmVM` biedt een vereenvoudigde syntaxis waarmee u gemakkelijk een nieuwe virtuele machine maakt. Er zijn slechts twee parameterwaarden die u moet opgeven: de naam van de VM en een set referenties voor het lokale beheerdersaccount op de VM.

Maak eerst het referentieobject.

```powershell
$cred = Get-Credential -Message "Enter a username and password for the virtual machine."
```

```Output
Windows PowerShell credential request.
Enter a username and password for the virtual machine.
User: localAdmin
Password for user localAdmin: *********
```
Maak vervolgens de VM.

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

Dat was makkelijk. Maar misschien vraagt u zich af wat er nog meer is gemaakt en hoe de VM is geconfigureerd. Bekijk eerst uw resourcegroepen.

```powershell
Get-AzureRmResourceGroup | Select-Object ResourceGroupName,Location
```

```Output
ResourceGroupName          Location
-----------------          --------
cloud-shell-storage-westus westus
SampleVM                   eastus
```

De resourcegroep **cloud-shell-storage-westus** wordt gemaakt wanneer u Cloud Shell voor het eerst gebruikt. De resourcegroep **SampleVM** is door de cmdlet `New-AzureRmVM` gemaakt.

Maar welke andere resources zijn er gemaakt in deze nieuwe resourcegroep?

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

Laten we wat meer informatie ophalen over de VM. Deze voorbeelden laten zien hoe u informatie over de installatiekopie van het besturingssysteem ophaalt die is gebruikt om de VM te maken.

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

## <a name="create-a-fully-configured-linux-virtual-machine"></a>Een volledig geconfigureerde virtuele Linux-machine maken

In het vorige voorbeeld werden de vereenvoudigde syntaxis en standaardparameterwaarden gebruikt om een virtuele Windows-machine te maken. In dit voorbeeld geven we waarden voor alle opties van de virtuele machine.

### <a name="create-a-resource-group"></a>Een resourcegroep maken

In dit voorbeeld maken we een resourcegroep. Resourcegroepen in Azure bieden u een manier voor het beheren van meerdere resources die u op een logische wijze wilt groeperen. U kunt bijvoorbeeld een resourcegroep voor een toepassing of project maken, en een virtuele machine, een database en een CDN-service aan deze resourcegroep toevoegen.

Laten we een resourcegroep maken met de naam 'MyResourceGroup' in de Azure-regio Europa West. Typ daartoe de volgende opdracht:

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

Deze nieuwe resourcegroep wordt gebruikt om alle benodigde resources voor het maken van een nieuwe VM op te slaan. Als we een nieuwe virtuele Linux-machine maken, moeten we eerst de vereiste resources maken en deze toewijzen aan een configuratie. Vervolgens gebruiken we die configuratie om de virtuele machine te maken. Er moet zich ook een openbare SSH-sleutel met de naam `id_rsa.pub` in de map .ssh van uw gebruikersprofiel bevinden.

#### <a name="create-the-required-network-resources"></a>De vereiste netwerkresources maken

Eerst moet er een subnetconfiguratie worden gemaakt die wordt gebruikt bij het maken van het virtuele netwerk. We gaan ook een openbaar IP-adres maken, zodat er verbinding met deze virtuele machine kan worden gemaakt. We maken een netwerkbeveiligingsgroep voor beveiligde toegang tot het openbare adres. Ten slotte maken we de virtuele NIC met alle voorgaande resources.

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

### <a name="create-the-vm-configuration"></a>De VM-configuratie maken

Nu u de vereiste resources hebt, kunt u het VM-configuratieobject maken.

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

### <a name="create-the-virtual-machine"></a>De virtuele machine maken

Nu kunt u de VM maken met behulp van het VM-configuratieobject.

```powershell
New-AzureRmVM -ResourceGroupName $resourceGroup -Location $location -VM $vmConfig
```

Nu de virtuele machine is gemaakt, kunt u zich aanmelden bij uw nieuwe virtuele Linux-machine via SSH, met het openbare IP-adres van de virtuele machine die u hebt gemaakt:

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

## <a name="creating-other-resources-in-azure"></a>Andere resources in Azure maken

We hebben u nu laten zien welke stappen u moet uitvoeren om een resourcegroep, een virtuele Linux-machine en een virtuele Windows Server-machine te maken. U kunt ook nog vele andere typen Azure-resources maken.

Als we bijvoorbeeld een Azure Network Load Balancer willen maken die we vervolgens gaan koppelen aan de nieuwe virtuele machines, kunnen we daarvoor de volgende opdracht gebruiken:

```powershell
New-AzureRmLoadBalancer -Name MyLoadBalancer -ResourceGroupName myResourceGroup -Location westeurope
```

We kunnen voor onze infrastructuur ook een nieuw privé virtueel netwerk (dat binnen Azure doorgaans 'VNet' wordt genoemd) maken en wel met de volgende opdracht:

```powershell
$subnetConfig = New-AzureRmVirtualNetworkSubnetConfig -Name mySubnet2 -AddressPrefix 10.0.0.0/16
$vnet = New-AzureRmVirtualNetwork -ResourceGroupName myResourceGroup -Location westeurope `
  -Name MYvNET3 -AddressPrefix 10.0.0.0/16 -Subnet $subnetConfig
```

Wat Azure en Azure PowerShell zo krachtig maakt, is dat ze niet alleen kunnen worden gebruikt in de cloudinfrastructuur, maar ook voor het maken van beheerde platformservices. De beheerde platformservices kunnen bovendien worden gecombineerd met de infrastructuur om nog krachtigere oplossingen te maken.

U kunt bijvoorbeeld Azure PowerShell gebruiken om een Azure AppService te maken. Azure AppService is een beheerde platformservice die uitstekend kan worden gebruikt om web-apps te hosten zonder dat u zich zorgen hoeft te maken over de infrastructuur. Nadat de Azure AppService is gemaakt, kunt u binnen de AppService twee nieuwe Azure-web-apps maken en wel met de volgende opdrachten:

```powershell
# Create an Azure AppService that we can host any number of web apps within
New-AzureRmAppServicePlan -Name MyAppServicePlan -Tier Basic -NumberofWorkers 2 -WorkerSize Small -ResourceGroupName myResourceGroup -Location westeurope

# Create Two Web Apps within the AppService (note: name param must be a unique DNS entry)
New-AzureRmWebApp -Name MyWebApp43432 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
New-AzureRmWebApp -Name MyWebApp43433 -AppServicePlan MyAppServicePlan -ResourceGroupName myResourceGroup -Location westeurope
```

## <a name="listing-deployed-resources"></a>Geïmplementeerde resources in een lijst weergeven

U kunt de cmdlet `Get-AzureRmResource` gebruiken om de resources weer te geven die in Azure worden uitgevoerd. In het volgende voorbeeld worden de resources weergegeven die we zojuist in de nieuwe resourcegroep hebben gemaakt.

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

## <a name="deleting-resources"></a>Resources verwijderen

Als u uw Azure-account wilt opschonen, moet u de resources verwijderen die in dit voorbeeld zijn gemaakt. U kunt de cmdlets `Remove-AzureRm*` gebruiken om de resources te verwijderen die u niet meer nodig hebt. Als u de virtuele Windows-machine wilt verwijderen die we hebben gemaakt, gebruikt u de volgende opdracht:

```powershell
Remove-AzureRmVM -Name myWindowsVM -ResourceGroupName myResourceGroup
```

U wordt gevraagd om te bevestigen dat u de resource wilt verwijderen.

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

U kunt ook een opdracht gebruiken om veel resources in één keer te verwijderen. Met de volgende opdracht wordt bijvoorbeeld de volledige resourcegroep 'MyResourceGroup' verwijderd die we hebben gebruikt in alle voorbeelden in deze Aan de slag-zelfstudie. Hiermee verwijdert u de resourcegroep en alle resources die deze bevat.

```powershell
Remove-AzureRmResourceGroup -Name myResourceGroup
```

```Output
Confirm
Are you sure you want to remove resource group 'myResourceGroup'
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
```

Dit kan enkele minuten in beslag nemen.

## <a name="get-samples"></a>Voorbeelden ophalen

Voor meer informatie over het gebruik van Azure PowerShell kunt u onze meest voorkomende scripts voor [virtuele Linux-machines](/azure/virtual-machines/virtual-machines-linux-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [virtuele Windows-machines](/azure/virtual-machines/virtual-machines-windows-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json), [Web Apps](/azure/app-service-web/app-service-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) en [SQL Databases](/azure/sql-database/sql-database-powershell-samples?toc=%2fpowershell%2fazure%%2ftoc.json) raadplegen.

## <a name="next-steps"></a>Volgende stappen

* [Aanmelden met Azure PowerShell](authenticate-azureps.md)
* [Azure-abonnementen beheren met Azure PowerShell](manage-subscriptions-azureps.md)
* [Azure PowerShell gebruiken om service-principals in Azure te maken](create-azure-service-principal-azureps.md)
* Lees de Releaseopmerkingen over het migreren van een oudere versie: [https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes](https://github.com/Azure/azure-powershell/tree/dev/documentation/release-notes).
* Hulp van de community:
  * [Azure-forum op MSDN](http://go.microsoft.com/fwlink/p/?LinkId=320212)
  * [Stackoverflow](http://go.microsoft.com/fwlink/?LinkId=320213)
