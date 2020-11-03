---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 1011011c8ce5471f976336e6b563f6d1662e17e4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201420"
---
# <span data-ttu-id="82f57-103">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="82f57-103">Remove-TypeData</span></span>

## <span data-ttu-id="82f57-104">概要</span><span class="sxs-lookup"><span data-stu-id="82f57-104">Synopsis</span></span>
<span data-ttu-id="82f57-105">從目前的工作階段刪除延伸類型。</span><span class="sxs-lookup"><span data-stu-id="82f57-105">Deletes extended types from the current session.</span></span>

## <span data-ttu-id="82f57-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="82f57-106">Syntax</span></span>

### <span data-ttu-id="82f57-107">RemoveTypeDataSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="82f57-107">RemoveTypeDataSet (Default)</span></span>

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82f57-108">RemoveTypeSet</span><span class="sxs-lookup"><span data-stu-id="82f57-108">RemoveTypeSet</span></span>

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82f57-109">RemoveFileSet</span><span class="sxs-lookup"><span data-stu-id="82f57-109">RemoveFileSet</span></span>

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="82f57-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="82f57-110">DESCRIPTION</span></span>

<span data-ttu-id="82f57-111">`Remove-TypeData`Cmdlet 會從目前的會話刪除延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="82f57-111">The `Remove-TypeData` cmdlet deletes extended type data from the current session.</span></span> <span data-ttu-id="82f57-112">此 Cmdlet 只會影響目前的工作階段和在目前工作階段中建立的工作階段。</span><span class="sxs-lookup"><span data-stu-id="82f57-112">This cmdlet affects only the current session and sessions that are created in the current session.</span></span>

<span data-ttu-id="82f57-113">您可以藉由在命令和檔案中定義來將屬性和方法新增至 PowerShell 中的物件 `Update-TypeData` `Types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-113">You can add properties and methods to objects in PowerShell by defining them in `Update-TypeData` commands and `Types.ps1xml` files.</span></span> <span data-ttu-id="82f57-114">`Remove-TypeData` 從目前的會話刪除這些擴充屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="82f57-114">`Remove-TypeData` deletes those extended properties and methods from the current session.</span></span> <span data-ttu-id="82f57-115">`Remove-TypeData` 不會刪除檔案，也不會 `Types.ps1xml` 刪除檔案中的任何延伸類型定義 `Types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-115">`Remove-TypeData` does not delete the `Types.ps1xml` files or delete any extended type definitions from the `Types.ps1xml` files.</span></span> <span data-ttu-id="82f57-116">如需檔案的詳細資訊 `Types.ps1xml` ，請參閱 [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="82f57-116">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).</span></span>

<span data-ttu-id="82f57-117">此 Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="82f57-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="82f57-118">範例</span><span class="sxs-lookup"><span data-stu-id="82f57-118">Examples</span></span>

### <span data-ttu-id="82f57-119">範例 1︰移除指定類型的類型資料</span><span class="sxs-lookup"><span data-stu-id="82f57-119">Example 1: Remove type data for a specified type</span></span>

<span data-ttu-id="82f57-120">此範例會從會話中刪除 system.string **類型的所有類型資料** ，包括檔案所新增的類型資料， `Types.ps1xml` 以及使用指令程式新增至會話的動態類型資料 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-120">This example deletes all type data for the **System.Array** type  from the session, including type data that was added by a `Types.ps1xml` file and dynamic type data that was added to the session by using the `Update-TypeData` cmdlet.</span></span>

```powershell
Remove-TypeData -TypeName System.Array
```

### <span data-ttu-id="82f57-121">範例 2︰從工作階段移除延伸的資料類型</span><span class="sxs-lookup"><span data-stu-id="82f57-121">Example 2: Remove an extended data type from a session</span></span>

<span data-ttu-id="82f57-122">此範例顯示從會話移除延伸類型資料的效果。</span><span class="sxs-lookup"><span data-stu-id="82f57-122">This example shows the effect of removing extended type data from a session.</span></span> <span data-ttu-id="82f57-123">第一個會 `Get-TypeData` 取得 system.string 類型的延伸 **System.DateTime** 類型資料。</span><span class="sxs-lookup"><span data-stu-id="82f57-123">The first `Get-TypeData` gets extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="82f57-124">輸出顯示已將 **DateTime** 屬性新增至 PowerShell 中 **的所有 system.string 物件。**</span><span class="sxs-lookup"><span data-stu-id="82f57-124">The output shows that a **DateTime** property has been added to all **System.DateTime** objects in PowerShell.</span></span> <span data-ttu-id="82f57-125">Cmdlet 會傳回 `Get-Date` **system.object** 物件。</span><span class="sxs-lookup"><span data-stu-id="82f57-125">The `Get-Date` cmdlet returns a **System.DateTime** object.</span></span> <span data-ttu-id="82f57-126">此命令會使用點標記法來取得傳回之 **system.string 物件的** **datetime** 屬性值 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-126">The command uses dot notation to get the value of the **DateTime** property of the **System.DateTime** object that `Get-Date` returns.</span></span>

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

<span data-ttu-id="82f57-127">下一個指令程式 `Get-TypeData` 可取得 system.string 類型的所有延伸 **System.DateTime** 類型資料，以及 Cmdlet 用來 `Remove-TypeData` 刪除延伸類型資料的管道。</span><span class="sxs-lookup"><span data-stu-id="82f57-127">The next `Get-TypeData` cmdlet to get all extended type data for the **System.DateTime** type and pipes that to the `Remove-TypeData` cmdlet to delete the extended type data.</span></span> <span data-ttu-id="82f57-128">最後一個 `Get-Date` Cmdlet 會顯示刪除 system.string 類型之延伸類型資料的效果 **System.DateTime** 。</span><span class="sxs-lookup"><span data-stu-id="82f57-128">The last `Get-Date` cmdlet shows the effect of deleting the extended type data for the **System.DateTime** type.</span></span> <span data-ttu-id="82f57-129">因為 system.string **屬性不再** 存在，所以取得其值的命令不會傳回任何內容。</span><span class="sxs-lookup"><span data-stu-id="82f57-129">Because the **System.DateTime** property no longer exists, a command to get its value returns nothing.</span></span>

### <span data-ttu-id="82f57-130">範例 3︰移除模組的延伸類型</span><span class="sxs-lookup"><span data-stu-id="82f57-130">Example 3: Remove extended types for modules</span></span>

<span data-ttu-id="82f57-131">此範例會移除模組物件的所有延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="82f57-131">This example removes all extended type data for module objects.</span></span> <span data-ttu-id="82f57-132">當您使用管線將物件傳送至時 `Remove-TypeData` ，會 `Remove-TypeData` 取得物件類型的名稱，並移除該類型所有物件的所有類型資料。</span><span class="sxs-lookup"><span data-stu-id="82f57-132">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the name of the object type and removes all type data for all objects of that type.</span></span>

```powershell
Get-Module | Remove-TypeData
```

### <span data-ttu-id="82f57-133">範例 4︰移除指定模組的延伸類型</span><span class="sxs-lookup"><span data-stu-id="82f57-133">Example 4: Remove extended types from specified modules</span></span>

<span data-ttu-id="82f57-134">此範例會使用 Cmdlet 的 **Path** 參數 `Remove-TypeData` ，移除 `Types.ps1xml` **PSScheduledJob** 和 **PSWorkflow** 模組所新增之檔案中定義的延伸類型。</span><span class="sxs-lookup"><span data-stu-id="82f57-134">This example uses the **Path** parameter of the `Remove-TypeData` cmdlet to remove the extended types that are defined in the `Types.ps1xml` files that are added by the **PSScheduledJob** and **PSWorkflow** modules.</span></span> <span data-ttu-id="82f57-135">此命令不會影響使用 Cmdlet 新增的動態類型資料 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-135">This command does not affect dynamic type data that is added by using the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="82f57-136">只有在模組已經匯入目前的工作階段時，命令才會成功。</span><span class="sxs-lookup"><span data-stu-id="82f57-136">The command succeeds only when the modules have been imported into the current session.</span></span>

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

<span data-ttu-id="82f57-137">如需模組的詳細資訊，請參閱 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="82f57-137">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

### <span data-ttu-id="82f57-138">範例 5：從遠端工作階段移除延伸類型</span><span class="sxs-lookup"><span data-stu-id="82f57-138">Example 5: Remove extended types from a remote session</span></span>

<span data-ttu-id="82f57-139">此範例會從遠端會話移除延伸類型。</span><span class="sxs-lookup"><span data-stu-id="82f57-139">This example removes extended types from a remote session.</span></span> <span data-ttu-id="82f57-140">此命令會使用 `Invoke-Command` Cmdlet 來移除變數中會話內所有 CIM 類型的延伸類型資料 `$S` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-140">The command uses the `Invoke-Command` cmdlet to remove extended type data for all CIM types in the sessions in the `$S` variable.</span></span>

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## <span data-ttu-id="82f57-141">參數</span><span class="sxs-lookup"><span data-stu-id="82f57-141">Parameters</span></span>

### <span data-ttu-id="82f57-142">-Path</span><span class="sxs-lookup"><span data-stu-id="82f57-142">-Path</span></span>

<span data-ttu-id="82f57-143">指定此 Cmdlet 要從工作階段刪除延伸類型資料之檔案的陣列。</span><span class="sxs-lookup"><span data-stu-id="82f57-143">Specifies an array of files that this cmdlet deletes from the session extended type data.</span></span> <span data-ttu-id="82f57-144">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="82f57-144">This parameter is required.</span></span>

<span data-ttu-id="82f57-145">輸入一或多個檔案的路徑和檔案名 `Types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-145">Enter the paths and file names of one or more `Types.ps1xml` files.</span></span> <span data-ttu-id="82f57-146">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="82f57-146">Wildcards are not supported.</span></span> <span data-ttu-id="82f57-147">若省略路徑，則預設位置為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="82f57-147">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82f57-148">-TypeData</span><span class="sxs-lookup"><span data-stu-id="82f57-148">-TypeData</span></span>

<span data-ttu-id="82f57-149">指定此 Cmdlet 要從工作階段中刪除的類型資料。</span><span class="sxs-lookup"><span data-stu-id="82f57-149">Specifies the type data that this cmdlet deletes from the session.</span></span> <span data-ttu-id="82f57-150">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="82f57-150">This parameter is required.</span></span> <span data-ttu-id="82f57-151">輸入包含 **TypeData** 物件的變數， ( **TypeData** ) ，或輸入可取得 **TypeData** 物件的命令，例如 `Get-TypeData` 命令。</span><span class="sxs-lookup"><span data-stu-id="82f57-151">Enter a variable that contains **TypeData** objects ( **System.Management.Automation.Runspaces.TypeData** ) or a command that gets **TypeData** objects, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="82f57-152">您也可以透過管線將 **TypeData** 物件傳送至 `Remove-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-152">You can also pipe **TypeData** objects to `Remove-TypeData`.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="82f57-153">-TypeName</span><span class="sxs-lookup"><span data-stu-id="82f57-153">-TypeName</span></span>

<span data-ttu-id="82f57-154">指定此 Cmdlet 要刪除所有延伸類型資料的類型。</span><span class="sxs-lookup"><span data-stu-id="82f57-154">Specifies the types that this cmdlet deletes all extended type data for.</span></span> <span data-ttu-id="82f57-155">對於系統命名空間中的類型，請輸入簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="82f57-155">For types in the System namespace, enter the short name.</span></span> <span data-ttu-id="82f57-156">否則，需要完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="82f57-156">Otherwise, the full type name is required.</span></span> <span data-ttu-id="82f57-157">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="82f57-157">Wildcards are not supported.</span></span>

<span data-ttu-id="82f57-158">您可以用管線將類型名稱傳送至 `Remove-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-158">You can pipe type names to `Remove-TypeData`.</span></span> <span data-ttu-id="82f57-159">當您使用管線將物件傳送至時 `Remove-TypeData` ，會 `Remove-TypeData` 取得物件的類型名稱，並移除物件類型的所有類型資料。</span><span class="sxs-lookup"><span data-stu-id="82f57-159">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="82f57-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="82f57-160">-Confirm</span></span>

<span data-ttu-id="82f57-161">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="82f57-161">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="82f57-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="82f57-162">-WhatIf</span></span>

<span data-ttu-id="82f57-163">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="82f57-163">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="82f57-164">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="82f57-164">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="82f57-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82f57-165">CommonParameters</span></span>

<span data-ttu-id="82f57-166">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="82f57-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82f57-167">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="82f57-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82f57-168">輸入</span><span class="sxs-lookup"><span data-stu-id="82f57-168">Inputs</span></span>

### <span data-ttu-id="82f57-169">System.Management.Automation.Runspaces.TypeData</span><span class="sxs-lookup"><span data-stu-id="82f57-169">System.Management.Automation.Runspaces.TypeData</span></span>

<span data-ttu-id="82f57-170">您可以透過管線將 **TypeData** 物件（例如 Cmdlet 所傳回的物件）傳送 `Get-TypeData` 至 `Remove-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-170">You can pipe **TypeData** object, such as the ones that the `Get-TypeData` cmdlet returns, to `Remove-TypeData`.</span></span>

### <span data-ttu-id="82f57-171">System.String</span><span class="sxs-lookup"><span data-stu-id="82f57-171">System.String</span></span>

<span data-ttu-id="82f57-172">您可以透過管道將類型名稱傳送至 `Remove-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="82f57-172">You can pipe the type names to `Remove-TypeData`.</span></span> <span data-ttu-id="82f57-173">當您使用管線將物件傳送至時 `Remove-TypeData` ，會 `Remove-TypeData` 取得物件的類型名稱，並移除物件類型的所有類型資料。</span><span class="sxs-lookup"><span data-stu-id="82f57-173">When you pipe an object to `Remove-TypeData`, `Remove-TypeData` gets the type name of the object and removes all type data for the object type.</span></span>

## <span data-ttu-id="82f57-174">輸出</span><span class="sxs-lookup"><span data-stu-id="82f57-174">Outputs</span></span>

### <span data-ttu-id="82f57-175">無</span><span class="sxs-lookup"><span data-stu-id="82f57-175">None</span></span>

<span data-ttu-id="82f57-176">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="82f57-176">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="82f57-177">備忘稿</span><span class="sxs-lookup"><span data-stu-id="82f57-177">Notes</span></span>

<span data-ttu-id="82f57-178">`Remove-TypeData` 只能移除目前會話中的延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="82f57-178">`Remove-TypeData` can remove only the extended type data in the current session.</span></span> <span data-ttu-id="82f57-179">它無法移除已在電腦上但尚未新增至目前工作階段的延伸類型資料，例如尚未匯入目前工作階段之模組中定義的延伸類型。</span><span class="sxs-lookup"><span data-stu-id="82f57-179">It cannot remove extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="82f57-180">相關連結</span><span class="sxs-lookup"><span data-stu-id="82f57-180">Related links</span></span>

[<span data-ttu-id="82f57-181">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="82f57-181">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="82f57-182">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="82f57-182">Update-TypeData</span></span>](Update-TypeData.md)
