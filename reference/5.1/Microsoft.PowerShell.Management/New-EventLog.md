---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203596"
---
# <span data-ttu-id="31d4e-103">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="31d4e-103">New-EventLog</span></span>

## <span data-ttu-id="31d4e-104">概要</span><span class="sxs-lookup"><span data-stu-id="31d4e-104">SYNOPSIS</span></span>
<span data-ttu-id="31d4e-105">在本機或遠端電腦上建立新的事件記錄檔和新的事件來源。</span><span class="sxs-lookup"><span data-stu-id="31d4e-105">Creates a new event log and a new event source on a local or remote computer.</span></span>

## <span data-ttu-id="31d4e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="31d4e-106">SYNTAX</span></span>

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## <span data-ttu-id="31d4e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="31d4e-107">DESCRIPTION</span></span>

<span data-ttu-id="31d4e-108">這個 Cmdlet 會在本機或遠端電腦上建立新的傳統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="31d4e-108">This cmdlet creates a new classic event log on a local or remote computer.</span></span> <span data-ttu-id="31d4e-109">它也可以登錄要寫入新記錄檔或現有記錄檔的事件來源。</span><span class="sxs-lookup"><span data-stu-id="31d4e-109">It can also register an event source that writes to the new log or to an existing log.</span></span>

<span data-ttu-id="31d4e-110">包含事件記錄檔名詞 (事件記錄檔 Cmdlet) 的 Cmdlet 只適用於傳統的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="31d4e-110">The cmdlets that contain the EventLog noun (the Event log cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="31d4e-111">若要在 Windows Vista 和更新版本的 Windows 中，從使用 Windows 事件記錄檔技術的記錄檔中取得事件，請使用 `Get-WinEvent` 。</span><span class="sxs-lookup"><span data-stu-id="31d4e-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use `Get-WinEvent`.</span></span>

## <span data-ttu-id="31d4e-112">範例</span><span class="sxs-lookup"><span data-stu-id="31d4e-112">EXAMPLES</span></span>

### <span data-ttu-id="31d4e-113">範例 1-建立新的事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="31d4e-113">Example 1 - create a new event log</span></span>

<span data-ttu-id="31d4e-114">這個命令在本機電腦上建立 TestLog 事件記錄檔，並為其登錄新來源。</span><span class="sxs-lookup"><span data-stu-id="31d4e-114">This command creates the TestLog event log on the local computer and registers a new source for it.</span></span>

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### <span data-ttu-id="31d4e-115">範例 2-將新的事件來源新增至現有的記錄檔</span><span class="sxs-lookup"><span data-stu-id="31d4e-115">Example 2 - add a new event source to an existing log</span></span>

<span data-ttu-id="31d4e-116">這個命令將新的事件來源 (NewTestApp) 新增到 Server01 遠端電腦上的應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="31d4e-116">This command adds a new event source, NewTestApp, to the Application log on the Server01 remote computer.</span></span>

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

<span data-ttu-id="31d4e-117">這個命令要求 NewTestApp.dll 檔案必須位於 Server01 電腦上。</span><span class="sxs-lookup"><span data-stu-id="31d4e-117">The command requires that the NewTestApp.dll file is located on the Server01 computer.</span></span>

## <span data-ttu-id="31d4e-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="31d4e-118">PARAMETERS</span></span>

### <span data-ttu-id="31d4e-119">-CategoryResourceFile</span><span class="sxs-lookup"><span data-stu-id="31d4e-119">-CategoryResourceFile</span></span>

<span data-ttu-id="31d4e-120">指定包含來源事件類別字串的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="31d4e-120">Specifies the path to the file that contains category strings for the source events.</span></span> <span data-ttu-id="31d4e-121">這個檔案也稱為「類別訊息檔案」。</span><span class="sxs-lookup"><span data-stu-id="31d4e-121">This file is also known as the Category Message File.</span></span>

<span data-ttu-id="31d4e-122">這個檔案必須存在於建立事件記錄檔的電腦上。</span><span class="sxs-lookup"><span data-stu-id="31d4e-122">The file must be present on the computer on which the event log is being created.</span></span> <span data-ttu-id="31d4e-123">這個參數不會建立或移動檔案。</span><span class="sxs-lookup"><span data-stu-id="31d4e-123">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31d4e-124">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="31d4e-124">-ComputerName</span></span>

<span data-ttu-id="31d4e-125">在指定的電腦上建立新的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="31d4e-125">Creates the new event logs on the specified computers.</span></span> <span data-ttu-id="31d4e-126">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="31d4e-126">The default is the local computer.</span></span>

<span data-ttu-id="31d4e-127">遠端電腦的 NetBIOS 名稱、IP 位址或完整功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="31d4e-127">The NetBIOS name, IP address, or fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="31d4e-128">若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 "localhost"。</span><span class="sxs-lookup"><span data-stu-id="31d4e-128">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="31d4e-129">此參數不依賴 PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="31d4e-129">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="31d4e-130">**ComputerName** `Get-EventLog` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。</span><span class="sxs-lookup"><span data-stu-id="31d4e-130">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31d4e-131">-LogName</span><span class="sxs-lookup"><span data-stu-id="31d4e-131">-LogName</span></span>

<span data-ttu-id="31d4e-132">指定事件記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="31d4e-132">Specifies the name of the event log.</span></span>

<span data-ttu-id="31d4e-133">如果記錄檔不存在，就會 `New-EventLog` 建立記錄檔，並針對新事件記錄檔的 **Log** 和 **LogDisplayName** 屬性使用此值。</span><span class="sxs-lookup"><span data-stu-id="31d4e-133">If the log does not exist, `New-EventLog` creates the log and uses this value for the **Log** and **LogDisplayName** properties of the new event log.</span></span> <span data-ttu-id="31d4e-134">如果記錄檔存在， `New-EventLog` 則為事件記錄檔登錄新的來源。</span><span class="sxs-lookup"><span data-stu-id="31d4e-134">If the log exists, `New-EventLog` registers a new source for the event log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31d4e-135">-MessageResourceFile</span><span class="sxs-lookup"><span data-stu-id="31d4e-135">-MessageResourceFile</span></span>

<span data-ttu-id="31d4e-136">指定包含來源事件訊息格式字串的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="31d4e-136">Specifies the path to the file that contains message formatting strings for the source events.</span></span>
<span data-ttu-id="31d4e-137">這個檔案也稱為「事件訊息檔案」。</span><span class="sxs-lookup"><span data-stu-id="31d4e-137">This file is also known as the Event Message File.</span></span>

<span data-ttu-id="31d4e-138">這個檔案必須存在於建立事件記錄檔的電腦上。</span><span class="sxs-lookup"><span data-stu-id="31d4e-138">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="31d4e-139">這個參數不會建立或移動檔案。</span><span class="sxs-lookup"><span data-stu-id="31d4e-139">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31d4e-140">-ParameterResourceFile</span><span class="sxs-lookup"><span data-stu-id="31d4e-140">-ParameterResourceFile</span></span>

<span data-ttu-id="31d4e-141">指定檔案的路徑，該檔案中包含事件說明中用來替換參數的字串。</span><span class="sxs-lookup"><span data-stu-id="31d4e-141">Specifies the path to the file that contains strings used for parameter substitutions in event descriptions.</span></span> <span data-ttu-id="31d4e-142">這個檔案也稱為「參數訊息檔案」。</span><span class="sxs-lookup"><span data-stu-id="31d4e-142">This file is also known as the Parameter Message File.</span></span>

<span data-ttu-id="31d4e-143">這個檔案必須存在於建立事件記錄檔的電腦上。</span><span class="sxs-lookup"><span data-stu-id="31d4e-143">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="31d4e-144">這個參數不會建立或移動檔案。</span><span class="sxs-lookup"><span data-stu-id="31d4e-144">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31d4e-145">-Source</span><span class="sxs-lookup"><span data-stu-id="31d4e-145">-Source</span></span>

<span data-ttu-id="31d4e-146">指定事件記錄檔來源的名稱，例如，寫入事件記錄檔的應用程式。</span><span class="sxs-lookup"><span data-stu-id="31d4e-146">Specifies the names of the event log sources, such as application programs that write to the event log.</span></span> <span data-ttu-id="31d4e-147">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="31d4e-147">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31d4e-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31d4e-148">CommonParameters</span></span>

<span data-ttu-id="31d4e-149">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="31d4e-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="31d4e-150">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="31d4e-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="31d4e-151">輸入</span><span class="sxs-lookup"><span data-stu-id="31d4e-151">INPUTS</span></span>

### <span data-ttu-id="31d4e-152">無</span><span class="sxs-lookup"><span data-stu-id="31d4e-152">None</span></span>

<span data-ttu-id="31d4e-153">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="31d4e-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="31d4e-154">輸出</span><span class="sxs-lookup"><span data-stu-id="31d4e-154">OUTPUTS</span></span>

### <span data-ttu-id="31d4e-155">System.Diagnostics.EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="31d4e-155">System.Diagnostics.EventLogEntry</span></span>

## <span data-ttu-id="31d4e-156">注意</span><span class="sxs-lookup"><span data-stu-id="31d4e-156">NOTES</span></span>

<span data-ttu-id="31d4e-157">若要使用 `New-EventLog` Windows Vista 和更新版本的 windows，請使用 [以系統管理員身分執行] 選項開啟 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="31d4e-157">To use `New-EventLog` on Windows Vista and later versions of Windows, open PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="31d4e-158">若要在 Windows Vista、Windows XP Professional 或 Windows Server 2003 中建立事件來源，您必須是電腦上的 Administrators 群組成員。</span><span class="sxs-lookup"><span data-stu-id="31d4e-158">To create an event source in Windows Vista, Windows XP Professional, or Windows Server 2003, you must be a member of the Administrators group on the computer.</span></span>

<span data-ttu-id="31d4e-159">當您建立新的事件記錄檔和新的事件來源時，系統會登錄新記錄檔的新來源，但直到將第一個項目寫入記錄檔時，才會建立該記錄檔。</span><span class="sxs-lookup"><span data-stu-id="31d4e-159">When you create a new event log and a new event source, the system registers the new source for the new log, but the log is not created until the first entry is written to it.</span></span>

<span data-ttu-id="31d4e-160">作業系統會將事件記錄檔儲存為檔案。</span><span class="sxs-lookup"><span data-stu-id="31d4e-160">The operating system stores event logs as files.</span></span>

<span data-ttu-id="31d4e-161">當您建立新的事件記錄檔時，相關聯的檔案會儲存在 `$env:SystemRoot\System32\Config` 指定電腦上的目錄中。</span><span class="sxs-lookup"><span data-stu-id="31d4e-161">When you create a new event log, the associated file is stored in the `$env:SystemRoot\System32\Config` directory on the specified computer.</span></span>

<span data-ttu-id="31d4e-162">檔案名為 **Log** 屬性的前八個字元，檔案名副檔名為 .evt。</span><span class="sxs-lookup"><span data-stu-id="31d4e-162">The file name is the first eight characters of the **Log** property with an .evt file name extension.</span></span>

## <span data-ttu-id="31d4e-163">相關連結</span><span class="sxs-lookup"><span data-stu-id="31d4e-163">RELATED LINKS</span></span>

[<span data-ttu-id="31d4e-164">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="31d4e-164">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="31d4e-165">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="31d4e-165">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="31d4e-166">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="31d4e-166">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="31d4e-167">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="31d4e-167">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="31d4e-168">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="31d4e-168">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="31d4e-169">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="31d4e-169">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="31d4e-170">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="31d4e-170">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="31d4e-171">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="31d4e-171">Write-EventLog</span></span>](Write-EventLog.md)
