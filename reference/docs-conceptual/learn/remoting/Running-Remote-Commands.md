---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: 執行遠端命令
ms.openlocfilehash: d6609deafd8dec4f34a8412439d87dacd20d46f1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030324"
---
# <a name="running-remote-commands"></a>執行遠端命令

您可以使用單一 PowerShell 命令，在一部或數百部電腦上執行命令。 Windows PowerShell 透過使用各種技術 (包括 WMI、RPC 與 WS) 支援遠端運算。

PowerShell Core 支援 WMI、WS-Management 與 SSH 遠端功能。 不再支援 RPC。

如需 PowerShell Core 中遠端功能的詳細資訊，請參閱下列文章：

- [PowerShell Core 中的 SSH 遠端功能][ssh-remoting]
- [PowerShell Core 中的 WSMan 遠端功能][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>不需設定的 Windows PowerShell 遠端功能

許多 Windows PowerShell Cmdlet 都有 ComputerName 參數，可讓您收集資料，並變更一或多部遠端電腦的設定。 這些 Cmdlet 使用各種不同的通訊協定，在不需任何特殊設定的所有 Windows 作業系統上運作。

這些 Cmdlet 包含：

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Clear-EventLog](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

一般而言，不需特殊設定即可支援遠端功能的 Cmdlet 具有 ComputerName 參數，而且沒有 Session 參數。 若要在您的工作階段中尋找這些 Cmdlet，請輸入：

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Windows PowerShell 遠端執行功能

使用 WS-Management 通訊協定，Windows PowerShell 遠端功能可讓您在一或多部遠端電腦上執行任何 Windows PowerShell 命令。 您可以建立持續連線、啟動互動式工作階段，以及在遠端電腦上執行指令碼。

若要使用 Windows PowerShell 遠端執行功能，必須針對遠端管理設定遠端電腦。
如需包括指示的詳細資訊，請參閱[關於遠端需求](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)。

設定 Windows PowerShell 遠端功能之後，就有許多遠端處理策略可供您使用。
本文只列出其中幾個。 如需詳細資訊，請參閱[關於遠端](/powershell/module/microsoft.powershell.core/about/about_remote)。

### <a name="start-an-interactive-session"></a>啟動互動式工作階段

若要啟動與單一遠端電腦的互動式工作階段，請使用 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) Cmdlet。
例如，若要啟動與 Server01 遠端電腦的互動式工作階段，請輸入：

```powershell
Enter-PSSession Server01
```

此命令提示字元會變更以顯示遠端電腦的名稱。 您在提示字元中輸入的所有命令都會在遠端電腦上執行，而結果均會顯示於本機電腦上。

若要結束互動式工作階段，請輸入：

```powershell
Exit-PSSession
```

如需 Enter-PSSession 與 Exit-PSSession Cmdlet 的詳細資訊，請參閱：

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Exit-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>執行遠端命令

若要在一或多部遠端電腦上執行命令，請使用 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) Cmdlet。 例如，若要在 Server01 與 Server02 遠端電腦上執行 [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) 命令，請輸入：

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

輸出會傳回到您的電腦。

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>執行指令碼

若要在一或多部遠端電腦上執行指令碼，請使用 `Invoke-Command` Cmdlet 的 FilePath 參數。 您的本機電腦上必須有該指令碼或可存取該指令碼。 結果會傳回到您的本機電腦。

例如，下列命令會在遠端電腦 (Server01 與 Server02) 上執行 DiskCollect.ps1 指令碼。

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>建立持續連線

使用 `New-PSSession` Cmdlet，在遠端電腦上建立一個持續性工作階段。 下列範例會在 Server01 與 Server02 上建立遠端工作階段。 工作階段物件會儲存在 `$s` 變數中。

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

現在，工作階段已建立，您可以在其中執行任何命令。 此外，由於工作階段是持續性的，因此，您可以從單一命令收集資料，並將它用於其他命令中。

例如，下列命令會在 $s 變數的工作階段中執行 Get-HotFix 命令，並將結果儲存在 $h 變數中。 $h 變數是在 $s 的每個工作階段中所建立，但在本機工作階段中不存在。

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

現在，您可以搭配相同工作階段中的其他命令來使用 `$h` 變數中的資料。 結果會顯示在本機電腦上。 例如：

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>進階遠端處理

Windows PowerShell 遠端管理在這裡開始。 使用 Windows PowerShell 安裝的 Cmdlet，您可以同時建立及設定本機與遠端電腦的遠端工作階段、建立自訂與受限制的工作階段、允許使用者從實際隱含執行於遠端工作階段的遠端工作階段匯入命令，以及設定遠端工作階段安全性等。

Windows PowerShell 包含 WSMan 提供者。 提供者會建立 `WSMAN:` 磁碟機，讓您可以完整瀏覽本機電腦與遠端電腦上組態設定的階層。

如需 WSMan 提供者的詳細資訊，請參閱 [WSMan 提供者](https://technet.microsoft.com/library/dd819476.aspx) \(英文\) 與[關於 WS-Management Cmdlet](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets)，或在 Windows PowerShell 主控台中，輸入 `Get-Help wsman`。

如需詳細資訊，請參閱：

- [關於遠端常見問題集](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

如需遠端處理錯誤的說明，請參閱 [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx)。

## <a name="see-also"></a>另請參閱

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [WSMan 提供者](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
