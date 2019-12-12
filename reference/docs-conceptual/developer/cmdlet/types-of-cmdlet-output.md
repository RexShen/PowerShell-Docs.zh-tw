---
title: Cmdlet 輸出的類型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369287"
---
# <a name="types-of-cmdlet-output"></a>Cmdlet 輸出的類型

PowerShell 提供數個方法，可由 Cmdlet 呼叫以產生輸出。 這些方法會使用特定的作業，將其輸出寫入特定的資料流程，例如成功的資料流程或錯誤資料流程。 本文說明輸出的類型，以及用來產生它們的方法。

## <a name="types-of-output"></a>輸出類型

### <a name="success-output"></a>成功輸出

Cmdlet 可以藉由傳回管線中的下一個命令可以處理的物件，來報告成功。 在 Cmdlet 成功執行其動作之後，此 Cmdlet 會呼叫[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 我們建議您呼叫這個方法，而不是[PSHostUserInterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) ，而不是您要的[. writeline 方法](/dotnet/api/System.Console.WriteLine)。

您可以針對通常不會傳回物件的 Cmdlet 提供**PassThru**切換參數。
在命令列指定**PassThru**切換參數時，會要求 Cmdlet 傳回物件。 如需具有**PassThru**參數的 Cmdlet 範例，請參閱[新增-歷程記錄](/powershell/module/Microsoft.PowerShell.Core/Add-History)。

### <a name="error-output"></a>錯誤輸出

Cmdlet 可以報告錯誤。 當發生終止錯誤時，此 Cmdlet 會擲回例外狀況。 當發生非終止錯誤時，指令程式會呼叫[CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，將錯誤記錄傳送至錯誤資料流程。 如需錯誤報表的詳細資訊，請參閱[錯誤報表概念](./error-reporting-concepts.md)。

### <a name="verbose-output"></a>詳細資訊輸出

Cmdlet 可以提供有用的資訊給您，而 Cmdlet 會藉由呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法來正確處理記錄。 方法會產生詳細訊息，指出如何繼續執行動作。

根據預設，不會顯示詳細訊息。 執行 Cmdlet 時，您可以指定**Verbose**參數來顯示這些訊息。 **Verbose**是適用于所有 Cmdlet 的通用參數。

### <a name="progress-output"></a>進度輸出

當 Cmdlet 正在執行需要很長時間才能完成的工作（例如以遞迴方式複製目錄）時，Cmdlet 可以提供進度資訊給您。 若要顯示進度資訊，Cmdlet 會呼叫[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。

### <a name="debug-output"></a>Debug 輸出

Cmdlet 可以提供在對 Cmdlet 程式碼進行疑難排解時很有説明的 debug 訊息。 若要顯示調試資訊，Cmdlet 會呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。

根據預設，不會顯示偵錯工具訊息。 執行 Cmdlet 時，您可以指定**Debug**參數來顯示這些訊息。 **Debug**是可用於所有 Cmdlet 的通用參數。

### <a name="warning-output"></a>警告輸出

Cmdlet 可以藉由呼叫[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法來顯示警告訊息。

根據預設，會顯示警告訊息。 不過，您可以使用 `$WarningPreference` 變數，或在呼叫 Cmdlet 時使用**Verbose**和**Debug**參數來設定警告訊息。

## <a name="displaying-output"></a>顯示輸出

對於所有的寫入方法呼叫而言，內容顯示是由特定的執行時間變數所決定。 這個例外狀況是[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法的。 藉由使用這些變數，您可以在程式碼中的正確位置進行適當的寫入呼叫，而不需要擔心輸出是否應該顯示。

## <a name="accessing-the-output-functionality-of-a-host-application"></a>存取主應用程式的輸出功能

您也可以設計 Cmdlet，透過 PowerShell 執行時間直接存取主應用程式的輸出功能。 使用 PowerShell 所提供的主機 Api，而不是[system. 主控台](/dotnet/api/System.Console)或[system.web](/dotnet/api/System.Windows.Forms) ，可確保您的 Cmdlet 可與各種主機搭配使用。 例如： **powershell .exe**主控台主機、 **powershell_ise .exe**圖形化主機、powershell 遠端主機和協力廠商主機。

## <a name="see-also"></a>另請參閱

[錯誤報表概念](./error-reporting-concepts.md)

[Cmdlet 總覽](./cmdlet-overview.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)