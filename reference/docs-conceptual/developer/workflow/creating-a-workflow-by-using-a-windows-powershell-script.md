---
title: 使用 Windows PowerShell 腳本來建立工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: cc613240e056e8443b075019cbff6dd15da3716f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557443"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>使用 Windows PowerShell 指令碼建立工作流程

您可以撰寫 Windows PowerShell 腳本來建立工作流程。 若要建立工作流程，請在腳本主體之前，使用 workflow 關鍵字，後面接著工作流程名稱。 例如：

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

您可以透過與任何其他 Windows PowerShell 命令相同的方式來尋找工作流程。

## <a name="implementing-parallel-and-sequence"></a>實作為平行和順序

[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90))支援以平行方式執行活動。 若要在 Windows PowerShell 腳本中執行這項功能，請 `parallel` 在腳本區塊前面使用關鍵字。 您也可以使用 `foreach -parallel` 結構來平行逐一查看物件的集合。 若要在平行區塊內依序執行一組活動，請將活動群組括在腳本區塊中，然後在區塊前面加上 sequence 關鍵字。

## <a name="joining-computers-to-a-domain"></a>將電腦加入網域

下列腳本會建立一個工作流程，它會檢查使用者指定之電腦群組的網域狀態，並將它們加入網域（如果尚未聯結），然後重新檢查狀態。
這是[使用 Windows PowerShell 活動建立工作流程](./creating-a-workflow-with-windows-powershell-activities.md)中說明的 XAML 工作流程腳本版本。

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
