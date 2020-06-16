---
title: 格式、別名、提供者、比較
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: eb23b048a50f10ea83d156c0499772b1be439336
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437999"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a>第 5 章 - 格式、別名、提供者、比較

## <a name="requirements"></a>需求

本章所示的部分範例需要 SQL Server PowerShell 模組。 模組會安裝為 [SQL Server Management Studio (SMSS)][SMSS] 的一部分。 後續章節也會用到它。 將它下載並安裝在您的 Windows 10 實驗室環境電腦上。

## <a name="format-right"></a>右側格式化

在第 4 章中，您已了解如何盡可能地篩選左側。 手動格式化命令輸出的規則類似於該規則，但它必須盡可能地出現在最右邊。

最常見的格式化命令是 `Format-Table` 和 `Format-List`。 也可以使用 `Format-Wide` 和 `Format-Custom`，但較不常見。

如第 3 章中所述，除非使用自訂格式，否則傳回四個以上屬性的命令會預設為清單。

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

使用 `Format-Table` Cmdlet 來手動覆寫格式，並將輸出以資料表顯示，而不是清單。

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

`Get-Service` 的預設輸出是資料表中的三個屬性。

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

使用 `Format-List` Cmdlet 來覆寫預設格式，並以清單傳回結果。

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

請注意，只要將 `Get-Service` 以管線傳送至 `Format-List` 就可讓它傳回其他屬性。 由於在幕後對該特定命令的格式設定方式，並非每個命令都可執行此動作。

使用格式化 Cmdlet 必須注意的第一件事便是，它們會產生與 PowerShell 中一般物件不同的格式化物件。

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

這表示格式化命令無法以管線傳送至大部分的其他命令。 它們可以透過管線傳送至一些 `Out-*` 命令，就這些。 這就是為什麼您想要在行尾執行任何格式設定 (格式化右側)。

## <a name="aliases"></a>別名

PowerShell 中的別名是命令的較短名稱。 PowerShell 包含一組內建的別名，您也可以定義自己的別名。

`Get-Alias` Cmdlet 可用來尋找別名。 如果您已知道命令的別名，則會使用 **Name** 參數來判斷別名所關聯的命令。

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

可以為 **Name** 參數的值指定多個別名。

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

您通常會看到 **Name** 參數已省略，因為它是位置參數。

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

如果您想要尋找命令的別名，則必須使用 **Definition** 參數。

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

**Definition** 參數無法依位置使用，因此必須指定它。

別名可以讓您省去一些按鍵輸入的時間，而且當您將命令輸入主控台時，其可正常運作。
它們不應該用於指令碼或您要儲存或與其他人共用的任何程式碼中。 如本書稍早所述，使用完整的 Cmdlet 和參數名稱是自我說明且易於了解的。

建立自己的別名時請務必小心，因為它們只會存在於您電腦上目前的 PowerShell 工作階段中。

## <a name="providers"></a>提供者

PowerShell 中的提供者是介面，會允許對資料存放區執行類似檔案系統的存取。 PowerShell 中有許多內建提供者。

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

如您在先前的結果中所見，有一些用於登錄、別名、環境變數、檔案系統、函式、變數、憑證和 WSMan 的內建提供者。

這些提供者用來公開其資料存放區的實際磁碟機，可以使用 `Get-PSDrive` Cmdlet 來判斷。 `Get-PSDrive` Cmdlet 不只會顯示提供者所公開的磁碟機，還會顯示 Windows 邏輯磁碟機，包括與網路共用對應的磁碟機。

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

協力廠商模組 (例如 Active Directory PowerShell 模組和 SQLServer PowerShell 模組) 都會新增自己的 PowerShell 提供者和 PSDrive。

匯入 Active Directory 和 SQL Server PowerShell 模組。

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

檢查以了解是否已新增任何其他 PowerShell 提供者。

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

請注意，在先前的結果集中，現在存在兩個新的 PowerShell 提供者，一個用於 Active Directory，另一個則用於 SQL Server。

也針對每個模組新增了一個 PSDrive。

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

您可以如傳統檔案系統般存取 PSDrive。

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a>比較運算子

PowerShell 包含一些比較運算子，用來比較值或尋找符合特定模式的值。 資料表 5-1 包含 PowerShell 中比較運算子的清單。

|    運算子    |                          定義                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | 等於                                                     |
| `-ne`          | 不等於                                                 |
| `-gt`          | 大於                                                 |
| `-ge`          | 大於或等於                                     |
| `-lt`          | 小於                                                    |
| `-le`          | 小於或等於                                        |
| `-Like`        | 使用 `*` 萬用字元比對                       |
| `-NotLike`     | 不符合使用 `*` 萬用字元              |
| `-Match`       | 比對指定的規則運算式                     |
| `-NotMatch`    | 不符合指定的規則運算式              |
| `-Contains`    | 判斷集合是否包含指定的值        |
| `-NotContains` | 判斷集合是否不包含特定值 |
| `-In`          | 判斷指定的值是否在集合中           |
| `-NotIn`       | 判斷指定的值是否不在集合中       |
| `-Replace`     | 取代指定的值                                 |

資料表 5-1 中列出的所有運算子都不區分大小寫。 將 `c` 放在資料表 5-1 所列的運算子前面，可使其區分大小寫。 例如，`-ceq` 是 `-eq` 比較運算子的區分大小寫版本。

使用等於比較運算子時，適當大小寫 "PowerShell" 會等於小寫 "powershell"。

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

它不等於使用等於比較運算子的區分大小寫版本。

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

不等於比較運算子會反轉條件。

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

大於、大於或等於、小於，以及小於或等於均可對字串或數值使用。

```powershell
5 -gt 5
```

```Output
False
```

對上一個範例使用大於或等於，而不是大於，會傳回 **布林值** true，因為五等於五。

```powershell
5 -ge 5
```

```Output
True
```

根據前兩個範例的結果，您也許能猜測小於和小於或等於的運作方式。

```powershell
5 -lt 10
```

```Output
True
```

即使是有經驗的 PowerShell 使用者，`-Like` 和 `-Match` 運算子也可能令人混淆。 `-Like` 會與萬用字元 `*` 和 `?` 搭配使用，以執行 "like" 比對。

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

`-Match` 使用規則運算式來執行比對。

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

使用範圍運算子，將數字 1 到 10 儲存在變數中。

```powershell
$Numbers = 1..10
```

```Output
```

判斷 `$Numbers` 變數是否包含 15。

```powershell
$Numbers -contains 15
```

```Output
False
```

判斷它是否包含數字 10。

```powershell
$Numbers -contains 10
```

```Output
True
```

`-NotContains` 會反轉邏輯，以查看 `$Numbers` 變數是否不包含值。

```powershell
$Numbers -notcontains 15
```

```Output
True
```

上一個範例會傳回 **布林值** true，因為 `$Numbers` 變數不會包含 15。 不過，它確定包含數字 10，因此在測試時為 false。

```powershell
$Numbers -notcontains 10
```

```Output
False
```

"in" 比較運算子最初是在 PowerShell 3.0 版中推出。 它是用來判斷值是否「在」陣列中。 `$Numbers` 變數是陣列，因為它包含多個值。

```powershell
15 -in $Numbers
```

```Output
False
```

換句話說，`-in` 會執行與包含比較運算子相同的測試，但方向相反。

```powershell
10 -in $Numbers
```

```Output
True
```

15 不在 `$Numbers` 陣列中，因此在下列範例中會傳回 false。

```powershell
15 -in $Numbers
```

```Output
False
```

就像 `-contains` 運算子一樣，`not` 會反轉 `-in` 運算子的邏輯。

```powershell
10 -notin $Numbers
```

```Output
False
```

上一個範例會傳回 false，因為 `$Numbers` 陣列確實包含 10，而測試條件是要判斷它是否未包含 10。

15「不在」`$Numbers` 陣列中，因此會傳回 **布林值** true。

```powershell
15 -notin $Numbers
```

```Output
True
```

`-replace` 運算子只會執行您想要的動作。 其用來取代某個項目。 指定一個值時，將該值取代為空值。 在下列範例中，我將 "Shell" 取代為空值。

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

如果您想要將某個值取代為不同的值，請在您想要取代的模式之後指定該新值。 巴頓魯治的 SQL 星期六是我每年都會試著談到的事件。 在下列範例中，我將 "Saturday" 這個字取代為縮寫 "Sat"。

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

還有一些 **Replace ()**  之類的方法，可用來取代項目，類似取代運算子的運作方式。 不過，`-Replace` 運算子預設為不區分大小寫，而 **Replace ()**  方法則區分大小寫。

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

請注意，在上一個範例中，並未取代 "Saturday" 這個字。 這是因為指定了與原始不同的大小寫。 以與原始相同的大小寫指定 "Saturday" 這個字時，**Replace ()** 方法會如預期般加以取代。

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

使用方法來轉換資料時請小心，因為您可能會遇到未預期的問題，例如使得_土耳其測試_失敗。 如需範例，請參閱標題為[使用 Pester 測試 PowerShell 程式碼與其他文化特性][]的部落格文章。 我的建議是盡可能使用運算子，而不是方法來避免這些類型的問題。

雖然可以如先前範例所示使用比較運算子，但我通常會發現自己是使用 `Where-Object` Cmdlet 來執行某種類型的篩選。

## <a name="summary"></a>摘要

在本章中，您已了解一些不同的主題來包含右側格式化、別名、提供者和比較運算子。

## <a name="review"></a>檢閱

1. 為什麼有必要盡可能執行右側格式化？
1. 如何判斷用於 `%` 別名的實際 Cmdlet 為何？
1. 為什麼不應該在您儲存的指令碼或與其他人共用的程式碼中使用別名？
1. 在與其中一個登錄提供者相關聯的磁碟機上執行目錄列出。
1. 使用取代運算子而非 replace 方法的其中一個主要優點是什麼？

## <a name="recommended-reading"></a>建議閱讀資料

- [Format-Table][]
- [Format-List][]
- [Format-Wide][]
- [about_Aliases][]
- [about_Providers][]
- [about_Comparison_Operators][]
- [about_Arrays][]

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[使用 Pester 測試 PowerShell 程式碼與其他文化特性]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
