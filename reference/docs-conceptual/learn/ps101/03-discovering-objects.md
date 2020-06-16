---
title: 探索物件、屬性與方法
description: 您不需要是開發人員，就能瞭解及使用物件、屬性和方法。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 5ab972755afeba0d94bf6c2debaf84ec84cd9244
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438069"
---
# <a name="chapter-3---discovering-objects-properties-and-methods"></a><span data-ttu-id="75919-103">第 3 章 - 探索物件、屬性與方法</span><span class="sxs-lookup"><span data-stu-id="75919-103">Chapter 3 - Discovering objects, properties, and methods</span></span>

<span data-ttu-id="75919-104">我的第一部入門電腦是 Commodore 64，但我的第一部新式電腦是執行 Microsoft DOS 3.3 的 286 12-Mhz IBM 仿製品 ，配備 1 MB 記憶體、40 MB 硬碟，以及 5-1/4 吋軟碟機和 CGA 顯示器。</span><span class="sxs-lookup"><span data-stu-id="75919-104">My first introduction to computers was a Commodore 64, but my first modern computer was a 286 12-Mhz IBM clone with 1 megabyte of memory, a 40-megabyte hard drive, and one 5-1/4 inch floppy disk drive with a CGA monitor running Microsoft DOS 3.3.</span></span>

<span data-ttu-id="75919-105">許多 IT 專家 (像我自己) 都對命令列不陌生，但是一提到物件、屬性和方法等主題時，他們就像被車頭燈照到的鹿一樣驚惶失措，連忙否認說「我不是開發人員」。</span><span class="sxs-lookup"><span data-stu-id="75919-105">Many IT Pros, like myself, are no stranger to the command line, but when the subject of objects, properties, and methods comes up, they get the deer in the headlights look and say, "I'm not a developer."</span></span> <span data-ttu-id="75919-106">但您知道嗎？</span><span class="sxs-lookup"><span data-stu-id="75919-106">Guess what?</span></span> <span data-ttu-id="75919-107">不是開發人員也能成功使用 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="75919-107">You don't have to be a developer to be successful with PowerShell.</span></span> <span data-ttu-id="75919-108">您無需對這些術語望之卻步。</span><span class="sxs-lookup"><span data-stu-id="75919-108">Don't get bogged down in the terminology.</span></span> <span data-ttu-id="75919-109">一開始或許一頭霧水，但在經過實際操作後，您就會開始在某些時候突然領悟。</span><span class="sxs-lookup"><span data-stu-id="75919-109">Not everything may make sense initially, but after a little hands-on experience you'll start to have those "light bulb" moments.</span></span> <span data-ttu-id="75919-110">「原來如此！</span><span class="sxs-lookup"><span data-stu-id="75919-110">"Aha!</span></span> <span data-ttu-id="75919-111">這本書談的就是這個。」</span><span class="sxs-lookup"><span data-stu-id="75919-111">So that's what the book was talking about."</span></span>

<span data-ttu-id="75919-112">請務必在電腦上嘗試操作這些範例，就能獲得實際的體驗。</span><span class="sxs-lookup"><span data-stu-id="75919-112">Be sure to try the examples on your computer to gain some of that hands-on experience.</span></span>

## <a name="requirements"></a><span data-ttu-id="75919-113">需求</span><span class="sxs-lookup"><span data-stu-id="75919-113">Requirements</span></span>

<span data-ttu-id="75919-114">本章所示的部分範例需要 Active Directory PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="75919-114">The Active Directory PowerShell module is required by some of the examples shown in this chapter.</span></span>
<span data-ttu-id="75919-115">此模組是適用於 Windows 的遠端伺服器管理工具 (RSAT) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="75919-115">The module is part of the Remote Server Administration Tools (RSAT) for Windows.</span></span> <span data-ttu-id="75919-116">若為組建版本 1809 (或更高) 的 Windows，RSAT 工具須安裝為 Windows 功能。</span><span class="sxs-lookup"><span data-stu-id="75919-116">For the 1809 (or higher) build of Windows, the RSAT tools are installed as a Windows feature.</span></span>

- <span data-ttu-id="75919-117">如需安裝 RSAT 工具的詳細資訊，請參閱 [Windows 管理模組][]。</span><span class="sxs-lookup"><span data-stu-id="75919-117">For information about installing the RSAT tools, see [Windows Management modules][].</span></span>
- <span data-ttu-id="75919-118">若為舊版的 Windows，請參閱[適用於 Windows 的 RSAT][]。</span><span class="sxs-lookup"><span data-stu-id="75919-118">For older versions of Windows, see [RSAT for Windows][].</span></span>

## <a name="get-member"></a><span data-ttu-id="75919-119">Get-Member</span><span class="sxs-lookup"><span data-stu-id="75919-119">Get-Member</span></span>

<span data-ttu-id="75919-120">`Get-Member` 協助您探索可用於命令的物件、屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="75919-120">`Get-Member` helps you discover what objects, properties, and methods are available for commands.</span></span>
<span data-ttu-id="75919-121">任何產生以物件為基礎之輸出的命令，都可以透過管道傳送至 `Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="75919-121">Any command that produces object-based output can be piped to `Get-Member`.</span></span> <span data-ttu-id="75919-122">「屬性」是關於項目的特性。</span><span class="sxs-lookup"><span data-stu-id="75919-122">A property is a characteristic about an item.</span></span> <span data-ttu-id="75919-123">您的駕照上有一個名為「眼睛顏色」的屬性，而該屬性最常見的值為藍色和棕色。</span><span class="sxs-lookup"><span data-stu-id="75919-123">Your drivers license has a property called eye color and the most common values for that property are blue and brown.</span></span> <span data-ttu-id="75919-124">「方法」是可以對項目採取的動作。</span><span class="sxs-lookup"><span data-stu-id="75919-124">A method is an action that can be taken on an item.</span></span> <span data-ttu-id="75919-125">以駕照為例，方法之一就是「撤銷」，因為監理處可以撤銷您的駕照。</span><span class="sxs-lookup"><span data-stu-id="75919-125">In staying with the drivers license example, one of the methods is "Revoke" because the department of motor vehicles can revoke your drivers license.</span></span>

### <a name="properties"></a><span data-ttu-id="75919-126">屬性</span><span class="sxs-lookup"><span data-stu-id="75919-126">Properties</span></span>

<span data-ttu-id="75919-127">在下列範例中，我將擷取電腦上執行 Windows 時間服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="75919-127">In the following example, I'll retrieve information about the Windows Time service running on my computer.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="75919-128">如同上一組結果所示，就是以 **Status**、**Name** 和 **DisplayName** 等屬性為例。</span><span class="sxs-lookup"><span data-stu-id="75919-128">**Status**, **Name**, and **DisplayName** are examples of properties as shown in the previous set of results.</span></span> <span data-ttu-id="75919-129">**Status** 屬性的值為 `Running`，**Name** 屬性的值為 `w32time`，而 **DisplayName** 的值為 `Windows Time`。</span><span class="sxs-lookup"><span data-stu-id="75919-129">The value for the **Status** property is `Running`, the value for the **Name** property is `w32time`, and the value for **DisplayName** is `Windows Time`.</span></span>

<span data-ttu-id="75919-130">接下來我要用管道傳送相同的命令給 `Get-Member`：</span><span class="sxs-lookup"><span data-stu-id="75919-130">Now I'll pipe that same command to `Get-Member`:</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="75919-131">上一個範例中結果的第一行包含一則非常重要的資訊。</span><span class="sxs-lookup"><span data-stu-id="75919-131">The first line of the results in the previous example contains one piece of very important information.</span></span> <span data-ttu-id="75919-132">**TypeName** 會告訴您傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="75919-132">**TypeName** tells you what type of object was returned.</span></span> <span data-ttu-id="75919-133">在此範例中，傳回了 **System.serviceprocess.dll. ServiceController** 物件。</span><span class="sxs-lookup"><span data-stu-id="75919-133">In this example, a **System.ServiceProcess.ServiceController** object was returned.</span></span> <span data-ttu-id="75919-134">這通常縮寫為 **TypeName** 最後一個句點後面的部分；亦即本範例中的 **ServiceController**。</span><span class="sxs-lookup"><span data-stu-id="75919-134">This is often abbreviated as the portion of the **TypeName** just after the last period; **ServiceController** in this example.</span></span>

<span data-ttu-id="75919-135">在瞭解命令所產生的物件類型後，您就可以使用這項資訊來尋找接受該物件類型做為輸入的命令。</span><span class="sxs-lookup"><span data-stu-id="75919-135">Once you know what type of object a command produces, you can use this information to find commands that accept that type of object as input.</span></span>

```powershell
Get-Command -ParameterType ServiceController
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
```

<span data-ttu-id="75919-136">所有這些命令都有參數，可透過管道、參數輸入或兩者來接受 **ServiceController** 物件類型。</span><span class="sxs-lookup"><span data-stu-id="75919-136">All of those commands have a parameter that accepts a **ServiceController** object type by pipeline, parameter input, or both.</span></span>

<span data-ttu-id="75919-137">請注意，屬性數量會比預設顯示多。</span><span class="sxs-lookup"><span data-stu-id="75919-137">Notice that there are more properties than are displayed by default.</span></span> <span data-ttu-id="75919-138">雖然依預設不會顯示其他這些屬性，但您可以從管道中選取，方法是透過管道將命令傳送至 `Select-Object` Cmdlet，並使用 **Property** 參數。</span><span class="sxs-lookup"><span data-stu-id="75919-138">Although these additional properties aren't displayed by default, they can be selected from the pipeline by piping the command to the `Select-Object` cmdlet and using the **Property** parameter.</span></span> <span data-ttu-id="75919-139">下列範例會藉由將 `Get-Service` 的結果傳送至 `Select-Object`，並將 `*` 萬用字元指定為 **Property** 參數的值，來選取所有屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-139">The following example selects all of the properties by piping the results of `Get-Service` to `Select-Object` and specifying the `*` wildcard character as the value for the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="75919-140">您也可以使用以逗號分隔的清單，選取特定屬性，作為 **Property** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="75919-140">Specific properties can also be selected using a comma-separated list for the value of the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

<span data-ttu-id="75919-141">根據預設，資料表中會傳回四個屬性，並在清單中傳回五或更多個屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-141">By default, four properties are returned in a table and five or more are returned in a list.</span></span> <span data-ttu-id="75919-142">有些命令會使用自訂格式來覆寫資料表中預設顯示的屬性數量。</span><span class="sxs-lookup"><span data-stu-id="75919-142">Some commands use custom formatting to override how many properties are displayed by default in a table.</span></span>
<span data-ttu-id="75919-143">有幾個 `Format-*` Cmdlet 可以用來手動覆寫這些預設值。</span><span class="sxs-lookup"><span data-stu-id="75919-143">There are several `Format-*` cmdlets that can be used to manually override these defaults.</span></span> <span data-ttu-id="75919-144">我們將在下一章中討論最常見的 `Format-Table` 和 `Format-List`。</span><span class="sxs-lookup"><span data-stu-id="75919-144">The most common ones are `Format-Table` and `Format-List`, both of which will be covered in an upcoming chapter.</span></span>

<span data-ttu-id="75919-145">以 `Select-Object` 指定屬性名稱時，可以使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="75919-145">Wildcard characters can be used when specifying the property names with `Select-Object`.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```powershell
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="75919-146">在上一個範例中，我們使用 `Can*` 作為 **Property** 參數的一個值，來傳回以 `Can` 開頭的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-146">In the previous example, `Can*` was used as one of the values for the **Property** parameter to return all the properties that start with `Can`.</span></span> <span data-ttu-id="75919-147">其中包括 **CanPauseAndContinue**、**CanShutdown** 和 **CanStop**。</span><span class="sxs-lookup"><span data-stu-id="75919-147">These include **CanPauseAndContinue**, **CanShutdown**, and **CanStop**.</span></span>

### <a name="methods"></a><span data-ttu-id="75919-148">方法</span><span class="sxs-lookup"><span data-stu-id="75919-148">Methods</span></span>

<span data-ttu-id="75919-149">方法是指可以採取的動作。</span><span class="sxs-lookup"><span data-stu-id="75919-149">Methods are an action that can be taken.</span></span> <span data-ttu-id="75919-150">使用 **MemberType** 參數，將 `Get-Member` 的結果縮小為只顯示 `Get-Service` 的方法。</span><span class="sxs-lookup"><span data-stu-id="75919-150">Use the **MemberType** parameter to narrow down the results of `Get-Member` to only show the methods for `Get-Service`.</span></span>

```powershell
Get-Service -Name w32time | Get-Member -MemberType Method
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType Definition
----                      ---------- ----------
Close                     Method     void Close()
Continue                  Method     void Continue()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type ...
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
ExecuteCommand            Method     void ExecuteCommand(int command)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Pause                     Method     void Pause()
Refresh                   Method     void Refresh()
Start                     Method     void Start(), void Start(string[] args)
Stop                      Method     void Stop()
WaitForStatus             Method     void WaitForStatus(System.ServiceProcess.ServiceC...
```

<span data-ttu-id="75919-151">如您所見，有許多方法。</span><span class="sxs-lookup"><span data-stu-id="75919-151">As you can see, there are many methods.</span></span> <span data-ttu-id="75919-152">**Stop** 方法可以用來停止 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="75919-152">The **Stop** method can be used to stop a Windows service.</span></span>

```powershell
(Get-Service -Name w32time).Stop()
```

<span data-ttu-id="75919-153">現在確認 Windows 時間服務確實已停止。</span><span class="sxs-lookup"><span data-stu-id="75919-153">Now to verify the Windows time service has indeed been stopped.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

<span data-ttu-id="75919-154">我很少會使用方法，但是仍需要加以注意。</span><span class="sxs-lookup"><span data-stu-id="75919-154">I rarely find myself using methods, but they're something you need to be aware of.</span></span> <span data-ttu-id="75919-155">有時候，您會遇到 `Get-*` 命令，但沒有對應的命令來修改該項目。</span><span class="sxs-lookup"><span data-stu-id="75919-155">There are times that you'll come across a `Get-*` command without a corresponding command to modify that item.</span></span>
<span data-ttu-id="75919-156">通常可使用某種方法執行修改的動作。</span><span class="sxs-lookup"><span data-stu-id="75919-156">Often, a method can be used to perform an action that modifies it.</span></span> <span data-ttu-id="75919-157">SqlServer PowerShell 模組中的 `Get-SqlAgentJob` Cmdlet 就是這種情形的絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="75919-157">The `Get-SqlAgentJob` cmdlet in the SqlServer PowerShell module is a good example of this.</span></span> <span data-ttu-id="75919-158">模組可作為 [SQL Server Management Studio (SMSS)][SMSS] 的一部分來安裝。</span><span class="sxs-lookup"><span data-stu-id="75919-158">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="75919-159">沒有對應的 `Set-*` Cmdlet，但可以使用某種方法來完成相同的工作。</span><span class="sxs-lookup"><span data-stu-id="75919-159">No corresponding `Set-*` cmdlet exists, but a method can be used to complete the same task.</span></span>

<span data-ttu-id="75919-160">另一個要注意方法的原因是，許多新手都認為 `Get-*` 命令不可能造成破壞性變更。</span><span class="sxs-lookup"><span data-stu-id="75919-160">Another reason to be aware of methods is that many beginners assume destructive changes can't be made with `Get-*` commands.</span></span> <span data-ttu-id="75919-161">但如果不當使用，確實會造成嚴重的問題。</span><span class="sxs-lookup"><span data-stu-id="75919-161">But they indeed can cause serious problems if used inappropriately.</span></span>

<span data-ttu-id="75919-162">建議可以選擇使用 Cmdlet 來執行動作 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="75919-162">A better option is to use a cmdlet to perform the action if one exists.</span></span> <span data-ttu-id="75919-163">請繼續操作並啟動 Windows 時間服務，但這次使用 Cmdlet 來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="75919-163">Go ahead and start the Windows Time service, except this time use the cmdlet for starting services.</span></span>

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="75919-164">根據預設，`Start-Service` 不會傳回任何結果，就像 `Get-Service` 的啟動方法一樣。</span><span class="sxs-lookup"><span data-stu-id="75919-164">By default, `Start-Service` doesn't return any results just like the start method of `Get-Service`.</span></span>
<span data-ttu-id="75919-165">但是使用 Cmdlet 的優點之一是，許多時候 Cmdlet 可提供方法所無法提供的其他功能。</span><span class="sxs-lookup"><span data-stu-id="75919-165">But one of the benefits of using a cmdlet is that many times the cmdlet offers additional functionality that isn't available with a method.</span></span> <span data-ttu-id="75919-166">在上述範例中，使用了 **PassThru** 參數。</span><span class="sxs-lookup"><span data-stu-id="75919-166">In the previous example, the **PassThru** parameter was used.</span></span> <span data-ttu-id="75919-167">這會導致 Cmdlet 產生輸出 (通常不會)。</span><span class="sxs-lookup"><span data-stu-id="75919-167">This causes a cmdlet that doesn't normally produce output, to produce output.</span></span>

<span data-ttu-id="75919-168">請注意關於 Cmdlet 輸出的假設。</span><span class="sxs-lookup"><span data-stu-id="75919-168">Be careful with assumptions about the output of a cmdlet.</span></span> <span data-ttu-id="75919-169">我們都知道當您假設時，會導致什麼後果。</span><span class="sxs-lookup"><span data-stu-id="75919-169">We all know what happens when you assume things.</span></span> <span data-ttu-id="75919-170">我將擷取在 Windows 10 實驗室環境電腦上執行之 PowerShell 程序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="75919-170">I'll retrieve information about the PowerShell process running on my Windows 10 lab environment computer.</span></span>

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

<span data-ttu-id="75919-171">接下來我要透過管道將相同的命令傳送給 Get-Member：</span><span class="sxs-lookup"><span data-stu-id="75919-171">Now I'll pipe that same command to Get-Member:</span></span>

```powershell
Get-Process -Name PowerShell | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
```

<span data-ttu-id="75919-172">請注意，列出的屬性數量會比預設顯示多。</span><span class="sxs-lookup"><span data-stu-id="75919-172">Notice that there are more properties listed than are displayed by default.</span></span> <span data-ttu-id="75919-173">當觀看 `Get-Member` 的結果時，一些預設屬性不會顯示為屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-173">A number of the default properties displayed don't show up as properties when viewing the results of `Get-Member`.</span></span> <span data-ttu-id="75919-174">這是因為許多顯示的值 (例如 `NPM(K)`、`PM(K)`、`WS(K)` 和 `CPU(s)`) 都是計算的屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-174">This is because many of the displayed values, such as `NPM(K)`, `PM(K)`, `WS(K)`, and `CPU(s)`, are calculated properties.</span></span> <span data-ttu-id="75919-175">若要判斷實際的屬性名稱，必須透過管道將命令傳送至 `Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="75919-175">To determine the actual property names, the command must be piped to `Get-Member`.</span></span>

<span data-ttu-id="75919-176">如果命令不會產生輸出，則無法透過管道將命令傳送至 `Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="75919-176">If a command does not produce output, it can't be piped to `Get-Member`.</span></span> <span data-ttu-id="75919-177">由於 `Start-Service` 預設不會產生任何輸出，因此當您嘗試透過管道將其傳送至 `Get-Member` 時，就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="75919-177">Since `Start-Service` doesn't produce any output by default, it generates an error when you try to pipe it to `Get-Member`.</span></span>

```powershell
Start-Service -Name w32time | Get-Member
```

```Output
Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:31
+ Start-Service -Name w32time | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMembe
   rCommand
```

<span data-ttu-id="75919-178">您可以使用 `Start-Service` Cmdlet 來指定 **PassThru** 參數，使其產生輸出，即可透過管道將其傳送至 `Get-Member` 而不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="75919-178">The **PassThru** parameter can be specified with the `Start-Service` cmdlet make it produce output, which is then piped to `Get-Member` without error.</span></span>

```powershell
Start-Service -Name w32time -PassThru | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="75919-179">若要透過管道將其傳送至 `Get-Member`，命令必須產生以物件為基礎的輸出。</span><span class="sxs-lookup"><span data-stu-id="75919-179">To be piped to `Get-Member`, a command must produce object-based output.</span></span>

```powershell
Get-Service -Name w32time | Out-Host | Get-Member
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time

Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:40
+ Get-Service -Name w32time | Out-Host | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMemberCommand
```

<span data-ttu-id="75919-180">`Out-Host` 直接寫入 PowerShell 主機，但不會為管道產生以物件為基礎的輸出。</span><span class="sxs-lookup"><span data-stu-id="75919-180">`Out-Host` writes directly to the PowerShell host, but it doesn't produce object-based output for the pipeline.</span></span> <span data-ttu-id="75919-181">因此無法透過管道將其傳送至 `Get-Member`。</span><span class="sxs-lookup"><span data-stu-id="75919-181">So it can't be piped to `Get-Member`.</span></span>

## <a name="active-directory"></a><span data-ttu-id="75919-182">Active Directory</span><span class="sxs-lookup"><span data-stu-id="75919-182">Active Directory</span></span>

> [!NOTE]
> <span data-ttu-id="75919-183">您需要本章「需求」一節中所列的「遠端伺服器管理工具」才能完成本節課程。</span><span class="sxs-lookup"><span data-stu-id="75919-183">The Remote Server Administration Tools listed in the requirements section of this chapter are required to complete this section.</span></span> <span data-ttu-id="75919-184">此外，如本書簡介中所述，您的 Windows 10 實驗室環境電腦必須是實驗室環境網域的成員。</span><span class="sxs-lookup"><span data-stu-id="75919-184">Also, as mentioned in the introduction to this book, your Windows 10 lab environment computer must be a member of the lab environment domain.</span></span>

<span data-ttu-id="75919-185">搭配使用 `Get-Command` 和 **Module** 參數，以判斷在安裝遠端伺服器管理工具時，新增作為 ActiveDirectory PowerShell 模組一部分的命令。</span><span class="sxs-lookup"><span data-stu-id="75919-185">Use `Get-Command` with the **Module** parameter to determine what commands were added as part of the ActiveDirectory PowerShell module when the remote server administration tools were installed.</span></span>

```powershell
Get-Command -Module ActiveDirectory
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Add-ADCentralAccessPolicyMember                    1.0.0.0    ActiveDi...
Cmdlet          Add-ADComputerServiceAccount                       1.0.0.0    ActiveDi...
Cmdlet          Add-ADDomainControllerPasswordReplicationPolicy    1.0.0.0    ActiveDi...
Cmdlet          Add-ADFineGrainedPasswordPolicySubject             1.0.0.0    ActiveDi...
Cmdlet          Add-ADGroupMember                                  1.0.0.0    ActiveDi...
Cmdlet          Add-ADPrincipalGroupMembership                     1.0.0.0    ActiveDi...
Cmdlet          Add-ADResourcePropertyListMember                   1.0.0.0    ActiveDi...
Cmdlet          Clear-ADAccountExpiration                          1.0.0.0    ActiveDi...
Cmdlet          Clear-ADClaimTransformLink                         1.0.0.0    ActiveDi...
Cmdlet          Disable-ADAccount                                  1.0.0.0    ActiveDi...
...
```

<span data-ttu-id="75919-186">在 ActiveDirectory PowerShell 模組中，總共新增了147 個命令。</span><span class="sxs-lookup"><span data-stu-id="75919-186">A total of 147 commands were added as part of the ActiveDirectory PowerShell module.</span></span> <span data-ttu-id="75919-187">根據預設，其中的某些命令只會傳回部分可用屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-187">Some commands of these commands only return a portion of the available properties by default.</span></span>

<span data-ttu-id="75919-188">您是否注意到此模組中的命令名稱有何不同？</span><span class="sxs-lookup"><span data-stu-id="75919-188">Did you notice anything different about the names of the commands in this module?</span></span> <span data-ttu-id="75919-189">命令的名詞部分具有 AD 字首。</span><span class="sxs-lookup"><span data-stu-id="75919-189">The noun portion of the commands has an AD prefix.</span></span> <span data-ttu-id="75919-190">這在大部分模組的命令上很常見。</span><span class="sxs-lookup"><span data-stu-id="75919-190">This is common to see on the commands of most modules.</span></span> <span data-ttu-id="75919-191">字首的設計是為了防止命名衝突。</span><span class="sxs-lookup"><span data-stu-id="75919-191">The prefix is designed to help prevent naming conflicts.</span></span>

```powershell
Get-ADUser -Identity mike | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name              MemberType            Definition
----              ----------            ----------
Contains          Method                bool Contains(string propertyName)
Equals            Method                bool Equals(System.Object obj)
GetEnumerator     Method                System.Collections.IDictionaryEnumerator GetEn...
GetHashCode       Method                int GetHashCode()
GetType           Method                type GetType()
ToString          Method                string ToString()
Item              ParameterizedProperty Microsoft.ActiveDirectory.Management.ADPropert...
DistinguishedName Property              System.String DistinguishedName {get;set;}
Enabled           Property              System.Boolean Enabled {get;set;}
GivenName         Property              System.String GivenName {get;set;}
Name              Property              System.String Name {get;}
ObjectClass       Property              System.String ObjectClass {get;set;}
ObjectGUID        Property              System.Nullable`1[[System.Guid, mscorlib, Vers...
SamAccountName    Property              System.String SamAccountName {get;set;}
SID               Property              System.Security.Principal.SecurityIdentifier S...
Surname           Property              System.String Surname {get;set;}
UserPrincipalName Property              System.String UserPrincipalName {get;set;}
```

<span data-ttu-id="75919-192">即使您不太熟悉 Active Directory，您可能也知道使用者帳戶的屬性數量比此範例中顯示的還要多。</span><span class="sxs-lookup"><span data-stu-id="75919-192">Even if you're only vaguely familiar with Active Directory, you're probably aware that a user account has more properties than are shown in this example.</span></span>

<span data-ttu-id="75919-193">`Get-ADUser` Cmdlet 具有 **Properties** 參數，可用來指定您想要傳回的其他（非預設）屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-193">The `Get-ADUser` cmdlet has a **Properties** parameter that is used to specify the additional (non-default) properties you want to return.</span></span> <span data-ttu-id="75919-194">指定 `*` 萬用字元可傳回所有這些屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-194">Specifying the `*` wildcard character returns all of them.</span></span>

```powershell
Get-ADUser -Identity mike -Properties * | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name                                 MemberType            Definition
----                                 ----------            ----------
Contains                             Method                bool Contains(string proper...
Equals                               Method                bool Equals(System.Object obj)
GetEnumerator                        Method                System.Collections.IDiction...
GetHashCode                          Method                int GetHashCode()
GetType                              Method                type GetType()
ToString                             Method                string ToString()
Item                                 ParameterizedProperty Microsoft.ActiveDirectory.M...
AccountExpirationDate                Property              System.DateTime AccountExpi...
accountExpires                       Property              System.Int64 accountExpires...
AccountLockoutTime                   Property              System.DateTime AccountLock...
AccountNotDelegated                  Property              System.Boolean AccountNotDe...
AllowReversiblePasswordEncryption    Property              System.Boolean AllowReversi...
AuthenticationPolicy                 Property              Microsoft.ActiveDirectory.M...
AuthenticationPolicySilo             Property              Microsoft.ActiveDirectory.M...
BadLogonCount                        Property              System.Int32 BadLogonCount ...
badPasswordTime                      Property              System.Int64 badPasswordTim...
badPwdCount                          Property              System.Int32 badPwdCount {g...
CannotChangePassword                 Property              System.Boolean CannotChange...
CanonicalName                        Property              System.String CanonicalName...
Certificates                         Property              Microsoft.ActiveDirectory.M...
City                                 Property              System.String City {get;set;}
CN                                   Property              System.String CN {get;}
codePage                             Property              System.Int32 codePage {get;...
Company                              Property              System.String Company {get;...
CompoundIdentitySupported            Property              Microsoft.ActiveDirectory.M...
Country                              Property              System.String Country {get;...
countryCode                          Property              System.Int32 countryCode {g...
Created                              Property              System.DateTime Created {get;}
createTimeStamp                      Property              System.DateTime createTimeS...
Deleted                              Property              System.Boolean Deleted {get;}
Department                           Property              System.String Department {g...
Description                          Property              System.String Description {...
DisplayName                          Property              System.String DisplayName {...
DistinguishedName                    Property              System.String Distinguished...
Division                             Property              System.String Division {get...
DoesNotRequirePreAuth                Property              System.Boolean DoesNotRequi...
dSCorePropagationData                Property              Microsoft.ActiveDirectory.M...
EmailAddress                         Property              System.String EmailAddress ...
EmployeeID                           Property              System.String EmployeeID {g...
EmployeeNumber                       Property              System.String EmployeeNumbe...
Enabled                              Property              System.Boolean Enabled {get...
Fax                                  Property              System.String Fax {get;set;}
GivenName                            Property              System.String GivenName {ge...
HomeDirectory                        Property              System.String HomeDirectory...
HomedirRequired                      Property              System.Boolean HomedirRequi...
HomeDrive                            Property              System.String HomeDrive {ge...
HomePage                             Property              System.String HomePage {get...
HomePhone                            Property              System.String HomePhone {ge...
Initials                             Property              System.String Initials {get...
instanceType                         Property              System.Int32 instanceType {...
isDeleted                            Property              System.Boolean isDeleted {g...
KerberosEncryptionType               Property              Microsoft.ActiveDirectory.M...
LastBadPasswordAttempt               Property              System.DateTime LastBadPass...
LastKnownParent                      Property              System.String LastKnownPare...
lastLogoff                           Property              System.Int64 lastLogoff {ge...
lastLogon                            Property              System.Int64 lastLogon {get...
LastLogonDate                        Property              System.DateTime LastLogonDa...
lastLogonTimestamp                   Property              System.Int64 lastLogonTimes...
LockedOut                            Property              System.Boolean LockedOut {g...
logonCount                           Property              System.Int32 logonCount {ge...
LogonWorkstations                    Property              System.String LogonWorkstat...
Manager                              Property              System.String Manager {get;...
MemberOf                             Property              Microsoft.ActiveDirectory.M...
MNSLogonAccount                      Property              System.Boolean MNSLogonAcco...
MobilePhone                          Property              System.String MobilePhone {...
Modified                             Property              System.DateTime Modified {g...
modifyTimeStamp                      Property              System.DateTime modifyTimeS...
msDS-User-Account-Control-Computed   Property              System.Int32 msDS-User-Acco...
Name                                 Property              System.String Name {get;}
nTSecurityDescriptor                 Property              System.DirectoryServices.Ac...
ObjectCategory                       Property              System.String ObjectCategor...
ObjectClass                          Property              System.String ObjectClass {...
ObjectGUID                           Property              System.Nullable`1[[System.G...
objectSid                            Property              System.Security.Principal.S...
Office                               Property              System.String Office {get;s...
OfficePhone                          Property              System.String OfficePhone {...
Organization                         Property              System.String Organization ...
OtherName                            Property              System.String OtherName {ge...
PasswordExpired                      Property              System.Boolean PasswordExpi...
PasswordLastSet                      Property              System.DateTime PasswordLas...
PasswordNeverExpires                 Property              System.Boolean PasswordNeve...
PasswordNotRequired                  Property              System.Boolean PasswordNotR...
POBox                                Property              System.String POBox {get;set;}
PostalCode                           Property              System.String PostalCode {g...
PrimaryGroup                         Property              System.String PrimaryGroup ...
primaryGroupID                       Property              System.Int32 primaryGroupID...
PrincipalsAllowedToDelegateToAccount Property              Microsoft.ActiveDirectory.M...
ProfilePath                          Property              System.String ProfilePath {...
ProtectedFromAccidentalDeletion      Property              System.Boolean ProtectedFro...
pwdAnswer                            Property              System.String pwdAnswer {ge...
pwdLastSet                           Property              System.Int64 pwdLastSet {ge...
pwdQuestion                          Property              System.String pwdQuestion {...
SamAccountName                       Property              System.String SamAccountNam...
sAMAccountType                       Property              System.Int32 sAMAccountType...
ScriptPath                           Property              System.String ScriptPath {g...
sDRightsEffective                    Property              System.Int32 sDRightsEffect...
ServicePrincipalNames                Property              Microsoft.ActiveDirectory.M...
SID                                  Property              System.Security.Principal.S...
SIDHistory                           Property              Microsoft.ActiveDirectory.M...
SmartcardLogonRequired               Property              System.Boolean SmartcardLog...
sn                                   Property              System.String sn {get;set;}
State                                Property              System.String State {get;set;}
StreetAddress                        Property              System.String StreetAddress...
Surname                              Property              System.String Surname {get;...
Title                                Property              System.String Title {get;set;}
TrustedForDelegation                 Property              System.Boolean TrustedForDe...
TrustedToAuthForDelegation           Property              System.Boolean TrustedToAut...
UseDESKeyOnly                        Property              System.Boolean UseDESKeyOnl...
userAccountControl                   Property              System.Int32 userAccountCon...
userCertificate                      Property              Microsoft.ActiveDirectory.M...
UserPrincipalName                    Property              System.String UserPrincipal...
uSNChanged                           Property              System.Int64 uSNChanged {get;}
uSNCreated                           Property              System.Int64 uSNCreated {get;}
whenChanged                          Property              System.DateTime whenChanged...
whenCreated                          Property              System.DateTime whenCreated...
```

<span data-ttu-id="75919-195">現在看起來更像了。</span><span class="sxs-lookup"><span data-stu-id="75919-195">Now that looks more like it.</span></span>

<span data-ttu-id="75919-196">您認為為什麼要預設限制 Active Directory 使用者帳戶的屬性？</span><span class="sxs-lookup"><span data-stu-id="75919-196">Can you think of a reason why the properties of an Active Directory user account would be so limited by default?</span></span> <span data-ttu-id="75919-197">假設您要在生產 Active Directory 環境中為每個使用者帳戶傳回所有屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-197">Imagine if you returned every property for every user account in your production Active Directory environment.</span></span> <span data-ttu-id="75919-198">請考慮您可能會造成網域控制站本身以及您網路的效能降低。</span><span class="sxs-lookup"><span data-stu-id="75919-198">Think of the performance degradation that you could cause, not only to the domain controllers themselves, but also to your network.</span></span> <span data-ttu-id="75919-199">無論如何，這都會讓人懷疑您是否真的需要所有屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-199">It's doubtful that you'll actually need every property anyway.</span></span> <span data-ttu-id="75919-200">如果是要判斷存在哪些屬性，可接受的作法是傳回單一使用者帳戶的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-200">Returning all of the properties for a single user account is perfectly acceptable when you're trying to determine what properties exist.</span></span>

<span data-ttu-id="75919-201">在建立原型時多次執行某個命令，這並非罕見的情況。</span><span class="sxs-lookup"><span data-stu-id="75919-201">It's not uncommon to run a command many times when prototyping it.</span></span> <span data-ttu-id="75919-202">如果您要執行龐大的查詢，請查詢一次，然後將結果儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="75919-202">If you're going to perform some huge query, query it once and store the results in a variable.</span></span> <span data-ttu-id="75919-203">然後使用變數的內容，而不要重複使用一些昂貴的查詢。</span><span class="sxs-lookup"><span data-stu-id="75919-203">Then work with the contents of the variable instead of repeatedly using some expensive query.</span></span>

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

<span data-ttu-id="75919-204">使用 `$Users` 變數的內容，而不是執行前述命令多次。</span><span class="sxs-lookup"><span data-stu-id="75919-204">Use the contents of the `$Users` variable instead of running the previous command numerous times.</span></span>
<span data-ttu-id="75919-205">請記住，在 Active Directory 中對該使用者進行變更時，不會更新變數的內容。</span><span class="sxs-lookup"><span data-stu-id="75919-205">Keep in mind that the contents of the variable aren't updated when changes are made to that user in Active Directory.</span></span>

<span data-ttu-id="75919-206">您可以透過管道將 `$Users` 變數傳送至 `Get-Member`，以探索可用的屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-206">You could pipe the `$Users` variable to `Get-Member` to discover the available properties.</span></span>

```powershell
$Users | Get-Member
```

<span data-ttu-id="75919-207">然後，藉由將 `$Users` 透過管道傳送至 `Select-Object` 來選取個別的屬性 ，而不需要多次查詢 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="75919-207">Then select the individual properties by piping `$Users` to `Select-Object`, all without ever having to query Active Directory more than one time.</span></span>

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

<span data-ttu-id="75919-208">如果您要多次查詢 Active Directory，請使用 **Properties** 參數來指定所需的任何非預設屬性。</span><span class="sxs-lookup"><span data-stu-id="75919-208">If you are going to query Active Directory more than once, use the **Properties** parameter to specify any non-default properties you want.</span></span>

```powershell
Get-ADUser -Identity mike -Properties LastLogonDate, LastBadPasswordAttempt
```

```Output
DistinguishedName      : CN=Mike F. Robbins,OU=Sales,DC=mikefrobbins,DC=com
Enabled                : True
GivenName              : Mike
LastBadPasswordAttempt : 2/4/2017 10:46:15 AM
LastLogonDate          : 2/18/2017 12:45:14 AM
Name                   : Mike F. Robbins
ObjectClass            : user
ObjectGUID             : a82a8c58-1332-4a57-a6e2-68e0c750ea56
SamAccountName         : mike
SID                    : S-1-5-21-2989741381-570885089-3319121794-1108
Surname                : Robbins
UserPrincipalName      : miker@mikefrobbins.com
```

## <a name="summary"></a><span data-ttu-id="75919-209">摘要</span><span class="sxs-lookup"><span data-stu-id="75919-209">Summary</span></span>

<span data-ttu-id="75919-210">在本章中，您已瞭解如何判斷命令所產生的物件類型、如何判斷命令所能使用的屬性和方法，以及如何使用依預設限制傳回屬性的命令。</span><span class="sxs-lookup"><span data-stu-id="75919-210">In this chapter, you've learned how to determine what type of object a command produces, how to determine what properties and methods are available for a command, and how to work with commands that limit the properties that are returned by default.</span></span>

## <a name="review"></a><span data-ttu-id="75919-211">檢閱</span><span class="sxs-lookup"><span data-stu-id="75919-211">Review</span></span>

1. <span data-ttu-id="75919-212">`Get-Process` Cmdlet 會產生哪種類型的物件？</span><span class="sxs-lookup"><span data-stu-id="75919-212">What type of object does the `Get-Process` cmdlet produce?</span></span>
1. <span data-ttu-id="75919-213">如何判斷命令的可用屬性為何？</span><span class="sxs-lookup"><span data-stu-id="75919-213">How do you determine what the available properties are for a command?</span></span>
1. <span data-ttu-id="75919-214">如果存在可以用來取得但無法設定的某個命令，您應該檢查哪些內容？</span><span class="sxs-lookup"><span data-stu-id="75919-214">If a command exists for getting something but not for setting the same thing, what should you check for?</span></span>
1. <span data-ttu-id="75919-215">如何讓預設不會產生輸出的特定命令產生輸出？</span><span class="sxs-lookup"><span data-stu-id="75919-215">How can certain commands that don't produce output by default be made to produce output?</span></span>
1. <span data-ttu-id="75919-216">如果您要使用會產生大量輸出的命令結果，您應該考慮怎麼做？</span><span class="sxs-lookup"><span data-stu-id="75919-216">If you're going to be working with the results of a command that produces an enormous amount of output, what should you consider doing?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="75919-217">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="75919-217">Recommended Reading</span></span>

- <span data-ttu-id="75919-218">[Get-Member][]</span><span class="sxs-lookup"><span data-stu-id="75919-218">[Get-Member][]</span></span>
- <span data-ttu-id="75919-219">[檢視物件結構 (Get-Member)][]</span><span class="sxs-lookup"><span data-stu-id="75919-219">[Viewing Object Structure (Get-Member)][]</span></span>
- <span data-ttu-id="75919-220">[about_Objects][]</span><span class="sxs-lookup"><span data-stu-id="75919-220">[about_Objects][]</span></span>
- <span data-ttu-id="75919-221">[about_Properties][]</span><span class="sxs-lookup"><span data-stu-id="75919-221">[about_Properties][]</span></span>
- <span data-ttu-id="75919-222">[about_Methods][]</span><span class="sxs-lookup"><span data-stu-id="75919-222">[about_Methods][]</span></span>
- <span data-ttu-id="75919-223">[沒有可啟動或停止某個內容的 PowerShell Cmdlet？別忘了查看在 Get Cmdlet 上的方法][use-methods]</span><span class="sxs-lookup"><span data-stu-id="75919-223">[No PowerShell Cmdlet to Start or Stop Something? Don’t Forget to Check for Methods on the Get Cmdlets][use-methods]</span></span>

<!-- link references -->
[適用於 Windows 的 RSAT]: https://support.microsoft.com/help/2693643
[RSAT for Windows]: https://support.microsoft.com/help/2693643
[Windows 管理模組]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Windows Management modules]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Get-Member]: /powershell/module/microsoft.powershell.utility/get-member
[檢視物件結構 (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[Viewing Object Structure (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
