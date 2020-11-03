---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: 3c34022c84c26ee0d8395fc589e8d1da957979b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204984"
---
# New-Object

## 概要
建立 Microsoft .NET Framework 或 COM 物件的執行個體。

## SYNTAX

### Net (預設值)

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### Com

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## DESCRIPTION

`New-Object`Cmdlet 會建立 .NET Framework 或 COM 物件的實例。

您可以指定 .NET Framework 類別的類型或 COM 物件的 ProgID。 根據預設，您需要輸入 .NET Framework 類別的完整名稱，而這個 Cmdlet 會傳回該類別執行個體的參考。 若要建立 COM 物件的實例，請使用 **ComObject** 參數，並指定物件的 ProgID 做為其值。

## 範例

### 範例1：建立 System. Version 物件

此範例會使用 "1.2.3.4" 字串做為函式，建立 **system.object** 物件。

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### 範例2：建立 Internet Explorer COM 物件

這個範例會建立代表 Internet Explorer 應用程式之 COM 物件的兩個實例。 第一個實例使用 **屬性** 參數雜湊表來呼叫 **Navigate2** 方法，並將物件的 **Visible** 屬性設定為， `$True` 讓應用程式成為可見的。
第二個實例會使用個別命令取得相同的結果。

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### 範例3：使用 Strict 參數來產生非終止錯誤

這個範例示範新增 **Strict** 參數會導致 `New-Object` Cmdlet 在 COM 物件使用 interop 元件時產生非終止錯誤。

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### 範例4：建立 COM 物件來管理 Windows 桌面

這個範例示範如何建立和使用 COM 物件來管理您的 Windows 桌面。

第一個命令會使用 Cmdlet 的 **ComObject** 參數 `New-Object` ，以 **Shell. 應用程式** ProgID 來建立 COM 物件。 它會將產生的物件儲存在 `$ObjShell` 變數中。 第二個命令會 `$ObjShell` 以管道將變數傳送至 `Get-Member` Cmdlet，此 Cmdlet 會顯示 COM 物件的屬性和方法。 在這些方法中，方法是 **ToggleDesktop** 方法。 第三個命令呼叫物件的 **ToggleDesktop** 方法，將桌面上開啟的視窗最小化。

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### 範例5：傳遞多個引數給函式

這個範例示範如何使用接受多個參數的函式來建立物件。 使用 **ArgumentList** 參數時，必須將參數放在陣列中。

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

PowerShell 會將陣列的每個成員系結至函式的參數。

> [!NOTE]
> 這個範例會使用參數展開來提高可讀性。 如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

### 範例6：呼叫採用陣列作為單一參數的函式

這個範例示範如何使用接受陣列或集合參數的函式來建立物件。 陣列參數必須放在另一個陣列內。

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

在此範例中，第一次嘗試建立物件失敗。 PowerShell 嘗試將的三個成員系結至函式的 `$array` 參數，但此函式不會採用三個參數。 `$array`在另一個陣列中換行，可防止 PowerShell 嘗試將的三個成員系結至函式的 `$array` 參數。

## PARAMETERS

### -ArgumentList

指定要傳遞給 .NET Framework 類別之函式的引數陣列。 如果此函式採用屬於陣列的單一參數，則您必須將該參數包裝在另一個陣列中。 例如：

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)。

**ArgumentList** 的別名是 **Args** 。

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComObject

指定 COM 物件的程式設計識別碼 (ProgID)。

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

設定屬性值，並叫用新物件的方法。

輸入雜湊表，其中索引鍵為屬性或方法的名稱，而值為屬性值或方法引數。 `New-Object` 建立物件並設定每個屬性值，並依其在雜湊表中出現的順序來叫用每個方法。

如果新的物件衍生自 **PSObject** 類別，而且您指定了不存在於物件上的屬性，則會 `New-Object` 將指定的屬性加入至物件做為 NoteProperty。 如果物件不是 **PSObject** ，命令就會產生非終止錯誤。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strict

指出當您嘗試建立的 COM 物件使用 interop 元件時，此 Cmdlet 會產生非終止錯誤。 這個功能可以區分真正的 COM 物件與使用 COM 可呼叫包裝函式的 .NET Framework 物件。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

指定 .NET Framework 類別的完整名稱。 您無法同時指定 **TypeName** 參數和 **ComObject** 參數。

```yaml
Type: System.String
Parameter Sets: Net
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### Object

`New-Object` 傳回所建立的物件。

## 注意

- `New-Object` 提供 VBScript CreateObject 函式最常使用的功能。 `Set objShell = CreateObject("Shell.Application")`VBScript 中的語句可 `$objShell = New-Object -COMObject "Shell.Application"` 在 PowerShell 中轉譯為。
- `New-Object` 利用 Windows Script Host 環境中的可用功能，輕鬆地從命令列和腳本內使用 .NET Framework 物件，以擴充其功能。

## 相關連結

[about_Object_Creation](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[Compare-Object](Compare-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

