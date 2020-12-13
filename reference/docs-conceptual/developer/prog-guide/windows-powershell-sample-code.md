---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 範例程式碼
description: Windows PowerShell 範例程式碼
ms.openlocfilehash: da916fa3557f44ecc9126ecef38235109aa391ec
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390128"
---
# <a name="windows-powershell-sample-code"></a>Windows PowerShell 範例程式碼

Windows PowerShell&reg; 範例可透過 Windows SDK 取得。 本節包含 Windows SDK 範例中的範例程式碼。

> [!NOTE]
> 安裝 Windows SDK 時，會建立 **範例** 目錄，您可在其中取得所有 Windows PowerShell 範例。 通常安裝目錄為 **C:\Program Files\Microsoft SDKs\Windows\v6.0**。 啟動 Windows PowerShell 並鍵入 **"cd Samples\SysMgmt\PowerShell"** ，以尋找 Windows PowerShell 範例目錄。 在本文件中，Windows PowerShell Samples 目錄會以 **\<PowerShell Samples>** 表示。

## <a name="sample-code-listing"></a>範例程式碼清單

|                                    範例程式碼                                    |                                                                                                                                           描述                                                                                                                                           |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [AccessDbProviderSample01 程式碼範例](./accessdbprovidersample01-code-sample.md) | 此為[建立基本 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)中所描述提供者。                                                                                                                                                            |
| [AccessDbProviderSample02 程式碼範例](./accessdbprovidersample02-code-sample.md) | 此為[建立 Windows 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)中所描述提供者。                                                                                                                                                            |
| [AccessDbProviderSample03 程式碼範例](./accessdbprovidersample03-code-sample.md) | 此為[建立 Windows 項目提供者](./creating-a-windows-powershell-item-provider.md)中所描述提供者。                                                                                                                                                              |
| [AccessDbProviderSample04 程式碼範例](./accessdbprovidersample04-code-sample.md) | 此為[建立 Windows 容器提供者](./creating-a-windows-powershell-container-provider.md)中所描述提供者。                                                                                                                                                    |
| [AccessDbProviderSample05 程式碼範例](./accessdbprovidersample05-code-sample.md) | 此為[建立 Windows 瀏覽提供者](./creating-a-windows-powershell-navigation-provider.md)中所描述提供者。                                                                                                                                                  |
| [AccessDbProviderSample06 程式碼範例](./accessdbprovidersample06-code-sample.md) | 此為[建立 Windows 內容提供者](./creating-a-windows-powershell-content-provider.md)中所描述提供者。                                                                                                                                                        |
| [GetProc01 程式碼範例](./getproc01-code-samples.md)                             | 此為[建立第一個 Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md) 中所描述基本 `Get-Process` Cmdlet 範例。                                                                                                                                                     |
| [GetProc02 程式碼範例](./getproc02-code-samples.md)                             | 此為[新增可處理命令列輸入的參數](../cmdlet/adding-parameters-that-process-command-line-input.md)中所描述 `Get-Process` Cmdlet 範例。                                                                                                                       |
| [GetProc03 程式碼範例](./getproc03-code-samples.md)                             | 此為[新增可處理管線輸入的參數](../cmdlet/adding-parameters-that-process-pipeline-input.md)中所描述 `Get-Process` Cmdlet 範例。                                                                                                                               |
| [GetProc04 程式碼範例](./getproc04-code-samples.md)                             | 此為[新增持續錯誤報告至 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md) 中所描述 `Get-Process` Cmdlet 範例。                                                                                                                |
| [GetProc05 程式碼範例](./getproc05-code-samples.md)                             | 此為與[新增持續錯誤報告至 Cmdlet](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md) 中所描述 Cmdlet 相似的 `Get-Process` Cmdlet 範例。                                                                                                     |
| [StopProc01 程式碼範例](./stopproc01-code-samples.md)                           | 此為[建立可修改系統的 Cmdlet](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md) 中所描述 `Stop-Process` Cmdlet 範例。                                                                                                                                    |
| [StopProcessSample04 程式碼範例](./stopprocesssample04-code-samples.md)         | 此為[新增參數集至 Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md) 中所描述 `Stop-Process` Cmdlet 範例。                                                                                                                                                      |
| [Runspace01 程式碼範例](./runspace01-code-samples.md)                           | 此為[建立執行指定命令的主控台應用程式](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)中所描述 Runspace 程式碼範例。                                                                                      |
| [Runspace02 程式碼範例](./runspace02-code-samples.md)                           | 此範例使用 [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 類別來同步執行 `Get-Process` Cmdlet。                                                                                                            |
| [RunSpace03 程式碼範例](./runspace03-code-samples.md)                           | 此為＜建立執行指定指令碼的主控台應用程式＞中所描述 Runspace 程式碼範例。                                                                                                                                                                         |
| [RunSpace04 程式碼範例](./runspace04-code-samples.md)                           | 此為 Runspace 的程式碼範例，該 Runspace 會使用 [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 類別來執行會產生終止錯誤的指令碼。                                                                         |
| [RunSpace05 程式碼範例](./runspace05-code-sample.md)                             |                                                                                                            |
| [RunSpace06 程式碼範例](./runspace06-code-sample.md)                             |                                                                                                     |
| [RunSpace07 程式碼範例](./runspace07-code-sample.md)                             |                                                                                               |
| [RunSpace08 程式碼範例](./runspace08-code-sample.md)                             |                                                                                              |
| [RunSpace09 程式碼範例](./runspace09-code-sample.md)                             |                                                                                       |
| [RunSpace10 程式碼範例](./runspace10-code-sample.md)                             | 這是 Runspace10 範例的原始程式碼，此原始程式碼會將 Cmdlet 新增至 [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration)，然後使用修改過的組態資訊來建立 Runspace。 |

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
