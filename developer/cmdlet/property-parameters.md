---
title: 屬性參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251416"
---
# <a name="property-parameters"></a>屬性參數

下表列出建議的名稱和屬性參數的功能。

|參數|功能|
|---|---|
|**Count**<br>資料類型：Int32|實作此參數，讓使用者可以指定要處理的物件數目。|
|**描述**<br>資料類型：String|實作此參數，讓使用者可以指定資源的描述。|
|**從**<br>資料類型：String|實作此參數，讓使用者可以指定參考物件，以取得資訊。|
|**Id**<br>資料類型：相依的資源|實作此參數，讓使用者可以指定資源的識別項。|
|**輸入**<br>資料類型：String|實作此參數，讓使用者可以指定輸入的檔案規格。|
|**位置**<br>資料類型：String|實作此參數，讓使用者可以指定資源的位置。|
|**LogName**<br>資料類型：String|實作此參數，讓使用者可以指定要處理，或使用的記錄檔的名稱。|
|**名稱**<br>資料類型：String|實作此參數，讓使用者可以指定資源的名稱。|
|**Output**<br>資料類型：String|實作此參數，讓使用者可以指定輸出檔。|
|**Owner**<br>資料類型：String|實作此參數，讓使用者可以指定資源的擁有者的名稱。|
|**屬性**<br>資料類型：String|實作此參數，讓使用者可以指定的名稱或要使用之屬性的名稱。|
|**Reason**<br>資料類型：String|實作此參數，讓使用者可以指定為什麼這個指令程式會叫用。|
|**Regex**<br>資料類型：SwitchParameter|實作此參數，指定此參數時，會使用規則運算式。 當指定這個參數時，就不會解析萬用字元的字元。|
|**速度**<br>資料類型：Int32|實作此參數，讓使用者可以指定的傳輸速率。 使用者會將此參數設定之資源的速度。|
|**狀態**<br>資料類型：關鍵字陣列|實作此參數，讓使用者可以指定的狀態，例如 KEYDOWN 名稱。|
|**值**<br>資料類型：物件|實作此參數，讓使用者可以指定要提供給此 cmdlet 的值。|
|**Version** (版本)<br>資料類型：String|實作此參數，讓使用者可以指定屬性的版本。|

## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
