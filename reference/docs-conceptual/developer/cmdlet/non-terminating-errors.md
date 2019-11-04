---
title: 非終止錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369597"
---
# <a name="non-terminating-errors"></a>非終止錯誤

本主題討論用來報告非終止錯誤的方法。 它也會討論如何從 Cmdlet 內呼叫方法。

當發生非終止錯誤時，此 Cmdlet 應該會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來報告此錯誤。 當 Cmdlet 回報非終止錯誤時，此 Cmdlet 可以繼續在此輸入物件以及進一步的傳入管線物件上操作。 如果指令程式呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，此 Cmdlet 可以撰寫錯誤記錄，以描述造成非終止錯誤的狀況。 如需錯誤記錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。

Cmdlet 可以視需要從其輸入處理方法中呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 。 不過，Cmdlet 只能從呼叫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)、 [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)的執行緒，以 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 的身分，來進行指令程式的自管理元件的呼叫。 （或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ）輸入處理方法。 請不要從另一個執行緒呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 。 相反地，會將錯誤傳達回到主執行緒。

## <a name="see-also"></a>另請參閱

[WriteError 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[BeginProcessing 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[ProcessRecord 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.servicemodel. Cmdlet。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
