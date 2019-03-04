---
title: 類型的 Cmdlet 輸出 |Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853924"
---
# <a name="types-of-cmdlet-output"></a>類型的 cmdlet 輸出

PowerShell 提供數種方法，可呼叫指令程式來產生輸出。 這些方法會使用特定的作業，將其輸出寫入至特定的資料流，例如成功的資料流或錯誤資料流。 本文說明輸出和用來產生這些方法的類型。

## <a name="types-of-output"></a>類型的輸出

### <a name="success-output"></a>成功輸出

Cmdlet 可以藉由傳回的物件，可處理的管線中下一個命令會報告成功。 此指令程式已成功執行其動作之後，cmdlet 就會呼叫[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 我們建議您呼叫此方法，而非[System.Console.WriteLine](/dotnet/api/System.Console.WriteLine)或是[System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine)方法。

您可以提供**PassThru**切換通常不會傳回物件的 cmdlet 的參數。
當**PassThru**在命令列指定切換參數，cmdlet 會要求傳回的物件。 如需範例指令程式可**PassThru**參數，請參閱[Add-history](/powershell/module/Microsoft.PowerShell.Core/Add-History)。

### <a name="error-output"></a>錯誤輸出

Cmdlet 可以報告的錯誤。 終止錯誤發生時，此指令程式會擲回例外狀況。 發生非終止錯誤時，cmdlet 就會呼叫[System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，將錯誤記錄傳送至錯誤資料流。 如需有關錯誤報告的詳細資訊，請參閱 <<c0> [ 錯誤報告概念](./error-reporting-concepts.md)。

### <a name="verbose-output"></a>詳細資訊輸出

Cmdlet 可以提供有用的資訊給您時 cmdlet 呼叫中正確處理資料錄[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。 此方法會產生詳細的訊息，指出動作正在進行的方式。

根據預設，將不會顯示詳細訊息。 您可以指定**Verbose**時，此 cmdlet 會執行，以顯示這些訊息。 **Verbose**是常見的參數所使用的所有 cmdlet。

### <a name="progress-output"></a>進度輸出

Cmdlet 可以將進度資訊提供給您，當 cmdlet 執行工作都要花很長的時間才能完成，例如目錄遞迴複製。 若要顯示進度資訊指令程式會呼叫[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。

### <a name="debug-output"></a>偵錯輸出

Cmdlet 可以提供疑難排解 cmdlet 程式碼時很有幫助的偵錯訊息。 若要顯示偵錯資訊的指令程式會呼叫[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。

根據預設，不會顯示偵錯訊息。 您可以指定**偵錯**時，此 cmdlet 會執行，以顯示這些訊息。 **偵錯**是常見的參數所使用的所有 cmdlet。

### <a name="warning-output"></a>警告輸出

Cmdlet 可以顯示警告訊息，藉由呼叫[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法。

根據預設，會顯示警告訊息。 不過，您可以設定警告訊息，利用`$WarningPreference`變數，或使用**Verbose**並**偵錯**參數呼叫 cmdlet 時。

## <a name="displaying-output"></a>顯示輸出

針對所有寫入方法呼叫，內容顯示由特定執行階段變數決定。 例外狀況[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 藉由使用這些變數，您可以進行適當的程式碼中寫入的正確位置的呼叫，而不必擔心時，或應該會顯示輸出。

## <a name="accessing-the-output-functionality-of-a-host-application"></a>存取主應用程式的輸出功能

您也可以設計可直接透過 PowerShell 執行階段存取主應用程式的輸出功能的 cmdlet。 使用主應用程式而不是 PowerShell 所提供的 Api [System.Console](/dotnet/api/System.Console)或是[System.Windows.Forms](/dotnet/api/System.Windows.Forms)可確保您的 cmdlet 會使用各種不同的主機。 例如： **powershell.exe**主控台主機**powershell_ise.exe**圖形化的主機、 PowerShell 遠端處理主應用程式和協力廠商主機。

## <a name="see-also"></a>另請參閱

[錯誤報告的概念](./error-reporting-concepts.md)

[指令程式概觀](./cmdlet-overview.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)