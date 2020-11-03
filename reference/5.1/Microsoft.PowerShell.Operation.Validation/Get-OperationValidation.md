---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203431"
---
# <span data-ttu-id="26439-103">Get-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="26439-103">Get-OperationValidation</span></span>

## <span data-ttu-id="26439-104">概要</span><span class="sxs-lookup"><span data-stu-id="26439-104">SYNOPSIS</span></span>
<span data-ttu-id="26439-105">取得作業驗證架構測試。</span><span class="sxs-lookup"><span data-stu-id="26439-105">Gets Operation Validation Framework tests.</span></span>

## <span data-ttu-id="26439-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="26439-106">SYNTAX</span></span>

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="26439-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="26439-107">DESCRIPTION</span></span>
<span data-ttu-id="26439-108">**OperationValidation** 指令程式會取得已安裝模組的作業驗證架構測試。</span><span class="sxs-lookup"><span data-stu-id="26439-108">The **Get-OperationValidation** cmdlet gets Operation Validation Framework tests for installed modules.</span></span>

<span data-ttu-id="26439-109">系統會檢查包含診斷資料夾的模組，以在簡單或完整的子資料夾中進行 Pester 測試，或同時檢查兩者。</span><span class="sxs-lookup"><span data-stu-id="26439-109">Modules that include a Diagnostics folder are inspected for Pester tests in the Simple or Comprehensive subfolder, or both.</span></span>

## <span data-ttu-id="26439-110">範例</span><span class="sxs-lookup"><span data-stu-id="26439-110">EXAMPLES</span></span>

### <span data-ttu-id="26439-111">範例1：取得作業驗證測試</span><span class="sxs-lookup"><span data-stu-id="26439-111">Example 1: Get Operation Validation tests</span></span>

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

<span data-ttu-id="26439-112">此命令會從 C:\temp\modules 資料夾中名為 AddNumbers 的模組取得驗證測試。</span><span class="sxs-lookup"><span data-stu-id="26439-112">This command gets validation tests from the module named AddNumbers in the C:\temp\modules folder.</span></span>

## <span data-ttu-id="26439-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="26439-113">PARAMETERS</span></span>

### <span data-ttu-id="26439-114">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="26439-114">-ModuleName</span></span>
<span data-ttu-id="26439-115">指定模組名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="26439-115">Specifies an array of names of modules.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="26439-116">->testtype</span><span class="sxs-lookup"><span data-stu-id="26439-116">-TestType</span></span>
<span data-ttu-id="26439-117">指定測試類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="26439-117">Specifies an array of test types.</span></span>
<span data-ttu-id="26439-118">有效值為 Simple、綜合性或 both。</span><span class="sxs-lookup"><span data-stu-id="26439-118">Valid values are Simple, Comprehensive, or both.</span></span>
<span data-ttu-id="26439-119">預設值為「簡單、完整」。</span><span class="sxs-lookup"><span data-stu-id="26439-119">The default is "Simple,Comprehensive".</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="26439-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="26439-120">CommonParameters</span></span>
<span data-ttu-id="26439-121">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="26439-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="26439-122">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="26439-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="26439-123">輸入</span><span class="sxs-lookup"><span data-stu-id="26439-123">INPUTS</span></span>

### <span data-ttu-id="26439-124">無</span><span class="sxs-lookup"><span data-stu-id="26439-124">None</span></span>
<span data-ttu-id="26439-125">您無法透過管道傳送任何輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26439-125">You cannot pipe any input to this cmdlet.</span></span>

## <span data-ttu-id="26439-126">輸出</span><span class="sxs-lookup"><span data-stu-id="26439-126">OUTPUTS</span></span>

### <span data-ttu-id="26439-127">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="26439-127">PSCustomObject</span></span>
<span data-ttu-id="26439-128">**PSCustomObject** 會描述驗證。</span><span class="sxs-lookup"><span data-stu-id="26439-128">The **PSCustomObject** describes the validation.</span></span>

## <span data-ttu-id="26439-129">注意</span><span class="sxs-lookup"><span data-stu-id="26439-129">NOTES</span></span>

## <span data-ttu-id="26439-130">相關連結</span><span class="sxs-lookup"><span data-stu-id="26439-130">RELATED LINKS</span></span>

[<span data-ttu-id="26439-131">Invoke-OperationValidation</span><span class="sxs-lookup"><span data-stu-id="26439-131">Invoke-OperationValidation</span></span>](Invoke-OperationValidation.md)
