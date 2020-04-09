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
ms.openlocfilehash: 4d697e73ff4ab4cc4b88593f814d589f89005663
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978639"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 範例

這個範例會示範如何使用執行時間集區的執行空間，以非同步方式執行命令。 此範例會產生命令的清單，然後在 Windows PowerShell 引擎視需要從集區開啟執行時間時，執行這些命令。

## <a name="requirements"></a>需求

- 此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

這個範例示範下列作業：

- 建立 RunspacePool 物件，其中包含允許同時開啟的最小和最大執行空間數目。
- 建立命令清單。
- 以非同步方式執行命令。
- 呼叫[Runspacepool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces)方法，查看有多少個可用的多工。
- 使用[Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法，來捕捉命令輸出。

## <a name="example"></a>範例

這個範例會示範如何開啟執行時間集區的執行空間，以及如何以非同步方式在這些執行空間中執行命令。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 主應用程式](./writing-a-windows-powershell-host-application.md)
