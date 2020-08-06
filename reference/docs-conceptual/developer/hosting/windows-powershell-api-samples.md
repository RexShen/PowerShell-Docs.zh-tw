---
title: Windows PowerShell API 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d7232bb16851f1d568cbdfc4374e287d0875adc8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780163"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API 範例

本節包含範例程式碼，示範如何建立可限制功能的執行空間，以及如何使用執行時間集區以非同步方式執行命令，以提供執行空間。 您可以使用 Microsoft Visual Studio 建立主控台應用程式，然後將此區段中的主題中的程式碼複製到您的主應用程式。

## <a name="in-this-section"></a>本節內容

[PowerShell01 範例](./windows-powershell01-sample.md)這個範例示範如何使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件來限制執行時間的功能。 這個範例的輸出示範如何限制執行時間的語言模式、如何將 Cmdlet 標示為私用、如何新增和移除 Cmdlet 和提供者、如何新增 proxy 命令等。

[PowerShell02 範例](./windows-powershell02-sample.md)這個範例會示範如何使用執行時間集區的執行程式，以非同步方式執行命令。 此範例會產生命令的清單，然後在 Windows PowerShell 引擎視需要從集區開啟執行時間時，執行這些命令。
