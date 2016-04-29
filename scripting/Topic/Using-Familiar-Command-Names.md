---
title: 使用熟悉的命令名稱
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
---
# 使用熟悉的命令名稱
Windows PowerShell 使用稱為*別名*的機制，讓使用者依據替代名稱來參照命令。 別名可讓具有其他殼層經驗的使用者重複使用他們已經熟悉的一般命令名稱，以在 Windows PowerShell 中執行類似作業。 雖然我們不會詳細討論 Windows PowerShell 別名，但是您在開始使用 Windows PowerShell 時仍然可以使用它們。

別名會將您所輸入的命令名稱與另一個命令產生關聯。 例如，Windows PowerShell 的內部函式 **Clear-Host** 會清除輸出視窗。 如果您在命令提示字元中輸入 **cls** 或 **clear** 命令，則 Windows PowerShell 會解譯這是 **Clear-Host** 函式的別名，並執行 **Clear-Host** 函式。

這項功能可協助使用者了解 Windows PowerShell。 首先，大部分 Cmd.exe 和 UNIX 使用者都有使用者已經透過名稱知道的大型命令庫，而且雖然 Windows PowerShell 對等項目可能不會產生相同的結果，但是它們夠接近使用者可以使用它們來執行工作的形式，而不需要先記下 Windows PowerShell 名稱。 其次，使用者在已熟悉其他殼層時學習新殼層的主要挫折來源是「finger 記憶體」所造成的錯誤。 如果您已使用 Cmd.exe 數年，則整個畫面已填滿輸出而且想要予以清除時，則應該輸入 **cls** 命令並按 ENTER 鍵。 **Clear-Host** 函式在 Windows PowerShell 中沒有別名，因此您只會收到錯誤訊息「**'cls' 無法辨識為 Cmdlet、函式、作業程式或指令碼檔案。**」， 而且不知道怎麼清除輸出。

下列是您可在 Windows PowerShell 內使用的常見 Cmd.exe 和 UNIX 命令的簡短清單︰

|||||
|-|-|-|-|
|cat|dir|掛上 - mount|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|型別|
|del|lp|r|write|
|diff|ls|ren||

如果您發現自己使用其中一個命令，並且想要了解原生 Windows PowerShell 命令的實際名稱，則可以使用 **Get-Alias** 命令：

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

若要讓範例更容易閱讀，《Windows PowerShell 使用者手冊》一般會避免使用別名。 不過，如果您正在使用其他來源中的任意 Windows PowerShell 程式碼片段，或想要定義您自己的別名，則更早深入了解別名仍然十分有用。 本節的其餘部分將討論標準別名，以及如何定義您自己的別名。

### 解譯標準別名
與上述的別名不同 (是針對與其他介面的名稱相容性所設計)，Windows PowerShell 內建的別名通常是針對簡潔性所設計。 這些較短的名稱可以快速輸入，但在您不知道它們所參考的項目時則無法讀取。

Windows PowerShell 嘗試在詳細性與簡潔性之間取得妥協，方法是提供根據一般動詞和名詞之縮寫名稱的一組標準別名。 在您知道縮寫名稱時，這允許可讀取之常見 Cmdlet 的一組核心別名。 例如，在標準別名中，動詞 **Get** 縮寫為 **g**動詞 **Set** 縮寫為 **s**、名詞 **Item** 縮寫為 **i**、名詞 **Location** 縮寫為 **l**，而名詞 Command 縮寫為 **cm**。

以下是說明其運作方式的簡單範例。 Get-Item 的標準別名是合併 **g** (代表 Get) 與 **i** (代表 Item)：**gi**。 Set-Item 的標準別名是合併 **s** (代表 Set) 與 **i** (代表 Item)：**si**。 Get-Location 的標準別名是合併 **g** (代表 Get) 與 **l** (代表 Location)：**gl**。 Set-Location 的標準別名是合併 **s** (代表 Set) 與 **l** (代表 Location)：**sl**。 Get-Command 的標準別名是合併 **g** (代表 Get) 與 **cm** (代表 Command)：**gcm**。 沒有 Set-Command Cmdlet，但是如果有的話，我們可以猜出標準別名來自 **s** (代表 Set) 和 **cm** (代表 Command)：**scm**。 甚至，熟悉 Windows PowerShell 別名的人員在遇到 **scm** 時，可以猜出別名參照 Set-Command。

### 建立新別名
您可以使用 Set-Alias Cmdlet 來建立專屬別名。 例如，下列陳述式會建立＜解譯標準別名＞中所討論的標準 Cmdlet 別名︰

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

在內部，Windows PowerShell 會在啟動期間使用這類命令，但這些別名無法變更。 如果您嘗試實際執行其中一個命令，則會收到說明無法修改別名的錯誤。 例如：

<pre>PS> Set-Alias -Name gi -Value Get-Item
Set-Alias：無法寫入別名，因為別名 gi 是唯讀或常數，因此無法寫入。
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item</pre>



<!--HONumber=Apr16_HO1-->


