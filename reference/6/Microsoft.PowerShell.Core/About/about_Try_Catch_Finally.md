---
description: 描述如何使用 `Try` 、 `Catch` 和 `Finally` 區塊來處理終止錯誤。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: b9395fd4149e4cdaf564d252861377dfc5e17ddd
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206840"
---
# <a name="about-try-catch-finally"></a>關於 Try Catch Finally

## <a name="short-description"></a>簡短描述
描述如何使用 `Try` 、 `Catch` 和 `Finally` 區塊來處理終止錯誤。

## <a name="long-description"></a>詳細描述

使用 `Try` 、 `Catch` 和 `Finally` 區塊來回應或處理腳本中的終止錯誤。 `Trap`語句也可以用來處理腳本中的終止錯誤。 如需詳細資訊，請參閱 [about_Trap](about_Trap.md)。

終止錯誤會停止執行語句。 如果 PowerShell 沒有以某種方式處理終止錯誤，PowerShell 也會停止使用目前的管線來執行函式或腳本。 在其他語言中（例如 C \# ），終止錯誤稱為例外狀況。

使用 `Try` 區塊來定義腳本的區段，讓 PowerShell 監視錯誤。 當區塊內發生錯誤時 `Try` ，會先將錯誤儲存至 `$Error` 自動變數。 PowerShell 接著會搜尋 `Catch` 區塊以處理錯誤。 如果 `Try` 語句沒有相符的 `Catch` 區塊，則 PowerShell 會繼續 `Catch` 在父範圍中搜尋適當的區塊或 `Trap` 語句。 `Catch`區塊完成之後，或如果 `Catch` 找不到適當的區塊或 `Trap` 語句，則 `Finally` 會執行區塊。 如果無法處理錯誤，就會將錯誤寫入錯誤串流。

`Catch`區塊可以包含用來追蹤錯誤或復原預期腳本流程的命令。 `Catch`區塊可以指定它所攔截的錯誤類型。 `Try`語句可以 `Catch` 針對不同種類的錯誤，包含多個區塊。

`Finally`區塊可以用來釋放腳本不再需要的任何資源。

`Try`、 `Catch` 和 `Finally` 類似于 `Try` C 程式 `Catch` `Finally` 設計語言中使用的、和關鍵字 \# 。

### <a name="syntax"></a>SYNTAX

`Try`語句包含 `Try` 區塊、零個或多個 `Catch` 區塊，以及零或一個 `Finally` 區塊。 `Try`語句至少必須有一個 `Catch` 區塊或一個 `Finally` 區塊。

以下顯示 `Try` 區塊語法：

```powershell
try {<statement list>}
```

`Try`關鍵字後面接著以大括弧括住的語句清單。 如果在執行語句清單中的語句時，發生終止錯誤，腳本會將錯誤物件從 `Try` 區塊傳遞到適當的 `Catch` 區塊。

以下顯示 `Catch` 區塊語法：

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

錯誤類型會顯示在括弧中。 最外層的括弧表示元素是選擇性的。

`Catch`關鍵字後面接著選擇性的錯誤類型規格清單和語句清單。 如果區塊中發生終止錯誤 `Try` ，則 PowerShell 會搜尋適當的 `Catch` 區塊。 如果找到一個，就 `Catch` 會執行區塊中的語句。

`Catch`區塊可以指定一或多個錯誤類型。 錯誤類型是 Microsoft .NET Framework 例外狀況或衍生自 .NET Framework 例外狀況的例外狀況。 `Catch`區塊會處理指定之 .NET Framework 例外狀況類別或衍生自指定類別之任何類別的錯誤。

如果 `Catch` 區塊指定錯誤類型，該區塊會 `Catch` 處理該錯誤類型。 如果 `Catch` 區塊未指定錯誤類型，該 `Catch` 區塊會處理區塊中發生的任何錯誤 `Try` 。 `Try`語句可以 `Catch` 針對不同的指定錯誤類型包含多個區塊。

以下顯示 `Finally` 區塊語法：

```powershell
finally {<statement list>}
```

`Finally`關鍵字後面接著會在每次執行腳本時執行的語句清單，即使執行的 `Try` 語句沒有錯誤或在語句中攔截到錯誤 `Catch` 。

請注意，按下<kbd>CTRL</kbd> + <kbd>C</kbd>會停止管線。 傳送至管線的物件將不會顯示為輸出。 因此，如果您包含要顯示的語句，例如 "Finally block run"，就不會在您按下<kbd>CTRL</kbd>C 之後顯示它，即使區塊已執行也一樣 + <kbd>C</kbd> `Finally` 。

### <a name="catching-errors"></a>捕捉錯誤

下列範例腳本會顯示 `Try` 具有區塊的區塊 `Catch` ：

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

`Catch`關鍵字必須緊接在 `Try` 區塊或另一個 `Catch` 區塊之後。

PowerShell 無法將 "NonsenseString" 辨識為 Cmdlet 或其他專案。
執行此腳本會傳回下列結果：

```powershell
An error occurred.
```

當腳本遇到 "NonsenseString" 時，會造成終止錯誤。 區塊會執行 `Catch` 區塊內的語句清單，以處理錯誤。

### <a name="using-multiple-catch-statements"></a>使用多個 CATCH 語句

`Try`語句可以有任意數目的 `Catch` 區塊。 例如，下列腳本具有 `Try` 下載的區塊 `MyDoc.doc` ，其中包含兩個 `Catch` 區塊：

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

第一個 `Catch` 區塊會處理 **系統 WebException** 和 **IOException** 類型的錯誤。 第二個 `Catch` 區塊未指定錯誤類型。 第二個 `Catch` 區塊會處理發生的任何其他終止錯誤。

PowerShell 會依繼承比對錯誤類型。 `Catch`區塊會處理指定之 .NET Framework 例外狀況類別或衍生自指定類別之任何類別的錯誤。 下列範例包含攔截「找 `Catch` 不到命令」錯誤的區塊：

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

指定的錯誤類型 **system.management.automation.commandnotfoundexception** 繼承自 **System.SystemException** 類型。 下列範例也會捕捉找不到命令錯誤：

```powershell
catch [System.SystemException] {"Base Exception" }
```

此 `Catch` 區塊會處理「找不到命令」錯誤，以及繼承自 **SystemException** 類型的其他錯誤。

如果您指定 error 類別和它的其中一個衍生類別，請將 `Catch` 衍生類別的區塊放在 `Catch` 一般類別的區塊之前。

### <a name="using-traps-in-a-try-catch"></a>在 Try Catch 中使用陷阱

在區塊中 `Try` 定義的區塊中發生終止錯誤 `Trap` `Try` ，即使有相符的 `Catch` 區塊， `Trap` 語句還是會取得控制權。

如果 `Trap` 存在於較高的區塊 `Try` 中，而且 `Catch` 目前的範圍內沒有相符的區塊，則即使有 `Trap` 任何父範圍具有相符的區塊，也會取得控制權 `Catch` 。

### <a name="accessing-exception-information"></a>存取例外狀況資訊

在 `Catch` 區塊內，可以使用來存取目前的錯誤 `$_` ，也就是所謂的 `$PSItem` 。 物件的類型為 **ErrorRecord** 。

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

執行此腳本會傳回下列結果：

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

還有其他可以存取的屬性，例如 **ScriptStackTrace** 、 **Exception** 和 **ErrorDetails** 。  例如，如果我們將腳本變更為下列程式碼：

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

結果會類似于：

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a>使用 FINALLY 釋放資源

若要釋放腳本所使用的資源，請在 `Finally` 和區塊之後加入區塊 `Try` `Catch` 。 `Finally`無論 `Try` 區塊是否遇到終止錯誤，區塊語句都會執行。 PowerShell 會在 `Finally` 腳本結束之前或目前區塊超出範圍之前執行區塊。

`Finally`即使您使用<kbd>CTRL</kbd> + <kbd>C</kbd>停止腳本，還是會執行區塊。 `Finally`如果 Exit 關鍵字在區塊內停止腳本，也會執行區塊 `Catch` 。

### <a name="see-also"></a>另請參閱

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)
