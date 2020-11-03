---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203564"
---
# <span data-ttu-id="b617d-103">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="b617d-103">Remove-EventLog</span></span>

## <span data-ttu-id="b617d-104">概要</span><span class="sxs-lookup"><span data-stu-id="b617d-104">SYNOPSIS</span></span>
<span data-ttu-id="b617d-105">刪除事件記錄檔或取消註冊事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-105">Deletes an event log or unregisters an event source.</span></span>

## <span data-ttu-id="b617d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b617d-106">SYNTAX</span></span>

### <span data-ttu-id="b617d-107">Default (預設值)</span><span class="sxs-lookup"><span data-stu-id="b617d-107">Default (Default)</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b617d-108">來源</span><span class="sxs-lookup"><span data-stu-id="b617d-108">Source</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b617d-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b617d-109">DESCRIPTION</span></span>
<span data-ttu-id="b617d-110">**Remove-EventLog** Cmdlet 會從本機或遠端電腦中刪除事件記錄檔，並取消註冊記錄檔的所有事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-110">The **Remove-EventLog** cmdlet deletes an event log file from a local or remote computer and unregisters all its event sources for the log.</span></span>
<span data-ttu-id="b617d-111">您也可以使用這個 Cmdlet 來取消註冊事件來源，而不刪除任何事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b617d-111">You can also use this cmdlet to unregister event sources without deleting any event logs.</span></span>

<span data-ttu-id="b617d-112">包含 **eventlog** 名詞（ **eventlog** Cmdlet）的 Cmdlet 只適用于傳統的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b617d-112">The cmdlets that contain the **EventLog** noun, the **EventLog** cmdlets, work only on classic event logs.</span></span>
<span data-ttu-id="b617d-113">在 Windows Vista 和更新版本的 Windows 作業系統中，若要從使用「Windows 事件記錄檔」技術的記錄檔中取得事件，請使用 Get-WinEvent。</span><span class="sxs-lookup"><span data-stu-id="b617d-113">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use Get-WinEvent.</span></span>

<span data-ttu-id="b617d-114">注意：這個 Cmdlet 可以刪除作業系統事件記錄檔，這樣可能導致應用程式失敗和非預期的系統行為。</span><span class="sxs-lookup"><span data-stu-id="b617d-114">CAUTION: This cmdlet can delete operating system event logs, which might cause application failures and unexpected system behavior.</span></span>

## <span data-ttu-id="b617d-115">範例</span><span class="sxs-lookup"><span data-stu-id="b617d-115">EXAMPLES</span></span>

### <span data-ttu-id="b617d-116">範例 1︰從本機電腦中移除事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="b617d-116">Example 1: Remove an event log from the local computer</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

<span data-ttu-id="b617d-117">此命令會從本機電腦刪除 MyLog 事件記錄檔，並取消註冊其事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-117">This command deletes the MyLog event log from the local computer and unregisters its event sources.</span></span>

### <span data-ttu-id="b617d-118">範例 2︰從幾部電腦中移除事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="b617d-118">Example 2: Remove an event log from several computers</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="b617d-119">此命令會從本機電腦與 Server01 和 Server02 遠端電腦中刪除 MyLog 和 TestLog 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b617d-119">This command deletes the MyLog and TestLog event logs from the local computer and the Server01 and Server02 remote computers.</span></span>
<span data-ttu-id="b617d-120">此命令也會取消註冊這些記錄檔的事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-120">The command also unregisters the event sources for these logs.</span></span>

### <span data-ttu-id="b617d-121">範例 3︰刪除事件來源</span><span class="sxs-lookup"><span data-stu-id="b617d-121">Example 3: Delete an event source</span></span>

```
PS C:\> Remove-EventLog -Source "MyApp"
```

<span data-ttu-id="b617d-122">此命令會從本機電腦上的記錄檔刪除 MyApp 事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-122">This command deletes the MyApp event source from the logs on the local computer.</span></span>
<span data-ttu-id="b617d-123">當命令完成時，MyApp 程式無法寫入任何事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b617d-123">When the command finishes, the MyApp program cannot write to any event logs.</span></span>

### <span data-ttu-id="b617d-124">範例 4︰移除事件記錄檔，然後確認動作</span><span class="sxs-lookup"><span data-stu-id="b617d-124">Example 4: Remove an event log and confirm the action</span></span>

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

<span data-ttu-id="b617d-125">這些命令會顯示如何列出電腦上的事件記錄檔，並確認已成功 **移除 EventLog** 命令。</span><span class="sxs-lookup"><span data-stu-id="b617d-125">These commands show how to list the event logs on a computer and verify that a **Remove-EventLog** command was successful.</span></span>

### <span data-ttu-id="b617d-126">範例 5︰移除事件來源，然後確認動作</span><span class="sxs-lookup"><span data-stu-id="b617d-126">Example 5: Remove an event source and confirm the action</span></span>

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

<span data-ttu-id="b617d-127">這些命令使用 Get-WmiObject Cmdlet，列出本機電腦上的事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-127">These commands use the Get-WmiObject cmdlet to list the event sources on the local computer.</span></span>
<span data-ttu-id="b617d-128">您可以使用這些命令來確認命令成功與否或刪除事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-128">You can these commands to verify the success of a command or to delete an event source.</span></span>

<span data-ttu-id="b617d-129">第一個命令會取得本機電腦上 TestLog 事件記錄檔的事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-129">The first command gets the event sources of the TestLog event log on the local computer.</span></span>
<span data-ttu-id="b617d-130">MyApp 是其中一個來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-130">MyApp is one of the sources.</span></span>

<span data-ttu-id="b617d-131">第二個命令會使用 **Remove-EventLog** 的 *Source* 參數來刪除 MyApp 事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-131">The second command uses the *Source* parameter of **Remove-EventLog** to delete the MyApp event source.</span></span>

<span data-ttu-id="b617d-132">第三個命令與第一個命令相同。</span><span class="sxs-lookup"><span data-stu-id="b617d-132">The third command is identical to the first.</span></span>
<span data-ttu-id="b617d-133">它會顯示已刪除 MyApp 事件來源 。</span><span class="sxs-lookup"><span data-stu-id="b617d-133">It shows that the MyApp event source was deleted.</span></span>

## <span data-ttu-id="b617d-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b617d-134">PARAMETERS</span></span>

### <span data-ttu-id="b617d-135">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b617d-135">-ComputerName</span></span>
<span data-ttu-id="b617d-136">指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="b617d-136">Specifies a remote computer.</span></span>
<span data-ttu-id="b617d-137">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="b617d-137">The default is the local computer.</span></span>

<span data-ttu-id="b617d-138">輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="b617d-138">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="b617d-139">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。</span><span class="sxs-lookup"><span data-stu-id="b617d-139">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="b617d-140">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="b617d-140">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="b617d-141">您可以使用 **Remove-EventLog** 的 *ComputerName* 參數，即使您的電腦未設定為執行遠端命令也一樣。</span><span class="sxs-lookup"><span data-stu-id="b617d-141">You can use the *ComputerName* parameter of **Remove-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b617d-142">-LogName</span><span class="sxs-lookup"><span data-stu-id="b617d-142">-LogName</span></span>
<span data-ttu-id="b617d-143">指定事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b617d-143">Specifies the event logs.</span></span>
<span data-ttu-id="b617d-144">輸入一或多個事件記錄檔的記錄檔名稱，並使用逗號區隔。</span><span class="sxs-lookup"><span data-stu-id="b617d-144">Enter the log name of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="b617d-145">記錄檔名稱是 **Log** 屬性的值，而非 *LogDisplayName* ，不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b617d-145">The log name is the value of the **Log** property, not the *LogDisplayName* , Wildcard characters are not permitted.</span></span>
<span data-ttu-id="b617d-146">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="b617d-146">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b617d-147">-Source</span><span class="sxs-lookup"><span data-stu-id="b617d-147">-Source</span></span>
<span data-ttu-id="b617d-148">指定此 Cmdlet 取消註冊的事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-148">Specifies the event sources that this cmdlet unregisters.</span></span>
<span data-ttu-id="b617d-149">輸入來源名稱 (不是可執行檔名稱)，並使用逗號區隔。</span><span class="sxs-lookup"><span data-stu-id="b617d-149">Enter the source names, not the executable name, separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b617d-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b617d-150">-Confirm</span></span>
<span data-ttu-id="b617d-151">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="b617d-151">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b617d-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b617d-152">-WhatIf</span></span>
<span data-ttu-id="b617d-153">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="b617d-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b617d-154">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="b617d-154">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b617d-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b617d-155">CommonParameters</span></span>
<span data-ttu-id="b617d-156">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b617d-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b617d-157">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b617d-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b617d-158">輸入</span><span class="sxs-lookup"><span data-stu-id="b617d-158">INPUTS</span></span>

### <span data-ttu-id="b617d-159">無</span><span class="sxs-lookup"><span data-stu-id="b617d-159">None</span></span>
<span data-ttu-id="b617d-160">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b617d-160">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b617d-161">輸出</span><span class="sxs-lookup"><span data-stu-id="b617d-161">OUTPUTS</span></span>

### <span data-ttu-id="b617d-162">無</span><span class="sxs-lookup"><span data-stu-id="b617d-162">None</span></span>
<span data-ttu-id="b617d-163">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="b617d-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="b617d-164">注意</span><span class="sxs-lookup"><span data-stu-id="b617d-164">NOTES</span></span>

* <span data-ttu-id="b617d-165">若要在 Windows Vista 和更新版本的 Windows 作業系統上使用 **Remove-EventLog** ，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="b617d-165">To use **Remove-EventLog** on Windows Vista and later versions of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

  <span data-ttu-id="b617d-166">如果您移除事件記錄檔，然後重新建立記錄檔，您將無法註冊相同的事件來源。</span><span class="sxs-lookup"><span data-stu-id="b617d-166">If you remove an event log and then re-create the log, you will not be able to register the same event sources.</span></span>
<span data-ttu-id="b617d-167">使用事件來源將項目寫入原始記錄檔的應用程式，將無法寫入新的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b617d-167">Applications that used the events sources to write entries to the original log will not be able to write to the new log.</span></span>

* <span data-ttu-id="b617d-168">當您取消註冊特定記錄檔的事件來源時，事件來源可能無法在其他事件記錄檔中寫入項目。</span><span class="sxs-lookup"><span data-stu-id="b617d-168">When you unregister an event source for a particular log, the event source might be prevented from writing entries in other event logs.</span></span>

## <span data-ttu-id="b617d-169">相關連結</span><span class="sxs-lookup"><span data-stu-id="b617d-169">RELATED LINKS</span></span>

[<span data-ttu-id="b617d-170">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="b617d-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="b617d-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="b617d-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="b617d-172">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="b617d-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="b617d-173">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="b617d-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="b617d-174">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="b617d-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="b617d-175">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="b617d-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="b617d-176">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="b617d-176">Write-EventLog</span></span>](Write-EventLog.md)
