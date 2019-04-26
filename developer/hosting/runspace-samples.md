---
title: Runspace 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082731"
---
# <a name="runspace-samples"></a>Runspace 範例

本節包含示範如何使用不同類型的 runspace，以同步和非同步方式執行命令的範例程式碼。 您可以使用 Microsoft Visual Studio 來建立主控台應用程式，然後將從這一節的主題的程式碼複製到主應用程式。

## <a name="in-this-section"></a>在本節中

> [!NOTE]
> 如需建立自訂主機介面的主機應用程式的範例，請參閱[自訂主應用程式範例](./custom-host-samples.md)。

 [Runspace01 範例](./runspace01-sample.md)這個範例示範如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)類別來執行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 以同步方式，並在主控台中顯示其輸出視窗。

 [Runspace02 範例](./runspace02-sample.md)這個範例示範如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)類別來執行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)並[Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)cmdlet 以同步方式。 這些命令的結果會顯示藉由使用[System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView)控制項。

 [Runspace03 範例](./runspace03-sample.md)這個範例示範如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)類別以同步方式執行指令碼，以及如何處理非終止錯誤。 指令碼會接收處理序名稱的清單，然後擷取這些處理序。 指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。

 [範例 Runspace04](./runspace04-sample.md)這個範例示範如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)類別來執行命令，以及如何捕捉執行命令時，會擲回的終止錯誤。 執行了兩個命令，而最後一個命令傳遞了無效的參數引數。 如此一來會傳回任何物件，並會擲回終止錯誤。

 [範例 Runspace05](./runspace05-sample.md)這個範例示範如何將嵌入式管理單元，來新增[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，讓嵌入式管理單元的 cmdlet 可在 runspace 開啟時。 嵌入式管理單元提供 Get-proc cmdlet (由[GetProcessSample01 範例](../cmdlet/getprocesssample01-sample.md)) 執行使用同步[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。

 [Runspace06 範例](./runspace06-sample.md)這個範例示範如何將模組加入[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，以便在 runspace 開啟時載入的模組。 模組提供 Get-proc cmdlet (由[GetProcessSample02 範例](../cmdlet/getprocesssample02-sample.md)) 執行使用同步[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。

 [Runspace07 範例](./runspace07-sample.md)這個範例示範如何建立 runspace，並使用以同步方式執行兩個 cmdlet 中使用該 runspace [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。

 [Runspace08 範例](./runspace08-sample.md)這個範例示範如何將命令和引數新增至管線[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件，以及如何以同步方式執行命令。

 [Runspace09 範例](./runspace09-sample.md)這個範例示範如何將指令碼新增至管線[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件，以及如何以非同步方式執行指令碼。 事件為用來處理指令碼的輸出。

 [Runspace10 範例](./runspace10-sample.md)這個範例示範如何建立預設初始工作階段狀態，如何新增到 cmdlet [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)，如何建立會使用的 runspace初始工作階段狀態，以及如何使用執行命令[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。

 [Runspace11 範例](./runspace11-sample.md)這會顯示如何使用[System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand)類別來建立 proxy 命令呼叫現有的 cmdlet，但會限制可用的參數集。 Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。 這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。

## <a name="see-also"></a>另請參閱
