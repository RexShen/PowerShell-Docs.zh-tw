---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc 教學課程
description: GetProc 教學課程
ms.openlocfilehash: 9379e791dd5361fcf5b79061bf0a601ebeb84f42
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652775"
---
# <a name="getproc-tutorial"></a>GetProc 教學課程

本節提供的教學課程可讓您建立與 Windows PowerShell 所提供之 [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet 非常類似的 Get-Proc Cmdlet。 本教學課程提供的程式碼片段可說明如何實作為 Cmdlet 的程式碼，以及程式碼的說明。

## <a name="topics-in-this-tutorial"></a>本教學課程中的主題

本教學課程中的主題是設計成依序讀取，每個主題都是以上一個主題中討論的內容為基礎。

[建立不含參數的 Cmdlet](./creating-a-cmdlet-without-parameters.md) 本節說明如何建立 Cmdlet，以在不使用參數的情況下，從本機電腦抓取資訊，然後將資訊寫入管線。

[加入處理 Command-Line 輸入的參數](./adding-parameters-that-process-command-line-input.md) 本節說明如何將參數新增至 Get-Proc Cmdlet，讓 Cmdlet 可以根據傳遞給 Cmdlet 的明確物件來處理輸入。 此處所述的執行會根據其名稱來抓取進程，然後將資訊寫入管線。

[加入處理管線輸入的參數](./adding-parameters-that-process-pipeline-input.md) 本節說明如何將參數新增至 Get-Proc Cmdlet，讓 Cmdlet 可以處理透過管線傳遞給它的物件。 此處所述的執行 Cmdlet 會根據傳遞給 Cmdlet 的物件來抓取進程，然後將資訊寫入管線。

[將非終止錯誤報表新增至您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) 本節說明如何將非終止錯誤報表新增至 Cmdlet。 此處所述的執行會偵測處理輸入時所發生的非終止錯誤，並將錯誤記錄寫入至錯誤資料流程。

## <a name="see-also"></a>另請參閱

[建立不含參數的 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[加入處理 Command-Line 輸入的參數](./adding-parameters-that-process-command-line-input.md)

[新增處理管道輸入的參數](./adding-parameters-that-process-pipeline-input.md)

[將非終止錯誤報表新增至您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
