---
title: 日期和時間參數 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f1b2bb3b3da2b73860298e36d88502bfd67c5b22
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774655"
---
# <a name="date-and-time-parameters"></a>日期和時間參數

下錶針對處理日期和時間資訊的參數，列出建議的名稱和功能。 日期和時間參數通常用來記錄何時建立或存取某個專案。

|參數|功能|
|---|---|
|**存取**<br>資料類型： SwitchParameter|執行此參數，以便在指定時，Cmdlet 會根據**Before**和**After**參數所指定的日期和時間，在已存取的資源上運作。 如果指定此參數，則必須指定**建立**和**修改**的參數。|
|**之後**<br>資料類型： DateTime|執行此參數來指定使用 Cmdlet 的日期和時間。 若要讓**After**參數能夠正常執行，Cmdlet 也必須具有已**存取**、已**建立**或**已修改**的參數。 而且，當呼叫 Cmdlet 時，該參數必須設定為**true** 。|
|**之前**<br>資料類型： DateTime|執行此參數來指定使用 Cmdlet 之前的日期和時間。 若要讓**Before**參數能夠正常執行，Cmdlet 也必須具有已**存取**、已**建立**或**已修改**的參數。 而且，當呼叫 Cmdlet 時，該參數必須設定為**true** 。|
|**建立日期**<br>資料類型： SwitchParameter|執行此參數，以便在指定時，Cmdlet 會在根據**Before**和**After**參數所指定日期和時間所建立的資源上運作。 如果指定了這個參數，就不能指定**存取**的和**修改過**的參數。|
|**精確**<br>資料類型： SwitchParameter|請執行此參數，以便在指定時，資源字詞必須完全符合資源名稱。 未指定參數時，資源詞彙和名稱不需要完全相符。|
|**被**<br>資料類型： DateTime|執行此參數，以便在指定時，Cmdlet 會在已根據**Before**和**After**參數所指定日期和時間變更的資源上運作。 如果指定了這個參數，就不能指定**存取**和**建立**的參數。|
## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
