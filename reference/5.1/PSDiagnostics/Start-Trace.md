---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: cbdb40edf85dd4645552f6e096a99384532b4443
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203044"
---
# <span data-ttu-id="7ce07-103">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="7ce07-103">Start-Trace</span></span>

## <span data-ttu-id="7ce07-104">概要</span><span class="sxs-lookup"><span data-stu-id="7ce07-104">SYNOPSIS</span></span>
<span data-ttu-id="7ce07-105">啟動事件追蹤記錄會話。</span><span class="sxs-lookup"><span data-stu-id="7ce07-105">Start an Event Trace logging session.</span></span>

## <span data-ttu-id="7ce07-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7ce07-106">SYNTAX</span></span>

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="7ce07-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="7ce07-107">DESCRIPTION</span></span>
<span data-ttu-id="7ce07-108">此 Cmdlet 會啟動 Windows 事件追蹤記錄會話。</span><span class="sxs-lookup"><span data-stu-id="7ce07-108">This cmdlet starts a Windows Event Trace logging session.</span></span>

<span data-ttu-id="7ce07-109">下列 Cmdlet 會使用此 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="7ce07-109">This cmdlet is used by the following cmdlets:</span></span>

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

<span data-ttu-id="7ce07-110">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7ce07-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="7ce07-111">範例</span><span class="sxs-lookup"><span data-stu-id="7ce07-111">EXAMPLES</span></span>

### <span data-ttu-id="7ce07-112">範例1：啟動 WSMan 追蹤記錄會話</span><span class="sxs-lookup"><span data-stu-id="7ce07-112">Example 1: Start a WSMan Trace logging session</span></span>

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## <span data-ttu-id="7ce07-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7ce07-113">PARAMETERS</span></span>

### <span data-ttu-id="7ce07-114">-BufferSizeInKB</span><span class="sxs-lookup"><span data-stu-id="7ce07-114">-BufferSizeInKB</span></span>
<span data-ttu-id="7ce07-115">事件追蹤會話緩衝區大小，以 kb 為單位 (KB) 。</span><span class="sxs-lookup"><span data-stu-id="7ce07-115">Event Trace Session buffer size in kilobytes (KB).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce07-116">-ETS</span><span class="sxs-lookup"><span data-stu-id="7ce07-116">-ETS</span></span>
<span data-ttu-id="7ce07-117">直接將命令傳送至事件追蹤會話，而不儲存或排程。</span><span class="sxs-lookup"><span data-stu-id="7ce07-117">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce07-118">-Format</span><span class="sxs-lookup"><span data-stu-id="7ce07-118">-Format</span></span>
<span data-ttu-id="7ce07-119">指定資料收集器的記錄檔格式。</span><span class="sxs-lookup"><span data-stu-id="7ce07-119">Specifies the log format for the data collector.</span></span> <span data-ttu-id="7ce07-120">針對 SQL database 格式，您必須在命令列中使用 **OutputFilePath** 選項搭配 `dsn!log` 值。</span><span class="sxs-lookup"><span data-stu-id="7ce07-120">For SQL database format, you must use the **OutputFilePath** option in the command line with the `dsn!log` value.</span></span> <span data-ttu-id="7ce07-121">預設值為 binary (bin) 。</span><span class="sxs-lookup"><span data-stu-id="7ce07-121">The default is binary (bin).</span></span> <span data-ttu-id="7ce07-122">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="7ce07-122">The possible values are:</span></span>

- <span data-ttu-id="7ce07-123">bin-二進位</span><span class="sxs-lookup"><span data-stu-id="7ce07-123">bin - binary</span></span>
- <span data-ttu-id="7ce07-124">bincirc-具有迴圈記錄的二進位檔</span><span class="sxs-lookup"><span data-stu-id="7ce07-124">bincirc - binary with circular logging</span></span>
- <span data-ttu-id="7ce07-125">csv-逗點分隔值</span><span class="sxs-lookup"><span data-stu-id="7ce07-125">csv - Comma-separated values</span></span>
- <span data-ttu-id="7ce07-126">tsv-Tab 分隔值</span><span class="sxs-lookup"><span data-stu-id="7ce07-126">tsv - Tab-separated values</span></span>
- <span data-ttu-id="7ce07-127">sql-SQL database</span><span class="sxs-lookup"><span data-stu-id="7ce07-127">sql - SQL database</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: bin, bincirc, csv, tsv, sql

Required: False
Position: Named
Default value: bin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce07-128">-MaxBuffers</span><span class="sxs-lookup"><span data-stu-id="7ce07-128">-MaxBuffers</span></span>
<span data-ttu-id="7ce07-129">設定事件追蹤會話緩衝區的最大數目。</span><span class="sxs-lookup"><span data-stu-id="7ce07-129">Sets the maximum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce07-130">-MaxLogFileSizeInMB</span><span class="sxs-lookup"><span data-stu-id="7ce07-130">-MaxLogFileSizeInMB</span></span>
<span data-ttu-id="7ce07-131">將記錄檔大小上限設定為 mb (MB) 或 SQL 記錄檔的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="7ce07-131">Sets the maximum log file size in megabytes (MB) or number of records for SQL logs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0 (no limit)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce07-132">-MinBuffers</span><span class="sxs-lookup"><span data-stu-id="7ce07-132">-MinBuffers</span></span>
<span data-ttu-id="7ce07-133">設定事件追蹤會話緩衝區的最小數目。</span><span class="sxs-lookup"><span data-stu-id="7ce07-133">Sets the minimum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce07-134">-OutputFilePath</span><span class="sxs-lookup"><span data-stu-id="7ce07-134">-OutputFilePath</span></span>
<span data-ttu-id="7ce07-135">輸出記錄檔的路徑，或 SQL 資料庫中的 DSN 和記錄集名稱。</span><span class="sxs-lookup"><span data-stu-id="7ce07-135">Path of the output log file or the DSN and log set name in a SQL database.</span></span> <span data-ttu-id="7ce07-136">預設路徑為 `$env:systemdrive\PerfLogs\Admin`。</span><span class="sxs-lookup"><span data-stu-id="7ce07-136">The default path is `$env:systemdrive\PerfLogs\Admin`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: $env:systemdrive\PerfLogs\Admin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce07-137">-ProviderFilePath</span><span class="sxs-lookup"><span data-stu-id="7ce07-137">-ProviderFilePath</span></span>
<span data-ttu-id="7ce07-138">列出要啟用的多個事件追蹤提供者的檔案。</span><span class="sxs-lookup"><span data-stu-id="7ce07-138">File listing multiple Event Trace providers to enable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce07-139">-SessionName</span><span class="sxs-lookup"><span data-stu-id="7ce07-139">-SessionName</span></span>
<span data-ttu-id="7ce07-140">事件追蹤會話的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ce07-140">The name of the Event Trace session.</span></span> <span data-ttu-id="7ce07-141">若要停止追蹤會話，您必須知道會話名稱。</span><span class="sxs-lookup"><span data-stu-id="7ce07-141">To stop a trace session you must know the session name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ce07-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7ce07-142">CommonParameters</span></span>

<span data-ttu-id="7ce07-143">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="7ce07-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7ce07-144">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="7ce07-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7ce07-145">輸入</span><span class="sxs-lookup"><span data-stu-id="7ce07-145">INPUTS</span></span>

### <span data-ttu-id="7ce07-146">無</span><span class="sxs-lookup"><span data-stu-id="7ce07-146">None</span></span>

## <span data-ttu-id="7ce07-147">輸出</span><span class="sxs-lookup"><span data-stu-id="7ce07-147">OUTPUTS</span></span>

### <span data-ttu-id="7ce07-148">System.Object</span><span class="sxs-lookup"><span data-stu-id="7ce07-148">System.Object</span></span>

## <span data-ttu-id="7ce07-149">注意</span><span class="sxs-lookup"><span data-stu-id="7ce07-149">NOTES</span></span>

## <span data-ttu-id="7ce07-150">相關連結</span><span class="sxs-lookup"><span data-stu-id="7ce07-150">RELATED LINKS</span></span>

[<span data-ttu-id="7ce07-151">事件追蹤</span><span class="sxs-lookup"><span data-stu-id="7ce07-151">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="7ce07-152">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="7ce07-152">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="7ce07-153">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="7ce07-153">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="7ce07-154">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="7ce07-154">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="7ce07-155">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="7ce07-155">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="7ce07-156">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="7ce07-156">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)