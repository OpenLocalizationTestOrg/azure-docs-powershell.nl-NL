---
title: Gebruikersaanmeldingen behouden tussen PowerShell-sessies
description: In dit artikel worden nieuwe functies in Azure PowerShell beschreven waarmee u referenties en andere gebruikersinformatie kunt hergebruiken in verschillende PowerShell-sessies.
services: azure
author: sdwheeler
ms.author: sewhee
manager: carmonm
ms.product: azure
ms.service: azure-powershell
ms.devlang: powershell
ms.topic: conceptual
ms.date: 08/31/2017
ms.openlocfilehash: 8ef20796b64b16c78a653e293a57d5e752d89710
ms.sourcegitcommit: 15bf69bf95eceb936b3a429e741add95c308826a
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2018
---
# <a name="persisting-user-logins-across-powershell-sessions"></a>Gebruikersaanmeldingen behouden tussen PowerShell-sessies

In de release van september 2017 van Azure PowerShell introduceren we een nieuwe functie voor de cmdlets van Azure Resource Manager, namelijk **AzureRmContextAutoSave**. Met deze functie komen verschillende nieuwe gebruikersscenario's beschikbaar, waaronder:

- Opslaan van aanmeldingsgegevens voor hergebruik in nieuwe PowerShell-sessies.
- Eenvoudiger gebruik van achtergrondtaken voor het uitvoeren van langlopende cmdlets.
- Schakelen tussen accounts, abonnementen en omgevingen zonder afzonderlijke aanmelding.
- Gelijktijdige uitvoering van taken met andere referenties en abonnementen, vanuit dezelfde PowerShell-sessie.

## <a name="azure-contexts-defined"></a>Definitie van Azure-contexten

Een *Azure-context* is een set gegevens die het doel van Azure PowerShell-cmdlets beschrijft. De context bestaat uit vijf onderdelen:

- Een *account*: De gebruikersnaam of service-principal die wordt gebruikt voor de verificatie van de communicatie met Azure.
- Een *abonnement*: Het Azure-abonnement met de resources waarop een of meer bewerkingen worden uitgevoerd.
- Een *tenant*: De Azure Active Directory-tenant met uw abonnement. Tenants zijn met name belangrijk bij verificatie via een service-principal.
- Een *omgeving*: De specifieke Azure-cloud die als doel wordt ingesteld, meestal de algemene Azure-cloud.
  U kunt echter ook kiezen voor de omgeving National of Government en voor on-premises clouds (Azure Stack).
- *Referenties*: De informatie die door Azure wordt gebruikt om uw identiteit te controleren en u te autoriseren voor toegang tot resources in Azure.

In eerdere versies moest bij het openen van een nieuwe PowerShell-sessie steeds de context voor Azure worden ingesteld. Vanaf Azure PowerShell versie 4.4.0 kunt u de functie voor automatisch opslaan inschakelen en Azure-contexten opnieuw gebruiken wanneer u een nieuwe PowerShell-sessie opent.

## <a name="automatically-saving-the-context-for-the-next-login"></a>Context automatisch opslaan voor volgende aanmelding

De standaardinstelling is dat contextgegevens worden verwijderd door Azure PowerShell wanneer u een PowerShell-sessie sluit.

Gebruik `Enable-AzureRmContextAutosave` om aan te geven dat Azure PowerShell uw context moet onthouden nadat de PowerShell-sessie is gesloten. De context en referentiegegevens worden dan automatisch opgeslagen in een speciale verborgen map in uw lijst met gebruikers (`%AppData%\Roaming\Windows Azure PowerShell`).
In elke volgende PowerShell-sessie wordt dan automatisch de context uit de vorige sessie gebruikt.

Met `Disable-AzureRmContextAutoSave` geeft u opdracht om de context en referenties te wissen. U moet u dan iedere keer aanmelden bij Azure wanneer u een PowerShell-sessie opent.

De cmdlets waarmee u Azure contexten kunt beheren, zijn ook geschikt om het bereik op te geven voor wijzigingen die u gaat aanbrengen. Als u wilt dat wijzigingen alleen van toepassing zijn op de huidige PowerShell-sessie, gebruikt u `Process`. Met `CurrentUser` stelt u in dat de wijzigingen gelden voor elke PowerShell-sessie. Deze opties worden nader toegelicht in [Werken met contextbereiken](#Using-Context-Scopes).

## <a name="running-azure-powershell-cmdlets-as-background-jobs"></a>Azure PowerShell-cmdlets uitvoeren als achtergrondtaken

Met de functie **AzureRmContextAutoSave** voor het automatisch opslaan van Azure-contexten kunt u een context ook delen met PowerShell-achtergrondtaken. In PowerShell kunt u langlopende taken starten en controleren als achtergrondtaken, zonder dat u hoeft te wachten totdat de taken voltooid zijn. U kunt referenties op twee verschillende manieren delen met achtergrondtaken:

- De context doorgeven als een argument

  In de meeste AzureRM-cmdlets kunt u de context via een parameter doorgeven aan de cmdlet. U kunt een context doorgeven aan een achtergrondtaak zoals wordt weergegeven in het volgende voorbeeld:

  ```powershell
  PS C:\> $job = Start-Job { param ($ctx) New-AzureRmVm -AzureRmContext $ctx [... Additional parameters ...]} -ArgumentList (Get-AzureRmContext)
  ```

- De standaardcontext gebruiken met automatisch opslaan ingeschakeld

  Als u **AzureRmContextAutoSave** hebt ingeschakeld, wordt voor achtergrondtaken automatisch de standaardcontext gebruikt die is opgeslagen.

  ```powershell
  PS C:\> $job = Start-Job { New-AzureRmVm [... Additional parameters ...]}
  ```

Als u het resultaat van de achtergrondtaak wilt weten, gebruikt u `Get-Job` om de taakstatus te controleren en `Wait-Job` om te wachten totdat de taak is voltooid. Gebruik `Receive-Job` om de uitvoer van de achtergrondtaak vast te leggen of weer te geven. Zie [About Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs) (Taken) voor meer informatie.

## <a name="creating-selecting-renaming-and-removing-contexts"></a>Contexten maken, selecteren, verwijderen en een andere naam geven

Als u een context wilt maken, moet u zijn aangemeld bij Azure. Met de cmdlet `Add-AzureRmAccount` (of de bijbehorende alias `Login-AzureRmAccount`) stelt u de standaardcontext in die moet worden gebruikt door volgende Azure PowerShell-cmdlets. De cmdlet biedt ook toegang tot alle tenants of abonnementen die toegankelijk zijn met uw aanmeldingsreferenties.

Als u na aanmelding een nieuwe context wilt toevoegen, gebruikt u `Set-AzureRmContext` (of de alias `Select-AzureRmSubscription`).

```powershell
PS C:\> Set-AzureRMContext -Subscription "Contoso Subscription 1" -Name "Contoso1"
```

In het vorige voorbeeld wordt met behulp van uw huidige referenties een nieuwe context voor 'Contoso Subscription 1' toegevoegd. De naam van de nieuwe context is 'Contoso1'. Als u geen naam opgeeft voor de context, wordt er automatisch een standaardnaam gebruikt, op basis van de account-id en de abonnements-id.

Als u de naam van een bestaande context wilt wijzigen, gebruikt u de cmdlet `Rename-AzureRmContext`. Bijvoorbeeld:

```powershell
PS C:\> Rename-AzureRmContext '[user1@contoso.org; 123456-7890-1234-564321]` 'Contoso2'
```

In dit voorbeeld wijzigt u de automatisch toegewezen contextnaam `[user1@contoso.org; 123456-7890-1234-564321]` in de overzichtelijke naam 'Contoso2'. Cmdlets voor het beheren van contexten bieden ook ondersteuning voor tabvoltooiing, zodat u snel de context kunt selecteren.

Met cmdlet `Remove-AzureRmContext` kunt u een context altijd weer verwijderen.  Bijvoorbeeld:

```powershell
PS C:\> Remove-AzureRmContext Contoso2
```

De context met de naam 'Contoso2' wordt nu niet gebruikt in de volgende sessie. U kunt deze context weer opnieuw maken met behulp van `Set-AzureRmContext`.

## <a name="removing-credentials"></a>Referenties verwijderen

Met behulp van `Remove-AzureRmAccount` (ook wel bekend als `Logout-AzureRmAccount`) kunt u alle referenties en bijbehorende contexten voor een gebruiker of service-principal verwijderen. Als u de cmdlet `Remove-AzureRmAccount` uitvoert zonder parameters, verwijdert u alle referenties en contexten die zijn gekoppeld aan de gebruiker of service-principal in de huidige context. U kunt een gebruikersnaam, de naam van een service-principal of een context opgeven om alleen gegevens voor een bepaalde principal te verwijderen.

```powershell
Remove-AzureRmAccount user1@contoso.org
```

## <a name="using-context-scopes"></a>Werken met contextbereiken

Het kan gebeuren dat u een context in een PowerShell-sessie wilt selecteren, wijzigen of verwijderen zonder dat dit gevolgen heeft voor andere sessies. U kunt het standaardgedrag van context-cmdlets wijzigen met de parameter `Scope`. Met het bereik `Process` overschrijft u het standaardgedrag door de wijzigingen alleen te laten gelden voor de huidige sessie. Als u daarentegen het bereik `CurrentUser` opgeeft, wordt de context in alle sessies gewijzigd, dus niet alleen in de huidige sessie.

Gebruik bijvoorbeeld deze opdracht om de standaardcontext alleen te wijzigen in de huidige PowerShell-sessie, dus niet in andere vensters en evenmin in de context van de volgende sessie die wordt geopend:

```powershell
PS C:\> Select-AzureRmContext Contoso1 -Scope Process
```

## <a name="how-the-context-autosave-setting-is-remembered"></a>Locatie van instelling voor automatisch opslaan van context

De instelling van AzureRmContextAutoSave wordt opgeslagen in de lijst met gebruikers van Azure PowerShell (`%AppData%\Roaming\Windows Azure PowerShell`). Het is mogelijk dat bepaalde typen computeraccounts geen toegang hebben tot deze lijst. Voor dergelijke scenario's kunt u deze omgevingsvariabele gebruiken:

```powershell
$env:AzureRmContextAutoSave="true" | "false"
```

Als deze variabele is ingesteld op 'true', wordt de context automatisch opgeslagen. Als u deze variabele instelt op 'false', wordt de context niet opgeslagen.

## <a name="changes-to-the-azurermprofile-module"></a>Wijzigingen aan de module AzureRM.Profile

Nieuwe cmdlets voor het beheren van context

- [Enable-AzureRmContextAutosave][enable]: De context opslaan tussen PowerShell-sessies.
  Wijzigingen zijn van invloed op de algemene context.
- [Disable-AzureRmContextAutosave][disable]: Automatisch opslaan van context uitschakelen. Bij elke nieuwe PowerShell-sessie is opnieuw aanmelden vereist.
- [Select-AzureRmContext][select]: Een context selecteren als de standaardcontext. Alle volgende cmdlets gebruiken de referenties in deze context voor verificatie.
- [Remove-AzureRmAccount][remove-cred]: Alle referenties en contexten verwijderen die aan een account zijn gekoppeld.
- [Remove-AzureRmContext][remove-context]: De opgegeven context verwijderen.
- [Rename-AzureRmContext][rename]: De naam van een bestaande context wijzigen.

Wijzigingen aan bestaande profiel-cmdlets

- [Add-AzureRmAccount][login]: Het bereik van de aanmelding instellen op het proces of de huidige gebruiker.
  De naam van de standaardcontext kan na aanmelding worden opgegeven.
- [Import-AzureRmContext][import]: Het bereik van de aanmelding instellen op het proces of de huidige gebruiker.
- [Set-AzureRmContext][set-context]: Selectie toestaan van bestaande benoemde contexten, en bereik wijzigen (proces of huidige gebruiker).

<!-- Hyperlinks -->
[enable]: /powershell/module/azurerm.profile/Enable-AzureRmContextAutosave
[disable]: /powershell/module/azurerm.profile/Disable-AzureRmContextAutosave
[select]: /powershell/module/azurerm.profile/Select-AzureRmContext
[remove-cred]: /powershell/module/azurerm.profile/Remove-AzureRmAccount
[remove-context]: /powershell/module/azurerm.profile/Remove-AzureRmContext
[rename]: /powershell/module/azurerm.profile/Rename-AzureRmContext

<!-- Updated cmdlets -->
[login]: /powershell/module/azurerm.profile/Add-AzureRmAccount
[import]: /powershell/module/azurerm.profile/Import-AzureRmAccount
[set-context]: /powershell/module/azurerm.profile/Import-AzureRmContext
