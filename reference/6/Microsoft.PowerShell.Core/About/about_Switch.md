---
description: 說明如何使用參數來處理多個 `If` 語句。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 2b39f8e0ad49c9e5f6cab06eea34e8f27b37186b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206848"
---
# <a name="about-switch"></a>關於切換

## <a name="short-description"></a>簡短描述
說明如何使用參數來處理多個 `If` 語句。

## <a name="long-description"></a>完整描述

若要檢查腳本或函數中的條件，請使用 `If` 語句。 `If`語句可以檢查許多類型的條件，包括變數的值和物件的屬性。

若要檢查多個條件，請使用 `Switch` 語句。 `Switch`語句相當於一連串的 `If` 語句，但比較簡單。 此 `Switch` 語句會列出每個條件和一個選擇性的動作。 如果條件獲得，則會執行動作。

`Switch`語句可以使用 `$_` 和 `$switch` 自動變數。 如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。

基本 `Switch` 語句的格式如下：

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

例如，下列語句會將 `Switch` 測試值3與每個條件進行比較。 當測試值符合條件時，便會執行動作。

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

在這個簡單的範例中，會將值與清單中的每個條件進行比較，即使值3有相符的值也一樣。 下列 `Switch` 語句有兩個值3的條件。 它會示範根據預設，所有條件都會進行測試。

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

若要指示在比對 `Switch` 之後停止比較，請使用 `Break` 語句。 `Break`語句會終止 `Switch` 語句。

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

如果測試值為集合（例如陣列），則集合中的每個專案都會依照其出現的順序進行評估。 下列範例會評估4然後2。

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

任何 `Break` 語句都會套用至集合，而不是每個值，如下列範例所示。 語句 `Switch` 是由 `Break` 值4的條件中的語句所終止。

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a>Syntax

完整的 `Switch` 語句語法如下所示：

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

或

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

如果未使用任何參數，其行為會與 `Switch` 使用 **確切** 的參數相同。 它會對值執行不區分大小寫的比對。 如果值是集合，每個專案都會依其出現的順序進行評估。

`Switch`語句必須包含至少一個 condition 語句。

`Default`當值不符合任何條件時，就會觸發子句。 它相當於 `Else` 語句中的子句 `If` 。 `Default`每個語句中只允許一個子句 `Switch` 。

`Switch` 具有下列參數：

- **萬用字元** -表示條件是萬用字元字串。 如果 match 子句不是字串，則會忽略參數。 此比較不區分大小寫。
- **Exact** -指出 match 子句（如果它是字串）必須完全相符。 如果 match 子句不是字串，則會忽略這個參數。 此比較不區分大小寫。
- **CaseSensitive** -執行區分大小寫的比對。 如果 match 子句不是字串，則會忽略這個參數。
- **File** -接受來自檔案的輸入，而不是值語句。 如果包含 **多個** 檔案參數，則只會使用最後一個。 檔案的每一行都是由語句讀取和評估 `Switch` 。 此比較不區分大小寫。
- **Regex** -執行符合條件之值的正則運算式比對。 如果 match 子句不是字串，則會忽略這個參數。
  此比較不區分大小寫。 `$matches`自動變數可在相符的語句區塊內使用。

> [!NOTE]
> 指定衝突的值（例如 **Regex** 和 **萬用字元** ）時，會優先使用指定的最後一個參數，且會忽略所有衝突的參數。 也可以使用多個參數的實例。 不過，只有最後使用的參數才有效。

在此範例中，不是字串或數值資料的物件會傳遞至 `Switch` 。 會 `Switch` 在物件上執行字串強制型轉，並評估結果。

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

在此範例中，沒有任何相符的案例，因此沒有任何輸出。

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

藉由新增 `Default` 子句，您可以在沒有其他條件成功時執行動作。

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

若要讓 "十四" 這個字元合大小寫，您必須使用 `-Wildcard` 或 `-Regex` 參數。

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

下列範例會使用 `-Regex` 參數。

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

Switch 語句條件可以是：

- 其值與輸入值比較的運算式
- 如果符合條件，則應傳回的腳本區塊 `$true` 。

`$_`自動變數包含傳遞給 switch 語句的值，而且可以在條件陳述式的範圍內進行評估和使用。

每個條件的動作與其他條件中的動作無關。

下列範例示範如何使用腳本區塊做為 `Switch` 語句條件。

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

如果值符合多個條件，則會執行每個條件的動作。 若要變更此行為，請使用 `Break` 或 `Continue` 關鍵字。

`Break`關鍵字會停止處理並結束 `Switch` 語句。

`Continue`關鍵字會停止處理目前的值，但會繼續處理任何後續的值。

下列範例會處理數位的陣列，如果它們是奇數或偶數，則會顯示。 使用關鍵字略過負數 `Continue` 。 如果遇到非數位，則會以關鍵字結束執行 `Break` 。

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a>另請參閱

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)
