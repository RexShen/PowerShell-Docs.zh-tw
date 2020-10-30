---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 管理服務
description: PowerShell 提供數個 Cmdlet，可協助管理本機和遠端電腦上的服務。
ms.openlocfilehash: 003803cdaa37e51b3788f3f897cbec7d6e243ca8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500346"
---
# <a name="managing-services"></a><span data-ttu-id="c5e1c-104">管理服務</span><span class="sxs-lookup"><span data-stu-id="c5e1c-104">Managing Services</span></span>

<span data-ttu-id="c5e1c-105">有八個針對各種服務工作設計的核心服務 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-105">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="c5e1c-106">我們只會探討列出及變更服務的執行中狀態，但您可以使用 `Get-Help \*-Service` 取得服務 Cmdlet 清單，以及使用 `Get-Help <Cmdlet-Name>` (例如 `Get-Help New-Service`) 尋找各個服務 Cmdlet 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-106">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="c5e1c-107">取得服務</span><span class="sxs-lookup"><span data-stu-id="c5e1c-107">Getting Services</span></span>

<span data-ttu-id="c5e1c-108">您可以使用 `Get-Service` Cmdlet 取得本機或遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-108">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="c5e1c-109">如同 `Get-Process`，在不使用參數的情況下使用 `Get-Service` 命令會傳回所有服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-109">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="c5e1c-110">您可以依名稱篩選，甚至可以使用星號作為萬用字元︰</span><span class="sxs-lookup"><span data-stu-id="c5e1c-110">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="c5e1c-111">因為服務的實際名稱不一定很明顯，所以您有時可能需要依顯示名稱尋找服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-111">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="c5e1c-112">您可以依特定名稱、使用萬用字元或使用顯示名稱清單來執行這項操作︰</span><span class="sxs-lookup"><span data-stu-id="c5e1c-112">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="c5e1c-113">您可以使用 Get-Service Cmdlet 的 ComputerName 參數取得遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-113">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="c5e1c-114">ComputerName 參數接受多個值和萬用字元，因此您可以使用單一命令取得多部電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-114">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="c5e1c-115">例如，下列命令會取得 Server01 遠端電腦上的服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-115">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="c5e1c-116">取得必要和相依的服務</span><span class="sxs-lookup"><span data-stu-id="c5e1c-116">Getting Required and Dependent Services</span></span>

<span data-ttu-id="c5e1c-117">Get-Service Cmdlet 有兩個對服務管理很有用的參數。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-117">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="c5e1c-118">DependentServices 參數可取得依存於此服務的服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-118">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="c5e1c-119">RequiredServices 參數可取得此服務依存的服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-119">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="c5e1c-120">這些參數只會顯示 Get-Service 所傳回之 System.ServiceProcess.ServiceController 物件的 DependentServices 和 ServicesDependedOn (別名=RequiredServices) 屬性值，但它們簡化了命令，讓您更容易取得這項資訊。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-120">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="c5e1c-121">下列命令會取得 LanmanWorkstation 服務所需的服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-121">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="c5e1c-122">下列命令會取得需要 LanmanWorkstation 服務的服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-122">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="c5e1c-123">您甚至可以取得具有相依性的所有服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-123">You can even get all services that have dependencies.</span></span> <span data-ttu-id="c5e1c-124">下列命令會執行這項操作，然後使用 Format-Table Cmdlet 顯示電腦上服務的 Status、Name、RequiredServices 和 DependentServices 屬性。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-124">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="c5e1c-125">停止、啟動、暫停及重新啟動服務</span><span class="sxs-lookup"><span data-stu-id="c5e1c-125">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="c5e1c-126">所有服務 Cmdlet 都有相同的一般形式。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-126">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="c5e1c-127">服務可以使用一般名稱或顯示名稱來指定，並接受清單和萬用字元作為值。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-127">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="c5e1c-128">若要停止列印多工緩衝處理器，請使用：</span><span class="sxs-lookup"><span data-stu-id="c5e1c-128">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="c5e1c-129">若要啟動已停止的列印多工緩衝處理器，請使用：</span><span class="sxs-lookup"><span data-stu-id="c5e1c-129">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="c5e1c-130">若要暫停列印多工緩衝處理器，請使用：</span><span class="sxs-lookup"><span data-stu-id="c5e1c-130">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="c5e1c-131">`Restart-Service` Cmdlet 與其他服務 Cmdlet 的運作方式相同，不過我們將示範一些更複雜的範例。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-131">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="c5e1c-132">最簡單的使用方式是指定服務的名稱︰</span><span class="sxs-lookup"><span data-stu-id="c5e1c-132">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="c5e1c-133">您會發現自己一再重複收到有關列印多工緩衝處理器正在啟動的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-133">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="c5e1c-134">當您執行需要一些時間的服務操作時，Windows PowerShell 會通知您，它仍在嘗試執行工作。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-134">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="c5e1c-135">如果您想要重新啟動多項服務，您可以取得服務清單、加以篩選，然後執行重新啟動︰</span><span class="sxs-lookup"><span data-stu-id="c5e1c-135">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="c5e1c-136">這些服務 Cmdlet 沒有 ComputerName 參數，但您可以使用 Invoke-Command Cmdlet 在遠端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-136">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="c5e1c-137">例如，下列命令會重新啟動 Server01 遠端電腦上的多工緩衝處理器服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-137">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="c5e1c-138">設定服務屬性</span><span class="sxs-lookup"><span data-stu-id="c5e1c-138">Setting Service Properties</span></span>

<span data-ttu-id="c5e1c-139">`Set-Service` Cmdlet 會變更本機或遠端電腦上的服務屬性。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-139">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="c5e1c-140">因為服務狀態是屬性，所以您可以使用這個 Cmdlet 來啟動、停止及暫停服務。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-140">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="c5e1c-141">Set-Service Cmdlet 也有 StartupType 參數，可讓您變更服務啟動類型。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-141">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="c5e1c-142">若要在 Windows Vista 和更新的 Windows 版本上使用 `Set-Service`，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c5e1c-142">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="c5e1c-143">如需詳細資訊，請參閱 [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span><span class="sxs-lookup"><span data-stu-id="c5e1c-143">For more information, see [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span></span>

## <a name="see-also"></a><span data-ttu-id="c5e1c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5e1c-144">See Also</span></span>

- [<span data-ttu-id="c5e1c-145">Get-Service</span><span class="sxs-lookup"><span data-stu-id="c5e1c-145">Get-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [<span data-ttu-id="c5e1c-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="c5e1c-146">Set-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [<span data-ttu-id="c5e1c-147">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="c5e1c-147">Restart-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [<span data-ttu-id="c5e1c-148">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="c5e1c-148">Suspend-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
