---
title: GetProc 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364437"
---
# <a name="getproc-tutorial"></a>GetProc 教學課程

本節提供的教學課程可讓您建立與 Windows PowerShell 所提供的「[取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」 Cmdlet 非常相似的「處理常式」 Cmdlet。 本教學課程提供程式碼片段，說明如何實作為 Cmdlet，以及程式碼的說明。

## <a name="topics-in-this-tutorial"></a>本教學課程中的主題

本教學課程中的主題設計為依序閱讀，每個主題都會根據上一個主題中所討論的內容來建立。

[建立不含參數的 Cmdlet](./creating-a-cmdlet-without-parameters.md)本節說明如何建立在不使用參數的情況下，從本機電腦抓取資訊的 Cmdlet，然後將資訊寫入管線。

[新增可處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)本節說明如何將參數新增至 Get-help Cmdlet，讓 Cmdlet 可以根據傳遞至 Cmdlet 的明確物件來處理輸入。 此處所述的執行會根據其名稱來抓取進程，然後將資訊寫入管線。

[加入處理管線輸入的參數](./adding-parameters-that-process-pipeline-input.md)本節說明如何將參數新增至 Get-help Cmdlet，讓 Cmdlet 可以處理透過管線傳遞給它的物件。 這裡所述的執行 Cmdlet 會根據傳遞給 Cmdlet 的物件來抓取處理常式，然後將資訊寫入管線。

[將非終止錯誤報表新增至您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)本節說明如何將非終止錯誤報表新增至 Cmdlet。 此處所述的執行會偵測處理輸入時所發生的非終止錯誤，並將錯誤記錄寫入錯誤資料流程。

## <a name="see-also"></a>另請參閱

[建立不含參數的 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[新增可處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)

[加入處理管線輸入的參數](./adding-parameters-that-process-pipeline-input.md)

[將非終止錯誤報表新增至您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
