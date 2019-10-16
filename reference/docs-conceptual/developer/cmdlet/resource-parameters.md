---
title: 資源參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369507"
---
# <a name="resource-parameters"></a>資源參數

下表列出資源參數的建議名稱和功能。 對於這些參數，資源可以是包含 Cmdlet 類別的元件，或是執行 Cmdlet 的主應用程式。

|參數|功能|
|---|---|
|**應用程式**<br>資料類型：字串|執行此參數，讓使用者可以指定應用程式。|
|**Assembly**<br>資料類型：字串|執行此參數，讓使用者可以指定元件。|
|**特性**<br>資料類型：字串|執行此參數，讓使用者可以指定屬性。|
|**課堂**<br>資料類型：字串|執行此參數，讓使用者可以指定 Microsoft .NET Framework 類別。|
|**該群**<br>資料類型：字串|執行此參數，讓使用者可以指定叢集。|
|**區域**<br>資料類型：字串|執行此參數，讓使用者可以指定要在其中執行 Cmdlet 的文化特性。|
|**Domain**<br>資料類型：字串|執行此參數，讓使用者可以指定功能變數名稱。|
|**硬碟磁碟機**<br>資料類型：字串|執行此參數，讓使用者可以指定磁片磁碟機名稱。|
|**發生**<br>資料類型：字串|執行此參數，讓使用者可以指定事件名稱。|
|**介面**<br>資料類型：字串|執行此參數，讓使用者可以指定網路介面名稱。|
|**Ip**<br>資料類型：字串|執行此參數，讓使用者可以指定 IP 位址。|
|**任務**<br>資料類型：字串|執行此參數，讓使用者可以指定作業。|
|**LiteralPath**<br>資料類型：字串|執行此參數，讓使用者可以在不支援萬用字元時，指定資源的路徑。 （當支援萬用字元時，請使用**Path**參數）。|
|**Mac**<br>資料類型：字串|執行此參數，讓使用者可以指定媒體存取控制站（MAC）位址。|
|**ParentId**<br>資料類型：字串|執行此參數，讓使用者可以指定父系識別碼。|
|**路徑名**<br>資料類型：字串、字串 []|執行此參數，讓使用者可以在支援萬用字元時指出資源的路徑。 （不支援萬用字元時，請使用**LiteralPath**參數）。我們建議您開發此參數，讓它支援提供者所使用的完整 @no__t 1 語法。 我們也建議您進行開發，讓它可以使用最多的提供者。|
|**移植**<br>資料類型：整數、字串|請執行此參數，讓使用者可以為網路或字串值（例如「biztalk」）指定整數值，以用於其他類型的埠。|
|**印表機**<br>資料類型：整數、字串|執行此參數，讓使用者可以指定要用於 Cmdlet 的印表機。|
|**容量**<br>資料類型： Int32|執行此參數，讓使用者可以指定大小。|
|**TID**<br>資料類型：字串|執行此參數，讓使用者可以指定 Cmdlet 的交易識別碼（TID）。|
|**型**<br>資料類型：字串|請執行這個參數，讓使用者可以指定要在其上操作的資源類型。|
|**連結**<br>資料類型：字串|執行此參數，讓使用者可以指定統一資源定位器（URL）。|
|**User**<br>資料類型：字串|執行此參數，讓使用者可以指定其名稱或其他使用者的名稱。|

## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
