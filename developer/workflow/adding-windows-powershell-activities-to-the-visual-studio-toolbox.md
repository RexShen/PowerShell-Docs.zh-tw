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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863564"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>新增 Windows PowerShell 活動至 Visual Studio 工具箱

您撰寫使用工作流程設計工具的 PowerShell 工作流程之前，您必須先將 PowerShell 活動加入的工具箱中的 Visual Studio 工作流程主控台應用程式專案。 下列程序示範如何從 Microsoft.PowerShell.Core.Activities 組件將活動加入至 Visual Studio 工具箱。

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Windows PowerShell 活動新增至工具箱

1. Visual Studio 中建立新的工作流程主控台應用程式專案。

2. 在 **檢視**功能表上，按一下**工具箱**。

3. 在 [工具箱] 加入新的索引標籤，工具箱內部按一下滑鼠右鍵，然後按一下**加入索引標籤**，並提供新的索引標籤的名稱，例如 「 PowerShell 活動 」。

   將索引標籤可讓您群組的 PowerShell 活動從 [工具箱] 中的其他工具不同。

4. 在新的工具箱索引標籤中，按一下 **選擇項目...**.**選擇工具箱項目**對話方塊隨即出現。

5. 在 **選擇工具箱項目** 對話方塊中，按一下**System.Activities**  索引標籤。

6. 按一下 **[瀏覽]**。

7. 瀏覽至 %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e 資料夾，然後按兩下 Microsoft.PowerShell.Core.Activities.dll。

8. 按一下 **[確定]**。 Microsoft.PowerShell.Core.Activities 組件所定義的活動現在已提供工具箱 中的。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 工作流程](./writing-a-windows-powershell-workflow.md)

[使用 Windows PowerShell 活動建立工作流程](./creating-a-workflow-with-windows-powershell-activities.md)