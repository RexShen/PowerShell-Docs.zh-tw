---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: 5a949629cdf0f0822866863822e82e70fc38d8c2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202708"
---
# <span data-ttu-id="a341b-103">Out-Null</span><span class="sxs-lookup"><span data-stu-id="a341b-103">Out-Null</span></span>

## <span data-ttu-id="a341b-104">概要</span><span class="sxs-lookup"><span data-stu-id="a341b-104">SYNOPSIS</span></span>
<span data-ttu-id="a341b-105">隱藏輸出，而不是將它向下傳送或顯示。</span><span class="sxs-lookup"><span data-stu-id="a341b-105">Hides the output instead of sending it down the pipeline or displaying it.</span></span>

## <span data-ttu-id="a341b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a341b-106">SYNTAX</span></span>

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="a341b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a341b-107">DESCRIPTION</span></span>
<span data-ttu-id="a341b-108">**Out-Null** Cmdlet 會將其輸出傳送至 Null，實際上會將其從管線中移除，並防止輸出顯示在畫面上。</span><span class="sxs-lookup"><span data-stu-id="a341b-108">The **Out-Null** cmdlet sends its output to NULL, in effect, removing it from the pipeline and preventing the output to be displayed at the screen.</span></span> <span data-ttu-id="a341b-109">這只會影響標準輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="a341b-109">This only affects the standard output stream.</span></span>
<span data-ttu-id="a341b-110">其他輸出資料流程（例如錯誤資料流程）不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="a341b-110">Other output streams, like the Error stream are not affected.</span></span> <span data-ttu-id="a341b-111">將會顯示例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a341b-111">Exceptions will be displayed.</span></span> <span data-ttu-id="a341b-112">這可讓您更輕鬆地測試命令是否有任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="a341b-112">This makes it easier to test your command for any errors.</span></span>

## <span data-ttu-id="a341b-113">範例</span><span class="sxs-lookup"><span data-stu-id="a341b-113">EXAMPLES</span></span>

### <span data-ttu-id="a341b-114">範例 1︰刪除輸出</span><span class="sxs-lookup"><span data-stu-id="a341b-114">Example 1: Delete output</span></span>

```
PS C:\> Get-ChildItem | Out-Null
```

<span data-ttu-id="a341b-115">此命令會取得目前位置/目錄中的專案，但其輸出不會透過管線傳遞，也不會在命令列中顯示。</span><span class="sxs-lookup"><span data-stu-id="a341b-115">This command gets items in the current location/directory, but its output is not passed through the pipeline nor displayed at the command line.</span></span>
<span data-ttu-id="a341b-116">這適用于隱藏您不需要的輸出。</span><span class="sxs-lookup"><span data-stu-id="a341b-116">This is useful for hiding output that you do not need.</span></span>

## <span data-ttu-id="a341b-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a341b-117">PARAMETERS</span></span>

### <span data-ttu-id="a341b-118">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a341b-118">-InputObject</span></span>
<span data-ttu-id="a341b-119">指定要傳送至 Null (從管線) 移除的物件。</span><span class="sxs-lookup"><span data-stu-id="a341b-119">Specifies the object to be sent to NULL (removed from pipeline).</span></span>
<span data-ttu-id="a341b-120">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="a341b-120">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a341b-121">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a341b-121">CommonParameters</span></span>
<span data-ttu-id="a341b-122">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a341b-122">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a341b-123">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a341b-123">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a341b-124">輸入</span><span class="sxs-lookup"><span data-stu-id="a341b-124">INPUTS</span></span>

### <span data-ttu-id="a341b-125">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="a341b-125">System.Management.Automation.PSObject</span></span>
<span data-ttu-id="a341b-126">您可以使用管線將任何物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a341b-126">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="a341b-127">輸出</span><span class="sxs-lookup"><span data-stu-id="a341b-127">OUTPUTS</span></span>

### <span data-ttu-id="a341b-128">無</span><span class="sxs-lookup"><span data-stu-id="a341b-128">None</span></span>
<span data-ttu-id="a341b-129">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a341b-129">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a341b-130">注意</span><span class="sxs-lookup"><span data-stu-id="a341b-130">NOTES</span></span>

* <span data-ttu-id="a341b-131">包含 **out** Cmdlet ( **out** Cmdlet 的 Cmdlet) 沒有名稱或檔案路徑的參數。</span><span class="sxs-lookup"><span data-stu-id="a341b-131">The cmdlets that contain the **Out** verb (the **Out** cmdlets) do not have parameters for names or file paths.</span></span> <span data-ttu-id="a341b-132">若要將資料傳送給 **Out** Cmdlet，請使用管線運算子 (|) 將 Windows PowerShell 命令的輸出傳送給此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a341b-132">To send data to an **Out** cmdlet, use a pipeline operator (|) to send the output of a Windows PowerShell command to the cmdlet.</span></span> <span data-ttu-id="a341b-133">您也可以將資料儲存在變數中，然後使用 *InputObject* 參數將資料傳遞給 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a341b-133">You can also store data in a variable and use the *InputObject* parameter to pass the data to the cmdlet.</span></span> <span data-ttu-id="a341b-134">如需詳細資訊，請參閱範例。</span><span class="sxs-lookup"><span data-stu-id="a341b-134">For more information, see the examples.</span></span>
* <span data-ttu-id="a341b-135">**Out-Null** 不會傳回任何輸出物件。</span><span class="sxs-lookup"><span data-stu-id="a341b-135">**Out-Null** does not return any output objects.</span></span> <span data-ttu-id="a341b-136">如果您使用管線將 **Out-Null** 的輸出傳送至 Get-Member Cmdlet， **Get-Member** 即會報告尚未指定任何物件。</span><span class="sxs-lookup"><span data-stu-id="a341b-136">If you pipe the output of **Out-Null** to the Get-Member cmdlet, **Get-Member** reports that no objects have been specified.</span></span>

## <span data-ttu-id="a341b-137">相關連結</span><span class="sxs-lookup"><span data-stu-id="a341b-137">RELATED LINKS</span></span>

[<span data-ttu-id="a341b-138">Out-Default</span><span class="sxs-lookup"><span data-stu-id="a341b-138">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="a341b-139">Out-Host</span><span class="sxs-lookup"><span data-stu-id="a341b-139">Out-Host</span></span>](Out-Host.md)
