---
title: 適用於 PowerShell Cmdlet 撰寫說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083156"
---
# <a name="writing-help-for-powershell-cmdlets"></a>適用於 PowerShell Cmdlet 撰寫說明

PowerShell cmdlet 會很有用，但除非您的 [說明] 主題清楚地說明 cmdlet 的功能，以及如何使用它，此 cmdlet 可能會使用或更糟的是，它可能會讓使用者不耐煩。
XML 型 cmdlet 說明檔格式強化一致性，但大的幫助需要更多。

如果您從未撰寫 cmdlet 說明，請檢閱下列指導方針。
撰寫 cmdlet 說明主題所需的 XML 結構描述是由下列一節所述。
開頭[建立 Cmdlet 說明檔](./how-to-create-the-cmdlet-help-file.md)。
該主題都包含最上層的 XML 節點的描述。

## <a name="writing-guidelines-for-cmdlet-help"></a>撰寫 Cmdlet 說明的指導方針

### <a name="write-well"></a>撰寫
不會取代編寫完善的主題。
如果您不是專業的寫入器，尋找可協助您讓寫入器或編輯器。
另一個替代方式是複製到 Microsoft Word 的說明文字，並使用文法與拼字檢查來改善您的工作。

### <a name="write-simply"></a>只要撰寫
使用簡單的單字和片語。
避免術語。
請考慮許多讀者便有能力只使用外國語言字典和說明主題。

### <a name="write-consistently"></a>以一致的方式寫入
說明相關的 cmdlet 應該類似於 （例如 get-x 和 set-x）。
標準的參數，使用標準的描述，例如**Force**並**InputObject**。
（複製它們的說明對核心 cmdlet）。使用標準的詞彙。
例如，使用 「 參數 」，不 「 引數 」，並使用 「 cmdlet 」 不 「 命令 」 或者"cmdlet。 」

### <a name="start-the-synopsis-with-a-verb"></a>使用動詞啟動概要
此指令程式不會它是什麼或它的運作方式，概要欄位就會通知使用者。
動詞命令建立一個以工作為基礎的陳述式，會通知使用者，如果此 cmdlet 會符合其需求。
使用簡單的動詞命令，例如 「 get 」、 「 建立 」 和 「 變更 」。
避免 「 set 」，它可以是含糊不清，和 「 修改 」 之類的複雜的單字。

### <a name="focus-on-objects"></a>專注於物件
大部分 「 取得 」 cmdlet 顯示項目，但其主要功能是以取得的物件。
在您的協助，著重於物件，好讓使用者瞭解的預設顯示是任一種，以及他們可以使用的方法和您以不同的方式擷取這些物件的屬性。

### <a name="write-detailed-descriptions"></a>寫入詳細的描述
簡短列出所有的 cmdlet 可以執行作業的詳細說明中的項目。
如果 main 函式來變更一個屬性，但 cmdlet 可以變更所有屬性，請將這列入詳細的描述。

### <a name="use-conventional-syntax"></a>使用傳統的語法
使用標準的巴克斯格式是很常見的 Windows 和 UNIX 命令列說明。

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>使用 Microsoft.NET Framework 類型的參數值
（中的語法和參數的描述） 的參數值的預留位置，顯示.NET Framework 類型的參數會接受物件。
PowerShell 小組開發此慣例，可協助教導使用者有關.NET Framework。

### <a name="write-complete-parameter-descriptions"></a>撰寫完整的參數描述
參數說明必須通知使用者兩件事： 何種參數的用途 （其作用），以及他們必須輸入的參數值。

### <a name="write-practical-examples"></a>撰寫實用的範例
範例應該會顯示如何使用的所有參數，但最重要的事是要說明如何在真實世界工作中使用此 cmdlet。
簡單範例開始，寫入日益複雜的範例。
在最後一個範例中，示範如何在管線中使用此 cmdlet。

### <a name="use-the-notes-field"></a>使用附註 欄位
使用附註 欄位來解釋使用者需要了解此 cmdlet 的概念。
您也可以使用資訊以協助使用者避免常見的錯誤。
變更時，請避免 Url。
相反地，提供要搜尋的使用者條款。

### <a name="test-your-help"></a>測試您的協助
就像您測試您的程式碼，請測試說明。
朋友和同事讀取您的說明內容，並提供意見反應。
您也可以請求意見反應的新聞群組。

## <a name="see-also"></a>另請參閱

 [如何建立 Cmdlet 說明檔](./how-to-create-the-cmdlet-help-file.md)

 [如何將 Cmdlet 說明主題的概要與 Cmdlet 名稱](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [如何將詳細的說明新增至 Cmdlet 的說明主題](./how-to-add-a-cmdlet-description.md)

 [如何將 Cmdlet 說明主題中的語法](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [如何將參數新增至 Cmdlet 的說明主題](./how-to-add-parameter-information.md)

 [如何將輸入類型新增至 Cmdlet 說明主題](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [如何將傳回的值新增至 Cmdlet 的說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [如何新增備忘稿 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [如何新增 Cmdlet 說明主題的範例](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [如何將相關的連結新增至 Cmdlet 的說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)