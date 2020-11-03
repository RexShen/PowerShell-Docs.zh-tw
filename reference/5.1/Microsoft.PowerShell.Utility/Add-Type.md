---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: af7cd937ccfc7c5f05fd0213764ed51a3ba9f2bb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203367"
---
# <span data-ttu-id="934d1-103">Add-Type</span><span class="sxs-lookup"><span data-stu-id="934d1-103">Add-Type</span></span>

## <span data-ttu-id="934d1-104">概要</span><span class="sxs-lookup"><span data-stu-id="934d1-104">SYNOPSIS</span></span>
<span data-ttu-id="934d1-105">將 Microsoft .NET Framework 類別新增至 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="934d1-105">Adds a Microsoft .NET Framework class to a PowerShell session.</span></span>

## <span data-ttu-id="934d1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="934d1-106">SYNTAX</span></span>

### <span data-ttu-id="934d1-107">FromSource (預設) </span><span class="sxs-lookup"><span data-stu-id="934d1-107">FromSource (Default)</span></span>

```
Add-Type [-CodeDomProvider <CodeDomProvider>] [-CompilerParameters <CompilerParameters>]
 [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [<CommonParameters>]
```

### <span data-ttu-id="934d1-108">FromMember</span><span class="sxs-lookup"><span data-stu-id="934d1-108">FromMember</span></span>

```
Add-Type [-CodeDomProvider <CodeDomProvider>] [-CompilerParameters <CompilerParameters>]
 [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>] [-UsingNamespace <String[]>]
 [-Language <Language>] [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="934d1-109">FromPath</span><span class="sxs-lookup"><span data-stu-id="934d1-109">FromPath</span></span>

```
Add-Type [-CompilerParameters <CompilerParameters>] [-Path] <String[]>
 [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>]
 [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="934d1-110">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="934d1-110">FromLiteralPath</span></span>

```
Add-Type [-CompilerParameters <CompilerParameters>] -LiteralPath <String[]>
 [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>]
 [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

### <span data-ttu-id="934d1-111">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="934d1-111">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [-IgnoreWarnings] [<CommonParameters>]
```

## <span data-ttu-id="934d1-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="934d1-112">DESCRIPTION</span></span>

<span data-ttu-id="934d1-113">此 `Add-Type` Cmdlet 可讓您在 PowerShell 會話中定義 Microsoft .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="934d1-113">The `Add-Type` cmdlet lets you define a Microsoft .NET Framework class in your PowerShell session.</span></span>
<span data-ttu-id="934d1-114">然後，您可以使用 Cmdlet 來具現化物件， `New-Object` 並使用物件，就像使用任何 .NET Framework 物件一樣。</span><span class="sxs-lookup"><span data-stu-id="934d1-114">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Framework object.</span></span> <span data-ttu-id="934d1-115">如果您將 `Add-Type` 命令新增至 powershell 設定檔，則可在所有 powershell 會話中使用類別。</span><span class="sxs-lookup"><span data-stu-id="934d1-115">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="934d1-116">您可以透過指定現有組件或原始程式碼檔案來指定類型，或者指定變數中內嵌或預存的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="934d1-116">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="934d1-117">您甚至可以指定方法，並 `Add-Type` 將定義和產生類別。</span><span class="sxs-lookup"><span data-stu-id="934d1-117">You can even specify only a method and `Add-Type` will define and generate the class.</span></span> <span data-ttu-id="934d1-118">在 Windows 上，您可以使用這項功能，讓平台叫用 (P/Invoke) PowerShell 中非受控函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="934d1-118">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="934d1-119">如果您指定原始程式碼，則會 `Add-Type` 編譯指定的原始程式碼，並產生包含新 .NET Framework 類型的記憶體內元件。</span><span class="sxs-lookup"><span data-stu-id="934d1-119">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Framework types.</span></span>

<span data-ttu-id="934d1-120">您可以使用的參數 `Add-Type` 來指定替代語言和編譯器，c # 是預設的、編譯器選項、元件相依性、類別命名空間、類型名稱，以及產生的元件。</span><span class="sxs-lookup"><span data-stu-id="934d1-120">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

## <span data-ttu-id="934d1-121">範例</span><span class="sxs-lookup"><span data-stu-id="934d1-121">EXAMPLES</span></span>

### <span data-ttu-id="934d1-122">範例1：將 .NET 型別新增至會話</span><span class="sxs-lookup"><span data-stu-id="934d1-122">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="934d1-123">此範例會藉由指定儲存在變數中的原始程式碼，將 **BasicTest** 類別新增至會話。</span><span class="sxs-lookup"><span data-stu-id="934d1-123">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="934d1-124">**BasicTest** 類別可用來新增整數、建立物件，以及將整數相乘。</span><span class="sxs-lookup"><span data-stu-id="934d1-124">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

<span data-ttu-id="934d1-125">`$Source`變數會儲存類別的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="934d1-125">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="934d1-126">此類型有一個稱為的靜態方法 `Add` ，以及一個稱為的非靜態方法 `Multiply` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-126">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="934d1-127">`Add-Type`Cmdlet 會將類別新增至會話。</span><span class="sxs-lookup"><span data-stu-id="934d1-127">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="934d1-128">因為它是使用內嵌原始程式碼，所以命令會使用 **TypeDefinition** 參數來指定變數中的程式碼 `$Source` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-128">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="934d1-129">`Add` **BasicTest** 類別的靜態方法會使用雙冒號字元 (`::`) 來指定類別的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="934d1-129">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="934d1-130">系統會加入整數，並顯示總和。</span><span class="sxs-lookup"><span data-stu-id="934d1-130">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="934d1-131">此 Cmdlet 會具現 `New-Object` 化 **BasicTest** 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="934d1-131">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="934d1-132">它會將新的物件儲存在 `$BasicTestObject` 變數中。</span><span class="sxs-lookup"><span data-stu-id="934d1-132">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="934d1-133">`$BasicTestObject` 使用 `Multiply` 方法。</span><span class="sxs-lookup"><span data-stu-id="934d1-133">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="934d1-134">整數會相乘，並顯示產品。</span><span class="sxs-lookup"><span data-stu-id="934d1-134">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="934d1-135">範例2：檢查新增的類型</span><span class="sxs-lookup"><span data-stu-id="934d1-135">Example 2: Examine an added type</span></span>

<span data-ttu-id="934d1-136">此範例會使用 `Get-Member` Cmdlet 來檢查 `Add-Type` 和 `New-Object` Cmdlet 在 **範例 1** 中建立的物件。</span><span class="sxs-lookup"><span data-stu-id="934d1-136">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1** .</span></span>

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

<span data-ttu-id="934d1-137">此 `Get-Member` Cmdlet 會取得新增至會話之 **BasicTest** 類別的類型和成員 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-137">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="934d1-138">此 `Get-Member` 命令會顯示它是衍生自 **system.object** 類別的 **>system.runtimetype** 物件。</span><span class="sxs-lookup"><span data-stu-id="934d1-138">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="934d1-139">`Get-Member`**靜態** 參數會取得 **BasicTest** 類別的靜態屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="934d1-139">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="934d1-140">輸出會顯示 `Add` 已包含方法。</span><span class="sxs-lookup"><span data-stu-id="934d1-140">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="934d1-141">`Get-Member`Cmdlet 會取得儲存在變數中之物件的成員 `$BasicTestObject` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-141">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="934d1-142">`$BasicTestObject` 是使用 `New-Object` Cmdlet 搭配 **BasicTest** 類別所建立。</span><span class="sxs-lookup"><span data-stu-id="934d1-142">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="934d1-143">輸出會顯示變數的值 `$BasicTestObject` 是 **BasicTest** 類別的實例，而且它包含名為的成員 `Multiply` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-143">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="934d1-144">範例3：從元件新增類型</span><span class="sxs-lookup"><span data-stu-id="934d1-144">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="934d1-145">此範例會將元件中的類別新增 `Accessibility.dll` 至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="934d1-145">This example adds the classes from the `Accessibility.dll` assembly to the current session.</span></span>

```powershell
$AccType = Add-Type -AssemblyName "accessib*" -PassThru
```

<span data-ttu-id="934d1-146">`$AccType`變數會儲存使用 Cmdlet 建立的物件 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-146">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="934d1-147">`Add-Type` 使用 **AssemblyName** 參數指定元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="934d1-147">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="934d1-148">星號 (`*`) 萬用字元可讓您取得正確的元件，即使您不確定名稱或拼寫時也一樣。</span><span class="sxs-lookup"><span data-stu-id="934d1-148">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="934d1-149">**PassThru** 參數會產生代表已新增至會話之類別的物件。</span><span class="sxs-lookup"><span data-stu-id="934d1-149">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="934d1-150">範例4：呼叫原生 Windows Api</span><span class="sxs-lookup"><span data-stu-id="934d1-150">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="934d1-151">此範例示範如何在 PowerShell 中呼叫原生 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="934d1-151">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="934d1-152">`Add-Type` 使用平台叫用 (P/Invoke) 機制，從 PowerShell 呼叫中的函式 `User32.dll` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-152">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="934d1-153">此範例僅適用于執行 Windows 作業系統的電腦。</span><span class="sxs-lookup"><span data-stu-id="934d1-153">This example only works on computers running the Windows operating system.</span></span>

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

<span data-ttu-id="934d1-154">變數會儲存函式 `$Signature` 的 c # 簽章 `ShowWindowAsync` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-154">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="934d1-155">為了確保在 PowerShell 會話中可以看見產生的方法， `public` 已將關鍵字新增至標準簽章。</span><span class="sxs-lookup"><span data-stu-id="934d1-155">To ensure that the resulting method will be visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="934d1-156">如需詳細資訊，請參閱 [ShowWindowAsync 函數](/windows/win32/api/winuser/nf-winuser-showwindowasync)。</span><span class="sxs-lookup"><span data-stu-id="934d1-156">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="934d1-157">`$ShowWindowAsync`變數會儲存 `Add-Type` **PassThru** 參數所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="934d1-157">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="934d1-158">Cmdlet 會將函式 `Add-Type` 新增 `ShowWindowAsync` 至 PowerShell 會話作為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="934d1-158">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="934d1-159">此命令會使用 **MemberDefinition** 參數來指定儲存在變數中的方法定義 `$Signature` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-159">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="934d1-160">此命令會使用 **Name** 和 **Namespace** 參數指定類別的名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="934d1-160">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="934d1-161">**PassThru** 參數會產生代表類型的物件。</span><span class="sxs-lookup"><span data-stu-id="934d1-161">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="934d1-162">新的 `ShowWindowAsync` 靜態方法用於命令中，以將 PowerShell 主控台的最小化和還原。</span><span class="sxs-lookup"><span data-stu-id="934d1-162">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="934d1-163">方法採用兩個參數：視窗控制碼，以及指定視窗顯示方式的整數。</span><span class="sxs-lookup"><span data-stu-id="934d1-163">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="934d1-164">若要將 PowerShell 主控台最小化，請 `ShowWindowAsync` 使用 `Get-Process` Cmdlet 搭配 `$PID` 自動變數來取得裝載目前 PowerShell 會話的程式。</span><span class="sxs-lookup"><span data-stu-id="934d1-164">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="934d1-165">然後，它會使用目前進程的 **MainWindowHandle** 屬性，以及 `2` 代表值的值 `SW_MINIMIZE` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-165">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="934d1-166">若要還原視窗，請 `ShowWindowAsync` 使用 `4` 代表值的視窗位置值 `SW_RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-166">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="934d1-167">若要將視窗最大化，請使用 `3` 代表的值 `SW_MAXIMIZE` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-167">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

### <span data-ttu-id="934d1-168">範例5：從 Visual Basic 檔案新增類型</span><span class="sxs-lookup"><span data-stu-id="934d1-168">Example 5: Add a type from a Visual Basic file</span></span>

<span data-ttu-id="934d1-169">此範例會使用 `Add-Type` Cmdlet 將檔案中定義的 **VBFromFile** 類別新增 `Hello.vb` 至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="934d1-169">This example uses the `Add-Type` cmdlet to add the **VBFromFile** class that's defined in the `Hello.vb` file to the current session.</span></span> <span data-ttu-id="934d1-170">檔的文字 `Hello.vb` 會顯示在命令輸出中。</span><span class="sxs-lookup"><span data-stu-id="934d1-170">The text of the `Hello.vb` file is shown in the command output.</span></span>

```powershell
Add-Type -Path "C:\PS-Test\Hello.vb"
[VBFromFile]::SayHello(", World")

# From Hello.vb

Public Class VBFromFile
  Public Shared Function SayHello(sourceName As String) As String
    Dim myValue As String = "Hello"
    return myValue + sourceName
  End Function
End Class
```

```Output
Hello, World
```

<span data-ttu-id="934d1-171">`Add-Type` 使用 **Path** 參數來指定原始檔， `Hello.vb` 並加入檔案中定義的類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-171">`Add-Type` uses the **Path** parameter to specify the source file, `Hello.vb`, and adds the type defined in the file.</span></span> <span data-ttu-id="934d1-172">`SayHello`函數會以 **VBFromFile** 類別的靜態方法來呼叫。</span><span class="sxs-lookup"><span data-stu-id="934d1-172">The `SayHello` function is called as a static method of the **VBFromFile** class.</span></span>

### <span data-ttu-id="934d1-173">範例6：新增具有 JScript.NET 的類別</span><span class="sxs-lookup"><span data-stu-id="934d1-173">Example 6: Add a class with JScript.NET</span></span>

<span data-ttu-id="934d1-174">此範例會使用 JScript.NET，在您的 PowerShell 會話中建立新的 **FRectangle** 類別。</span><span class="sxs-lookup"><span data-stu-id="934d1-174">This example uses JScript.NET to create a new class, **FRectangle** , in your PowerShell session.</span></span>

```powershell
Add-Type @'
 class FRectangle {
   var Length : double;
   var Height : double;
   function Perimeter() : double {
       return (Length + Height) * 2; }
   function Area() : double {
       return Length * Height;  } }
'@ -Language JScript

$rect = [FRectangle]::new()
$rect
```

```Output
Length Height
------ ------
     0      0
```

### <span data-ttu-id="934d1-175">範例7：新增 F # 編譯器</span><span class="sxs-lookup"><span data-stu-id="934d1-175">Example 7: Add an F# compiler</span></span>

<span data-ttu-id="934d1-176">此範例示範如何使用指令程式， `Add-Type` 將 F # 程式碼編譯器新增至 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="934d1-176">This example shows how to use the `Add-Type` cmdlet to add an F# code compiler to your PowerShell session.</span></span> <span data-ttu-id="934d1-177">若要在 PowerShell 中執行此範例，您必須具有 `FSharp.Compiler.CodeDom.dll` 以 F # 語言安裝的。</span><span class="sxs-lookup"><span data-stu-id="934d1-177">To run this example in PowerShell, you must have the `FSharp.Compiler.CodeDom.dll` that is installed with the F# language.</span></span>

```powershell
Add-Type -Path "FSharp.Compiler.CodeDom.dll"
$Provider = New-Object Microsoft.FSharp.Compiler.CodeDom.FSharpCodeProvider
$FSharpCode = @"
let rec loop n =if n <= 0 then () else beginprint_endline (string_of_int n);loop (n-1)end
"@
$FSharpType = Add-Type -TypeDefinition $FSharpCode -CodeDomProvider $Provider -PassThru |
   Where-Object { $_.IsPublic }
$FSharpType::loop(4)
```

```Output
4
3
2
1
```

<span data-ttu-id="934d1-178">`Add-Type` 使用 **Path** 參數來指定元件，並取得元件中的類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-178">`Add-Type` uses the **Path** parameter to specify an assembly and gets the types in the assembly.</span></span>
<span data-ttu-id="934d1-179">`New-Object` 建立 F # 程式碼提供者的實例，並將結果儲存在 `$Provider` 變數中。</span><span class="sxs-lookup"><span data-stu-id="934d1-179">`New-Object` creates an instance of the F# code provider and saves the result in the `$Provider` variable.</span></span> <span data-ttu-id="934d1-180">`$FSharpCode`變數會儲存定義 **迴圈** 方法的 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="934d1-180">The `$FSharpCode` variable saves the F# code that defines the **Loop** method.</span></span>

<span data-ttu-id="934d1-181">`$FSharpType`變數會儲存 Cmdlet 的結果 `Add-Type` ，以儲存中定義的公用類型 `$FSharpCode` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-181">The the `$FSharpType` variable stores the results of the `Add-Type` cmdlet that saves the public types defined in `$FSharpCode`.</span></span> <span data-ttu-id="934d1-182">**TypeDefinition** 參數會指定定義類型的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="934d1-182">The **TypeDefinition** parameter specifies the source code that defines the types.</span></span> <span data-ttu-id="934d1-183">**CodeDomProvider** 參數會指定原始程式碼編譯器。</span><span class="sxs-lookup"><span data-stu-id="934d1-183">The **CodeDomProvider** parameter specifies the source code compiler.</span></span> <span data-ttu-id="934d1-184">**PassThru** 參數會指示傳回 `Add-Type` 代表類型的 **運行** 時間物件。</span><span class="sxs-lookup"><span data-stu-id="934d1-184">The **PassThru** parameter directs `Add-Type` to return a **Runtime** object that represents the types.</span></span>
<span data-ttu-id="934d1-185">這些物件會向下傳送至 `Where-Object` Cmdlet，此 Cmdlet 只會傳回公用類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-185">The objects are sent down the pipeline to the `Where-Object` cmdlet, which returns only the public types.</span></span> <span data-ttu-id="934d1-186">使用 **Where 物件** Cmdlet 的原因是 F # 提供者會產生非公用類型來支援產生的公用類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-186">The **Where-Object** cmdlet is used because the F# provider generates non-public types to support the resulting public type.</span></span>

<span data-ttu-id="934d1-187">迴圈方法會以變數中所儲存之類型的靜態方法來呼叫 `$FSharpType` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-187">The Loop method is called as a static method of the type stored in the `$FSharpType` variable.</span></span>

## <span data-ttu-id="934d1-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="934d1-188">PARAMETERS</span></span>

### <span data-ttu-id="934d1-189">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="934d1-189">-AssemblyName</span></span>

<span data-ttu-id="934d1-190">指定包含類型之組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="934d1-190">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="934d1-191">`Add-Type` 從指定的元件取得類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-191">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="934d1-192">當您要根據元件名稱建立類型時，需要這個參數。</span><span class="sxs-lookup"><span data-stu-id="934d1-192">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="934d1-193">輸入元件的完整或簡單名稱（也稱為部分名稱）。</span><span class="sxs-lookup"><span data-stu-id="934d1-193">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="934d1-194">組件名稱允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="934d1-194">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="934d1-195">如果您輸入簡單或部分名稱，請將 `Add-Type` 它解析成完整名稱，然後使用完整名稱載入元件。</span><span class="sxs-lookup"><span data-stu-id="934d1-195">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="934d1-196">此參數不接受路徑或檔案名。</span><span class="sxs-lookup"><span data-stu-id="934d1-196">This parameter doesn't accept a path or a file name.</span></span> <span data-ttu-id="934d1-197">若要輸入元件動態連結程式庫的路徑 (DLL) 檔，請使用 **path** 參數。</span><span class="sxs-lookup"><span data-stu-id="934d1-197">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="934d1-198">-CodeDomProvider</span><span class="sxs-lookup"><span data-stu-id="934d1-198">-CodeDomProvider</span></span>

<span data-ttu-id="934d1-199">指定程式碼產生器或編譯器。</span><span class="sxs-lookup"><span data-stu-id="934d1-199">Specifies a code generator or compiler.</span></span> <span data-ttu-id="934d1-200">`Add-Type` 使用指定的編譯器來編譯原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="934d1-200">`Add-Type` uses the specified compiler to compile the source code.</span></span> <span data-ttu-id="934d1-201">預設值是 c # 編譯器。</span><span class="sxs-lookup"><span data-stu-id="934d1-201">The default is the C# compiler.</span></span> <span data-ttu-id="934d1-202">如果您所使用的語言無法使用 **language** 參數指定，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="934d1-202">Use this parameter if you're using a language that can't be specified by using the **Language** parameter.</span></span> <span data-ttu-id="934d1-203">您指定的 **CodeDomProvider** 必須能夠從原始程式碼產生元件。</span><span class="sxs-lookup"><span data-stu-id="934d1-203">The **CodeDomProvider** that you specify must be able to generate assemblies from source code.</span></span>

```yaml
Type: System.CodeDom.Compiler.CodeDomProvider
Parameter Sets: FromSource, FromMember
Aliases: Provider

Required: False
Position: Named
Default value: C# compiler
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-204">->compilerparameters</span><span class="sxs-lookup"><span data-stu-id="934d1-204">-CompilerParameters</span></span>

<span data-ttu-id="934d1-205">指定原始程式碼編譯器的選項。</span><span class="sxs-lookup"><span data-stu-id="934d1-205">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="934d1-206">這些選項會在不經過修訂的情況下傳送至編譯器。</span><span class="sxs-lookup"><span data-stu-id="934d1-206">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="934d1-207">此參數可讓您指示編譯器產生可執行檔、內嵌資源，或設定命令列選項，例如 `/unsafe` 選項。</span><span class="sxs-lookup"><span data-stu-id="934d1-207">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span> <span data-ttu-id="934d1-208">此參數會實 **>compilerparameters** 類別 **>compilerparameters** 。</span><span class="sxs-lookup"><span data-stu-id="934d1-208">This parameter implements the **CompilerParameters** class, **System.CodeDom.Compiler.CompilerParameters** .</span></span>

<span data-ttu-id="934d1-209">您無法在同一個命令中使用 **>compilerparameters** 和 **ReferencedAssemblies** 參數。</span><span class="sxs-lookup"><span data-stu-id="934d1-209">You can't use the **CompilerParameters** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.CodeDom.Compiler.CompilerParameters
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: CP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-210">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="934d1-210">-IgnoreWarnings</span></span>

<span data-ttu-id="934d1-211">忽略編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="934d1-211">Ignores compiler warnings.</span></span> <span data-ttu-id="934d1-212">您可以使用這個參數來防止將 `Add-Type` 編譯器警告當作錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="934d1-212">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-213">-Language</span><span class="sxs-lookup"><span data-stu-id="934d1-213">-Language</span></span>

<span data-ttu-id="934d1-214">指定在原始程式碼中使用的語言。</span><span class="sxs-lookup"><span data-stu-id="934d1-214">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="934d1-215">此 `Add-Type` Cmdlet 會使用此參數的值來選取適當的 **CodeDomProvider** 。</span><span class="sxs-lookup"><span data-stu-id="934d1-215">The `Add-Type` cmdlet uses the value of this parameter to select the appropriate **CodeDomProvider** .</span></span> <span data-ttu-id="934d1-216">CSharp 是預設值。</span><span class="sxs-lookup"><span data-stu-id="934d1-216">CSharp is the default value.</span></span> <span data-ttu-id="934d1-217">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="934d1-217">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="934d1-218">CSharp</span><span class="sxs-lookup"><span data-stu-id="934d1-218">CSharp</span></span>
- <span data-ttu-id="934d1-219">CSharpVersion2</span><span class="sxs-lookup"><span data-stu-id="934d1-219">CSharpVersion2</span></span>
- <span data-ttu-id="934d1-220">CSharpVersion3</span><span class="sxs-lookup"><span data-stu-id="934d1-220">CSharpVersion3</span></span>
- <span data-ttu-id="934d1-221">JScript</span><span class="sxs-lookup"><span data-stu-id="934d1-221">JScript</span></span>
- <span data-ttu-id="934d1-222">VisualBasic</span><span class="sxs-lookup"><span data-stu-id="934d1-222">VisualBasic</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp, CSharpVersion2, CSharpVersion3, JScript, VisualBasic

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-223">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="934d1-223">-LiteralPath</span></span>

<span data-ttu-id="934d1-224">指定包含類型之原始程式碼檔案或組件 DLL 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="934d1-224">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="934d1-225">與 **Path** 不同， **LiteralPath** 參數的值會完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="934d1-225">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="934d1-226">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="934d1-226">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="934d1-227">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="934d1-227">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="934d1-228">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="934d1-228">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-229">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="934d1-229">-MemberDefinition</span></span>

<span data-ttu-id="934d1-230">為類別指定新的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="934d1-230">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="934d1-231">`Add-Type` 產生支援屬性或方法所需的範本程式碼。</span><span class="sxs-lookup"><span data-stu-id="934d1-231">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="934d1-232">在 Windows 上，您可以使用這項功能，讓平台叫用 (P/Invoke) PowerShell 中非受控函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="934d1-232">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-233">-Name</span><span class="sxs-lookup"><span data-stu-id="934d1-233">-Name</span></span>

<span data-ttu-id="934d1-234">指定要建立之類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="934d1-234">Specifies the name of the class to create.</span></span> <span data-ttu-id="934d1-235">從成員定義產生類型時，此參數是必要的。</span><span class="sxs-lookup"><span data-stu-id="934d1-235">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="934d1-236">類別名稱和命名空間在工作階段中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="934d1-236">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="934d1-237">您無法卸載或變更類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-237">You can't unload a type or change it.</span></span>
<span data-ttu-id="934d1-238">若要變更類型的程式碼，您必須變更名稱或啟動新的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="934d1-238">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="934d1-239">否則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="934d1-239">Otherwise, the command fails.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-240">-Namespace</span><span class="sxs-lookup"><span data-stu-id="934d1-240">-Namespace</span></span>

<span data-ttu-id="934d1-241">指定類型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="934d1-241">Specifies a namespace for the type.</span></span>

<span data-ttu-id="934d1-242">如果命令中未包含此參數，則會在 **AddType. microsoft.powershell.commands.addtype.autogeneratedtypes** 命名空間中建立此類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-242">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="934d1-243">如果參數包含在具有空字串值或值的命令中 `$Null` ，則會在全域命名空間中產生類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-243">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-244">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="934d1-244">-OutputAssembly</span></span>

<span data-ttu-id="934d1-245">使用位置中的指定名稱來產生組件的 DLL 檔。</span><span class="sxs-lookup"><span data-stu-id="934d1-245">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="934d1-246">輸入選擇性的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="934d1-246">Enter an optional path and file name.</span></span> <span data-ttu-id="934d1-247">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="934d1-247">Wildcard characters are permitted.</span></span> <span data-ttu-id="934d1-248">根據預設， `Add-Type` 只會在記憶體中產生元件。</span><span class="sxs-lookup"><span data-stu-id="934d1-248">By default, `Add-Type` generates the assembly only in memory.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="934d1-249">-OutputType</span><span class="sxs-lookup"><span data-stu-id="934d1-249">-OutputType</span></span>

<span data-ttu-id="934d1-250">指定輸出組件的輸出類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-250">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="934d1-251">預設不會指定任何輸出類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-251">By default, no output type is specified.</span></span> <span data-ttu-id="934d1-252">此參數只有在命令中已指定輸出組件時才有效。</span><span class="sxs-lookup"><span data-stu-id="934d1-252">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="934d1-253">如需這些值的詳細資訊，請參閱 [ Outputassemblytype 列舉](/dotnet/api/microsoft.powershell.commands.outputassemblytype)。</span><span class="sxs-lookup"><span data-stu-id="934d1-253">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="934d1-254">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="934d1-254">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="934d1-255">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="934d1-255">ConsoleApplication</span></span>
- <span data-ttu-id="934d1-256">程式庫</span><span class="sxs-lookup"><span data-stu-id="934d1-256">Library</span></span>
- <span data-ttu-id="934d1-257">WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="934d1-257">WindowsApplication</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-258">-PassThru</span><span class="sxs-lookup"><span data-stu-id="934d1-258">-PassThru</span></span>

<span data-ttu-id="934d1-259">傳回代表已新增之類型的 **System.Runtime** 物件。</span><span class="sxs-lookup"><span data-stu-id="934d1-259">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="934d1-260">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="934d1-260">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-261">-Path</span><span class="sxs-lookup"><span data-stu-id="934d1-261">-Path</span></span>

<span data-ttu-id="934d1-262">指定包含類型之原始程式碼檔案或組件 DLL 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="934d1-262">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="934d1-263">如果您提交原始程式碼檔，則會 `Add-Type` 編譯檔案中的程式碼，並建立類型的記憶體內元件。</span><span class="sxs-lookup"><span data-stu-id="934d1-263">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="934d1-264">**Path** 值中指定的副檔名會決定使用的編譯器 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-264">The file name extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="934d1-265">如果您提交元件檔，則 `Add-Type` 會從元件取得類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-265">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="934d1-266">若要指定記憶體內組件或全域組件快取，請使用 **AssemblyName** 參數。</span><span class="sxs-lookup"><span data-stu-id="934d1-266">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-267">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="934d1-267">-ReferencedAssemblies</span></span>

<span data-ttu-id="934d1-268">指定類型相依的組件。</span><span class="sxs-lookup"><span data-stu-id="934d1-268">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="934d1-269">依預設，會 `Add-Type` 參考 `System.dll` 和 `System.Management.Automation.dll` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-269">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="934d1-270">除了參照預設組件之外，也會參照您使用此參數指定的組件。</span><span class="sxs-lookup"><span data-stu-id="934d1-270">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="934d1-271">您無法在同一個命令中使用 **>compilerparameters** 和 **ReferencedAssemblies** 參數。</span><span class="sxs-lookup"><span data-stu-id="934d1-271">You can't use the **CompilerParameters** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-272">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="934d1-272">-TypeDefinition</span></span>

<span data-ttu-id="934d1-273">指定包含類型定義的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="934d1-273">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="934d1-274">以字串或 here-string 輸入原始程式碼，或者輸入包含原始程式碼的變數。</span><span class="sxs-lookup"><span data-stu-id="934d1-274">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="934d1-275">如需有關此字串的詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="934d1-275">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="934d1-276">在您的類型定義中包含命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="934d1-276">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="934d1-277">如果您省略命名空間宣告，您的類型的名稱可能會與其他類型或其他類型的捷徑名稱相同，這會造成意外覆寫。</span><span class="sxs-lookup"><span data-stu-id="934d1-277">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="934d1-278">例如，如果您定義了一個名為 **exception** 的型別，則使用 **exception** 作為 system.string 快捷 **方式的腳本將會** 失敗。</span><span class="sxs-lookup"><span data-stu-id="934d1-278">For example, if you define a type called **Exception** , scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-279">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="934d1-279">-UsingNamespace</span></span>

<span data-ttu-id="934d1-280">指定類別需要的其他命名空間。</span><span class="sxs-lookup"><span data-stu-id="934d1-280">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="934d1-281">這與 c # 關鍵字很類似 `Using` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-281">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="934d1-282">根據預設，會 `Add-Type` 參考 **System** 命名空間。</span><span class="sxs-lookup"><span data-stu-id="934d1-282">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="934d1-283">使用 **MemberDefinition** 參數時， `Add-Type` 預設也會參考 **system.runtime.interopservices.outattribute** 命名空間。</span><span class="sxs-lookup"><span data-stu-id="934d1-283">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="934d1-284">除了參照預設命名空間之外，也會參照您使用 **UsingNamespace** 參數新增的命名空間。</span><span class="sxs-lookup"><span data-stu-id="934d1-284">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="934d1-285">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="934d1-285">CommonParameters</span></span>

<span data-ttu-id="934d1-286">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="934d1-286">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="934d1-287">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="934d1-287">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="934d1-288">輸入</span><span class="sxs-lookup"><span data-stu-id="934d1-288">INPUTS</span></span>

### <span data-ttu-id="934d1-289">無</span><span class="sxs-lookup"><span data-stu-id="934d1-289">None</span></span>

<span data-ttu-id="934d1-290">您無法將物件沿著管線向下傳送至 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-290">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="934d1-291">輸出</span><span class="sxs-lookup"><span data-stu-id="934d1-291">OUTPUTS</span></span>

### <span data-ttu-id="934d1-292">無或系統類型</span><span class="sxs-lookup"><span data-stu-id="934d1-292">None or System.Type</span></span>

<span data-ttu-id="934d1-293">當您使用 **PassThru** 參數時，會傳回 `Add-Type` 代表新類型的 **system.object** 物件。</span><span class="sxs-lookup"><span data-stu-id="934d1-293">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="934d1-294">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="934d1-294">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="934d1-295">注意</span><span class="sxs-lookup"><span data-stu-id="934d1-295">NOTES</span></span>

<span data-ttu-id="934d1-296">您新增的類型只存在於目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="934d1-296">The types that you add exist only in the current session.</span></span> <span data-ttu-id="934d1-297">若要在所有會話中使用類型，請將它們新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="934d1-297">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="934d1-298">如需設定檔的詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="934d1-298">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="934d1-299">型別名稱和命名空間在會話中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="934d1-299">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="934d1-300">您無法卸載或變更類型。</span><span class="sxs-lookup"><span data-stu-id="934d1-300">You can't unload a type or change it.</span></span> <span data-ttu-id="934d1-301">如果您需要變更類型的程式碼，您必須變更名稱或啟動新的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="934d1-301">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="934d1-302">否則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="934d1-302">Otherwise, the command fails.</span></span>

<span data-ttu-id="934d1-303">某些語言的 **CodeDomProvider** 類別，例如 IronPython 和 j #，並不會產生輸出。</span><span class="sxs-lookup"><span data-stu-id="934d1-303">The **CodeDomProvider** class for some languages, such as IronPython and J#, doesn't generate output.</span></span> <span data-ttu-id="934d1-304">因此，以這些語言撰寫的類型無法搭配使用 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="934d1-304">As a result, types written in these languages can't be used with `Add-Type`.</span></span>

<span data-ttu-id="934d1-305">此 Cmdlet 是以 Microsoft .NET Framework [CodeDomProvider 類別](/dotnet/api/system.codedom.compiler.codedomprovider)為基礎。</span><span class="sxs-lookup"><span data-stu-id="934d1-305">This cmdlet is based on the Microsoft .NET Framework [CodeDomProvider Class](/dotnet/api/system.codedom.compiler.codedomprovider).</span></span>

## <span data-ttu-id="934d1-306">相關連結</span><span class="sxs-lookup"><span data-stu-id="934d1-306">RELATED LINKS</span></span>

[<span data-ttu-id="934d1-307">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="934d1-307">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="934d1-308">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="934d1-308">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="934d1-309">Add-Member</span><span class="sxs-lookup"><span data-stu-id="934d1-309">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="934d1-310">New-Object</span><span class="sxs-lookup"><span data-stu-id="934d1-310">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="934d1-311"> Outputassemblytype</span><span class="sxs-lookup"><span data-stu-id="934d1-311">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="934d1-312">平台叫用 (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="934d1-312">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="934d1-313">Where-Object</span><span class="sxs-lookup"><span data-stu-id="934d1-313">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
