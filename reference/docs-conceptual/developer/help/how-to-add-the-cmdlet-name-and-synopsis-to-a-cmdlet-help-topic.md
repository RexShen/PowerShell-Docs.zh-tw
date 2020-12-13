---
ms.date: 09/13/2016
ms.topic: reference
title: 如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題
description: 如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題
ms.openlocfilehash: aeeb0cdd1d6d17b88067928ff952dc57a9441917
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659059"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題

本節說明如何新增在 Cmdlet 說明的 **名稱** 和 **概要** 區段中顯示的內容。 在說明檔中，此內容會新增至每個 Cmdlet 的命令節點。

> [!NOTE]
> 如需說明檔的完整觀點，請開啟 `dll-Help.xml` 位於 PowerShell 安裝目錄中的其中一個檔案。 例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>新增 Cmdlet 名稱和概要

- Cmdlet 說明可以顯示指令程式的兩個描述。 第一個描述是簡短描述，稱為「摘要」。 第二個描述是更詳細的描述，會在 [將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)中討論。
  這兩個描述應該撰寫成單一段落。

- 在概要中，不會重複 Cmdlet 名稱。 通知使用者 `Get-Server` Cmdlet 取得伺服器是短暫的，但無法提供資訊。 相反地，請使用同義字並將詳細資料新增至描述。

  範例：「取得代表本機或遠端電腦的物件」。

- 使用簡單的動詞命令，例如 "get"、"create" 和 "change" （在摘要中）。 請避免使用「設定」，因為它是模糊的，而像是「修改」的單字。

  範例：「取得檔案中 Authenticode 簽章的相關資訊」。

- 以主動語音撰寫。 例如，「使用 TimeSpan 物件 ...」比「可以使用 TimeSpan 物件 ...」更清楚

- 描述取得物件的 Cmdlet 時，請避免動詞 "display"。 雖然 Windows PowerShell 會顯示 Cmdlet 資料，但請務必為使用者介紹 Cmdlet 所傳回的概念，.NET Framework 可能不會顯示其資料的物件。 如果您強調顯示，使用者可能不知道 Cmdlet 可能傳回許多其他有用的屬性和不會顯示的方法。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
