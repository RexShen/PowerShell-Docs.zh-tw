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
ms.openlocfilehash: 12b0b246b78142f3811f9f566cd94e4dabd40cc9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557460"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>透過 Windows PowerShell 活動建立工作流程

您可以從 [Visual Studio 工具箱] 選取 [活動]，並將其拖曳至 [工作流程設計工具] 視窗，以建立 Windows PowerShell 工作流程。 如需將 Windows PowerShell 活動新增至 Visual Studio 工具箱的詳細資訊，請參閱[將 Windows Powershell 活動新增至 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)。

下列程式說明如何建立可檢查使用者指定之電腦群組的網域狀態的工作流程、將它們加入網域（如果尚未聯結），然後重新檢查狀態。

### <a name="setting-up-the-project"></a>設定專案

1. 依照[將 Windows PowerShell 活動新增至 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)中的程式，建立工作流程專案，並將活動從[microsoft. powershell. 活動](/dotnet/api/Microsoft.PowerShell.Activities)和[microsoft. powershell 管理](/dotnet/api/Microsoft.PowerShell.Management.Activities)元件新增至 [工具箱]。

2. 將 [管理]、[microsoft]、[系統管理]、[]、[microsoft]、[管理] 和 [] 專案新增為 [參考元件]。

### <a name="adding-activities-to-the-workflow"></a>將活動新增至工作流程

1. 將 [**序列**] 活動新增至工作流程。

2. 建立名為 `ComputerName` 且引數類型為的引數 `String[]` 。 這個引數代表要檢查和聯結的電腦名稱稱。

3. 建立名為的引數，其 `DomainCred` 類型為[system.web](/dotnet/api/System.Management.Automation.PSCredential)。 此引數代表已獲授權將電腦加入網域之網域帳戶的網域認證。

4. 建立名為的引數，其 `MachineCred` 類型為[system.web](/dotnet/api/System.Management.Automation.PSCredential)。 此引數代表要檢查和聯結之電腦上系統管理員的認證。

5. 在 [**序列**] 活動內新增**ParallelForEach**活動。 `comp` `ComputerName` 在文字方塊中輸入和，讓迴圈逐一查看陣列的元素 `ComputerName` 。

6. 將 [**序列**] 活動新增至**ParallelForEach**活動的主體。 將序列的**DisplayName**屬性設定為 `JoinDomain` 。

7. 將**GetWmiObject**活動新增至**JoinDomain**序列。

8. 編輯**GetWmiObject**活動的屬性，如下所示。

   |屬性|值|
   |--------------|-----------|
   |**類別**|"Win32_ComputerSystem"|
   |**PSComputerName**|背光|
   |**PSCredential**|MachineCred|

9. 將**AddComputer**活動新增至**GetWmiObject**活動後面的**JoinDomain**序列。

10. 編輯**AddComputer**活動的屬性，如下所示。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|背光|
    |**DomainCredential**|DomainCred|

11. 將**RestartComputer**活動新增至**AddComputer**活動後面的**JoinDomain**序列。

12. 編輯**RestartComputer**活動的屬性，如下所示。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|背光|
    |**認證**|MachineCred|
    |**對於**|WaitForServiceTypes 的 PowerShell。|
    |**使**|True|
    |等候|True|
    |PSComputerName|{""}|

13. 將**GetWmiObject**活動新增至**RestartComputer**活動後面的**JoinDomain**序列。 編輯其屬性，以與先前的**GetWmiObject**活動相同。

    當您完成程式時，工作流程設計視窗看起來應該像這樣。

    ![在工作流程設計工具中 JoinDomain XAML 在 ](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
     ![workflow designer 中 JoinDomain xaml](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")
