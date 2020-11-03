---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 098e98dec6733af036795e4decb633f59d40c633
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196696"
---
# <span data-ttu-id="6c5ed-103">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="6c5ed-103">Get-UICulture</span></span>

## <span data-ttu-id="6c5ed-104">概要</span><span class="sxs-lookup"><span data-stu-id="6c5ed-104">SYNOPSIS</span></span>
<span data-ttu-id="6c5ed-105">取得作業系統中目前的 UI 文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-105">Gets the current UI culture settings in the operating system.</span></span>

## <span data-ttu-id="6c5ed-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6c5ed-106">SYNTAX</span></span>

```
Get-UICulture [<CommonParameters>]
```

## <span data-ttu-id="6c5ed-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6c5ed-107">DESCRIPTION</span></span>
<span data-ttu-id="6c5ed-108">**UICulture 指令程式** 會取得 Windows 的目前使用者介面 (UI) 文化特性設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-108">The **Get-UICulture** cmdlet gets information about the current user interface (UI) culture settings for Windows.</span></span>
<span data-ttu-id="6c5ed-109">UI 文化特性會決定要將哪些文字字串用於使用者介面元素，例如功能表和訊息。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-109">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

<span data-ttu-id="6c5ed-110">您也可以使用 Get-Culture Cmdlet，這會取得系統上目前的文化特性。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-110">You can also use the Get-Culture cmdlet, which gets the current culture on the system.</span></span>
<span data-ttu-id="6c5ed-111">文化特性會決定項目 (例如數字、貨幣及日期) 的顯示格式。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-111">The culture determines the display format of items such as numbers, currency, and dates.</span></span>

## <span data-ttu-id="6c5ed-112">範例</span><span class="sxs-lookup"><span data-stu-id="6c5ed-112">EXAMPLES</span></span>

### <span data-ttu-id="6c5ed-113">範例1：取得 UI 文化特性</span><span class="sxs-lookup"><span data-stu-id="6c5ed-113">Example 1: Get the UI culture</span></span>

```
PS C:\> Get-UICulture
```

<span data-ttu-id="6c5ed-114">這個命令會取得目前的 UI 文化特性資訊。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-114">This command gets the current UI culture information.</span></span>

### <span data-ttu-id="6c5ed-115">範例2：取得 UI 文化特性並設定結果格式</span><span class="sxs-lookup"><span data-stu-id="6c5ed-115">Example 2: Get the UI culture and format the results</span></span>

```
PS C:\> Get-UICulture | Format-List *
```

<span data-ttu-id="6c5ed-116">這個命令會以清單顯示目前 UI 文化特性的所有屬性值。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-116">This command displays the values of all of the properties of the current UI culture in a list.</span></span>

### <span data-ttu-id="6c5ed-117">範例3：取得行事曆屬性的值</span><span class="sxs-lookup"><span data-stu-id="6c5ed-117">Example 3: Get the value of the Calendar property</span></span>

```
PS C:\> (Get-UICulture).Calendar
```

<span data-ttu-id="6c5ed-118">這個命令會顯示目前 UI 文化特性之 Calendar 屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-118">This command displays the current values for the Calendar property of the current UI culture.</span></span>
<span data-ttu-id="6c5ed-119">Calendar 只是 UI 文化特性的一個屬性。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-119">Calendar is just one property of UI culture.</span></span>
<span data-ttu-id="6c5ed-120">若要查看所有屬性，請輸入 `Get-UICulture | Get-Member` 。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-120">To see all of the properties, type `Get-UICulture | Get-Member`.</span></span>

### <span data-ttu-id="6c5ed-121">範例4：取得簡短日期模式</span><span class="sxs-lookup"><span data-stu-id="6c5ed-121">Example 4: Get the short date pattern</span></span>

```
PS C:\> (Get-UICulture).DateTimeFormat.ShortDatePattern
```

<span data-ttu-id="6c5ed-122">這個命令會顯示目前 UI 文化特性的簡短日期模式。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-122">This command displays the short date pattern for the current UI culture.</span></span>
<span data-ttu-id="6c5ed-123">若要查看 UI 文化特性之 DateTimeFormat 屬性的所有子屬性，請輸入 `(Get-UICulture).DateTimeFormat | gm` 。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-123">To see all of the subproperties of the DateTimeFormat property of the UI culture, type `(Get-UICulture).DateTimeFormat | gm`.</span></span>

## <span data-ttu-id="6c5ed-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6c5ed-124">PARAMETERS</span></span>

### <span data-ttu-id="6c5ed-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6c5ed-125">CommonParameters</span></span>
<span data-ttu-id="6c5ed-126">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6c5ed-127">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6c5ed-128">輸入</span><span class="sxs-lookup"><span data-stu-id="6c5ed-128">INPUTS</span></span>

### <span data-ttu-id="6c5ed-129">無</span><span class="sxs-lookup"><span data-stu-id="6c5ed-129">None</span></span>
<span data-ttu-id="6c5ed-130">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-130">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6c5ed-131">輸出</span><span class="sxs-lookup"><span data-stu-id="6c5ed-131">OUTPUTS</span></span>

### <span data-ttu-id="6c5ed-132">System.string、VistaCultureInfo、</span><span class="sxs-lookup"><span data-stu-id="6c5ed-132">System.Globalization.CultureInfo, Microsoft.PowerShell.VistaCultureInfo</span></span>
<span data-ttu-id="6c5ed-133">**UICulture** 會傳回代表目前 UI 文化特性的物件。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-133">**Get-UICulture** returns an object that represents the current UI culture.</span></span>
<span data-ttu-id="6c5ed-134">在 Windows PowerShell 3.0 中，它會傳回 **CultureInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-134">In Windows PowerShell 3.0, it returns a **CultureInfo** object.</span></span>
<span data-ttu-id="6c5ed-135">在 Windows PowerShell 2.0 中，它會傳回 **VistaCultureInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-135">In Windows PowerShell 2.0, it returns a **VistaCultureInfo** object.</span></span>

## <span data-ttu-id="6c5ed-136">注意</span><span class="sxs-lookup"><span data-stu-id="6c5ed-136">NOTES</span></span>

* <span data-ttu-id="6c5ed-137">您也可以使用 $PsCulture 和 $PsUICulture 變數。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-137">You can also use the $PsCulture and $PsUICulture variables.</span></span> <span data-ttu-id="6c5ed-138">$PsCulture 變數會儲存目前文化特性的名稱，而 $PsUICulture 變數會儲存目前 UI 文化特性的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c5ed-138">The $PsCulture variable stores the name of the current culture, and the $PsUICulture variable stores the name of the current UI culture.</span></span>

*

## <span data-ttu-id="6c5ed-139">相關連結</span><span class="sxs-lookup"><span data-stu-id="6c5ed-139">RELATED LINKS</span></span>

## <span data-ttu-id="6c5ed-140">相關連結</span><span class="sxs-lookup"><span data-stu-id="6c5ed-140">RELATED LINKS</span></span>
