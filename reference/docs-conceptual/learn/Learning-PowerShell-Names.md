---
ms.date: 08/24/2018
keywords: powershell,cmdlet
title: 了解 PowerShell 命令名稱
ms.openlocfilehash: a65ffcdca6510093b0a77234e20546b6cc1f02bf
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030423"
---
# <a name="learning-powershell-command-names"></a>了解 PowerShell 命令名稱

您需要針對大部分命令列介面投入大量時間來學習命令與參數的名稱。 問題在於模式很少。 記憶是學習您需定期使用之參數與命令的唯一方式。

當您使用新的命令或參數時，不能總是使用您已經知道的項目。 您必須尋找並學習新名稱。 傳統上，命令列介面會從一小組工具開始，並隨著累加的新增項目而成長。 很容易就能理解為什麼沒有標準結構。
這似乎就是命令名稱的邏輯，因為每個命令都是一個單獨的工具。 PowerShell 提供更好的方式來處理命令名稱。

## <a name="learning-command-names-in-traditional-shells"></a>學習傳統殼層中的命令名稱

大部分命令的建置目的是為了管理作業系統或應用程式的項目，例如服務或處理程序。 命令的名稱不一定適合某個系列。 例如，在 Windows 系統上，您可以使用 `net start` 與 `net stop` 命令來啟動及停止服務。 **Sc.exe** 是另一個適用於 Windows 的服務控制工具。 該名稱不符合 **net.exe** 服務命令的命名模式。 為了管理處理序，Windows 提供 **tasklist.exe** 命令來列出處理序，並提供 **taskkill.exe** 命令來刪除處理序。

此外，這些命令也沒有標準的參數規格。 您無法使用 `net start` 命令來啟動遠端電腦上的服務。 **sc.exe** 命令可以啟動遠端電腦上的服務。 但是，若要指定遠端電腦，您必須在其名稱前面加上雙反斜線。 若要在名為 DC01 的遠端電腦上啟動多工緩衝處理器服務，您要輸入 `sc.exe \\DC01 start spooler`。
若要列出在 DC01 上執行的工作，請使用 **/S** 參數與不含反斜線的電腦名稱。 例如： `tasklist /S DC01` 。

> [!NOTE]
> 在 PowerShell v6 之前，`sc` 是 `Set-Content` Cmdlet 的別名。 因此，若要在 v6 之前的 PowerShell 版本中執行 **sc.exe** 命令，必須包括完整檔案名稱 **sc.exe** (包含副檔名 **exe**)。

服務與處理序是電腦上具有明確定義之生命週期且可管理的元素範例。 您可能會啟動或停止服務與處理序，或是取得所有目前執行中的服務或處理序清單。 雖然它們之間有重要的技術區別，但您在服務和處理序上執行的動作在概念上是一樣的。 此外，透過指定參數來自訂動作的選項在概念上也可能很類似。

PowerShell 利用這些相似之處，來減少學習及使用 Cmdlet 時需要知道之不同名稱的數量。

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Cmdlet 使用「指令動詞-名詞」名稱降低記住命令的需求

PowerShell 會使用「指令動詞-名詞」命名系統。 每個 Cmdlet 名稱都是由一個標準指令動詞、連字號及一個特定名詞所組成的。 PowerShell 指令動詞不一定是英文動詞，但會表示 PowerShell 中的特定動作。 名詞非常類似任何語言中的名詞。 它們會說明系統管理中重要物件的特定類型。 透過查看一些範例，就能輕鬆地示範這些由兩部分組成的名稱如何減少學習的投入量。

PowerShell 提供一組建議的標準指令動詞。 名詞的限制較少，但一律會說明指令動詞的作用。 PowerShell 提供 `Get-Process`、`Stop-Process`、`Get-Service` 與 `Stop-Service` 之類的命令。

針對這個含有兩個名詞與指令動詞的範例，一致性無法有效簡化學習。 將該清單擴充為具有 10 個指令動詞與 10 個名詞的標準化集合。 現在您只需學習 20 個單字。
但那些單字可組合以形成 100 個完全不同的命令名稱。

透過閱讀 PowerShell 命令的名稱，很容易就能了解該命令的功用。 關閉電腦的命令是 `Stop-Computer`。 列出網路上所有電腦的命令是 `Get-Computer`。 取得系統日期的命令是 `Get-Date`。

您可以針對 **使用**Verb`Get-Command` 參數來列出包含特定指令動詞的所有命令。 例如，若要查看使用 `Get` 指令動詞的所有 Cmdlet，請輸入：

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

使用 **Noun** 參數來查看會影響相同類型物件的一系列命令。 例如，執行下列命令來查看可用於管理服務的命令：

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Cmdlet 使用標準參數

如前所述，傳統命令列介面中所使用的命令不一定會有一致的參數名稱。 參數通常是可輕鬆輸入，但新使用者不容易了解的單一字元或縮寫單字。

不同於其他大部分傳統命令列介面，PowerShell 會直接處理參數，並透過直接存取參數及開發人員指導方針來將參數名稱標準化。 此指導方針鼓勵但不保證每個 Cmdlet 都符合標準。

PowerShell 也會將參數分隔符號標準化。 參數名稱前面一定會加上 '-' 並搭配一個 PowerShell 命令。 請考慮下列範例：

```powershell
Get-Command -Name Clear-Host
```

參數的名稱是 **Name**，但在命令列上用來作為參數時會輸入為 `-Name`。

以下是一些標準參數名稱和使用方式的一般特性。

### <a name="the-help-parameter-"></a>說明參數 (?)

當您在任何 Cmdlet 上指定 `-?` 參數時，PowerShell 會顯示該 Cmdlet 的說明。
未執行 Cmdlet。

### <a name="common-parameters"></a>一般參數

PowerShell 提供數個「一般參數」  。 這些參數是由 PowerShell 引擎所控制。 一般參數一律會以相同方式運作。 一般參數包括 **WhatIf**、**Confirm**、**Verbose**、**Debug**、**Warn**、**ErrorAction**、**ErrorVariable**、**OutVariable** 和 **OutBuffer**。

### <a name="recommended-parameter-names"></a>建議的參數名稱

PowerShell 核心 Cmdlet 會針對類似的參數使用標準名稱。 不會強制使用這些標準名稱，但有明確的指導方針來鼓勵標準化。

例如，參考電腦之參數的建議名稱是 **ComputerName**，而不是 Server、Host、System、Node 或其他常見的替代項目。 其他重要的建議參數名稱包括 **Force**、**Exclude**、**Include**、**PassThru**、**Path** 與 **CaseSensitive**。
