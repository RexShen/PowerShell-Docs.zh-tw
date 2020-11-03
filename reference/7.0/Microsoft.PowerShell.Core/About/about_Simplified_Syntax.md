---
description: 描述更簡單、更自然語言的物件集合腳本篩選方式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: 9c9587a2030abeb892115c5e604b4cac921c5a99
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206580"
---
# <a name="about_simplified_syntax"></a>about_Simplified_Syntax

## <a name="short-description"></a>簡短描述
描述更簡單、更自然語言的物件集合腳本篩選方式。

## <a name="long-description"></a>詳細描述

簡化的語法，在 Windows PowerShell 3.0 中引進，可讓您建立一些篩選命令，而不需要使用腳本區塊。 簡化的語法與自然語言更相似，而且主要是用於輸送至命令的物件集合及其對應的 `Where-Object` `ForEach-Object` 別名 `where` 和 `foreach` 。

您可以在集合的成員上使用方法 (最常見的陣列) ，而不會參考 `$_` 腳本區塊內的自動變數。

請考慮下列兩個調用：

### <a name="standard-syntax"></a>標準語法

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }```

### Simplified syntax

Under the simplified syntax, comparison operators that work on members of objects in a
collection are treated as parameters. You can invoke a method on objects in a
collection without referring to the automatic variable `$_` inside a script block.
Compare the following two invocations to those of the previous example:

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

雖然這兩個語法都能運作，但簡化的語法會傳回結果，而不會參考 `$_` 腳本區塊內的自動變數。
方法名稱 `GetKeyAlgorithm` 會被視為的參數 `ForEach-Object` 。
第二個命令會傳回相同的結果，但不會發生錯誤，因為簡化的語法不會嘗試傳回未套用指定引數之專案的結果。

在此範例中， `Process` 會將屬性做 `Description` 為成員名稱參數傳遞至 `ForEach-Object` 命令。 結果是使用中進程的描述。

```powershell
Get-Process | foreach Description
```

在此範例中， `DirectoryInfo` 方法 `GetFiles` 會以命令的成員名稱參數形式傳遞 `ForEach-Object` 。  
使用搜尋模式參數來呼叫方法 `.*` 。  
結果是 `FileInfo` 使用者主目錄中所有 Unix 樣式隱藏檔案的記錄。

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a>另請參閱

- [about_Comparison_Operators](about_Comparison_Operators.md)
- [about_Foreach](about_Foreach.md)
- [Where-Object](xref:Microsoft.PowerShell.Core.Where-Object)
- [Foreach-Object](xref:Microsoft.PowerShell.Core.ForEach-Object)
