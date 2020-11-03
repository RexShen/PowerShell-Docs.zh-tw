---
description: 描述報告函式所傳回之物件類型的屬性。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 94e6ab9926f8d31e6b7602792f836fa5eadd3b50
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207084"
---
# <a name="about-functions-outputtypeattribute"></a><span data-ttu-id="6696d-104">關於函式 OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="6696d-104">About Functions OutputTypeAttribute</span></span>

## <a name="short-description"></a><span data-ttu-id="6696d-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="6696d-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="6696d-106">描述報告函式所傳回之物件類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="6696d-106">Describes an attribute that reports the type of object that the function returns.</span></span>

## <a name="long-description"></a><span data-ttu-id="6696d-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="6696d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="6696d-108">OutputType 屬性會列出函式傳回之物件的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="6696d-108">The OutputType attribute lists the .NET types of objects that the functions returns.</span></span> <span data-ttu-id="6696d-109">您可以使用其選擇性的 ParameterSetName 參數，針對每個參數集列出不同的輸出類型。</span><span class="sxs-lookup"><span data-stu-id="6696d-109">You can use its optional ParameterSetName parameter to list different output types for each parameter set.</span></span>

<span data-ttu-id="6696d-110">Simple 和 advanced 函式支援 OutputType 屬性。</span><span class="sxs-lookup"><span data-stu-id="6696d-110">The OutputType attribute is supported on simple and advanced functions.</span></span> <span data-ttu-id="6696d-111">它與 CmdletBinding 屬性無關。</span><span class="sxs-lookup"><span data-stu-id="6696d-111">It is independent of the CmdletBinding attribute.</span></span>

<span data-ttu-id="6696d-112">OutputType 屬性會提供 Cmdlet 所傳回之 **FunctionInfo** 物件的 OutputType 屬性的值 `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="6696d-112">The OutputType attribute provides the value of the OutputType property of the **System.Management.Automation.FunctionInfo** object that the `Get-Command` cmdlet returns.</span></span>

<span data-ttu-id="6696d-113">OutputType 屬性值只是文件備註。</span><span class="sxs-lookup"><span data-stu-id="6696d-113">The OutputType attribute value is only a documentation note.</span></span> <span data-ttu-id="6696d-114">它不是衍生自函式程式碼，或與實際的函式輸出比較。</span><span class="sxs-lookup"><span data-stu-id="6696d-114">It is not derived from the function code or compared to the actual function output.</span></span> <span data-ttu-id="6696d-115">因此，此值可能不正確。</span><span class="sxs-lookup"><span data-stu-id="6696d-115">As such, the value might be inaccurate.</span></span>

## <a name="syntax"></a><span data-ttu-id="6696d-116">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6696d-116">SYNTAX</span></span>

<span data-ttu-id="6696d-117">函數的 OutputType 屬性具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="6696d-117">The OutputType attribute of functions has the following syntax:</span></span>

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

<span data-ttu-id="6696d-118">**ParameterSetName** 參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="6696d-118">The **ParameterSetName** parameter is optional.</span></span>

<span data-ttu-id="6696d-119">您可以在 OutputType 屬性中列出多個類型。</span><span class="sxs-lookup"><span data-stu-id="6696d-119">You can list multiple types in the OutputType attribute.</span></span>

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

<span data-ttu-id="6696d-120">您可以使用 **ParameterSetName** 參數來指出不同的參數集合會傳回不同的類型。</span><span class="sxs-lookup"><span data-stu-id="6696d-120">You can use the **ParameterSetName** parameter to indicate that different parameter sets return different types.</span></span>

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

<span data-ttu-id="6696d-121">將 OutputType 屬性語句放在語句之前的屬性清單中 `Param` 。</span><span class="sxs-lookup"><span data-stu-id="6696d-121">Place the OutputType attribute statements in the attributes list that precedes the `Param` statement.</span></span>

<span data-ttu-id="6696d-122">下列範例顯示在簡單的函式中，OutputType 屬性的位置。</span><span class="sxs-lookup"><span data-stu-id="6696d-122">The following example shows the placement of the OutputType attribute in a simple function.</span></span>

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

<span data-ttu-id="6696d-123">下列範例會顯示在 advanced 函數中的 OutputType 屬性位置。</span><span class="sxs-lookup"><span data-stu-id="6696d-123">The following example shows the placement of the OutputType attribute in advanced functions.</span></span>

```powershell
function AdvancedFunction1
{
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}

function AdvancedFunction2
{
  [CmdletBinding(SupportsShouldProcess=<Boolean>)]
  [OutputType([<Type>])]
  Param (
    [parameter(Mandatory=$true)]
    [String[]]
    $Parameter1
  )

  <function body>
}
```

## <a name="examples"></a><span data-ttu-id="6696d-124">範例</span><span class="sxs-lookup"><span data-stu-id="6696d-124">EXAMPLES</span></span>

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a><span data-ttu-id="6696d-125">範例1：建立具有字串 OutputType 的函式</span><span class="sxs-lookup"><span data-stu-id="6696d-125">Example 1: Create a function that has the OutputType of String</span></span>

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

<span data-ttu-id="6696d-126">若要查看產生的輸出類型屬性，請使用 `Get-Command` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6696d-126">To see the resulting output type property, use the `Get-Command` cmdlet.</span></span>

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a><span data-ttu-id="6696d-127">範例2：使用 Output 屬性工作表示動態輸出類型</span><span class="sxs-lookup"><span data-stu-id="6696d-127">Example 2: Use the Output attribute to indicate dynamic output types</span></span>

<span data-ttu-id="6696d-128">下列 advanced 函數會使用 OutputType 屬性來指出函式會根據函數命令中使用的參數集傳回不同的類型。</span><span class="sxs-lookup"><span data-stu-id="6696d-128">The following advanced function uses the OutputType attribute to indicate that the function returns different types depending on the parameter set used in the function command.</span></span>

```powershell
function Get-User
{
  [CmdletBinding(DefaultParameterSetName="ID")]

  [OutputType("System.Int32", ParameterSetName="ID")]
  [OutputType([String], ParameterSetName="Name")]

  Param (
    [parameter(Mandatory=$true, ParameterSetName="ID")]
    [Int[]]
    $UserID,

    [parameter(Mandatory=$true, ParameterSetName="Name")]
    [String[]]
    $UserName
  )

  <function body>
}
```

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a><span data-ttu-id="6696d-129">範例3：顯示實際的輸出與 OutputType 有何不同</span><span class="sxs-lookup"><span data-stu-id="6696d-129">Example 3: Shows when an actual output differs from the OutputType</span></span>

<span data-ttu-id="6696d-130">下列範例將示範 [輸出類型] 屬性值是否會顯示 OutputType 屬性的值，即使它不正確也是一樣。</span><span class="sxs-lookup"><span data-stu-id="6696d-130">The following example demonstrates that the output type property value displays the value of the OutputType attribute, even when it is inaccurate.</span></span>

<span data-ttu-id="6696d-131">`Get-Time`函數會傳回字串，其中包含任何 DateTime 物件中之時間的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="6696d-131">The `Get-Time` function returns a string that contains the short form of the time in any DateTime object.</span></span> <span data-ttu-id="6696d-132">但是，OutputType 屬性會回報它傳回 **system.string 物件。**</span><span class="sxs-lookup"><span data-stu-id="6696d-132">However, the OutputType attribute reports that it returns a **System.DateTime** object.</span></span>

```powershell
function Get-Time
{
  [OutputType([DateTime])]
  Param (
    [parameter(Mandatory=$true)]
    [Datetime]$DateTime
  )

  $DateTime.ToShortTimeString()
}
```

<span data-ttu-id="6696d-133">`GetType()`方法會確認函數會傳回字串。</span><span class="sxs-lookup"><span data-stu-id="6696d-133">The `GetType()` method confirms that the function returns a string.</span></span>

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

<span data-ttu-id="6696d-134">不過，OutputType 屬性（它會從 OutputType 屬性取得其值）會回報函數傳回 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="6696d-134">However, the OutputType property, which gets its value from the OutputType attribute, reports that the function returns a **DateTime** object.</span></span>

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a><span data-ttu-id="6696d-135">範例4：不應有輸出的函式</span><span class="sxs-lookup"><span data-stu-id="6696d-135">Example 4: A function  that shouldn't have output</span></span>

<span data-ttu-id="6696d-136">下列範例顯示應該執行的自訂函式，但不傳回任何動作。</span><span class="sxs-lookup"><span data-stu-id="6696d-136">The following example shows a custom function that should perform and action but not return anything.</span></span>

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a><span data-ttu-id="6696d-137">注意</span><span class="sxs-lookup"><span data-stu-id="6696d-137">NOTES</span></span>

<span data-ttu-id="6696d-138">**FunctionInfo** 物件的 OutputType 屬性值是 **PSTypeName** 物件的陣列，其中每個物件都有 Name 和 Type 屬性。</span><span class="sxs-lookup"><span data-stu-id="6696d-138">The value of the OutputType property of a **FunctionInfo** object is an array of **System.Management.Automation.PSTypeName** objects, each of which have Name and Type properties.</span></span>

<span data-ttu-id="6696d-139">若只要取得每個輸出類型的名稱，請使用具有下列格式的命令。</span><span class="sxs-lookup"><span data-stu-id="6696d-139">To get only the name of each output type, use a command with the following format.</span></span>

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

<span data-ttu-id="6696d-140">OutputType 屬性的值可以是 null。</span><span class="sxs-lookup"><span data-stu-id="6696d-140">The value of the OutputType property can be null.</span></span> <span data-ttu-id="6696d-141">當輸出不是 .NET 類型時，請使用 null 值，例如 **WMI** 物件或物件的格式化視圖。</span><span class="sxs-lookup"><span data-stu-id="6696d-141">Use a null value when the output is a not a .NET type, such as a **WMI** object or a formatted view of an object.</span></span>

## <a name="see-also"></a><span data-ttu-id="6696d-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6696d-142">SEE ALSO</span></span>

[<span data-ttu-id="6696d-143">about_Functions</span><span class="sxs-lookup"><span data-stu-id="6696d-143">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="6696d-144">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="6696d-144">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="6696d-145">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="6696d-145">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="6696d-146">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="6696d-146">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="6696d-147">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="6696d-147">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)
