---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 00e9b3bc18d24fe252aee20eb77af0b5ad99468e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202188"
---
# <span data-ttu-id="d91c6-103">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="d91c6-103">Set-TraceSource</span></span>

## <span data-ttu-id="d91c6-104">概要</span><span class="sxs-lookup"><span data-stu-id="d91c6-104">SYNOPSIS</span></span>
<span data-ttu-id="d91c6-105">設定、啟動和停止 PowerShell 元件的追蹤。</span><span class="sxs-lookup"><span data-stu-id="d91c6-105">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="d91c6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d91c6-106">SYNTAX</span></span>

### <span data-ttu-id="d91c6-107">optionsSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="d91c6-107">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="d91c6-108">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="d91c6-108">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d91c6-109">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="d91c6-109">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="d91c6-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d91c6-110">DESCRIPTION</span></span>

<span data-ttu-id="d91c6-111">**TraceSource 指令程式會設定** 、啟動和停止 PowerShell 元件的追蹤。</span><span class="sxs-lookup"><span data-stu-id="d91c6-111">The **Set-TraceSource** cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span>
<span data-ttu-id="d91c6-112">您可以使用它來指定要追蹤的元件和傳送追蹤輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="d91c6-112">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="d91c6-113">範例</span><span class="sxs-lookup"><span data-stu-id="d91c6-113">EXAMPLES</span></span>

### <span data-ttu-id="d91c6-114">範例1：追蹤 ParameterBinding 元件</span><span class="sxs-lookup"><span data-stu-id="d91c6-114">Example 1: Trace the ParameterBinding component</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="d91c6-115">此命令會啟動 PowerShell ParameterBinding 元件的追蹤。</span><span class="sxs-lookup"><span data-stu-id="d91c6-115">This command starts tracing for the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="d91c6-116">它會使用 *Name* 參數來指定追蹤來源、選取 ExecutionFlow 追蹤事件的 *Option* 參數，並使用 *PSHost* 參數來選取將輸出傳送至主控台的 PowerShell 主機接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d91c6-116">It uses the *Name* parameter to specify the trace source, the *Option* parameter to select the ExecutionFlow trace events, and the *PSHost* parameter to select the PowerShell host listener, which sends the output to the console.</span></span>
<span data-ttu-id="d91c6-117">*ListenerOption* 參數會將 ProcessID 和 TimeStamp 值加入到追蹤訊息前置詞。</span><span class="sxs-lookup"><span data-stu-id="d91c6-117">The *ListenerOption* parameter adds the ProcessID and TimeStamp values to the trace message prefix.</span></span>

### <span data-ttu-id="d91c6-118">範例2：停止追蹤</span><span class="sxs-lookup"><span data-stu-id="d91c6-118">Example 2: Stop a trace</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="d91c6-119">此命令會停止追蹤 PowerShell 的 ParameterBinding 元件。</span><span class="sxs-lookup"><span data-stu-id="d91c6-119">This command stops the trace of the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="d91c6-120">它會使用 *Name* 參數來識別正在追蹤的元件，以及使用 *RemoveListener* 參數來識別追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d91c6-120">It uses the *Name* parameter to identify the component that was being traced and the *RemoveListener* parameter to identify the trace listener.</span></span>

## <span data-ttu-id="d91c6-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d91c6-121">PARAMETERS</span></span>

### <span data-ttu-id="d91c6-122">-Debugger</span><span class="sxs-lookup"><span data-stu-id="d91c6-122">-Debugger</span></span>

<span data-ttu-id="d91c6-123">指出此 Cmdlet 會將追蹤輸出傳送至偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d91c6-123">Indicates that the cmdlet sends the trace output to the debugger.</span></span>
<span data-ttu-id="d91c6-124">您可以在任何使用者模式或核心模式偵錯工具或 Microsoft Visual Studio 中檢視輸出。</span><span class="sxs-lookup"><span data-stu-id="d91c6-124">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span>
<span data-ttu-id="d91c6-125">這個參數也會選取預設的追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d91c6-125">This parameter also selects the default trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d91c6-126">-FilePath</span><span class="sxs-lookup"><span data-stu-id="d91c6-126">-FilePath</span></span>

<span data-ttu-id="d91c6-127">指定此 Cmdlet 將追蹤輸出傳送至其中的檔案。</span><span class="sxs-lookup"><span data-stu-id="d91c6-127">Specifies a file that this cmdlet sends the trace output to.</span></span>
<span data-ttu-id="d91c6-128">這個參數也會選取檔案追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d91c6-128">This parameter also selects the file trace listener.</span></span>
<span data-ttu-id="d91c6-129">如果您使用這個參數來啟動追蹤，請使用 *RemoveFileListener* 參數來停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="d91c6-129">If you use this parameter to start the trace, use the *RemoveFileListener* parameter to stop the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d91c6-130">-Force</span><span class="sxs-lookup"><span data-stu-id="d91c6-130">-Force</span></span>

<span data-ttu-id="d91c6-131">指出此 Cmdlet 會覆寫唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="d91c6-131">Indicates that the cmdlet overwrites a read-only file.</span></span>
<span data-ttu-id="d91c6-132">搭配 *FilePath* 參數使用。</span><span class="sxs-lookup"><span data-stu-id="d91c6-132">Use with the *FilePath* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d91c6-133">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="d91c6-133">-ListenerOption</span></span>

<span data-ttu-id="d91c6-134">在輸出中，將選擇性資料指定為每個追蹤訊息的前置詞。</span><span class="sxs-lookup"><span data-stu-id="d91c6-134">Specifies optional data to the prefix of each trace message in the output.</span></span>
<span data-ttu-id="d91c6-135">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="d91c6-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d91c6-136">無</span><span class="sxs-lookup"><span data-stu-id="d91c6-136">None</span></span>
- <span data-ttu-id="d91c6-137">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="d91c6-137">LogicalOperationStack</span></span>
- <span data-ttu-id="d91c6-138">Datetime</span><span class="sxs-lookup"><span data-stu-id="d91c6-138">DateTime</span></span>
- <span data-ttu-id="d91c6-139">時間戳記</span><span class="sxs-lookup"><span data-stu-id="d91c6-139">Timestamp</span></span>
- <span data-ttu-id="d91c6-140">ProcessId</span><span class="sxs-lookup"><span data-stu-id="d91c6-140">ProcessId</span></span>
- <span data-ttu-id="d91c6-141">ThreadId</span><span class="sxs-lookup"><span data-stu-id="d91c6-141">ThreadId</span></span>
- <span data-ttu-id="d91c6-142">呼叫堆疊</span><span class="sxs-lookup"><span data-stu-id="d91c6-142">Callstack</span></span>

<span data-ttu-id="d91c6-143">預設值為 None。</span><span class="sxs-lookup"><span data-stu-id="d91c6-143">None is the default.</span></span>

<span data-ttu-id="d91c6-144">如果要指定多個選項，請以逗點加以區隔，但不含空格，並將其括在引號中，例如 "ProcessID,ThreadID"。</span><span class="sxs-lookup"><span data-stu-id="d91c6-144">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d91c6-145">-Name</span><span class="sxs-lookup"><span data-stu-id="d91c6-145">-Name</span></span>

<span data-ttu-id="d91c6-146">指定要追蹤的元件。</span><span class="sxs-lookup"><span data-stu-id="d91c6-146">Specifies which components are traced.</span></span>
<span data-ttu-id="d91c6-147">輸入每個元件的追蹤來源名稱。</span><span class="sxs-lookup"><span data-stu-id="d91c6-147">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="d91c6-148">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d91c6-148">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d91c6-149">-Option</span><span class="sxs-lookup"><span data-stu-id="d91c6-149">-Option</span></span>

<span data-ttu-id="d91c6-150">指定要追蹤的事件種類。</span><span class="sxs-lookup"><span data-stu-id="d91c6-150">Specifies the type of events that are traced.</span></span>
<span data-ttu-id="d91c6-151">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="d91c6-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d91c6-152">無</span><span class="sxs-lookup"><span data-stu-id="d91c6-152">None</span></span>
- <span data-ttu-id="d91c6-153">建構函式</span><span class="sxs-lookup"><span data-stu-id="d91c6-153">Constructor</span></span>
- <span data-ttu-id="d91c6-154">處置</span><span class="sxs-lookup"><span data-stu-id="d91c6-154">Dispose</span></span>
- <span data-ttu-id="d91c6-155">完成項</span><span class="sxs-lookup"><span data-stu-id="d91c6-155">Finalizer</span></span>
- <span data-ttu-id="d91c6-156">方法</span><span class="sxs-lookup"><span data-stu-id="d91c6-156">Method</span></span>
- <span data-ttu-id="d91c6-157">屬性</span><span class="sxs-lookup"><span data-stu-id="d91c6-157">Property</span></span>
- <span data-ttu-id="d91c6-158">委派</span><span class="sxs-lookup"><span data-stu-id="d91c6-158">Delegates</span></span>
- <span data-ttu-id="d91c6-159">事件</span><span class="sxs-lookup"><span data-stu-id="d91c6-159">Events</span></span>
- <span data-ttu-id="d91c6-160">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d91c6-160">Exception</span></span>
- <span data-ttu-id="d91c6-161">鎖定</span><span class="sxs-lookup"><span data-stu-id="d91c6-161">Lock</span></span>
- <span data-ttu-id="d91c6-162">錯誤</span><span class="sxs-lookup"><span data-stu-id="d91c6-162">Error</span></span>
- <span data-ttu-id="d91c6-163">Errors</span><span class="sxs-lookup"><span data-stu-id="d91c6-163">Errors</span></span>
- <span data-ttu-id="d91c6-164">警告</span><span class="sxs-lookup"><span data-stu-id="d91c6-164">Warning</span></span>
- <span data-ttu-id="d91c6-165">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="d91c6-165">Verbose</span></span>
- <span data-ttu-id="d91c6-166">WriteLine</span><span class="sxs-lookup"><span data-stu-id="d91c6-166">WriteLine</span></span>
- <span data-ttu-id="d91c6-167">資料</span><span class="sxs-lookup"><span data-stu-id="d91c6-167">Data</span></span>
- <span data-ttu-id="d91c6-168">範圍</span><span class="sxs-lookup"><span data-stu-id="d91c6-168">Scope</span></span>
- <span data-ttu-id="d91c6-169">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="d91c6-169">ExecutionFlow</span></span>
- <span data-ttu-id="d91c6-170">Assert</span><span class="sxs-lookup"><span data-stu-id="d91c6-170">Assert</span></span>
- <span data-ttu-id="d91c6-171">全部</span><span class="sxs-lookup"><span data-stu-id="d91c6-171">All</span></span>

<span data-ttu-id="d91c6-172">All 為預設值。</span><span class="sxs-lookup"><span data-stu-id="d91c6-172">All is the default.</span></span>

<span data-ttu-id="d91c6-173">下列的值為其他值的組合：</span><span class="sxs-lookup"><span data-stu-id="d91c6-173">The following values are combinations of other values:</span></span>

- <span data-ttu-id="d91c6-174">ExecutionFlow：(Constructor、Dispose、Finalizer、Method、Delegates、Events 及 Scope)</span><span class="sxs-lookup"><span data-stu-id="d91c6-174">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="d91c6-175">Data：(Constructor、Dispose、Finalizer、Property、Verbose 及 WriteLine)</span><span class="sxs-lookup"><span data-stu-id="d91c6-175">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="d91c6-176">Errors：(Error 和 Exception)。</span><span class="sxs-lookup"><span data-stu-id="d91c6-176">Errors: (Error and Exception).</span></span>

<span data-ttu-id="d91c6-177">如果要指定多個選項，請以逗點加以區隔，但不含空格，並將其括在引號中，例如 "Constructor,Dispose"。</span><span class="sxs-lookup"><span data-stu-id="d91c6-177">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d91c6-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="d91c6-178">-PassThru</span></span>

<span data-ttu-id="d91c6-179">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="d91c6-179">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="d91c6-180">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d91c6-180">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d91c6-181">-PSHost</span><span class="sxs-lookup"><span data-stu-id="d91c6-181">-PSHost</span></span>

<span data-ttu-id="d91c6-182">表示，此 Cmdlet 會將追蹤輸出傳送至 PowerShell 主機。</span><span class="sxs-lookup"><span data-stu-id="d91c6-182">ndicates that this cmdlet sends the trace output to the PowerShell host.</span></span>
<span data-ttu-id="d91c6-183">這個參數也會選取 PSHost 追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d91c6-183">This parameter also selects the PSHost trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d91c6-184">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="d91c6-184">-RemoveFileListener</span></span>

<span data-ttu-id="d91c6-185">藉由移除與指定檔案相關聯的檔案追蹤接聽程式來停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="d91c6-185">Stops the trace by removing the file trace listener associated with the specified file.</span></span>
<span data-ttu-id="d91c6-186">輸入追蹤輸出檔的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d91c6-186">Enter the path and file name of the trace output file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d91c6-187">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="d91c6-187">-RemoveListener</span></span>

<span data-ttu-id="d91c6-188">藉由移除追蹤接聽程式來停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="d91c6-188">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="d91c6-189">使用 *RemoveListener* 的下列值：</span><span class="sxs-lookup"><span data-stu-id="d91c6-189">Use the following values with *RemoveListener* :</span></span>

- <span data-ttu-id="d91c6-190">若要移除 PSHost (主控台) ，請輸入 `Host` 。</span><span class="sxs-lookup"><span data-stu-id="d91c6-190">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="d91c6-191">若要移除偵錯工具，請輸入 `Debug` 。</span><span class="sxs-lookup"><span data-stu-id="d91c6-191">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="d91c6-192">若要移除所有追蹤接聽程式，請輸入 `*` 。</span><span class="sxs-lookup"><span data-stu-id="d91c6-192">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="d91c6-193">若要移除檔案追蹤接聽程式，請使用 *RemoveFileListener* 參數。</span><span class="sxs-lookup"><span data-stu-id="d91c6-193">To remove the file trace listener, use the *RemoveFileListener* parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d91c6-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d91c6-194">CommonParameters</span></span>

<span data-ttu-id="d91c6-195">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d91c6-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d91c6-196">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d91c6-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d91c6-197">輸入</span><span class="sxs-lookup"><span data-stu-id="d91c6-197">INPUTS</span></span>

### <span data-ttu-id="d91c6-198">System.String</span><span class="sxs-lookup"><span data-stu-id="d91c6-198">System.String</span></span>

<span data-ttu-id="d91c6-199">您可以使用管線將包含名稱的字串傳送至 **TraceSource** 。</span><span class="sxs-lookup"><span data-stu-id="d91c6-199">You can pipe a string that contains a name to **Set-TraceSource** .</span></span>

## <span data-ttu-id="d91c6-200">輸出</span><span class="sxs-lookup"><span data-stu-id="d91c6-200">OUTPUTS</span></span>

### <span data-ttu-id="d91c6-201">無或 System.Management.Automation.PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="d91c6-201">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="d91c6-202">當您使用 *PassThru* 參數時， **TraceSource** 會產生代表追蹤會話的 **system.management.automation.pstracesource** 物件。</span><span class="sxs-lookup"><span data-stu-id="d91c6-202">When you use the *PassThru* parameter, **Set-TraceSource** generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span>
<span data-ttu-id="d91c6-203">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="d91c6-203">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d91c6-204">注意</span><span class="sxs-lookup"><span data-stu-id="d91c6-204">NOTES</span></span>

* <span data-ttu-id="d91c6-205">追蹤是開發人員用來偵錯及改善程式的方法。</span><span class="sxs-lookup"><span data-stu-id="d91c6-205">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="d91c6-206">當進行追蹤時，程式會產生有關內部處理中每個步驟的詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="d91c6-206">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="d91c6-207">PowerShell 追蹤 Cmdlet 是設計來協助 PowerShell 開發人員，但它們可供所有使用者使用。</span><span class="sxs-lookup"><span data-stu-id="d91c6-207">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span>
<span data-ttu-id="d91c6-208">它們可讓您監視 PowerShell 功能的幾乎每個層面。</span><span class="sxs-lookup"><span data-stu-id="d91c6-208">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="d91c6-209">追蹤來源是每個 PowerShell 元件的一部分，可管理追蹤並產生元件的追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="d91c6-209">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span>
<span data-ttu-id="d91c6-210">如果要追蹤元件，您必須識別其追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="d91c6-210">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="d91c6-211">追蹤接聽程式會接收追蹤的輸出，並將其顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="d91c6-211">A trace listener receives the output of the trace and displays it to the user.</span></span>
<span data-ttu-id="d91c6-212">您可以選擇將追蹤資料傳送至使用者模式或核心模式的偵錯工具、主控台、檔案，或從 **TraceListener** 類別衍生的自訂接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d91c6-212">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

* <span data-ttu-id="d91c6-213">若要啟動追蹤，請使用 *Name* 參數來指定追蹤來源和 *FilePath* 、 *偵錯工具* 或 *PSHost* 參數，以指定 (輸出) 目的地的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d91c6-213">To start a trace, use the *Name* parameter to specify a trace source and the *FilePath* , *Debugger* , or *PSHost* parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="d91c6-214">您可以使用 *Options* 參數來判斷所追蹤的事件種類，以及用來設定追蹤輸出的 *ListenerOption* 參數。</span><span class="sxs-lookup"><span data-stu-id="d91c6-214">Use the *Options* parameter to determine the types of events that are traced and the *ListenerOption* parameter to configure the trace output.</span></span>
* <span data-ttu-id="d91c6-215">若要變更追蹤的設定，請輸入 **TraceSource** 命令，就像開始追蹤一樣。</span><span class="sxs-lookup"><span data-stu-id="d91c6-215">To change the configuration of a trace, enter a **Set-TraceSource** command as you would to start a trace.</span></span> <span data-ttu-id="d91c6-216">PowerShell 辨識出追蹤來源已在追蹤中。</span><span class="sxs-lookup"><span data-stu-id="d91c6-216">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="d91c6-217">它會停止追蹤、新增設定，並啟動或重新啟動追蹤。</span><span class="sxs-lookup"><span data-stu-id="d91c6-217">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
* <span data-ttu-id="d91c6-218">若要停止追蹤，請使用 *RemoveListener* 參數。</span><span class="sxs-lookup"><span data-stu-id="d91c6-218">To stop a trace, use the *RemoveListener* parameter.</span></span> <span data-ttu-id="d91c6-219">若要停止使用檔案接聽程式的追蹤 (使用 *FilePath* 參數) 啟動的追蹤，請使用 *RemoveFileListener* 參數。</span><span class="sxs-lookup"><span data-stu-id="d91c6-219">To stop a trace that uses the file listener (a trace started by using the *FilePath* parameter), use the *RemoveFileListener* parameter.</span></span> <span data-ttu-id="d91c6-220">當您移除接聽程式，追蹤會隨即停止。</span><span class="sxs-lookup"><span data-stu-id="d91c6-220">When you remove the listener, the trace stops.</span></span>
* <span data-ttu-id="d91c6-221">如果要判斷可追蹤的元件，請使用 Get-TraceSource。</span><span class="sxs-lookup"><span data-stu-id="d91c6-221">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="d91c6-222">當元件正在使用中時，每個模組的追蹤來源會自動載入，而且會出現在 **TraceSource** 的輸出中。</span><span class="sxs-lookup"><span data-stu-id="d91c6-222">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of **Get-TraceSource** .</span></span>

## <span data-ttu-id="d91c6-223">相關連結</span><span class="sxs-lookup"><span data-stu-id="d91c6-223">RELATED LINKS</span></span>

[<span data-ttu-id="d91c6-224">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="d91c6-224">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="d91c6-225">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="d91c6-225">Trace-Command</span></span>](Trace-Command.md)

