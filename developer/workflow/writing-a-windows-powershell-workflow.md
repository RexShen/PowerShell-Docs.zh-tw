---
title: 撰寫 Windows PowerShell 工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857404"
---
# <a name="writing-a-windows-powershell-workflow"></a>撰寫 Windows PowerShell 工作流程

您可以加入至工作流程設計工具在 Visual Studio 中的 Windows PowerShell 組件所公開的活動，以建立 XAML 工作流程。 下列 Windows PowerShell 組件公開 （expose) 啟用工作流程的活動。

> [!IMPORTANT]
> XAML 工作流程必須封裝成模組，如果您想要提供工作流程的說明。 如需模組的資訊，請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

- [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft.Powershell.Core.Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft.Powershell.Diagnostics.Activities](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft.Powershell.Security.Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft.Powershell.Utility.Activities](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  下列主題說明如何使用 Windows PowerShell 活動建立工作流程。

- [將 Windows PowerShell 活動加入至 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [使用 Windows PowerShell 活動建立工作流程](./creating-a-workflow-with-windows-powershell-activities.md)

- [使用 Windows PowerShell 指令碼建立工作流程](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [匯入和叫用 Windows PowerShell 工作流程](./importing-and-invoking-a-windows-powershell-workflow.md)

- [從 Windows PowerShell Cmdlet 建立工作流程活動](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)