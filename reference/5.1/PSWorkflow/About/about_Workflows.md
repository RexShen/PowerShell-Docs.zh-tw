---
description: 提供 PowerShell 工作流程功能的簡介。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207211"
---
# <a name="about-workflows"></a>關於工作流程

## <a name="short-description"></a>簡短描述

提供 PowerShell 工作流程功能的簡介。

## <a name="long-description"></a>完整描述

PowerShell 工作流程帶來了 [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) 到 powershell 的優點，並可讓您撰寫和執行工作流程。

Powershell 工作流程是在 PowerShell 3.0 中引進，且模組最多可供 PowerShell 5.1 使用。 如需 PowerShell 工作流程的詳細資訊，請參閱 [工作流程指南](/previous-versions/powershell/scripting/components/workflows-guide) 和 [撰寫 Windows PowerShell 工作流程](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)。

## <a name="about-workflows"></a>關於工作流程

工作流程是由一系列順序的相關活動所組成的命令。 通常，它們會執行一段很長的時間、收集資料，以及對數百部電腦進行變更，通常是在不同的環境中。

您可以使用 XAML、Windows Workflow Foundation 中所使用的語言或 PowerShell 語言來撰寫工作流程。 工作流程通常封裝在模組中，並包含說明主題。 如需詳細資訊，請參閱 [XAML 總覽 (WPF) ](/dotnet/framework/wpf/advanced/xaml-overview-wpf)。

工作流程在 IT 環境中是很重要的，因為它們可以在重新開機後繼續進行，而不會從常見的失敗 您可以中斷連線，並從執行工作流程的電腦中斷連線，而不會中斷工作流程處理，並以透明方式暫停和繼續工作流程，而不會遺失 您可以記錄和審核工作流程中的每個活動，以供參考。
工作流程可作為工作執行，而且可以使用 PowerShell 的排程工作功能進行排程。

工作流程中的狀態和資料會在工作流程的開頭和結尾，以及您指定的點儲存或保存。 工作流程持續點的運作方式就像是資料庫快照集或程式檢查點，可保護工作流程免于中斷和失敗的影響。 如果工作流程無法從失敗中復原，您可以使用保存的資料並從最後一個持續點繼續，而不是從頭重新執行廣泛的工作流程。

## <a name="workflow-requirements-and-configuration"></a>工作流程需求和設定

PowerShell 工作流程設定是由下列元素所組成：

- 執行工作流程的用戶端電腦。
- 用戶端電腦或遠端電腦上的工作流程會話（ **PSSession** ）。
- 受管理的節點，受工作流程活動影響的目的電腦。

工作流程會話並非必要，但建議使用。 **Pssession** 可以利用 PowerShell 的健全修復和中斷連線會話功能來復原中斷連線的工作流程會話。 如需詳細資訊，請參閱 [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)

由於用戶端電腦和執行工作流程會話的電腦可以是受管理的節點，因此您可以在單一電腦上執行工作流程來滿足所有角色。

用戶端電腦和執行工作流程會話的電腦必須執行 PowerShell 3.0。 支援所有符合條件的系統，包括 Windows Server 作業系統的 Server Core 安裝選項。

若要執行包含 Cmdlet 的工作流程，受管理的節點必須有 Windows PowerShell 2.0 或更新版本。 除非工作流程包含 Cmdlet，否則受管理的節點不需要 PowerShell。 您可以在沒有 PowerShell 的電腦上執行包含 Windows Management Instrumentation (WMI) 和通用訊息模型 (CIM) 命令的工作流程。

## <a name="how-to-get-workflows"></a>如何取得工作流程

工作流程通常封裝在模組中。 若要匯入包含工作流程的模組，請使用模組中的任何命令或使用 `Import-Module` Cmdlet。
在模組中第一次使用任何命令時，會自動匯入模組。

若要在電腦上安裝的模組中尋找工作流程，請使用 `Get-Command` Cmdlet 的 **CommandType** 參數。

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a>如何執行工作流程

若要執行工作流程，請使用下列程式。

1. 當受管理的節點為本機電腦時，不需要執行此步驟。
   否則，請在用戶端電腦上使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. 在執行工作流程會話的電腦和包含 Cmdlet 的工作流程所影響的受管理節點上啟用 PowerShell 遠端功能。

   您只需要在每一部參與的電腦上執行此步驟一次。

   只有在執行包含 Cmdlet 的工作流程時，才需要執行此步驟。 除非工作流程會話是在用戶端電腦上執行，或是在任何執行 PowerShell 3.0 的受管理節點上執行，否則您不需要在用戶端電腦上啟用遠端功能。

   若要啟用遠端功能，請使用 `Enable-PSRemoting` Cmdlet。

   ```powershell
   Enable-PSRemoting -Force
   ```

   您可以使用 [ **開啟腳本執行** ] 群組原則設定來啟用遠端功能。 如需詳細資訊，請參閱 [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) 和 [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。

1. 使用 `New-PSWorkflowSession` 或 `New-PSSession` Cmdlet 來建立工作流程會話。

   此 `New-PSWorkflowSession` Cmdlet 會啟動一個會話，該會話會在目的地電腦上使用內建的 **Microsoft PowerShell. 工作流程** 會話設定。 此會話設定包括腳本、類型和格式化檔案，以及針對工作流程設計的選項。

   或者，使用 `New-PSSession` Cmdlet。 使用 **ConfigurationName** 參數來指定 **Microsoft PowerShell. 工作流程** 會話設定。 此命令與使用 `New-PSWorkflowSession` Cmdlet 相同。

   替代方法是使用 `New-PSSession` Cmdlet。 使用 **ConfigurationName** 參數來指定 **Microsoft PowerShell. 工作流程** 會話設定。

   在本機電腦上：

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   在遠端電腦上：

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   如果您是工作流程會話電腦的系統管理員，您可以使用 `New-PSWorkflowExecutionOption` Cmdlet 來建立工作流程會話設定的自訂選項設定。 而且，使用 `Set-PSSessionConfiguration` Cmdlet 來變更會話設定。

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. 在工作流程會話中執行工作流程。 若要指定受管理的節點（目的電腦）的名稱，請使用 **PSComputerName** 工作流程一般參數。

   下列範例會執行名為「 **測試-工作流程** 」的工作流程。

   其中受管理的節點是裝載工作流程會話的電腦：

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   受管理的節點是遠端電腦。

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   下列範例會在數百部電腦上執行 **測試工作流程** 。 `Get-Content`Cmdlet 會從文字檔中取得電腦名稱稱，並將它們儲存在 `$Servers` 本機電腦上的變數中。

   `Invoke-Command` 使用 `$Using` 範圍修飾符， `$Servers` 在本機會話中定義變數。 如需範圍修飾符的詳細資訊 `$Using` ，請參閱 [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)。

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a>使用工作流程一般參數

工作流程一般參數是 PowerShell 自動新增至所有工作流程的一組參數。 PowerShell 會將 Cmdlet 一般參數新增至所有工作流程，即使工作流程不使用 **CmdletBinding** 屬性。

例如，下列工作流程不會定義任何參數。 不過，當您執行工作流程時，它會同時具有 **CommonParameters** 和 **WorkflowCommonParameters** 。

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

工作流程一般參數包含多個執行工作流程的必要參數。 例如， **PSComputerName** 一般參數會指定工作流程影響的受管理節點。

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

**PSPersist** 工作流程一般參數會決定保存工作流程資料的時間。 它可讓您將活動之間的持續點新增至未定義持續點的工作流程。

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

其他工作流程一般參數可讓您指定受管理節點的遠端連線特性。 它們的名稱和功能與遠端 Cmdlet 的參數類似，包括 `Invoke-Command` 。

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

請小心將為工作流程會話定義連接的遠端參數，與定義受管理節點連線的 **PS** 前置工作流程一般參數進行區分。

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

某些工作流程一般參數對工作流程而言是唯一的，例如 **PSParameterCollection** 參數，可讓您為不同的遠端節點指定不同的工作流程一般參數值。 如需工作流程一般參數的清單和說明，請參閱 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)。

## <a name="see-also"></a>另請參閱

[Invoke-AsWorkflow](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[PSWorkflow](xref:PSWorkflow) Cmdlet

[工作流程指南](/previous-versions/powershell/scripting/components/workflows-guide)

[撰寫 Windows PowerShell 工作流程](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
