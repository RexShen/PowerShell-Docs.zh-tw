---
title: 終止錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059230"
---
# <a name="terminating-errors"></a>終止錯誤

本主題討論用來終止錯誤的報表的方法。 它也會討論如何呼叫這個 cmdlet，從方法，它將告訴您可以在呼叫方法時，Windows PowerShell 執行階段所傳回的例外狀況。

當終止會發生錯誤，指令程式應該報告錯誤，藉由呼叫[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法。 這個方法可讓 cmdlet 傳送錯誤記錄，描述造成終止錯誤的條件。 如需詳細的錯誤記錄的詳細資訊，請參閱[Windows PowerShell 的錯誤記錄](./windows-powershell-error-records.md)。

當[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)呼叫方法，Windows PowerShell 執行階段永久停止管線執行，且會擲回[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)例外狀況。 若要呼叫的任何後續嘗試[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)， [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)，或其他數個 Api 會導致這些呼叫擲回[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)例外狀況。

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)如果管線中的另一個 cmdlet 會報告終止錯誤，如果使用者已要求停止管線，或如果管線已停止執行，也會發生例外狀況之前完成，因為任何原因。 此 cmdlet 不需要以攔截[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)例外狀況除非資源或其內部狀態，必須清除功能會開啟它。

Cmdlet 可以報告的終止錯誤之前撰寫任意數目的輸出物件或非終止錯誤。 不過，管線中，而任何進一步的輸出，終止錯誤，，永遠會停止的終止錯誤，或可以報告非終止錯誤。

指令程式可以呼叫[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)只能從呼叫的執行緒[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)輸入處理方法。 請勿嘗試呼叫[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)或是[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)從另一個執行緒。 相反地，必須通知錯誤傳回至主執行緒。

就可以為 cmdlet 的實作中擲回的例外狀況[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 從這些方法 （除了有幾個嚴重的錯誤條件所停止的 Windows PowerShell 主機） 擲回任何例外狀況會解譯為終止錯誤，這會停止管線，而非整個 Windows PowerShell。 （這只適用於主要 cmdlet 執行緒。 Cmdlet 所繁衍的執行緒中的未攔截到例外狀況一般情況下，暫止的 Windows PowerShell 主機。）我們建議您改用[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)而不是擲回例外狀況，因為錯誤記錄會提供錯誤狀況的其他資訊，這是很有用終端使用者。 指令程式應該接受針對擷取及處理所有例外狀況的 managed 程式碼指導方針 (`catch (Exception e)`)。 轉換錯誤記錄中的已知且預期類型的例外狀況。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
