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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369327"
---
# <a name="terminating-errors"></a>終止錯誤

本主題討論用來報告終止錯誤的方法。 此外，它也會討論如何從 Cmdlet 內呼叫方法，並討論當呼叫方法時，Windows PowerShell 執行時間可以傳回的例外狀況。

當發生終止錯誤時，此 Cmdlet 應該會呼叫[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法來報告錯誤。 這個方法可讓 Cmdlet 傳送描述導致終止錯誤之條件的錯誤記錄。 如需錯誤記錄的詳細資訊，請參閱[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)。

當呼叫[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)方法時，Windows PowerShell 執行時間會永久停止執行管線，並擲回[Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)例外狀況（exception）的功能。 任何後續嘗試呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)、 [WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)或數個其他 api 時，都會導致這些呼叫擲回[Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)例外狀況（exception），而不會發生問題。

如果管線中的另一個 Cmdlet 回報終止錯誤、使用者已要求停止管線，或因為任何原因而在完成之前已停止管線，也可能會發生[Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)例外狀況。 Cmdlet 不需要攔截[Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)例外狀況，除非它必須清除開啟的資源或其內部狀態。

Cmdlet 可以在報告終止錯誤之前，撰寫任何數目的輸出物件或非終止錯誤。 不過，終止錯誤會永久停止管線，而不會報告進一步的輸出、終止錯誤或非終止錯誤。

指令程式只能從呼叫[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)的執行緒，而不是，則為[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 的自管理元件（可能為系統管理）。 （或[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) ）輸入處理方法。 請不要嘗試從另一個執行緒呼叫[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)或[WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ，而是從其他執行緒。 相反地，錯誤必須傳回到主執行緒。

Cmdlet 可能會在它的[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)、 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)或 system.servicemodel 方法的執行中擲回例外狀況（exception），或使用... [（系統管理](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).）。 從這些方法擲回的任何例外狀況（除了一些停止 Windows PowerShell 主機的嚴重錯誤情況除外）都會被視為終止的錯誤，它會停止管線，而不是 Windows PowerShell 整體。 （這只適用于主要的 Cmdlet 執行緒。 Cmdlet 所產生的執行緒中未攔截到的例外狀況，通常會暫停 Windows PowerShell 主機。）我們建議使用[Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ，而不是擲回例外狀況，因為錯誤記錄會提供錯誤條件的其他相關資訊，這對使用者很有用。 Cmdlet 應遵循 managed 程式碼指導方針來攔截和處理所有例外狀況（`catch (Exception e)`）。 只將已知和預期類型的例外狀況轉換成錯誤記錄。

## <a name="see-also"></a>另請參閱

[BeginProcessing 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.servicemodel. Cmdlet。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[ProcessRecord 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Pipelinestoppedexception。](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[Throwterminatingerror * 的 *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[WriteError 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell 錯誤記錄](./windows-powershell-error-records.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
