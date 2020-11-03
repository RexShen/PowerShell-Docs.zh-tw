---
description: 說明 (Pssession) 的 PowerShell 會話，並說明如何建立與遠端電腦的持續連線。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: ae7f5d06773253328c58f770595dd041c5ff6367
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207004"
---
# <a name="about-pssessions"></a>關於 Pssession

## <a name="short-description"></a>簡短描述
說明 (Pssession) 的 PowerShell 會話，並說明如何建立與遠端電腦的持續連線。

## <a name="long-description"></a>完整描述

若要在遠端電腦上執行 PowerShell 命令，您可以使用 Cmdlet 的 **ComputerName** 參數，也可以 (pssession) 建立 powershell 會話，然後在 pssession 中執行命令。

當您建立 PSSession 時，PowerShell 會建立與遠端電腦的持續連線。 使用 PSSession 在遠端電腦上執行一連串的相關命令。 在相同 PSSession 中執行的命令可以共用資料，例如變數、別名和函數的值。

您也可以在本機電腦上建立 PSSession，並在其中執行命令。
本機 PSSession 使用 PowerShell 遠端基礎結構來建立和維護 PSSession。

從 Windows PowerShell 3.0 開始，Pssession 與建立它們的會話無關。 作用中的 Pssession 會在遠端電腦上進行維護 (或連線) 的「伺服器端」電腦。 如此一來，您就可以從 PSSession 中斷連線，並在稍後從同一部電腦或不同的電腦重新連接到它。

本主題說明如何建立、使用、取得和刪除 Pssession。 如需更多的詳細資訊，請參閱 [about_PSSession_Details](about_PSSession_Details.md)。

注意： Pssession 使用 PowerShell 遠端基礎結構。 若要使用 Pssession，必須設定本機和遠端電腦以進行遠端處理。
如需詳細資訊，請參閱[about_Remote_Requirements](about_Remote_Requirements.md)。

在 Windows Vista 和更新版本的 Windows 中，若要在本機電腦上建立 PSSession，您必須使用 [以系統管理員身分執行] 選項啟動 PowerShell。

## <a name="what-is-a-session"></a>什麼是會話？

會話是 PowerShell 執行所在的環境。

每次啟動 PowerShell 時，系統就會為您建立會話，而且您可以在會話中執行命令。 您也可以將專案新增至您的會話（例如模組和嵌入式管理單元），也可以建立專案，例如變數、函式和別名。 這些專案只存在於會話中，而且會在會話結束時刪除。

您也可以在本機電腦或遠端電腦上建立使用者管理的會話，也就是所謂的「PowerShell 會話」或「Pssession」。 如同預設的會話，您可以在 PSSession 中執行命令，並加入和建立專案。 但是，不同于自動啟動的會話，您可以控制您所建立的 Pssession。 您可以取得、建立、設定和移除它們、中斷連接並重新連接，以及在相同的 PSSession 中執行多個命令。 PSSession 會保持可用，直到您將它刪除或超時為止。

一般來說，您會建立 PSSession，在遠端電腦上執行一連串的相關命令。 當您在遠端電腦上建立 PSSession 時，PowerShell 會建立與遠端電腦的持續連線以支援會話。

如果您使用或 Cmdlet 的 **ComputerName** 參數 `Invoke-Command` `Enter-PSSession` 執行遠端命令或啟動互動式會話，PowerShell 會在遠端電腦上建立暫時會話，並在命令完成或互動式會話結束時立即關閉會話。 您無法控制這些暫時性會話，也無法將它們用於單一命令或單一互動式會話。

在 PowerShell 中，「目前會話」是您正在使用的會話。 「目前的會話」可以參考任何會話，包括暫時性會話或 PSSession。

## <a name="why-use-a-pssession"></a>為何要使用 PSSession？

當您需要持續連線到遠端電腦時，請使用 PSSession。
您可以使用 PSSession 來執行一系列共用資料的命令，例如變數的值、函式的內容，或別名的定義。

您可以執行遠端命令，而不需要建立 PSSession。 使用已啟用遠端 Cmdlet 的 **ComputerName** 參數，在一或多部電腦上執行單一命令或一系列不相關的命令。

當您使用或的 **ComputerName** 參數 `Invoke-Command` 時 `Enter-PSSession` ，PowerShell 會建立連到遠端電腦的暫時連線，然後在命令完成時立即關閉連線。 當連接關閉時，您建立的任何資料元素都會遺失。

其他具有 **ComputerName** 參數的 Cmdlet （例如 `Get-Eventlog` 和）會 `Get-WmiObject` 使用不同的遠端技術來收集資料。 無建立持續連線，例如 PSSession。

## <a name="how-to-create-a-pssession"></a>如何建立 PSSession

若要建立 PSSession，請使用 `New-PSSession` Cmdlet。 若要在遠端電腦上建立 PSSession，請使用 Cmdlet 的 **ComputerName** 參數 `New-PSSession` 。

例如，下列命令會在 Server01 電腦上建立新的 PSSession。

```powershell
New-PSSession -ComputerName Server01
```

當您提交命令時，會 `New-PSSession` 建立 PSSession 並傳回代表 PSSession 的物件。 當您建立 PSSession 時，可以將物件儲存在變數中，或者您可以使用 `Get-PSSession` 命令，在稍後取得 pssession。

例如，下列命令會在 Server01 電腦上建立新的 PSSession，並將產生的物件儲存在 $ps 變數中。

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a>如何在多部電腦上建立 Pssession

若要在多部電腦上建立 Pssession，請使用 Cmdlet 的 **ComputerName** 參數 `New-PSSession` 。 在以逗號分隔的清單中輸入遠端電腦的名稱。

例如，若要在 Server01、Server02 和 Server03 電腦上建立 Pssession，請輸入：

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

`New-PSSession` 在每一部遠端電腦上建立一個 PSSession。

## <a name="how-to-get-pssessions"></a>如何取得 Pssession

若要取得在目前會話中建立的 Pssession，請使用 `Get-PSSession` 不含 **ComputerName** 參數的 Cmdlet。 `Get-PSSession` 傳回傳回的相同物件類型 `New-PSSession` 。

下列命令會取得在目前會話中建立的所有 Pssession。

```powershell
Get-PSSession
```

Pssession 的預設顯示會顯示其識別碼和預設顯示名稱。 當您建立會話時，可以指派替代的顯示名稱。

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

您也可以將 Pssession 儲存在變數中。 下列命令會取得 Pssession，並將它們儲存在 \$ ps123 變數中。

```powershell
$ps123 = Get-PSSession
```

使用 PSSession Cmdlet 時，您可以依識別碼、名稱或其實例識別碼來參考 PSSession， (GUID) 。 下列命令會依識別碼取得 PSSession，並將它儲存在 \$ ps01 變數中。

```powershell
$ps01 = Get-PSSession -Id 1
```

從 Windows PowerShell 3.0 開始，Pssession 會在遠端電腦上進行維護。 若要取得您在特定遠端電腦上建立的 Pssession，請使用 Cmdlet 的 **ComputerName** 參數 `Get-PSSession` 。 下列命令會取得您在 Server01 遠端電腦上建立的 Pssession。 這包括在目前會話中建立的 Pssession，以及在本機電腦或其他電腦上的其他會話中建立的。

```powershell
Get-PSSession -ComputerName Server01
```

在 Windows PowerShell 2.0 中， `Get-PSSession` 只會取得在目前會話中建立的 pssession。 它不會取得在其他會話或其他電腦上建立的 Pssession，即使會話連線到本機電腦上的命令也是如此。

## <a name="how-to-run-commands-in-a-pssession"></a>如何在 PSSession 中執行命令

若要在一或多個 Pssession 中執行命令，請使用 `Invoke-Command` Cmdlet。
使用 Session 參數指定 Pssession 和 **ScriptBlock** 參數來指定命令。

例如，若要 `Get-ChildItem` 在 $ps 123 變數中儲存的三個 pssession 中，執行 ( "dir" ) 命令，請輸入：

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a>如何刪除 Pssession

當您完成 PSSession 之後，請使用指令程式 `Remove-PSSession` 來刪除 pssession 並釋放它所使用的資源。

```powershell
Remove-PSSession -Session $ps
```

或

```powershell
Remove-PSSession -Id 1
```

若要從遠端電腦移除 PSSession，請使用 Cmdlet 的 **ComputerName** 參數 `Remove-PSSession` 。

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

如果您未刪除 PSSession，PSSession 仍可供使用，直到它超時為止。

您也可以使用 Cmdlet 的 **IdleTimeout** 參數 `New-PSSessionOption` 來設定閒置 PSSession 的到期時間。 如需詳細資訊，請參閱 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)。

## <a name="the-pssession-cmdlets"></a>PSSession Cmdlet

如需 PSSession Cmdlet 的清單，請輸入：

```powershell
Get-Help *-PSSession
```

- Connect-PSSession：將 PSSession 連接到目前的會話
- 中斷連線-PSSession：中斷目前會話的 PSSession 連接
- 輸入-PSSession：啟動互動式會話
- Exit-PSSession：結束互動式會話
- 取得-PSSession：取得目前會話中的 Pssession
- 新的-PSSession：在本機或遠端電腦上建立新的 PSSession
- 接收-PSSession：取得在中斷連線的會話中執行的命令結果
- 移除-PSSession：刪除目前會話中的 Pssession

## <a name="for-more-information"></a>詳細資訊

如需 Pssession 的詳細資訊，請參閱 [about_PSSession_Details](about_PSSession_Details.md)。

## <a name="see-also"></a>另請參閱

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Disconnect-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)
