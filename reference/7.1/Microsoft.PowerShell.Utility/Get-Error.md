---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: c29115a65b46d38039d78b10eee293e6944cede5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202839"
---
# <span data-ttu-id="bc294-103">Get-Error</span><span class="sxs-lookup"><span data-stu-id="bc294-103">Get-Error</span></span>

## <span data-ttu-id="bc294-104">概要</span><span class="sxs-lookup"><span data-stu-id="bc294-104">SYNOPSIS</span></span>

<span data-ttu-id="bc294-105">取得並顯示目前會話中最近的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="bc294-105">Gets and displays the most recent error messages from the current session.</span></span>

## <span data-ttu-id="bc294-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bc294-106">SYNTAX</span></span>

### <span data-ttu-id="bc294-107">最新 (預設) </span><span class="sxs-lookup"><span data-stu-id="bc294-107">Newest (Default)</span></span>

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="bc294-108">錯誤</span><span class="sxs-lookup"><span data-stu-id="bc294-108">Error</span></span>

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="bc294-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bc294-109">DESCRIPTION</span></span>

<span data-ttu-id="bc294-110">此 `Get-Error` Cmdlet 會取得 **PSExtendedError** 物件，該物件代表會話中最後一個錯誤的目前錯誤詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bc294-110">The `Get-Error` cmdlet gets a **PSExtendedError** object that represents the current error details from the last error that occurred in the session.</span></span>

<span data-ttu-id="bc294-111">您可以使用 `Get-Error` 來顯示目前會話中使用 **最新** 參數所發生的指定錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="bc294-111">You can use `Get-Error` to display a specified number of errors that have occurred in the current session using the **Newest** parameter.</span></span>

<span data-ttu-id="bc294-112">此 `Get-Error` Cmdlet 也會從集合接收錯誤物件（例如 `$Error` ），以顯示目前會話的多個錯誤。</span><span class="sxs-lookup"><span data-stu-id="bc294-112">The `Get-Error` cmdlet also receives error objects from a collection, such as `$Error`, to display multiple errors from the current session.</span></span>

## <span data-ttu-id="bc294-113">範例</span><span class="sxs-lookup"><span data-stu-id="bc294-113">EXAMPLES</span></span>

### <span data-ttu-id="bc294-114">範例1：取得最新的錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="bc294-114">Example 1: Get the most recent error details</span></span>

<span data-ttu-id="bc294-115">在此範例中， `Get-Error` 會顯示目前會話中發生之最新錯誤的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bc294-115">In this example, `Get-Error` displays the details of the most recent error that occurred in the current session.</span></span>

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### <span data-ttu-id="bc294-116">範例2：取得目前會話中所發生的指定錯誤訊息數目</span><span class="sxs-lookup"><span data-stu-id="bc294-116">Example 2: Get the specified number of error messages that occurred in the current session</span></span>

<span data-ttu-id="bc294-117">此範例示範如何搭配 `Get-Error` **最新** 的參數使用。</span><span class="sxs-lookup"><span data-stu-id="bc294-117">This example shows how to use `Get-Error` with the **Newest** parameter.</span></span> <span data-ttu-id="bc294-118">在此範例中， **最新** 會傳回在此會話中所發生3個最新錯誤的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bc294-118">In this example, **Newest** returns the details of the 3 newest errors that occurred in this session.</span></span>

```powershell
Get-Error -Newest 3
```

### <span data-ttu-id="bc294-119">範例3：傳送錯誤的集合以接收詳細訊息</span><span class="sxs-lookup"><span data-stu-id="bc294-119">Example 3: Send a collection of errors to receive detailed messages</span></span>

<span data-ttu-id="bc294-120">`$Error`自動變數在目前的會話中包含錯誤物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="bc294-120">The `$Error` automatic variable contains an array of error objects in the current session.</span></span> <span data-ttu-id="bc294-121">您可以透過管道將物件陣列傳送至， `Get-Error` 以接收詳細的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="bc294-121">The array of objects can be piped to `Get-Error` to receive detailed error messages.</span></span>

<span data-ttu-id="bc294-122">在此範例中， `$Error` 會透過管道傳送至 `Get-Error` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bc294-122">In this example, `$Error` is piped to the `Get-Error` cmdlet.</span></span> <span data-ttu-id="bc294-123">結果是一份詳細的錯誤訊息清單，類似于範例1的結果。</span><span class="sxs-lookup"><span data-stu-id="bc294-123">the result is list of detailed error messages, similar to the result of Example 1.</span></span>

```powershell
$Error | Get-Error
```

## <span data-ttu-id="bc294-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bc294-124">PARAMETERS</span></span>

### <span data-ttu-id="bc294-125">-Newest</span><span class="sxs-lookup"><span data-stu-id="bc294-125">-Newest</span></span>

<span data-ttu-id="bc294-126">指定目前會話中所發生的錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="bc294-126">Specifies the number of errors to display that have occurred in the current session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc294-127">-InputObject</span><span class="sxs-lookup"><span data-stu-id="bc294-127">-InputObject</span></span>

<span data-ttu-id="bc294-128">此參數用於管線輸入。</span><span class="sxs-lookup"><span data-stu-id="bc294-128">This parameter is used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bc294-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bc294-129">CommonParameters</span></span>

<span data-ttu-id="bc294-130">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bc294-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bc294-131">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bc294-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bc294-132">輸入</span><span class="sxs-lookup"><span data-stu-id="bc294-132">INPUTS</span></span>

### <span data-ttu-id="bc294-133">PSObject</span><span class="sxs-lookup"><span data-stu-id="bc294-133">PSObject</span></span>

<span data-ttu-id="bc294-134">支援來自任何 **PSObject** 的輸入，但結果會有所不同，除非提供了 **ErrorRecord** 或 **Exception** 物件。</span><span class="sxs-lookup"><span data-stu-id="bc294-134">Supports input from any **PSObject** , but results vary unless either an **ErrorRecord** or **Exception** object are supplied.</span></span>

## <span data-ttu-id="bc294-135">輸出</span><span class="sxs-lookup"><span data-stu-id="bc294-135">OUTPUTS</span></span>

### <span data-ttu-id="bc294-136">ErrorRecord # PSExtendedError。</span><span class="sxs-lookup"><span data-stu-id="bc294-136">System.Management.Automation.ErrorRecord#PSExtendedError</span></span>

<span data-ttu-id="bc294-137">**PSExtendedError** 物件中的輸出。</span><span class="sxs-lookup"><span data-stu-id="bc294-137">Output in a **PSExtendedError** object.</span></span>

## <span data-ttu-id="bc294-138">注意</span><span class="sxs-lookup"><span data-stu-id="bc294-138">NOTES</span></span>

<span data-ttu-id="bc294-139">`Get-Error` 接受管線輸入。</span><span class="sxs-lookup"><span data-stu-id="bc294-139">`Get-Error` accepts pipeline input.</span></span> <span data-ttu-id="bc294-140">例如： `$Error | Get-Error` 。</span><span class="sxs-lookup"><span data-stu-id="bc294-140">For example, `$Error | Get-Error`.</span></span>

## <span data-ttu-id="bc294-141">相關連結</span><span class="sxs-lookup"><span data-stu-id="bc294-141">RELATED LINKS</span></span>

[<span data-ttu-id="bc294-142">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="bc294-142">about_Try_Catch_Finally</span></span>](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
