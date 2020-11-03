---
description: 描述如何在 Windows PowerShell 中執行遠端命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: ce75863c616bebcdb4a8273c287271b9feea3396
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207943"
---
# <a name="about-remote"></a>關於遠端

## <a name="short-description"></a>簡短描述

描述如何在 Windows PowerShell 中執行遠端命令。

## <a name="long-description"></a>詳細描述

您可以使用暫存或持續連線，在單一電腦或多部電腦上執行遠端命令。 您也可以啟動單一遠端電腦的互動式會話。

本主題提供一系列的範例，說明如何執行不同類型的遠端命令。 在您嘗試這些基本命令之後，請閱讀描述這些命令所使用之每個 Cmdlet 的說明主題。 這些主題會提供詳細資料，並說明如何修改命令以符合您的需求。

注意：若要使用 Windows PowerShell 遠端處理，必須設定本機和遠端電腦以進行遠端處理。 如需詳細資訊，請參閱[about_Remote_Requirements](about_Remote_Requirements.md)。

## <a name="how-to-start-an-interactive-session-enter-pssession"></a>如何啟動互動式會話 (輸入-PSSESSION) 

執行遠端命令最簡單的方式，就是啟動遠端電腦的互動式會話。

當會話啟動時，您輸入的命令會在遠端電腦上執行，就像您直接在遠端電腦上輸入一樣。 您只能在每個互動式會話中連接到一部電腦。

若要啟動互動式會話，請使用 Enter-PSSession Cmdlet。 下列命令會啟動 Server01 電腦的互動式會話：

```powershell
Enter-PSSession Server01
```

命令提示字元會變更，以指出您已連線到 Server01 電腦。

```
Server01\PS>
```

現在，您可以在 Server01 電腦上輸入命令。

若要結束互動式工作階段，請輸入：

```powershell
Exit-PSSession
```

如需詳細資訊，請參閱輸入-PSSession。

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a>如何使用具有 COMPUTERNAME 參數的 CMDLET 來取得遠端資料

有數個 Cmdlet 具有 ComputerName 參數，可讓您從遠端電腦取得物件。

因為這些 Cmdlet 不會使用 WS-MANAGEMENT 型 Windows PowerShell 遠端處理，所以您可以在執行 Windows PowerShell 的任何電腦上使用這些 Cmdlet 的 ComputerName 參數。 電腦不需要針對 Windows PowerShell 遠端進行設定，且電腦不需要符合遠端處理的系統需求。

下列 Cmdlet 具有 ComputerName 參數：

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

例如，下列命令會取得 Server01 遠端電腦上的服務：

```powershell
Get-Service -ComputerName Server01
```

一般而言，支援遠端處理而不需要特殊設定的 Cmdlet 具有 **ComputerName** 參數，且沒有 **Session** 參數。 若要在您的工作階段中尋找這些 Cmdlet，請輸入：

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a>如何執行遠端命令

若要在遠端電腦上執行其他命令，請使用 Invoke-Command Cmdlet。

若要執行單一命令或一些不相關的命令，請使用 Invoke-Command 的 ComputerName 參數來指定遠端電腦。 使用 ScriptBlock 參數來指定命令。

例如，下列命令會在 Server01 電腦上執行 Get-Culture 命令。

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

ComputerName 參數是針對您在一或多部電腦上執行單一命令或數個不相關命令的情況所設計。 若要建立連到遠端電腦的持續連線，請使用 Session 參數。

## <a name="how-to-create-a-persistent-connection-pssession"></a>如何建立 (PSSESSION) 的持續連線

當您使用 Invoke-Command Cmdlet 的 ComputerName 參數時，Windows PowerShell 只會針對命令建立連接。 然後，在命令完成時，就會關閉連線。 命令中所定義的任何變數或函數都會遺失。

若要建立連到遠端電腦的持續連線，請使用 New-PSSession Cmdlet。 例如，下列命令會在 Server01 和 Server02 電腦上建立 Pssession，然後將 Pssession 儲存在 $s 變數中。

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a>如何在 PSSESSION 中執行命令

您可以使用 PSSession 來執行一系列共用資料的遠端命令，例如函數、別名和變數的值。 若要在 PSSession 中執行命令，請使用 Invoke-Command Cmdlet 的 Session 參數。

例如，下列命令會使用 Invoke-Command Cmdlet，在 Server01 和 Server02 電腦上的 Pssession 中執行 Get-Process 命令。
命令會將 $p 變數中的處理常式儲存在每個 PSSession 中。

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

因為 PSSession 使用持續性連接，所以您可以在使用 $p 變數的相同 PSSession 中執行另一個命令。 下列命令會計算 $p 中儲存的進程數目。

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a>如何在多部電腦上執行遠端命令

若要在多部電腦上執行遠端命令，請在 [Invoke 命令的 ComputerName] 參數值中輸入所有電腦名稱稱。 以逗號分隔名稱。

例如，下列命令會在三部電腦上執行 Get-Culture 命令：

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

您也可以在多個 Pssession 中執行命令。 下列命令會在 Server01、Server02 和 Server03 電腦上建立 Pssession，然後在每個 Pssession 中執行 Get-Culture 命令。

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

若要包含電腦的 [本機電腦] 清單，請輸入本機電腦的名稱、輸入點 ( ) 或輸入 "localhost"。

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a>如何在遠端電腦上執行腳本

若要在遠端電腦上執行本機腳本，請使用 Invoke 命令的 FilePath 參數。

例如，下列命令會在 S1 和 S2 電腦上執行 Sample.ps1 腳本：

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

腳本的結果會傳回到本機電腦。 您不需要複製任何檔案。

## <a name="how-to-stop-a-remote-command"></a>如何停止遠端命令

若要中斷命令，請按 CTRL + C。 中斷要求會傳遞至遠端電腦，以終止遠端命令。

## <a name="for-more-information"></a>詳細資訊

- 如需遠端處理系統需求的詳細資訊，請參閱 [about_Remote_Requirements](about_Remote_Requirements.md)。

- 如需如何格式化遠端輸出的說明，請參閱 [about_Remote_Output](about_Remote_Output.md)。

- 如需遠端處理運作方式、如何管理遠端資料、特殊設定、安全性問題和其他常見問題的詳細資訊，請參閱 [about_Remote_FAQ](about_Remote_FAQ.md)。

- 如需解決遠端處理錯誤的說明，請參閱 about_Remote_Troubleshooting。

- 如需 Pssession 和持續連接的詳細資訊，請參閱 [about_PSSessions](about_PSSessions.md)。

- 如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](about_Jobs.md)。

## <a name="keywords"></a>關鍵 字

about_Remoting

## <a name="see-also"></a>另請參閱

[about_PSSessions](about_PSSessions.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_FAQ](about_Remote_FAQ.md)

[about_Remote_TroubleShooting](about_Remote_TroubleShooting.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
