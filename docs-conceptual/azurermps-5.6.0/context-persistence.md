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
ms.openlocfilehash: 4b2b3b690a8c5d6951b24d49091154c6fb479fe3
ms.sourcegitcommit: 8376e0bc5f862d382d7283ba72990e3707591e7b
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2018
---
# <a name="persisting-user-logins-across-powershell-sessions"></a><span data-ttu-id="a737c-103">Gebruikersaanmeldingen behouden tussen PowerShell-sessies</span><span class="sxs-lookup"><span data-stu-id="a737c-103">Persisting user logins across PowerShell sessions</span></span>

<span data-ttu-id="a737c-104">In de release van september 2017 van Azure PowerShell introduceren we een nieuwe functie voor de cmdlets van Azure Resource Manager, namelijk **AzureRmContextAutoSave**.</span><span class="sxs-lookup"><span data-stu-id="a737c-104">In the September 2017 release of Azure PowerShell, Azure Resource Manager cmdlets introduce a new feature, **Azure Context Autosave**.</span></span> <span data-ttu-id="a737c-105">Met deze functie komen verschillende nieuwe gebruikersscenario's beschikbaar, waaronder:</span><span class="sxs-lookup"><span data-stu-id="a737c-105">This feature enables several new user scenarios, including:</span></span>

- <span data-ttu-id="a737c-106">Opslaan van aanmeldingsgegevens voor hergebruik in nieuwe PowerShell-sessies.</span><span class="sxs-lookup"><span data-stu-id="a737c-106">Retention of login information for reuse in new PowerShell sessions.</span></span>
- <span data-ttu-id="a737c-107">Eenvoudiger gebruik van achtergrondtaken voor het uitvoeren van langlopende cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a737c-107">Easier use of background tasks for executing long-running cmdlets.</span></span>
- <span data-ttu-id="a737c-108">Schakelen tussen accounts, abonnementen en omgevingen zonder afzonderlijke aanmelding.</span><span class="sxs-lookup"><span data-stu-id="a737c-108">Switch between accounts, subscriptions, and environments without a separate login.</span></span>
- <span data-ttu-id="a737c-109">Gelijktijdige uitvoering van taken met andere referenties en abonnementen, vanuit dezelfde PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="a737c-109">Execution of tasks using different credentials and subscriptions, simultaneously, from the same PowerShell session.</span></span>

## <a name="azure-contexts-defined"></a><span data-ttu-id="a737c-110">Definitie van Azure-contexten</span><span class="sxs-lookup"><span data-stu-id="a737c-110">Azure contexts defined</span></span>

<span data-ttu-id="a737c-111">Een *Azure-context* is een set gegevens die het doel van Azure PowerShell-cmdlets beschrijft.</span><span class="sxs-lookup"><span data-stu-id="a737c-111">An *Azure context* is a set of information that defines the target of Azure PowerShell cmdlets.</span></span> <span data-ttu-id="a737c-112">De context bestaat uit vijf onderdelen:</span><span class="sxs-lookup"><span data-stu-id="a737c-112">The context consists of five parts:</span></span>

- <span data-ttu-id="a737c-113">Een *account*: De gebruikersnaam of service-principal die wordt gebruikt voor de verificatie van de communicatie met Azure.</span><span class="sxs-lookup"><span data-stu-id="a737c-113">An *Account* - the UserName or Service Principal used to authenticate communications with Azure</span></span>
- <span data-ttu-id="a737c-114">Een *abonnement*: Het Azure-abonnement met de resources waarop een of meer bewerkingen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a737c-114">A *Subscription* - The Azure Subscription containing the Resources being acted upon.</span></span>
- <span data-ttu-id="a737c-115">Een *tenant*: De Azure Active Directory-tenant met uw abonnement.</span><span class="sxs-lookup"><span data-stu-id="a737c-115">A *Tenant* - The Azure Active Directory tenant that contains your subscription.</span></span> <span data-ttu-id="a737c-116">Tenants zijn met name belangrijk bij verificatie via een service-principal.</span><span class="sxs-lookup"><span data-stu-id="a737c-116">Tenants are more important to ServicePrincipal authentication.</span></span>
- <span data-ttu-id="a737c-117">Een *omgeving*: De specifieke Azure-cloud die als doel wordt ingesteld, meestal de algemene Azure-cloud.</span><span class="sxs-lookup"><span data-stu-id="a737c-117">An *Environment* - The particular Azure Cloud being targeted, usually the Azure global Cloud.</span></span>
  <span data-ttu-id="a737c-118">U kunt echter ook kiezen voor de omgeving National of Government en voor on-premises clouds (Azure Stack).</span><span class="sxs-lookup"><span data-stu-id="a737c-118">However, the environment setting allows you to target National, Government, and on-premises (Azure Stack) clouds as well.</span></span>
- <span data-ttu-id="a737c-119">*Referenties*: De informatie die door Azure wordt gebruikt om uw identiteit te controleren en u te autoriseren voor toegang tot resources in Azure.</span><span class="sxs-lookup"><span data-stu-id="a737c-119">*Credentials* - The information used by Azure to verify your identity and ensure your authorization to access resources in Azure</span></span>

<span data-ttu-id="a737c-120">In eerdere versies moest bij het openen van een nieuwe PowerShell-sessie steeds de context voor Azure worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="a737c-120">In previous releases, your Azure Context had to be created each time you opened a new PowerShell session.</span></span> <span data-ttu-id="a737c-121">Vanaf Azure PowerShell versie 4.4.0 kunt u de functie voor automatisch opslaan inschakelen en Azure-contexten opnieuw gebruiken wanneer u een nieuwe PowerShell-sessie opent.</span><span class="sxs-lookup"><span data-stu-id="a737c-121">Beginning with Azure PowerShell v4.4.0, you can enable the automatic saving and reuse of Azure Contexts whenever you open a new PowerShell session.</span></span>

## <a name="automatically-saving-the-context-for-the-next-login"></a><span data-ttu-id="a737c-122">Context automatisch opslaan voor volgende aanmelding</span><span class="sxs-lookup"><span data-stu-id="a737c-122">Automatically saving the context for the next login</span></span>

<span data-ttu-id="a737c-123">De standaardinstelling is dat contextgegevens worden verwijderd door Azure PowerShell wanneer u een PowerShell-sessie sluit.</span><span class="sxs-lookup"><span data-stu-id="a737c-123">By default, Azure PowerShell discards your context information whenever you close the PowerShell session.</span></span>

<span data-ttu-id="a737c-124">Gebruik `Enable-AzureRmContextAutosave` om aan te geven dat Azure PowerShell uw context moet onthouden nadat de PowerShell-sessie is gesloten.</span><span class="sxs-lookup"><span data-stu-id="a737c-124">To allow Azure PowerShell to remember your context after the PowerShell session is closed, use `Enable-AzureRmContextAutosave`.</span></span> <span data-ttu-id="a737c-125">De context en referentiegegevens worden dan automatisch opgeslagen in een speciale verborgen map in uw lijst met gebruikers (`%AppData%\Roaming\Windows Azure PowerShell`).</span><span class="sxs-lookup"><span data-stu-id="a737c-125">Context and credential information are automatically saved in a special hidden folder in your user directory (`%AppData%\Roaming\Windows Azure PowerShell`).</span></span>
<span data-ttu-id="a737c-126">In elke volgende PowerShell-sessie wordt dan automatisch de context uit de vorige sessie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a737c-126">Subsequently, each new PowerShell session targets the context used in your last session.</span></span>

<span data-ttu-id="a737c-127">Met `Disable-AzureRmContextAutoSave` geeft u opdracht om de context en referenties te wissen.</span><span class="sxs-lookup"><span data-stu-id="a737c-127">To set PowerShell to forget your context and credentials, use `Disable-AzureRmContextAutoSave`.</span></span> <span data-ttu-id="a737c-128">U moet u dan iedere keer aanmelden bij Azure wanneer u een PowerShell-sessie opent.</span><span class="sxs-lookup"><span data-stu-id="a737c-128">You will need to log in to Azure every time you open a PowerShell session.</span></span>

<span data-ttu-id="a737c-129">De cmdlets waarmee u Azure contexten kunt beheren, zijn ook geschikt om het bereik op te geven voor wijzigingen die u gaat aanbrengen.</span><span class="sxs-lookup"><span data-stu-id="a737c-129">The cmdlets that allow you to manage Azure contexts also allow you fine grained control.</span></span> <span data-ttu-id="a737c-130">Als u wilt dat wijzigingen alleen van toepassing zijn op de huidige PowerShell-sessie, gebruikt u `Process`. Met `CurrentUser` stelt u in dat de wijzigingen gelden voor elke PowerShell-sessie.</span><span class="sxs-lookup"><span data-stu-id="a737c-130">If you want changes to apply only to the current PowerShell session (`Process` scope) or every PowerShell session (`CurrentUser` scope).</span></span> <span data-ttu-id="a737c-131">Deze opties worden nader toegelicht in [Werken met contextbereiken](#Using-Context-Scopes).</span><span class="sxs-lookup"><span data-stu-id="a737c-131">These options are discussed in mode detail in [Using Context Scopes](#Using-Context-Scopes).</span></span>

## <a name="running-azure-powershell-cmdlets-as-background-jobs"></a><span data-ttu-id="a737c-132">Azure PowerShell-cmdlets uitvoeren als achtergrondtaken</span><span class="sxs-lookup"><span data-stu-id="a737c-132">Running Azure PowerShell cmdlets as background jobs</span></span>

<span data-ttu-id="a737c-133">Met de functie **AzureRmContextAutoSave** voor het automatisch opslaan van Azure-contexten kunt u een context ook delen met PowerShell-achtergrondtaken.</span><span class="sxs-lookup"><span data-stu-id="a737c-133">The **Azure Context Autosave** feature also allows you to share you context with PowerShell background jobs.</span></span> <span data-ttu-id="a737c-134">In PowerShell kunt u langlopende taken starten en controleren als achtergrondtaken, zonder dat u hoeft te wachten totdat de taken voltooid zijn.</span><span class="sxs-lookup"><span data-stu-id="a737c-134">PowerShell allows you to start and monitor long-executing tasks as background jobs without having to wait for the tasks to complete.</span></span> <span data-ttu-id="a737c-135">U kunt referenties op twee verschillende manieren delen met achtergrondtaken:</span><span class="sxs-lookup"><span data-stu-id="a737c-135">You can share credentials with background jobs in two different ways:</span></span>

- <span data-ttu-id="a737c-136">De context doorgeven als een argument</span><span class="sxs-lookup"><span data-stu-id="a737c-136">Passing the context as an argument</span></span>

  <span data-ttu-id="a737c-137">In de meeste AzureRM-cmdlets kunt u de context via een parameter doorgeven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a737c-137">Most AzureRM cmdlets allow you to pass the context as a parameter to the cmdlet.</span></span> <span data-ttu-id="a737c-138">U kunt een context doorgeven aan een achtergrondtaak zoals wordt weergegeven in het volgende voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a737c-138">You can pass a context to a background job as shown in the following example:</span></span>

  ```powershell
  PS C:\> $job = Start-Job { param ($ctx) New-AzureRmVm -AzureRmContext $ctx [... Additional parameters ...]} -ArgumentList (Get-AzureRmContext)
  ```

- <span data-ttu-id="a737c-139">De standaardcontext gebruiken met automatisch opslaan ingeschakeld</span><span class="sxs-lookup"><span data-stu-id="a737c-139">Using the default context with Autosave enabled</span></span>

  <span data-ttu-id="a737c-140">Als u **AzureRmContextAutoSave** hebt ingeschakeld, wordt voor achtergrondtaken automatisch de standaardcontext gebruikt die is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a737c-140">If you have enabled **Context Autosave**, background jobs automatically use the default saved context.</span></span>

  ```powershell
  PS C:\> $job = Start-Job { New-AzureRmVm [... Additional parameters ...]}
  ```

<span data-ttu-id="a737c-141">Als u het resultaat van de achtergrondtaak wilt weten, gebruikt u `Get-Job` om de taakstatus te controleren en `Wait-Job` om te wachten totdat de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="a737c-141">When you need to know the outcome of the background task, use `Get-Job` to check the job status and `Wait-Job` to wait for the Job to complete.</span></span> <span data-ttu-id="a737c-142">Gebruik `Receive-Job` om de uitvoer van de achtergrondtaak vast te leggen of weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a737c-142">Use `Receive-Job` to capture or display the output of the background job.</span></span> <span data-ttu-id="a737c-143">Zie [About Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs) (Taken) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a737c-143">For more information, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

## <a name="creating-selecting-renaming-and-removing-contexts"></a><span data-ttu-id="a737c-144">Contexten maken, selecteren, verwijderen en een andere naam geven</span><span class="sxs-lookup"><span data-stu-id="a737c-144">Creating, selecting, renaming, and removing contexts</span></span>

<span data-ttu-id="a737c-145">Als u een context wilt maken, moet u zijn aangemeld bij Azure.</span><span class="sxs-lookup"><span data-stu-id="a737c-145">To create a context, you must be logged in to Azure.</span></span> <span data-ttu-id="a737c-146">Met de cmdlet `Connect-AzureRmAccount` (of de bijbehorende alias `Login-AzureRmAccount`) stelt u de standaardcontext in die moet worden gebruikt door volgende Azure PowerShell-cmdlets. De cmdlet biedt ook toegang tot alle tenants of abonnementen die toegankelijk zijn met uw aanmeldingsreferenties.</span><span class="sxs-lookup"><span data-stu-id="a737c-146">The `Connect-AzureRmAccount` cmdlet (or its alias, `Login-AzureRmAccount`) sets the default context used by subsequent Azure PowerShell cmdlets, and allows you to access any tenants or subscriptions allowed by your login credentials.</span></span>

<span data-ttu-id="a737c-147">Als u na aanmelding een nieuwe context wilt toevoegen, gebruikt u `Set-AzureRmContext` (of de alias `Select-AzureRmSubscription`).</span><span class="sxs-lookup"><span data-stu-id="a737c-147">To add a new context after login, use `Set-AzureRmContext` (or its alias, `Select-AzureRmSubscription`).</span></span>

```powershell
PS C:\> Set-AzureRMContext -Subscription "Contoso Subscription 1" -Name "Contoso1"
```

<span data-ttu-id="a737c-148">In het vorige voorbeeld wordt met behulp van uw huidige referenties een nieuwe context voor 'Contoso Subscription 1' toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="a737c-148">The previous example adds a new context targeting 'Contoso Subscription 1' using your current credentials.</span></span> <span data-ttu-id="a737c-149">De naam van de nieuwe context is 'Contoso1'.</span><span class="sxs-lookup"><span data-stu-id="a737c-149">The new context is named 'Contoso1'.</span></span> <span data-ttu-id="a737c-150">Als u geen naam opgeeft voor de context, wordt er automatisch een standaardnaam gebruikt, op basis van de account-id en de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="a737c-150">If you do not provide a name for the context, a default name, using the account ID and subscription ID is used.</span></span>

<span data-ttu-id="a737c-151">Als u de naam van een bestaande context wilt wijzigen, gebruikt u de cmdlet `Rename-AzureRmContext`.</span><span class="sxs-lookup"><span data-stu-id="a737c-151">To rename an existing context, use the `Rename-AzureRmContext` cmdlet.</span></span> <span data-ttu-id="a737c-152">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a737c-152">For example:</span></span>

```powershell
PS C:\> Rename-AzureRmContext '[user1@contoso.org; 123456-7890-1234-564321]` 'Contoso2'
```

<span data-ttu-id="a737c-153">In dit voorbeeld wijzigt u de automatisch toegewezen contextnaam `[user1@contoso.org; 123456-7890-1234-564321]` in de overzichtelijke naam 'Contoso2'.</span><span class="sxs-lookup"><span data-stu-id="a737c-153">This example renames the context with automatic name `[user1@contoso.org; 123456-7890-1234-564321]` to the simple name 'Contoso2'.</span></span> <span data-ttu-id="a737c-154">Cmdlets voor het beheren van contexten bieden ook ondersteuning voor tabvoltooiing, zodat u snel de context kunt selecteren.</span><span class="sxs-lookup"><span data-stu-id="a737c-154">Cmdlets that manage contexts also use tab completion, allowing you to quickly select the context.</span></span>

<span data-ttu-id="a737c-155">Met cmdlet `Remove-AzureRmContext` kunt u een context altijd weer verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a737c-155">Finally, to remove a context, use the `Remove-AzureRmContext` cmdlet.</span></span>  <span data-ttu-id="a737c-156">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a737c-156">For example:</span></span>

```powershell
PS C:\> Remove-AzureRmContext Contoso2
```

<span data-ttu-id="a737c-157">De context met de naam 'Contoso2' wordt nu niet gebruikt in de volgende sessie.</span><span class="sxs-lookup"><span data-stu-id="a737c-157">Forgets the context that was named 'Contoso2'.</span></span> <span data-ttu-id="a737c-158">U kunt deze context weer opnieuw maken met behulp van `Set-AzureRmContext`.</span><span class="sxs-lookup"><span data-stu-id="a737c-158">You can recreate this context subsequently using `Set-AzureRmContext`</span></span>

## <a name="removing-credentials"></a><span data-ttu-id="a737c-159">Referenties verwijderen</span><span class="sxs-lookup"><span data-stu-id="a737c-159">Removing credentials</span></span>

<span data-ttu-id="a737c-160">Met behulp van `Remove-AzureRmAccount` (ook wel bekend als `Logout-AzureRmAccount`) kunt u alle referenties en bijbehorende contexten voor een gebruiker of service-principal verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a737c-160">You can remove all credentials and associated contexts for a user or service principal using `Remove-AzureRmAccount` (also known as `Logout-AzureRmAccount`).</span></span> <span data-ttu-id="a737c-161">Als u de cmdlet `Remove-AzureRmAccount` uitvoert zonder parameters, verwijdert u alle referenties en contexten die zijn gekoppeld aan de gebruiker of service-principal in de huidige context.</span><span class="sxs-lookup"><span data-stu-id="a737c-161">When executed without parameters, the `Remove-AzureRmAccount` cmdlet removes all credentials and contexts associated with the User or Service Principal in the current context.</span></span> <span data-ttu-id="a737c-162">U kunt een gebruikersnaam, de naam van een service-principal of een context opgeven om alleen gegevens voor een bepaalde principal te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a737c-162">You may pass in a Username, Service Principal Name, or context to target a particular principal.</span></span>

```powershell
Remove-AzureRmAccount user1@contoso.org
```

## <a name="using-context-scopes"></a><span data-ttu-id="a737c-163">Werken met contextbereiken</span><span class="sxs-lookup"><span data-stu-id="a737c-163">Using context scopes</span></span>

<span data-ttu-id="a737c-164">Het kan gebeuren dat u een context in een PowerShell-sessie wilt selecteren, wijzigen of verwijderen zonder dat dit gevolgen heeft voor andere sessies.</span><span class="sxs-lookup"><span data-stu-id="a737c-164">Occasionally, you may want to select, change, or remove a context in a PowerShell session without impacting other sessions.</span></span> <span data-ttu-id="a737c-165">U kunt het standaardgedrag van context-cmdlets wijzigen met de parameter `Scope`.</span><span class="sxs-lookup"><span data-stu-id="a737c-165">To change the default behavior of context cmdlets, use the `Scope` parameter.</span></span> <span data-ttu-id="a737c-166">Met het bereik `Process` overschrijft u het standaardgedrag door de wijzigingen alleen te laten gelden voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a737c-166">The `Process` scope overrides the default behavior by making it apply only for the current session.</span></span> <span data-ttu-id="a737c-167">Als u daarentegen het bereik `CurrentUser` opgeeft, wordt de context in alle sessies gewijzigd, dus niet alleen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="a737c-167">Conversely `CurrentUser` scope changes the context in all sessions, instead of just the current session.</span></span>

<span data-ttu-id="a737c-168">Gebruik bijvoorbeeld deze opdracht om de standaardcontext alleen te wijzigen in de huidige PowerShell-sessie, dus niet in andere vensters en evenmin in de context van de volgende sessie die wordt geopend:</span><span class="sxs-lookup"><span data-stu-id="a737c-168">As an example, to change the default context in the current PowerShell session without impacting other windows, or the context used the next time a session is opened, use:</span></span>

```powershell
PS C:\> Select-AzureRmContext Contoso1 -Scope Process
```

## <a name="how-the-context-autosave-setting-is-remembered"></a><span data-ttu-id="a737c-169">Locatie van instelling voor automatisch opslaan van context</span><span class="sxs-lookup"><span data-stu-id="a737c-169">How the context autosave setting is remembered</span></span>

<span data-ttu-id="a737c-170">De instelling van AzureRmContextAutoSave wordt opgeslagen in de lijst met gebruikers van Azure PowerShell (`%AppData%\Roaming\Windows Azure PowerShell`).</span><span class="sxs-lookup"><span data-stu-id="a737c-170">The context AutoSave setting is saved to the user Azure PowerShell directory (`%AppData%\Roaming\Windows Azure PowerShell`).</span></span> <span data-ttu-id="a737c-171">Het is mogelijk dat bepaalde typen computeraccounts geen toegang hebben tot deze lijst.</span><span class="sxs-lookup"><span data-stu-id="a737c-171">Some kinds of computer accounts may not have access to this directory.</span></span> <span data-ttu-id="a737c-172">Voor dergelijke scenario's kunt u deze omgevingsvariabele gebruiken:</span><span class="sxs-lookup"><span data-stu-id="a737c-172">For such scenarios, you can use the environment variable</span></span>

```powershell
$env:AzureRmContextAutoSave="true" | "false"
```

<span data-ttu-id="a737c-173">Als deze variabele is ingesteld op 'true', wordt de context automatisch opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a737c-173">If set to 'true', the context is automatically saved.</span></span> <span data-ttu-id="a737c-174">Als u deze variabele instelt op 'false', wordt de context niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="a737c-174">If set to 'false', the context is not saved.</span></span>

## <a name="changes-to-the-azurermprofile-module"></a><span data-ttu-id="a737c-175">Wijzigingen aan de module AzureRM.Profile</span><span class="sxs-lookup"><span data-stu-id="a737c-175">Changes to the AzureRM.Profile module</span></span>

<span data-ttu-id="a737c-176">Nieuwe cmdlets voor het beheren van context</span><span class="sxs-lookup"><span data-stu-id="a737c-176">New cmdlets for managing context</span></span>

- <span data-ttu-id="a737c-177">[Enable-AzureRmContextAutosave][enable]: De context opslaan tussen PowerShell-sessies.</span><span class="sxs-lookup"><span data-stu-id="a737c-177">[Enable-AzureRmContextAutosave][enable] - Allow saving the context between powershell sessions.</span></span>
  <span data-ttu-id="a737c-178">Wijzigingen zijn van invloed op de algemene context.</span><span class="sxs-lookup"><span data-stu-id="a737c-178">Any changes alter the global context.</span></span>
- <span data-ttu-id="a737c-179">[Disable-AzureRmContextAutosave][disable]: Automatisch opslaan van context uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="a737c-179">[Disable-AzureRmContextAutosave][disable] - Turn off autosaving the context.</span></span> <span data-ttu-id="a737c-180">Bij elke nieuwe PowerShell-sessie is opnieuw aanmelden vereist.</span><span class="sxs-lookup"><span data-stu-id="a737c-180">Each new PowerShell session is required to log in again.</span></span>
- <span data-ttu-id="a737c-181">[Select-AzureRmContext][select]: Een context selecteren als de standaardcontext.</span><span class="sxs-lookup"><span data-stu-id="a737c-181">[Select-AzureRmContext][select] - Select a context as the default.</span></span> <span data-ttu-id="a737c-182">Alle volgende cmdlets gebruiken de referenties in deze context voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="a737c-182">All subsequent cmdlets use the credentials in this context for authentication.</span></span>
- <span data-ttu-id="a737c-183">[Remove-AzureRmAccount][remove-cred]: Alle referenties en contexten verwijderen die aan een account zijn gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="a737c-183">[Remove-AzureRmAccount][remove-cred] - Remove all credentials and contexts associated with an account.</span></span>
- <span data-ttu-id="a737c-184">[Remove-AzureRmContext][remove-context]: De opgegeven context verwijderen.</span><span class="sxs-lookup"><span data-stu-id="a737c-184">[Remove-AzureRmContext][remove-context] - Remove a named context.</span></span>
- <span data-ttu-id="a737c-185">[Rename-AzureRmContext][rename]: De naam van een bestaande context wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a737c-185">[Rename-AzureRmContext][rename] - Rename an existing context.</span></span>

<span data-ttu-id="a737c-186">Wijzigingen aan bestaande profiel-cmdlets</span><span class="sxs-lookup"><span data-stu-id="a737c-186">Changes to existing profile cmdlets</span></span>

- <span data-ttu-id="a737c-187">[Add-AzureRmAccount][login]: Het bereik van de aanmelding instellen op het proces of de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a737c-187">[Add-AzureRmAccount][login] - Allow scoping of the login to the process or the current user.</span></span>
  <span data-ttu-id="a737c-188">De naam van de standaardcontext kan na aanmelding worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a737c-188">Allow naming the default context after login.</span></span>
- <span data-ttu-id="a737c-189">[Import-AzureRmContext][import]: Het bereik van de aanmelding instellen op het proces of de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a737c-189">[Import-AzureRmContext][import] - Allow scoping of the login to the process or the current user.</span></span>
- <span data-ttu-id="a737c-190">[Set-AzureRmContext][set-context]: Selectie toestaan van bestaande benoemde contexten, en bereik wijzigen (proces of huidige gebruiker).</span><span class="sxs-lookup"><span data-stu-id="a737c-190">[Set-AzureRmContext][set-context] - Allow selection of existing named contexts, and scope changes to the process or current user.</span></span>

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
