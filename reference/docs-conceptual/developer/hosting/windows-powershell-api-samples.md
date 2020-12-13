---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell API 範例
description: Windows PowerShell API 範例
ms.openlocfilehash: b6336ae7a2abb98cbbaa69bf6c9455f893db2d94
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657540"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API 範例

本節包含的範例程式碼會示範如何建立可限制功能的執行程式，以及如何使用執行空間集區以非同步方式執行命令以提供執行空間。 您可以使用 Microsoft Visual Studio 來建立主控台應用程式，然後將本節中的主題的程式碼複製到您的主應用程式。

## <a name="in-this-section"></a>本節內容

[PowerShell01 範例](./windows-powershell01-sample.md) 這個範例示範如何使用 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 物件來限制執行時間的功能。 此範例的輸出會示範如何限制執行時間的語言模式、如何將 Cmdlet 標記為私用、如何新增和移除 Cmdlet 和提供者、如何新增 proxy 命令等等。

[PowerShell02 範例](./windows-powershell02-sample.md) 此範例示範如何使用執行空間集區的執行程式，以非同步方式執行命令。 此範例會產生命令清單，然後在 Windows PowerShell 引擎在需要時從集區開啟執行程式時，執行這些命令。
