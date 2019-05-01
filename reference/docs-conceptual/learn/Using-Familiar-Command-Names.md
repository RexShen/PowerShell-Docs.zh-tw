---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 使用熟悉的命令名稱
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: b61d647d882d4b2f7ea423a48319e3c104ce96c7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057990"
---
# <a name="using-familiar-command-names"></a>使用熟悉的命令名稱

PowerShell 支援別名，以使用替代名稱來參考命令。 別名讓具有其他殼層使用體驗的使用者能夠使用他們已經知道的常見命令名稱，在 PowerShell 中執行類似作業。

別名會將新名稱與另一個命令產生關聯。 例如，PowerShell 具有會清除輸出視窗的內部函式 `Clear-Host`。 您可以在命令提示字元中輸入 `cls` 或 `clear` 別名。 PowerShell 會解譯這些別名並執行 `Clear-Host` 函式。

此功能可協助使用者學習 PowerShell。 首先，大部分的 **cmd.exe** 與 Unix 使用者都具備他們已經透過名稱知道的大量命令技能。 PowerShell 對應項可能不會產生相同的結果。 不過，結果非常接近，足以讓使用者在不知道 PowerShell 命令名稱的情況下執行動作。 在學習新的命令殼層時，「手指記憶」是挫折的另一個主要來源。 如果您已使用 **cmd.exe** 多年，您可能會反過來輸入 `cls` 命令來清除畫面。 如果沒有 `Clear-Host` 的別名，您就會收到錯誤訊息，而且不知道該怎麼清除輸出。

下列清單顯示一些您可以在 PowerShell 中使用的常見 **cmd.exe** 與 Unix 命令：

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

`Get-Alias` Cmdlet 會顯示與別名相關聯之原生 PowerShell 命令的實際名稱。

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>解譯標準別名

先前提到的別名是專為與其他命令殼層名稱相容所設計。
PowerShell 內建的大部分別名都是基於簡潔性而設計的。 較短的名稱比較容易輸入，但如果您不知道它們指的是什麼，就會變得不容易閱讀。

PowerShell 別名試圖在清晰度與簡潔性之間做出妥協。 PowerShell 會針對常見名詞與指令動詞使用一組標準別名。

範例縮寫：

| 名詞或指令動詞 | 縮寫 |
|--------------|--------------|
| 取得          | g            |
| 設定          | s            |
| 項目         | i            |
| 位置     | l            |
| 命令      | cm           |
| 別名        | al           |

當您知道縮寫名稱，就能了解這些別名。

| Cmdlet 名稱    | 別名 |
|----------------|-------|
| `Get-Item`     | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | gal   |

一旦您熟悉 PowerShell 別名之後，很容易就能猜出 **sal** 別名是指 `Set-Alias`。

## <a name="creating-new-aliases"></a>建立新別名

您可以使用 `Set-Alias` Cmdlet 來建立自己的別名。 例如，下列陳述式會建立先前所討論的標準 Cmdlet 別名：

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

在內部，PowerShell 會在啟動期間使用類似命令，但這些別名無法變更。
如果您嘗試執行這其中一個命令，則會收到說明無法修改別名的錯誤。 例如：

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
