---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace 範例
description: Runspace 範例
ms.openlocfilehash: 0171622f3ade3b341bc226f14398d6d293262f0c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657952"
---
# <a name="runspace-samples"></a>Runspace 範例

本節包含範例程式碼，示範如何使用不同類型的執行程式，以同步和非同步方式執行命令。 您可以使用 Microsoft Visual Studio 來建立主控台應用程式，然後將本節中的主題的程式碼複製到您的主應用程式。

## <a name="in-this-section"></a>本節內容

> [!NOTE]
> 如需建立自訂主機介面之主應用程式的範例，請參閱 [自訂主機範例](./custom-host-samples.md)。

 [Runspace01 範例](./runspace01-sample.md) 此範例示範如何使用 [system.string 類別來](/dotnet/api/system.management.automation.powershell) 同步執行 [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet，並在主控台視窗中顯示其輸出。

 [Runspace02 範例](./runspace02-sample.md) 這個範例會示範如何使用 system.string [類別，](/dotnet/api/system.management.automation.powershell) 以同步方式執行 [Get 進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 和 [排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) Cmdlet。 這些命令的結果會使用 [ [system.object](/dotnet/api/System.Windows.Forms.DataGridView) ] 控制項來顯示。

 [Runspace03 範例](./runspace03-sample.md) 這個範例會示範如何使用 system.string [類別來](/dotnet/api/system.management.automation.powershell) 同步執行腳本，以及如何處理非終止錯誤。 指令碼會接收處理序名稱的清單，然後擷取這些處理序。 指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。

 [Runspace04 範例](./runspace04-sample.md) 此範例示範如何使用 [system.servicemodel 類別來](/dotnet/api/system.management.automation.powershell) 執行命令，以及如何捕捉在執行命令時所擲回的終止錯誤。 執行了兩個命令，而最後一個命令傳遞了無效的參數引數。 如此一來，就不會傳回任何物件，並且會擲回終止錯誤。

 [Runspace05 範例](./runspace05-sample.md) 此範例示範如何將嵌入式管理單元新增至 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 物件，以便在開啟執行時間時可以使用嵌入式管理單元的 Cmdlet。 此嵌入式管理單元提供由 >getprocesssample01 範例所定義的 Get-Proc Cmdlet (，此範例會使用[範例](../cmdlet/getprocesssample01-sample.md)) 以同步方式[執行。](/dotnet/api/system.management.automation.powershell)

 [Runspace06 範例](./runspace06-sample.md) 這個範例示範如何將模組加入 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 物件，以便在開啟執行時間時載入模組。 此模組會提供 Get-Proc 的 Cmdlet (由[>getprocesssample02 範例](../cmdlet/getprocesssample02-sample.md)所定義) ，此範例會使用[import-module 物件同步執行。](/dotnet/api/system.management.automation.powershell)

 [Runspace07 範例](./runspace07-sample.md) 這個範例示範如何建立執行時間，然後使用該執行時間，以同步方式使用 [system.servicemodel 物件來](/dotnet/api/system.management.automation.powershell) 執行兩個 Cmdlet。

 [Runspace08 範例](./runspace08-sample.md) 這個範例會示範如何將命令和引數新增至 [system.servicemodel 物件的](/dotnet/api/system.management.automation.powershell) 管線，以及如何以同步方式執行命令。

 [Runspace09 範例](./runspace09-sample.md) 這個範例會示範如何將腳本新增至 [管理](/dotnet/api/system.management.automation.powershell) 物件的管線，以及如何以非同步方式執行腳本。 事件為用來處理指令碼的輸出。

 [Runspace10 範例](./runspace10-sample.md)這個範例示範如何建立預設的初始會話狀態、如何將指令程式新增至[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)、如何建立使用初始會話狀態的執行時間，以及如何使用[system.servicemodel 物件執行命令。](/dotnet/api/system.management.automation.powershell)

 [Runspace11 範例](./runspace11-sample.md) 這會示範如何使用 [Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) 類別來建立 proxy 命令，以呼叫現有的 Cmdlet，但會限制可用參數的集合。 Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。 這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。

## <a name="see-also"></a>另請參閱
