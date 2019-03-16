---
title: 使用 Windows PowerShell 活動建立工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055422"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>透過 Windows PowerShell 活動建立工作流程

您可以從 Visual Studio 工具箱中選取活動，並將它們拖曳至 [工作流程設計工具] 視窗，以建立 Windows PowerShell 工作流程。 如需將 Windows PowerShell 活動新增至 Visual Studio 工具箱，請參閱[至 Visual Studio 工具箱中新增 Windows PowerShell 活動](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)。

下列程序說明如何建立會檢查一組使用者指定電腦的網域狀態、 將它們加入網域，如果他們未已經加入，然後再檢查一次狀態的工作流程。

### <a name="setting-up-the-project"></a>設定專案

1. 請依照下列中的程序[新增 Windows PowerShell 活動新增到 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)來建立工作流程專案，並將從活動加入[Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)和[Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)至工具箱的組件。

2. 加入 System.Management.Automation、 Microsoft.PowerShell.Activities、 System.Management、 Microsoft.PowerShell.Management.Activities 和 Microsoft.PowerShell.Commands.Management 專案來做為參考組件。

### <a name="adding-activities-to-the-workflow"></a>將活動加入至工作流程

1. 新增**順序**至工作流程的活動。

2. 建立名為引數`ComputerName`的引數類型`String[]`。 這個引數表示要檢查和加入的電腦名稱。

3. 建立名為引數`DomainCred`型別的[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)。 這個引數代表有權將電腦加入網域的網域帳戶的網域認證。

4. 建立名為引數`MachineCred`型別的[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)。 這個引數代表檢查，並將 在電腦上的系統管理員的認證。

5. 新增**ParallelForEach**活動內**順序**活動。 請輸入`comp`並`ComputerName`中的文字方塊，讓迴圈逐一查看的項目`ComputerName`陣列。

6. 新增**順序**活動的主體**ParallelForEach**活動。 設定**DisplayName**屬性的順序`JoinDomain`。

7. 新增**GetWmiObject**活動**JoinDomain**順序。

8. 編輯的屬性**GetWmiObject**活動，如下所示。

   |屬性|值|
   |--------------|-----------|
   |**類別**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. 新增**AddComputer**活動**JoinDomain**序列之後**GetWmiObject**活動。

10. 編輯的屬性**AddComputer**活動，如下所示。

    |屬性|值|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. 新增**RestartComputer**活動**JoinDomain**序列之後**AddComputer**活動。

12. 編輯的屬性**RestartComputer**活動，如下所示。

    |屬性|值|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**認證**|MachineCred|
    |**For**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|True|
    |Wait|True|
    |PSComputerName|{""}|

13. 新增**GetWmiObject**活動**JoinDomain**序列之後**RestartComputer**活動。 編輯其屬性，以與先前相同**GetWmiObject**活動。

    當您完成程序時，工作流程的 [設計] 視窗應該如下所示。

    ![在工作流程設計工具中的 JoinDomain XAML](../media/joindomainworkflow.png)
    ![工作流程設計工具中的 JoinDomain XAML](../media/joindomainworkflow.png "JoinDomainWorkflow")