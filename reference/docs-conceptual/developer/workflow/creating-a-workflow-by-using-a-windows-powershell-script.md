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
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366027"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>使用 Windows PowerShell 指令碼建立工作流程

您可以撰寫 Windows PowerShell 腳本來建立工作流程。 若要建立工作流程，請在腳本主體之前，使用 workflow 關鍵字，後面接著工作流程名稱。 例如：

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

您可以透過與任何其他 Windows PowerShell 命令相同的方式來尋找工作流程。

## <a name="implementing-parallel-and-sequence"></a>實作為平行和順序

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx)支援以平行方式執行活動。 若要在 Windows PowerShell 腳本中執行這項功能，請在腳本區塊前面使用 `parallel` 關鍵字。 您也可以使用 `foreach -parallel` 結構來平行逐一查看物件的集合。 若要在平行區塊內依序執行一組活動，請將活動群組括在腳本區塊中，然後在區塊前面加上 sequence 關鍵字。

## <a name="joining-computers-to-a-domain"></a>將電腦加入網域

下列腳本會建立一個工作流程，它會檢查使用者指定之電腦群組的網域狀態，並將它們加入網域（如果尚未聯結），然後重新檢查狀態。 這是[使用 Windows PowerShell 活動建立工作流程](./creating-a-workflow-with-windows-powershell-activities.md)中說明的 XAML 工作流程腳本版本。

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