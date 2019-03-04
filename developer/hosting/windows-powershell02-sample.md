---
title: Windows PowerShell02 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861064"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 範例

此範例示範如何使用 runspace 的 runspace 集區，以非同步方式執行命令。 此範例會產生一份命令，並再執行這些命令，而 Windows PowerShell 引擎便會開啟 runspace 從集區會在需要時。

## <a name="requirements"></a>需求

- 這個範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

此範例示範下列作業：

- 建立 RunspacePool 物件最小和最大數目的 runspace 可同時為開啟。

- 建立命令的清單。

- 以非同步方式執行命令。

- 呼叫[System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces)若要查看有多少 runspace 可用的方法。

- 擷取命令輸出[System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。

## <a name="example"></a>範例

此範例示範如何開啟的 runspace 的 runspace 集區，以及如何以非同步方式在那些 runspace 中執行命令。

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 主機應用程式](./writing-a-windows-powershell-host-application.md)