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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067445"
---
# <a name="resource-parameters"></a>資源參數

下表列出建議的名稱和資源參數的功能。 對於這些參數，資源可能包含在 cmdlet 類別或執行此指令程式的主應用程式的組件。

|參數|功能|
|---|---|
|**Application**<br>資料類型：String|實作此參數，讓使用者可以指定應用程式。|
|**組件**<br>資料類型：String|實作此參數，讓使用者可以指定組件。|
|**屬性**<br>資料類型：String|實作此參數，讓使用者可以指定屬性。|
|**類別**<br>資料類型：String|實作此參數，讓使用者可以指定 Microsoft.NET Framework 類別。|
|**Cluster**<br>資料類型：String|實作此參數，讓使用者可以指定叢集。|
|**文化特性**<br>資料類型：String|實作此參數，讓使用者可以指定要執行此指令程式的文化特性。|
|**網域**<br>資料類型：String|實作此參數，讓使用者可以指定的網域名稱。|
|**Drive**<br>資料類型：String|實作此參數，讓使用者可以指定磁碟機名稱。|
|**事件**<br>資料類型：String|實作此參數，讓使用者可以指定事件名稱。|
|**介面**<br>資料類型：String|實作此參數，讓使用者可以指定網路介面名稱。|
|**IpAddress**<br>資料類型：String|實作此參數，讓使用者可以指定 IP 位址。|
|**Job**<br>資料類型：String|實作此參數，讓使用者可以指定的作業。|
|**LiteralPath**<br>資料類型：String|實作此參數，讓使用者在不支援萬用字元時，可以指定資源的路徑。 (使用**路徑**參數支援萬用字元。)|
|**Mac**<br>資料類型：String|實作此參數，讓使用者可以指定媒體存取控制站 (MAC) 位址。|
|**ParentId**<br>資料類型：String|實作此參數，讓使用者可以指定的父識別碼。|
|**路徑**<br>資料類型：String, String[]|實作此參數，以支援使用萬用字元時，使用者可能表示資源的路徑。 (使用**LiteralPath**時不支援萬用字元的參數。)我們建議您開發這個參數，以便支援完整`provider:path`提供者所使用的語法。 我們也建議您開發它，讓它盡可能使用多個提供者。|
|**連接埠**<br>資料類型：整數、 字串|實作此參數，讓使用者可以指定的網路功能的整數值或字串值，例如"biztalk"對於其他類型的連接埠。|
|**印表機**<br>資料類型：整數、 字串|實作此參數，讓使用者可以指定要使用此指令程式的印表機。|
|**Size**<br>資料類型：Int32|實作此參數，讓使用者可以指定大小。|
|**TID**<br>資料類型：String|實作此參數，讓使用者可以指定此 cmdlet 的交易識別碼 (TID)。|
|**型別**<br>資料類型：String|實作此參數，讓使用者可以指定所要執行的資源類型。|
|**URL**<br>資料類型：String|實作此參數，讓使用者可以指定統一資源定位器 (URL)。|
|**User**<br>資料類型：String|實作此參數，讓使用者可以指定其名稱或另一位使用者的名稱。|

## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
