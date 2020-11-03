---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203619"
---
# <span data-ttu-id="435d3-103">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="435d3-103">Limit-EventLog</span></span>

## <span data-ttu-id="435d3-104">概要</span><span class="sxs-lookup"><span data-stu-id="435d3-104">SYNOPSIS</span></span>
<span data-ttu-id="435d3-105">設定限制事件記錄檔大小和其項目存留期的事件記錄檔屬性。</span><span class="sxs-lookup"><span data-stu-id="435d3-105">Sets the event log properties that limit the size of the event log and the age of its entries.</span></span>

## <span data-ttu-id="435d3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="435d3-106">SYNTAX</span></span>

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="435d3-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="435d3-107">DESCRIPTION</span></span>
<span data-ttu-id="435d3-108">**Limit-EventLog** Cmdlet 會設定傳統事件記錄檔的大小上限、每個事件必須保留多久，以及當記錄檔到達大小上限時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="435d3-108">The **Limit-EventLog** cmdlet sets the maximum size of a classic event log, how long each event must be retained, and what happens when the log reaches its maximum size.</span></span>
<span data-ttu-id="435d3-109">您可以使用它來限制本機電腦或遠端電腦上的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="435d3-109">You can use it to limit the event logs on local or remote computers.</span></span>

<span data-ttu-id="435d3-110">包含 EventLog 名詞 (EventLog Cmdlet) 的 Cmdlet 只能用於傳統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="435d3-110">The cmdlets that contain the EventLog noun (the EventLog cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="435d3-111">在 Windows Vista 和更新版本的 Windows 中，若要從使用「Windows 事件記錄檔」技術的記錄檔中取得事件，請使用 Get-WinEvent。</span><span class="sxs-lookup"><span data-stu-id="435d3-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use Get-WinEvent.</span></span>

## <span data-ttu-id="435d3-112">範例</span><span class="sxs-lookup"><span data-stu-id="435d3-112">EXAMPLES</span></span>

### <span data-ttu-id="435d3-113">範例1：增加事件記錄檔的大小</span><span class="sxs-lookup"><span data-stu-id="435d3-113">Example 1: Increase the size of an event log</span></span>

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

<span data-ttu-id="435d3-114">此命令將本機電腦上 Windows PowerShell 事件記錄檔的大小上限增加到 20480 位元組 (20 KB)。</span><span class="sxs-lookup"><span data-stu-id="435d3-114">This command increases the maximum size of the Windows PowerShell event log on the local computer to 20480 bytes (20 KB).</span></span>

### <span data-ttu-id="435d3-115">範例2：保留指定期間的事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="435d3-115">Example 2: Retain an event log for a specified duration</span></span>

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

<span data-ttu-id="435d3-116">此命令會確保將 Server01 和 Server02 電腦上 Security 事件記錄檔中的事件至少保留 7 天。</span><span class="sxs-lookup"><span data-stu-id="435d3-116">This command ensures that events in the Security log on the Server01 and Server02 computers are retained for at least 7 days.</span></span>

### <span data-ttu-id="435d3-117">範例3：變更所有事件記錄檔的溢位動作</span><span class="sxs-lookup"><span data-stu-id="435d3-117">Example 3: Change the overflow action of all event logs</span></span>

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

<span data-ttu-id="435d3-118">此範例會將本機電腦上所有事件記錄檔的溢位動作變更為 OverwriteOlder。</span><span class="sxs-lookup"><span data-stu-id="435d3-118">This example changes the overflow action of all event logs on the local computer to OverwriteOlder.</span></span>

<span data-ttu-id="435d3-119">第一個命令取得本機電腦上所有記錄檔的記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="435d3-119">The first command gets the log names of all of the logs on the local computer.</span></span>
<span data-ttu-id="435d3-120">第二個命令設定溢位動作。</span><span class="sxs-lookup"><span data-stu-id="435d3-120">The second command sets the overflow action.</span></span>
<span data-ttu-id="435d3-121">第三個命令顯示結果。</span><span class="sxs-lookup"><span data-stu-id="435d3-121">The third command displays the results.</span></span>

## <span data-ttu-id="435d3-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="435d3-122">PARAMETERS</span></span>

### <span data-ttu-id="435d3-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="435d3-123">-ComputerName</span></span>
<span data-ttu-id="435d3-124">指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="435d3-124">Specifies remote computers.</span></span>
<span data-ttu-id="435d3-125">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="435d3-125">The default is the local computer.</span></span>

<span data-ttu-id="435d3-126">輸入 NetBIOS 名稱、網際網路通訊協定 (IP) 位址，或遠端電腦 (FQDN) 的完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="435d3-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="435d3-127">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。</span><span class="sxs-lookup"><span data-stu-id="435d3-127">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="435d3-128">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="435d3-128">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="435d3-129">即使您的電腦未設定為執行遠端命令，您也可以使用 **Limit-EventLog** 的 *ComputerName* 參數。</span><span class="sxs-lookup"><span data-stu-id="435d3-129">You can use the *ComputerName* parameter of **Limit-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="435d3-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="435d3-130">-LogName</span></span>
<span data-ttu-id="435d3-131">指定事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="435d3-131">Specifies the event logs.</span></span>
<span data-ttu-id="435d3-132">輸入一或多個事件記錄檔的記錄檔名稱 (Log 屬性的值，而不是 LogDisplayName)，並使用逗號區隔。</span><span class="sxs-lookup"><span data-stu-id="435d3-132">Enter the log name (the value of the Log property; not the LogDisplayName) of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="435d3-133">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="435d3-133">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="435d3-134">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="435d3-134">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="435d3-135">-MaximumSize</span><span class="sxs-lookup"><span data-stu-id="435d3-135">-MaximumSize</span></span>
<span data-ttu-id="435d3-136">指定事件記錄檔的大小上限 (單位為位元組)。</span><span class="sxs-lookup"><span data-stu-id="435d3-136">Specifies the maximum size of the event logs in bytes.</span></span>
<span data-ttu-id="435d3-137">輸入介於 64 KB 到 4 GB 之間的值。</span><span class="sxs-lookup"><span data-stu-id="435d3-137">Enter a value between 64 kilobytes (KB) and 4 gigabytes (GB).</span></span>
<span data-ttu-id="435d3-138">此值必須可被 64 KB (65536) 整除。</span><span class="sxs-lookup"><span data-stu-id="435d3-138">The value must be divisible by 64 KB (65536).</span></span>

<span data-ttu-id="435d3-139">此參數會指定代表傳統事件記錄檔之 system.string **物件的** **MaximumKilobytes** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="435d3-139">This parameter specifies the value of the **MaximumKilobytes** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="435d3-140">-OverflowAction</span><span class="sxs-lookup"><span data-stu-id="435d3-140">-OverflowAction</span></span>
<span data-ttu-id="435d3-141">指定當事件記錄檔達到大小上限時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="435d3-141">Specifies what happens when the event log reaches its maximum size.</span></span>

<span data-ttu-id="435d3-142">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="435d3-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="435d3-143">DoNotOverwrite：保留現有的項目並捨棄新的項目。</span><span class="sxs-lookup"><span data-stu-id="435d3-143">DoNotOverwrite:  Existing entries are retained and new entries are discarded.</span></span>
- <span data-ttu-id="435d3-144">OverwriteAsNeeded：每個新項目皆覆寫最舊的項目。</span><span class="sxs-lookup"><span data-stu-id="435d3-144">OverwriteAsNeeded:  Each new entry overwrites the oldest entry.</span></span>
- <span data-ttu-id="435d3-145">OverwriteOlder：新的事件會覆寫早于 **MinimumRetentionDays** 屬性所指定之值的事件。</span><span class="sxs-lookup"><span data-stu-id="435d3-145">OverwriteOlder:  New events overwrite events older than the value specified by the **MinimumRetentionDays** property.</span></span> <span data-ttu-id="435d3-146">如果沒有早于 **MinimumRetentionDays** 屬性值所指定的事件，則會捨棄新的事件。</span><span class="sxs-lookup"><span data-stu-id="435d3-146">If there are no events older than specified by the **MinimumRetentionDays** property value, new events are discarded.</span></span>

<span data-ttu-id="435d3-147">此參數會指定代表傳統事件記錄檔之 system.string **物件的** **OverflowAction** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="435d3-147">This parameter specifies the value of the **OverflowAction** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="435d3-148">-RetentionDays</span><span class="sxs-lookup"><span data-stu-id="435d3-148">-RetentionDays</span></span>
<span data-ttu-id="435d3-149">指定事件必須保留在事件記錄檔中的天數下限。</span><span class="sxs-lookup"><span data-stu-id="435d3-149">Specifies the minimum number of days that an event must remain in the event log.</span></span>

<span data-ttu-id="435d3-150">此參數會指定代表傳統事件記錄檔之 system.string **物件的** **MinimumRetentionDays** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="435d3-150">This parameter specifies the value of the **MinimumRetentionDays** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="435d3-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="435d3-151">-Confirm</span></span>
<span data-ttu-id="435d3-152">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="435d3-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="435d3-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="435d3-153">-WhatIf</span></span>
<span data-ttu-id="435d3-154">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="435d3-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="435d3-155">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="435d3-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="435d3-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="435d3-156">CommonParameters</span></span>
<span data-ttu-id="435d3-157">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="435d3-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="435d3-158">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="435d3-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="435d3-159">輸入</span><span class="sxs-lookup"><span data-stu-id="435d3-159">INPUTS</span></span>

### <span data-ttu-id="435d3-160">無</span><span class="sxs-lookup"><span data-stu-id="435d3-160">None</span></span>
<span data-ttu-id="435d3-161">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="435d3-161">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="435d3-162">輸出</span><span class="sxs-lookup"><span data-stu-id="435d3-162">OUTPUTS</span></span>

### <span data-ttu-id="435d3-163">無</span><span class="sxs-lookup"><span data-stu-id="435d3-163">None</span></span>
<span data-ttu-id="435d3-164">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="435d3-164">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="435d3-165">注意</span><span class="sxs-lookup"><span data-stu-id="435d3-165">NOTES</span></span>

* <span data-ttu-id="435d3-166">若要在 Windows Vista 和更新版本的 Windows 上使用此 Cmdlet，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="435d3-166">To use this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="435d3-167">此 Cmdlet 會變更代表傳統事件記錄檔之 **system.string 物件的屬性。**</span><span class="sxs-lookup"><span data-stu-id="435d3-167">This cmdlet changes the properties of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>
<span data-ttu-id="435d3-168">若要查看事件記錄檔屬性的目前設定，請輸入 `Get-EventLog -List` 。</span><span class="sxs-lookup"><span data-stu-id="435d3-168">To see the current settings of the event log properties, type `Get-EventLog -List`.</span></span>

*

## <span data-ttu-id="435d3-169">相關連結</span><span class="sxs-lookup"><span data-stu-id="435d3-169">RELATED LINKS</span></span>

[<span data-ttu-id="435d3-170">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="435d3-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="435d3-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="435d3-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="435d3-172">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="435d3-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="435d3-173">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="435d3-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="435d3-174">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="435d3-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="435d3-175">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="435d3-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="435d3-176">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="435d3-176">Write-EventLog</span></span>](Write-EventLog.md)
