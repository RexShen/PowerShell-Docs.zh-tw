---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫 PowerShell Cmdlet 的說明
description: 撰寫 PowerShell Cmdlet 的說明
ms.openlocfilehash: b1deaa5998dbc54add93764db785d57afcc0a779
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658111"
---
# <a name="writing-help-for-powershell-cmdlets"></a>撰寫 PowerShell Cmdlet 的說明

PowerShell Cmdlet 可能很有用，但除非您的說明主題清楚地說明了 Cmdlet 的用途和使用方式，否則 Cmdlet 可能無法使用，或甚至更糟的是，它可能會讓使用者感到不快。 以 XML 為基礎的 Cmdlet 說明檔案格式可增強一致性，但有很大的説明需要更多。

如果您從未撰寫過 Cmdlet 說明，請參閱下列指導方針。 下一節將說明撰寫 Cmdlet 說明主題所需的 XML 架構。 從 [建立 Cmdlet](./how-to-create-the-cmdlet-help-file.md)說明檔開始。 該主題包含最上層 XML 節點的描述。

## <a name="writing-guidelines-for-cmdlet-help"></a>Cmdlet 說明的撰寫指導方針

### <a name="write-well"></a>寫得很好

任何東西都不會取代妥善撰寫的主題。 如果您不是專業作者，請尋找可協助您的寫入器或編輯器。 另一個替代方法是將您的解說文字複製到 Microsoft Word 中，並使用文法和拼寫檢查來改善您的工作。

### <a name="write-simply"></a>單純撰寫

使用簡單的單字和片語。 避免術語。 請考慮許多讀者僅配備外部語言字典和您的說明主題。

### <a name="write-consistently"></a>一致寫入

相關 Cmdlet 的說明應該類似 (例如，1.x 和 x-y) 。 使用標準參數的標準描述，例如 **Force** 和 **InputObject**。  (從核心 Cmdlet 的說明複製這些專案。 ) 使用標準術語。 例如，使用「參數」，而不是「引數」，並使用「Cmdlet」而非「命令」或「命令-let」。

### <a name="start-the-synopsis-with-a-verb"></a>使用動詞開始摘要

摘要欄位會通知使用者 Cmdlet 的功能，而不是它的作用或運作方式。 動詞命令會建立以工作為基礎的語句，以在此 Cmdlet 符合其需求時通知使用者。 使用簡單的動詞命令，例如「get」、「create」和「change」。 避免「設定」，這可以是不清楚的單字，例如「修改」。

### <a name="focus-on-objects"></a>專注于物件

大部分的 "get" Cmdlet 會顯示一些內容，但其主要功能是取得物件。 在您的 [說明] 中，將焦點放在物件上，讓使用者瞭解預設顯示是其中一種，而且可以使用您針對它們所抓取之物件的方法和屬性（以不同方式）。

### <a name="write-detailed-descriptions"></a>寫入詳細描述

簡短列出 Cmdlet 可在詳細描述中進行的所有動作。 如果主要函式是變更某個屬性，但 Cmdlet 可以變更所有屬性，請在詳細的描述中列出這項功能。

### <a name="use-conventional-syntax"></a>使用傳統語法

使用 Windows 和 UNIX 命令列說明常用的標準 Backus-Naur 格式。

### <a name="use-microsoft-net-types-for-parameter-values"></a>使用 Microsoft .NET 類型作為參數值

參數值的預留位置 (在語法和參數描述中) 顯示參數將接受之物件的 .NET Framework 類型。 PowerShell 小組開發了此慣例，以協助使用者瞭解 .NET Framework。

### <a name="write-complete-parameter-descriptions"></a>撰寫完整的參數描述

參數描述必須通知使用者兩件事：參數 (其效果) ，以及必須為參數值輸入的內容。

### <a name="write-practical-examples"></a>撰寫實用範例

這些範例應該會示範如何使用所有參數，但最重要的是示範如何在真實世界的工作中使用此 Cmdlet。 從簡單的範例開始，並撰寫逐漸複雜的範例。 在最後一個範例中，示範如何在管線中使用 Cmdlet。

### <a name="use-the-notes-field"></a>使用附注欄位

使用 [附注] 欄位來說明使用者瞭解 Cmdlet 所需的概念。 您也可以使用附注來協助使用者避免常見的錯誤。 避免 Url 變更。 相反地，請提供使用者字詞來搜尋。

### <a name="test-your-help"></a>測試您的協助

測試您的程式碼，就像測試程式碼一樣。 讓朋友和同事閱讀您的說明內容，並提供意見反應。 您也可以從新聞群組請求意見反應。

## <a name="see-also"></a>另請參閱

 [如何建立 Cmdlet 說明檔案](./how-to-create-the-cmdlet-help-file.md)

 [如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [如何將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)

 [如何新增語法至 Cmdlet 說明主題](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [如何將參數新增至 Cmdlet 說明主題](./how-to-add-parameter-information.md)

 [如何將輸入類型新增至 Cmdlet 說明主題](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [如何新增傳回值至 Cmdlet 說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [如何新增附註至 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [如何新增範例至 Cmdlet 說明主題](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [如何新增相關連結至 Cmdlet 說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
