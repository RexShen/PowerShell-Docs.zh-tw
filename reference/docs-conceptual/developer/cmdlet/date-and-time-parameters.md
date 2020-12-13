---
ms.date: 09/13/2016
ms.topic: reference
title: 日期和時間參數
description: 日期和時間參數
ms.openlocfilehash: 2f73d16ca8261ebc4ca8d2c18aff4176d7d7314c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653197"
---
# <a name="date-and-time-parameters"></a>日期和時間參數

下表列出處理日期和時間資訊之參數的建議名稱和功能。 日期和時間參數通常用來記錄建立或存取某個事物的時機。

|參數|功能|
|---|---|
|**訪問**<br>資料類型： SwitchParameter|請執行此參數，如此一來，當您指定此參數時，Cmdlet 將會根據 **之前** 和 **之後** 參數所指定的日期和時間來操作已存取的資源。 如果指定了此參數，就必須指定 **建立** 和 **修改** 的參數。|
|**更新後**<br>資料類型： DateTime|執行此參數來指定使用 Cmdlet 的日期和時間。 若要讓 **After** 參數運作，Cmdlet 也必須有 **存取**、 **建立** 或 **修改** 的參數。 而且，呼叫 Cmdlet 時，該參數必須設定為 **true** 。|
|**更新前**<br>資料類型： DateTime|執行此參數來指定使用指令程式之前的日期和時間。 若要讓 **Before** 參數運作，Cmdlet 也必須有 **存取**、 **建立** 或 **修改** 的參數。 而且，呼叫 Cmdlet 時，該參數必須設定為 **true** 。|
|**建立時間**<br>資料類型： SwitchParameter|請執行此參數，如此一來，當您指定此參數時，Cmdlet 將會根據 **之前** 和 **之後** 參數所指定的日期和時間，在建立的資源上運作。 如果指定了此參數，就不能指定 **存取** 的和 **修改過** 的參數。|
|**精確**<br>資料類型： SwitchParameter|請執行此參數，以在指定資源字詞時，完全符合資源名稱。 當未指定參數時，資源字詞和名稱不需要完全相符。|
|**修改日期**<br>資料類型： DateTime|執行此參數，如此一來，當您指定此參數時，Cmdlet 會在已根據 **之前** 和 **之後** 參數所指定的日期和時間變更的資源上運作。 如果指定這個參數，則不能指定所 **存取** 和 **建立** 的參數。|
## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
