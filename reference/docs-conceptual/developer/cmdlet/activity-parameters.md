---
title: 活動參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364637"
---
# <a name="activity-parameters"></a>活動參數

下表列出活動參數的建議名稱和功能。

|參數|功能|
|---|---|
|**附加**<br>資料類型： SwitchParameter|執行此參數，讓使用者可以在指定參數時，將內容新增至資源的結尾。|
|**CaseSensitive**<br>資料類型： SwitchParameter|請執行此參數，以便在指定參數時，使用者可以要求區分大小寫。|
|**Command**<br>資料類型：字串|執行此參數，讓使用者可以指定要執行的命令字串。|
|**CompatibleVersion**<br>資料類型： System.object 物件|執行此參數，讓使用者可以指定 Cmdlet 必須相容的語義，以與舊版相容。|
|**壓縮**<br>資料類型： SwitchParameter|執行此參數，以便在指定參數時使用資料壓縮。|
|**壓縮**<br>資料類型：關鍵字|執行此參數，讓使用者可以指定要用於資料壓縮的演算法。|
|**系列**<br>資料類型： SwitchParameter|執行此參數，以便在使用者于指定參數時終止 Cmdlet 之後，才處理資料。 如果未指定參數，此 Cmdlet 會處理預先定義的資料量，然後終止作業。|
|**建立**<br>資料類型： SwitchParameter|執行這個參數，以指出當指定了參數時，如果資源尚未存在，就會建立該資源。|
|**刪除**<br>資料類型： SwitchParameter|執行此參數，以便在 Cmdlet 已在指定參數時完成其作業時，刪除資源。|
|**弱電**<br>資料類型： SwitchParameter|執行這個參數，表示在指定參數時，在 Cmdlet 處理新資料之前，會處理未完成的工作專案。 如果未指定參數，則會立即處理工作專案。|
|**Erase**<br>資料類型： Int32|請執行這個參數，讓使用者可以指定刪除資源之前，將其清除的次數。|
|**ErrorLevel**<br>資料類型： Int32|執行此參數，讓使用者可以指定要報告的錯誤層級。|
|**排除**<br>資料類型： String []|執行此參數，讓使用者可以從活動中排除某些專案。 如需如何使用輸入篩選器的詳細資訊，請參閱[輸入篩選參數](input-filter-parameters.md)。|
|**篩選器**<br>資料類型：關鍵字|執行此參數，讓使用者可以指定篩選準則，以選取要在其上執行 Cmdlet 動作的資源。 如需如何使用輸入篩選器的詳細資訊，請參閱[輸入篩選參數](./input-filter-parameters.md)。|
|**接**<br>資料類型： SwitchParameter|執行此參數，以便在指定參數時追蹤進度。|
|**使**<br>資料類型： SwitchParameter|執行這個參數，以指出即使在指定參數時遇到限制，使用者也可以執行動作。 參數不允許洩露安全性。 例如，此參數可讓使用者覆寫唯讀檔案。|
|**包含**<br>資料類型： String []|執行此參數，讓使用者可以包含活動中的某個專案。 如需如何使用輸入篩選器的詳細資訊，請參閱[輸入篩選參數](input-filter-parameters.md)。|
|**累加**<br>資料類型： SwitchParameter|執行這個參數，表示當指定參數時，會以累加方式執行處理。 例如，此參數可讓使用者執行增量備份，只備份自從上次備份後的檔。|
|**InputObject**<br>資料類型：物件|當 Cmdlet 接受來自其他 Cmdlet 的輸入時，請執行此參數。 當您定義**InputObject**參數時，請一律在宣告**參數**屬性時指定**ValueFromPipeline**關鍵字。 如需有關使用輸入篩選器的詳細資訊，請參閱[輸入篩選參數](./input-filter-parameters.md)。|
|**Insert**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時插入專案。|
|**Interactive**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時與使用者互動。|
|**間隔**<br>資料類型： HashTable|執行此參數，讓使用者可以指定包含值的關鍵字雜湊表。 下列範例會顯示**Interval**參數的範例值： `-interval @{ResumeScan=15; Retry=3}`。|
|**Log**<br>資料類型： SwitchParameter|當指定參數時，請執行此參數來審核 Cmdlet 的動作。|
|**NoClobber**<br>資料類型： SwitchParameter|執行此參數，如此一來，當指定參數時，就不會覆寫資源。 這個參數通常會套用至建立新物件的 Cmdlet，讓它們可以防止覆寫具有相同名稱的現有物件。|
|**通知**<br>資料類型： SwitchParameter|執行此參數，以便在指定參數時，通知使用者活動已完成。|
|**NotifyAddress**<br>資料類型：電子郵件地址|執行此參數，讓使用者可以在指定**Notify**參數時，指定用來傳送通知的電子郵件地址。|
|**Overwrite**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時覆寫任何現有的資料。|
|**提示**<br>資料類型：字串|執行此參數，讓使用者可以指定 Cmdlet 的提示。|
|**無訊息**<br>資料類型： SwitchParameter|執行此參數，以在指定參數時，讓 Cmdlet 隱藏使用者對其動作的意見反應。|
|**遞迴**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時，以遞迴方式對資源執行其動作。|
|**Repair**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 會在指定參數時嘗試從中斷狀態更正某些專案。|
|**RepairString**<br>資料類型：字串|執行此參數，讓使用者可以指定要在指定**Repair**參數時使用的字串。|
|**重試**<br>資料類型： Int32|請執行此參數，讓使用者可以指定 Cmdlet 嘗試執行動作的次數。|
|**選取**<br>資料類型：關鍵字陣列|執行此參數，讓使用者可以指定專案類型的陣列。|
|**資料流**<br>資料類型： SwitchParameter|執行此參數，讓使用者可以在指定參數時，透過管線串流多個輸出物件。|
|**Strict**<br>資料類型： SwitchParameter|執行此參數，以便在指定參數時，將所有錯誤處理為終止錯誤。|
|**TempLocation**<br>資料類型：字串|執行此參數，讓使用者可以指定在 Cmdlet 作業期間使用的暫存資料位置。|
|**逾時**<br>資料類型： Int32|執行此參數，讓使用者可以指定逾時間隔（以毫秒為單位）。|
|**各**<br>資料類型： SwitchParameter|執行此參數，以便在指定參數時，Cmdlet 會截斷其動作。 如果未指定參數，此 Cmdlet 會執行另一個動作。|
|**驗證**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 會進行測試，以判斷指定參數時是否已發生動作。|
|**Wait**<br>資料類型： SwitchParameter|執行此參數，讓 Cmdlet 在指定參數時繼續等候使用者輸入。
|**WaitTime**<br>資料類型： Int32|執行此參數，讓使用者可以指定當指定**wait**參數時，Cmdlet 將等候使用者輸入的持續時間（以秒為單位）。|

## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
