---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: cfd6cac9c1dda0a86b5b2762be936dc5d77bf34e
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "93206232"
---
# <span data-ttu-id="dc3ea-103">Add-Type</span><span class="sxs-lookup"><span data-stu-id="dc3ea-103">Add-Type</span></span>

## <span data-ttu-id="dc3ea-104">概要</span><span class="sxs-lookup"><span data-stu-id="dc3ea-104">SYNOPSIS</span></span>
<span data-ttu-id="dc3ea-105">將 Microsoft .NET Core 類別新增至 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-105">Adds a Microsoft .NET Core class to a PowerShell session.</span></span>

## <span data-ttu-id="dc3ea-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dc3ea-106">SYNTAX</span></span>

### <span data-ttu-id="dc3ea-107">FromSource (預設) </span><span class="sxs-lookup"><span data-stu-id="dc3ea-107">FromSource (Default)</span></span>

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="dc3ea-108">FromMember</span><span class="sxs-lookup"><span data-stu-id="dc3ea-108">FromMember</span></span>

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="dc3ea-109">FromPath</span><span class="sxs-lookup"><span data-stu-id="dc3ea-109">FromPath</span></span>

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="dc3ea-110">FromLiteralPath</span><span class="sxs-lookup"><span data-stu-id="dc3ea-110">FromLiteralPath</span></span>

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="dc3ea-111">FromAssemblyName</span><span class="sxs-lookup"><span data-stu-id="dc3ea-111">FromAssemblyName</span></span>

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="dc3ea-112">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="dc3ea-112">DESCRIPTION</span></span>

<span data-ttu-id="dc3ea-113">此 `Add-Type` Cmdlet 可讓您在 PowerShell 會話中定義 Microsoft .Net Core 類別。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-113">The `Add-Type` cmdlet lets you define a Microsoft .NET Core class in your PowerShell session.</span></span> <span data-ttu-id="dc3ea-114">然後，您可以使用 Cmdlet 來具現化物件， `New-Object` 並使用物件，就像使用任何 .Net Core 物件一樣。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-114">You can then instantiate objects, by using the `New-Object` cmdlet, and use the objects just as you would use any .NET Core object.</span></span> <span data-ttu-id="dc3ea-115">如果您將 `Add-Type` 命令新增至 powershell 設定檔，則可在所有 powershell 會話中使用類別。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-115">If you add an `Add-Type` command to your PowerShell profile, the class is available in all PowerShell sessions.</span></span>

<span data-ttu-id="dc3ea-116">您可以透過指定現有組件或原始程式碼檔案來指定類型，或者指定變數中內嵌或預存的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-116">You can specify the type by specifying an existing assembly or source code files, or you can specify the source code inline or saved in a variable.</span></span> <span data-ttu-id="dc3ea-117">您甚至可以指定方法，並 `Add-Type` 定義和產生類別。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-117">You can even specify only a method and `Add-Type` defines and generates the class.</span></span> <span data-ttu-id="dc3ea-118">在 Windows 上，您可以使用這項功能，讓平台叫用 (P/Invoke) PowerShell 中非受控函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-118">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span> <span data-ttu-id="dc3ea-119">如果您指定原始程式碼，請 `Add-Type` 編譯指定的原始程式碼，然後產生包含新 .Net Core 類型的記憶體內元件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-119">If you specify source code, `Add-Type` compiles the specified source code and generates an in-memory assembly that contains the new .NET Core types.</span></span>

<span data-ttu-id="dc3ea-120">您可以使用的參數 `Add-Type` 來指定替代語言和編譯器，c # 是預設的、編譯器選項、元件相依性、類別命名空間、類型名稱，以及產生的元件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-120">You can use the parameters of `Add-Type` to specify an alternate language and compiler, C# is the default, compiler options, assembly dependencies, the class namespace, the names of the type, and the resulting assembly.</span></span>

<span data-ttu-id="dc3ea-121">從 PowerShell 7 開始， `Add-Type` 如果已經存在具有相同名稱的型別，則不會編譯型別。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-121">Beginning in PowerShell 7, `Add-Type` does not compile a type if a type with the same name already exists.</span></span> <span data-ttu-id="dc3ea-122">此外，也 `Add-Type` 會尋找資料夾中 `ref` 包含之資料夾下的元件 `pwsh.dll` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-122">Also, `Add-Type` looks for assemblies in a `ref` folder under the folder that contains `pwsh.dll`.</span></span>

## <span data-ttu-id="dc3ea-123">範例</span><span class="sxs-lookup"><span data-stu-id="dc3ea-123">EXAMPLES</span></span>

### <span data-ttu-id="dc3ea-124">範例1：將 .NET 型別新增至會話</span><span class="sxs-lookup"><span data-stu-id="dc3ea-124">Example 1: Add a .NET type to a session</span></span>

<span data-ttu-id="dc3ea-125">此範例會藉由指定儲存在變數中的原始程式碼，將 **BasicTest** 類別新增至會話。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-125">This example adds the **BasicTest** class to the session by specifying source code that is stored in a variable.</span></span> <span data-ttu-id="dc3ea-126">**BasicTest** 類別可用來新增整數、建立物件，以及將整數相乘。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-126">The **BasicTest** class is used to add integers, create an object, and multiply integers.</span></span>

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

<span data-ttu-id="dc3ea-127">`$Source`變數會儲存類別的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-127">The `$Source` variable stores the source code for the class.</span></span> <span data-ttu-id="dc3ea-128">此類型有一個稱為的靜態方法 `Add` ，以及一個稱為的非靜態方法 `Multiply` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-128">The type has a static method called `Add` and a non-static method called `Multiply`.</span></span>

<span data-ttu-id="dc3ea-129">`Add-Type`Cmdlet 會將類別新增至會話。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-129">The `Add-Type` cmdlet adds the class to the session.</span></span> <span data-ttu-id="dc3ea-130">因為它是使用內嵌原始程式碼，所以命令會使用 **TypeDefinition** 參數來指定變數中的程式碼 `$Source` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-130">Because it's using inline source code, the command uses the **TypeDefinition** parameter to specify the code in the `$Source` variable.</span></span>

<span data-ttu-id="dc3ea-131">`Add` **BasicTest** 類別的靜態方法會使用雙冒號字元 (`::`) 來指定類別的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-131">The `Add` static method of the **BasicTest** class uses the double-colon characters (`::`) to specify a static member of the class.</span></span> <span data-ttu-id="dc3ea-132">系統會加入整數，並顯示總和。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-132">The integers are added and the sum is displayed.</span></span>

<span data-ttu-id="dc3ea-133">此 Cmdlet 會具現 `New-Object` 化 **BasicTest** 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-133">The `New-Object` cmdlet instantiates an instance of the **BasicTest** class.</span></span> <span data-ttu-id="dc3ea-134">它會將新的物件儲存在 `$BasicTestObject` 變數中。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-134">It saves the new object in the `$BasicTestObject` variable.</span></span>

<span data-ttu-id="dc3ea-135">`$BasicTestObject` 使用 `Multiply` 方法。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-135">`$BasicTestObject` uses the `Multiply` method.</span></span> <span data-ttu-id="dc3ea-136">整數會相乘，並顯示產品。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-136">The integers are multiplied and the product is displayed.</span></span>

### <span data-ttu-id="dc3ea-137">範例2：檢查新增的類型</span><span class="sxs-lookup"><span data-stu-id="dc3ea-137">Example 2: Examine an added type</span></span>

<span data-ttu-id="dc3ea-138">此範例會使用 `Get-Member` Cmdlet 來檢查 `Add-Type` 和 `New-Object` Cmdlet 在 **範例 1** 中建立的物件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-138">This example uses the `Get-Member` cmdlet to examine the objects that the `Add-Type` and `New-Object` cmdlets created in **Example 1** .</span></span>

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

<span data-ttu-id="dc3ea-139">此 `Get-Member` Cmdlet 會取得新增至會話之 **BasicTest** 類別的類型和成員 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-139">The `Get-Member` cmdlet gets the type and members of the **BasicTest** class that `Add-Type` added to the session.</span></span> <span data-ttu-id="dc3ea-140">此 `Get-Member` 命令會顯示它是衍生自 **system.object** 類別的 **>system.runtimetype** 物件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-140">The `Get-Member` command reveals that it's a **System.RuntimeType** object, which is derived from the **System.Object** class.</span></span>

<span data-ttu-id="dc3ea-141">`Get-Member`**靜態** 參數會取得 **BasicTest** 類別的靜態屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-141">The `Get-Member` **Static** parameter gets the static properties and methods of the **BasicTest** class.</span></span> <span data-ttu-id="dc3ea-142">輸出會顯示 `Add` 已包含方法。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-142">The output shows that the `Add` method is included.</span></span>

<span data-ttu-id="dc3ea-143">`Get-Member`Cmdlet 會取得儲存在變數中之物件的成員 `$BasicTestObject` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-143">The `Get-Member` cmdlet gets the members of the object stored in the `$BasicTestObject` variable.</span></span>
<span data-ttu-id="dc3ea-144">`$BasicTestObject` 是使用 `New-Object` Cmdlet 搭配 **BasicTest** 類別所建立。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-144">`$BasicTestObject` was created by using the `New-Object` cmdlet with the **BasicTest** class.</span></span> <span data-ttu-id="dc3ea-145">輸出會顯示變數的值 `$BasicTestObject` 是 **BasicTest** 類別的實例，而且它包含名為的成員 `Multiply` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-145">The output reveals that the value of the `$BasicTestObject` variable is an instance of the **BasicTest** class and that it includes a member called `Multiply`.</span></span>

### <span data-ttu-id="dc3ea-146">範例3：從元件新增類型</span><span class="sxs-lookup"><span data-stu-id="dc3ea-146">Example 3: Add types from an assembly</span></span>

<span data-ttu-id="dc3ea-147">此範例會將元件中的類別新增 `NJsonSchema.dll` 至目前的會話。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-147">This example adds the classes from the `NJsonSchema.dll` assembly to the current session.</span></span>

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

<span data-ttu-id="dc3ea-148">`Set-Location` 使用 **Path** 參數來指定 `$PSHOME` 變數。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-148">`Set-Location` uses the **Path** parameter to specify the `$PSHOME` variable.</span></span> <span data-ttu-id="dc3ea-149">變數會參照 DLL 檔案所在的 PowerShell 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-149">The variable references the PowerShell installation directory where the DLL file is located.</span></span>

<span data-ttu-id="dc3ea-150">`$AccType`變數會儲存使用 Cmdlet 建立的物件 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-150">The `$AccType` variable stores an object created with the `Add-Type` cmdlet.</span></span> <span data-ttu-id="dc3ea-151">`Add-Type` 使用 **AssemblyName** 參數指定元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-151">`Add-Type` uses the **AssemblyName** parameter to specify the name of the assembly.</span></span> <span data-ttu-id="dc3ea-152">星號 (`*`) 萬用字元可讓您取得正確的元件，即使您不確定名稱或拼寫時也一樣。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-152">The asterisk (`*`) wildcard character allows you to get the correct assembly even when you aren't sure of the name or its spelling.</span></span> <span data-ttu-id="dc3ea-153">**PassThru** 參數會產生代表已新增至會話之類別的物件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-153">The **PassThru** parameter generates objects that represent the classes that are added to the session.</span></span>

### <span data-ttu-id="dc3ea-154">範例4：呼叫原生 Windows Api</span><span class="sxs-lookup"><span data-stu-id="dc3ea-154">Example 4: Call native Windows APIs</span></span>

<span data-ttu-id="dc3ea-155">此範例示範如何在 PowerShell 中呼叫原生 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-155">This example demonstrates how to call native Windows APIs in PowerShell.</span></span> <span data-ttu-id="dc3ea-156">`Add-Type` 使用平台叫用 (P/Invoke) 機制，從 PowerShell 呼叫中的函式 `User32.dll` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-156">`Add-Type` uses the Platform Invoke (P/Invoke) mechanism to call a function in `User32.dll` from PowerShell.</span></span> <span data-ttu-id="dc3ea-157">此範例僅適用于執行 Windows 作業系統的電腦。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-157">This example only works on computers running the Windows operating system.</span></span>

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

<span data-ttu-id="dc3ea-158">變數會儲存函式 `$Signature` 的 c # 簽章 `ShowWindowAsync` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-158">The `$Signature` variable stores the C# signature of the `ShowWindowAsync` function.</span></span> <span data-ttu-id="dc3ea-159">為了確保在 PowerShell 會話中可以看見產生的方法， `public` 關鍵字已新增至標準簽章。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-159">To ensure that the resulting method is visible in a PowerShell session, the `public` keyword was added to the standard signature.</span></span> <span data-ttu-id="dc3ea-160">如需詳細資訊，請參閱 [ShowWindowAsync 函數](/windows/win32/api/winuser/nf-winuser-showwindowasync)。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-160">For more information, see [ShowWindowAsync function](/windows/win32/api/winuser/nf-winuser-showwindowasync).</span></span>

<span data-ttu-id="dc3ea-161">`$ShowWindowAsync`變數會儲存 `Add-Type` **PassThru** 參數所建立的物件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-161">The `$ShowWindowAsync` variable stores the object created by the `Add-Type` **PassThru** parameter.</span></span>
<span data-ttu-id="dc3ea-162">Cmdlet 會將函式 `Add-Type` 新增 `ShowWindowAsync` 至 PowerShell 會話作為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-162">The `Add-Type` cmdlet adds the `ShowWindowAsync` function to the PowerShell session as a static method.</span></span> <span data-ttu-id="dc3ea-163">此命令會使用 **MemberDefinition** 參數來指定儲存在變數中的方法定義 `$Signature` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-163">The command uses the **MemberDefinition** parameter to specify the method definition saved in the `$Signature` variable.</span></span> <span data-ttu-id="dc3ea-164">此命令會使用 **Name** 和 **Namespace** 參數指定類別的名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-164">The command uses the **Name** and **Namespace** parameters to specify a name and namespace for the class.</span></span> <span data-ttu-id="dc3ea-165">**PassThru** 參數會產生代表類型的物件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-165">The **PassThru** parameter generates an object that represents the types.</span></span>

<span data-ttu-id="dc3ea-166">新的 `ShowWindowAsync` 靜態方法用於命令中，以將 PowerShell 主控台的最小化和還原。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-166">The new `ShowWindowAsync` static method is used in the commands to minimize and restore the PowerShell console.</span></span> <span data-ttu-id="dc3ea-167">方法採用兩個參數：視窗控制碼，以及指定視窗顯示方式的整數。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-167">The method takes two parameters: the window handle, and an integer that specifies how the window is displayed.</span></span>

<span data-ttu-id="dc3ea-168">若要將 PowerShell 主控台最小化，請 `ShowWindowAsync` 使用 `Get-Process` Cmdlet 搭配 `$PID` 自動變數來取得裝載目前 PowerShell 會話的程式。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-168">To minimize the PowerShell console, `ShowWindowAsync` uses the `Get-Process` cmdlet with the `$PID` automatic variable to get the process that is hosting the current PowerShell session.</span></span> <span data-ttu-id="dc3ea-169">然後，它會使用目前進程的 **MainWindowHandle** 屬性，以及 `2` 代表值的值 `SW_MINIMIZE` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-169">Then it uses the **MainWindowHandle** property of the current process and a value of `2`, which represents the `SW_MINIMIZE` value.</span></span>

<span data-ttu-id="dc3ea-170">若要還原視窗，請 `ShowWindowAsync` 使用 `4` 代表值的視窗位置值 `SW_RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-170">To restore the window, `ShowWindowAsync` uses a value of `4` for the window position, which represents the `SW_RESTORE` value.</span></span>

<span data-ttu-id="dc3ea-171">若要將視窗最大化，請使用 `3` 代表的值 `SW_MAXIMIZE` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-171">To maximize the window, use the value of `3` that represents `SW_MAXIMIZE`.</span></span>

## <span data-ttu-id="dc3ea-172">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dc3ea-172">PARAMETERS</span></span>

### <span data-ttu-id="dc3ea-173">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="dc3ea-173">-AssemblyName</span></span>

<span data-ttu-id="dc3ea-174">指定包含類型之組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-174">Specifies the name of an assembly that includes the types.</span></span> <span data-ttu-id="dc3ea-175">`Add-Type` 從指定的元件取得類型。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-175">`Add-Type` takes the types from the specified assembly.</span></span> <span data-ttu-id="dc3ea-176">當您要根據元件名稱建立類型時，需要這個參數。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-176">This parameter is required when you're creating types based on an assembly name.</span></span>

<span data-ttu-id="dc3ea-177">輸入元件的完整或簡單名稱（也稱為部分名稱）。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-177">Enter the full or simple name, also known as the partial name, of an assembly.</span></span> <span data-ttu-id="dc3ea-178">組件名稱允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-178">Wildcard characters are permitted in the assembly name.</span></span> <span data-ttu-id="dc3ea-179">如果您輸入簡單或部分名稱，請將 `Add-Type` 它解析成完整名稱，然後使用完整名稱載入元件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-179">If you enter a simple or partial name, `Add-Type` resolves it to the full name, and then uses the full name to load the assembly.</span></span>

<span data-ttu-id="dc3ea-180">此參數不接受路徑或檔案名。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-180">This parameter doesn't accept a path or a filename.</span></span> <span data-ttu-id="dc3ea-181">若要輸入元件動態連結程式庫的路徑 (DLL) 檔，請使用 **path** 參數。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-181">To enter the path to the assembly dynamic-link library (DLL) file, use the **Path** parameter.</span></span>

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

### <span data-ttu-id="dc3ea-182">-CompilerOptions</span><span class="sxs-lookup"><span data-stu-id="dc3ea-182">-CompilerOptions</span></span>

<span data-ttu-id="dc3ea-183">指定原始程式碼編譯器的選項。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-183">Specifies the options for the source code compiler.</span></span> <span data-ttu-id="dc3ea-184">這些選項會在不經過修訂的情況下傳送至編譯器。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-184">These options are sent to the compiler without revision.</span></span>

<span data-ttu-id="dc3ea-185">此參數可讓您指示編譯器產生可執行檔、內嵌資源，或設定命令列選項，例如 `/unsafe` 選項。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-185">This parameter allows you to direct the compiler to generate an executable file, embed resources, or set command-line options, such as the `/unsafe` option.</span></span>

<span data-ttu-id="dc3ea-186">您無法在同一個命令中使用 **CompilerOptions** 和 **ReferencedAssemblies** 參數。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-186">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc3ea-187">-IgnoreWarnings</span><span class="sxs-lookup"><span data-stu-id="dc3ea-187">-IgnoreWarnings</span></span>

<span data-ttu-id="dc3ea-188">忽略編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-188">Ignores compiler warnings.</span></span> <span data-ttu-id="dc3ea-189">您可以使用這個參數來防止將 `Add-Type` 編譯器警告當作錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-189">Use this parameter to prevent `Add-Type` from handling compiler warnings as errors.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc3ea-190">-Language</span><span class="sxs-lookup"><span data-stu-id="dc3ea-190">-Language</span></span>

<span data-ttu-id="dc3ea-191">指定在原始程式碼中使用的語言。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-191">Specifies the language that is used in the source code.</span></span> <span data-ttu-id="dc3ea-192">此參數可接受的值是 **CSharp** 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-192">The acceptable value for this parameter is **CSharp** .</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc3ea-193">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dc3ea-193">-LiteralPath</span></span>

<span data-ttu-id="dc3ea-194">指定包含類型之原始程式碼檔案或組件 DLL 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-194">Specifies the path to source code files or assembly DLL files that contain the types.</span></span> <span data-ttu-id="dc3ea-195">與 **Path** 不同， **LiteralPath** 參數的值會完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-195">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="dc3ea-196">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-196">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="dc3ea-197">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-197">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="dc3ea-198">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-198">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc3ea-199">-MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="dc3ea-199">-MemberDefinition</span></span>

<span data-ttu-id="dc3ea-200">為類別指定新的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-200">Specifies new properties or methods for the class.</span></span> <span data-ttu-id="dc3ea-201">`Add-Type` 產生支援屬性或方法所需的範本程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-201">`Add-Type` generates the template code that is required to support the properties or methods.</span></span>

<span data-ttu-id="dc3ea-202">在 Windows 上，您可以使用這項功能，讓平台叫用 (P/Invoke) PowerShell 中非受控函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-202">On Windows, you can use this feature to make Platform Invoke (P/Invoke) calls to unmanaged functions in PowerShell.</span></span>

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

### <span data-ttu-id="dc3ea-203">-Name</span><span class="sxs-lookup"><span data-stu-id="dc3ea-203">-Name</span></span>

<span data-ttu-id="dc3ea-204">指定要建立之類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-204">Specifies the name of the class to create.</span></span> <span data-ttu-id="dc3ea-205">從成員定義產生類型時，此參數是必要的。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-205">This parameter is required when generating a type from a member definition.</span></span>

<span data-ttu-id="dc3ea-206">類別名稱和命名空間在工作階段中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-206">The type name and namespace must be unique within a session.</span></span> <span data-ttu-id="dc3ea-207">您無法卸載或變更類型。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-207">You can't unload a type or change it.</span></span>
<span data-ttu-id="dc3ea-208">若要變更類型的程式碼，您必須變更名稱或啟動新的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-208">To change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="dc3ea-209">否則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-209">Otherwise, the command fails.</span></span>

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

### <span data-ttu-id="dc3ea-210">-Namespace</span><span class="sxs-lookup"><span data-stu-id="dc3ea-210">-Namespace</span></span>

<span data-ttu-id="dc3ea-211">指定類型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-211">Specifies a namespace for the type.</span></span>

<span data-ttu-id="dc3ea-212">如果命令中未包含此參數，則會在 **AddType. microsoft.powershell.commands.addtype.autogeneratedtypes** 命名空間中建立此類型。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-212">If this parameter isn't included in the command, the type is created in the **Microsoft.PowerShell.Commands.AddType.AutoGeneratedTypes** namespace.</span></span> <span data-ttu-id="dc3ea-213">如果參數包含在具有空字串值或值的命令中 `$Null` ，則會在全域命名空間中產生類型。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-213">If the parameter is included in the command with an empty string value or a value of `$Null`, the type is generated in the global namespace.</span></span>

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

### <span data-ttu-id="dc3ea-214">-OutputAssembly</span><span class="sxs-lookup"><span data-stu-id="dc3ea-214">-OutputAssembly</span></span>

<span data-ttu-id="dc3ea-215">使用位置中的指定名稱來產生組件的 DLL 檔。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-215">Generates a DLL file for the assembly with the specified name in the location.</span></span> <span data-ttu-id="dc3ea-216">輸入選擇性的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-216">Enter an optional path and filename.</span></span> <span data-ttu-id="dc3ea-217">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-217">Wildcard characters are permitted.</span></span> <span data-ttu-id="dc3ea-218">根據預設， `Add-Type` 只會在記憶體中產生元件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-218">By default, `Add-Type` generates the assembly only in memory.</span></span>

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

### <span data-ttu-id="dc3ea-219">-OutputType</span><span class="sxs-lookup"><span data-stu-id="dc3ea-219">-OutputType</span></span>

<span data-ttu-id="dc3ea-220">指定輸出組件的輸出類型。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-220">Specifies the output type of the output assembly.</span></span> <span data-ttu-id="dc3ea-221">預設不會指定任何輸出類型。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-221">By default, no output type is specified.</span></span> <span data-ttu-id="dc3ea-222">此參數只有在命令中已指定輸出組件時才有效。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-222">This parameter is valid only when an output assembly is specified in the command.</span></span> <span data-ttu-id="dc3ea-223">如需這些值的詳細資訊，請參閱 [ Outputassemblytype 列舉](/dotnet/api/microsoft.powershell.commands.outputassemblytype)。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-223">For more information about the values, see [OutputAssemblyType Enumeration](/dotnet/api/microsoft.powershell.commands.outputassemblytype).</span></span>

<span data-ttu-id="dc3ea-224">此參數可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="dc3ea-224">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="dc3ea-225">ConsoleApplication</span><span class="sxs-lookup"><span data-stu-id="dc3ea-225">ConsoleApplication</span></span>
- <span data-ttu-id="dc3ea-226">程式庫</span><span class="sxs-lookup"><span data-stu-id="dc3ea-226">Library</span></span>
- <span data-ttu-id="dc3ea-227">WindowsApplication</span><span class="sxs-lookup"><span data-stu-id="dc3ea-227">WindowsApplication</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc3ea-228">從 PowerShell 7.1， `ConsoleApplication` 和 `WindowsApplication` 不受支援，而且如果其中一個指定為 **OutputType** 參數的值，則 powershell 會擲回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-228">As of PowerShell 7.1, `ConsoleApplication` and `WindowsApplication` are not supported and PowerShell throws a terminating error if either are specified as values for the **OutputType** parameter.</span></span>

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

### <span data-ttu-id="dc3ea-229">-PassThru</span><span class="sxs-lookup"><span data-stu-id="dc3ea-229">-PassThru</span></span>

<span data-ttu-id="dc3ea-230">傳回代表已新增之類型的 **System.Runtime** 物件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-230">Returns a **System.Runtime** object that represents the types that were added.</span></span> <span data-ttu-id="dc3ea-231">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-231">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="dc3ea-232">-Path</span><span class="sxs-lookup"><span data-stu-id="dc3ea-232">-Path</span></span>

<span data-ttu-id="dc3ea-233">指定包含類型之原始程式碼檔案或組件 DLL 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-233">Specifies the path to source code files or assembly DLL files that contain the types.</span></span>

<span data-ttu-id="dc3ea-234">如果您提交原始程式碼檔，則會 `Add-Type` 編譯檔案中的程式碼，並建立類型的記憶體內元件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-234">If you submit source code files, `Add-Type` compiles the code in the files and creates an in-memory assembly of the types.</span></span> <span data-ttu-id="dc3ea-235">**Path** 值中所指定的副檔名會決定使用的編譯器 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-235">The file extension specified in the value of **Path** determines the compiler that `Add-Type` uses.</span></span>

<span data-ttu-id="dc3ea-236">如果您提交元件檔，則 `Add-Type` 會從元件取得類型。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-236">If you submit an assembly file, `Add-Type` takes the types from the assembly.</span></span> <span data-ttu-id="dc3ea-237">若要指定記憶體內組件或全域組件快取，請使用 **AssemblyName** 參數。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-237">To specify an in-memory assembly or the global assembly cache, use the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="dc3ea-238">-ReferencedAssemblies</span><span class="sxs-lookup"><span data-stu-id="dc3ea-238">-ReferencedAssemblies</span></span>

<span data-ttu-id="dc3ea-239">指定類型相依的組件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-239">Specifies the assemblies upon which the type depends.</span></span> <span data-ttu-id="dc3ea-240">依預設，會 `Add-Type` 參考 `System.dll` 和 `System.Management.Automation.dll` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-240">By default, `Add-Type` references `System.dll` and `System.Management.Automation.dll`.</span></span> <span data-ttu-id="dc3ea-241">除了參照預設組件之外，也會參照您使用此參數指定的組件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-241">The assemblies that you specify by using this parameter are referenced in addition to the default assemblies.</span></span>

<span data-ttu-id="dc3ea-242">從 PowerShell 6 開始， **ReferencedAssemblies** 不會包含預設的 .net 元件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-242">Beginning in PowerShell 6, **ReferencedAssemblies** doesn't include the default .NET assemblies.</span></span> <span data-ttu-id="dc3ea-243">您必須在傳遞給此參數的值中包含特定的參考。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-243">You must include a specific reference to them in the value passed to this parameter.</span></span>

<span data-ttu-id="dc3ea-244">您無法在同一個命令中使用 **CompilerOptions** 和 **ReferencedAssemblies** 參數。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-244">You can't use the **CompilerOptions** and **ReferencedAssemblies** parameters in the same command.</span></span>

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

### <span data-ttu-id="dc3ea-245">-TypeDefinition</span><span class="sxs-lookup"><span data-stu-id="dc3ea-245">-TypeDefinition</span></span>

<span data-ttu-id="dc3ea-246">指定包含類型定義的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-246">Specifies the source code that contains the type definitions.</span></span> <span data-ttu-id="dc3ea-247">以字串或 here-string 輸入原始程式碼，或者輸入包含原始程式碼的變數。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-247">Enter the source code in a string or here-string, or enter a variable that contains the source code.</span></span> <span data-ttu-id="dc3ea-248">如需有關此字串的詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-248">For more information about here-strings, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md).</span></span>

<span data-ttu-id="dc3ea-249">在您的類型定義中包含命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-249">Include a namespace declaration in your type definition.</span></span> <span data-ttu-id="dc3ea-250">如果您省略命名空間宣告，您的類型的名稱可能會與其他類型或其他類型的捷徑名稱相同，這會造成意外覆寫。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-250">If you omit the namespace declaration, your type might have the same name as another type or the shortcut for another type, causing an unintentional overwrite.</span></span> <span data-ttu-id="dc3ea-251">例如，如果您定義了一個名為 **exception** 的型別，則使用 **exception** 作為 system.string 快捷 **方式的腳本將會** 失敗。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-251">For example, if you define a type called **Exception** , scripts that use **Exception** as the shortcut for **System.Exception** will fail.</span></span>

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

### <span data-ttu-id="dc3ea-252">-UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="dc3ea-252">-UsingNamespace</span></span>

<span data-ttu-id="dc3ea-253">指定類別需要的其他命名空間。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-253">Specifies other namespaces that are required for the class.</span></span> <span data-ttu-id="dc3ea-254">這與 c # 關鍵字很類似 `Using` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-254">This is much like the C# keyword, `Using`.</span></span>

<span data-ttu-id="dc3ea-255">根據預設，會 `Add-Type` 參考 **System** 命名空間。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-255">By default, `Add-Type` references the **System** namespace.</span></span> <span data-ttu-id="dc3ea-256">使用 **MemberDefinition** 參數時， `Add-Type` 預設也會參考 **system.runtime.interopservices.outattribute** 命名空間。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-256">When the **MemberDefinition** parameter is used, `Add-Type` also references the **System.Runtime.InteropServices** namespace by default.</span></span> <span data-ttu-id="dc3ea-257">除了參照預設命名空間之外，也會參照您使用 **UsingNamespace** 參數新增的命名空間。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-257">The namespaces that you add by using the **UsingNamespace** parameter are referenced in addition to the default namespaces.</span></span>

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

### <span data-ttu-id="dc3ea-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dc3ea-258">CommonParameters</span></span>

<span data-ttu-id="dc3ea-259">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dc3ea-260">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dc3ea-261">輸入</span><span class="sxs-lookup"><span data-stu-id="dc3ea-261">INPUTS</span></span>

### <span data-ttu-id="dc3ea-262">無</span><span class="sxs-lookup"><span data-stu-id="dc3ea-262">None</span></span>

<span data-ttu-id="dc3ea-263">您無法將物件沿著管線向下傳送至 `Add-Type` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-263">You can't send objects down the pipeline to `Add-Type`.</span></span>

## <span data-ttu-id="dc3ea-264">輸出</span><span class="sxs-lookup"><span data-stu-id="dc3ea-264">OUTPUTS</span></span>

### <span data-ttu-id="dc3ea-265">無或系統類型</span><span class="sxs-lookup"><span data-stu-id="dc3ea-265">None or System.Type</span></span>

<span data-ttu-id="dc3ea-266">當您使用 **PassThru** 參數時，會傳回 `Add-Type` 代表新類型的 **system.object** 物件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-266">When you use the **PassThru** parameter, `Add-Type` returns a **System.Type** object that represents the new type.</span></span> <span data-ttu-id="dc3ea-267">否則，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-267">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="dc3ea-268">注意</span><span class="sxs-lookup"><span data-stu-id="dc3ea-268">NOTES</span></span>

<span data-ttu-id="dc3ea-269">您新增的類型只存在於目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-269">The types that you add exist only in the current session.</span></span> <span data-ttu-id="dc3ea-270">若要在所有會話中使用類型，請將它們新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-270">To use the types in all sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="dc3ea-271">如需設定檔的詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-271">For more information about the profile, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="dc3ea-272">型別名稱和命名空間在會話中必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-272">Type names and namespaces must be unique within a session.</span></span> <span data-ttu-id="dc3ea-273">您無法卸載或變更類型。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-273">You can't unload a type or change it.</span></span> <span data-ttu-id="dc3ea-274">如果您需要變更類型的程式碼，您必須變更名稱或啟動新的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-274">If you need to change the code for a type, you must change the name or start a new PowerShell session.</span></span>
<span data-ttu-id="dc3ea-275">否則命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-275">Otherwise, the command fails.</span></span>

<span data-ttu-id="dc3ea-276">在 Windows PowerShell (5.1 版和以下版本) 中，您需要 `Add-Type` 針對尚未載入的任何功能使用。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-276">In Windows PowerShell (version 5.1 and below), you need to use `Add-Type` for anything that isn't already loaded.</span></span> <span data-ttu-id="dc3ea-277">最常見的情況是，這適用于全域組件快取 (GAC) 中找到的元件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-277">Most commonly, this applies to assemblies found in the Global Assembly Cache (GAC).</span></span>
<span data-ttu-id="dc3ea-278">在 PowerShell 6 和更新版本中，沒有任何 GAC，因此 PowerShell 會在中安裝它自己的元件 `$PSHome` 。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-278">In PowerShell 6 and higher, there is no GAC, so PowerShell installs its own assemblies in `$PSHome`.</span></span>
<span data-ttu-id="dc3ea-279">這些元件會在要求時自動載入，因此不需要使用 `Add-Type` 載入它們。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-279">These assemblies are automatically loaded on request, so there's no need to use `Add-Type` to load them.</span></span> <span data-ttu-id="dc3ea-280">不過， `Add-Type` 仍允許使用，以允許腳本與任何 PowerShell 版本隱含相容。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-280">However, using `Add-Type` is still permitted to allow scripts to be implicitly compatible with any version of PowerShell.</span></span>

<span data-ttu-id="dc3ea-281">GAC 中的元件可以依類型名稱載入，而不是依路徑載入。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-281">Assemblies in the GAC can be loaded by type name, rather than by path.</span></span> <span data-ttu-id="dc3ea-282">從任意路徑載入元件需要 `Add-Type` ，因為無法自動載入這些元件。</span><span class="sxs-lookup"><span data-stu-id="dc3ea-282">Loading assemblies from an arbitrary path requires `Add-Type`, since those assemblies cannot not be loaded automatically.</span></span>

## <span data-ttu-id="dc3ea-283">相關連結</span><span class="sxs-lookup"><span data-stu-id="dc3ea-283">RELATED LINKS</span></span>

[<span data-ttu-id="dc3ea-284">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="dc3ea-284">about_Profiles</span></span>](../Microsoft.PowerShell.Core/About/about_profiles.md)

[<span data-ttu-id="dc3ea-285">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="dc3ea-285">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="dc3ea-286">Add-Member</span><span class="sxs-lookup"><span data-stu-id="dc3ea-286">Add-Member</span></span>](Add-Member.md)

[<span data-ttu-id="dc3ea-287">New-Object</span><span class="sxs-lookup"><span data-stu-id="dc3ea-287">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="dc3ea-288"> Outputassemblytype</span><span class="sxs-lookup"><span data-stu-id="dc3ea-288">OutputAssemblyType</span></span>](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[<span data-ttu-id="dc3ea-289">平台叫用 (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="dc3ea-289">Platform Invoke (P/Invoke)</span></span>](/dotnet/standard/native-interop/pinvoke)

[<span data-ttu-id="dc3ea-290">Where-Object</span><span class="sxs-lookup"><span data-stu-id="dc3ea-290">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
