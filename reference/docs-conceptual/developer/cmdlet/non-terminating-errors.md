---
title: 非終止錯誤 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d74c248e6ef54151400b8060d76524e89d87352c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786555"
---
# <a name="non-terminating-errors"></a>非終止錯誤

本主題討論用來報告非終止錯誤的方法。 它也會討論如何從 Cmdlet 內呼叫方法。

當發生非終止錯誤時，此 Cmdlet 應該會呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法來報告此錯誤。 當 Cmdlet 回報非終止錯誤時，此 Cmdlet 可以繼續在此輸入物件以及進一步的傳入管線物件上操作。 如果指令程式呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法，此 Cmdlet 可以撰寫錯誤記錄，以描述造成非終止錯誤的狀況。。 如需錯誤記錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。

Cmdlet 可以視需要從其輸入處理方法中呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 。 不過，Cmdlet 只能從呼叫[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)、 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)的執行緒[，或由](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)或 system.servicemodel 輸入處理方法，來進行呼叫的程式，而不會進行此指令程式中的指令程式的呼叫。 請不要從另一個執行緒呼叫[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 。 相反地，會將錯誤傳達回到主執行緒。

## <a name="see-also"></a>另請參閱

[WriteError 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[BeginProcessing 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[ProcessRecord 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.servicemodel. Cmdlet。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
