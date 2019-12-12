---
title: 將 Windows PowerShell 活動新增至 Visual Studio 工具箱 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359647"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>新增 Windows PowerShell 活動至 Visual Studio 工具箱

使用工作流程設計工具撰寫 PowerShell 工作流程之前，您必須先將 PowerShell 活動新增至 Visual Studio 工作流程主控台應用程式專案中的 [工具箱]。 下列程式顯示如何將活動從 [Microsoft] [...] 元件新增至 [Visual Studio 工具箱]。

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>將 Windows PowerShell 活動新增至工具箱

1. 在 Visual Studio 中建立新的工作流程主控台應用程式專案。

2. 在 [檢視] 功能表上，按一下 [工具箱]。

3. 在 [工具箱] 中按一下滑鼠右鍵，然後按一下 [加入索引標籤 **]** ，在 [工具箱] 中加入新的索引標籤，然後為新的索引標籤命名，例如「PowerShell 活動」。

   新增索引標籤可讓您將 PowerShell 活動與 [工具箱] 中的其他工具分開分組。

4. 在 [新增工具箱] 索引標籤上，按一下 **[選擇專案**]。[**選擇工具箱專案**] 對話方塊隨即出現。

5. 在 [**選擇工具箱專案**] 對話方塊中，按一下 [**系統活動**] 索引標籤。

6. 按一下 \[瀏覽\]。

7. 流覽至%WINDIR%\Microsoft.NET\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.Activities\v4.0_3.0.0. 0__31bf3856ad364e 資料夾，然後按兩下 [Microsoft]。

8. 按一下 **[確定]** 。 在 [工具箱] 中，現在可以使用 [Microsoft] [活動] 元件所定義的活動。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 工作流程](./writing-a-windows-powershell-workflow.md)

[使用 Windows PowerShell 活動建立工作流程](./creating-a-workflow-with-windows-powershell-activities.md)