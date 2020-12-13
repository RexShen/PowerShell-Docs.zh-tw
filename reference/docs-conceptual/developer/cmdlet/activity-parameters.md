---
ms.date: 09/13/2016
ms.topic: reference
title: 活動參數
description: 活動參數
ms.openlocfilehash: 241fb8a7796d1c9dc10e8410d6daef4db70c9b4e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653708"
---
# <a name="activity-parameters"></a>活動參數

下表列出活動參數的建議名稱和功能。

|參數|功能|
|---|---|
|**Append**<br>資料類型： SwitchParameter|執行此參數，讓使用者可以在指定參數時，將內容新增至資源的結尾。|
|**CaseSensitive**<br>資料類型： SwitchParameter|執行此參數，讓使用者在指定參數時，可以要求區分大小寫。|
|**命令**<br>資料類型：字串|執行此參數，讓使用者可以指定要執行的命令字串。|
|**CompatibleVersion**<br>資料類型： System.object 物件|請執行此參數，讓使用者可以指定 Cmdlet 必須與舊版相容的語法。|
|**壓縮**<br>資料類型： SwitchParameter|請執行此參數，以便在指定參數時使用資料壓縮。|
|**壓縮**<br>資料類型：關鍵字|執行此參數，讓使用者可以指定要用於資料壓縮的演算法。|
|**連續**<br>資料類型： SwitchParameter|在指定參數時，請執行此參數以處理資料，直到使用者終止 Cmdlet 為止。 如果未指定參數，Cmdlet 會處理預先定義的資料量，然後終止作業。|
|**建立**<br>資料類型： SwitchParameter|如果指定了參數，則請執行此參數來表示建立的資源（如果不存在的話）。|
|**刪除**<br>資料類型： SwitchParameter|執行此參數，以便當 Cmdlet 在指定參數時完成其作業時，就會刪除資源。|
|**清空**<br>資料類型： SwitchParameter|執行這個參數，表示在指定參數時，會先處理未處理的工作專案，然後再處理新的資料。 如果未指定參數，則會立即處理工作專案。|
|**擦 除**<br>資料類型： Int32|執行此參數，讓使用者可以指定刪除資源之前，要清除資源的次數。|
|**ErrorLevel**<br>資料類型： Int32|執行這個參數，讓使用者可以指定要報告的錯誤層級。|
|**排除**<br>資料類型： String []|執行此參數，讓使用者可以從活動中排除某個內容。 如需如何使用輸入篩選的詳細資訊，請參閱 [輸入篩選參數](input-filter-parameters.md)。|
|**Filter**<br>資料類型：關鍵字|執行此參數，讓使用者可以指定篩選器，以選取要在其上執行 Cmdlet 動作的資源。 如需如何使用輸入篩選的詳細資訊，請參閱 [輸入篩選參數](./input-filter-parameters.md)。|
|**追隨**<br>資料類型： SwitchParameter|執行這個參數，以便在指定參數時追蹤進度。|
|**力**<br>資料類型： SwitchParameter|您可以執行這個參數，指出即使在指定參數時遇到限制，使用者仍可執行動作。 參數不允許洩漏安全性。 例如，此參數可讓使用者覆寫唯讀檔案。|
|**包括**<br>資料類型： String []|請執行此參數，讓使用者可以在活動中包含某個東西。 如需如何使用輸入篩選的詳細資訊，請參閱 [輸入篩選參數](input-filter-parameters.md)。|
|**增量**<br>資料類型： SwitchParameter|執行這個參數，表示在指定參數時，會以累加方式執行處理。 例如，此參數可讓使用者執行增量備份，只備份自上次備份後的檔。|
|**InputObject**<br>資料類型：物件|當 Cmdlet 接受來自其他 Cmdlet 的輸入時，請執行此參數。 當您定義 **InputObject** 參數時，請一律在宣告 **參數** 屬性時指定 **ValueFromPipeline** 關鍵字。 如需使用輸入篩選器的詳細資訊，請參閱 [輸入篩選參數](./input-filter-parameters.md)。|
|**插入**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時插入專案。|
|**互動式**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時以互動方式與使用者互動。|
|**間隔**<br>資料類型：雜湊表|執行這個參數，讓使用者可以指定包含值之關鍵字的雜湊表。 下列範例顯示 **Interval** 參數的範例值： `-interval @{ResumeScan=15; Retry=3}` 。|
|**Log**<br>資料類型： SwitchParameter|當指定參數時，請執行此參數來審核 Cmdlet 的動作。|
|**NoClobber**<br>資料類型： SwitchParameter|請執行此參數，如此一來，當指定參數時，就不會覆寫資源。 此參數通常會套用至建立新物件的 Cmdlet，以便防止覆寫具有相同名稱的現有物件。|
|**通知**<br>資料類型： SwitchParameter|請執行此參數，如此一來，當指定參數時，使用者就會收到活動已完成的通知。|
|**NotifyAddress**<br>資料類型：電子郵件地址|執行此參數，讓使用者可以在指定 **Notify** 參數時，指定用來傳送通知的電子郵件地址。|
|**Overwrite**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時覆寫任何現有的資料。|
|**提示**<br>資料類型：字串|執行此參數，讓使用者可以指定 Cmdlet 的提示。|
|**安靜**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時，隱藏使用者的意見反應。|
|**遞迴**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時，以遞迴方式在資源上執行其動作。|
|**修復**<br>資料類型： SwitchParameter|請執行此參數，如此一來，當指定參數時，Cmdlet 會嘗試更正損毀狀態中的某些內容。|
|**RepairString**<br>資料類型：字串|執行此參數，讓使用者可以指定要在指定 **Repair** 參數時使用的字串。|
|**重試**<br>資料類型： Int32|請執行此參數，讓使用者可以指定 Cmdlet 將嘗試執行動作的次數。|
|**選取**<br>資料類型：關鍵字陣列|執行這個參數，讓使用者可以指定專案類型的陣列。|
|**資料流**<br>資料類型： SwitchParameter|執行此參數，讓使用者可以在指定參數時，透過管線串流多個輸出物件。|
|**嚴格**<br>資料類型： SwitchParameter|執行這個參數，以便在指定參數時將所有錯誤處理為終止錯誤。|
|**TempLocation**<br>資料類型：字串|請執行此參數，讓使用者可以指定在 Cmdlet 操作期間使用的暫存資料位置。|
|**逾時**<br>資料類型： Int32|執行此參數，讓使用者可以指定逾時間隔，以毫秒為單位來 () 。|
|**截斷**<br>資料類型： SwitchParameter|您可以執行此參數，讓 Cmdlet 在指定參數時截斷其動作。 如果未指定參數，則 Cmdlet 會執行另一個動作。|
|**Verify**<br>資料類型： SwitchParameter|您可以執行此參數，以在指定參數時，測試是否發生動作。|
|**等候**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時繼續等候使用者輸入。
|**等候時間**<br>資料類型： Int32|請執行此參數，讓使用者可以指定持續時間 (秒) ，當指定 **wait** 參數時，Cmdlet 會等候使用者輸入。|

## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
