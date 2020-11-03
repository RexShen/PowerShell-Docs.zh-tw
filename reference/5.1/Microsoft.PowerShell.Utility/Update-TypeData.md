---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: eb7bafff1af34ef34a1b67c1fbe8f9e2db0ca7ad
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203096"
---
# <span data-ttu-id="af6bf-103">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="af6bf-103">Update-TypeData</span></span>

## <span data-ttu-id="af6bf-104">概要</span><span class="sxs-lookup"><span data-stu-id="af6bf-104">Synopsis</span></span>
<span data-ttu-id="af6bf-105">更新工作階段中的延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="af6bf-105">Updates the extended type data in the session.</span></span>

## <span data-ttu-id="af6bf-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="af6bf-106">Syntax</span></span>

### <span data-ttu-id="af6bf-107">FileSet (預設) </span><span class="sxs-lookup"><span data-stu-id="af6bf-107">FileSet (Default)</span></span>

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="af6bf-108">DynamicTypeSet</span><span class="sxs-lookup"><span data-stu-id="af6bf-108">DynamicTypeSet</span></span>

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="af6bf-109">TypeDataSet</span><span class="sxs-lookup"><span data-stu-id="af6bf-109">TypeDataSet</span></span>

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="af6bf-110">Description</span><span class="sxs-lookup"><span data-stu-id="af6bf-110">Description</span></span>

<span data-ttu-id="af6bf-111">指令 `Update-TypeData` 程式會藉由將檔案重載 `Types.ps1xml` 到記憶體並新增延伸類型資料，來更新會話中的延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="af6bf-111">The `Update-TypeData` cmdlet updates the extended type data in the session by reloading the `Types.ps1xml` files into memory and adding new extended type data.</span></span>

<span data-ttu-id="af6bf-112">根據預設，PowerShell 會在需要時載入延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="af6bf-112">By default, PowerShell loads extended type data as it is needed.</span></span> <span data-ttu-id="af6bf-113">如果沒有參數，會 `Update-TypeData` 重載 `Types.ps1xml` 已載入會話中的所有檔案，包括您新增的任何類型檔案。</span><span class="sxs-lookup"><span data-stu-id="af6bf-113">Without parameters, `Update-TypeData` reloads all of the `Types.ps1xml` files that it has loaded in the session, including any type files that you added.</span></span> <span data-ttu-id="af6bf-114">您可以使用的參數 `Update-TypeData` 加入新的類型檔案，以及加入和取代延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="af6bf-114">You can use the parameters of `Update-TypeData` to add new type files and add and replace extended type data.</span></span>

<span data-ttu-id="af6bf-115">`Update-TypeData`Cmdlet 可以用來預先載入所有類型資料。</span><span class="sxs-lookup"><span data-stu-id="af6bf-115">The `Update-TypeData` cmdlet can be used to preload all type data.</span></span> <span data-ttu-id="af6bf-116">當您正在開發類型並且想要基於測試目的載入這些新的類型，這個功能就特別有用。</span><span class="sxs-lookup"><span data-stu-id="af6bf-116">This feature is particularly useful when you are developing types and want to load those new types for testing purposes.</span></span>

<span data-ttu-id="af6bf-117">從 Windows PowerShell 3.0 開始，您可以在 `Update-TypeData` 不使用檔案的情況下，使用來新增及取代會話中的延伸類型資料 `Types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-117">Beginning in Windows PowerShell 3.0, you can use `Update-TypeData` to add and replace extended type data in the session without using a `Types.ps1xml` file.</span></span> <span data-ttu-id="af6bf-118">動態方式加入的類型資料 (也就是不具有檔案) 僅新增到目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="af6bf-118">Type data that is added dynamically, that is, without a file, is added only to the current session.</span></span> <span data-ttu-id="af6bf-119">若要將類型資料新增到所有會話，請將 `Update-TypeData` 命令新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="af6bf-119">To add the type data to all sessions, add an `Update-TypeData` command to your PowerShell profile.</span></span> <span data-ttu-id="af6bf-120">如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="af6bf-120">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="af6bf-121">此外，從 Windows PowerShell 3.0 開始，您可以使用 `Get-TypeData` Cmdlet 取得目前會話中的延伸類型，以及使用 `Remove-TypeData` Cmdlet 從目前的會話刪除延伸類型。</span><span class="sxs-lookup"><span data-stu-id="af6bf-121">Also, beginning in Windows PowerShell 3.0, you can use the `Get-TypeData` cmdlet to get the extended types in the current session and the `Remove-TypeData` cmdlet to delete extended types from the current session.</span></span>

<span data-ttu-id="af6bf-122">在屬性中發生的例外狀況，或是將屬性新增至命令時， `Update-TypeData` 不會報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="af6bf-122">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors.</span></span> <span data-ttu-id="af6bf-123">這是為了在進行格式化與輸出期間，抑制在許多常見類型中可能會出現的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="af6bf-123">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="af6bf-124">如果您要取得 .NET 屬性，可以改為使用方法語法來解決例外狀況的隱藏，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="af6bf-124">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

`"hello".get_Length()`

<span data-ttu-id="af6bf-125">請注意，方法語法只能與 .NET 屬性搭配使用。</span><span class="sxs-lookup"><span data-stu-id="af6bf-125">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="af6bf-126">藉由執行 Cmdlet 所新增的屬性 `Update-TypeData` 無法使用方法語法。</span><span class="sxs-lookup"><span data-stu-id="af6bf-126">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

<span data-ttu-id="af6bf-127">如需 PowerShell 中檔案的詳細資訊 `Types.ps1xml` ，請參閱 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="af6bf-127">For more information about the `Types.ps1xml` files in PowerShell, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

## <span data-ttu-id="af6bf-128">範例</span><span class="sxs-lookup"><span data-stu-id="af6bf-128">Examples</span></span>

### <span data-ttu-id="af6bf-129">範例1：更新擴充類型</span><span class="sxs-lookup"><span data-stu-id="af6bf-129">Example 1: Update extended types</span></span>

```powershell
Update-TypeData
```

<span data-ttu-id="af6bf-130">此命令會從已 `Types.ps1xml` 在會話中使用的檔案更新擴充類型設定。</span><span class="sxs-lookup"><span data-stu-id="af6bf-130">This command updates the extended type configuration from the `Types.ps1xml` files that have already been used in the session.</span></span>

### <span data-ttu-id="af6bf-131">範例2：多次更新類型</span><span class="sxs-lookup"><span data-stu-id="af6bf-131">Example 2: Update types multiple times</span></span>

<span data-ttu-id="af6bf-132">此範例顯示如何在相同的會話中多次更新類型檔案中的類型。</span><span class="sxs-lookup"><span data-stu-id="af6bf-132">This example shows how to update the types in a type file multiple times in the same session.</span></span>

<span data-ttu-id="af6bf-133">第一個命令會從檔案更新擴充類型設定 `Types.ps1xml` ， `TypesA.types.ps1xml` 並先處理和檔案 `TypesB.types.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-133">The first command updates the extended type configuration from the `Types.ps1xml` files, processing the `TypesA.types.ps1xml` and `TypesB.types.ps1xml` files first.</span></span>

<span data-ttu-id="af6bf-134">第二個命令會顯示如何 `TypesA.types.ps1xml` 再次更新，例如，如果您在檔案中新增或變更類型，您可能會這麼做。</span><span class="sxs-lookup"><span data-stu-id="af6bf-134">The second command shows how to update the `TypesA.types.ps1xml` again, such as you might do if you added or changed a type in the file.</span></span> <span data-ttu-id="af6bf-135">您可以針對檔案重複上述命令 `TypesA.types.ps1xml` ，或執行 `Update-TypeData` 不含參數的命令，因為 `TypesA.types.ps1xml` 已經在目前會話的類型檔案清單中。</span><span class="sxs-lookup"><span data-stu-id="af6bf-135">You can either repeat the previous command for the `TypesA.types.ps1xml` file, or run an `Update-TypeData` command without parameters, because `TypesA.types.ps1xml` is already in the type file list for the current session.</span></span>

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### <span data-ttu-id="af6bf-136">範例3：將腳本屬性加入至 DateTime 物件</span><span class="sxs-lookup"><span data-stu-id="af6bf-136">Example 3: Add a script property to DateTime objects</span></span>

<span data-ttu-id="af6bf-137">這個範例會使用將 `Update-TypeData` **季** 腳本屬性新增到目前會話中的 **system.object** 物件，例如 Cmdlet 所傳回的物件。 `Get-Date`</span><span class="sxs-lookup"><span data-stu-id="af6bf-137">This example uses `Update-TypeData` to add the **Quarter** script property to **System.DateTime** objects in the current session, such as those returned by the `Get-Date` cmdlet.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

<span data-ttu-id="af6bf-138">此 `Update-TypeData` 命令會使用 **TypeName** 參數來指定 **the System.DateTime** system.string 類型、 **成員** 名稱參數，以指定新屬性的名稱、使用 **MemberType** 屬性指定 **ScriptProperty** 類型，並使用 **Value** 參數來指定決定年度季的腳本。</span><span class="sxs-lookup"><span data-stu-id="af6bf-138">The `Update-TypeData` command uses the **TypeName** parameter to specify **the System.DateTime** type, the **MemberName** parameter to specify a name for the new property, the **MemberType** property to specify the **ScriptProperty** type, and the **Value** parameter to specify the script that determines the annual quarter.</span></span>

<span data-ttu-id="af6bf-139">**Value** 屬性的值為計算目前年度季別的指令碼。</span><span class="sxs-lookup"><span data-stu-id="af6bf-139">The value of the **Value** property is a script that calculates the current annual quarter.</span></span> <span data-ttu-id="af6bf-140">腳本區塊 `$this` 會使用自動變數來代表物件目前的實例，並使用 In 運算子來判斷月份值是否出現在每個整數陣列中。</span><span class="sxs-lookup"><span data-stu-id="af6bf-140">The script block uses the `$this` automatic variable to represent the current instance of the object and the In operator to determine whether the month value appears in each integer array.</span></span> <span data-ttu-id="af6bf-141">如需有關運算子的詳細資訊 `-in` ，請參閱 [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="af6bf-141">For more information about the `-in` operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).</span></span>

<span data-ttu-id="af6bf-142">第二個命令會取得目前日期的新 Quarter 屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-142">The second command gets the new Quarter property of the current date.</span></span>

### <span data-ttu-id="af6bf-143">範例4：依預設，更新清單中顯示的類型</span><span class="sxs-lookup"><span data-stu-id="af6bf-143">Example 4: Update a type that displays in lists by default</span></span>

<span data-ttu-id="af6bf-144">這個範例示範如何設定依預設顯示在清單中的類型屬性，也就是未指定屬性時。</span><span class="sxs-lookup"><span data-stu-id="af6bf-144">This example shows how to set the properties of a type that displays in lists by default, that is, when no properties are specified.</span></span> <span data-ttu-id="af6bf-145">因為類型資料不是在檔案中指定 `Types.ps1xml` ，所以它只會在目前的會話中生效。</span><span class="sxs-lookup"><span data-stu-id="af6bf-145">Because the type data is not specified in a `Types.ps1xml` file, it is effective only in the current session.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

<span data-ttu-id="af6bf-146">第一個命令會使用指令 `Update-TypeData` 程式來設定 **System. DateTime** 類型的預設清單屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-146">The first command uses the `Update-TypeData` cmdlet to set the default list properties for the **System.DateTime** type.</span></span> <span data-ttu-id="af6bf-147">此命令使用 **TypeName** 參數來指定類型和 **DefaultDisplayPropertySet** 參數來指定預設清單屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-147">The command uses the **TypeName** parameter to specify the type and the **DefaultDisplayPropertySet** parameter to specify the default properties for a list.</span></span> <span data-ttu-id="af6bf-148">選取的屬性包含上一個範例中所加入的新 **季** 腳本屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-148">The selected properties include the new **Quarter** script property that was added in a previous example.</span></span>

<span data-ttu-id="af6bf-149">第二個命令 `Get-Date` 會使用 Cmdlet 取得代表目前日期 **的 system.string** 物件。</span><span class="sxs-lookup"><span data-stu-id="af6bf-149">The second command uses the `Get-Date` cmdlet to get a **System.DateTime** object that represents the current date.</span></span> <span data-ttu-id="af6bf-150">此命令會使用管線運算子 (`|`) 將 **DateTime** 物件傳送至 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="af6bf-150">The command uses a pipeline operator (`|`) to send the **DateTime** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="af6bf-151">由於 `Format-List` 命令未指定要顯示在清單中的屬性，因此 PowerShell 會使用命令所建立的預設值 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-151">Because the `Format-List` command does not specify the properties to display in the list, PowerShell uses the default values that were established by the `Update-TypeData` command.</span></span>

### <span data-ttu-id="af6bf-152">範例5：更新管道物件的類型資料</span><span class="sxs-lookup"><span data-stu-id="af6bf-152">Example 5: Update type data for a piped object</span></span>

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

<span data-ttu-id="af6bf-153">這個範例示範當您使用管線將物件傳送至時 `Update-TypeData` ，會 `Update-TypeData` 加入物件類型的延伸類型資料。</span><span class="sxs-lookup"><span data-stu-id="af6bf-153">This example demonstrates that when you pipe an object to `Update-TypeData`, `Update-TypeData` adds extended type data for the object type.</span></span>

<span data-ttu-id="af6bf-154">這項技術比使用 `Get-Member` Cmdlet 或 `Get-Type` 方法來取得物件類型更快。</span><span class="sxs-lookup"><span data-stu-id="af6bf-154">This technique is quicker than using the `Get-Member` cmdlet or the `Get-Type` method to get the object type.</span></span> <span data-ttu-id="af6bf-155">但是，如果您使用管線將物件集合傳送到 `Update-TypeData` ，它會更新第一個物件類型的類型資料，然後針對集合中的所有其他物件傳回錯誤，因為該類型上已經定義該成員。</span><span class="sxs-lookup"><span data-stu-id="af6bf-155">However, if you pipe a collection of objects to `Update-TypeData`, it updates the type data of the first object type and then returns an error for all other objects in the collection because the member is already defined on the type.</span></span>

<span data-ttu-id="af6bf-156">第一個命令會使用 `Get-Module` Cmdlet 來取得 PSScheduledJob 模組。</span><span class="sxs-lookup"><span data-stu-id="af6bf-156">The first command uses the `Get-Module` cmdlet to get the PSScheduledJob module.</span></span> <span data-ttu-id="af6bf-157">此命令會使用管線將模組物件傳送至 `Update-TypeData` Cmdlet，此 Cmdlet 會更新 **PSModuleInfo** 類型的類型資料，以及從中衍生的類型，例如 `Get-Module` 當您在命令中使用 **ListAvailable** 參數時所傳回的 ModuleInfoGrouping 類型。</span><span class="sxs-lookup"><span data-stu-id="af6bf-157">The command pipes the module object to the `Update-TypeData` cmdlet, which updates the type data for the **System.Management.Automation.PSModuleInfo** type and the types derived from it, such as the ModuleInfoGrouping type that `Get-Module` returns when you use the **ListAvailable** parameter in the command.</span></span>

<span data-ttu-id="af6bf-158">這些 `Update-TypeData` 命令會將 **SupportsUpdatableHelp** 腳本屬性新增至所有匯入的模組。</span><span class="sxs-lookup"><span data-stu-id="af6bf-158">The `Update-TypeData` commands adds the **SupportsUpdatableHelp** script property to all imported modules.</span></span> <span data-ttu-id="af6bf-159">**Value** `$True` 如果已填入模組的 **HelpInfoUri** 屬性，則 value 參數的值為會傳回的腳本 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-159">The value of the **Value** parameter is a script that returns `$True` if the **HelpInfoUri** property of the module is populated and `$False` otherwise.</span></span>

<span data-ttu-id="af6bf-160">第二個命令會使用管線將模組物件傳送 `Get-Module` 至 `Format-Table` Cmdlet，此 Cmdlet 會顯示清單中所有模組的 **Name** 和 **SupportsUpdatableHelp** 屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-160">The second command pipes the module objects from `Get-Module` to the `Format-Table` cmdlet, which displays the **Name** and **SupportsUpdatableHelp** properties of all modules in a list.</span></span>

## <span data-ttu-id="af6bf-161">參數</span><span class="sxs-lookup"><span data-stu-id="af6bf-161">Parameters</span></span>

### <span data-ttu-id="af6bf-162">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="af6bf-162">-AppendPath</span></span>

<span data-ttu-id="af6bf-163">指定選用檔案的路徑 `.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-163">Specifies the path to optional `.ps1xml` files.</span></span> <span data-ttu-id="af6bf-164">指定的檔案會依載入內建檔案之後所列出的順序載入。</span><span class="sxs-lookup"><span data-stu-id="af6bf-164">The specified files are loaded in the order that they are listed after the built-in files are loaded.</span></span> <span data-ttu-id="af6bf-165">您也可以使用管線將 **AppendPath** 值傳送至 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-165">You can also pipe an **AppendPath** value to `Update-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-166">-DefaultDisplayProperty</span><span class="sxs-lookup"><span data-stu-id="af6bf-166">-DefaultDisplayProperty</span></span>

<span data-ttu-id="af6bf-167">指定 `Format-Wide` 當未指定其他屬性時，Cmdlet 所顯示的型別的屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-167">Specifies the property of the type that is displayed by the `Format-Wide` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="af6bf-168">輸入類型的標準或延伸屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-168">Type the name of a standard or extended property of the type.</span></span> <span data-ttu-id="af6bf-169">此參數的值可以是相同命令中新增之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-169">The value of this parameter can be the name of a type that is added in the same command.</span></span>

<span data-ttu-id="af6bf-170">只有在檔案中沒有針對型別定義任何寬度的視圖時，此值才會生效 `Format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-170">This value is effective only when there are no wide views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="af6bf-171">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-171">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-172">-DefaultDisplayPropertySet</span><span class="sxs-lookup"><span data-stu-id="af6bf-172">-DefaultDisplayPropertySet</span></span>

<span data-ttu-id="af6bf-173">指定類型的一或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-173">Specifies one or more properties of the type.</span></span> <span data-ttu-id="af6bf-174">`Format-List`如果未指定其他屬性，Cmdlet 會顯示這些屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-174">These properties are displayed by the `Format-List` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="af6bf-175">輸入類型的標準或延伸屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-175">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="af6bf-176">此參數的值可以是相同命令中新增之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-176">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="af6bf-177">只有在檔案中沒有針對類型定義清單視圖時，此值才會生效 `Format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-177">This value is effective only when there are no list views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="af6bf-178">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-178">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-179">-DefaultKeyPropertySet</span><span class="sxs-lookup"><span data-stu-id="af6bf-179">-DefaultKeyPropertySet</span></span>

<span data-ttu-id="af6bf-180">指定類型的一或多個屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-180">Specifies one or more properties of the type.</span></span> <span data-ttu-id="af6bf-181">`Group-Object` `Sort-Object` 當沒有指定其他屬性時，和 Cmdlet 會使用這些屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-181">These properties are used by the `Group-Object` and `Sort-Object` cmdlets when no other properties are specified.</span></span>

<span data-ttu-id="af6bf-182">輸入類型的標準或延伸屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-182">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="af6bf-183">此參數的值可以是相同命令中新增之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-183">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="af6bf-184">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-184">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-185">-Force</span><span class="sxs-lookup"><span data-stu-id="af6bf-185">-Force</span></span>

<span data-ttu-id="af6bf-186">指出此 Cmdlet 會使用指定的類型資料，即使已經為該類型指定類型資料。</span><span class="sxs-lookup"><span data-stu-id="af6bf-186">Indicates that the cmdlet uses the specified type data, even if type data has already been specified for that type.</span></span>

<span data-ttu-id="af6bf-187">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-187">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-188">-InheritPropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="af6bf-188">-InheritPropertySerializationSet</span></span>

<span data-ttu-id="af6bf-189">指出是否繼承已序列化的屬性集。</span><span class="sxs-lookup"><span data-stu-id="af6bf-189">Indicates whether the set of properties that are serialized is inherited.</span></span> <span data-ttu-id="af6bf-190">預設值是 `$Null`。</span><span class="sxs-lookup"><span data-stu-id="af6bf-190">The default value is `$Null`.</span></span> <span data-ttu-id="af6bf-191">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="af6bf-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="af6bf-192">`$True`.</span><span class="sxs-lookup"><span data-stu-id="af6bf-192">`$True`.</span></span> <span data-ttu-id="af6bf-193">已繼承屬性集。</span><span class="sxs-lookup"><span data-stu-id="af6bf-193">The property set is inherited.</span></span>
- <span data-ttu-id="af6bf-194">`$False`.</span><span class="sxs-lookup"><span data-stu-id="af6bf-194">`$False`.</span></span> <span data-ttu-id="af6bf-195">未繼承屬性集。</span><span class="sxs-lookup"><span data-stu-id="af6bf-195">The property set is not inherited.</span></span>
- <span data-ttu-id="af6bf-196">`$Null`.</span><span class="sxs-lookup"><span data-stu-id="af6bf-196">`$Null`.</span></span> <span data-ttu-id="af6bf-197">未定義繼承。</span><span class="sxs-lookup"><span data-stu-id="af6bf-197">Inheritance is not defined.</span></span>

<span data-ttu-id="af6bf-198">只有當 **SerializationMethod** 參數的值為時，此參數才有效 `SpecificProperties` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-198">This parameter is valid only when the value of the **SerializationMethod** parameter is `SpecificProperties`.</span></span> <span data-ttu-id="af6bf-199">當此參數的值為時 `$False` ，需要 **PropertySerializationSet** 參數。</span><span class="sxs-lookup"><span data-stu-id="af6bf-199">When the value of this parameter is `$False`, the **PropertySerializationSet** parameter is required.</span></span>

<span data-ttu-id="af6bf-200">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-200">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-201">-成員名稱</span><span class="sxs-lookup"><span data-stu-id="af6bf-201">-MemberName</span></span>

<span data-ttu-id="af6bf-202">指定屬性或方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-202">Specifies the name of a property or method.</span></span>

<span data-ttu-id="af6bf-203">使用此參數與 **TypeName** 、 **MemberType** 、 **Value** 及 **SecondValue** 參數，新增或變更類型的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="af6bf-203">Use this parameter with the **TypeName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="af6bf-204">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-205">-MemberType</span><span class="sxs-lookup"><span data-stu-id="af6bf-205">-MemberType</span></span>

<span data-ttu-id="af6bf-206">指定要新增或變更的成員類型。</span><span class="sxs-lookup"><span data-stu-id="af6bf-206">Specifies the type of the member to add or change.</span></span>

<span data-ttu-id="af6bf-207">使用此參數與 **TypeName** 、 **MemberType** 、 **Value** 及 **SecondValue** 參數，新增或變更類型的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="af6bf-207">Use this parameter with the **TypeName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span> <span data-ttu-id="af6bf-208">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="af6bf-208">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="af6bf-209">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="af6bf-209">AliasProperty</span></span>
- <span data-ttu-id="af6bf-210">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="af6bf-210">CodeMethod</span></span>
- <span data-ttu-id="af6bf-211">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="af6bf-211">CodeProperty</span></span>
- <span data-ttu-id="af6bf-212">Noteproperty</span><span class="sxs-lookup"><span data-stu-id="af6bf-212">Noteproperty</span></span>
- <span data-ttu-id="af6bf-213">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="af6bf-213">ScriptMethod</span></span>
- <span data-ttu-id="af6bf-214">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="af6bf-214">ScriptProperty</span></span>

<span data-ttu-id="af6bf-215">如需這些值的詳細資訊，請參閱 [ Psmembertypes 列舉](/dotnet/api/system.management.automation.psmembertypes)。</span><span class="sxs-lookup"><span data-stu-id="af6bf-215">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes).</span></span>

<span data-ttu-id="af6bf-216">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-216">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-217">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="af6bf-217">-PrependPath</span></span>

<span data-ttu-id="af6bf-218">指定選用檔案的路徑 `.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-218">Specifies the path to the optional `.ps1xml` files.</span></span> <span data-ttu-id="af6bf-219">指定的檔案會依載入內建檔案之前所列出的順序載入。</span><span class="sxs-lookup"><span data-stu-id="af6bf-219">The specified files are loaded in the order that they are listed before the built-in files are loaded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-220">-PropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="af6bf-220">-PropertySerializationSet</span></span>

<span data-ttu-id="af6bf-221">指定已序列化的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-221">Specifies the names of properties that are serialized.</span></span> <span data-ttu-id="af6bf-222">當 **SerializationMethod** 參數的值為 **SpecificProperties** 時使用此參數。</span><span class="sxs-lookup"><span data-stu-id="af6bf-222">Use this parameter when the value of the **SerializationMethod** parameter is **SpecificProperties** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-223">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="af6bf-223">-SecondValue</span></span>

<span data-ttu-id="af6bf-224">指定 **AliasProperty** 、 **ScriptProperty** 、 **CodeProperty** 或 **CodeMethod** 成員的額外值。</span><span class="sxs-lookup"><span data-stu-id="af6bf-224">Specifies additional values for **AliasProperty** , **ScriptProperty** , **CodeProperty** , or **CodeMethod** members.</span></span>

<span data-ttu-id="af6bf-225">使用此參數搭配 **TypeName** 、 **MemberType** 、 **Value** 和 **SecondValue** 參數，以新增或變更類型的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="af6bf-225">Use this parameter with the **TypeName** , **MemberType** , **Value** , and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="af6bf-226">當 **MemberType** 參數的值為時 `AliasProperty` ， **SecondValue** 參數的值必須是資料類型。</span><span class="sxs-lookup"><span data-stu-id="af6bf-226">When the value of the **MemberType** parameter is `AliasProperty`, the value of the **SecondValue** parameter must be a data type.</span></span> <span data-ttu-id="af6bf-227">PowerShell 會將 (轉換為，將別名屬性的值) 轉換為指定的類型。</span><span class="sxs-lookup"><span data-stu-id="af6bf-227">PowerShell converts (that is, casts) the value of the alias property to the specified type.</span></span> <span data-ttu-id="af6bf-228">例如，如果您加入一個別名屬性來為字串屬性提供替代名稱，您也可以指定 **system.string 的** **SecondValue** ，將別名字串值轉換為整數。</span><span class="sxs-lookup"><span data-stu-id="af6bf-228">For example, if you add an alias property that provides an alternate name for a string property, you can also specify a **SecondValue** of **System.Int32** to convert the aliased string value to an integer.</span></span>

<span data-ttu-id="af6bf-229">當 **MemberType** 參數的值為時 `ScriptProperty` ，您可以使用 **SecondValue** 參數來指定其他腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="af6bf-229">When the value of the **MemberType** parameter is `ScriptProperty`, you can use the **SecondValue** parameter to specify an additional script block.</span></span> <span data-ttu-id="af6bf-230">**Value** 參數值中的指令碼區塊會取得變數值。</span><span class="sxs-lookup"><span data-stu-id="af6bf-230">The script block in the value of the **Value** parameter gets the value of a variable.</span></span> <span data-ttu-id="af6bf-231">**SecondValue** 參數值中的指令碼區塊會設定變數值。</span><span class="sxs-lookup"><span data-stu-id="af6bf-231">The script block in the value of the **SecondValue** parameter set the value of the variable.</span></span>

<span data-ttu-id="af6bf-232">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-233">-SerializationDepth</span><span class="sxs-lookup"><span data-stu-id="af6bf-233">-SerializationDepth</span></span>

<span data-ttu-id="af6bf-234">指定要將多少層的類型物件序列化為字串。</span><span class="sxs-lookup"><span data-stu-id="af6bf-234">Specifies how many levels of type objects are serialized as strings.</span></span> <span data-ttu-id="af6bf-235">預設值會序列化 `1` 物件和其屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-235">The default value `1` serializes the object and its properties.</span></span> <span data-ttu-id="af6bf-236">值會序列化 `0` 物件，但不會序列化其屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-236">A value of `0` serializes the object, but not its properties.</span></span> <span data-ttu-id="af6bf-237">的值會序列化 `2` 物件、其屬性，以及屬性值中的任何物件。</span><span class="sxs-lookup"><span data-stu-id="af6bf-237">A value of `2` serializes the object, its properties, and any objects in property values.</span></span>

<span data-ttu-id="af6bf-238">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-238">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-239">-SerializationMethod</span><span class="sxs-lookup"><span data-stu-id="af6bf-239">-SerializationMethod</span></span>

<span data-ttu-id="af6bf-240">指定類型的序列化方法。</span><span class="sxs-lookup"><span data-stu-id="af6bf-240">Specifies a serialization method for the type.</span></span> <span data-ttu-id="af6bf-241">序列化方法決定哪些類型的屬性會序列化，以及用來序列化它們的技術。</span><span class="sxs-lookup"><span data-stu-id="af6bf-241">A serialization method determines which properties of the type are serialized and the technique that is used to serialize them.</span></span> <span data-ttu-id="af6bf-242">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="af6bf-242">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="af6bf-243">`AllPublicProperties`.</span><span class="sxs-lookup"><span data-stu-id="af6bf-243">`AllPublicProperties`.</span></span> <span data-ttu-id="af6bf-244">序列化類型的所有公用屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-244">Serialize all public properties of the type.</span></span> <span data-ttu-id="af6bf-245">您可以使用 **SerializationDepth** 參數，決定是否序列化子屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-245">You can use the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>
- <span data-ttu-id="af6bf-246">`String`.</span><span class="sxs-lookup"><span data-stu-id="af6bf-246">`String`.</span></span> <span data-ttu-id="af6bf-247">將類型序列化為字串。</span><span class="sxs-lookup"><span data-stu-id="af6bf-247">Serialize the type as a string.</span></span> <span data-ttu-id="af6bf-248">您可以使用 **StringSerializationSource** ，指定要做為序列化結果的類型屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-248">You can use the **StringSerializationSource** to specify a property of the type to use as the serialization result.</span></span> <span data-ttu-id="af6bf-249">否則，會使用物件的 **ToString** 方法將類型序列化。</span><span class="sxs-lookup"><span data-stu-id="af6bf-249">Otherwise, the type is serialized by using the **ToString** method of the object.</span></span>
- <span data-ttu-id="af6bf-250">`SpecificProperties`.</span><span class="sxs-lookup"><span data-stu-id="af6bf-250">`SpecificProperties`.</span></span> <span data-ttu-id="af6bf-251">只序列化此類型的指定屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-251">Serialize only the specified properties of this type.</span></span> <span data-ttu-id="af6bf-252">使用 **PropertySerializationSet** 參數，指定已序列化的類型屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-252">Use the **PropertySerializationSet** parameter to specify the properties of the type that are serialized.</span></span>
  <span data-ttu-id="af6bf-253">您也可以使用 **InheritPropertySerializationSet** 參數來決定是否要繼承屬性集，與 **SerializationDepth** 參數來決定是否要序列化子屬性。</span><span class="sxs-lookup"><span data-stu-id="af6bf-253">You can also use the **InheritPropertySerializationSet** parameter to determine whether the property set is inherited and the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>

<span data-ttu-id="af6bf-254">在 PowerShell 中，序列化方法會儲存在 **PSStandardMembers** 的內建物件中。</span><span class="sxs-lookup"><span data-stu-id="af6bf-254">In PowerShell, serialization methods are stored in **PSStandardMembers** internal objects.</span></span>

<span data-ttu-id="af6bf-255">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-255">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-256">-StringSerializationSource</span><span class="sxs-lookup"><span data-stu-id="af6bf-256">-StringSerializationSource</span></span>

<span data-ttu-id="af6bf-257">指定類型的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-257">Specifies the name of a property of the type.</span></span> <span data-ttu-id="af6bf-258">指定屬性的值可做為序列化結果。</span><span class="sxs-lookup"><span data-stu-id="af6bf-258">The value of specified property is used as the serialization result.</span></span> <span data-ttu-id="af6bf-259">只有當 **SerializationMethod** 參數的值是字串時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="af6bf-259">This parameter is valid only when the value of the **SerializationMethod** parameter is String.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-260">-TargetTypeForDeserialization</span><span class="sxs-lookup"><span data-stu-id="af6bf-260">-TargetTypeForDeserialization</span></span>

<span data-ttu-id="af6bf-261">指定此類型物件還原序列化時所轉換成為的類型。</span><span class="sxs-lookup"><span data-stu-id="af6bf-261">Specifies the type to which object of this type are converted when they are deserialized.</span></span>

<span data-ttu-id="af6bf-262">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-263">-TypeAdapter</span><span class="sxs-lookup"><span data-stu-id="af6bf-263">-TypeAdapter</span></span>

<span data-ttu-id="af6bf-264">指定類型介面卡的類型，例如 **microsoft.powershell.cim.ciminstanceadapter** 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-264">Specifies the type of a type adapter, such as **Microsoft.PowerShell.Cim.CimInstanceAdapter** .</span></span> <span data-ttu-id="af6bf-265">類型介面卡可讓 PowerShell 取得類型的成員。</span><span class="sxs-lookup"><span data-stu-id="af6bf-265">A type adapter enables PowerShell to get the members of a type.</span></span>

<span data-ttu-id="af6bf-266">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-267">-TypeConverter</span><span class="sxs-lookup"><span data-stu-id="af6bf-267">-TypeConverter</span></span>

<span data-ttu-id="af6bf-268">指定類型轉換器來轉換不同類型之間的值。</span><span class="sxs-lookup"><span data-stu-id="af6bf-268">Specifies a type converter to convert values between different types.</span></span> <span data-ttu-id="af6bf-269">如果定義了類型的類型轉換器，類型轉換器的執行個體將會用於轉換。</span><span class="sxs-lookup"><span data-stu-id="af6bf-269">If a type converter is defined for a type, an instance of the type converter is used for the conversion.</span></span>

<span data-ttu-id="af6bf-270">輸入衍生自 **System.ComponentModel.TypeConverter** 或 **System.Management.Automation.PSTypeConverter** 類別的 **System.Type** 值。</span><span class="sxs-lookup"><span data-stu-id="af6bf-270">Enter a **System.Type** value that is derived from the **System.ComponentModel.TypeConverter** or **System.Management.Automation.PSTypeConverter** classes.</span></span>

<span data-ttu-id="af6bf-271">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-272">-TypeData</span><span class="sxs-lookup"><span data-stu-id="af6bf-272">-TypeData</span></span>

<span data-ttu-id="af6bf-273">指定此 Cmdlet 新增至會話的型別資料陣列。</span><span class="sxs-lookup"><span data-stu-id="af6bf-273">Specifies an array of type data that this cmdlet adds to the session.</span></span> <span data-ttu-id="af6bf-274">輸入包含 **TypeData** 物件的變數，或輸入可取得 **TypeData** 物件的命令，例如 `Get-TypeData` 命令。</span><span class="sxs-lookup"><span data-stu-id="af6bf-274">Enter a variable that contains a **TypeData** object or a command that gets a **TypeData** object, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="af6bf-275">您也可以使用管線將 **TypeData** 物件傳送至 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-275">You can also pipe a **TypeData** object to `Update-TypeData`.</span></span>

<span data-ttu-id="af6bf-276">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-276">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-277">-TypeName</span><span class="sxs-lookup"><span data-stu-id="af6bf-277">-TypeName</span></span>

<span data-ttu-id="af6bf-278">指定要延伸的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-278">Specifies the name of the type to extend.</span></span>

<span data-ttu-id="af6bf-279">對於 **System** 命名空間中的類型，請輸入簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-279">For types in the **System** namespace, enter the short name.</span></span> <span data-ttu-id="af6bf-280">否則，需要完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="af6bf-280">Otherwise, the full type name is required.</span></span> <span data-ttu-id="af6bf-281">不支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="af6bf-281">Wildcards are not supported.</span></span>

<span data-ttu-id="af6bf-282">您可以用管線將類型名稱傳送至 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-282">You can pipe type names to `Update-TypeData`.</span></span> <span data-ttu-id="af6bf-283">當您使用管線將物件傳送至時，會取得物件的 `Update-TypeData` `Update-TypeData` 類型名稱以及物件類型的類型資料。</span><span class="sxs-lookup"><span data-stu-id="af6bf-283">When you pipe an object to `Update-TypeData`, `Update-TypeData` gets the type name of the object and type data to the object type.</span></span>

<span data-ttu-id="af6bf-284">您可以使用此參數搭配 **成員名稱** 、 **MemberType** 、 **值** 和 **SecondValue** 參數，來新增或變更類型的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="af6bf-284">Use this parameter with the **MemberName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="af6bf-285">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-285">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-286">-Value</span><span class="sxs-lookup"><span data-stu-id="af6bf-286">-Value</span></span>

<span data-ttu-id="af6bf-287">指定屬性或方法的值。</span><span class="sxs-lookup"><span data-stu-id="af6bf-287">Specifies the value of the property or method.</span></span>

<span data-ttu-id="af6bf-288">如果您加入 `AliasProperty` 、、 `CodeProperty` `ScriptProperty` 或 `CodeMethod` 成員，您可以使用 **SecondValue** 參數來新增其他資訊。</span><span class="sxs-lookup"><span data-stu-id="af6bf-288">If you add an `AliasProperty`, `CodeProperty`, `ScriptProperty`, or `CodeMethod` member, you can use the **SecondValue** parameter to add additional information.</span></span>

<span data-ttu-id="af6bf-289">您可以使用此參數搭配 **成員名稱** 、 **MemberType** 、 **值** 和 **SecondValue** 參數，來新增或變更類型的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="af6bf-289">Use this parameter with the **MemberName** , **MemberType** , **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="af6bf-290">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="af6bf-290">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="af6bf-291">-Confirm</span><span class="sxs-lookup"><span data-stu-id="af6bf-291">-Confirm</span></span>

<span data-ttu-id="af6bf-292">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="af6bf-292">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="af6bf-293">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="af6bf-293">-WhatIf</span></span>

<span data-ttu-id="af6bf-294">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="af6bf-294">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="af6bf-295">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="af6bf-295">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="af6bf-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="af6bf-296">CommonParameters</span></span>

<span data-ttu-id="af6bf-297">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="af6bf-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="af6bf-298">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="af6bf-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="af6bf-299">輸入</span><span class="sxs-lookup"><span data-stu-id="af6bf-299">Inputs</span></span>

### <span data-ttu-id="af6bf-300">System.String</span><span class="sxs-lookup"><span data-stu-id="af6bf-300">System.String</span></span>

<span data-ttu-id="af6bf-301">您可以使用管線將包含 **AppendPath** 、 **TypeName** 或 **TypeData** 參數值的字串傳送至 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="af6bf-301">You can pipe a string that contains the values of the **AppendPath** , **TypeName** , or **TypeData** parameters to `Update-TypeData`.</span></span>

## <span data-ttu-id="af6bf-302">輸出</span><span class="sxs-lookup"><span data-stu-id="af6bf-302">Outputs</span></span>

### <span data-ttu-id="af6bf-303">無</span><span class="sxs-lookup"><span data-stu-id="af6bf-303">None</span></span>

<span data-ttu-id="af6bf-304">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="af6bf-304">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="af6bf-305">備忘稿</span><span class="sxs-lookup"><span data-stu-id="af6bf-305">Notes</span></span>

## <span data-ttu-id="af6bf-306">相關連結</span><span class="sxs-lookup"><span data-stu-id="af6bf-306">Related links</span></span>

[<span data-ttu-id="af6bf-307">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="af6bf-307">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="af6bf-308">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="af6bf-308">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="af6bf-309">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="af6bf-309">Remove-TypeData</span></span>](Remove-TypeData.md)
