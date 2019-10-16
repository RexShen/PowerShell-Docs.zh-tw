---
title: 運行空間範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360997"
---
# <a name="runspace-samples"></a>Runspace 範例

本節包含範例程式碼，示範如何使用不同類型的執行程式，以同步和非同步方式執行命令。 您可以使用 Microsoft Visual Studio 建立主控台應用程式，然後將此區段中的主題中的程式碼複製到您的主應用程式。

## <a name="in-this-section"></a>在本節中

> [!NOTE]
> 如需建立自訂主機介面之主應用程式的範例，請參閱[自訂主機範例](./custom-host-samples.md)。

 [Runspace01 範例](./runspace01-sample.md)這個範例示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別，以同步方式執行[處理常式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)Cmdlet，並在主控台視窗中顯示其輸出。

 [Runspace02 範例](./runspace02-sample.md)這個範例示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別，以同步方式執行[Get 進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)和[排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)Cmdlet。 這些命令的結果會使用[system.web](/dotnet/api/System.Windows.Forms.DataGridView)控制項來顯示。

 [Runspace03 範例](./runspace03-sample.md)這個範例會示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別，以同步方式執行腳本，以及如何處理非終止錯誤。 指令碼會接收處理序名稱的清單，然後擷取這些處理序。 指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。

 [Runspace04 範例](./runspace04-sample.md)這個範例會示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別來執行命令，以及如何攔截執行命令時所擲回的終止錯誤。 執行了兩個命令，而最後一個命令傳遞了無效的參數引數。 因此，不會傳回任何物件，也會擲回終止錯誤。

 [Runspace05 範例](./runspace05-sample.md)這個範例會示範如何將嵌入式管理單元新增至[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，以便在開啟執行時間時可以使用嵌入式管理單元的 Cmdlet。 此嵌入式管理單元提供一個使用[GetProcessSample01 範例](../cmdlet/getprocesssample01-sample.md)所定義的「取得程式」指令程式，此 Cmdlet 會以同步方式[執行。](/dotnet/api/system.management.automation.powershell)

 [Runspace06 範例](./runspace06-sample.md)這個範例會示範如何將模組新增至[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，以便在開啟執行時間時載入該模組。 此模組會提供使用[GetProcessSample02 範例](../cmdlet/getprocesssample02-sample.md)所定義的「取得程式」 Cmdlet，此指令程式會以同步方式[執行。](/dotnet/api/system.management.automation.powershell)

 [Runspace07 範例](./runspace07-sample.md)這個範例會示範如何建立執行時間，然後使用該執行時間，透過使用[system.web](/dotnet/api/system.management.automation.powershell)物件，以同步方式執行兩個 Cmdlet。

 [Runspace08 範例](./runspace08-sample.md)這個範例示範如何將命令和引數新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線，以及如何同步執行命令。

 [Runspace09 範例](./runspace09-sample.md)這個範例示範如何將腳本新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線，以及如何以非同步方式執行腳本。 事件為用來處理指令碼的輸出。

 [Runspace10 範例](./runspace10-sample.md)這個範例會示範如何建立預設初始會話狀態、如何將 Cmdlet 新增至[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)、如何建立使用初始會話狀態的執行時間，以及如何使用來執行此命令的方法[管理元件： Powershell](/dotnet/api/system.management.automation.powershell)物件。

 [Runspace11 範例](./runspace11-sample.md)這會示範如何使用[Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand)類別來建立 proxy 命令，以呼叫現有的 Cmdlet，但會限制可用的參數集合。 Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。 這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。

## <a name="see-also"></a>另請參閱
