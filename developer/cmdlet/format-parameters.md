---
title: 設定參數的格式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068108"
---
# <a name="format-parameters"></a>格式參數

下表列出建議的名稱和參數，可用來格式化，或產生資料的功能。

|參數|功能|
|---|---|
|**As**<br>資料類型：關鍵字|實作這個參數來指定 cmdlet 的輸出格式。 例如，文字或指令碼，可能是可能的值。|
|**二進位檔**<br>資料類型：SwitchParameter|實作此參數，以指出此 cmdlet 會處理二進位值。|
|**編碼方式**<br>資料類型：關鍵字|實作這個參數來指定支援的編碼類型。 例如，ASCII、 UTF8、 Unicode、 UTF7、 BigEndianUnicode、 位元組、 和字串，可能是可能的值。|
|**NewLine**<br>資料類型：SwitchParameter|實作此參數，參數會指定時，才支援新行字元。|
|**ShortName**<br>資料類型：SwitchParameter|實作此參數，參數會指定時，才支援短檔名。|
|**Width**<br>資料類型：Int32|實作此參數，讓使用者可以指定輸出裝置的寬度。|
|**Wrap**<br>資料類型：SwitchParameter|實作此參數，指定此參數時，支援文字換行。|
## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
