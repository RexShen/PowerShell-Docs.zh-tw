---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: 695a13d4fbbf60caadeed994c1aa9c36432be917
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204068"
---
# <span data-ttu-id="cbd18-103">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="cbd18-103">Clear-EventLog</span></span>

## <span data-ttu-id="cbd18-104">概要</span><span class="sxs-lookup"><span data-stu-id="cbd18-104">SYNOPSIS</span></span>
<span data-ttu-id="cbd18-105">清除本機或遠端電腦上指定之事件記錄檔中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="cbd18-105">Clears all entries from specified event logs on the local or remote computers.</span></span>

## <span data-ttu-id="cbd18-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cbd18-106">SYNTAX</span></span>

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cbd18-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cbd18-107">DESCRIPTION</span></span>

<span data-ttu-id="cbd18-108">`Clear-EventLog`Cmdlet 會刪除本機電腦或遠端電腦上指定之事件記錄檔中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="cbd18-108">The `Clear-EventLog` cmdlet deletes all of the entries from the specified event logs on the local computer or on remote computers.</span></span>
<span data-ttu-id="cbd18-109">若要使用 `Clear-EventLog` ，您必須是受影響電腦上 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="cbd18-109">To use `Clear-EventLog`, you must be a member of the Administrators group on the affected computer.</span></span>

<span data-ttu-id="cbd18-110">包含 **eventlog** 名詞 (eventlog Cmdlet 的指令程式) 只會在傳統事件記錄檔上運作。</span><span class="sxs-lookup"><span data-stu-id="cbd18-110">The cmdlets that contain the **EventLog** noun (the EventLog cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="cbd18-111">若要在 Windows Vista 和更新版本的 Windows 中，從使用 Windows 事件記錄檔技術的記錄檔中取得事件，請使用 Get-WinEvent Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cbd18-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use the Get-WinEvent cmdlet.</span></span>

## <span data-ttu-id="cbd18-112">範例</span><span class="sxs-lookup"><span data-stu-id="cbd18-112">EXAMPLES</span></span>

### <span data-ttu-id="cbd18-113">範例1：清除本機電腦上的特定事件記錄檔類型</span><span class="sxs-lookup"><span data-stu-id="cbd18-113">Example 1: Clear specific event log types from the local computer</span></span>

```powershell
Clear-EventLog "Windows PowerShell"
```

<span data-ttu-id="cbd18-114">此命令會清除本機電腦上 Windows PowerShell 事件記錄檔中的專案。</span><span class="sxs-lookup"><span data-stu-id="cbd18-114">This command clears the entries from the Windows PowerShell event log on the local computer.</span></span>

### <span data-ttu-id="cbd18-115">範例2：清除本機和遠端電腦上的特定多個記錄類型</span><span class="sxs-lookup"><span data-stu-id="cbd18-115">Example 2: Clear specific multiple log types from the local and remote computers</span></span>

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

<span data-ttu-id="cbd18-116">此命令會清除 Microsoft Office 診斷 (ODiag) 中的所有專案，以及 Microsoft Office 會話 (OSession) 本機電腦和 Server02 遠端電腦上的記錄。</span><span class="sxs-lookup"><span data-stu-id="cbd18-116">This command clears all of the entries in the Microsoft Office Diagnostics (ODiag) and Microsoft Office Sessions (OSession) logs on the local computer and the Server02 remote computer.</span></span>

### <span data-ttu-id="cbd18-117">範例3：清除指定電腦上的所有記錄，然後顯示事件記錄檔清單</span><span class="sxs-lookup"><span data-stu-id="cbd18-117">Example 3: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
Clear-EventLog -LogName application, system -confirm
```

<span data-ttu-id="cbd18-118">此命令會在刪除指定的事件記錄檔中的項目之前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="cbd18-118">This command prompts you for confirmation before deleting the entries in the specified event logs.</span></span>

### <span data-ttu-id="cbd18-119">範例4：清除指定電腦上的所有記錄，然後顯示事件記錄檔清單</span><span class="sxs-lookup"><span data-stu-id="cbd18-119">Example 4: Clear all logs on the specified computers then display the event log list</span></span>

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

<span data-ttu-id="cbd18-120">此函式會清除指定電腦上的所有事件記錄檔，然後顯示操作結果的事件記錄檔清單。</span><span class="sxs-lookup"><span data-stu-id="cbd18-120">This function clears all event logs on the specified computers and then displays the resulting event log list.</span></span>

<span data-ttu-id="cbd18-121">請注意，在清除記錄檔之後有一些項目加入「系統」和「安全性」記錄檔，而加入的時間是在顯示記錄檔之前。</span><span class="sxs-lookup"><span data-stu-id="cbd18-121">Notice that a few entries were added to the System and Security logs after the logs were cleared but before they were displayed.</span></span>

## <span data-ttu-id="cbd18-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cbd18-122">PARAMETERS</span></span>

### <span data-ttu-id="cbd18-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="cbd18-123">-ComputerName</span></span>

<span data-ttu-id="cbd18-124">指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="cbd18-124">Specifies a remote computer.</span></span>
<span data-ttu-id="cbd18-125">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="cbd18-125">The default is the local computer.</span></span>

<span data-ttu-id="cbd18-126">輸入遠端電腦的 NetBIOS 名稱、網際網路通訊協定 (IP) 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="cbd18-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="cbd18-127">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="cbd18-127">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="cbd18-128">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="cbd18-128">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="cbd18-129">**ComputerName** `Get-EventLog` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。</span><span class="sxs-lookup"><span data-stu-id="cbd18-129">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd18-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="cbd18-130">-LogName</span></span>

<span data-ttu-id="cbd18-131">指定事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="cbd18-131">Specifies the event logs.</span></span>
<span data-ttu-id="cbd18-132">輸入一或多個事件記錄檔的記錄檔名稱 (Log 屬性的值，而不是 LogDisplayName)，並使用逗號區隔。</span><span class="sxs-lookup"><span data-stu-id="cbd18-132">Enter the log name (the value of the Log property; not the LogDisplayName) of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="cbd18-133">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cbd18-133">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="cbd18-134">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="cbd18-134">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cbd18-135">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cbd18-135">-Confirm</span></span>

<span data-ttu-id="cbd18-136">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="cbd18-136">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cbd18-137">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cbd18-137">-WhatIf</span></span>

<span data-ttu-id="cbd18-138">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="cbd18-138">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="cbd18-139">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="cbd18-139">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cbd18-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cbd18-140">CommonParameters</span></span>

<span data-ttu-id="cbd18-141">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cbd18-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cbd18-142">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="cbd18-142">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="cbd18-143">輸入</span><span class="sxs-lookup"><span data-stu-id="cbd18-143">INPUTS</span></span>

### <span data-ttu-id="cbd18-144">無</span><span class="sxs-lookup"><span data-stu-id="cbd18-144">None</span></span>

<span data-ttu-id="cbd18-145">您無法透過管道傳送物件至 `Clear-EventLog` 。</span><span class="sxs-lookup"><span data-stu-id="cbd18-145">You cannot pipe objects to `Clear-EventLog`.</span></span>

## <span data-ttu-id="cbd18-146">輸出</span><span class="sxs-lookup"><span data-stu-id="cbd18-146">OUTPUTS</span></span>

### <span data-ttu-id="cbd18-147">無</span><span class="sxs-lookup"><span data-stu-id="cbd18-147">None</span></span>

<span data-ttu-id="cbd18-148">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="cbd18-148">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="cbd18-149">注意</span><span class="sxs-lookup"><span data-stu-id="cbd18-149">NOTES</span></span>

- <span data-ttu-id="cbd18-150">若要使用 `Clear-EventLog` Windows Vista 和更新版本的 windows，請使用 [以系統管理員身分執行] 選項開始 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cbd18-150">To use `Clear-EventLog` on Windows Vista and later versions of Windows, start Windows PowerShell with the "Run as administrator" option.</span></span>

## <span data-ttu-id="cbd18-151">相關連結</span><span class="sxs-lookup"><span data-stu-id="cbd18-151">RELATED LINKS</span></span>

[<span data-ttu-id="cbd18-152">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="cbd18-152">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="cbd18-153">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="cbd18-153">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="cbd18-154">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="cbd18-154">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="cbd18-155">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="cbd18-155">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="cbd18-156">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="cbd18-156">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="cbd18-157">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="cbd18-157">Write-EventLog</span></span>](Write-EventLog.md)
