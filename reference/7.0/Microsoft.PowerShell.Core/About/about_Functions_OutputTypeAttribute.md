---
description: 描述報告函式所傳回之物件類型的屬性。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_OutputTypeAttribute
ms.openlocfilehash: 72133dc124c28f375afa90f8b32b004ba72f0c97
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207428"
---
# <a name="about-functions-outputtypeattribute"></a>關於函式 OutputTypeAttribute

## <a name="short-description"></a>簡短描述
描述報告函式所傳回之物件類型的屬性。

## <a name="long-description"></a>詳細描述

OutputType 屬性會列出函式傳回之物件的 .NET 類型。 您可以使用其選擇性的 ParameterSetName 參數，針對每個參數集列出不同的輸出類型。

Simple 和 advanced 函式支援 OutputType 屬性。 它與 CmdletBinding 屬性無關。

OutputType 屬性會提供 Cmdlet 所傳回之 **FunctionInfo** 物件的 OutputType 屬性的值 `Get-Command` 。

OutputType 屬性值只是文件備註。 它不是衍生自函式程式碼，或與實際的函式輸出比較。 因此，此值可能不正確。

## <a name="syntax"></a>SYNTAX

函數的 OutputType 屬性具有下列語法：

```
[OutputType([<TypeLiteral>], ParameterSetName="<Name>")]
[OutputType("<TypeNameString>", ParameterSetName="<Name>")]
```

**ParameterSetName** 參數是選擇性的。

您可以在 OutputType 屬性中列出多個類型。

```
[OutputType([<Type1>],[<Type2>],[<Type3>])]
```

您可以使用 **ParameterSetName** 參數來指出不同的參數集合會傳回不同的類型。

```
[OutputType([<Type1>], ParameterSetName=("<Set1>","<Set2>"))]
[OutputType([<Type2>], ParameterSetName="<Set3>")]
```

將 OutputType 屬性語句放在語句之前的屬性清單中 `Param` 。

下列範例顯示在簡單的函式中，OutputType 屬性的位置。

```powershell
function SimpleFunction2
{
  [OutputType([<Type>])]
  Param ($Parameter1)

  <function body>
}
```

下列範例會顯示在 advanced 函數中的 OutputType 屬性位置。

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

## <a name="examples"></a>範例

### <a name="example-1-create-a-function-that-has-the-outputtype-of-string"></a>範例1：建立具有字串 OutputType 的函式

```powershell
function Send-Greeting
{
  [OutputType([String])]
  Param ($Name)

  "Hello, $Name"
}
```

若要查看產生的輸出類型屬性，請使用 `Get-Command` Cmdlet。

```powershell
(Get-Command Send-Greeting).OutputType
```

```Output
Name                                               Type
----                                               ----
System.String                                      System.String
```

### <a name="example-2-use-the-output-attribute-to-indicate-dynamic-output-types"></a>範例2：使用 Output 屬性工作表示動態輸出類型

下列 advanced 函數會使用 OutputType 屬性來指出函式會根據函數命令中使用的參數集傳回不同的類型。

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

### <a name="example-3-shows-when-an-actual-output-differs-from-the-outputtype"></a>範例3：顯示實際的輸出與 OutputType 有何不同

下列範例將示範 [輸出類型] 屬性值是否會顯示 OutputType 屬性的值，即使它不正確也是一樣。

`Get-Time`函數會傳回字串，其中包含任何 DateTime 物件中之時間的簡短形式。 但是，OutputType 屬性會回報它傳回 **system.string 物件。**

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

`GetType()`方法會確認函數會傳回字串。

```powershell
(Get-Time -DateTime (Get-Date)).GetType().FullName
```

```Output
System.String
```

不過，OutputType 屬性（它會從 OutputType 屬性取得其值）會回報函數傳回 **DateTime** 物件。

```powershell
(Get-Command Get-Time).OutputType
```

```Output
Name                                      Type
----                                      ----
System.DateTime                           System.DateTime
```

### <a name="example-4-a-function--that-shouldnt-have-output"></a>範例4：不應有輸出的函式

下列範例顯示應該執行的自訂函式，但不傳回任何動作。

```powershell
function Invoke-Notepad
{
  [OutputType([System.Void])]
  Param ()
  & notepad.exe | Out-Null
}
```

## <a name="notes"></a>注意

**FunctionInfo** 物件的 OutputType 屬性值是 **PSTypeName** 物件的陣列，其中每個物件都有 Name 和 Type 屬性。

若只要取得每個輸出類型的名稱，請使用具有下列格式的命令。

```powershell
(Get-Command Get-Time).OutputType | ForEach {$_.Name}
```

OutputType 屬性的值可以是 null。 當輸出不是 .NET 類型時，請使用 null 值，例如 **WMI** 物件或物件的格式化視圖。

## <a name="see-also"></a>另請參閱

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)
