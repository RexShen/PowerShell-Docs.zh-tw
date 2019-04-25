---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: 了解 PowerShell 重要概念
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: fad64563d1a7a6abd4f0e430331f81f91f43d312
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058585"
---
# <a name="understanding-important-powershell-concepts"></a>了解 PowerShell 重要概念

PowerShell 設計整合了許多不同環境的概念。 對於具有殼層或程式設計環境體驗的人員來說，將會對其中數個概念感到熟悉。 不過，很少人可以全部精通。 查看其中一些概念，可提供有用的殼層概觀。

## <a name="output-is-object-based"></a>輸出是以物件為基礎的

不同於傳統的命令列介面，PowerShell Cmdlet 是設計來處理物件。
物件是結構化的資訊，而不僅僅是出現在畫面上的字元字串。 命令輸出一律會攜帶您在需要時可以使用的額外資訊。

如果您過去曾使用文字處理工具來處理資料，將會發現它們的行為與在 PowerShell 中使用時不同。 在大部分情況下，您不需要使用文字處理工具來擷取特定資訊。 您可以使用標準的 PowerShell 物件語法，直接存取部分資料。

## <a name="the-command-family-is-extensible"></a>命令系列可進行擴充

**cmd.exe** 之類的介面並未提供可讓您直接擴充內建命令集的方式。 您可以建立要在 **cmd.exe** 中執行的外部命令列工具。 但這些外部工具不會提供任何服務，例如說明整合。 **cmd.exe** 不會自動得知這些外部工具為有效命令。

PowerShell 中的原生命令稱為 *Cmdlet* (唸成 command-let)。 您可以使用已編譯的程式碼或指令碼來建立自己的 Cmdlet 模組與函式。 模組可將 Cmdlet 與提供者新增到殼層。 PowerShell 也支援與 UNIX 殼層指令碼和 **Cmd.exe** 批次檔案類似的指令碼。

## <a name="powershell-handles-console-input-and-display"></a>PowerShell 會處理主控台輸入和顯示

當您輸入命令時，PowerShell 一律會直接處理命令列輸入。 PowerShell 也會將您在畫面上看到的輸出格式化。 此差異十分重要，因為它可以減少每個 Cmdlet 所需的工作。 它會確保您一律可以使用與任何 Cmdlet 相同的方式來執行動作。 Cmdlet 開發人員不需要撰寫程式碼來剖析命令列引數，或將輸出格式化。

傳統命令列工具有其專屬方法來要求和顯示說明。 部分命令列工具使用 **/?** 來觸發說明顯示；其他則使用 **-?**、**/H** 或甚至 **//**。 有一部分會在 GUI 視窗中顯示說明，而不是在主控台顯示中。 如果您使用錯誤的參數，工具可能會忽略您輸入的內容，並開始自動執行工作。
由於 PowerShell 會自動剖析及處理命令列，因此，**-?** 參數一律表示「為我顯示此命令的說明」。

> [!NOTE]
> 如果您在 PowerShell 中執行圖形應用程式，即會開啟應用程式的視窗。
> 只有在處理您提供的命令列輸入或傳回給主控台視窗的應用程式輸出時，PowerShell 才會介入。 它不會影響應用程式的內部運作方式。

## <a name="powershell-uses-some-c-syntax"></a>PowerShell 使用一些 C# 語法

PowerShell 建置於 .NET Framework 之上。 它共用與 C# 程式設計語言相同的部分語法功能和關鍵字。 學習 PowerShell 可以更容易學習 C#。 如果您已經熟悉 C#，則這些相似性可讓學習 PowerShell 更為簡單。
