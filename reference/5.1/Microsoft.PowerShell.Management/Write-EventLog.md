---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: 4044453cb46b407344619f1edd3227213bf67250
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388241"
---
# <span data-ttu-id="20b8c-103">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="20b8c-103">Write-EventLog</span></span>

## <span data-ttu-id="20b8c-104">概要</span><span class="sxs-lookup"><span data-stu-id="20b8c-104">SYNOPSIS</span></span>
<span data-ttu-id="20b8c-105">將事件寫入事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="20b8c-105">Writes an event to an event log.</span></span>

## <span data-ttu-id="20b8c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20b8c-106">SYNTAX</span></span>

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## <span data-ttu-id="20b8c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="20b8c-107">DESCRIPTION</span></span>
<span data-ttu-id="20b8c-108">Cmdlet 會將 `Write-EventLog` 事件寫入事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="20b8c-108">The `Write-EventLog` cmdlet writes an event to an event log.</span></span>

<span data-ttu-id="20b8c-109">若要將事件寫入事件記錄檔，事件記錄檔必須存在於電腦上，並且必須為事件記錄檔登錄來源。</span><span class="sxs-lookup"><span data-stu-id="20b8c-109">To write an event to an event log, the event log must exist on the computer and the source must be registered for the event log.</span></span>

<span data-ttu-id="20b8c-110">包含 **eventlog** 名詞 ( **eventlog** Cmdlet 的指令程式) 只會在傳統事件記錄檔上運作。</span><span class="sxs-lookup"><span data-stu-id="20b8c-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span> <span data-ttu-id="20b8c-111">若要在 Windows Vista 和更新版本的 Windows 作業系統中，從使用 Windows 事件記錄檔技術的記錄檔中取得事件，請使用 `Get-WinEvent` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="20b8c-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the `Get-WinEvent` cmdlet.</span></span>

## <span data-ttu-id="20b8c-112">範例</span><span class="sxs-lookup"><span data-stu-id="20b8c-112">EXAMPLES</span></span>

### <span data-ttu-id="20b8c-113">範例 1︰將事件寫入應用程式事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="20b8c-113">Example 1: Write an event to the Application event log</span></span>

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

<span data-ttu-id="20b8c-114">此命令將事件從 MyApp 來源寫入 Application 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="20b8c-114">This command writes an event from the MyApp source to the Application event log.</span></span>

### <span data-ttu-id="20b8c-115">範例 2︰將事件寫入遠端電腦的應用程式事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="20b8c-115">Example 2: Write an event to the Application event log of a remote computer</span></span>

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

<span data-ttu-id="20b8c-116">此命令將事件從 MyApp 來源寫入 Server01 遠端電腦上的 Application 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="20b8c-116">This command writes an event from the MyApp source to the Application event log on the Server01 remote computer.</span></span>

## <span data-ttu-id="20b8c-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="20b8c-117">PARAMETERS</span></span>

### <span data-ttu-id="20b8c-118">-Category</span><span class="sxs-lookup"><span data-stu-id="20b8c-118">-Category</span></span>

<span data-ttu-id="20b8c-119">指定事件的工作類別。</span><span class="sxs-lookup"><span data-stu-id="20b8c-119">Specifies a task category for the event.</span></span> <span data-ttu-id="20b8c-120">輸入與事件記錄檔之類別訊息檔案中的字串關聯的整數。</span><span class="sxs-lookup"><span data-stu-id="20b8c-120">Enter an integer that is associated with the strings in the category message file for the event log.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20b8c-121">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="20b8c-121">-ComputerName</span></span>

<span data-ttu-id="20b8c-122">指定遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="20b8c-122">Specifies a remote computer.</span></span> <span data-ttu-id="20b8c-123">預設是本機電腦。</span><span class="sxs-lookup"><span data-stu-id="20b8c-123">The default is the local computer.</span></span>

<span data-ttu-id="20b8c-124">輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="20b8c-124">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="20b8c-125">此參數不必依賴 Windows PowerShell 遠端功能。</span><span class="sxs-lookup"><span data-stu-id="20b8c-125">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="20b8c-126">**ComputerName** `Get-EventLog` 即使您的電腦未設定為執行遠端命令，您也可以使用此 Cmdlet 的 ComputerName 參數。</span><span class="sxs-lookup"><span data-stu-id="20b8c-126">You can use the **ComputerName** parameter of the `Get-EventLog` cmdlet even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20b8c-127">-EntryType</span><span class="sxs-lookup"><span data-stu-id="20b8c-127">-EntryType</span></span>

<span data-ttu-id="20b8c-128">指定事件的項目類型。</span><span class="sxs-lookup"><span data-stu-id="20b8c-128">Specifies the entry type of the event.</span></span> <span data-ttu-id="20b8c-129">這個參數可接受的值如下︰Error、Warning、Information、SuccessAudit 和 FailureAudit。</span><span class="sxs-lookup"><span data-stu-id="20b8c-129">The acceptable values for this parameter are: Error, Warning, Information, SuccessAudit, and FailureAudit.</span></span> <span data-ttu-id="20b8c-130">預設值為 Information。</span><span class="sxs-lookup"><span data-stu-id="20b8c-130">The default value is Information.</span></span>

<span data-ttu-id="20b8c-131">如需值的描述，請參閱 [EventLogEntryType 列舉](/dotnet/api/system.diagnostics.eventlogentrytype)。</span><span class="sxs-lookup"><span data-stu-id="20b8c-131">For a description of the values, see [EventLogEntryType Enumeration](/dotnet/api/system.diagnostics.eventlogentrytype).</span></span>

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20b8c-132">-EventId</span><span class="sxs-lookup"><span data-stu-id="20b8c-132">-EventId</span></span>

<span data-ttu-id="20b8c-133">指定事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="20b8c-133">Specifies the event identifier.</span></span> <span data-ttu-id="20b8c-134">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="20b8c-134">This parameter is required.</span></span> <span data-ttu-id="20b8c-135">適用於 **EventId** 參數的最大值為 65535。</span><span class="sxs-lookup"><span data-stu-id="20b8c-135">The maximum value for the **EventId** parameter is 65535.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20b8c-136">-LogName</span><span class="sxs-lookup"><span data-stu-id="20b8c-136">-LogName</span></span>

<span data-ttu-id="20b8c-137">指定要在其中寫入事件之記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="20b8c-137">Specifies the name of the log to which the event is written.</span></span> <span data-ttu-id="20b8c-138">輸入記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="20b8c-138">Enter the log name.</span></span> <span data-ttu-id="20b8c-139">記錄檔名稱是 **Log** 屬性的值，而不是 **LogDisplayName** 的值。</span><span class="sxs-lookup"><span data-stu-id="20b8c-139">The log name is the value of the **Log** property, not the **LogDisplayName**.</span></span> <span data-ttu-id="20b8c-140">不允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="20b8c-140">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="20b8c-141">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="20b8c-141">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20b8c-142">-Message</span><span class="sxs-lookup"><span data-stu-id="20b8c-142">-Message</span></span>

<span data-ttu-id="20b8c-143">指定事件訊息。</span><span class="sxs-lookup"><span data-stu-id="20b8c-143">Specifies the event message.</span></span> <span data-ttu-id="20b8c-144">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="20b8c-144">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20b8c-145">-RawData</span><span class="sxs-lookup"><span data-stu-id="20b8c-145">-RawData</span></span>

<span data-ttu-id="20b8c-146">指定與事件關聯的二進位資料 (單位為位元組)。</span><span class="sxs-lookup"><span data-stu-id="20b8c-146">Specifies the binary data that is associated with the event, in bytes.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20b8c-147">-Source</span><span class="sxs-lookup"><span data-stu-id="20b8c-147">-Source</span></span>

<span data-ttu-id="20b8c-148">指定事件來源，這通常是正在將事件寫入記錄檔之應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="20b8c-148">Specifies the event source, which is typically the name of the application that is writing the event to the log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20b8c-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20b8c-149">CommonParameters</span></span>

<span data-ttu-id="20b8c-150">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="20b8c-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20b8c-151">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="20b8c-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20b8c-152">輸入</span><span class="sxs-lookup"><span data-stu-id="20b8c-152">INPUTS</span></span>

### <span data-ttu-id="20b8c-153">無</span><span class="sxs-lookup"><span data-stu-id="20b8c-153">None</span></span>
<span data-ttu-id="20b8c-154">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="20b8c-154">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="20b8c-155">輸出</span><span class="sxs-lookup"><span data-stu-id="20b8c-155">OUTPUTS</span></span>

### <span data-ttu-id="20b8c-156">System.Diagnostics.EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="20b8c-156">System.Diagnostics.EventLogEntry</span></span>
<span data-ttu-id="20b8c-157">這個 Cmdlet 會傳回代表記錄檔中事件的物件。</span><span class="sxs-lookup"><span data-stu-id="20b8c-157">This cmdlet returns objects that represents the events in the logs.</span></span>

## <span data-ttu-id="20b8c-158">注意</span><span class="sxs-lookup"><span data-stu-id="20b8c-158">NOTES</span></span>

<span data-ttu-id="20b8c-159">若要使用 `Write-EventLog` ，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="20b8c-159">To use `Write-EventLog`, start Windows PowerShell by using the Run as administrator option.</span></span>

## <span data-ttu-id="20b8c-160">相關連結</span><span class="sxs-lookup"><span data-stu-id="20b8c-160">RELATED LINKS</span></span>

[<span data-ttu-id="20b8c-161">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="20b8c-161">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="20b8c-162">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="20b8c-162">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="20b8c-163">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="20b8c-163">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="20b8c-164">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="20b8c-164">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="20b8c-165">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="20b8c-165">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="20b8c-166">Show-EventLog</span><span class="sxs-lookup"><span data-stu-id="20b8c-166">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="20b8c-167">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="20b8c-167">Write-EventLog</span></span>](Write-EventLog.md)
