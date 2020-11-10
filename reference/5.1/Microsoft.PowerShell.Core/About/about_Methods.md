---
description: 說明如何使用方法，在 PowerShell 中的物件上執行動作。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Methods
ms.openlocfilehash: 39ebd876b99d77d699c5026e298acc931b501382
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388938"
---
# <a name="about-methods"></a><span data-ttu-id="ea03c-104">關於方法</span><span class="sxs-lookup"><span data-stu-id="ea03c-104">About methods</span></span>

## <a name="short-description"></a><span data-ttu-id="ea03c-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="ea03c-105">Short description</span></span>
<span data-ttu-id="ea03c-106">說明如何使用方法，在 PowerShell 中的物件上執行動作。</span><span class="sxs-lookup"><span data-stu-id="ea03c-106">Describes how to use methods to perform actions on objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ea03c-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="ea03c-107">Long description</span></span>

<span data-ttu-id="ea03c-108">PowerShell 會使用物件來代表資料存放區中的專案或電腦的狀態。</span><span class="sxs-lookup"><span data-stu-id="ea03c-108">PowerShell uses objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="ea03c-109">例如，FileInfo 物件代表檔案系統磁碟機中的檔案，ProcessInfo 物件代表電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="ea03c-109">For example, FileInfo objects represent the files in file system drives and ProcessInfo objects represent the processes on the computer.</span></span>

<span data-ttu-id="ea03c-110">物件具有屬性，可儲存關於物件的相關資料，以及可讓您變更物件的方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-110">Objects have properties, which store data about the object, and methods that let you change the object.</span></span>

<span data-ttu-id="ea03c-111">「方法」是一組指示，指定可對物件執行的動作。</span><span class="sxs-lookup"><span data-stu-id="ea03c-111">A "method" is a set of instructions that specify an action you can perform on the object.</span></span> <span data-ttu-id="ea03c-112">例如， `FileInfo` 物件包含複製物件所代表之檔案的 `CopyTo` 方法 `FileInfo` 。</span><span class="sxs-lookup"><span data-stu-id="ea03c-112">For example, the `FileInfo` object includes the `CopyTo` method that copies the file that the `FileInfo` object represents.</span></span>

<span data-ttu-id="ea03c-113">若要取得任何物件的方法，請使用 `Get-Member` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ea03c-113">To get the methods of any object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="ea03c-114">使用其 **MemberType** 屬性，其值為 "Method"。</span><span class="sxs-lookup"><span data-stu-id="ea03c-114">Use its **MemberType** property with a value of "Method".</span></span> <span data-ttu-id="ea03c-115">下列命令會取得處理程序物件的方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-115">The following command gets the methods of process objects.</span></span>

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

<span data-ttu-id="ea03c-116">若要執行或「叫用」物件的方法，請輸入點 (.)、方法名稱及一組括號 "()"。</span><span class="sxs-lookup"><span data-stu-id="ea03c-116">To perform or "invoke" a method of an object, type a dot (.), the method name, and a set of parentheses "()".</span></span> <span data-ttu-id="ea03c-117">如果方法包含引數，請將引數值包含在括號內。</span><span class="sxs-lookup"><span data-stu-id="ea03c-117">If the method has arguments, place the argument values inside the parentheses.</span></span> <span data-ttu-id="ea03c-118">即使沒有引數，每個方法呼叫仍需要括號。</span><span class="sxs-lookup"><span data-stu-id="ea03c-118">The parentheses are required for every method call, even when there are no arguments.</span></span> <span data-ttu-id="ea03c-119">如果方法接受多個引數，它們應該以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="ea03c-119">If the method takes multiple arguments, they should be separated by commas.</span></span>

<span data-ttu-id="ea03c-120">例如，下列命令會叫用處理程序的 Kill 方法，以結束電腦上的 [記事本] 處理程序。</span><span class="sxs-lookup"><span data-stu-id="ea03c-120">For example, the following command invokes the Kill method of processes to end the Notepad process on the computer.</span></span>

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

<span data-ttu-id="ea03c-121">您可以藉由結合上述語句來縮短此範例。</span><span class="sxs-lookup"><span data-stu-id="ea03c-121">This example can be shortened by combining the above statements.</span></span>

```powershell
(Get-Process Notepad).Kill()
```

<span data-ttu-id="ea03c-122">此 `Get-Process` 命令會以括弧括住，以確保它會在叫用 Kill 方法之前執行。</span><span class="sxs-lookup"><span data-stu-id="ea03c-122">The `Get-Process` command is enclosed in parentheses to ensure that it runs before the Kill method is invoked.</span></span> <span data-ttu-id="ea03c-123">`Kill`然後，會在傳回的物件上叫用方法 `Process` 。</span><span class="sxs-lookup"><span data-stu-id="ea03c-123">The `Kill` method is then invoked on the returned `Process` object.</span></span>

<span data-ttu-id="ea03c-124">另一個非常實用的方法是 `Replace` 字串的方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-124">Another very useful method is the `Replace` method of strings.</span></span> <span data-ttu-id="ea03c-125">`Replace`方法會取代字串中的文字。</span><span class="sxs-lookup"><span data-stu-id="ea03c-125">The `Replace` method, replaces text within a string.</span></span> <span data-ttu-id="ea03c-126">在下列範例中，點 (. ) 可以緊接在字串的結尾引號之後。</span><span class="sxs-lookup"><span data-stu-id="ea03c-126">In the example below, the dot (.) can be placed immediately after the end quote of the string.</span></span>

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

<span data-ttu-id="ea03c-127">如先前的範例所示，您可以使用命令、變數中的物件或任何產生物件 (（例如引號中的字串) ）來叫用物件上的方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-127">As shown in the previous examples, you can invoke a method on an object that you get by using a command, an object in a variable, or anything that results in an object (like a string in quotes).</span></span>

<span data-ttu-id="ea03c-128">從 PowerShell 4.0 開始，支援使用動態方法名稱來叫用方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-128">Starting in PowerShell 4.0, method invocation by using dynamic method names is supported.</span></span>

### <a name="learning-about-methods"></a><span data-ttu-id="ea03c-129">瞭解方法</span><span class="sxs-lookup"><span data-stu-id="ea03c-129">Learning about methods</span></span>

<span data-ttu-id="ea03c-130">若要尋找物件之方法的定義，請移至 [物件類型] 的 [說明] 主題，並尋找其 [方法] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ea03c-130">To find definitions of the methods of an object, go to help topic for the object type and look for its methods page.</span></span> <span data-ttu-id="ea03c-131">例如，下列頁面描述進程物件的方法：處理 [程式](/dotnet/api/system.diagnostics.process#methods)。</span><span class="sxs-lookup"><span data-stu-id="ea03c-131">For example, the following page describes the methods of process objects [System.Diagnostics.Process](/dotnet/api/system.diagnostics.process#methods).</span></span>

<span data-ttu-id="ea03c-132">若要判斷方法的引數，請檢查方法定義，這就像是 PowerShell Cmdlet 的語法圖。</span><span class="sxs-lookup"><span data-stu-id="ea03c-132">To determine the arguments of a method, review the method definition, which is like the syntax diagram of a PowerShell cmdlet.</span></span>

<span data-ttu-id="ea03c-133">方法定義可能會有一或多個方法簽章，就像是 PowerShell Cmdlet 的參數集。</span><span class="sxs-lookup"><span data-stu-id="ea03c-133">A method definition might have one or more method signatures, which are like the parameter sets of PowerShell cmdlets.</span></span> <span data-ttu-id="ea03c-134">簽章會顯示叫用方法的所有有效命令格式。</span><span class="sxs-lookup"><span data-stu-id="ea03c-134">The signatures show all of the valid formats of commands to invoke the method.</span></span>

<span data-ttu-id="ea03c-135">例如，類別的 `CopyTo` 方法 `FileInfo` 包含下列兩個方法簽章：</span><span class="sxs-lookup"><span data-stu-id="ea03c-135">For example, the `CopyTo` method of the `FileInfo` class contains the following two method signatures:</span></span>

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

<span data-ttu-id="ea03c-136">第一個方法簽章採用目的地檔案名稱 (和路徑)。</span><span class="sxs-lookup"><span data-stu-id="ea03c-136">The first method signature takes the destination file name (and a path).</span></span> <span data-ttu-id="ea03c-137">下列範例會使用第一個 `CopyTo` 方法，將檔案複製 `Final.txt` 到 `C:\Bin` 目錄。</span><span class="sxs-lookup"><span data-stu-id="ea03c-137">The following example uses the first `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> <span data-ttu-id="ea03c-138">與 PowerShell 的 _引數_ 模式不同的是，物件方法會以 _運算式_ 模式執行，這是傳遞至 PowerShell 建立所在的 .net framework。</span><span class="sxs-lookup"><span data-stu-id="ea03c-138">Unlike PowerShell's _argument_ mode, object methods execute in _expression_ mode, which is a pass-through to the .NET framework that PowerShell is built on.</span></span> <span data-ttu-id="ea03c-139">在 _運算式_ 模式中 **bareword** 引數 (不具引號的字串) 是不允許的。</span><span class="sxs-lookup"><span data-stu-id="ea03c-139">In _expression_ mode **bareword** arguments (unquoted strings) are not allowed.</span></span> <span data-ttu-id="ea03c-140">使用路徑作為參數時，您可以看到此差異，而將路徑視為引數。</span><span class="sxs-lookup"><span data-stu-id="ea03c-140">You can see this difference when using a the path as a parameter, versus the path as an argument.</span></span> <span data-ttu-id="ea03c-141">您可以在[about_Parsing](about_Parsing.md)中閱讀剖析模式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ea03c-141">You can read more about parsing modes in [about_Parsing](about_Parsing.md)</span></span>

<span data-ttu-id="ea03c-142">第二個方法簽章會採用目的地檔案名和布林值，判斷是否應該覆寫目的地檔案（如果已經存在的話）。</span><span class="sxs-lookup"><span data-stu-id="ea03c-142">The second method signature takes a destination file name and a Boolean value that determines whether the destination file should be overwritten, if it already exists.</span></span>

<span data-ttu-id="ea03c-143">下列範例會使用第二 `CopyTo` 種方法將檔案複製 `Final.txt` 到 `C:\Bin` 目錄，並覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="ea03c-143">The following example uses the second `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory, and to overwrite existing files.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a><span data-ttu-id="ea03c-144">純量物件和集合的方法</span><span class="sxs-lookup"><span data-stu-id="ea03c-144">Methods of Scalar objects and Collections</span></span>

<span data-ttu-id="ea03c-145">特定類型的單一 (「純量」) 物件方法通常不同於同類型物件集合的方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-145">The methods of one ("scalar") object of a particular type are often different from the methods of a collection of objects of the same type.</span></span>

<span data-ttu-id="ea03c-146">例如，每個進程都有一個 `Kill` 方法，但是進程的集合沒有 Kill 方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-146">For example, every process has a `Kill` method, but a collection of processes does not have a Kill method.</span></span>

<span data-ttu-id="ea03c-147">從 PowerShell 3.0 開始，PowerShell 會嘗試避免因為純量物件和集合的不同方法所產生的腳本錯誤。</span><span class="sxs-lookup"><span data-stu-id="ea03c-147">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing methods of scalar objects and collections.</span></span>

<span data-ttu-id="ea03c-148">如果您提交集合，但要求的方法僅存在單一 ( 「純量」 ) 物件上，則 PowerShell 會在集合中的每個物件上叫用方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-148">If you submit a collection, but request a method that exists only on single ("scalar") objects, PowerShell invokes the method on every object in the collection.</span></span>

<span data-ttu-id="ea03c-149">如果方法存在於個別的物件和集合上，則只會叫用集合的方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-149">If the method exists on the individual objects and on the collection, only the collection's method is invoked.</span></span>

<span data-ttu-id="ea03c-150">這項功能也適用於純量物件和集合的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea03c-150">This feature also works on properties of scalar objects and collections.</span></span> <span data-ttu-id="ea03c-151">如需詳細資訊，請參閱 [about_Properties](about_Properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ea03c-151">For more information, see [about_Properties](about_Properties.md).</span></span>

### <a name="examples"></a><span data-ttu-id="ea03c-152">範例</span><span class="sxs-lookup"><span data-stu-id="ea03c-152">Examples</span></span>

<span data-ttu-id="ea03c-153">下列範例會在物件集合中執行個別進程物件的 **Kill** 方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-153">The following example runs the **Kill** method of individual process objects in a collection of objects.</span></span>

<span data-ttu-id="ea03c-154">第一個命令會啟動「記事本」處理程序的三個執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea03c-154">The first command starts three instances of the Notepad process.</span></span> <span data-ttu-id="ea03c-155">`Get-Process` 取得「記事本」處理常式的所有三個實例，並將它們儲存在 `$p` 變數中。</span><span class="sxs-lookup"><span data-stu-id="ea03c-155">`Get-Process` gets all three instance of the Notepad process and saves them in the `$p` variable.</span></span>

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

<span data-ttu-id="ea03c-156">下一個命令會在變數中的所有三個進程上執行 **Kill** 方法 `$p` 。</span><span class="sxs-lookup"><span data-stu-id="ea03c-156">The next command runs the **Kill** method on all three processes in the `$p` variable.</span></span> <span data-ttu-id="ea03c-157">即使處理常式集合沒有方法，此命令仍可運作 `Kill` 。</span><span class="sxs-lookup"><span data-stu-id="ea03c-157">This command works even though a collection of processes does not have a `Kill` method.</span></span>

```powershell
$p.Kill()
Get-Process Notepad
```

<span data-ttu-id="ea03c-158">此 `Get-Process` 命令會確認 `Kill` 方法是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="ea03c-158">The `Get-Process` command confirms that the `Kill` method worked.</span></span>

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

<span data-ttu-id="ea03c-159">這個範例在功能上相當於使用指令程式 `Foreach-Object` 在集合中的每個物件上執行方法。</span><span class="sxs-lookup"><span data-stu-id="ea03c-159">This example is functionally equivalent to using the `Foreach-Object` cmdlet to run the method on each object in the collection.</span></span>

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a><span data-ttu-id="ea03c-160">ForEach 和 Where 方法</span><span class="sxs-lookup"><span data-stu-id="ea03c-160">ForEach and Where methods</span></span>

<span data-ttu-id="ea03c-161">從 PowerShell 4.0 開始，支援使用方法語法進行集合篩選。</span><span class="sxs-lookup"><span data-stu-id="ea03c-161">Beginning in PowerShell 4.0, collection filtering by using a method syntax is supported.</span></span> <span data-ttu-id="ea03c-162">這可讓您在處理集合和時使用兩個新的方法 `ForEach` `Where` 。</span><span class="sxs-lookup"><span data-stu-id="ea03c-162">This allows use of two new methods when dealing with collections `ForEach` and `Where`.</span></span>

<span data-ttu-id="ea03c-163">您可以在 [about_arrays](about_arrays.md) 中深入閱讀這些方法</span><span class="sxs-lookup"><span data-stu-id="ea03c-163">You can read more about these methods in [about_arrays](about_arrays.md)</span></span>

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a><span data-ttu-id="ea03c-164">有多個多載存在時呼叫特定的方法</span><span class="sxs-lookup"><span data-stu-id="ea03c-164">Calling a specific method when multiple overloads exist</span></span>

<span data-ttu-id="ea03c-165">呼叫 .NET 方法時，請考慮下列案例。</span><span class="sxs-lookup"><span data-stu-id="ea03c-165">Consider the following scenario when calling .NET methods.</span></span> <span data-ttu-id="ea03c-166">如果方法接受物件，但透過介面採用更明確的類型來進行多載，則 PowerShell 會選擇接受物件的方法，除非您明確地將它轉換成該介面。</span><span class="sxs-lookup"><span data-stu-id="ea03c-166">If a method takes an object but has an overload via an interface taking a more specific type, PowerShell chooses the method that accepts the object unless you explicitly cast it to that interface.</span></span>

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

<span data-ttu-id="ea03c-167">在此範例中， `object` 已選擇 **橫條** 方法的較不特定多載。</span><span class="sxs-lookup"><span data-stu-id="ea03c-167">In this example the less specific `object` overload of the **Bar** method was chosen.</span></span>

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

<span data-ttu-id="ea03c-168">在此範例中，我們會將方法轉換為介面 **IFoo** ，以選取更明確的 **Bar** 方法多載。</span><span class="sxs-lookup"><span data-stu-id="ea03c-168">In this example we cast the method to the interface **IFoo** to select the more specific overload of the **Bar** method.</span></span>

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a><span data-ttu-id="ea03c-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea03c-169">See Also</span></span>

[<span data-ttu-id="ea03c-170">about_Objects</span><span class="sxs-lookup"><span data-stu-id="ea03c-170">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="ea03c-171">about_Properties</span><span class="sxs-lookup"><span data-stu-id="ea03c-171">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="ea03c-172">Get-Member</span><span class="sxs-lookup"><span data-stu-id="ea03c-172">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
