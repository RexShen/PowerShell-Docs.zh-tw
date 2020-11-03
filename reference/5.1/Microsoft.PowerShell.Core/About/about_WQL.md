---
description: 描述 WMI 查詢語言 (WQL)，這可用於取得 Windows PowerShell 中的 WMI 物件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207880"
---
# <a name="about-wql"></a>關於 WQL

## <a name="short-description"></a>簡短描述

描述 WMI 查詢語言 (WQL)，這可用於取得 Windows PowerShell 中的 WMI 物件。

## <a name="long-description"></a>詳細描述

WQL 是 Windows Management Instrumentation (WMI) 查詢語言，這是用來從 WMI 取得資訊的語言。

在 Windows PowerShell 中，您不需要使用 WQL 來執行 WMI 查詢。
相反地，您可以使用 Get-WmiObject 或 Get-CimInstance Cmdlet 的參數。 WQL 查詢的速度比標準 Get-WmiObject 命令還快，而且當命令在數百個系統上執行時，改善的效能也會明顯。 不過，請確定您花費在撰寫成功 WQL 查詢的時間不會超過效能改進。

您需要使用 WQL 的基本 WQL 語句包括 Select、Where 和 From。

## <a name="when-to-use-wql"></a>使用 WQL 的時機

使用 WMI 時（尤其是 WQL），請別忘了您也會使用 Windows PowerShell。 通常，如果 WQL 查詢未如預期般運作，則使用標準 Windows PowerShell 命令比偵測 WQL 查詢更容易。

除非您是從跨頻寬限制的遠端系統傳回大量資料，否則當有完全可接受的 Windows Cmdlet 來執行相同的工作時，很少需要花費數小時的時間來完成複雜且複雜的 WQL 查詢（如果有點緩慢）。

## <a name="using-the-select-statement"></a>使用 SELECT 語句

一般的 WMI 查詢是以 Select 語句開頭，該語句會取得 WMI 類別的所有屬性或特定屬性。 若要選取 WMI 類別的所有屬性，請使用星號 (\*) 。 From 關鍵字會指定 WMI 類別。

Select 語句的格式如下：

```
Select <property> from <WMI-class>
```

例如，下列 Select 語句會從 Win32_Bios WMI 類別的實例中選取所有屬性 ( * ) 。

```
Select * from Win32_Bios
```

若要選取 WMI 類別的特定屬性，請將屬性名稱放在 Select 和 From 關鍵字之間。

下列查詢只會從 Win32_Bios WMI 類別選取 BIOS 的名稱。 命令會將查詢儲存在 $queryName 變數中。

```
Select Name from Win32_Bios
```

若要選取一個以上的屬性，請使用逗號來分隔屬性名稱。
下列 WMI 查詢會選取 Win32_Bios WMI 類別的名稱和版本。 命令會將查詢儲存在 $queryNameVersion 變數中。

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a>使用 WQL 查詢

在 Windows PowerShell 命令中使用 WQL 查詢有三種方式。

- 使用 Get-WmiObject Cmdlet
- 使用 Get-CimInstance Cmdlet
- 使用 [wmisearcher] 類型加速器。

## <a name="using-the-get-wmiobject-cmdlet"></a>使用 >GET-WMIOBJECT 指令 CMDLET

使用 WQL 查詢的最基本方式，就是將它括在引號 (作為字串) ，然後使用查詢字串做為 Get-WmiObject Cmdlet 的查詢參數值，如下列範例所示。

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

您也可以將 WQL 語句儲存在變數中，然後使用該變數做為查詢參數的值，如下列命令所示。

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

您可以使用任一種格式搭配任何 WQL 語句。 下列命令會使用 $queryName 變數中的查詢，只取得系統 BIOS 的名稱和版本屬性。

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

請記住，您可以使用 Get-WmiObject Cmdlet 的參數來取得相同的結果。 例如，下列命令也會取得 Win32_Bios WMI 類別之實例的 Name 和 Version 屬性值。

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a>使用 CIMINSTANCE 指令 CMDLET

從 Windows PowerShell 3.0 開始，您可以使用 Get-CimInstance Cmdlet 來執行 WQL 查詢。

Get-CimInstance 取得 CIM 相容類別的實例，包括 WMI 類別。 Windows PowerShell 3.0 引進的 CIM Cmdlet 會執行與 WMI Cmdlet 相同的工作。 CIM Cmdlet 符合 WS-Management (WSMan) 標準以及通用訊息模型 (CIM) 標準，可讓 Cmdlet 使用相同的技術來管理執行其他作業系統的 Windows 電腦和電腦。

下列命令使用 Get-CimInstance Cmdlet 來執行 WQL 查詢。

任何可以搭配 Get-WmiObject 使用的 WQL 查詢，也可以搭配 CimInstance 使用。

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Get-CimInstance 會傳回 CimInstance 物件，而不是 Get-WmiObject 傳回的 System.management.managementobject，但物件相當類似。

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a>使用 [wmisearcher] 類型加速器

[Wmisearcher] 類型加速器會從 WQL 語句字串建立 ManagementObjectSearcher 物件。 ManagementObjectSearcher 物件有許多屬性和方法，但是最基本的方法是 Get 方法，它會叫用指定的 WMI 查詢並傳回產生的物件。

藉由使用 [wmisearcher]，您可以輕鬆地存取 ManagementObjectSearcher .NET Framework 類別。 這可讓您查詢 WMI 並設定查詢的執行方式。

若要使用 [wmisearcher] 類型加速器：

1. 將 WQL 字串轉換成 ManagementObjectSearcher 物件。
2. 呼叫 ManagementObjectSearcher 物件的 Get 方法。

例如，下列命令會轉換「全選」查詢、將結果儲存在 $bios 變數中，然後在 $bios 變數中呼叫 ManagementObjectSearcher 物件的 Get 方法。

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

注意：預設只會顯示選取的物件屬性。 這些屬性是在 Types.ps1xml 檔案中定義。

您可以使用 [wmisearcher] 類型加速器來轉換查詢或變數。 在下列範例中，會使用 [wmisearcher] 類型加速器來轉換變數。 結果會相同。

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

當您使用 [wmisearcher] 類型加速器時，它會將查詢字串變更為 ManagementObjectSearcher 物件，如下列命令所示。

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

此命令格式適用于任何查詢。 下列命令會取得 Win32_Bios WMI 類別之 Name 屬性的值。

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

您可以使用單一命令來執行這項作業，雖然命令有點難以解讀。

使用這種格式時，您可以使用 [wmisearcher] 類型加速器將 WQL 查詢字串轉換成 ManagementObjectSearcher，然後在該物件上呼叫 Get 方法，全都在單一命令中。 括弧 ( # A1，用來括住轉換字串直接 Windows PowerShell，以在呼叫方法之前轉換字串。

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a>使用基本 WQL WHERE 語句

Where 語句會針對 Select 語句所傳回的資料，建立條件。

Where 語句的格式如下：

```
where <property> <operator> <value>
```

例如：

```
where Name = 'Notepad.exe'
```

Where 語句會搭配 Select 語句使用，如下列範例所示。

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

使用 Where 語句時，屬性名稱和值必須是正確的。

例如，下列命令會取得本機電腦上的「記事本」處理常式。

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

但是，下列命令會失敗，因為進程名稱包含 ".exe" 副檔名。

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a>WHERE 語句比較運算子

下列運算子在 WQL Where 語句中是有效的。

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

還有其他運算子，但這些運算子是用來進行比較的運算子。

例如，下列查詢會從進程優先權大於或等於11的 Win32_Process 類別中的處理常式，選取名稱和優先權屬性。 Get-WmiObject Cmdlet 會執行查詢。

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a>在篩選參數中使用 WQL 運算子

WQL 運算子也可以用在 Get-WmiObject 或 Get-CimInstance Cmdlet 的 Filter 參數值中，也可以在這些 Cmdlet 的查詢參數值中使用。

例如，下列命令會取得最後五個進程的名稱和 ProcessID 屬性，其 ProcessID 值大於1004。 此命令會使用 Filter 參數來指定 ProcessID 條件。

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a>使用 LIKE 運算子

Like 運算子可讓您使用萬用字元來篩選 WQL 查詢的結果。

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

使用 Like 運算子時，如果沒有任何萬用字元或範圍運算子，其行為就像是相等運算子 (=) ，而且只有在與模式完全相符時，才會傳回物件。

您可以將範圍作業與百分比萬用字元結合，以建立簡單但功能強大的篩選準則。

### <a name="like-operator-examples"></a>LIKE 運算子範例

#### <a name="example-1-range"></a>範例1： [ \<range> ]

下列命令會啟動 [記事本]，然後搜尋 Win32_Process 類別的實例，該實例的名稱開頭為 "H" 和 "N" (不區分大小寫) 。

此查詢應該會透過 Notepad.exe 從 Hotpad.exe 傳回任何處理程式。

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a>範例2： [ \<range> ] 和%

下列命令會選取名稱以 A 和 P 之間的字母為開頭的所有進程 (不區分大小寫) ，後面接著零或多個字母的任何組合。

Get-WmiObject Cmdlet 會執行查詢，Select-Object Cmdlet 會取得 Name 和 ProcessID 屬性，而 Sort-Object Cmdlet 會依名稱以字母順序排序結果。

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a>範例3：不在範圍 (^) 

下列命令會取得名稱不是以下列任何字母開頭的進程： A、S、W、P、R、C、U、N

並遵循零或多個字母。

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a>範例4：任何字元--或無 (% ) 

下列命令會取得名稱開頭為 "calc" 的處理常式。
WQL 中的% 符號相當於 \* 正則運算式中的星號 () 符號。

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a>範例5：一個字元 (_) 

下列命令會取得名稱具有下列模式的進程： "c_lc.exe"，其中底線字元代表任何一個字元。 此模式會透過 czlc.exe 或 c9lc.exe 來比對 calc.exe 中的任何名稱，但不會比對 "c" 和 "l" 以超過一個字元分隔的名稱。

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a>範例6：完全相符

下列命令會取得名為 WLIDSVC.exe 的進程。 即使查詢使用 Like 關鍵字，它還是需要完全相符，因為該值不包含任何萬用字元。

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a>使用 OR 運算子

若要指定多個獨立的條件，請使用或關鍵字。 Where 子句中會出現或關鍵字。 它會在兩個 (或更多) 條件上執行內含 OR 運算，並傳回符合任何條件的專案。

Or 運算子的格式如下：

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

例如，下列命令會取得 Win32_Process WMI 類別的所有實例，但只有在處理常式名稱是 winword.exe 或 excel.exe 時才會傳回它們。

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

或語句可以搭配兩個以上的條件使用。 在下列查詢中，或語句會取得 Winword.exe、Excel.exe 或 Powershell.exe。

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a>使用 AND 運算子

若要指定多個相關條件，請使用和關鍵字。 And 關鍵字會出現在 Where 子句中。 它會傳回符合所有條件的專案。

And 運算子的格式如下：

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

例如，下列命令會取得名稱為 "Winword.exe" 且處理序識別碼為6512的進程。

請注意，命令使用 Get-CimInstance Cmdlet。

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

所有運算子（包括 Like 運算子）都適用于 Or 和 And 運算子。 而且，您可以將 Or 和 And 運算子結合在單一查詢中，並以括弧括住 Windows PowerShell 要先處理的子句。

此命令會使用 Windows PowerShell 接續字元 (') 將命令分為兩行。

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a>搜尋 Null 值

在 WMI 中搜尋 null 值是一項挑戰，因為這可能會導致無法預期的結果。 Null 不是零，且不等於或為空字串。 某些 WMI 類別屬性已初始化，其他則不是，因此搜尋 null 對所有屬性都可能無法運作。

若要搜尋 null 值，請使用的是值為 "null" 的是運算子。

例如，下列命令會取得 IntallDate 屬性有 null 值的處理常式。 這些命令會傳回許多進程。

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

相反地，下列命令會取得具有 Description 屬性之 null 值的使用者帳戶。 此命令不會傳回任何使用者帳戶，即使大部分的使用者帳戶沒有 Description 屬性的任何值也一樣。

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

若要尋找沒有 Description 屬性值的使用者帳戶，請使用等號比較運算子來取得空字串。 若要表示空字串，請使用兩個連續的單引號。

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a>使用 TRUE 或 FALSE

若要在 WMI 物件的屬性中取得布林值，請使用 True 和 False。
它們不區分大小寫。

下列 WQL 查詢只會傳回已加入網域之電腦上的本機使用者帳戶。

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

若要尋找網域帳戶，請使用值 False，如下列範例所示。

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a>使用 ESCAPE 字元

WQL 使用反斜線 (\) 作為其 escape 字元。 這不同于 Windows PowerShell，其使用倒引號字元 (') 。

引號和用於引號的字元通常需要換成，如此就不會被誤解。

若要尋找名稱包含單引號的使用者，請使用反斜線來 escape 單引號，如下列命令所示。

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

在某些情況下，反斜線也需要進行轉義。 例如，下列命令會產生不正確查詢錯誤，因為標題值中有反斜線。

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

若要對反斜線進行 escape，請使用第二個反斜線字元，如下列命令所示。

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a>另請參閱

[about_Special_Characters](about_Special_Characters.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_WMI](about_WMI.md)

[about_WMI_Cmdlets](about_WMI_Cmdlets.md)
