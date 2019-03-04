---
title: 使用 Windows PowerShell 指令碼建立工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853044"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>使用 Windows PowerShell 指令碼建立工作流程

您可以藉由撰寫 Windows PowerShell 指令碼建立工作流程。 若要建立工作流程，使用工作流程關鍵字後面的指令碼主體之前的工作流程的名稱。 例如：

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

您可以找到工作流程中相同的方式就和任何其他 Windows PowerShell 命令。

## <a name="implementing-parallel-and-sequence"></a>實作 Parallel 和 Sequence

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx)支援平行執行的活動。 若要使用 Windows PowerShell 指令碼中實作這項功能，使用`parallel`關鍵字前面的指令碼區塊。 您也可以使用`foreach -parallel`建構來逐一查看集合的物件，以平行方式。 若要平行區塊內依序執行一組活動，指令碼區塊括住該群組的活動，並在前面加上順序關鍵字的區塊。

## <a name="joining-computers-to-a-domain"></a>將電腦加入網域

下列指令碼會建立的工作流程，會檢查一組使用者指定電腦的網域狀態、 將它們加入網域，如果他們未已經加入，然後再檢查一次狀態。 這是 XAML 工作流程中所述的指令碼版本[使用 Windows PowerShell 活動建立工作流程](./creating-a-workflow-with-windows-powershell-activities.md)。

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```