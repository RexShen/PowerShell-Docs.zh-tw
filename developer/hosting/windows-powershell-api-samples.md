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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082578"
---
# <a name="windows-powershell-api-samples"></a>Windows PowerShell API 範例

本節包含示範如何建立 runspace，以限制功能，以及如何以非同步方式執行命令，使用提供的 runspace 的 runspace 集區的範例程式碼。 您可以使用 Microsoft Visual Studio 來建立主控台應用程式，然後將從這一節的主題的程式碼複製到主應用程式。

## <a name="in-this-section"></a>在本節中

[範例 PowerShell01](./windows-powershell01-sample.md)這個範例示範如何使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件來限制的 runspace 的功能。 此範例的輸出會示範如何限制的 runspace、 如何將標示為私用的 cmdlet、 如何新增和移除 cmdlet 和提供者，將語言模式如何新增 proxy 命令，以及其他等等。

[PowerShell02 範例](./windows-powershell02-sample.md)這個範例示範如何使用 runspace 的 runspace 集區，以非同步方式執行命令。 此範例會產生一份命令，並再執行這些命令，而 Windows PowerShell 引擎便會開啟 runspace 從集區會在需要時。