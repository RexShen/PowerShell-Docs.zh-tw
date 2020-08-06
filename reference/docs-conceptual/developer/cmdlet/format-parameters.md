---
title: 格式參數 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8e031f62aa8bcb0e9d5b900b2eace7187b1f3dd
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784277"
---
# <a name="format-parameters"></a>格式參數

下表列出用來格式化或產生資料之參數的建議名稱和功能。

|參數|功能|
|---|---|
|**一旦**<br>資料類型：關鍵字|執行此參數以指定 Cmdlet 輸出格式。 例如，可能的值可以是文字或腳本。|
|**二進位**<br>資料類型： SwitchParameter|執行這個參數，以指出 Cmdlet 會處理二進位值。|
|**編碼**<br>資料類型：關鍵字|執行此參數來指定支援的編碼類型。 例如，可能的值為 ASCII、UTF8、Unicode、UTF7、BigEndianUnicode、Byte 和 String。|
|**換**<br>資料類型： SwitchParameter|執行此參數，以便在指定參數時支援分行符號。|
|**ShortName**<br>資料類型： SwitchParameter|請執行此參數，以便在指定參數時支援簡短名稱。|
|**寬度**<br>資料類型： Int32|執行此參數，讓使用者可以指定輸出裝置的寬度。|
|**包裝**<br>資料類型： SwitchParameter|執行此參數，以便在指定參數時支援文字換行。|
## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
