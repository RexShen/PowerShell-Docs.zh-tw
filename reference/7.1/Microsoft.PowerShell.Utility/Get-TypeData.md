---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: 0a935f03e479ed84fa8167f7c4c29e91bd774009
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202796"
---
# <span data-ttu-id="bb4c5-103">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="bb4c5-103">Get-TypeData</span></span>

## <span data-ttu-id="bb4c5-104">概要</span><span class="sxs-lookup"><span data-stu-id="bb4c5-104">Synopsis</span></span>
<span data-ttu-id="bb4c5-105">取得目前工作階段中的延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-105">Gets the extended type data in the current session.</span></span>

## <span data-ttu-id="bb4c5-106">語法</span><span class="sxs-lookup"><span data-stu-id="bb4c5-106">Syntax</span></span>

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="bb4c5-107">描述</span><span class="sxs-lookup"><span data-stu-id="bb4c5-107">Description</span></span>

<span data-ttu-id="bb4c5-108">`Get-TypeData`Cmdlet 會取得目前會話中的延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-108">The `Get-TypeData` cmdlet gets the extended type data in the current session.</span></span> <span data-ttu-id="bb4c5-109">這包括依檔案新增到會話的類型資料 `Types.ps1xml` ，以及使用 Cmdlet 的參數新增的動態類型資料 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-109">This includes type data that was added to the session by `Types.ps1xml` file and dynamic type data that was added by using the parameter of the `Update-TypeData` cmdlet.</span></span>

<span data-ttu-id="bb4c5-110">您可以使用傳回的延伸類型資料 `Get-TypeData` 來檢查會話中的類型資料，並將其傳送至 `Update-TypeData` 和 `Remove-TypeData` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-110">You can use the extended type data that `Get-TypeData` returns to examine the type data in the session and send it to the `Update-TypeData` and `Remove-TypeData` cmdlets.</span></span>

<span data-ttu-id="bb4c5-111">延伸類型資料會將屬性和方法新增至 PowerShell 中的物件。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-111">Extended type data adds properties and methods to objects in PowerShell.</span></span> <span data-ttu-id="bb4c5-112">您可以比照使用物件類型中定義之屬性和方法的方式，來使用新增的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-112">You can use the added properties and methods in the same ways that you would use the properties and methods that are defined in the object type.</span></span> <span data-ttu-id="bb4c5-113">不過，在撰寫腳本時，請注意，新增的屬性和方法可能不會出現在每個 PowerShell 會話中。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-113">However, when writing scripts, be aware that the added properties and methods might not be present in every PowerShell session.</span></span>

<span data-ttu-id="bb4c5-114">如需檔案的詳細資訊 `Types.ps1xml` ，請參閱 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-114">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span> <span data-ttu-id="bb4c5-115">如需 Cmdlet 新增之動態類型資料的詳細資訊 `Update-TypeData` ，請參閱 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-115">For more information about dynamic type data that the `Update-TypeData` cmdlet adds, see `Update-TypeData`.</span></span>

<span data-ttu-id="bb4c5-116">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="bb4c5-117">範例</span><span class="sxs-lookup"><span data-stu-id="bb4c5-117">Examples</span></span>

### <span data-ttu-id="bb4c5-118">範例1：取得所有延伸類型資料</span><span class="sxs-lookup"><span data-stu-id="bb4c5-118">Example 1: Get all extended type data</span></span>

<span data-ttu-id="bb4c5-119">這個範例會取得目前會話中的所有延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-119">This example gets all extended type data in the current session.</span></span>

 ```powershell
Get-TypeData
```

### <span data-ttu-id="bb4c5-120">範例2：依名稱取得類型</span><span class="sxs-lookup"><span data-stu-id="bb4c5-120">Example 2: Get types by name</span></span>

<span data-ttu-id="bb4c5-121">這個範例會取得目前會話中名稱包含事件的所有類型。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-121">This example gets all types in the current session that have names that contain Eventing.</span></span>

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### <span data-ttu-id="bb4c5-122">範例3：取得用來建立屬性值的腳本區塊</span><span class="sxs-lookup"><span data-stu-id="bb4c5-122">Example 3: Get the script block that creates a property value</span></span>

<span data-ttu-id="bb4c5-123">這個範例會取得腳本區塊，以建立 **EventLogEntry** 物件之 **EventID** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-123">This example gets the script block that creates the value of the **EventID** property of **EventLogEntry** objects.</span></span>

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### <span data-ttu-id="bb4c5-124">範例4：取得定義指定物件之屬性的腳本區塊</span><span class="sxs-lookup"><span data-stu-id="bb4c5-124">Example 4: Get the script block that defines a property for a specified object</span></span>

<span data-ttu-id="bb4c5-125">這個範例會取得腳本區塊，以定義 PowerShell 中 system.string **物件的** **datetime** 屬性。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-125">This example gets the script block that defines the **DateTime** property of **System.DateTime** objects in PowerShell.</span></span>

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

<span data-ttu-id="bb4c5-126">此命令會使用 `Get-TypeData` Cmdlet 來取得 **DataTime** 類型的延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-126">The command uses the `Get-TypeData` cmdlet to get the extended type data for the **System.DataTime** type.</span></span> <span data-ttu-id="bb4c5-127">此命令取得 **TypeData** 物件的 **Members** 屬性。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-127">The command gets the **Members** property of the **TypeData** object.</span></span>

<span data-ttu-id="bb4c5-128">**Members** 屬性包含由延伸類型資料所定義之屬性和方法的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-128">The **Members** property contains a hash table of properties and methods that are defined by extended type data.</span></span> <span data-ttu-id="bb4c5-129">Members 雜湊表中的每個索引鍵都是一個屬性或方法的名稱，而每個值則是該屬性或方法值的定義。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-129">Each key in the Members hash table is a property or method name and each value is the definition of the property or method value.</span></span>

<span data-ttu-id="bb4c5-130">此命令會取得 **成員** 及其 **GetScriptBlock** 屬性值中的 **日期時間** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-130">The command gets the **DateTime** key in **Members** and its **GetScriptBlock** property value.</span></span>

<span data-ttu-id="bb4c5-131">輸出會顯示腳本區塊，此區塊會在 PowerShell 中 **建立每個** system.string 物件的 **datetime** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-131">The output shows the script block that creates the value of the **DateTime** property of every **System.DateTime** object in PowerShell.</span></span>

## <span data-ttu-id="bb4c5-132">參數</span><span class="sxs-lookup"><span data-stu-id="bb4c5-132">Parameters</span></span>

### <span data-ttu-id="bb4c5-133">-TypeName</span><span class="sxs-lookup"><span data-stu-id="bb4c5-133">-TypeName</span></span>

<span data-ttu-id="bb4c5-134">只針對具有指定名稱的類型，將類型資料指定為數組。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-134">Specifies type data as an array only for the types with the specified names.</span></span> <span data-ttu-id="bb4c5-135">依預設，會 `Get-TypeData` 取得會話中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-135">By default, `Get-TypeData` gets all types in the session.</span></span>

<span data-ttu-id="bb4c5-136">請輸入類型名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-136">Enter type names or a name patterns.</span></span> <span data-ttu-id="bb4c5-137">即使是 System 命名空間中的類型，還是需要具有萬用字元的完整名稱或名稱模式。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-137">Full names, or name patterns with wildcard characters are required, even for types in the System namespace.</span></span> <span data-ttu-id="bb4c5-138">支援萬用字元，且參數名稱 **TypeName** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-138">Wildcards are supported and the parameter name **TypeName** is optional.</span></span> <span data-ttu-id="bb4c5-139">您也可以透過管道將類型名稱傳送至 `Get-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-139">You can also pipe type names to `Get-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="bb4c5-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb4c5-140">CommonParameters</span></span>

<span data-ttu-id="bb4c5-141">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb4c5-142">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb4c5-143">輸入</span><span class="sxs-lookup"><span data-stu-id="bb4c5-143">Inputs</span></span>

### <span data-ttu-id="bb4c5-144">System.String</span><span class="sxs-lookup"><span data-stu-id="bb4c5-144">System.String</span></span>

<span data-ttu-id="bb4c5-145">您可以用管線將類型名稱傳送至 `Get-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-145">You can pipe type names to `Get-TypeData`.</span></span>

## <span data-ttu-id="bb4c5-146">輸出</span><span class="sxs-lookup"><span data-stu-id="bb4c5-146">Outputs</span></span>

### <span data-ttu-id="bb4c5-147">System.Management.Automation.Runspaces.TypeData</span><span class="sxs-lookup"><span data-stu-id="bb4c5-147">System.Management.Automation.Runspaces.TypeData</span></span>

## <span data-ttu-id="bb4c5-148">備忘稿</span><span class="sxs-lookup"><span data-stu-id="bb4c5-148">Notes</span></span>

<span data-ttu-id="bb4c5-149">`Get-TypeData` 只取得目前會話中的延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-149">`Get-TypeData` gets only the extended type data in the current session.</span></span> <span data-ttu-id="bb4c5-150">它不會取得已在電腦上但尚未新增至目前工作階段的延伸類型資料，例如尚未匯入目前工作階段之模組中定義的延伸類型。</span><span class="sxs-lookup"><span data-stu-id="bb4c5-150">It does not get extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="bb4c5-151">相關連結</span><span class="sxs-lookup"><span data-stu-id="bb4c5-151">Related links</span></span>

[<span data-ttu-id="bb4c5-152">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="bb4c5-152">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="bb4c5-153">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="bb4c5-153">Remove-TypeData</span></span>](Remove-TypeData.md)

[<span data-ttu-id="bb4c5-154">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="bb4c5-154">Update-TypeData</span></span>](Update-TypeData.md)

