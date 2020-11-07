---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-printer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Printer
ms.openlocfilehash: bd9a141537c7f075d3c02827af4694813d6f0db6
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346916"
---
# <span data-ttu-id="b918b-103">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="b918b-103">Out-Printer</span></span>

## <span data-ttu-id="b918b-104">概要</span><span class="sxs-lookup"><span data-stu-id="b918b-104">SYNOPSIS</span></span>
<span data-ttu-id="b918b-105">將輸出傳送到印表機。</span><span class="sxs-lookup"><span data-stu-id="b918b-105">Sends output to a printer.</span></span>

## <span data-ttu-id="b918b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b918b-106">SYNTAX</span></span>

```
Out-Printer [[-Name] <String>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="b918b-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b918b-107">DESCRIPTION</span></span>

<span data-ttu-id="b918b-108">`Out-Printer`Cmdlet 會將輸出傳送到預設印表機或替代印表機（若有指定）。</span><span class="sxs-lookup"><span data-stu-id="b918b-108">The `Out-Printer` cmdlet sends output to the default printer or to an alternate printer, if one is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="b918b-109">PowerShell 7 中已重新引入此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b918b-109">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="b918b-110">只有支援 Windows 桌面的 Windows 系統才能使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b918b-110">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span>

## <span data-ttu-id="b918b-111">範例</span><span class="sxs-lookup"><span data-stu-id="b918b-111">EXAMPLES</span></span>

### <span data-ttu-id="b918b-112">範例 1-傳送要列印在預設印表機上的檔案</span><span class="sxs-lookup"><span data-stu-id="b918b-112">Example 1 - Send a file to be printed on the default printer</span></span>

<span data-ttu-id="b918b-113">這個範例會示範如何列印檔案，即使沒有 `Out-Printer` **Path** 參數也是一樣。</span><span class="sxs-lookup"><span data-stu-id="b918b-113">This example shows how to print a file, even though `Out-Printer` does not have a **Path** parameter.</span></span>

```powershell
Get-Content -Path ./readme.txt | Out-Printer
```

<span data-ttu-id="b918b-114">`Get-Content`取得目前目錄中檔案的內容， `readme.txt` 並將其傳送至 `Out-Printer` 預設印表機，以傳送到預設印表機。</span><span class="sxs-lookup"><span data-stu-id="b918b-114">`Get-Content`gets the contents of the `readme.txt` file in the current directory and pipes it to `Out-Printer`, which sends it to the default printer.</span></span>

### <span data-ttu-id="b918b-115">範例2：將字串列印到遠端印表機</span><span class="sxs-lookup"><span data-stu-id="b918b-115">Example 2: Print a string to a remote printer</span></span>

<span data-ttu-id="b918b-116">此範例會列印 `Hello, World` 到 Server01 上的 **Prt 6b 彩色** 印表機。</span><span class="sxs-lookup"><span data-stu-id="b918b-116">This example prints `Hello, World` to the **Prt-6B Color** printer on Server01.</span></span>

```powershell
"Hello, World" | Out-Printer -Name "\\Server01\Prt-6B Color"
```

<span data-ttu-id="b918b-117">**Name** 參數會選取特定的印表機，而不是預設的。</span><span class="sxs-lookup"><span data-stu-id="b918b-117">The **Name** parameter selects a specific printer, rather than the default.</span></span>

### <span data-ttu-id="b918b-118">範例 3-將說明主題列印到預設印表機</span><span class="sxs-lookup"><span data-stu-id="b918b-118">Example 3 - Print a help topic to the default printer</span></span>

<span data-ttu-id="b918b-119">這個範例會列印的完整版說明主題 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="b918b-119">This example prints the full version of the Help topic for `Get-CimInstance`.</span></span>

```powershell
$H = Get-Help -Full Get-CimInstance
Out-Printer -InputObject $H
```

<span data-ttu-id="b918b-120">`Get-Help` 取得的說明主題的完整版本 `Get-CimInstance` ，並將它儲存在 `$H` 變數中。</span><span class="sxs-lookup"><span data-stu-id="b918b-120">`Get-Help` gets the full version of the Help topic for `Get-CimInstance` and stores it in the `$H` variable.</span></span> <span data-ttu-id="b918b-121">**InputObject** 參數會將的值傳遞 `$H` 給 `Out-Printer` 。</span><span class="sxs-lookup"><span data-stu-id="b918b-121">The **InputObject** parameter passes the value of `$H` to `Out-Printer`.</span></span>

## <span data-ttu-id="b918b-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b918b-122">PARAMETERS</span></span>

### <span data-ttu-id="b918b-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b918b-123">-InputObject</span></span>

<span data-ttu-id="b918b-124">指定要傳送到印表機的物件。</span><span class="sxs-lookup"><span data-stu-id="b918b-124">Specifies the objects to be sent to the printer.</span></span> <span data-ttu-id="b918b-125">輸入包含物件的變數，或輸入可取得物件的命令或運算式。</span><span class="sxs-lookup"><span data-stu-id="b918b-125">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="b918b-126">-Name</span><span class="sxs-lookup"><span data-stu-id="b918b-126">-Name</span></span>

<span data-ttu-id="b918b-127">將輸出傳送到指定的印表機。</span><span class="sxs-lookup"><span data-stu-id="b918b-127">Sends the output to the specified printer.</span></span> <span data-ttu-id="b918b-128">參數名稱 **名稱** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="b918b-128">The parameter name **Name** is optional.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PrinterName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b918b-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b918b-129">CommonParameters</span></span>

<span data-ttu-id="b918b-130">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b918b-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b918b-131">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b918b-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b918b-132">輸入</span><span class="sxs-lookup"><span data-stu-id="b918b-132">INPUTS</span></span>

### <span data-ttu-id="b918b-133">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="b918b-133">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b918b-134">您可以透過管線將任何物件傳送至 `Out-Printer` 。</span><span class="sxs-lookup"><span data-stu-id="b918b-134">You can pipe any object to `Out-Printer`.</span></span>

## <span data-ttu-id="b918b-135">輸出</span><span class="sxs-lookup"><span data-stu-id="b918b-135">OUTPUTS</span></span>

### <span data-ttu-id="b918b-136">None</span><span class="sxs-lookup"><span data-stu-id="b918b-136">None</span></span>

<span data-ttu-id="b918b-137">`Out-Printer` 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="b918b-137">`Out-Printer` does not return any objects.</span></span>

## <span data-ttu-id="b918b-138">注意</span><span class="sxs-lookup"><span data-stu-id="b918b-138">NOTES</span></span>

<span data-ttu-id="b918b-139">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="b918b-139">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="b918b-140">包含動詞的 Cmdlet `Out` 不會將物件格式化。</span><span class="sxs-lookup"><span data-stu-id="b918b-140">The cmdlets that contain the `Out` verb do not format objects.</span></span> <span data-ttu-id="b918b-141">它們只會轉譯它們並傳送至指定的顯示目的地。</span><span class="sxs-lookup"><span data-stu-id="b918b-141">They just render them and send them to the specified display destination.</span></span> <span data-ttu-id="b918b-142">如果您將未格式化的物件傳送至 `Out` Cmdlet，此 Cmdlet 會將它傳送到格式化 Cmdlet，然後才轉譯它。</span><span class="sxs-lookup"><span data-stu-id="b918b-142">If you send an unformatted object to an `Out` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="b918b-143">`Out-Printer` 將資料傳送至印表機，但不會發出任何輸出物件至管線。</span><span class="sxs-lookup"><span data-stu-id="b918b-143">`Out-Printer` sends data to the printer, but does not emit any output objects to the pipeline.</span></span> <span data-ttu-id="b918b-144">如果您使用管線將的輸出傳送 `Out-Printer` 至，就會 `Get-Member` `Get-Member` 報告未指定任何物件。</span><span class="sxs-lookup"><span data-stu-id="b918b-144">If you pipe the output of `Out-Printer` to `Get-Member`, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="b918b-145">相關連結</span><span class="sxs-lookup"><span data-stu-id="b918b-145">RELATED LINKS</span></span>

[<span data-ttu-id="b918b-146">Out-File</span><span class="sxs-lookup"><span data-stu-id="b918b-146">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="b918b-147">Out-String</span><span class="sxs-lookup"><span data-stu-id="b918b-147">Out-String</span></span>](Out-String.md)
