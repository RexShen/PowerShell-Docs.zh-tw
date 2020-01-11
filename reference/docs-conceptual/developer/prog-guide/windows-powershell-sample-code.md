---
title: Windows PowerShell 範例程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1106829a-8ddc-454e-bbdd-ade15d4bffb4
caps.latest.revision: 7
ms.openlocfilehash: 89a1e6be94fe77e77b1b4be36e17314be37727e4
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870501"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell 範例程式碼

Windows PowerShell®範例可透過 Windows SDK 取得。 本節包含 Windows SDK 範例中包含的範例程式碼。

> [!NOTE]
> 安裝 Windows SDK 時，會建立一個**範例**目錄，其中提供所有的 Windows PowerShell 範例。 典型的安裝目錄是**C:\Program Files\Microsoft SDKs\Windows\v6.0**。 啟動 Windows PowerShell 並輸入 **"cd Samples\SysMgmt\PowerShell"** ，找出 Windows powershell Samples 目錄。 在本檔中，Windows PowerShell Samples 目錄稱為 **\<PowerShell 範例 >** 。

## <a name="sample-code-listing"></a>範例程式代碼清單

|                                    範例程式碼                                    |                                                                                                                                           說明                                                                                                                                           |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [AccessDbProviderSample01 程式碼範例](./accessdbprovidersample01-code-sample.md) | 這是[建立基本 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)中所述的提供者。                                                                                                                                                            |
| [AccessDbProviderSample02 程式碼範例](./accessdbprovidersample02-code-sample.md) | 這是[建立 Windows PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)中所述的提供者。                                                                                                                                                            |
| [AccessDbProviderSample03 程式碼範例](./accessdbprovidersample03-code-sample.md) | 這是[建立 Windows PowerShell 專案提供者](./creating-a-windows-powershell-item-provider.md)中所述的提供者。                                                                                                                                                              |
| [AccessDbProviderSample04 程式碼範例](./accessdbprovidersample04-code-sample.md) | 這是[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)中所述的提供者。                                                                                                                                                    |
| [AccessDbProviderSample05 程式碼範例](./accessdbprovidersample05-code-sample.md) | 這是[建立 Windows PowerShell 流覽提供者](./creating-a-windows-powershell-navigation-provider.md)中所述的提供者。                                                                                                                                                  |
| [AccessDbProviderSample06 程式碼範例](./accessdbprovidersample06-code-sample.md) | 這是[建立 Windows PowerShell 內容提供者](./creating-a-windows-powershell-content-provider.md)中所述的提供者。                                                                                                                                                        |
| [GetProc01 程式碼範例](./getproc01-code-samples.md)                             | 這是[建立您的第一個 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)中所述的基本 `Get-Process` Cmdlet 範例。                                                                                                                                                     |
| [GetProc02 程式碼範例](./getproc02-code-samples.md)                             | 這是[新增處理命令列輸入的參數](../cmdlet/adding-parameters-that-process-command-line-input.md)中所述的 `Get-Process` Cmdlet 範例。                                                                                                                       |
| [GetProc03 程式碼範例](./getproc03-code-samples.md)                             | 這是[新增處理管線輸入的參數](../cmdlet/adding-parameters-that-process-pipeline-input.md)中所述的 `Get-Process` Cmdlet 範例。                                                                                                                               |
| [GetProc04 程式碼範例](./getproc04-code-samples.md)                             | 這是[將非終止錯誤報表新增至您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 `Get-Process` Cmdlet 範例。                                                                                                                |
| [GetProc05 程式碼範例](./getproc05-code-samples.md)                             | 此 `Get-Process` Cmdlet 類似于[將非終止錯誤報表新增至您的 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)中所述的 Cmdlet。                                                                                                     |
| [StopProc01 程式碼範例](./stopproc01-code-samples.md)                           | 這是[建立修改系統的 Cmdlet](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md)中所述的 `Stop-Process` Cmdlet 範例。                                                                                                                                    |
| [StopProcessSample04 程式碼範例](./stopprocesssample04-code-samples.md)         | 這是[將參數集新增至 Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)中所述的 `Stop-Process` Cmdlet 範例。                                                                                                                                                      |
| [Runspace01 程式碼範例](./runspace01-code-samples.md)                           | 這些是[建立主控台應用程式（可執行指定的命令](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)）中所述之運行空間的程式碼範例。                                                                                      |
| [Runspace02 程式碼範例](./runspace02-code-samples.md)                           | 這個範例會使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別，以同步方式執行 `Get-Process` Cmdlet。                                                                                                            |
| [RunSpace03 程式碼範例](./runspace03-code-samples.md)                           | 這些是「建立執行指定腳本的主控台應用程式」中所述之運行空間的程式碼範例。                                                                                                                                                                         |
| [RunSpace04 程式碼範例](./runspace04-code-samples.md)                           | 這是使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)類別來執行腳本來產生終止錯誤的運行時的程式碼範例。                                                                         |
| [RunSpace05 程式碼範例](./runspace05-code-sample.md)                             | 這是[使用 RunspaceConfiguration 設定運行空間](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)中所述 Runspace05 範例的原始程式碼。                                                                                                           |
| [RunSpace06 程式碼範例](./runspace06-code-sample.md)                             | 這是[使用 Windows PowerShell 嵌入式管理單元設定運行](https://msdn.microsoft.com/a7289ee8-9732-49ee-91c7-d533e9538b83)時間中所述 Runspace06 範例的原始程式碼。                                                                                                    |
| [RunSpace07 程式碼範例](./runspace07-code-sample.md)                             | 這是[建立可將命令新增至管線的主控台應用程式](https://msdn.microsoft.com/01eb7808-e97b-4905-80be-9e2fa38c262e)中所述 Runspace07 範例的原始程式碼。                                                                                              |
| [RunSpace08 程式碼範例](./runspace08-code-sample.md)                             | 這是[建立可將參數新增至命令的主控台應用程式](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)中所述 Runspace08 範例的原始程式碼。                                                                                             |
| [RunSpace09 程式碼範例](./runspace09-code-sample.md)                             | 這是[建立以非同步方式叫用管線的主控台應用程式](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)中所述之 Runspace09 範例的原始程式碼。                                                                                        |
| [RunSpace10 程式碼範例](./runspace10-code-sample.md)                             | 這是 Runspace10 範例的原始程式碼，它會將 Cmdlet 新增至[Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) ，然後使用修改過的設定資訊來建立執行時間。 |

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)