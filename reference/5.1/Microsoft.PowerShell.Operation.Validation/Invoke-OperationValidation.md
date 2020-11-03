---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/invoke-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-OperationValidation
ms.openlocfilehash: 6c9d4001392de48032a0fe1ba3667db90ea614fc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203428"
---
# <span data-ttu-id="f81a6-103">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="f81a6-103">Invoke-OperationValidation</span></span>

## <span data-ttu-id="f81a6-104">概要</span><span class="sxs-lookup"><span data-stu-id="f81a6-104">SYNOPSIS</span></span>

<span data-ttu-id="f81a6-105">叫用作業驗證架構測試。</span><span class="sxs-lookup"><span data-stu-id="f81a6-105">Invokes Operation Validation Framework tests.</span></span>

## <span data-ttu-id="f81a6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f81a6-106">SYNTAX</span></span>

### <span data-ttu-id="f81a6-107">FileAndTest (預設) </span><span class="sxs-lookup"><span data-stu-id="f81a6-107">FileAndTest (Default)</span></span>

```
Invoke-OperationValidation [-TestInfo <PSObject[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f81a6-108">路徑</span><span class="sxs-lookup"><span data-stu-id="f81a6-108">Path</span></span>

```
Invoke-OperationValidation [-testFilePath <String[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f81a6-109">UseGetOperationTest</span><span class="sxs-lookup"><span data-stu-id="f81a6-109">UseGetOperationTest</span></span>

```
Invoke-OperationValidation [-ModuleName <String[]>] [-TestType <String[]>] [-IncludePesterOutput] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f81a6-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f81a6-110">DESCRIPTION</span></span>

<span data-ttu-id="f81a6-111">**OperationValidation 指令程式** 會叫用指定模組的作業驗證架構測試。</span><span class="sxs-lookup"><span data-stu-id="f81a6-111">The **Invoke-OperationValidation** cmdlet invokes Operation Validation Framework tests for a specified module.</span></span>

## <span data-ttu-id="f81a6-112">範例</span><span class="sxs-lookup"><span data-stu-id="f81a6-112">EXAMPLES</span></span>

### <span data-ttu-id="f81a6-113">範例1：叫用作業驗證測試</span><span class="sxs-lookup"><span data-stu-id="f81a6-113">Example 1: Invoke an Operation Validation test</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "OperationValidation" | Invoke-OperationValidation -IncludePesterOutput
Describing Simple Test Suite
 [+] first Operational test 20ms
 [+] second Operational test 19ms
 [+] third Operational test 9ms
Tests completed in 48ms
Passed: 3 Failed: 0 Skipped: 0 Pending: 0
Describing Scenario targeted tests
   Context The RemoteAccess service
    [+] The service is running 37ms
   Context The Firewall Rules
    [+] A rule for TCP port 3389 is enabled 1.19s
    [+] A rule for UDP port 3389 is enabled 11ms
Tests completed in 1.24s
Passed: 3 Failed: 0 Skipped: 0 Pending: 0




   Module: OperationValidation




Result  Name
------- --------
Passed  Simple Test Suite::first Operational test
Passed  Simple Test Suite::second Operational test
Passed  Simple Test Suite::third Operational test
Passed  Scenario targeted tests:The RemoteAccess service:The service is running
Passed  Scenario targeted tests:The Firewall Rules:A rule for TCP port 3389 is enabled
Passed  Scenario targeted tests:The Firewall Rules:A rule for UDP port 3389 is enabled
```

<span data-ttu-id="f81a6-114">此命令會取得名為 OperationValidation 的模組，並使用管線運算子將它傳遞給執行測試的 **OperationValidation** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f81a6-114">This command gets the module named OperationValidation, and uses the pipeline operator to pass it to the **Invoke-OperationValidation** cmdlet, which runs the test.</span></span>

## <span data-ttu-id="f81a6-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f81a6-115">PARAMETERS</span></span>

### <span data-ttu-id="f81a6-116">-IncludePesterOutput</span><span class="sxs-lookup"><span data-stu-id="f81a6-116">-IncludePesterOutput</span></span>

<span data-ttu-id="f81a6-117">包含 Pester 測試輸出。</span><span class="sxs-lookup"><span data-stu-id="f81a6-117">Includes Pester test output.</span></span>
<span data-ttu-id="f81a6-118">預設值為 $False。</span><span class="sxs-lookup"><span data-stu-id="f81a6-118">The default is $False.</span></span>

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

### <span data-ttu-id="f81a6-119">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="f81a6-119">-ModuleName</span></span>

<span data-ttu-id="f81a6-120">指定模組名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="f81a6-120">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f81a6-121">-testFilePath</span><span class="sxs-lookup"><span data-stu-id="f81a6-121">-testFilePath</span></span>

<span data-ttu-id="f81a6-122">指定作業驗證架構測試檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="f81a6-122">Specifies the path of an Operation Validation Framework test file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f81a6-123">-TestInfo</span><span class="sxs-lookup"><span data-stu-id="f81a6-123">-TestInfo</span></span>

<span data-ttu-id="f81a6-124">指定自訂物件，指定檔案的路徑，以及要執行之測試的名稱。</span><span class="sxs-lookup"><span data-stu-id="f81a6-124">Specifies a custom object that specifies the path to the file and the name of the test to run.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: FileAndTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f81a6-125">->testtype</span><span class="sxs-lookup"><span data-stu-id="f81a6-125">-TestType</span></span>

<span data-ttu-id="f81a6-126">指定測試類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="f81a6-126">Specifies an array of test types.</span></span>
<span data-ttu-id="f81a6-127">有效值為 Simple、綜合性或 both。</span><span class="sxs-lookup"><span data-stu-id="f81a6-127">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="f81a6-128">預設值為「簡單、完整」。</span><span class="sxs-lookup"><span data-stu-id="f81a6-128">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f81a6-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f81a6-129">-Confirm</span></span>

<span data-ttu-id="f81a6-130">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f81a6-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f81a6-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f81a6-131">-WhatIf</span></span>

<span data-ttu-id="f81a6-132">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f81a6-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f81a6-133">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f81a6-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f81a6-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f81a6-134">CommonParameters</span></span>
<span data-ttu-id="f81a6-135">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f81a6-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f81a6-136">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f81a6-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f81a6-137">輸入</span><span class="sxs-lookup"><span data-stu-id="f81a6-137">INPUTS</span></span>

### <span data-ttu-id="f81a6-138">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="f81a6-138">PSCustomObject</span></span>

<span data-ttu-id="f81a6-139">您可以透過管道將 **OperationValidation** 的輸出傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f81a6-139">You can pipe the output of **Get-OperationValidation** to this cmdlet.</span></span>

## <span data-ttu-id="f81a6-140">輸出</span><span class="sxs-lookup"><span data-stu-id="f81a6-140">OUTPUTS</span></span>

### <span data-ttu-id="f81a6-141">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="f81a6-141">PSCustomObject</span></span>

<span data-ttu-id="f81a6-142">**PSCustomObject** 描述驗證是否成功。</span><span class="sxs-lookup"><span data-stu-id="f81a6-142">The **PSCustomObject** describes whether the validation was successful.</span></span>

## <span data-ttu-id="f81a6-143">注意</span><span class="sxs-lookup"><span data-stu-id="f81a6-143">NOTES</span></span>

## <span data-ttu-id="f81a6-144">相關連結</span><span class="sxs-lookup"><span data-stu-id="f81a6-144">RELATED LINKS</span></span>

[<span data-ttu-id="f81a6-145">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="f81a6-145">Get-OperationValidation</span></span>](Get-OperationValidation.md)
