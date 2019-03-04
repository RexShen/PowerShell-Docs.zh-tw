---
title: GetProc Tutorial | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862454"
---
# <a name="getproc-tutorial"></a>GetProc 教學課程

本節提供的教學課程，建立 Get-proc cmdlet 是非常類似[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Windows PowerShell 所提供的 cmdlet。 本教學課程提供的說明 cmdlet 實作的方式的程式碼片段和程式碼的說明。

## <a name="topics-in-this-tutorial"></a>在本教學課程的主題

在本教學課程主題被設計來建置在上一個主題中討論的內容上的每個主題來循序讀取。

[建立不含參數的 Cmdlet](./creating-a-cmdlet-without-parameters.md)本章節描述如何建立 cmdlet 會從本機電腦，而不使用參數，擷取資訊，然後將資訊寫入管線。

[加入參數，該程序命令列輸入](./adding-parameters-that-process-command-line-input.md)本章節描述如何將參數新增至 Get-proc cmdlet，讓此指令程式可以處理明確傳遞至 cmdlet 的物件為基礎的輸入。 所述的實作這裡擷取其名稱為基礎的處理程序，並再將資訊寫入管線。

[加入參數，該程序管線輸入](./adding-parameters-that-process-pipeline-input.md)本章節描述如何將參數新增至 Get-proc cmdlet，讓此指令程式可以處理透過管線傳遞給它的物件。 描述實作 cmdlet 這裡擷取物件傳遞至 cmdlet，為基礎的處理序，並再將資訊寫入管線。

[將非終止錯誤報告加入至您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)本章節描述如何新增非終止錯誤回報給 cmdlet。 此處所述的實作會偵測到非終止錯誤發生時處理輸入，並將錯誤記錄寫入至資料流時發生錯誤。

## <a name="see-also"></a>另請參閱

[建立不含參數的 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[加入處理命令列輸入的參數](./adding-parameters-that-process-command-line-input.md)

[新增處理程序管線輸入的參數](./adding-parameters-that-process-pipeline-input.md)

[加入非終止錯誤回報給您的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
