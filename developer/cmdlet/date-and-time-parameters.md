---
title: 日期和時間參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251348"
---
# <a name="date-and-time-parameters"></a>日期和時間參數

下表列出建議的名稱和功能，以便處理日期和時間資訊的參數。 日期和時間參數通常用來記錄項目建立或存取時。

|參數|功能|
|---|---|
|**Accessed**<br>資料類型：SwitchParameter|實作此參數，讓它時指定此 cmdlet 會作用於已存取的資源為基礎的日期和時間所指定**之前**並**之後**參數。 如果指定此參數， **Created**和**Modified**參數必須是未指定。|
|**After**<br>資料類型：DateTime|實作此參數，以指定的日期和時間之後，使用此 cmdlet。 針對**之後**參數來運作，此 cmdlet 也必須**存取**，**建立**，或**修改**參數。 而且，該參數必須設定為 **，則為 true**呼叫 cmdlet 時。|
|**之前**<br>資料類型：DateTime|實作此參數，以指定的日期和時間之前使用此 cmdlet。 針對**之前**參數來運作，此 cmdlet 也必須**存取**，**建立**，或**修改**參數。 而且，該參數必須設定為 **，則為 true**呼叫 cmdlet 時。|
|**建立**<br>資料類型：SwitchParameter|實作此參數，讓它時指定此 cmdlet 會作用於已建立的資源為基礎的日期和時間所指定**之前**並**之後**參數。 如果指定這個參數，則**存取**並**Modified**不得指定參數。|
|**Exact**<br>資料類型：SwitchParameter|實作此參數，它會指定資源一詞時必須的資源名稱完全相符。 當未指定參數名稱與資源的詞彙不需要完全相符。|
|**修改**<br>資料類型：DateTime|實作此參數，讓它時指定此 cmdlet 將操作的已變更的資源為基礎的日期和時間所指定**之前**並**之後**參數。 如果指定這個參數，則**存取**並**建立**不得指定參數。|
## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
