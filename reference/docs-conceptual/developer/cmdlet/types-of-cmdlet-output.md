---
ms.date: 01/18/2019
ms.topic: reference
title: Cmdlet 輸出類型
description: Cmdlet 輸出類型
ms.openlocfilehash: 591b7699e951db9016e48d5ef623265e23791e11
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660495"
---
# <a name="types-of-cmdlet-output"></a>Cmdlet 輸出的類型

PowerShell 提供數個方法，可由 Cmdlet 呼叫以產生輸出。 這些方法會使用特定的作業，將其輸出寫入至特定資料流程，例如成功資料流程或錯誤資料流程。 本文說明輸出的類型以及用來產生它們的方法。

## <a name="types-of-output"></a>輸出類型

### <a name="success-output"></a>成功輸出

Cmdlet 可以藉由傳回管線中的下一個命令可處理的物件，來報告成功。 指令程式成功執行其動作之後，指令程式會呼叫 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 方法。 我們建議您呼叫這個方法，而不是[PSHostUserInterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) ，而不是呼叫[ writeline 方法](/dotnet/api/System.Console.WriteLine)。

您可以針對通常不會傳回物件的 Cmdlet 提供 **PassThru** 切換參數。
當您在命令列指定 **PassThru** 切換參數時，系統會要求 Cmdlet 傳回物件。 如需具有 **PassThru** 參數的 Cmdlet 範例，請參閱新增歷程 [記錄](/powershell/module/Microsoft.PowerShell.Core/Add-History)。

### <a name="error-output"></a>錯誤輸出

Cmdlet 可以報告錯誤。 當終止錯誤發生時，此 Cmdlet 會擲回例外狀況。 當非終止錯誤發生時，此 Cmdlet 會呼叫 [CmdletProvider WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 方法，以將錯誤記錄傳送至錯誤資料流程。 如需有關錯誤報表的詳細資訊，請參閱 [錯誤報表概念](./error-reporting-concepts.md)。

### <a name="verbose-output"></a>詳細資訊輸出

Cmdlet 可以藉由呼叫 [WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 方法來正確處理記錄，以提供實用的資訊給您。 方法會產生詳細訊息，指出動作如何進行。

依預設，不會顯示詳細訊息。 您可以在執行 Cmdlet 來顯示這些訊息時，指定 **Verbose** 參數。 **Verbose** 是適用于所有 Cmdlet 的通用參數。

### <a name="progress-output"></a>進度輸出

Cmdlet 可以在 Cmdlet 正在執行需要很長時間才能完成的工作（例如，以遞迴方式複製目錄）時，提供進度資訊給您。 若要顯示進度資訊，Cmdlet 會呼叫 [WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 方法。

### <a name="debug-output"></a>調試輸出

Cmdlet 可以提供在疑難排解 Cmdlet 程式碼時很有説明的偵錯工具訊息。 為了顯示 debug 資訊，Cmdlet 會呼叫 [WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 方法。

預設不會顯示 debug 訊息。 您可以在執行 Cmdlet 時指定 **Debug** 參數，以顯示這些訊息。 **Debug** 是可用於所有 Cmdlet 的通用參數。

### <a name="warning-output"></a>警告輸出

Cmdlet 可以藉由呼叫 [WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 方法來顯示警告訊息。

根據預設，會顯示警告訊息。 不過，您可以使用變數來設定警告訊息， `$WarningPreference` 或是在呼叫 Cmdlet 時使用 **Verbose** 和 **Debug** 參數。

## <a name="displaying-output"></a>顯示輸出

針對所有的寫入方法呼叫，內容顯示是由特定的執行時間變數所決定。 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法的例外狀況為例外。 藉由使用這些變數，您可以在程式碼中的正確位置進行適當的寫入呼叫，而不需要擔心何時或是否應顯示輸出。

## <a name="accessing-the-output-functionality-of-a-host-application"></a>存取主應用程式的輸出功能

您也可以設計 Cmdlet，透過 PowerShell 執行時間直接存取主機應用程式的輸出功能。 使用 PowerShell 提供的主機 Api （而不是 [系統主控台](/dotnet/api/System.Console) 或 system.string），可確保您的 Cmdlet [將可搭配](/dotnet/api/System.Windows.Forms) 各種主機使用。 例如： **powershell.exe** 主控台主機、 **powershell_ise.exe** 圖形化主機、PowerShell 遠端主機和協力廠商主機。

## <a name="see-also"></a>請參閱

[錯誤報告概念](./error-reporting-concepts.md)

[Cmdlet 概觀](./cmdlet-overview.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
