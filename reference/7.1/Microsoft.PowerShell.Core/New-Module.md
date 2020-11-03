---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: 7ee0f316b5aac138c8c6c5d2cf91ea3fa1c08151
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205027"
---
# <span data-ttu-id="a1ff0-103">New-Module</span><span class="sxs-lookup"><span data-stu-id="a1ff0-103">New-Module</span></span>

## <span data-ttu-id="a1ff0-104">概要</span><span class="sxs-lookup"><span data-stu-id="a1ff0-104">SYNOPSIS</span></span>
<span data-ttu-id="a1ff0-105">建立只存在記憶體中的新動態模組。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-105">Creates a new dynamic module that exists only in memory.</span></span>

## <span data-ttu-id="a1ff0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a1ff0-106">SYNTAX</span></span>

### <span data-ttu-id="a1ff0-107">ScriptBlock (預設值)</span><span class="sxs-lookup"><span data-stu-id="a1ff0-107">ScriptBlock (Default)</span></span>

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="a1ff0-108">Name</span><span class="sxs-lookup"><span data-stu-id="a1ff0-108">Name</span></span>

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="a1ff0-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a1ff0-109">DESCRIPTION</span></span>

<span data-ttu-id="a1ff0-110">`New-Module`Cmdlet 會從腳本區塊建立動態模組。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-110">The `New-Module` cmdlet creates a dynamic module from a script block.</span></span> <span data-ttu-id="a1ff0-111">動態模組的成員 (例如函式與變數) 可立即在工作階段中使用，而且在您關閉工作階段之前保持可用。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-111">The members of the dynamic module, such as functions and variables, are immediately available in the session and remain available until you close the session.</span></span>

<span data-ttu-id="a1ff0-112">類似靜態模組，預設會匯出動態模組中的 Cmdlet 與函式，而不會匯出變數與別名。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-112">Like static modules, by default, the cmdlets and functions in a dynamic module are exported and the variables and aliases are not.</span></span> <span data-ttu-id="a1ff0-113">不過，您可以使用 Export-ModuleMember Cmdlet 和的參數來覆 `New-Module` 寫預設值。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-113">However, you can use the Export-ModuleMember cmdlet and the parameters of `New-Module` to override the defaults.</span></span>

<span data-ttu-id="a1ff0-114">您也可以使用的 **AsCustomObject** 參數 `New-Module` ，將動態模組傳回做為自訂物件。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-114">You can also use the **AsCustomObject** parameter of `New-Module` to return the dynamic module as a custom object.</span></span> <span data-ttu-id="a1ff0-115">模組的成員 (例如函式) 會以自訂物件的指令碼方法實作，而不會匯入到工作階段。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-115">The members of the modules, such as functions, are implemented as script methods of the custom object instead of being imported into the session.</span></span>

<span data-ttu-id="a1ff0-116">動態模組只存在於記憶體中，而不是在磁片上。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-116">Dynamic modules exist only in memory, not on disk.</span></span> <span data-ttu-id="a1ff0-117">類似所有模組，動態模組的成員會在全域範圍的子系私人模組範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-117">Like all modules, the members of dynamic modules run in a private module scope that is a child of the global scope.</span></span> <span data-ttu-id="a1ff0-118">Get-Module 無法取得動態模組，但是 Get-Command 可以取得匯出的成員。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-118">Get-Module cannot get a dynamic module, but Get-Command can get the exported members.</span></span>

<span data-ttu-id="a1ff0-119">若要讓動態模組可供使用 `Get-Module` ，請使用管線將 `New-Module` 命令傳送至 import-module，或使用管線將傳回的模組物件傳送至 `New-Module` `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-119">To make a dynamic module available to `Get-Module`, pipe a `New-Module` command to Import-Module, or pipe the module object that `New-Module` returns to `Import-Module`.</span></span> <span data-ttu-id="a1ff0-120">此動作會將動態模組新增至 `Get-Module` 清單中，但不會將模組儲存到磁片或使其成為持續性。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-120">This action adds the dynamic module to the `Get-Module` list, but it does not save the module to disk or make it persistent.</span></span>

## <span data-ttu-id="a1ff0-121">範例</span><span class="sxs-lookup"><span data-stu-id="a1ff0-121">EXAMPLES</span></span>

### <span data-ttu-id="a1ff0-122">範例1：建立動態模組</span><span class="sxs-lookup"><span data-stu-id="a1ff0-122">Example 1: Create a dynamic module</span></span>

<span data-ttu-id="a1ff0-123">此範例會使用名為的函式建立新的動態模組 `Hello` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-123">This example creates a new dynamic module with a function called `Hello`.</span></span> <span data-ttu-id="a1ff0-124">此命令傳回代表新動態模組的模組物件。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-124">The command returns a module object that represents the new dynamic module.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### <span data-ttu-id="a1ff0-125">範例2：使用動態模組和 Get-Module 和 Get-Command</span><span class="sxs-lookup"><span data-stu-id="a1ff0-125">Example 2: Working with dynamic modules and Get-Module and Get-Command</span></span>

<span data-ttu-id="a1ff0-126">此範例示範 Cmdlet 不會傳回動態模組 `Get-Module` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-126">This example demonstrates that dynamic modules are not returned by the `Get-Module` cmdlet.</span></span> <span data-ttu-id="a1ff0-127">Cmdlet 會傳回它們所匯出的成員 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-127">The members that they export are returned by the `Get-Command` cmdlet.</span></span>

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### <span data-ttu-id="a1ff0-128">範例3：將變數匯出到目前的會話</span><span class="sxs-lookup"><span data-stu-id="a1ff0-128">Example 3: Export a variable into the current session</span></span>

<span data-ttu-id="a1ff0-129">此範例會使用 `Export-ModuleMember` Cmdlet 將變數匯出到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-129">This example uses the `Export-ModuleMember` cmdlet to export a variable into the current session.</span></span>
<span data-ttu-id="a1ff0-130">如果沒有 `Export-ModuleMember` 命令，則只會匯出函數。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-130">Without the `Export-ModuleMember` command, only the function is exported.</span></span>

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

<span data-ttu-id="a1ff0-131">輸出顯示變數與函式皆匯出到工作階段。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-131">The output shows that both the variable and the function were exported into the session.</span></span>

### <span data-ttu-id="a1ff0-132">範例4：將動態模組提供給 Get-Module</span><span class="sxs-lookup"><span data-stu-id="a1ff0-132">Example 4: Make a dynamic module available to Get-Module</span></span>

<span data-ttu-id="a1ff0-133">這個範例示範您可以使用管線將動態模組傳送至，藉以建立動態模組 `Get-Module` `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-133">This example demonstrates that you can make a dynamic module available to `Get-Module` by piping the dynamic module to `Import-Module`.</span></span>

<span data-ttu-id="a1ff0-134">`New-Module` 建立輸送至 Cmdlet 的模組物件 `Import-Module` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-134">`New-Module` creates a module object that is piped to the `Import-Module` cmdlet.</span></span> <span data-ttu-id="a1ff0-135">的 **name** 參數會將 `New-Module` 易記名稱指派給模組。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-135">The **Name** parameter of `New-Module` assigns a friendly name to the module.</span></span> <span data-ttu-id="a1ff0-136">因為 `Import-Module` 預設不會傳回任何物件，所以此命令沒有任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-136">Because `Import-Module` does not return any objects by default, there is no output from this command.</span></span> <span data-ttu-id="a1ff0-137">`Get-Module`**GreetingModule** 已匯入至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-137">`Get-Module` that the **GreetingModule** has been imported into the current session.</span></span>

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

<span data-ttu-id="a1ff0-138">此 `Get-Command` Cmdlet 會顯示 `Hello` 動態模組所匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-138">The `Get-Command` cmdlet shows the `Hello` function that the dynamic module exports.</span></span>

### <span data-ttu-id="a1ff0-139">範例5：產生具有匯出函數的自訂物件</span><span class="sxs-lookup"><span data-stu-id="a1ff0-139">Example 5: Generate a custom object that has exported functions</span></span>

<span data-ttu-id="a1ff0-140">這個範例會示範如何使用的 **AsCustomObject** 參數 `New-Module` 來產生自訂物件，該物件具有代表匯出函數的腳本方法。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-140">This example shows how to use the **AsCustomObject** parameter of `New-Module` to generate a custom object that has script methods that represent the exported functions.</span></span>

<span data-ttu-id="a1ff0-141">此 `New-Module` Cmdlet 會建立包含兩個函式和的動態模組 `Hello` `Goodbye` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-141">The `New-Module` cmdlet creates a dynamic module with two functions, `Hello` and `Goodbye`.</span></span> <span data-ttu-id="a1ff0-142">**AsCustomObject** 參數會建立自訂物件，而不是預設產生的 **PSModuleInfo** 物件 `New-Module` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-142">The **AsCustomObject** parameter creates a custom object instead of the **PSModuleInfo** object that `New-Module` generates by default.</span></span> <span data-ttu-id="a1ff0-143">這個自訂物件會儲存在 `$m` 變數中。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-143">This custom object is saved in the `$m` variable.</span></span>
<span data-ttu-id="a1ff0-144">`$m`變數似乎沒有指派的值。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-144">The `$m` variable appears to have no assigned value.</span></span>

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

<span data-ttu-id="a1ff0-145">輸送 `$m` 至 `Get-Member` Cmdlet 會顯示自訂物件的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-145">Piping `$m` to the `Get-Member` cmdlet displays the properties and methods of the custom object.</span></span> <span data-ttu-id="a1ff0-146">輸出顯示物件具有表示和函數的腳本方法 `Hello` `Goodbye` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-146">The output shows that the object has script methods that represent the `Hello` and `Goodbye` functions.</span></span>
<span data-ttu-id="a1ff0-147">最後，我們會呼叫這些腳本方法，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-147">Finally, we call these script methods and display the results.</span></span>

### <span data-ttu-id="a1ff0-148">範例6：取得腳本區塊的結果</span><span class="sxs-lookup"><span data-stu-id="a1ff0-148">Example 6: Get the results of the script block</span></span>

<span data-ttu-id="a1ff0-149">此範例使用 **ReturnResult** 參數來要求執行腳本區塊的結果，而不是要求模組物件。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-149">This example uses the **ReturnResult** parameter to request the results of running the script block instead of requesting a module object.</span></span> <span data-ttu-id="a1ff0-150">新模組中的腳本區塊會定義函式 `SayHello` ，然後呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-150">The script block in the new module defines the `SayHello` function and then calls the function.</span></span>

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## <span data-ttu-id="a1ff0-151">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1ff0-151">PARAMETERS</span></span>

### <span data-ttu-id="a1ff0-152">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="a1ff0-152">-ArgumentList</span></span>

<span data-ttu-id="a1ff0-153">指定引數陣列，這些引數是傳遞至腳本區塊的參數值。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-153">Specifies an array of arguments which are parameter values that are passed to the script block.</span></span> <span data-ttu-id="a1ff0-154">如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-154">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a1ff0-155">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="a1ff0-155">-AsCustomObject</span></span>

<span data-ttu-id="a1ff0-156">指出此 Cmdlet 會傳回代表動態模組的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-156">Indicates that this cmdlet returns a custom object that represents the dynamic module.</span></span> <span data-ttu-id="a1ff0-157">模組成員會以自訂物件的指令碼方法實作，但是不會匯入到工作階段中。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-157">The module members are implemented as script methods of the custom object, but they are not imported into the session.</span></span> <span data-ttu-id="a1ff0-158">您可以將自訂物件儲存在變數中，並使用點標記法來叫用成員。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-158">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

<span data-ttu-id="a1ff0-159">如果模組有多個同名的成員，例如函式和變數（兩者都是），則只能從自訂物件存取一個具有每個名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-159">If the module has multiple members with the same name, such as a function and a variable that are both named A, only one member with each name can be accessed from the custom object.</span></span>

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

### <span data-ttu-id="a1ff0-160">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a1ff0-160">-Cmdlet</span></span>

<span data-ttu-id="a1ff0-161">指定 Cmdlet 的陣列，此 Cmdlet 會從模組匯出到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-161">Specifies an array of cmdlets that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="a1ff0-162">輸入以逗號分隔的 Cmdlet 清單。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-162">Enter a comma-separated list of cmdlets.</span></span> <span data-ttu-id="a1ff0-163">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-163">Wildcard characters are permitted.</span></span> <span data-ttu-id="a1ff0-164">根據預設，會匯出模組中所有的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-164">By default, all cmdlets in the module are exported.</span></span>

<span data-ttu-id="a1ff0-165">您不能定義指令碼區塊中的 Cmdlet，但是動態模組可以包含　Cmdlet (若動態模組從二進位模組匯入 Cmdlet)。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-165">You cannot define cmdlets in a script block, but a dynamic module can include cmdlets if it imports the cmdlets from a binary module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a1ff0-166">-Function</span><span class="sxs-lookup"><span data-stu-id="a1ff0-166">-Function</span></span>

<span data-ttu-id="a1ff0-167">指定此 Cmdlet 從模組匯出到目前會話的函式陣列。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-167">Specifies an array of functions that this cmdlet exports from the module into the current session.</span></span>
<span data-ttu-id="a1ff0-168">輸入以逗號分隔的函式清單。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-168">Enter a comma-separated list of functions.</span></span> <span data-ttu-id="a1ff0-169">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-169">Wildcard characters are permitted.</span></span> <span data-ttu-id="a1ff0-170">根據預設，會匯出模組中定義的所有函式。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-170">By default, all functions defined in a module are exported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a1ff0-171">-Name</span><span class="sxs-lookup"><span data-stu-id="a1ff0-171">-Name</span></span>

<span data-ttu-id="a1ff0-172">指定新模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-172">Specifies a name for the new module.</span></span> <span data-ttu-id="a1ff0-173">您也可以使用管線將模組名稱傳送至 New-Module。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-173">You can also pipe a module name to New-Module.</span></span>

<span data-ttu-id="a1ff0-174">預設值是以開頭的自動產生名稱， `__DynamicModule_` 後面接著指定動態模組路徑的 GUID。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-174">The default value is an autogenerated name that starts with `__DynamicModule_` and is followed by a GUID that specifies the path of the dynamic module.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a1ff0-175">-ReturnResult</span><span class="sxs-lookup"><span data-stu-id="a1ff0-175">-ReturnResult</span></span>

<span data-ttu-id="a1ff0-176">指出此 Cmdlet 會執行腳本區塊並傳回腳本區塊的結果，而不是傳回模組物件。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-176">Indicates that this cmdlet runs the script block and returns the script block results instead of returning a module object.</span></span>

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

### <span data-ttu-id="a1ff0-177">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="a1ff0-177">-ScriptBlock</span></span>

<span data-ttu-id="a1ff0-178">指定動態模組的內容。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-178">Specifies the contents of the dynamic module.</span></span> <span data-ttu-id="a1ff0-179">以大括弧括住內容 (`{}`) 來建立腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-179">Enclose the contents in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="a1ff0-180">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-180">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a1ff0-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a1ff0-181">CommonParameters</span></span>

<span data-ttu-id="a1ff0-182">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a1ff0-183">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a1ff0-184">輸入</span><span class="sxs-lookup"><span data-stu-id="a1ff0-184">INPUTS</span></span>

### <span data-ttu-id="a1ff0-185">System.String</span><span class="sxs-lookup"><span data-stu-id="a1ff0-185">System.String</span></span>

<span data-ttu-id="a1ff0-186">您可以使用管線將模組名稱傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-186">You can pipe a module name to this cmdlet.</span></span>

## <span data-ttu-id="a1ff0-187">輸出</span><span class="sxs-lookup"><span data-stu-id="a1ff0-187">OUTPUTS</span></span>

### <span data-ttu-id="a1ff0-188">System.Management.Automation.PSModuleInfo、System.Management.Automation.PSCustomObject 或 None</span><span class="sxs-lookup"><span data-stu-id="a1ff0-188">System.Management.Automation.PSModuleInfo, System.Management.Automation.PSCustomObject, or None</span></span>

<span data-ttu-id="a1ff0-189">依預設，此 Cmdlet 會產生 **PSModuleInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-189">This cmdlet generates a **PSModuleInfo** object, by default.</span></span> <span data-ttu-id="a1ff0-190">如果您使用 **AsCustomObject** 參數，它會產生 **PSCustomObject** 物件。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-190">If you use the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span> <span data-ttu-id="a1ff0-191">如果您使用 **ReturnResult** 參數，它會傳回評估動態模組中腳本區塊的結果。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-191">If you use the **ReturnResult** parameter, it returns the result of evaluating the script block in the dynamic module.</span></span>

## <span data-ttu-id="a1ff0-192">注意</span><span class="sxs-lookup"><span data-stu-id="a1ff0-192">NOTES</span></span>

<span data-ttu-id="a1ff0-193">您也可以 `New-Module` 使用其別名來參考 `nmo` 。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-193">You can also refer to `New-Module` by its alias, `nmo`.</span></span> <span data-ttu-id="a1ff0-194">如需詳細資訊，請參閱 [about_Aliases](About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="a1ff0-194">For more information, see [about_Aliases](About/about_Aliases.md).</span></span>

## <span data-ttu-id="a1ff0-195">相關連結</span><span class="sxs-lookup"><span data-stu-id="a1ff0-195">RELATED LINKS</span></span>

[<span data-ttu-id="a1ff0-196">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="a1ff0-196">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="a1ff0-197">Get-Module</span><span class="sxs-lookup"><span data-stu-id="a1ff0-197">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="a1ff0-198">Import-Module</span><span class="sxs-lookup"><span data-stu-id="a1ff0-198">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="a1ff0-199">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="a1ff0-199">Remove-Module</span></span>](Remove-Module.md)

