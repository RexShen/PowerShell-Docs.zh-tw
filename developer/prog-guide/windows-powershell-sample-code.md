---
title: Windows PowerShell 的範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: 264e9f7538e13b48d899e87541239250eb88f14e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863354"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell 範例程式碼

Windows PowerShell® 範例都是透過 Windows SDK。 本節包含 Windows SDK 範例中所包含的範例程式碼。

> [!NOTE]
> 安裝 Windows SDK 時，**範例**Windows PowerShell 的所有範例都都可以建立目錄。 一般安裝目錄就是**C:\Program Files\Microsoft SDKs\Windows\v6.0**。 啟動 Windows PowerShell 並輸入 **"cd Samples\SysMgmt\PowerShell"** 找不到 Windows PowerShell 範例目錄。 在本文件中，Windows PowerShell 範例目錄指 **\<PowerShell 範例 >**。

## <a name="sample-code-listing"></a>範例程式碼清單

|範例程式碼|描述|
|-----------------|-----------------|
|[AccessDbProviderSample01 Code Sample](./accessdbprovidersample01-code-sample.md)|這是提供者中所述[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。|
|[AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md)|這是提供者中所述[建立 Windows PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。|
|[AccessDbProviderSample03 Code Sample](./accessdbprovidersample03-code-sample.md)|這是提供者中所述[建立 Windows PowerShell 項目提供者](./creating-a-windows-powershell-item-provider.md)。|
|[AccessDbProviderSample04 Code Sample](./accessdbprovidersample04-code-sample.md)|這是提供者中所述[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。|
|[AccessDbProviderSample05 Code Sample](./accessdbprovidersample05-code-sample.md)|這是提供者中所述[建立 Windows PowerShell 巡覽提供者](./creating-a-windows-powershell-navigation-provider.md)。|
|[AccessDbProviderSample06 Code Sample](./accessdbprovidersample06-code-sample.md)|這是提供者中所述[建立 Windows PowerShell 內容提供者](./creating-a-windows-powershell-content-provider.md)。|
|[GetProc01 Code Samples](./getproc01-code-samples.md)|這是基本`Get-Process`cmdlet 的範例中所述[建立您的第一個 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)。|
|[GetProc02 Code Samples](./getproc02-code-samples.md)|這是`Get-Process`cmdlet 的範例中所述[加入參數，該程序的命令列輸入](../cmdlet/adding-parameters-that-process-command-line-input.md)。|
|[GetProc03 Code Samples](./getproc03-code-samples.md)|這是`Get-Process`cmdlet 的範例中所述[加入參數，該程序管線輸入](../cmdlet/adding-parameters-that-process-pipeline-input.md)。|
|[GetProc04 Code Samples](./getproc04-code-samples.md)|這是`Get-Process`cmdlet 的範例中所述[新增非終止錯誤報告，您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)。|
|[GetProc05 Code Samples](./getproc05-code-samples.md)|這`Get-Process`cmdlet 是類似於中所述[新增非終止錯誤報告，您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)。|
|[StopProc01 Code Samples](./stopproc01-code-samples.md)|這是`Stop-Process`cmdlet 的範例中所述[建立 Cmdlet，會修改系統](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md)。|
|[StopProcessSample04 Code Samples](./stopprocesssample04-code-samples.md)|這是`Stop-Process`cmdlet 的範例中所述[新增至 Cmdlet 的參數集](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)。|
|[Runspace01 程式碼範例](./runspace01-code-samples.md)|這些是程式碼範例中所述的 runspace[建立主控台應用程式，執行指定命令](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e)。|
|[Runspace02 程式碼範例](./runspace02-code-samples.md)|這個範例會使用[System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別，以執行`Get-Process`cmdlet 以同步方式。|
|[RunSpace03 程式碼範例](./runspace03-code-samples.md)|這些是程式碼範例中所述的 runspace[建立主控台應用程式，執行指定指令碼](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68)。|
|[RunSpace04 程式碼範例](./runspace04-code-samples.md)|這是的程式碼範例會使用的 runspace [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行指令碼會產生終止錯誤。|
|[RunSpace05 程式碼範例](./runspace05-code-sample.md)|這是原始碼 Runspace05 範例中所述[設定 Runspace 使用 RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)。|
|[RunSpace06 程式碼範例](./runspace06-code-sample.md)|這是原始碼 Runspace06 範例中所述[設定使用 Windows PowerShell 嵌入式管理單元的 Runspace](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)。|
|[RunSpace07 程式碼範例](./runspace07-code-sample.md)|這是原始碼 Runspace07 範例中所述[建立主控台應用程式，新增命令至管線](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e)。|
|[RunSpace08 程式碼範例](./runspace08-code-sample.md)|這是原始碼 Runspace08 範例中所述[建立主控台應用程式，將命令參數](http://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba)。|
|[RunSpace09 程式碼範例](./runspace09-code-sample.md)|這是原始碼 Runspace09 範例中所述[建立主控台應用程式，會叫用管線以非同步方式](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)。|
|[RunSpace10 程式碼範例](./runspace10-code-sample.md)|這是 Runspace10 範例中，新增到 cmdlet 的原始程式碼[System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然後建立 runspace 中使用修改過的組態資訊。|

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)