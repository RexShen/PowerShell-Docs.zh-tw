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
# Add-Type

## 概要
將 Microsoft .NET Core 類別新增至 PowerShell 會話。

## SYNTAX

### FromSource (預設) 

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromMember

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromPath

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromLiteralPath

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromAssemblyName

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

此 `Add-Type` Cmdlet 可讓您在 PowerShell 會話中定義 Microsoft .Net Core 類別。 然後，您可以使用 Cmdlet 來具現化物件， `New-Object` 並使用物件，就像使用任何 .Net Core 物件一樣。 如果您將 `Add-Type` 命令新增至 powershell 設定檔，則可在所有 powershell 會話中使用類別。

您可以透過指定現有組件或原始程式碼檔案來指定類型，或者指定變數中內嵌或預存的原始程式碼。 您甚至可以指定方法，並 `Add-Type` 定義和產生類別。 在 Windows 上，您可以使用這項功能，讓平台叫用 (P/Invoke) PowerShell 中非受控函式的呼叫。 如果您指定原始程式碼，請 `Add-Type` 編譯指定的原始程式碼，然後產生包含新 .Net Core 類型的記憶體內元件。

您可以使用的參數 `Add-Type` 來指定替代語言和編譯器，c # 是預設的、編譯器選項、元件相依性、類別命名空間、類型名稱，以及產生的元件。

從 PowerShell 7 開始， `Add-Type` 如果已經存在具有相同名稱的型別，則不會編譯型別。 此外，也 `Add-Type` 會尋找資料夾中 `ref` 包含之資料夾下的元件 `pwsh.dll` 。

## 範例

### 範例1：將 .NET 型別新增至會話

此範例會藉由指定儲存在變數中的原始程式碼，將 **BasicTest** 類別新增至會話。 **BasicTest** 類別可用來新增整數、建立物件，以及將整數相乘。

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

`$Source`變數會儲存類別的原始程式碼。 此類型有一個稱為的靜態方法 `Add` ，以及一個稱為的非靜態方法 `Multiply` 。

`Add-Type`Cmdlet 會將類別新增至會話。 因為它是使用內嵌原始程式碼，所以命令會使用 **TypeDefinition** 參數來指定變數中的程式碼 `$Source` 。

`Add` **BasicTest** 類別的靜態方法會使用雙冒號字元 (`::`) 來指定類別的靜態成員。 系統會加入整數，並顯示總和。

此 Cmdlet 會具現 `New-Object` 化 **BasicTest** 類別的實例。 它會將新的物件儲存在 `$BasicTestObject` 變數中。

`$BasicTestObject` 使用 `Multiply` 方法。 整數會相乘，並顯示產品。

### 範例2：檢查新增的類型

此範例會使用 `Get-Member` Cmdlet 來檢查 `Add-Type` 和 `New-Object` Cmdlet 在 **範例 1** 中建立的物件。

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

此 `Get-Member` Cmdlet 會取得新增至會話之 **BasicTest** 類別的類型和成員 `Add-Type` 。 此 `Get-Member` 命令會顯示它是衍生自 **system.object** 類別的 **>system.runtimetype** 物件。

`Get-Member`**靜態** 參數會取得 **BasicTest** 類別的靜態屬性和方法。 輸出會顯示 `Add` 已包含方法。

`Get-Member`Cmdlet 會取得儲存在變數中之物件的成員 `$BasicTestObject` 。
`$BasicTestObject` 是使用 `New-Object` Cmdlet 搭配 **BasicTest** 類別所建立。 輸出會顯示變數的值 `$BasicTestObject` 是 **BasicTest** 類別的實例，而且它包含名為的成員 `Multiply` 。

### 範例3：從元件新增類型

此範例會將元件中的類別新增 `NJsonSchema.dll` 至目前的會話。

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

`Set-Location` 使用 **Path** 參數來指定 `$PSHOME` 變數。 變數會參照 DLL 檔案所在的 PowerShell 安裝目錄。

`$AccType`變數會儲存使用 Cmdlet 建立的物件 `Add-Type` 。 `Add-Type` 使用 **AssemblyName** 參數指定元件的名稱。 星號 (`*`) 萬用字元可讓您取得正確的元件，即使您不確定名稱或拼寫時也一樣。 **PassThru** 參數會產生代表已新增至會話之類別的物件。

### 範例4：呼叫原生 Windows Api

此範例示範如何在 PowerShell 中呼叫原生 Windows Api。 `Add-Type` 使用平台叫用 (P/Invoke) 機制，從 PowerShell 呼叫中的函式 `User32.dll` 。 此範例僅適用于執行 Windows 作業系統的電腦。

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

變數會儲存函式 `$Signature` 的 c # 簽章 `ShowWindowAsync` 。 為了確保在 PowerShell 會話中可以看見產生的方法， `public` 關鍵字已新增至標準簽章。 如需詳細資訊，請參閱 [ShowWindowAsync 函數](/windows/win32/api/winuser/nf-winuser-showwindowasync)。

`$ShowWindowAsync`變數會儲存 `Add-Type` **PassThru** 參數所建立的物件。
Cmdlet 會將函式 `Add-Type` 新增 `ShowWindowAsync` 至 PowerShell 會話作為靜態方法。 此命令會使用 **MemberDefinition** 參數來指定儲存在變數中的方法定義 `$Signature` 。 此命令會使用 **Name** 和 **Namespace** 參數指定類別的名稱和命名空間。 **PassThru** 參數會產生代表類型的物件。

新的 `ShowWindowAsync` 靜態方法用於命令中，以將 PowerShell 主控台的最小化和還原。 方法採用兩個參數：視窗控制碼，以及指定視窗顯示方式的整數。

若要將 PowerShell 主控台最小化，請 `ShowWindowAsync` 使用 `Get-Process` Cmdlet 搭配 `$PID` 自動變數來取得裝載目前 PowerShell 會話的程式。 然後，它會使用目前進程的 **MainWindowHandle** 屬性，以及 `2` 代表值的值 `SW_MINIMIZE` 。

若要還原視窗，請 `ShowWindowAsync` 使用 `4` 代表值的視窗位置值 `SW_RESTORE` 。

若要將視窗最大化，請使用 `3` 代表的值 `SW_MAXIMIZE` 。

## PARAMETERS

### -AssemblyName

指定包含類型之組件的名稱。 `Add-Type` 從指定的元件取得類型。 當您要根據元件名稱建立類型時，需要這個參數。

輸入元件的完整或簡單名稱（也稱為部分名稱）。 組件名稱允許使用萬用字元。 如果您輸入簡單或部分名稱，請將 `Add-Type` 它解析成完整名稱，然後使用完整名稱載入元件。

此參數不接受路徑或檔案名。 若要輸入元件動態連結程式庫的路徑 (DLL) 檔，請使用 **path** 參數。

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

### -CompilerOptions

指定原始程式碼編譯器的選項。 這些選項會在不經過修訂的情況下傳送至編譯器。

此參數可讓您指示編譯器產生可執行檔、內嵌資源，或設定命令列選項，例如 `/unsafe` 選項。

您無法在同一個命令中使用 **CompilerOptions** 和 **ReferencedAssemblies** 參數。

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

### -IgnoreWarnings

忽略編譯器警告。 您可以使用這個參數來防止將 `Add-Type` 編譯器警告當作錯誤處理。

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

### -Language

指定在原始程式碼中使用的語言。 此參數可接受的值是 **CSharp** 。

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

### -LiteralPath

指定包含類型之原始程式碼檔案或組件 DLL 檔案的路徑。 與 **Path** 不同， **LiteralPath** 參數的值會完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

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

### -MemberDefinition

為類別指定新的屬性或方法。 `Add-Type` 產生支援屬性或方法所需的範本程式碼。

在 Windows 上，您可以使用這項功能，讓平台叫用 (P/Invoke) PowerShell 中非受控函式的呼叫。

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

### -Name

指定要建立之類別的名稱。 從成員定義產生類型時，此參數是必要的。

類別名稱和命名空間在工作階段中必須是唯一的。 您無法卸載或變更類型。
若要變更類型的程式碼，您必須變更名稱或啟動新的 PowerShell 會話。
否則命令會失敗。

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

### -Namespace

指定類型的命名空間。

如果命令中未包含此參數，則會在 **AddType. microsoft.powershell.commands.addtype.autogeneratedtypes** 命名空間中建立此類型。 如果參數包含在具有空字串值或值的命令中 `$Null` ，則會在全域命名空間中產生類型。

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

### -OutputAssembly

使用位置中的指定名稱來產生組件的 DLL 檔。 輸入選擇性的路徑和檔案名。 允許使用萬用字元。 根據預設， `Add-Type` 只會在記憶體中產生元件。

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

### -OutputType

指定輸出組件的輸出類型。 預設不會指定任何輸出類型。 此參數只有在命令中已指定輸出組件時才有效。 如需這些值的詳細資訊，請參閱 [ Outputassemblytype 列舉](/dotnet/api/microsoft.powershell.commands.outputassemblytype)。

此參數可接受的值如下：

- ConsoleApplication
- 程式庫
- WindowsApplication

> [!IMPORTANT]
> 從 PowerShell 7.1， `ConsoleApplication` 和 `WindowsApplication` 不受支援，而且如果其中一個指定為 **OutputType** 參數的值，則 powershell 會擲回終止錯誤。

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

### -PassThru

傳回代表已新增之類型的 **System.Runtime** 物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Path

指定包含類型之原始程式碼檔案或組件 DLL 檔案的路徑。

如果您提交原始程式碼檔，則會 `Add-Type` 編譯檔案中的程式碼，並建立類型的記憶體內元件。 **Path** 值中所指定的副檔名會決定使用的編譯器 `Add-Type` 。

如果您提交元件檔，則 `Add-Type` 會從元件取得類型。 若要指定記憶體內組件或全域組件快取，請使用 **AssemblyName** 參數。

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

### -ReferencedAssemblies

指定類型相依的組件。 依預設，會 `Add-Type` 參考 `System.dll` 和 `System.Management.Automation.dll` 。 除了參照預設組件之外，也會參照您使用此參數指定的組件。

從 PowerShell 6 開始， **ReferencedAssemblies** 不會包含預設的 .net 元件。 您必須在傳遞給此參數的值中包含特定的參考。

您無法在同一個命令中使用 **CompilerOptions** 和 **ReferencedAssemblies** 參數。

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

### -TypeDefinition

指定包含類型定義的原始程式碼。 以字串或 here-string 輸入原始程式碼，或者輸入包含原始程式碼的變數。 如需有關此字串的詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)。

在您的類型定義中包含命名空間宣告。 如果您省略命名空間宣告，您的類型的名稱可能會與其他類型或其他類型的捷徑名稱相同，這會造成意外覆寫。 例如，如果您定義了一個名為 **exception** 的型別，則使用 **exception** 作為 system.string 快捷 **方式的腳本將會** 失敗。

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

### -UsingNamespace

指定類別需要的其他命名空間。 這與 c # 關鍵字很類似 `Using` 。

根據預設，會 `Add-Type` 參考 **System** 命名空間。 使用 **MemberDefinition** 參數時， `Add-Type` 預設也會參考 **system.runtime.interopservices.outattribute** 命名空間。 除了參照預設命名空間之外，也會參照您使用 **UsingNamespace** 參數新增的命名空間。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法將物件沿著管線向下傳送至 `Add-Type` 。

## 輸出

### 無或系統類型

當您使用 **PassThru** 參數時，會傳回 `Add-Type` 代表新類型的 **system.object** 物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

您新增的類型只存在於目前的工作階段。 若要在所有會話中使用類型，請將它們新增至您的 PowerShell 設定檔。 如需設定檔的詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

型別名稱和命名空間在會話中必須是唯一的。 您無法卸載或變更類型。 如果您需要變更類型的程式碼，您必須變更名稱或啟動新的 PowerShell 會話。
否則命令會失敗。

在 Windows PowerShell (5.1 版和以下版本) 中，您需要 `Add-Type` 針對尚未載入的任何功能使用。 最常見的情況是，這適用于全域組件快取 (GAC) 中找到的元件。
在 PowerShell 6 和更新版本中，沒有任何 GAC，因此 PowerShell 會在中安裝它自己的元件 `$PSHome` 。
這些元件會在要求時自動載入，因此不需要使用 `Add-Type` 載入它們。 不過， `Add-Type` 仍允許使用，以允許腳本與任何 PowerShell 版本隱含相容。

GAC 中的元件可以依類型名稱載入，而不是依路徑載入。 從任意路徑載入元件需要 `Add-Type` ，因為無法自動載入這些元件。

## 相關連結

[about_Profiles](../Microsoft.PowerShell.Core/About/about_profiles.md)

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Add-Member](Add-Member.md)

[New-Object](New-Object.md)

[ Outputassemblytype](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[平台叫用 (P/Invoke)](/dotnet/standard/native-interop/pinvoke)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
