---
description: 定義腳本區塊是什麼，並說明如何使用 PowerShell 程式設計語言的腳本區塊。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: dc3ee050399e92506cabed370e95d03c65652953
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206887"
---
# <a name="about-script-blocks"></a>關於腳本區塊

## <a name="short-description"></a>簡短描述

定義腳本區塊是什麼，並說明如何使用 PowerShell 程式設計語言的腳本區塊。

## <a name="long-description"></a>完整描述

在 PowerShell 程式設計語言中，腳本區塊是可當做單一單位使用的語句或運算式集合。
指令碼區塊可以接受引數和傳回值。

在語法上，腳本區塊是以大括弧括住的語句清單，如下列語法所示：

```
{<statement list>}
```

腳本區塊會傳回腳本區塊中所有命令的輸出，可以是單一物件或陣列。

您也可以使用關鍵字來指定傳回值 `return` 。 `return`關鍵字不會影響或隱藏從腳本區塊傳回的其他輸出。 不過， `return` 關鍵字會結束該行的腳本區塊。 如需詳細資訊，請參閱 [about_Return](about_Return.md)。

就像函式一樣，腳本區塊也可以包含參數。 使用 Param 關鍵字指派具名引數，如下列語法所示：

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> 在腳本區塊中，與函式不同的是，您不能在大括弧之外指定參數。

如同函式，腳本區塊可以包含 `DynamicParam` 、 `Begin` 、 `Process` 和 `End` 關鍵字。 如需詳細資訊，請參閱 [about_Functions](about_Functions.md) 和 [about_Functions_Advanced](about_Functions_Advanced.md)。

## <a name="using-script-blocks"></a>使用腳本區塊

腳本區塊是 Microsoft .NET Framework 類型的實例 `System.Management.Automation.ScriptBlock` 。 命令可以有腳本區塊參數值。 例如， `Invoke-Command` Cmdlet 具有 `ScriptBlock` 接受腳本區塊值的參數，如下列範例所示：

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

`Invoke-Command` 也可以執行具有參數區塊的腳本區塊。
參數是透過使用 **ArgumentList** 參數的位置來指派。

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

上述範例中的腳本區塊會使用 `param` 關鍵字來建立參數 `$p1` 和 `$p2` 。 字串 "First" 系結至第一個參數 (`$p1`) ，而 "Second" 系結至 (`$p2`) 。

如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about_Splatting.md#splatting-with-arrays)。

您可以使用變數來儲存和執行腳本區塊。 下列範例會將腳本區塊儲存在變數中，並將其傳遞至 `Invoke-Command` 。

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

呼叫運算子是另一種方式，可執行儲存在變數中的腳本區塊。
如同 `Invoke-Command` ，呼叫運算子會在子範圍中執行腳本區塊。 呼叫運算子可讓您更輕鬆地使用參數搭配您的腳本區塊。

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

您可以使用指派，將腳本區塊的輸出儲存在變數中。

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

如需呼叫運算子的詳細資訊，請參閱 [about_Operators](about_Operators.md)。

## <a name="using-delay-bind-script-blocks-with-parameters"></a>使用具有參數的延遲系結腳本區塊

接受管線輸入 (`by Value`) 或 (`by PropertyName`) 可在參數上使用 **延遲** 系結腳本區塊的型別參數。
在 **延遲** 系結腳本區塊內，您可以使用管線變數參考物件中的管道 `$_` 。

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

在更複雜的 Cmdlet 中，延遲系結腳本區塊可讓您重複使用物件中的一個管道來填入其他參數。

**延遲** 將腳本區塊系結為參數的注意事項：

- 您必須明確指定搭配 **延遲** 系結腳本區塊使用的任何參數名稱。
- 參數不可以是不具類型的，且參數的類型不得為 `[scriptblock]` 或 `[object]` 。
- 如果您在不提供管線輸入的情況下使用 **延遲** 系結腳本區塊，就會收到錯誤。

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a>另請參閱

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Operators](about_Operators.md)
