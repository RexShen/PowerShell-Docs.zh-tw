---
title: 如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題
ms.date: 09/13/2016
ms.openlocfilehash: 399defcb596ff9e9a596f4cd25ebcb6bcb7c34d2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892875"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題

本節說明如何新增 [Cmdlet 說明] 的 [**名稱**] 和 [**概要**] 區段中所顯示的內容。 在說明檔中，此內容會新增至每個 Cmdlet 的命令節點。

> [!NOTE]
> 如需說明檔的完整視圖，請開啟 `dll-Help.xml` 位於 PowerShell 安裝目錄中的其中一個檔案。 例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>新增 Cmdlet 名稱和概要

- Cmdlet 說明可以顯示 Cmdlet 的兩個描述。 第一個描述是簡短的描述，稱為「摘要」。 第二個描述是更詳細的描述，會在[將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)中討論。
  這兩個描述都應該寫成一個段落。

- 在 [摘要] 中，請勿重複 Cmdlet 名稱。 通知使用者 `Get-Server` Cmdlet 取得伺服器是簡短的，但沒有資訊。 請改用同義字，並將詳細資料加入至描述。

  範例：「取得代表本機或遠端電腦的物件」。

- 在概要中使用簡單動詞，例如 "get"、"create" 和 "change"。 請避免使用「set」，因為它是不清楚的，而是「修改」之類的單字。

  範例：「取得檔案中 Authenticode 簽章的相關資訊」。

- 以現用語音撰寫。 例如，「使用 TimeSpan 物件 ...」比「TimeSpan 物件可以用來 ...」更清楚

- 描述取得物件的 Cmdlet 時，請避免動詞「顯示」。 雖然 Windows PowerShell 會顯示指令程式資料，但請務必向使用者介紹此 Cmdlet 會傳回資料可能不會顯示 .NET Framework 物件的概念。 如果您強調顯示，使用者可能不知道 Cmdlet 可能傳回許多其他有用的屬性和不會顯示的方法。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
