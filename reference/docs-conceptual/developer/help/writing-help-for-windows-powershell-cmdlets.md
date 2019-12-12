---
title: 撰寫 PowerShell Cmdlet 的說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361067"
---
# <a name="writing-help-for-powershell-cmdlets"></a>撰寫 PowerShell Cmdlet 的說明

PowerShell Cmdlet 可能很實用，但除非您的說明主題清楚說明了 Cmdlet 的用途和使用方式，否則 Cmdlet 可能無法使用，或甚至更糟的是，可能會讓使用者感到不快。
以 XML 為基礎的 Cmdlet 說明檔案格式可增強一致性，但有很大的説明需要更多功能。

如果您從未撰寫過 Cmdlet 說明，請參閱下列指導方針。
下一節將說明撰寫 Cmdlet 說明主題所需的 XML 架構。
從[建立 Cmdlet](./how-to-create-the-cmdlet-help-file.md)說明檔開始。
該主題包含最上層 XML 節點的描述。

## <a name="writing-guidelines-for-cmdlet-help"></a>撰寫 Cmdlet 說明的指導方針

### <a name="write-well"></a>寫得好
任何內容都不會取代撰寫完善的主題。
如果您不是專業作者，請尋找可協助您的作者或編輯器。
另一種替代方式是將解說文字複製到 Microsoft Word，並使用文法和拼寫檢查來改善您的工作。

### <a name="write-simply"></a>簡單撰寫
使用簡單的字組和片語。
避免產生術語。
請考慮許多讀者僅配備外部語言字典和您的說明主題。

### <a name="write-consistently"></a>一致寫入
相關 Cmdlet 的說明應該類似（例如，get-x 和 set-x）。
使用標準參數的標準描述，例如**Force**和**InputObject**。
（從 [說明] 複製核心 Cmdlet）。使用標準詞彙。
例如，使用「參數」，而不是「引數」，並使用「Cmdlet」而不是「命令」或「命令-let」。

### <a name="start-the-synopsis-with-a-verb"></a>使用動詞來啟動概要
[摘要] 欄位會通知使用者 Cmdlet 的用途，而不是它的作用或其運作方式。
動詞建立以工作為基礎的語句，通知使用者此 Cmdlet 是否符合其需求。
使用簡單動詞，例如「get」、「create」和「change」。
請避免「設定」，這可能是不清楚的單字，例如「修改」。

### <a name="focus-on-objects"></a>專注于物件
大部分的 "get" Cmdlet 會顯示某個專案，但其主要功能是取得物件。
在您的 [說明] 中，將焦點放在物件上，讓使用者瞭解預設顯示是其中一種，而且它們可以使用您以不同方式為其取得之物件的方法和屬性。

### <a name="write-detailed-descriptions"></a>撰寫詳細描述
簡要列出 Cmdlet 在詳細描述中可執行檔所有動作。
如果 main 函式是要變更一個屬性，但 Cmdlet 可以變更所有屬性，請在詳細的描述中列出此項。

### <a name="use-conventional-syntax"></a>使用傳統語法
使用適用于 Windows 和 UNIX 命令列說明的標準巴克斯-Backus-naur 格式。

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>使用 Microsoft .NET Framework 類型做為參數值
參數值的預留位置（在語法和參數描述中）會顯示參數將接受之物件的 .NET Framework 類型。
PowerShell 小組會開發此慣例，協助使用者瞭解 .NET Framework 的相關資訊。

### <a name="write-complete-parameter-descriptions"></a>撰寫完整的參數描述
參數描述必須通知使用者兩個事項：參數的作用（其效果），以及它們必須為參數值輸入的內容。

### <a name="write-practical-examples"></a>撰寫實用的範例
範例應該會顯示如何使用所有參數，但最重要的是示範如何在真實世界的工作中使用此 Cmdlet。
從簡單的範例開始，並撰寫日益複雜的範例。
在最後一個範例中，示範如何在管線中使用 Cmdlet。

### <a name="use-the-notes-field"></a>使用 [附注] 欄位
使用 [附注] 欄位來說明使用者必須瞭解 Cmdlet 的概念。
您也可以使用記事來協助使用者避免常見的錯誤。
避免 Url 變更。
相反地，請提供要搜尋的使用者字詞。

### <a name="test-your-help"></a>測試您的協助
測試此協助，就像測試程式碼一樣。
讓朋友和同事閱讀您的說明內容並提供意見反應。
您也可以從新聞群組要求意見反應。

## <a name="see-also"></a>另請參閱

 [如何建立 Cmdlet 說明檔](./how-to-create-the-cmdlet-help-file.md)

 [如何將 Cmdlet 名稱和概要新增至 Cmdlet 說明主題](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [如何將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)

 [如何將語法新增至 Cmdlet 說明主題](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [如何將參數新增至 Cmdlet 說明主題](./how-to-add-parameter-information.md)

 [如何將輸入類型新增至 Cmdlet 說明主題](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [如何將傳回值新增至 Cmdlet 說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [如何將附注新增至 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [如何將範例新增至 Cmdlet 說明主題](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [如何將相關連結新增至 Cmdlet 說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)