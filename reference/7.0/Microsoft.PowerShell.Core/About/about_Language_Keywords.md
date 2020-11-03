---
description: 描述 PowerShell 指令碼語言中的關鍵字。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_keywords?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Keywords
ms.openlocfilehash: 09b0414a962cce3f9f5c90b28aa871f4c09f76e2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207399"
---
# <a name="about-language-keywords"></a>關於語言關鍵字

## <a name="short-description"></a>簡短描述
描述 PowerShell 指令碼語言中的關鍵字。

## <a name="long-description"></a>詳細描述

PowerShell 有下列語言關鍵字。 如需詳細資訊，請參閱關鍵字的「關於」主題和資料表後面的資訊。

關鍵字     | 參考
---         | ---
開始       | [about_Functions](about_Functions.md)， [about_Functions_Advanced](about_Functions_Advanced.md)
中斷       | [about_Break](about_Break.md)， [about_Trap](about_Trap.md)
Catch       | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
類別       | [about_Classes](about_Classes.md)
繼續    | [about_Continue](about_Continue.md)， [about_Trap](about_Trap.md)
資料        | [about_Data_Sections](about_Data_Sections.md)
定義      | 保留供日後使用
可行事項          | [about_Do](about_Do.md)， [about_While](about_While.md)
DynamicParam| [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)
Else        | [about_If](about_If.md)
Elseif      | [about_If](about_If.md)
結束         | [about_Functions](about_Functions.md)， [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
列舉        | [about_Enum](about_Enum.md)
結束        | [本主題所述](#exit)
Filter      | [about_Functions](about_Functions.md)
最後     | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
For         | [about_For](about_For.md)
ForEach     | [about_ForEach](about_ForEach.md)
從        | 保留供日後使用
函式    | [about_Functions](about_Functions.md)， [about_Functions_Advanced](about_Functions_Advanced.md)
Hidden      | [about_Hidden](about_Hidden.md)
如果          | [about_If](about_If.md)
位於          | [about_ForEach](about_ForEach.md)
Param       | [about_Functions](about_Functions.md)
程序     | [about_Functions](about_Functions.md)， [about_Functions_Advanced](about_Functions_Advanced.md)
傳回      | [about_Return](about_Return.md)
靜態      | [about_Classes](about_Classes.md)
參數      | [about_Switch](about_Switch.md)
Throw       | [about_Throw](about_Throw.md)， [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
陷阱        | [about_Trap](about_Trap.md)、 [about_Break](about_Break.md) [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
嘗試         | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
直到       | [about_Do](about_Do.md)
使用       | [about_Using](about_Using.md)， [about_Classes](about_Classes.md)
Var         | 保留供日後使用
While       | [about_While](about_While.md)， [about_Do](about_Do.md)

語言關鍵字

### <a name="begin"></a>開始

指定函數主體的一個部分，以及 `DynamicParam` 、 `Process` 和 `End` 關鍵字。 `Begin`語句清單會在從管線接收任何物件之前執行一次。

語法：

```Syntax
function <name> {
    DynamicParam {<statement list>}
    begin {<statement list>}
    process {<statement list>}
    end {<statement list>}
}
```

### <a name="break"></a>中斷

導致腳本結束迴圈。

語法：

```Syntax
while (<condition>) {
   <statements>
   ...

   break
   ...

   <statements>
}
```

### <a name="catch"></a>Catch

如果伴隨的 Try 語句清單中發生錯誤，則指定要執行的語句清單。 錯誤類型需要括弧。 第二組括弧表示錯誤類型是選擇性的。

語法：

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
```

### <a name="class"></a>類別

在 PowerShell 中指定新的類別。

語法：

```Syntax
class <class-name> {
    [[hidden] [static] <property-definition> ...]
    [<class-name>([argument-list>]) {<constructor-statement-list>} ...]
    [[hidden] [static] <method-definition> ...]
}
```

### <a name="continue"></a>繼續

導致腳本停止執行迴圈，並返回條件。 如果符合條件，腳本會再次開始迴圈。

語法：

```Syntax
while (<condition>) {
   <statements>
   ...

   continue
   ...

   <statements>
}
```

### <a name="data"></a>資料

在腳本中，定義一個區段，以隔離腳本邏輯中的資料。 也可以包含 `If` 語句和某些有限的命令。

語法：

```Syntax
data <variable> [-supportedCommand <cmdlet-name>] {<permitted content>}
```

### <a name="do"></a>可行事項

搭配 `While` 或關鍵字使用 `Until` 做為迴圈結構。 PowerShell 會執行至少一次語句清單，而不像使用的迴圈 `While` 。

`While` 的語法：

```Syntax
do {<statement list>} while (<condition>)
```

`Until` 的語法：

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="dynamicparam"></a>DynamicParam

指定函數主體的一個部分，以及 `Begin` 、 `Process` 和 `End` 關鍵字。 動態參數會在執行時間加入。

語法：

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="else"></a>Else

與關鍵字一起使用 `If` ，以指定預設的語句清單。

語法：

```Syntax
if (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="elseif"></a>Elseif

搭配 `If` 和關鍵字使用， `Else` 以指定其他條件。 `Else`關鍵字是選擇性的。

語法：

```Syntax
if (<condition>) {<statement list>}
elseif (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="end"></a>結束

指定函數主體的一個部分，以及 `DynamicParam` 、 `Begin` 和 `End` 關鍵字。 `End`語句清單會在從管線收到所有物件之後執行一次。

語法：

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="enum"></a>列舉

`enum` 用來宣告列舉;由一組稱為列舉值清單的命名標籤所組成的相異型別。

語法：

```Syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

### <a name="exit"></a>結束

使 PowerShell 結束腳本或 PowerShell 實例。

語法：

```Syntax
exit
exit <exitcode>
```

當您使用 `pwsh` 與 **File** 參數時， `.ps1` (腳本) 檔案本身應該包含處理腳本執行時所發生之任何錯誤或例外狀況的指示。 您應該只使用 `exit` 語句來指出腳本的執行後狀態。

在 Windows 上，允許和之間的任何數位 `[int]::MinValue` `[int]::MaxValue` 。

在 Unix 上，只 `[byte]::MinValue` 允許和之間 `[byte]::MaxValue` 的正負號。 範圍中的負數位會藉 `-1` `-255` 由新增256自動轉譯為正數。 例如， `-2` 會轉換成 `254` 。

在 PowerShell 中， `exit` 語句會設定變數的值 `$LASTEXITCODE` 。 在 Windows 命令 Shell ( # A0) 中，exit 語句會設定環境變數的值 `%ERRORLEVEL%` 。

任何非數位或外部平臺特定範圍的引數，都會轉譯為的值 `0` 。

在下列範例中，使用者將錯誤層級變數值新增至腳本檔，以將其設定為 4 `exit 4` `test.ps1` 。

```cmd
C:\scripts\test>type test.ps1
1
2
3
exit 4

C:\scripts\test>pwsh -file ./test.ps1
1
2
3

C:\scripts\test>echo %ERRORLEVEL%
4
```

當您執行 `pwsh.exe -File <path to a script>` 並使用命令終止腳本檔案時 `exit` ，結束代碼會設定為與命令搭配使用的數值引數 `exit` 。 如果腳本沒有 `exit` 語句，則 `0` 當腳本完成而沒有發生錯誤或 `1` 腳本從未處理的例外狀況結束時，一律會結束程式碼。

### <a name="filter"></a>Filter

針對每個輸入物件，指定語句清單執行一次的函數。 它與只包含進程區塊的函式具有相同的效果。

語法：

```Syntax
filter <name> {<statement list>}
```

### <a name="finally"></a>最後

定義在與 Try 和 Catch 相關聯的語句之後執行的語句清單。 `Finally`即使您按下 `CTRL+C` 以離開腳本，或在腳本中使用 Exit 關鍵字，還是會執行語句清單。

語法：

```Syntax
try {<statement list>}
catch [<error type>] {<statement list>}
finally {<statement list>}
```

### <a name="for"></a>For

使用條件定義迴圈。

語法：

```Syntax
for (<initialize>; <condition>; <iterate>) { <statement list> }
```

### <a name="foreach"></a>ForEach

使用集合的每個成員定義迴圈。

語法：

```Syntax
ForEach (<item> in <collection>) { <statement list> }
```

### <a name="from"></a>從

保留供未來使用。

### <a name="function"></a>函式

建立可重複使用程式碼的命名語句清單。 您可以命名函式所屬的範圍。 而且，您可以使用關鍵字來指定一個或多個具名引數 `Param` 。 在函數語句清單中，您可以包含 `DynamicParam` 、 `Begin` 、 `Process` 和 `End` 語句清單。

語法：

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1> [, [type]<$pname2>])
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

您也可以選擇在函式名稱之後，于語句清單外定義一個或多個參數。

語法：

```Syntax
function [<scope:>]<name> [([type]<$pname1>, [[type]<$pname2>])] {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="if"></a>如果

定義條件式。

語法：

```Syntax
if (<condition>) {<statement list>}
```

### <a name="hidden"></a>Hidden

從 Cmdlet 的預設結果 `Get-Member` ，以及從 IntelliSense 和 tab 鍵自動完成結果隱藏類別成員。

語法：

```Syntax
Hidden [data type] $member_name
```

### <a name="in"></a>位於

在語句中用 `ForEach` 來建立使用集合之每個成員的迴圈。

語法：

```Syntax
ForEach (<item> in <collection>){<statement list>}
```

### <a name="inlinescript"></a>InlineScript

在共用的 PowerShell 會話中執行工作流程命令。 此關鍵字只在 PowerShell 工作流程中有效。

語法：

```Syntax
workflow <verb>-<noun>
{
   InlineScript
   {
      <Command/Expression>
      ...

   }
}
```

`InlineScript`關鍵字表示 `InlineScript` 活動，此活動會在共用標準 (非工作流程) 會話中執行命令。 您可以使用 `InlineScript` 關鍵字來執行在工作流程中不正確命令，以及執行共用資料的命令。 根據預設，InlineScript 腳本區塊中的命令會在不同的進程中執行。

如需詳細資訊，請參閱 [在工作流程中執行 PowerShell 命令](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574197(v=ws.11))。

### <a name="param"></a>Param

定義函數中的參數。

語法：

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1>[, [[type]<$pname2>]])
   <statement list>
}
```

### <a name="process"></a>程序

指定函數主體的一部分，以及 `DynamicParam` 、 `Begin` 和 `End` 關鍵字。 當 `Process` 語句清單接收來自管線的輸入時， `Process` 語句清單會針對管線中的每個元素執行一次。 如果管線未提供任何物件，則 `Process` 不會執行語句清單。 如果命令是管線中的第一個命令，則 `Process` 語句清單會執行一次。

語法：

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="return"></a>傳回

使 PowerShell 離開目前的範圍（例如腳本或函式），並將選擇性的運算式寫入輸出。

語法：

```Syntax
return [<expression>]
```

### <a name="static"></a>靜態

指定定義之類別的所有實例都通用的屬性或方法。

如需使用範例，請參閱 `Class` 。

### <a name="switch"></a>參數

若要檢查多個條件，請使用 `Switch` 語句。 `Switch`語句相當於一連串的 `If` 語句，但比較簡單。

此 `Switch` 語句會列出每個條件和一個選擇性的動作。 如果條件獲得，則會執行動作。

語法 1：

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] ( <value> )
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

語法 2：

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] -file <filename>
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

### <a name="throw"></a>Throw

將物件擲回為錯誤。

語法：

```Syntax
throw [<object>]
```

### <a name="trap"></a>陷阱

定義在遇到錯誤時要執行的語句清單。 錯誤類型需要括弧。 第二組括弧表示錯誤類型是選擇性的。

語法：

```Syntax
trap [[<error type>]] {<statement list>}
```

### <a name="try"></a>嘗試

定義語句執行時，要檢查是否有錯誤的語句清單。 如果發生錯誤，PowerShell 會在或語句中繼續執行 `Catch` `Finally` 。 錯誤類型需要括弧。 第二組括弧表示錯誤類型是選擇性的。

語法：

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
finally {<statement list>}
```

### <a name="until"></a>直到

用在 `Do` 語句中做為迴圈結構，其中語句清單至少會執行一次。

語法：

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="using"></a>使用

允許表示會話中使用的命名空間。 類別和成員需要較少的輸入才能加以提及。 您也可以包含模組中的類別。

語法 #1：

```Syntax
using namespace <.Net-framework-namespace>
```

語法 #2：

```Syntax
using module <module-name>
```

### <a name="while"></a>While

`while`語句是迴圈結構，其中的條件會在執行語句之前進行測試。 如果條件為 FALSE，則不會執行語句。

語句語法：

```Syntax
while (<condition>) {
   <statements>
 }
```

在語句中使用時 `Do` ， `while` 是迴圈結構的一部分，其中語句清單至少會執行一次。

Do 迴圈語法：

```Syntax
do {<statement list>} while (<condition>)
```

## <a name="see-also"></a>另請參閱

- [about_Special_Characters](about_Special_Characters.md)
- [about_Wildcards](about_Wildcards.md)
