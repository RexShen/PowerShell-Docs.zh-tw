---
description: 列出無法當做識別碼使用的保留字，因為它們在 PowerShell 中有特殊意義。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: 928962b9bf28d95e8c037e9c09e5425ee730b172
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206903"
---
# <a name="about-reserved-words"></a>關於保留字

## <a name="short-description"></a>簡短描述
列出無法當做識別碼使用的保留字，因為它們在 PowerShell 中有特殊意義。

## <a name="long-description"></a>詳細描述

有些單字在 PowerShell 中有特殊意義。 當這些單字出現時沒有引號時，PowerShell 會嘗試套用其特殊意義，而不是將它們視為字元字串。 若要在命令或腳本中使用這些單字作為參數引數，而不叫用其特殊意義，請以引號括住保留字。

以下是 PowerShell 中的保留字：

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

許多語言關鍵字（包括 `Foreach` 、 `If` 、 `For` 和 `While` ）都有自己的說明文章。 若要查看它們，請輸入 `Get-Help about_` 並加入關鍵字。 例如，若要取得語句的相關資訊 `Foreach` ，請輸入：

```powershell
Get-Help about_ForEach
```

如需 `Filter` 語句或語句語法的詳細資訊 `Return` ，請輸入：

```powershell
Get-Help about_Functions
```

如需其他保留字的詳細資訊，請輸入：

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> 並非每個保留字都有自己的說明文章。 如果 `Get-Help` 未傳回文章，您可以使用下列命令來搜尋與保留字相關的文章：
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a>另請參閱

- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Language_Keywords](about_Language_Keywords.md)
- [about_Parsing](about_Parsing.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Special_Characters](about_Special_Characters.md)
