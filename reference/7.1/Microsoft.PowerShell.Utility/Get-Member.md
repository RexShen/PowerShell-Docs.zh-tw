---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-member?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Member
ms.openlocfilehash: 833be15e4018a0c25b0f604b5c84ab077c584cae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202828"
---
# Get-Member

## 概要
取得物件的屬性和方法。

## SYNTAX

```
Get-Member [-InputObject <PSObject>] [[-Name] <String[]>] [-MemberType <PSMemberTypes>]
 [-View <PSMemberViewTypes>] [-Static] [-Force] [<CommonParameters>]
```

## DESCRIPTION

`Get-Member`Cmdlet 會取得物件的成員、屬性和方法。

若要指定物件，請使用 **InputObject** 參數，或使用管線將物件傳送至 `Get-Member` 。 若要取得靜態成員 (類別的成員，而非執行個體的成員) 的相關資訊，請使用 **Static** 參數。 若只要取得特定類型的成員 (例如 **NoteProperties** )，請使用 **MemberType** 參數。

## 範例

### 範例 1：取得處理程序物件的成員

此命令會顯示 Cmdlet 所產生之服務物件的屬性和方法 `Get-Service` 。

因為 `Get-Member` 命令的部分沒有任何參數，所以它會使用參數的預設值。 根據預設，不 `Get-Member` 會取得靜態或內部成員。

```powershell
Get-Service | Get-Member
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, System.EventArgs)
Close                     Method        void Close()
Continue                  Method        void Continue()
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.ServiceControllerSt...
BinaryPathName            Property      System.String {get;set;}
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DelayedAutoStart          Property      System.Boolean {get;set;}
DependentServices         Property      System.ServiceProcess.ServiceController[] DependentServices {get;}
Description               Property      System.String {get;set;}
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle ServiceHandle {get;}
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] ServicesDependedOn {get;}
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType {get;}
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartType {get;}
StartupType               Property      Microsoft.PowerShell.Commands.ServiceStartupType {get;set;}
Status                    Property      System.ServiceProcess.ServiceControllerStatus Status {get;}
UserName                  Property      System.String {get;set;}
ToString                  ScriptMethod  System.Object ToString();
```

### 範例 2：取得服務物件的成員

這個範例會取得 Cmdlet 所抓取之服務物件 (屬性和方法) 的所有成員 `Get-Service` ，包括內建成員（例如 **PSBase** 、 **PSObject** 和 **get_** 和 **set_** 方法）。

```powershell
Get-Service | Get-Member -Force
(Get-Service Schedule).PSBase
```

此 `Get-Member` 命令會使用 **Force** 參數將物件的內建成員和編譯器產生的成員新增到顯示中。 當您使用這些屬性和方法時，可以比照與您使用物件的已調整方法時相同的方式。 第二個命令示範如何顯示 Schedule 服務之 PSBase 屬性的值。

### 範例 3：取得服務物件的擴充成員

這個範例會取得使用檔案或 Cmdlet 擴充之服務物件的方法和屬性 `Types.ps1xml` `Add-Member` 。

```powershell
Get-Service | Get-Member -View Extended
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name             MemberType    Definition
----             ----------    ----------
Name             AliasProperty Name = ServiceName
RequiredServices AliasProperty RequiredServices = ServicesDependedOn
ToString         ScriptMethod  System.Object ToString();
```

此 `Get-Member` 命令會使用 **View** 參數，只取得服務物件的擴充成員。 在此情況下，擴充成員是 **Name** 屬性，它是 **ServiceName** 屬性的別名屬性。

### 範例 4：取得事件記錄檔物件的指令碼屬性

此範例會取得事件檢視器中系統記錄檔中事件記錄檔物件的腳本屬性。

```powershell
Get-WinEvent -LogName System -MaxEvents 1 | Get-Member -MemberType NoteProperty
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.EventLogRecord

Name    MemberType   Definition
----    ----------   ----------
Message NoteProperty string Message=The machine-default permission settings do not grant Local ...
```

**MemberType** 參數只會取得 `NoteProperty` 其 **MemberType** 屬性值為的物件。

此命令會傳回 **EventLogRecord** 物件的 **Message** 屬性。

### 範例 5︰取得具有指定屬性的物件

此範例會從 Cmdlet 清單的輸出中取得具有 **MachineName** 屬性的物件。

`$list`變數包含要評估的 Cmdlet 清單。 **Foreach** 語句會叫用每個命令，並將結果傳送至 `Get-Member` 。 **Name** 參數會將的結果限制 `Get-Member` 為名稱為 **MachineName** 的成員。

```powershell
$list = "Get-Process", "Get-Service", "Get-Culture", "Get-PSDrive", "Get-ExecutionPolicy"
foreach ($cmdlet in $list) {& $cmdlet | Get-Member -Name MachineName}
```

```Output
   TypeName: System.Diagnostics.Process

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;}

   TypeName: System.Service.ServiceController#StartupType

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;set;}
```

結果顯示只有處理常式物件和服務物件具有 **MachineName** 屬性。

### 範例 6：取得陣列的成員

這個範例示範如何尋找物件陣列的成員。 當您使用管線將物件的物件傳送至時 `Get-Member` ，此 Cmdlet 會針對陣列中的每個唯一物件類型，傳回成員清單。
如果您使用 **InputObject** 參數傳遞陣列，則會將陣列視為單一物件。

```powershell
$array = @(1,'hello')
$array | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType Definition
----        ---------- ----------
CompareTo   Method     int CompareTo(System.Object value), int CompareTo(int value), int ICompar...
Equals      Method     bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int...
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
GetTypeCode Method     System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method     bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method     byte IConvertible.ToByte(System.IFormatProvider provider)
...

   TypeName: System.String

Name                 MemberType            Definition
----                 ----------            ----------
Clone                Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo            Method                int CompareTo(System.Object value), int CompareTo(str...
Contains             Method                bool Contains(string value), bool Contains(string val...
CopyTo               Method                void CopyTo(int sourceIndex, char[] destination, int ...
EndsWith             Method                bool EndsWith(string value), bool EndsWith(string val...
EnumerateRunes       Method                System.Text.StringRuneEnumerator EnumerateRunes()
Equals               Method                bool Equals(System.Object obj), bool Equals(string va...
GetEnumerator        Method                System.CharEnumerator GetEnumerator(), System.Collect...
GetHashCode          Method                int GetHashCode(), int GetHashCode(System.StringCompa...
...
```

```powershell
Get-Member -InputObject $array
```

```Output
   TypeName: System.Object[]

Name           MemberType            Definition
----           ----------            ----------
Add            Method                int IList.Add(System.Object value)
Address        Method                System.Object&, System.Private.CoreLib, Version=4.0.0.0, Cu...
Clear          Method                void IList.Clear()
Clone          Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo      Method                int IStructuralComparable.CompareTo(System.Object other, Sy...
...
```

`$array`變數包含 **Int32** 物件和 **string** 物件，如同將陣列輸送至時所見 `Get-Member` 。 `$array`使用 **InputObject** 參數傳遞時，會傳回 `Get-Member` **Object []** 類型的成員。

### 範例 7︰決定您可以設定哪些物件屬性

這個範例示範如何判斷物件的哪些屬性可以變更。

```powershell
$File = Get-Item c:\test\textFile.txt
$File.PSObject.Properties | Where-Object isSettable | Select-Object -Property Name
```

```Output
Name
----
PSPath
PSParentPath
PSChildName
PSDrive
PSProvider
PSIsContainer
IsReadOnly
CreationTime
CreationTimeUtc
LastAccessTime
LastAccessTimeUtc
LastWriteTime
LastWriteTimeUtc
Attributes
```

## PARAMETERS

### -Force

將內建成員和編譯器產生的 **get_** 以及 **set_** 方法加入至顯示器。
下列清單說明當您使用 **Force** 參數時會新增的屬性：

- **PSBase** ：沒有副檔名或調整的 .net 物件原始屬性。 這些是為物件類別定義的屬性。
- **PSAdapted** 。 PowerShell 擴充類型系統中定義的屬性和方法。
- **PSExtended** 。 在檔案中或使用 Cmdlet 新增的屬性和方法 `Types.ps1xml` `Add-Member` 。
- **PSObject** 。 將基底物件轉換成 PowerShell **PSObject** 物件的介面卡。
- **PSTypeNames** 。 描述物件的物件類型清單 (依明確性順序)。 格式化物件時，PowerShell 會在 PowerShell 安裝目錄中的檔案中搜尋類型 `Format.ps1xml` (`$PSHOME`) 。 它會使用所找到的第一個類型的格式定義。

根據預設， `Get-Member` 會在 **基底** 和調整以外的所有 **Adapted** 視圖中取得這些屬性，但是不會顯示它們。

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

### -InputObject

指定要供抓取成員的物件。

使用 **InputObject** 參數與將物件輸送至不同 `Get-Member` 。 差異如下：

- 當您使用管線將物件集合傳送至時 `Get-Member` ，會 `Get-Member` 取得集合中個別物件的成員，例如字串陣列中每個字串的屬性。
- 當您使用 **InputObject** 來提交物件的集合時，會 `Get-Member` 取得集合的成員，例如字串陣列中陣列的屬性。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberType

指定此 Cmdlet 取得的成員類型。 預設為 **All** 。

此參數可接受的值為：

- AliasProperty
- CodeProperty
- 屬性
- NoteProperty
- ScriptProperty
- 屬性
- PropertySet
- 方法
- CodeMethod
- ScriptMethod
- 方法
- ParameterizedProperty
- MemberSet
- 事件
- 動態
- 全部

如需這些值的詳細資訊，請參閱 [ Psmembertypes 列舉](/dotnet/api/system.management.automation.psmembertypes)。

並非所有物件都有每個類型的成員。 如果您指定物件沒有的成員類型，PowerShell 會傳回 null 值。

若要取得相關類型的成員 (例如所有擴充成員)，請使用 **View** 參數。 如果您搭配使用 **MemberType** 參數與 **Static** 或 **View** 參數，則 `Get-Member` 會取得同時屬於這兩個集合的成員。

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定一個或多個屬性的名稱或物件的方法。 `Get-Member` 只取得指定的屬性和方法。

如果您使用 **Name** 參數搭配 **MemberType** 、 **View** 或 **Static** 參數，只會 `Get-Member` 取得符合所有參數條件的成員。

若要依名稱取得靜態成員，請使用 **Static** 參數搭配 **Name** 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Static

指出此 Cmdlet 只會取得物件的靜態屬性和物件。 靜態屬性和方法是在物件的類別上定義，而非在類別的任何特定執行個體上定義。

如果您使用 **Static** 參數搭配 **View** 參數，則 **View** 參數會被忽略。
如果您使用 **靜態** 參數搭配 **MemberType** 參數，則 `Get-Member` 只會取得同時屬於這兩個集合的成員。

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

### -View

指定此 Cmdlet 只會取得特定的類型屬性和方法。 請指定一個或多個值。 預設 **值為 [已調整** ]、[ **擴充** ]。

此參數可接受的值為：

- Base： 只取得 .NET 物件的原始屬性和方法 (沒有副檔名或調整) 。
- Adapted： 只取得 PowerShell 擴充類型系統中定義的屬性和方法。
- Extended： 只取得檔案中新增的屬性和方法， `Types.ps1xml` 或使用 `Add-Member` Cmdlet。
- 全部。 取得 Base、Adapted 及 Extended 檢視中的成員。

**View** 參數會決定要擷取的成員，而不只是決定那些成員的顯示。

若要取得特定的成員類型 (例如指令碼屬性)，請使用 **MemberType** 參數。 如果您在同一個命令中使用 **MemberType** 和 **View** 參數，則 `Get-Member` 會取得同時屬於這兩個集合的成員。 如果您在相同的命令中使用 **Static** 和 **View** 參數，則 **View** 會被忽略。

```yaml
Type: System.Management.Automation.PSMemberViewTypes
Parameter Sets: (All)
Aliases:
Accepted values: Extended, Adapted, Base, All

Required: False
Position: Named
Default value: Adapted, Extended
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將任何物件傳送至 `Get-Member` 。

## 輸出

### Microsoft.PowerShell.Commands.MemberDefinition

`Get-Member` 針對其取得的每個屬性或方法傳回物件。

## 注意

您可以使用 **InputObject** 參數，或使用管線將物件（前面加上逗號）傳送至來取得集合物件的相關資訊 `Get-Member` 。

您可以 `$This` 在定義新屬性和方法之值的腳本區塊中使用自動變數。 `$This`變數是指要加入屬性和方法之物件的實例。 如需變數的詳細資訊 `$This` ，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

如果您傳遞代表 _類型_ 的物件，例如類型常值（例如），則會傳回 `[int]` `Get-Member` 類型的相關資訊 `[System.RuntimeType]` 。 不過，當您使用 **靜態** 參數時，會傳回 `Get-Member` 實例所表示之特定類型的靜態成員 `System.RuntimeType` 。

## 相關連結

[Add-Member](Add-Member.md)

