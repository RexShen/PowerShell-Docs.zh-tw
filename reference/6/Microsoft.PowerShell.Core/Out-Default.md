---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-default?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Default
ms.openlocfilehash: 19871bcfd1e045ab30bfef0dc88aa42a4c4aecf4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204483"
---
# <span data-ttu-id="4be39-103">Out-Default</span><span class="sxs-lookup"><span data-stu-id="4be39-103">Out-Default</span></span>

## <span data-ttu-id="4be39-104">概要</span><span class="sxs-lookup"><span data-stu-id="4be39-104">SYNOPSIS</span></span>
<span data-ttu-id="4be39-105">將輸出傳送到預設的格式器和預設的輸出 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4be39-105">Sends the output to the default formatter and to the default output cmdlet.</span></span>

## <span data-ttu-id="4be39-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4be39-106">SYNTAX</span></span>

```
Out-Default [-Transcript] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="4be39-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="4be39-107">DESCRIPTION</span></span>

<span data-ttu-id="4be39-108">PowerShell 會自動加入 `Out-Default` 至每個管線的結尾。</span><span class="sxs-lookup"><span data-stu-id="4be39-108">PowerShell automatically adds `Out-Default` to the end of every pipeline.</span></span> <span data-ttu-id="4be39-109">`Out-Default` 決定如何格式化和輸出物件資料流程。</span><span class="sxs-lookup"><span data-stu-id="4be39-109">`Out-Default` decides how to format and output the object stream.</span></span> <span data-ttu-id="4be39-110">如果物件資料流程是字串資料流程，請 `Out-Default` 直接將這些物件傳送至，以 `Out-Host` 呼叫主機提供的適當 api。</span><span class="sxs-lookup"><span data-stu-id="4be39-110">If the object stream is a stream of strings, `Out-Default` pipes these directly to `Out-Host` which calls the appropriate APIs provided by the host.</span></span> <span data-ttu-id="4be39-111">如果物件資料流程不包含字串，會 `Out-Default` 檢查物件以判斷要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="4be39-111">If the object stream does not contain strings, `Out-Default` inspects the object to determine what to do.</span></span>
<span data-ttu-id="4be39-112">首先，它會查看物件類型，並判斷是否有此物件類型的已註冊 _view_ 。</span><span class="sxs-lookup"><span data-stu-id="4be39-112">First it looks at the object type and determines whether there is a registered _view_ for this object type.</span></span>

<span data-ttu-id="4be39-113">PowerShell 會 (Cmdlet 定義 XML 架構和機制， `Update-FormatData`) 可讓任何人註冊物件類型的視圖。</span><span class="sxs-lookup"><span data-stu-id="4be39-113">PowerShell defines XML schema and a mechanism (the `Update-FormatData` cmdlet) where anyone can register views for an object type.</span></span> <span data-ttu-id="4be39-114">您可以針對任何物件類型指定 **寬型** 、 **清單** 、 **表格** 或 **自訂** 的視圖。</span><span class="sxs-lookup"><span data-stu-id="4be39-114">You can specify **wide** , **list** , **table** , or **custom** views for any object type.</span></span> <span data-ttu-id="4be39-115">這些視圖會指定要顯示的屬性，以及應如何顯示這些屬性。</span><span class="sxs-lookup"><span data-stu-id="4be39-115">The views specify which properties to display and how they should be displayed.</span></span> <span data-ttu-id="4be39-116">如果已註冊某個視圖，它會定義要使用的格式器。</span><span class="sxs-lookup"><span data-stu-id="4be39-116">If a view is registered, it defines which formatter to use.</span></span> <span data-ttu-id="4be39-117">因此，如果已註冊的視圖是 **資料表** 視圖，則會將 `Out-Default` 物件串流至 `Format-Table | Out-Host` 。</span><span class="sxs-lookup"><span data-stu-id="4be39-117">So if the registered view is a **table** view, `Out-Default` streams the objects to `Format-Table | Out-Host`.</span></span> <span data-ttu-id="4be39-118">`Format-Table` 將物件轉換成格式記錄的資料流程， (由 view 定義) 中的資料所驅動，然後將 `Out-Host` 格式化記錄轉換為主機介面上的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4be39-118">`Format-Table` transforms the objects into a stream of Formatting records (driven by the data in the view definition) and `Out-Host` transforms the formatting records into calls on the Host interface.</span></span>

## <span data-ttu-id="4be39-119">範例</span><span class="sxs-lookup"><span data-stu-id="4be39-119">EXAMPLES</span></span>

### <span data-ttu-id="4be39-120">範例 1</span><span class="sxs-lookup"><span data-stu-id="4be39-120">Example 1</span></span>

<span data-ttu-id="4be39-121">雖然這個 Cmdlet 不會直接由使用者執行，但它可以是。</span><span class="sxs-lookup"><span data-stu-id="4be39-121">While this cmdlet is not intended to be run directly by the end user, it can be.</span></span>

```powershell
Get-Process | Select-Object -First 5 | Out-Default
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     12     2.56       5.20       0.00    7376   0 aesm_service
     48    34.32      18.10      26.64    9320  13 AlertusDesktopAlert
     24    13.97      12.74       0.77   12656  13 ApplicationFrameHost
      8     1.79       4.41       0.00    8180   0 AppVShNotify
      9     1.99       5.07       0.19   19320  13 AppVShNotify
```

## <span data-ttu-id="4be39-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4be39-122">PARAMETERS</span></span>

### <span data-ttu-id="4be39-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4be39-123">-InputObject</span></span>

<span data-ttu-id="4be39-124">接受 Cmdlet 的輸入。</span><span class="sxs-lookup"><span data-stu-id="4be39-124">Accepts input to the cmdlet.</span></span>

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

### <span data-ttu-id="4be39-125">-文字記錄</span><span class="sxs-lookup"><span data-stu-id="4be39-125">-Transcript</span></span>

<span data-ttu-id="4be39-126">判斷是否應將輸出傳送至 PowerShell 的轉譯服務。</span><span class="sxs-lookup"><span data-stu-id="4be39-126">Determines whether the output should be sent to PowerShell's transcription services.</span></span>

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

### <span data-ttu-id="4be39-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4be39-127">CommonParameters</span></span>

<span data-ttu-id="4be39-128">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="4be39-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4be39-129">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="4be39-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4be39-130">輸入</span><span class="sxs-lookup"><span data-stu-id="4be39-130">INPUTS</span></span>

## <span data-ttu-id="4be39-131">輸出</span><span class="sxs-lookup"><span data-stu-id="4be39-131">OUTPUTS</span></span>

## <span data-ttu-id="4be39-132">注意</span><span class="sxs-lookup"><span data-stu-id="4be39-132">NOTES</span></span>

## <span data-ttu-id="4be39-133">相關連結</span><span class="sxs-lookup"><span data-stu-id="4be39-133">RELATED LINKS</span></span>

[<span data-ttu-id="4be39-134">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="4be39-134">Format-Custom</span></span>](../Microsoft.PowerShell.Utility/Format-Custom.md)

[<span data-ttu-id="4be39-135">Format-List</span><span class="sxs-lookup"><span data-stu-id="4be39-135">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="4be39-136">Format-Table</span><span class="sxs-lookup"><span data-stu-id="4be39-136">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="4be39-137">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="4be39-137">Format-Wide</span></span>](../Microsoft.PowerShell.Utility/Format-Wide.md)

[<span data-ttu-id="4be39-138">about_Format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="4be39-138">about_Format.ps1xml</span></span>](About/about_Format.ps1xml.md)

[<span data-ttu-id="4be39-139">PowerShell 格式化和輸出的實際運作方式</span><span class="sxs-lookup"><span data-stu-id="4be39-139">How PowerShell Formatting and Outputting REALLY works</span></span>](https://devblogs.microsoft.com/powershell/how-powershell-formatting-and-outputting-really-works/)
