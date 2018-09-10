---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: PowerShell 指令碼
ms.openlocfilehash: 754805148dc815a12c5c77e4894fb598c6927f7e
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43133988"
---
# <a name="powershell"></a>PowerShell

PowerShell 是工作型命令列殼層與指令碼語言，並建置在 .NET Framework 之上。
PowerShell 可協助系統管理員與進階使用者快速地將管理作業系統 (Linux、macOS 與 Windows) 與處理序的工作自動化。

PowerShell 命令可讓您從命令列管理電腦。 PowerShell 提供者可讓您如同存取檔案系統般輕易地存取資料存放區 (例如登錄與憑證存放區)。 PowerShell 包含豐富的運算式剖析器與完整開發的指令碼語言。

## <a name="powershell-is-open-source"></a>PowerShell 是開放原始碼

PowerShell 基本原始程式碼現在可在 GitHub 中取得並開放進行社群參與。
請參閱 [GitHub 上的 PowerShell 原始碼](https://github.com/powershell/powershell)。

您可以在[取得 PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) 中，找到入門所需的事項。
或者，從[開始使用](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell) \(英文\) 的快速入門開始。

## <a name="powershell-design-goals"></a>PowerShell 設計目標

PowerShell 消除了長久以來的問題並加入新功能，藉以改善命令列和指令碼環境。

### <a name="discoverability"></a>可搜尋性

PowerShell 可讓您輕鬆搜尋它的功能。 例如，若要尋找可檢視和變更 Windows 服務的 Cmdlet 清單，請輸入：

```powershell
Get-Command *-Service
```

搜尋到可完成工作的 Cmdlet 之後，即可使用 `Get-Help` Cmdlet 來進一步了解此 Cmdlet。 例如，若要顯示 `Get-Service` Cmdlet 的說明，請輸入：

```powershell
Get-Help Get-Service
```

大部分的 Cmdlet 都會傳回物件，這些物件可均操作然後轉譯為可供顯示的文字。 若要完全了解 Cmdlet 的輸出，請透過管道將輸出傳送到 `Get-Member` Cmdlet。 例如，下列命令會顯示 `Get-Service` Cmdlet 所輸出物件的成員相關資訊。

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>一致性

管理系統是一個複雜的工作。 擁有一致介面的工具有助於控制其中的複雜性。 可惜的是，命令列工具與可編寫指令碼的 COM 物件都不具有一致性。

因此，PowerShell 的一致性是非常寶貴的資產。 例如，如果您知道如何使用 `Sort-Object` Cmdlet，即可利用該知識來排序任何 Cmdlet 的輸出。 您不必了解每個 Cmdlet 的不同排序常式。

此外，Cmdlet 開發人員也不需要設計其 Cmdlet 的排序功能。 PowerShell 提供具有基本功能的架構，以強制執行一致性。 此架構會消除一些留給開發人員的選項。 但結果會讓 Cmdlet 的開發作業變得更簡單。

### <a name="interactive-and-scripting-environments"></a>互動式與指令碼環境

Windows 命令提示字元提供互動式殼層，其中具備命令列工具與基本指令碼的存取權。 Windows Script Host (WSH) 具有可編寫指令碼的命令列工具與 COM 自動化物件，但不提供互動式殼層。

PowerShell 結合了互動式殼層與指令碼環境。 PowerShell 可以存取命令列工具、COM 物件與 .NET 類別庫。 這個功能組合會擴充互動式使用者、指令碼寫入器與系統管理員的能力。

### <a name="object-orientation"></a>物件導向

PowerShell 以物件而非文字為基礎。 命令的輸出即為物件。 您可以透過管線將輸出物件傳送到另一個命令以作為它的輸入。

此管線為具有其他殼層使用體驗的人提供熟悉的介面。 PowerShell 透過傳送物件而非文字來延伸此概念。

### <a name="easy-transition-to-scripting"></a>輕鬆轉換為指令碼

PowerShell 的命令可探索性可將以互動方式輸入命令的作業，輕鬆轉換為建立及執行指令碼。 PowerShell 文字記錄與歷程記錄可讓您輕鬆地將命令複製到檔案，以用來作為指令碼。
