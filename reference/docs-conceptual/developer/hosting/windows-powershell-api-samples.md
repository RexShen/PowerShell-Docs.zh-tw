---
title: Windows PowerShell API 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360837"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API 範例

本節包含範例程式碼，示範如何建立可限制功能的執行空間，以及如何使用執行時間集區以非同步方式執行命令，以提供執行空間。 您可以使用 Microsoft Visual Studio 建立主控台應用程式，然後將此區段中的主題中的程式碼複製到您的主應用程式。

## <a name="in-this-section"></a>在本節中

[PowerShell01 範例](./windows-powershell01-sample.md)這個範例會示範如何使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件來限制執行時間的功能，。 這個範例的輸出示範如何限制執行時間的語言模式、如何將 Cmdlet 標示為私用、如何新增和移除 Cmdlet 和提供者、如何新增 proxy 命令等。

[PowerShell02 範例](./windows-powershell02-sample.md)這個範例會示範如何使用執行時間集區的執行程式，以非同步方式執行命令。 此範例會產生命令的清單，然後在 Windows PowerShell 引擎視需要從集區開啟執行時間時，執行這些命令。