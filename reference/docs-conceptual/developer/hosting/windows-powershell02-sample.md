---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell02 範例
description: Windows PowerShell02 範例
ms.openlocfilehash: 61dedd72d93d4000edf9a12f12bbb49fbaeb9f3c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657348"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 範例

此範例示範如何使用執行空間集區的執行程式，以非同步方式執行命令。 此範例會產生命令清單，然後在 Windows PowerShell 引擎在需要時從集區開啟執行程式時，執行這些命令。

## <a name="requirements"></a>規格需求

- 此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

本範例示範以下項目:

- 建立 RunspacePool 物件，其允許同時開啟的最小和最大執行空間數目。
- 建立命令的清單。
- 以非同步方式執行命令。
- 呼叫 [Runspacepool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) 方法，查看有多少個可用的空間。
- 使用 [Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 方法，來捕捉命令輸出。

## <a name="example"></a>範例

此範例說明如何開啟執行空間集區的執行程式，以及如何以非同步方式在這些執行空間中執行命令。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 主機應用程式](./writing-a-windows-powershell-host-application.md)
