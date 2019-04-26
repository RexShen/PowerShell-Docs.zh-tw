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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075183"
---
# <a name="activity-parameters"></a>活動參數

下表列出建議的名稱和活動參數的功能。

|參數|功能|
|---|---|
|**Append**<br>資料類型：SwitchParameter|實作此參數，讓使用者可以將內容新增至資源的結尾時指定此參數。|
|**CaseSensitive**<br>資料類型：SwitchParameter|讓使用者可以要求區分大小寫，在指定的參數時，請實作這個參數。|
|**命令**<br>資料類型：String|實作此參數，讓使用者可以指定要執行的命令字串。|
|**CompatibleVersion**<br>資料類型：System.Version 物件|實作此參數，讓使用者可以指定指令程式必須是為了與舊版的相容性與相容的語意。|
|**壓縮**<br>資料類型：SwitchParameter|實作此參數，指定此參數時，使用資料壓縮。|
|**壓縮**<br>資料類型：關鍵字|實作此參數，讓使用者可以指定要用於 資料壓縮演算法。|
|**連續**<br>資料類型：SwitchParameter|實作此參數，讓使用者終止此 cmdlet 時指定此參數之前不會處理資料。 如果未指定參數，cmdlet 就會處理預先定義的資料量，並終止作業。|
|**建立**<br>資料類型：SwitchParameter|實作此參數，以指出已建立的資源，是否其中一個不存在時指定此參數。|
|**Delete**<br>資料類型：SwitchParameter|實作此參數，此 cmdlet 時指定此參數完成其作業時，會刪除資源。|
|**清空**<br>資料類型：SwitchParameter|實作此參數，以指出時指定此參數，cmdlet 會處理新資料之前，會處理未完成的工作項目。 如果未指定參數，就會立即處理的工作項目。|
|**清除**<br>資料類型：Int32|實作此參數，讓使用者可以指定於刪除之前，會清除資源的次數。|
|**ErrorLevel**<br>資料類型：Int32|實作此參數，讓使用者可以指定要報告的錯誤層級。|
|**Exclude**<br>資料類型：String[]|實作此參數，讓使用者可以從活動中的項目排除。 如需如何使用輸入篩選器的詳細資訊，請參閱[輸入篩選參數](input-filter-parameters.md)。|
|**篩選器**<br>資料類型：關鍵字|實作此參數，讓使用者可以指定選取的資源，用來執行 cmdlet 動作的篩選。 如需如何使用輸入篩選器的詳細資訊，請參閱[輸入篩選參數](./input-filter-parameters.md)。|
|**Follow**<br>資料類型：SwitchParameter|實作此參數，指定此參數時，會追蹤進度。|
|**Force**<br>資料類型：SwitchParameter|實作此參數，以指出使用者可以執行的動作，即使指定此參數時會遇到的限制。 參數不允許遭到入侵的安全性。 比方說，此參數可讓使用者覆寫唯讀檔案。|
|**Include**<br>資料類型：String[]|實作此參數，讓使用者可以在活動中包含的項目。 如需如何使用輸入篩選器的詳細資訊，請參閱[輸入篩選參數](input-filter-parameters.md)。|
|**增量**<br>資料類型：SwitchParameter|實作此參數，以指定為參數指定當處理以累加方式執行。 比方說，此參數可讓使用者執行備份的檔案，只有自上次備份的增量備份。|
|**InputObject**<br>資料類型：物件|此 cmdlet 會從其他 cmdlet 的輸入時，請實作這個參數。 當您定義**InputObject**參數，一定要指定**ValueFromPipeline**關鍵字宣告**參數**屬性。 如需使用 輸入篩選器的詳細資訊，請參閱 <<c0> [ 輸入篩選參數](./input-filter-parameters.md)。|
|**插入**<br>資料類型：SwitchParameter|實作此參數，cmdlet 會插入項目時指定此參數。|
|**Interactive**<br>資料類型：SwitchParameter|實作此參數，cmdlet 適用於以互動方式與使用者時指定此參數。|
|**Interval**<br>資料類型：HashTable|實作此參數，讓使用者可以指定關鍵字的雜湊表，其中包含的值。 下列範例示範的範例值**間隔**參數： `-interval @{ResumeScan=15; Retry=3}`。|
|**Log**<br>資料類型：SwitchParameter|實作此參數的稽核動作的 cmdlet 時指定此參數。|
|**NoClobber**<br>資料類型：SwitchParameter|實作此參數，讓資源將不會覆寫時指定此參數。 此參數通常會套用至 cmdlet，建立新的物件，以便可以防止以相同名稱覆寫現有的物件。|
|**通知**<br>資料類型：SwitchParameter|實作此參數，將會通知使用者，指定此參數時，活動已完成。|
|**NotifyAddress**<br>資料類型：電子郵件地址|實作此參數，讓使用者可以指定用來傳送通知電子郵件地址時**通知**指定參數。|
|**Overwrite**<br>資料類型：SwitchParameter|實作此參數，此 cmdlet 在指定的參數時，會覆寫任何現有的資料。|
|**Prompt**<br>資料類型：String|實作此參數，讓使用者可以指定此 cmdlet 的提示。|
|**Quiet**<br>資料類型：SwitchParameter|實作此參數，cmdlet 會隱藏其動作期間使用者意見反應時指定此參數。|
|**Recurse**<br>資料類型：SwitchParameter|實作此參數，cmdlet 以遞迴方式會執行其動作的資源時指定此參數。|
|**Repair**<br>資料類型：SwitchParameter|實作此參數，cmdlet 將會嘗試修正從中斷狀態的項目時指定此參數。|
|**RepairString**<br>資料類型：String|實作此參數，讓使用者可以指定時要使用的字串**修復**指定參數。|
|**Retry**<br>資料類型：Int32|實作此參數，讓使用者可以指定此 cmdlet 會嘗試動作的次數。|
|**Select**<br>資料類型：關鍵字陣列|實作此參數，讓使用者可以指定項目類型的陣列。|
|**Stream**<br>資料類型：SwitchParameter|讓使用者可以串流處理管線的多個輸出物件，指定此參數時，請實作這個參數。|
|**Strict**<br>資料類型：SwitchParameter|實作此參數，指定此參數時，將會處理為終止錯誤的所有錯誤。|
|**TempLocation**<br>資料類型：String|實作此參數，讓使用者可以指定指令程式作業期間所使用的暫存資料的位置。|
|**逾時**<br>資料類型：Int32|實作此參數，讓使用者可以指定逾時間隔 （以毫秒為單位）。|
|**截斷**<br>資料類型：SwitchParameter|實作此參數，cmdlet 就會截斷其動作時指定此參數。 如果未指定參數，此 cmdlet 會執行其他動作。|
|**請確認**<br>資料類型：SwitchParameter|實作此參數，cmdlet 會測試以判斷是否發生動作時指定此參數。|
|**等候**<br>資料類型：SwitchParameter|實作此參數，cmdlet 會等候使用者輸入才能繼續作業時指定此參數。
|**WaitTime**<br>資料類型：Int32|實作此參數，讓使用者可以指定的持續時間 （以秒為單位），此 cmdlet 會等待使用者輸入時**等候**指定參數。|

## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
