---
description: PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 關於 PSReadLine
ms.openlocfilehash: 890f8e92172f2d492b6b817b558d4f25c70e8949
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206560"
---
# <a name="psreadline"></a>PSReadLine

## <a name="about_psreadline"></a>about_PSReadLine

## <a name="short-description"></a>簡短描述

PSReadLine 在 PowerShell 主控台中提供改良的命令列編輯體驗。

## <a name="long-description"></a>詳細描述

PSReadLine 2.0 為 PowerShell 主控台提供功能強大的命令列編輯體驗。 它提供：

- 命令列的語法著色
- 語法錯誤的視覺指示
-  (編輯和歷程記錄的更佳多行體驗) 
- 可自訂的按鍵系結
- Cmd 和 Emacs 模式
- 許多設定選項
- Bash 樣式完成 (在 Cmd 模式中為選擇性，預設為 Emacs 模式) 
- Emacs yank/kill-環形
- 以 PowerShell 權杖為基礎的「單字」移動和終止

下列函式可在類別 **[PSConsoleReadLine]** 中使用。

> [!NOTE]
> 從 PowerShell 7.0 開始，如果偵測到螢幕讀取程式，PowerShell 會略過在 Windows 上自動載入 PSReadLine。 PSReadLine 目前無法與螢幕讀取器順利搭配運作。 Windows 上 PowerShell 7.0 的預設轉譯和格式可正常運作。 如有必要，您可以手動載入模組。

## <a name="basic-editing-functions"></a>基本編輯函數

### <a name="abort"></a>中止

中止目前的動作，例如累加式歷程記錄搜尋。

- Emacs： `<Ctrl+g>`

### <a name="acceptandgetnext"></a>AcceptAndGetNext

嘗試執行目前的輸入。 如果可以像 AcceptLine) 一樣執行 (，則會在下一次呼叫 ReadLine 時，重新叫用歷程記錄中的下一個專案。

- Emacs： `<Ctrl+o>`

### <a name="acceptline"></a>AcceptLine

嘗試執行目前的輸入。 如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。

- Cmd： `<Enter>`
- Emacs： `<Enter>`
- Vi 插入模式： `<Enter>`

### <a name="addline"></a>AddLine

接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。 這對於將多行輸入輸入為單一命令很有用，即使單一行本身已完成輸入也是一樣。

- Cmd： `<Shift+Enter>`
- Emacs： `<Shift+Enter>`
- Vi 插入模式： `<Shift+Enter>`
- Vi 命令模式： `<Shift+Enter>`

### <a name="backwarddeletechar"></a>BackwardDeleteChar

刪除游標之前的字元。

- Cmd： `<Backspace>` ， `<Ctrl+h>`
- Emacs： `<Backspace>` 、 `<Ctrl+Backspace>` 、 `<Ctrl+h>`
- Vi 插入模式： `<Backspace>`
- Vi 命令模式： `<X>` 、 `<d,h>`

### <a name="backwarddeleteline"></a>BackwardDeleteLine

如同 BackwardKillLine-刪除從點到行首的文字，但不會將已刪除的文字放在終止環形中。

- Cmd： `<Ctrl+Home>`
- Vi 插入模式： `<Ctrl+u>` 、 `<Ctrl+Home>`
- Vi 命令模式： `<Ctrl+u>` 、 `<Ctrl+Home>` 、 `<d,0>`

### <a name="backwarddeleteword"></a>BackwardDeleteWord

刪除上一個字組。

- Vi 命令模式： `<Ctrl+w>` 、 `<d,b>`

### <a name="backwardkillline"></a>BackwardKillLine

清除輸入至資料指標開頭的輸入。 清除的文字會放在終止環形中。

- Emacs： `<Ctrl+u>` ， `<Ctrl+x,Backspace>`

### <a name="backwardkillword"></a>BackwardKillWord

清除從目前單字開頭到游標處的輸入。 如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。 清除的文字會放在終止環形中。

- Cmd： `<Ctrl+Backspace>`
- Emacs： `<Alt+Backspace>` ， `<Escape,Backspace>`
- Vi 插入模式： `<Ctrl+Backspace>`
- Vi 命令模式： `<Ctrl+Backspace>`

### <a name="cancelline"></a>CancelLine

取消目前的輸入，將輸入保留在畫面上，但返回主機，以便再次評估提示。

- Vi 插入模式： `<Ctrl+c>`
- Vi 命令模式： `<Ctrl+c>`

### <a name="copy"></a>複製

將選取的區域複製到系統剪貼簿。 如果未選取任何區域，請複製整行。

- Cmd： `<Ctrl+C>`

### <a name="copyorcancelline"></a>CopyOrCancelLine

如果已選取文字，請複製到剪貼簿，否則請取消該行。

- Cmd： `<Ctrl+c>`
- Emacs： `<Ctrl+c>`

### <a name="cut"></a>剪下

刪除選取的區域，將已刪除的文字放入系統剪貼簿。

- Cmd： `<Ctrl+x>`

### <a name="deletechar"></a>DeleteChar

刪除游標下的字元。

- Cmd： `<Delete>`
- Emacs： `<Delete>`
- Vi 插入模式： `<Delete>`
- Vi 命令模式： `<Delete>` 、 `<x>` 、 `<d,l>` 、 `<d,Space>`

### <a name="deletecharorexit"></a>DeleteCharOrExit

刪除游標下的字元，如果行是空的，請結束進程。

- Emacs： `<Ctrl+d>`

### <a name="deleteendofword"></a>DeleteEndOfWord

刪除到字尾。

- Vi 命令模式： `<d,e>`

### <a name="deleteline"></a>DeleteLine

刪除目前的行，並啟用復原。

- Vi 命令模式： `<d,d>`

### <a name="deletelinetofirstchar"></a>DeleteLineToFirstChar

將游標的文字刪除到行的第一個非空白字元。

- Vi 命令模式： `<d,^>`

### <a name="deletetoend"></a>DeleteToEnd

刪除至行尾。

- Vi 命令模式： `<D>` 、 `<d,$>`

### <a name="deleteword"></a>DeleteWord

刪除下一個字組。

- Vi 命令模式： `<d,w>`

### <a name="forwarddeleteline"></a>ForwardDeleteLine

如同 ForwardKillLine-刪除從點到行尾的文字，但不會將已刪除的文字放在終止環形中。

- Cmd： `<Ctrl+End>`
- Vi 插入模式： `<Ctrl+End>`
- Vi 命令模式： `<Ctrl+End>`

### <a name="insertlineabove"></a>InsertLineAbove

無論游標位於目前的行上，都會在目前的行上方建立新的空白行。 游標移至新行的開頭。

- Cmd： `<Ctrl+Enter>`

### <a name="insertlinebelow"></a>InsertLineBelow

目前的行下方會建立新的空白行，而不論游標在目前的行上。 游標移至新行的開頭。

- Cmd： `<Shift+Ctrl+Enter>`

### <a name="invertcase"></a>InvertCase

將目前字元的大小寫反轉，並移至下一個字元。

- Vi 命令模式： `<~>`

### <a name="killline"></a>KillLine

清除游標至輸入結尾的輸入。 清除的文字會放在終止環形中。

- Emacs： `<Ctrl+k>`

### <a name="killregion"></a>KillRegion

終止游標與標記之間的文字。

- 函數已解除系結。

### <a name="killword"></a>KillWord

清除游標到目前單字結尾的輸入。 如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。 清除的文字會放在終止環形中。

- Cmd： `<Ctrl+Delete>`
- Emacs： `<Alt+d>` ， `<Escape,d>`
- Vi 插入模式： `<Ctrl+Delete>`
- Vi 命令模式： `<Ctrl+Delete>`

### <a name="paste"></a>貼上

貼上系統剪貼簿中的文字。

- Cmd： `<Ctrl+v>` ， `<Shift+Insert>`
- Vi 插入模式： `<Ctrl+v>`
- Vi 命令模式： `<Ctrl+v>`

> [!IMPORTANT]
> 使用 **Paste** 函式時，剪貼簿緩衝區的整個內容會貼到 PSReadLine 的輸入緩衝區中。 輸入緩衝區接著會傳遞至 PowerShell 剖析器。 使用主控台應用程式的 **按右鍵** [貼上] 方法貼上的輸入會一次複製到輸入緩衝區一個字元。 當換行字元時，輸入緩衝區會傳遞給剖析器。 因此，輸入會一次剖析一行。 貼上方法之間的差異會導致不同的執行行為。

### <a name="pasteafter"></a>PasteAfter

將剪貼簿貼到游標之後，將游標移至貼上文字的結尾。

- Vi 命令模式： `<p>`

### <a name="pastebefore"></a>PasteBefore

將剪貼簿貼到游標之前，將游標移至貼上文字的結尾。

- Vi 命令模式： `<P>`

### <a name="prependandaccept"></a>PrependAndAccept

在前面加上 ' # ' 並接受該行。

- Vi 命令模式： `<#>`

### <a name="redo"></a>取消復原

復原復原。

- Cmd： `<Ctrl+y>`
- Vi 插入模式： `<Ctrl+y>`
- Vi 命令模式： `<Ctrl+y>`

### <a name="repeatlastcommand"></a>RepeatLastCommand

重複上次修改文字。

- Vi 命令模式： `<.>`

### <a name="revertline"></a>RevertLine

將所有輸入還原為目前的輸入。

- Cmd： `<Escape>`
- Emacs： `<Alt+r>` ， `<Escape,r>`

### <a name="shellbackwardkillword"></a>ShellBackwardKillWord

清除從目前單字開頭到游標處的輸入。 如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。 清除的文字會放在終止環形中。

函數已解除系結。

### <a name="shellkillword"></a>ShellKillWord

清除游標到目前單字結尾的輸入。 如果游標在單字之間，則會從資料指標清除輸入至下一個單字的結尾。 清除的文字會放在終止環形中。

函數已解除系結。

### <a name="swapcharacters"></a>SwapCharacters

交換目前的字元和前一個字元。

- Emacs： `<Ctrl+t>`
- Vi 插入模式： `<Ctrl+t>`
- Vi 命令模式： `<Ctrl+t>`

### <a name="undo"></a>復原

復原先前的編輯。

- Cmd： `<Ctrl+z>`
- Emacs： `<Ctrl+_>` ， `<Ctrl+x,Ctrl+u>`
- Vi 插入模式： `<Ctrl+z>`
- Vi 命令模式： `<Ctrl+z>` 、 `<u>`

### <a name="undoall"></a>UndoAll

復原所有先前編輯的行。

- Vi 命令模式： `<U>`

### <a name="unixwordrubout"></a>UnixWordRubout

清除從目前單字開頭到游標處的輸入。 如果游標在單字之間，則會從上一個單字開頭開始清除輸入至游標。 清除的文字會放在終止環形中。

- Emacs： `<Ctrl+w>`

### <a name="validateandacceptline"></a>ValidateAndAcceptLine

嘗試執行目前的輸入。 如果目前的輸入不完整 (例如遺漏右括弧、方括弧或引號，則接續提示會顯示在下一行，而 PSReadLine 會等候按鍵編輯目前的輸入。

- Emacs： `<Ctrl+m>`

### <a name="viacceptline"></a>ViAcceptLine

接受行並切換至插入模式。

- Vi 命令模式： `<Enter>`

### <a name="viacceptlineorexit"></a>ViAcceptLineOrExit

如同 Emacs 模式中的 DeleteCharOrExit，但會接受行，而不是刪除字元。

- Vi 插入模式： `<Ctrl+d>`
- Vi 命令模式： `<Ctrl+d>`

### <a name="viappendline"></a>ViAppendLine

新行會插入目前的行下方。

- Vi 命令模式： `<o>`

### <a name="vibackwarddeleteglob"></a>ViBackwardDeleteGlob

刪除先前的單字，只使用空白字元做為文字分隔符號。

- Vi 命令模式： `<d,B>`

### <a name="vibackwardglob"></a>ViBackwardGlob

將游標移回上一個單字的開頭，只使用空白字元做為分隔符號。

- Vi 命令模式： `<B>`

### <a name="videletebrace"></a>ViDeleteBrace

尋找相符的括弧、括弧或方括弧，並刪除內的所有內容，包括括弧。

- Vi 命令模式： `<d,%>`

### <a name="videleteendofglob"></a>ViDeleteEndOfGlob

刪除到字尾。

- Vi 命令模式： `<d,E>`

### <a name="videleteglob"></a>ViDeleteGlob

刪除下一個 glob (以空白字元分隔的單字) 。

- Vi 命令模式： `<d,W>`

### <a name="videletetobeforechar"></a>ViDeleteToBeforeChar

刪除指定的字元。

- Vi 命令模式： `<d,t>`

### <a name="videletetobeforecharbackward"></a>ViDeleteToBeforeCharBackward

刪除指定的字元。

- Vi 命令模式： `<d,T>`

### <a name="videletetochar"></a>ViDeleteToChar

刪除指定的字元。

- Vi 命令模式： `<d,f>`

### <a name="videletetocharbackward"></a>ViDeleteToCharBackward

在指定的字元之前反向刪除。

- Vi 命令模式： `<d,F>`

### <a name="viinsertatbegining"></a>ViInsertAtBegining

切換至插入模式，並將游標放在行首。

- Vi 命令模式： `<I>`

### <a name="viinsertatend"></a>ViInsertAtEnd

切換至插入模式，並將游標放在行尾。

- Vi 命令模式： `<A>`

### <a name="viinsertline"></a>ViInsertLine

新的行會插入到目前這一行的上方。

- Vi 命令模式： `<O>`

### <a name="viinsertwithappend"></a>ViInsertWithAppend

從目前的行位置附加。

- Vi 命令模式： `<a>`

### <a name="viinsertwithdelete"></a>ViInsertWithDelete

刪除目前的字元並切換至插入模式。

- Vi 命令模式： `<s>`

### <a name="vijoinlines"></a>ViJoinLines

加入目前的行和下一行。

- Vi 命令模式： `<J>`

### <a name="vireplaceline"></a>ViReplaceLine

清除整個命令列。

- Vi 命令模式： `<S>` 、 `<c,c>`

### <a name="vireplacetobeforechar"></a>ViReplaceToBeforeChar

取代指定的字元。

- Vi 命令模式： `<c,t>`

### <a name="vireplacetobeforecharbackward"></a>ViReplaceToBeforeCharBackward

取代指定的字元。

- Vi 命令模式： `<c,T>`

### <a name="vireplacetochar"></a>ViReplaceToChar

刪除指定的字元。

- Vi 命令模式： `<c,f>`

### <a name="vireplacetocharbackward"></a>ViReplaceToCharBackward

取代指定的字元。

- Vi 命令模式： `<c,F>`

### <a name="viyankbeginningofline"></a>ViYankBeginningOfLine

從緩衝區開頭 Yank 至資料指標。

- Vi 命令模式： `<y,0>`

### <a name="viyankendofglob"></a>ViYankEndOfGlob

從資料指標 Yank 至 WORD (s) 的結尾。

- Vi 命令模式： `<y,E>`

### <a name="viyankendofword"></a>ViYankEndOfWord

從資料指標 Yank 至 word (s) 的結尾。

- Vi 命令模式： `<y,e>`

### <a name="viyankleft"></a>ViYankLeft

Yank 字元 (s) 到游標的左邊。

- Vi 命令模式： `<y,h>`

### <a name="viyankline"></a>ViYankLine

Yank 整個緩衝區。

- Vi 命令模式： `<y,y>`

### <a name="viyanknextglob"></a>ViYankNextGlob

從資料指標 Yank 至下一個單字的開頭 (s) 。

- Vi 命令模式： `<y,W>`

### <a name="viyanknextword"></a>ViYankNextWord

Yank) 在游標之後 (s 的單字。

- Vi 命令模式： `<y,w>`

### <a name="viyankpercent"></a>ViYankPercent

Yank 至/從相符的括弧。

- Vi 命令模式： `<y,%>`

### <a name="viyankpreviousglob"></a>ViYankPreviousGlob

從字組開頭 (s 的 Yank) 到資料指標。

- Vi 命令模式： `<y,B>`

### <a name="viyankpreviousword"></a>ViYankPreviousWord

Yank) 在游標之前的文字 (s。

- Vi 命令模式： `<y,b>`

### <a name="viyankright"></a>ViYankRight

Yank 字元 (s) 在游標右邊和右邊。

- Vi 命令模式： `<y,l>` 、 `<y,Space>`

### <a name="viyanktoendofline"></a>ViYankToEndOfLine

從資料指標 Yank 至緩衝區的結尾。

- Vi 命令模式： `<y,$>`

### <a name="viyanktofirstchar"></a>ViYankToFirstChar

從第一個非空白字元 Yank 至游標。

- Vi 命令模式： `<y,^>`

### <a name="yank"></a>美國 佬

將最近終止的文字加入至輸入。

- Emacs： `<Ctrl+y>`

### <a name="yanklastarg"></a>YankLastArg

Yank 前一個歷程記錄行中的最後一個引數。 使用引數時，第一次叫用時，其行為就像 YankNthArg 一樣。 如果叫用多次，則改為逐一查看歷程記錄和 arg，將方向 (負反轉方向。 ) 

- Cmd： `<Alt+.>`
- Emacs： `<Alt+.>` 、 `<Alt+_>` 、 `<Escape,.>` 、 `<Escape,_>`

### <a name="yankntharg"></a>YankNthArg

從上一個歷程記錄行中 Yank 命令) 之後，第一個引數 (。
使用引數時，請 yank 第 n 個引數 (從 0) 開始，如果引數為負數，則從最後一個引數開始。

- Emacs： `<Ctrl+Alt+y>` ， `<Escape,Ctrl+y>`

### <a name="yankpop"></a>YankPop

如果先前的作業是 Yank 或 YankPop，請將先前 yanked 的文字取代為終止環形中的下一個已取消文字。

- Emacs： `<Alt+y>` ， `<Escape,y>`

## <a name="cursor-movement-functions"></a>資料指標移動函數

### <a name="backwardchar"></a>BackwardChar

將游標向左移動一個字元。 這可能會將游標移至多行輸入的上一行。

- Cmd： `<LeftArrow>`
- Emacs： `<LeftArrow>` ， `<Ctrl+b>`
- Vi 插入模式： `<LeftArrow>`
- Vi 命令模式： `<LeftArrow>` 、 `<Backspace>` 、 `<h>`

### <a name="backwardword"></a>BackwardWord

將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。 單字界限是由一組可設定的字元所定義。

- Cmd： `<Ctrl+LeftArrow>`
- Emacs： `<Alt+b>` ， `<Escape,b>`
- Vi 插入模式： `<Ctrl+LeftArrow>`
- Vi 命令模式： `<Ctrl+LeftArrow>`

### <a name="beginningofline"></a>BeginningOfLine

如果輸入有多行，請移至目前行的開頭，如果已經在行首，則移至輸入的開頭。 如果輸入具有單一行，請移至輸入的開頭。

- Cmd： `<Home>`
- Emacs： `<Home>` ， `<Ctrl+a>`
- Vi 插入模式： `<Home>`
- Vi 命令模式： `<Home>`

### <a name="endofline"></a>EndOfLine

如果輸入有多行，請移至目前行的結尾，如果已經在行尾，則移至輸入的結尾。 如果輸入具有單一行，請移至輸入的結尾。

- Cmd： `<End>`
- Emacs： `<End>` ， `<Ctrl+e>`
- Vi 插入模式： `<End>`

### <a name="forwardchar"></a>ForwardChar

將游標向右移動一個字元。 這可能會將游標移至下一行的多行輸入。

- Cmd： `<RightArrow>`
- Emacs： `<RightArrow>` ， `<Ctrl+f>`
- Vi 插入模式： `<RightArrow>`
- Vi 命令模式： `<RightArrow>` 、 `<Space>` 、 `<l>`

### <a name="forwardword"></a>ForwardWord

將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。 單字界限是由一組可設定的字元所定義。

- Emacs： `<Alt+f>` ， `<Escape,f>`

### <a name="gotobrace"></a>GotoBrace

移至相符的大括弧、括弧或方括弧。

- Cmd： `<Ctrl+]>`
- Vi 插入模式： `<Ctrl+]>`
- Vi 命令模式： `<Ctrl+]>`

### <a name="gotocolumn"></a>GotoColumn

移至 arg 所表示的資料行。

- Vi 命令模式： `<|>`

### <a name="gotofirstnonblankofline"></a>GotoFirstNonBlankOfLine

將游標移至行中的第一個非空白字元。

- Vi 命令模式： `<^>`

### <a name="movetoendofline"></a>MoveToEndOfLine

將游標移至輸入的結尾。

- Vi 命令模式： `<End>` 、 `<$>`

### <a name="nextline"></a>NextLine

將游標移至下一行。

- 函數已解除系結。

### <a name="nextword"></a>NextWord

將游標向前移至下一個單字的開頭。 單字界限是由一組可設定的字元所定義。

- Cmd： `<Ctrl+RightArrow>`
- Vi 插入模式： `<Ctrl+RightArrow>`
- Vi 命令模式： `<Ctrl+RightArrow>`

### <a name="nextwordend"></a>NextWordEnd

將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。 單字界限是由一組可設定的字元所定義。

- Vi 命令模式： `<e>`

### <a name="previousline"></a>PreviousLine

將游標移至上一行。

- 函數已解除系結。

### <a name="shellbackwardword"></a>ShellBackwardWord

將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。 單字界限是由 PowerShell 權杖所定義。

- 函數已解除系結。

### <a name="shellforwardword"></a>ShellForwardWord

將游標向前移至下一個單字的開頭。 單字界限是由 PowerShell 權杖所定義。

- 函數已解除系結。

### <a name="shellnextword"></a>ShellNextWord

將游標向前移動至目前單字的結尾，或在文字之間移動到下一個單字的結尾。 單字界限是由 PowerShell 權杖所定義。

- 函數已解除系結。

### <a name="vibackwardword"></a>ViBackwardWord

將游標移回目前單字的開頭，或將游標移回上一個單字開頭的單字。 單字界限是由一組可設定的字元所定義。

- Vi 命令模式： `<b>`

### <a name="viendofglob"></a>ViEndOfGlob

將游標移至單字的結尾，只使用空白字元做為分隔符號。

- Vi 命令模式： `<E>`

### <a name="viendofpreviousglob"></a>ViEndOfPreviousGlob

移至上一個單字的結尾，只使用空白字元做為單字分隔符號。

- 函數已解除系結。

### <a name="vigotobrace"></a>ViGotoBrace

類似于 GotoBrace，但它是以字元為基礎，而不是以權杖為基礎。

- Vi 命令模式： `<%>`

### <a name="vinextglob"></a>ViNextGlob

移至下一個單字，只使用空白字元做為單字分隔符號。

- Vi 命令模式： `<W>`

### <a name="vinextword"></a>ViNextWord

將游標向前移至下一個單字的開頭。 單字界限是由一組可設定的字元所定義。

- Vi 命令模式： `<w>`

## <a name="history-functions"></a>歷程記錄函數

### <a name="beginningofhistory"></a>BeginningOfHistory

移至歷程記錄中的第一個專案。

- Emacs： `<Alt+`<>`

### <a name="clearhistory"></a>ClearHistory

清除 PSReadLine 中的歷程記錄。 這不會影響 PowerShell 歷程記錄。

- Cmd： `<Alt+F7>`

### <a name="endofhistory"></a>EndOfHistory

移至記錄中目前輸入)  (的最後一個專案。

- Emacs： `<Alt+>>`

### <a name="forwardsearchhistory"></a>ForwardSearchHistory

透過歷程記錄執行漸進式向前搜尋。

- Cmd： `<Ctrl+s>`
- Emacs： `<Ctrl+s>`

### <a name="historysearchbackward"></a>HistorySearchBackward

將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' previous ' 專案。

- Cmd： `<F8>`

### <a name="historysearchforward"></a>HistorySearchForward

將目前的輸入取代為 PSReadLine 記錄中與開始和輸入和資料指標之間的字元相符的 ' next ' 專案。

- Cmd： `<Shift+F8>`

### <a name="nexthistory"></a>NextHistory

將目前的輸入取代為 PSReadLine 記錄中的 ' next ' 專案。

- Cmd： `<DownArrow>`
- Emacs： `<DownArrow>` ， `<Ctrl+n>`
- Vi 插入模式： `<DownArrow>`
- Vi 命令模式： `<DownArrow>` 、 `<j>` 、 `<+>`

### <a name="previoushistory"></a>PreviousHistory

將目前的輸入取代為 PSReadLine 記錄中的 ' previous ' 專案。

- Cmd： `<UpArrow>`
- Emacs： `<UpArrow>` ， `<Ctrl+p>`
- Vi 插入模式： `<UpArrow>`
- Vi 命令模式： `<UpArrow>` 、 `<k>` 、 `<->`

### <a name="reversesearchhistory"></a>ReverseSearchHistory

透過歷程記錄執行增量向前搜尋。

- Cmd： `<Ctrl+r>`
- Emacs： `<Ctrl+r>`

### <a name="visearchhistorybackward"></a>ViSearchHistoryBackward

提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。

- Vi 插入模式： `<Ctrl+r>`
- Vi 命令模式： `</>` 、 `<Ctrl+r>`

## <a name="completion-functions"></a>完成函式

### <a name="complete"></a>完成

嘗試對資料指標周圍的文字執行完成。 如果有多個可能的完成，則會使用最長的明確前置詞來完成。 如果嘗試完成最長的明確完成，則會顯示可能的完成清單。

- Emacs： `<Tab>`

### <a name="menucomplete"></a>MenuComplete

嘗試對資料指標周圍的文字執行完成。 如果有多個可能的完成，則會使用最長的明確前置詞來完成。 如果嘗試完成最長的明確完成，則會顯示可能的完成清單。

- Cmd： `<Ctrl+Space>`
- Emacs： `<Ctrl+Space>`

### <a name="possiblecompletions"></a>PossibleCompletions

顯示可能的完成清單。

- Emacs： `<Alt+=>`
- Vi 插入模式： `<Ctrl+Space>`
- Vi 命令模式： `<Ctrl+Space>`

### <a name="tabcompletenext"></a>TabCompleteNext

嘗試使用下一個可用的完成來完成資料指標周圍的文字。

- Cmd： `<Tab>`
- Vi 命令模式： `<Tab>`

### <a name="tabcompleteprevious"></a>TabCompletePrevious

嘗試使用先前的可用完成來完成資料指標周圍的文字。

- Cmd： `<Shift+Tab>`
- Vi 命令模式： `<Shift+Tab>`

### <a name="vitabcompletenext"></a>ViTabCompleteNext

視需要結束目前的編輯群組，並叫用 TabCompleteNext。

- Vi 插入模式： `<Tab>`

### <a name="vitabcompleteprevious"></a>ViTabCompletePrevious

視需要結束目前的編輯群組，並叫用 TabCompletePrevious。

- Vi 插入模式： `<Shift+Tab>`

## <a name="miscellaneous-functions"></a>其他函式

### <a name="capturescreen"></a>CaptureScreen

啟動互動式螢幕擷取畫面-向上/向下箭號選取 [線條]，輸入將選取的文字複製到剪貼簿做為文字和 html。

- 函數已解除系結。

### <a name="clearscreen"></a>ClearScreen

清除畫面並在畫面頂端繪製目前的線。

- Cmd： `<Ctrl+l>`
- Emacs： `<Ctrl+l>`
- Vi 插入模式： `<Ctrl+l>`
- Vi 命令模式： `<Ctrl+l>`

### <a name="digitargument"></a>DigitArgument

開始新的數位引數以傳遞至其他函式。

- Cmd： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、 `<Alt+3>` 、 `<Alt+4>` 、 `<Alt+5>` 、 `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>` 、、、、、 `<Alt+->`
- Emacs： `<Alt+0>` 、 `<Alt+1>` 、 `<Alt+2>` 、、、 `<Alt+3>` `<Alt+4>` `<Alt+5>` 、 `<Alt+6>` 、 `<Alt+7>` 、 `<Alt+8>` 、 `<Alt+9>` 、、 `<Alt+->`
- Vi 命令模式： `<0>` 、 `<1>` 、 `<2>` 、 `<3>` 、 `<4>` 、 `<5>` 、 `<6>` `<7>` `<8>` 、、、、 `<9>`

### <a name="invokeprompt"></a>InvokePrompt

清除目前的提示，並呼叫 prompt 函式以重新顯示提示。 適用于變更狀態的自訂金鑰處理常式，例如變更目前的目錄。

- 函數已解除系結。

### <a name="scrolldisplaydown"></a>ScrollDisplayDown

將顯示畫面向下移動一個畫面。

- Cmd： `<PageDown>`
- Emacs： `<PageDown>`

### <a name="scrolldisplaydownline"></a>ScrollDisplayDownLine

將向下移動一行。

- Cmd： `<Ctrl+PageDown>`
- Emacs： `<Ctrl+PageDown>`

### <a name="scrolldisplaytocursor"></a>ScrollDisplayToCursor

將顯示滾動至游標。

- Emacs： `<Ctrl+End>`

### <a name="scrolldisplaytop"></a>ScrollDisplayTop

將顯示器向上方滾動。

- Emacs： `<Ctrl+Home>`

### <a name="scrolldisplayup"></a>ScrollDisplayUp

將顯示畫面向上移動一次。

- Cmd： `<PageUp>`
- Emacs： `<PageUp>`

### <a name="scrolldisplayupline"></a>ScrollDisplayUpLine

將顯示畫面向下移動一行。

- Cmd： `<Ctrl+PageUp>`
- Emacs： `<Ctrl+PageUp>`

### <a name="selfinsert"></a>SelfInsert

插入金鑰。

- 函數已解除系結。

### <a name="showkeybindings"></a>ShowKeyBindings

顯示所有系結的索引鍵。

- Cmd： `<Ctrl+Alt+?>`
- Emacs： `<Ctrl+Alt+?>`
- Vi 插入模式： `<Ctrl+Alt+?>`

### <a name="vicommandmode"></a>ViCommandMode

將目前的作業模式從 Vi-Insert 切換至 Vi 命令。

- Vi 插入模式： `<Escape>`

### <a name="vidigitargumentinchord"></a>ViDigitArgumentInChord

開始新的數位引數，以傳遞至其他函式，而非 vi 的 chords 之一。

- 函數已解除系結。

### <a name="vieditvisually"></a>ViEditVisually

在 [$env：編輯器] 或 [$env：視覺效果] 所指定的文字編輯器中編輯命令行。

- Emacs： `<Ctrl+x,Ctrl+e>`
- Vi 命令模式： `<v>`

### <a name="viexit"></a>ViExit

離開 shell。

- 函數已解除系結。

### <a name="viinsertmode"></a>ViInsertMode

切換至插入模式。

- Vi 命令模式： `<i>`

### <a name="whatiskey"></a>WhatIsKey

讀取金鑰，並告訴我金鑰的系結目標。

- Cmd： `<Alt+?>`
- Emacs： `<Alt+?>`

## <a name="selection-functions"></a>選取函式

### <a name="exchangepointandmark"></a>ExchangePointAndMark

游標放在標記的位置，而標記會移至游標位置。

- Emacs： `<Ctrl+x,Ctrl+x>`

### <a name="selectall"></a>SelectAll

選取整行。

- Cmd： `<Ctrl+a>`

### <a name="selectbackwardchar"></a>SelectBackwardChar

調整目前的選取範圍，以包含前一個字元。

- Cmd： `<Shift+LeftArrow>`
- Emacs： `<Shift+LeftArrow>`

### <a name="selectbackwardsline"></a>SelectBackwardsLine

調整目前的選取範圍，以包含從游標到行首的起點。

- Cmd： `<Shift+Home>`
- Emacs： `<Shift+Home>`

### <a name="selectbackwardword"></a>SelectBackwardWord

調整目前的選取範圍，以包含前一個字組。

- Cmd： `<Shift+Ctrl+LeftArrow>`
- Emacs： `<Alt+B>`

### <a name="selectforwardchar"></a>SelectForwardChar

調整目前的選取範圍，以包含下一個字元。

- Cmd： `<Shift+RightArrow>`
- Emacs： `<Shift+RightArrow>`

### <a name="selectforwardword"></a>SelectForwardWord

使用 ForwardWord 調整目前的選取範圍，以包含下一個字組。

- Emacs： `<Alt+F>`

### <a name="selectline"></a>SelectLine

調整目前的選取範圍，以包含從游標到行尾。

- Cmd： `<Shift+End>`
- Emacs： `<Shift+End>`

### <a name="selectnextword"></a>SelectNextWord

調整目前的選取範圍，以包含下一個字組。

- Cmd： `<Shift+Ctrl+RightArrow>`

### <a name="selectshellbackwardword"></a>SelectShellBackwardWord

使用 ShellBackwardWord 調整目前的選取範圍，以包含前一個字組。

- 函數已解除系結。

### <a name="selectshellforwardword"></a>SelectShellForwardWord

使用 ShellForwardWord 調整目前的選取範圍，以包含下一個字組。

- 函數已解除系結。

### <a name="selectshellnextword"></a>SelectShellNextWord

使用 ShellNextWord 調整目前的選取範圍，以包含下一個字組。

- 函數已解除系結。

### <a name="setmark"></a>SetMark

標記目前的資料指標位置，以用於後續的編輯命令。

- Emacs： `<Ctrl+`>`

## <a name="search-functions"></a>搜尋函數

### <a name="charactersearch"></a>CharacterSearch

讀取字元，並向前搜尋該字元的下一個出現位置。
如果指定了引數，則在第 n 次發生) 時，向前搜尋 (或向後搜尋。

- Cmd： `<F3>`
- Emacs： `<Ctrl+]>`
- Vi 插入模式： `<F3>`
- Vi 命令模式： `<F3>`

### <a name="charactersearchbackward"></a>CharacterSearchBackward

讀取字元，並向後搜尋該字元的下一個出現位置。 如果指定了引數，則會在第 n 次出現) 時向後 (或向前搜尋。

- Cmd： `<Shift+F3>`
- Emacs： `<Ctrl+Alt+]>`
- Vi 插入模式： `<Shift+F3>`
- Vi 命令模式： `<Shift+F3>`

### <a name="repeatlastcharsearch"></a>RepeatLastCharSearch

重複上次錄製的字元搜尋。

- Vi 命令模式： `<;>`

### <a name="repeatlastcharsearchbackwards"></a>RepeatLastCharSearchBackwards

重複上次錄製的字元搜尋，但方向相反。

- Vi 命令模式： `<,>`

### <a name="repeatsearch"></a>RepeatSearch

以與之前相同的方向重複最後一個搜尋。

- Vi 命令模式： `<n>`

### <a name="repeatsearchbackward"></a>RepeatSearchBackward

以與之前相同的方向重複最後一個搜尋。

- Vi 命令模式： `<N>`

### <a name="searchchar"></a>SearchChar

讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。 這是「t」功能。

- Vi 命令模式： `<f>`

### <a name="searchcharbackward"></a>SearchCharBackward

讀取下一個字元，然後找出它，然後再向後移一字元。 這是「t」功能。

- Vi 命令模式： `<F>`

### <a name="searchcharbackwardwithbackoff"></a>SearchCharBackwardWithBackoff

讀取下一個字元，然後找出它，然後再向後移一字元。 這是「t」功能。

- Vi 命令模式： `<T>`

### <a name="searchcharwithbackoff"></a>SearchCharWithBackoff

讀取下一個字元，然後找出該字元，再繼續進行，然後再移出一個字元。 這是「t」功能。

- Vi 命令模式： `<t>`

### <a name="searchforward"></a>SearchForward

提示輸入搜尋字串，並在 AcceptLine 時起始搜尋。

- Vi 插入模式： `<Ctrl+s>`
- Vi 命令模式： `<?>` 、 `<Ctrl+s>`

## <a name="custom-key-bindings"></a>自訂索引鍵系結

PSReadLine 支援使用 Cmdlet 的自訂金鑰系結 `Set-PSReadLineKeyHandler` 。 大部分的自訂按鍵系結都會呼叫上述其中一項功能，例如

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

您可以將 ScriptBlock 系結至索引鍵。 ScriptBlock 可以進行任何您想要的動作。 一些實用的範例包括

- 編輯命令行
- 開啟新視窗 (例如說明) 
- 變更目錄而不變更命令列

ScriptBlock 會收到兩個引數：

- `$key` -A **[ConsoleKeyInfo]** 物件，它是觸發自訂系結的索引鍵。 如果您將相同的 ScriptBlock 系結至多個金鑰，且需要根據金鑰執行不同的動作，您可以檢查 $key。 許多自訂系結會忽略此引數。

- `$arg` -任意引數。 通常，這會是使用者從索引鍵系結 DigitArgument 傳遞的整數引數。 如果您的系結不接受引數，則可以合理地忽略此引數。

讓我們看看將命令列新增至歷程記錄，而不執行的範例。 當您知道您忘了進行某個動作，但不想重新輸入您已經輸入的命令列時，這會很有用。

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

您可以在檔案中看到許多在 `SamplePSReadLineProfile.ps1` PSReadLine 模組資料夾中安裝的範例。

大部分的按鍵系結都會使用一些 helper 函數來編輯命令行。
這些 Api 記載于下一節。

## <a name="custom-key-binding-support-apis"></a>自訂金鑰系結支援 Api

下列函式在 PSConsoleReadLine 中是公用的，但不能直接系結至索引鍵。 大部分在自訂金鑰系結中都很有用。

```csharp
void AddToHistory(string command)
```

將命令列新增至歷程記錄，而不加以執行。

```csharp
void ClearKillRing()
```

清除終止環形。  這大多用於測試。

```csharp
void Delete(int start, int length)
```

從開始刪除長度字元。  這種作業支援復原/重做。

```csharp
void Ding()
```

根據使用者喜好設定來執行 Ding 動作。

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

這兩個函式會取出輸入緩衝區目前狀態的相關實用資訊。  第一個較常用於簡單的案例。  如果您的系結使用 Ast 更先進地執行，則會使用第二個。

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

Get-PSReadLineKeyHandler 使用這個函式，而且在自訂按鍵系結中可能不實用。

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

Get-PSReadLineOption 使用這個函式，而且在自訂索引鍵系結中可能不太實用。

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

如果未在命令列上選取任何專案，則會以開始和長度傳回-1。 如果在命令列上有選取專案，則會傳回選取範圍的開始和長度。

```csharp
void Insert(char c)
void Insert(string s)
```

在游標處插入字元或字串。  這種作業支援復原/重做。

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

這是要 PSReadLine 的主要進入點。 它不支援遞迴，因此在自訂索引鍵系結中並不有用。

```csharp
void RemoveKeyHandler(string[] key)
```

Remove-PSReadLineKeyHandler 使用這個函式，而且在自訂索引鍵系結中可能不太實用。

```csharp
void Replace(int start, int length, string replacement)
```

取代部分輸入。 這種作業支援復原/重做。 這是優先于 Delete，後面接著 Insert，因為它會被視為復原的單一動作。

```csharp
void SetCursorPosition(int cursor)
```

將游標移至指定的位移。 不追蹤資料指標移動以進行復原。

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

此函式是 Cmdlet PSReadLineOption 所使用的 helper 方法，但對於想要暫時變更設定的自訂按鍵系結來說可能很有用。

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

此 helper 方法是用於接受 DigitArgument 的自訂系結。 一般呼叫看起來像

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a>注意

### <a name="powershell-compatibility"></a>POWERSHELL 相容性

PSReadLine 需要 PowerShell 3.0 或更新版本，以及主控台主機。 它無法在 PowerShell ISE 中運作。 它會在 Visual Studio Code 的主控台中運作。

### <a name="command-history"></a>命令歷程記錄

PSReadLine 會維護一個記錄檔，其中包含您從命令列輸入的所有命令和資料。 這可能包含機密資料，包括密碼。 例如，如果您使用指令 `ConvertTo-SecureString` 程式，密碼就會以純文字的形式記錄在記錄檔中。 記錄檔是名為的檔案 `$($host.Name)_history.txt` 。 在 Windows 系統上，歷程記錄檔案會儲存在中 `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` 。 在非 Windows 系統上，記錄檔會儲存在 `$env:XDG_DATA_HOME/powershell/PSReadLine` 或 `$env:HOME/.local/share/powershell/PSReadLine` 。

### <a name="feedback--contributing-to-psreadline"></a>意見反應 & 參與 PSReadLine

[GitHub 上的 PSReadLine](https://github.com/PowerShell/PSReadLine)

您可以隨時提交提取要求或在 GitHub 頁面上提交意見反應。

## <a name="see-also"></a>另請參閱

PSReadLine 會受到 GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 程式庫的高度影響。
