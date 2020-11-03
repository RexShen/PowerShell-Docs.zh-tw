---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: ad9e3daa7d67fc2bec6fa19a873573ce33dc609d
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208472"
---
# <span data-ttu-id="d8bdb-103">Write-Error</span><span class="sxs-lookup"><span data-stu-id="d8bdb-103">Write-Error</span></span>

## <span data-ttu-id="d8bdb-104">概要</span><span class="sxs-lookup"><span data-stu-id="d8bdb-104">SYNOPSIS</span></span>
<span data-ttu-id="d8bdb-105">將物件寫入錯誤串流。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-105">Writes an object to the error stream.</span></span>

## <span data-ttu-id="d8bdb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8bdb-106">SYNTAX</span></span>

### <span data-ttu-id="d8bdb-107">NoException (預設值)</span><span class="sxs-lookup"><span data-stu-id="d8bdb-107">NoException (Default)</span></span>

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="d8bdb-108">WithException</span><span class="sxs-lookup"><span data-stu-id="d8bdb-108">WithException</span></span>

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="d8bdb-109">ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="d8bdb-109">ErrorRecord</span></span>

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## <span data-ttu-id="d8bdb-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d8bdb-110">DESCRIPTION</span></span>

<span data-ttu-id="d8bdb-111">Cmdlet 會宣告 `Write-Error` 非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-111">The `Write-Error` cmdlet declares a non-terminating error.</span></span> <span data-ttu-id="d8bdb-112">根據預設，錯誤會透過錯誤串流連同輸出傳送至要顯示的主機程式。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-112">By default, errors are sent in the error stream to the host program to be displayed, along with output.</span></span>

<span data-ttu-id="d8bdb-113">若要寫入非終止錯誤，請輸入錯誤訊息字串、 **ErrorRecord** 物件，或 **Exception** 物件。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-113">To write a non-terminating error, enter an error message string, an **ErrorRecord** object, or an **Exception** object.</span></span> <span data-ttu-id="d8bdb-114">使用的其他參數 `Write-Error` 填入錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-114">Use the other parameters of `Write-Error` to populate the error record.</span></span>

<span data-ttu-id="d8bdb-115">非終止錯誤會將錯誤寫入錯誤串流，但是不會停止命令處理。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-115">Non-terminating errors write an error to the error stream, but they do not stop command processing.</span></span>
<span data-ttu-id="d8bdb-116">如果在輸入項目集合中的一個項目上宣告非終止錯誤，命令就會繼續處理集合中的其他項目。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-116">If a non-terminating error is declared on one item in a collection of input items, the command continues to process the other items in the collection.</span></span>

<span data-ttu-id="d8bdb-117">若要宣告終止錯誤，請使用 `Throw` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-117">To declare a terminating error, use the `Throw` keyword.</span></span>
<span data-ttu-id="d8bdb-118">如需詳細資訊，請參閱 [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-118">For more information, see [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span></span>

## <span data-ttu-id="d8bdb-119">範例</span><span class="sxs-lookup"><span data-stu-id="d8bdb-119">EXAMPLES</span></span>

### <span data-ttu-id="d8bdb-120">範例1：寫入 RegistryKey 物件的錯誤</span><span class="sxs-lookup"><span data-stu-id="d8bdb-120">Example 1: Write an error for RegistryKey object</span></span>

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

<span data-ttu-id="d8bdb-121">此命令會在 `Get-ChildItem` Cmdlet 傳回 `Microsoft.Win32.RegistryKey` 物件（例如 `HKLM:` PowerShell 登錄提供者的或磁片磁碟機中的物件）時，宣告非終止錯誤 `HKCU:` 。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-121">This command declares a non-terminating error when the `Get-ChildItem` cmdlet returns a `Microsoft.Win32.RegistryKey` object, such as the objects in the `HKLM:` or `HKCU:` drives of the PowerShell Registry provider.</span></span>

### <span data-ttu-id="d8bdb-122">範例2：將錯誤訊息寫入主控台</span><span class="sxs-lookup"><span data-stu-id="d8bdb-122">Example 2: Write an error message to the console</span></span>

```powershell
Write-Error "Access denied."
```

<span data-ttu-id="d8bdb-123">此命令宣告非終止錯誤，並寫入「拒絕存取」錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-123">This command declares a non-terminating error and writes an "Access denied" error.</span></span> <span data-ttu-id="d8bdb-124">此命令使用 **Message** 參數指定訊息，但是省略選擇性的 **Message** 參數名稱。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-124">The command uses the **Message** parameter to specify the message, but omits the optional **Message** parameter name.</span></span>

### <span data-ttu-id="d8bdb-125">範例3：將錯誤寫入主控台並指定類別目錄</span><span class="sxs-lookup"><span data-stu-id="d8bdb-125">Example 3: Write an error to the console and specify the category</span></span>

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

<span data-ttu-id="d8bdb-126">此命令宣告非終止錯誤，並指定錯誤類別。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-126">This command declares a non-terminating error and specifies an error category.</span></span>

### <span data-ttu-id="d8bdb-127">範例4：使用 Exception 物件撰寫錯誤</span><span class="sxs-lookup"><span data-stu-id="d8bdb-127">Example 4: Write an error using an Exception object</span></span>

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

<span data-ttu-id="d8bdb-128">此命令使用 **Exception** 物件宣告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-128">This command uses an **Exception** object to declare a non-terminating error.</span></span>

<span data-ttu-id="d8bdb-129">第一個命令使用雜湊表建立 **System.Exception** 物件。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-129">The first command uses a hash table to create the **System.Exception** object.</span></span> <span data-ttu-id="d8bdb-130">它會將例外狀況物件儲存在 `$E` 變數中。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-130">It saves the exception object in the `$E` variable.</span></span> <span data-ttu-id="d8bdb-131">您可以使用雜湊表建立具有 Null 建構函式類型的任何物件。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-131">You can use a hash table to create any object of a type that has a null constructor.</span></span>

<span data-ttu-id="d8bdb-132">第二個命令會使用 `Write-Error` Cmdlet 來宣告非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-132">The second command uses the `Write-Error` cmdlet to declare a non-terminating error.</span></span> <span data-ttu-id="d8bdb-133">**Exception** 參數的值是變數中的 **exception** 物件 `$E` 。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-133">The value of the **Exception** parameter is the **Exception** object in the `$E` variable.</span></span>

## <span data-ttu-id="d8bdb-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8bdb-134">PARAMETERS</span></span>

### <span data-ttu-id="d8bdb-135">-Category</span><span class="sxs-lookup"><span data-stu-id="d8bdb-135">-Category</span></span>

<span data-ttu-id="d8bdb-136">指定錯誤的類別。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-136">Specifies the category of the error.</span></span> <span data-ttu-id="d8bdb-137">預設值為 **NotSpecified** 。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-137">The default value is **NotSpecified** .</span></span> <span data-ttu-id="d8bdb-138">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="d8bdb-138">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d8bdb-139">NotSpecified</span><span class="sxs-lookup"><span data-stu-id="d8bdb-139">NotSpecified</span></span>
- <span data-ttu-id="d8bdb-140">OpenError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-140">OpenError</span></span>
- <span data-ttu-id="d8bdb-141">CloseError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-141">CloseError</span></span>
- <span data-ttu-id="d8bdb-142">DeviceError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-142">DeviceError</span></span>
- <span data-ttu-id="d8bdb-143">DeadlockDetected</span><span class="sxs-lookup"><span data-stu-id="d8bdb-143">DeadlockDetected</span></span>
- <span data-ttu-id="d8bdb-144">InvalidArgument</span><span class="sxs-lookup"><span data-stu-id="d8bdb-144">InvalidArgument</span></span>
- <span data-ttu-id="d8bdb-145">InvalidData</span><span class="sxs-lookup"><span data-stu-id="d8bdb-145">InvalidData</span></span>
- <span data-ttu-id="d8bdb-146">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="d8bdb-146">InvalidOperation</span></span>
- <span data-ttu-id="d8bdb-147">InvalidResult</span><span class="sxs-lookup"><span data-stu-id="d8bdb-147">InvalidResult</span></span>
- <span data-ttu-id="d8bdb-148">InvalidType</span><span class="sxs-lookup"><span data-stu-id="d8bdb-148">InvalidType</span></span>
- <span data-ttu-id="d8bdb-149">MetadataError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-149">MetadataError</span></span>
- <span data-ttu-id="d8bdb-150">NotImplemented</span><span class="sxs-lookup"><span data-stu-id="d8bdb-150">NotImplemented</span></span>
- <span data-ttu-id="d8bdb-151">NotInstalled</span><span class="sxs-lookup"><span data-stu-id="d8bdb-151">NotInstalled</span></span>
- <span data-ttu-id="d8bdb-152">ObjectNotFound</span><span class="sxs-lookup"><span data-stu-id="d8bdb-152">ObjectNotFound</span></span>
- <span data-ttu-id="d8bdb-153">OperationStopped</span><span class="sxs-lookup"><span data-stu-id="d8bdb-153">OperationStopped</span></span>
- <span data-ttu-id="d8bdb-154">OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="d8bdb-154">OperationTimeout</span></span>
- <span data-ttu-id="d8bdb-155">SyntaxError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-155">SyntaxError</span></span>
- <span data-ttu-id="d8bdb-156">ParserError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-156">ParserError</span></span>
- <span data-ttu-id="d8bdb-157">PermissionDenied</span><span class="sxs-lookup"><span data-stu-id="d8bdb-157">PermissionDenied</span></span>
- <span data-ttu-id="d8bdb-158">ResourceBusy</span><span class="sxs-lookup"><span data-stu-id="d8bdb-158">ResourceBusy</span></span>
- <span data-ttu-id="d8bdb-159">ResourceExists</span><span class="sxs-lookup"><span data-stu-id="d8bdb-159">ResourceExists</span></span>
- <span data-ttu-id="d8bdb-160">ResourceUnavailable</span><span class="sxs-lookup"><span data-stu-id="d8bdb-160">ResourceUnavailable</span></span>
- <span data-ttu-id="d8bdb-161">ReadError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-161">ReadError</span></span>
- <span data-ttu-id="d8bdb-162">WriteError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-162">WriteError</span></span>
- <span data-ttu-id="d8bdb-163">FromStdErr</span><span class="sxs-lookup"><span data-stu-id="d8bdb-163">FromStdErr</span></span>
- <span data-ttu-id="d8bdb-164">SecurityError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-164">SecurityError</span></span>
- <span data-ttu-id="d8bdb-165">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-165">ProtocolError</span></span>
- <span data-ttu-id="d8bdb-166">ConnectionError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-166">ConnectionError</span></span>
- <span data-ttu-id="d8bdb-167">AuthenticationError</span><span class="sxs-lookup"><span data-stu-id="d8bdb-167">AuthenticationError</span></span>
- <span data-ttu-id="d8bdb-168">LimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="d8bdb-168">LimitsExceeded</span></span>
- <span data-ttu-id="d8bdb-169">QuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="d8bdb-169">QuotaExceeded</span></span>
- <span data-ttu-id="d8bdb-170">NotEnabled</span><span class="sxs-lookup"><span data-stu-id="d8bdb-170">NotEnabled</span></span>

<span data-ttu-id="d8bdb-171">如需錯誤類別的詳細資訊，請參閱 [ErrorCategory 列舉](https://go.microsoft.com/fwlink/?LinkId=143600)。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-171">For information about the error categories, see [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600).</span></span>

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-172">-CategoryActivity</span><span class="sxs-lookup"><span data-stu-id="d8bdb-172">-CategoryActivity</span></span>

<span data-ttu-id="d8bdb-173">指定造成錯誤的動作。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-173">Specifies the action that caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-174">-CategoryReason</span><span class="sxs-lookup"><span data-stu-id="d8bdb-174">-CategoryReason</span></span>

<span data-ttu-id="d8bdb-175">指定活動造成錯誤的方式或原因。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-175">Specifies how or why the activity caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-176">-CategoryTargetName</span><span class="sxs-lookup"><span data-stu-id="d8bdb-176">-CategoryTargetName</span></span>

<span data-ttu-id="d8bdb-177">指定發生錯誤時正在處理的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-177">Specifies the name of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-178">-CategoryTargetType</span><span class="sxs-lookup"><span data-stu-id="d8bdb-178">-CategoryTargetType</span></span>

<span data-ttu-id="d8bdb-179">指定發生錯誤時正在處理的物件類型。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-179">Specifies the type of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-180">-ErrorId</span><span class="sxs-lookup"><span data-stu-id="d8bdb-180">-ErrorId</span></span>

<span data-ttu-id="d8bdb-181">指定識別錯誤的識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-181">Specifies an ID string to identify the error.</span></span> <span data-ttu-id="d8bdb-182">字串對於每個錯誤必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-182">The string should be unique to the error.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-183">-ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="d8bdb-183">-ErrorRecord</span></span>

<span data-ttu-id="d8bdb-184">指定表示錯誤的錯誤記錄物件。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-184">Specifies an error record object that represents the error.</span></span> <span data-ttu-id="d8bdb-185">使用物件的屬性可描述錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-185">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="d8bdb-186">若要建立錯誤記錄物件，請使用 `New-Object` Cmdlet 或從自動變數中的陣列取得錯誤記錄物件 `$Error` 。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-186">To create an error record object, use the `New-Object` cmdlet or get an error record object from the array in the `$Error` automatic variable.</span></span>

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-187">-Exception</span><span class="sxs-lookup"><span data-stu-id="d8bdb-187">-Exception</span></span>

<span data-ttu-id="d8bdb-188">指定表示錯誤的例外狀況物件。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-188">Specifies an exception object that represents the error.</span></span> <span data-ttu-id="d8bdb-189">使用物件的屬性可描述錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-189">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="d8bdb-190">若要建立例外狀況物件，請使用雜湊表或使用 `New-Object` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-190">To create an exception object, use a hash table or use the `New-Object` cmdlet.</span></span>

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-191">-Message</span><span class="sxs-lookup"><span data-stu-id="d8bdb-191">-Message</span></span>

<span data-ttu-id="d8bdb-192">指定錯誤的訊息文字。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-192">Specifies the message text of the error.</span></span> <span data-ttu-id="d8bdb-193">如果文字包含空格或特殊字元，請將它括在引號中。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-193">If the text includes spaces or special characters, enclose it in quotation marks.</span></span> <span data-ttu-id="d8bdb-194">您也可以使用管線將訊息字串傳送至 `Write-Error` 。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-194">You can also pipe a message string to `Write-Error`.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-195">-RecommendedAction</span><span class="sxs-lookup"><span data-stu-id="d8bdb-195">-RecommendedAction</span></span>

<span data-ttu-id="d8bdb-196">指定使用者應該採取以解決或避免錯誤的動作。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-196">Specifies the action that the user should take to resolve or prevent the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-197">-TargetObject</span><span class="sxs-lookup"><span data-stu-id="d8bdb-197">-TargetObject</span></span>

<span data-ttu-id="d8bdb-198">指定發生錯誤時正在處理的物件。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-198">Specifies the object that was being processed when the error occurred.</span></span> <span data-ttu-id="d8bdb-199">輸入物件、包含物件的變數，或可取得物件的命令。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-199">Enter the object, a variable that contains the object, or a command that gets the object.</span></span>

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8bdb-200">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8bdb-200">CommonParameters</span></span>

<span data-ttu-id="d8bdb-201">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-201">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8bdb-202">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-202">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8bdb-203">輸入</span><span class="sxs-lookup"><span data-stu-id="d8bdb-203">INPUTS</span></span>

### <span data-ttu-id="d8bdb-204">System.String</span><span class="sxs-lookup"><span data-stu-id="d8bdb-204">System.String</span></span>

<span data-ttu-id="d8bdb-205">您可以使用管線將包含錯誤訊息的字串傳送至 `Write-Error` 。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-205">You can pipe a string that contains an error message to `Write-Error`.</span></span>

## <span data-ttu-id="d8bdb-206">輸出</span><span class="sxs-lookup"><span data-stu-id="d8bdb-206">OUTPUTS</span></span>

### <span data-ttu-id="d8bdb-207">Error 物件</span><span class="sxs-lookup"><span data-stu-id="d8bdb-207">Error object</span></span>

<span data-ttu-id="d8bdb-208">`Write-Error` 只寫入至錯誤資料流程。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-208">`Write-Error` writes only to the error stream.</span></span> <span data-ttu-id="d8bdb-209">它不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-209">It does not return any objects.</span></span>

## <span data-ttu-id="d8bdb-210">注意</span><span class="sxs-lookup"><span data-stu-id="d8bdb-210">NOTES</span></span>

<span data-ttu-id="d8bdb-211">`Write-Error` 不會變更自動變數的值 `$?` ，因此不會發出終止錯誤條件的信號。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-211">`Write-Error` does not change the value of the `$?` automatic variable, therefore it does not signal a terminating error condition.</span></span> <span data-ttu-id="d8bdb-212">若要指示終止錯誤，請使用 [$PSCmdlet. WriteError ( # B1 ](/dotnet/api/system.management.automation.cmdlet.writeerror) 方法。</span><span class="sxs-lookup"><span data-stu-id="d8bdb-212">To signal a terminating error, use the [$PSCmdlet.WriteError()](/dotnet/api/system.management.automation.cmdlet.writeerror) method.</span></span>

## <span data-ttu-id="d8bdb-213">相關連結</span><span class="sxs-lookup"><span data-stu-id="d8bdb-213">RELATED LINKS</span></span>

[<span data-ttu-id="d8bdb-214">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="d8bdb-214">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="d8bdb-215">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="d8bdb-215">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="d8bdb-216">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="d8bdb-216">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="d8bdb-217">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="d8bdb-217">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="d8bdb-218">Write-Host</span><span class="sxs-lookup"><span data-stu-id="d8bdb-218">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="d8bdb-219">Write-Output</span><span class="sxs-lookup"><span data-stu-id="d8bdb-219">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="d8bdb-220">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="d8bdb-220">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="d8bdb-221">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="d8bdb-221">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="d8bdb-222">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="d8bdb-222">Write-Warning</span></span>](Write-Warning.md)
