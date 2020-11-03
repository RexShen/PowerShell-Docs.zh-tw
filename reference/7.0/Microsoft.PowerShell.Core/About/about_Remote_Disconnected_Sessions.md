---
description: 說明如何中斷連線並重新連線至 PowerShell 會話 (PSSession) 。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: f4dbcd4d9255e4285687692902a41a3f3f40e093
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208187"
---
# <a name="about-remote-disconnected-sessions"></a>關於遠端中斷連線的會話

## <a name="short-description"></a>簡短描述

說明如何中斷連線並重新連線至 PowerShell 會話 (PSSession) 。

## <a name="long-description"></a>完整描述

從 PowerShell 3.0 開始，您可以從 PSSession 中斷連線，然後重新連接到同一部電腦或不同電腦上的 PSSession。 會話狀態會保持不變，而 PSSession 中的命令會在會話中斷連接時繼續執行。

只有當遠端電腦執行 PowerShell 3.0 或更新版本時，才能使用 [已中斷連線的會話] 功能。

[已中斷連線的會話] 功能可讓您關閉建立 PSSession 的會話，甚至關閉 PowerShell 並關閉電腦，而不會中斷 PSSession 中執行的命令。 已中斷連線的會話適用于執行需要花費很長時間才能完成的命令，並提供 IT 專業人員所需的時間和裝置彈性。

您無法從使用 Cmdlet 啟動的互動式會話中斷連線 `Enter-PSSession` 。

您可以使用已中斷連線的會話來管理因電腦或網路中斷而意外中斷連線的 Pssession。

在實際使用中，已中斷連線的會話功能可讓您開始解決問題、將注意力轉換成較高優先順序的問題，然後繼續在解決方案上工作，甚至是在不同的電腦上的其他位置。

## <a name="disconnected-session-cmdlets"></a>已中斷連線的會話 Cmdlet

下列 Cmdlet 支援已中斷連線的會話功能：

- `Connect-PSSession`：連接到中斷連線的 PSSession。
- `Disconnect-PSSession`：中斷 PSSession 的連接。
- `Get-PSSession`：取得本機電腦或遠端電腦上的 Pssession。
- `Receive-PSSession`：取得在已中斷連線的會話中執行的命令結果。
- `Invoke-Command`： **InDisconnectedSession** 參數會建立 PSSession 並立即中斷連接。

## <a name="how-the-disconnected-sessions-feature-works"></a>中斷連線的會話功能如何運作

從 PowerShell 3.0 開始，Pssession 與建立它們的會話無關。 作用中的 Pssession 會在連線的遠端電腦或 **伺服器端** 上維持，即使建立 PSSession 的會話已關閉，且原始電腦已關閉或中斷與網路的連線。

在 PowerShell 2.0 中，從遠端電腦中斷與原始會話或建立它的會話的連線時，會刪除該 PSSession。

當您中斷連線 PSSession 時，PSSession 會保持作用中狀態，並在遠端電腦上進行維護。 會話狀態 **會從 [執行中]** 變更為 [已 **中斷** 連線]。 您可以從目前的會話或相同電腦上的不同會話，或從不同的電腦重新連接到中斷連線的 PSSession。 維護會話的遠端電腦必須正在執行，且必須連接到網路。

中斷連線的 PSSession 中的命令會在遠端電腦上繼續執行，直到命令完成或輸出緩衝區填滿為止。 若要防止完整輸出緩衝區暫停命令，請使用 **OutputBufferingMode** `Disconnect-PSSession` 、 `New-PSSessionOption` 或 Cmdlet 的 OutputBufferingMode 參數 `New-PSTransportOption` 。

中斷連線的會話會維持在遠端電腦上的中斷線上狀態。 您可以使用這些方法來重新連接，直到您刪除 PSSession 為止（例如使用 `Remove-PSSession` Cmdlet），或直到 PSSession 的閒置超時時間過期為止。 您可以使用、或 Cmdlet 的 **IdleTimeoutSec** 或 **IdleTimeout** 參數，來調整 PSSession 的閒置時間 `Disconnect-PSSession` `New-PSSessionOption` `New-PSTransportOption` 。

另一位使用者可以連接到您建立的 Pssession，但只有在可以提供用來建立會話的認證時，或是使用會話設定的 `RunAs` 認證。

## <a name="how-to-get-pssessions"></a>如何取得 Pssession

從 PowerShell 3.0 開始，此 `Get-PSSession` Cmdlet 會在本機電腦和遠端電腦上取得 pssession。 它也可以取得在目前會話中建立的 Pssession。

若要在本機電腦或遠端電腦上取得 Pssession，請使用 **ComputerName** 或 **ConnectionUri** 參數。 如果沒有參數，則會 `Get-PSSession` 取得在本機會話中建立的 PSSession （不論它們終止的位置為何）。

取得 Pssession 時，請記得在維護的電腦（也就是遠端或 **伺服器端** 電腦）上尋找它們。

例如，如果您建立 Server01 電腦的 PSSession，請從 Server01 電腦取得該會話。 如果您從另一部電腦建立 PSSession 至本機電腦，請從本機電腦取得會話。

下列命令順序顯示如何 `Get-PSSession` 運作。

第一個命令會建立 Server01 電腦的會話。 會話位於 Server01 電腦上。

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

若要取得會話，請使用值為 Server01 的 **ComputerName** 參數 `Get-PSSession` 。

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

如果 **ComputerName** 參數的值 `Get-PSSession` 是 localhost，會 `Get-PSSession` 取得在上終止的 pssession，並且在本機電腦上進行維護。 即使是在本機電腦上啟動，也不會在 Server01 電腦上取得 Pssession。

```powershell
Get-PSSession -ComputerName localhost
```

若要取得在目前會話中建立的會話，請使用 `Get-PSSession` 不含參數的 Cmdlet。 在此範例中， `Get-PSSession` 會取得在目前會話中建立並連接到 Server01 電腦的 PSSession。

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a>如何中斷會話的連線

若要中斷連接 PSSession，請使用 `Disconnect-PSSession` Cmdlet。 若要識別 PSSession，請使用 **Session** 參數，或從 `New-PSSession` 或 Cmdlet 到的管線 `Get-PSSession` `Disconnect-PSSession` 。

下列命令會中斷連接 PSSession 與 Server01 電腦的連線。
請注意， **State** 屬性的值已 **中斷** 連線，而且 **可用性** 為 **None** 。

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

若要建立已中斷連線的會話，請使用 Cmdlet 的 **InDisconnectedSession** 參數 `Invoke-Command` 。 它會建立會話、啟動命令，然後立即中斷連線，然後命令才會傳回任何輸出。

下列命令會 `Get-WinEvent` 在 Server02 遠端電腦上的已中斷連線會話中執行命令。

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a>如何連接到已中斷連線的會話

您可以從建立 PSSession 的會話，或從本機電腦或其他電腦上的其他會話，連接到任何可用的中斷連線 PSSession。

您可以建立 PSSession、在 PSSession 中執行命令、中斷連接 PSSession、關閉 PowerShell，然後關閉電腦。 數小時之後，您可以開啟不同的電腦、取得 PSSession、連接到該電腦，並取得在 PSSession 中斷連接時在 PSSession 中執行的命令結果。 然後，您可以在會話中執行更多命令。

若要連接中斷連線的 PSSession，請使用 `Connect-PSSession` Cmdlet。 您可以使用 **ComputerName** 或 **ConnectionUri** 參數來識別 pssession，或從管線到的 `Get-PSSession` 管線 `Connect-PSSession` 。

下列命令會取得 Server02 電腦上的會話。 輸出包含兩個已中斷連線的會話，兩者皆可使用。

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

下列命令會連接到 Session2。 PSSession 現在已開放且可供使用。

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a>如何取得結果

若要取得在中斷連線的 PSSession 中執行之命令的結果，請使用 `Receive-PSSession` Cmdlet。

您可以使用 `Receive-PSSession` 而不是使用 `Connect-PSSession` Cmdlet。 如果會話已重新連接，則 `Receive-PSSession` 會取得會話中斷連線時執行的命令結果。 如果 PSSession 仍中斷連接，則會 `Receive-PSSession` 連接到它，然後取得在中斷連接時執行的命令結果。

`Receive-PSSession` 可以在作業 (中，以非同步方式傳回結果) 或以同步方式) 主機程式 (。 使用 **OutTarget** 參數來選取 **作業** 或 **主機** 。 預設值為 **Host** 。 但是，如果所接收的命令是在目前會話中做為 **工作** 啟動，則預設會以 **作業** 形式傳回。

下列命令會使用指令 `Receive-PSSession` 程式來連線到 Server02 電腦上的 PSSession，並取得 `Get-WinEvent` 在 Session3 會話中執行之命令的結果。 此命令會使用 **OutTarget** 參數來取得 **作業** 中的結果。

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

若要取得作業的結果，請使用 `Receive-Job` Cmdlet。

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a>狀態和可用性屬性

中斷連線之 PSSession 的 **狀態** 和 **可用性** 屬性會告訴您會話是否可供您重新連接。

當 PSSession 連接到目前的會話時，它的狀態會 **開啟** ，而且 **可以使用** 它的可用性。 當您中斷與 PSSession 的連接時，PSSession 狀態會 **中斷** 連線，而且其可用性為 **None** 。

**State** 屬性的值是相對於目前工作階段。 值為「已 **中斷** 連線」表示 PSSession 未連接到目前的會話。 但是，這並不表示 PSSession 與所有會話中斷連接。 它可能連線不同的工作階段。

若要判斷您是否可以連接或重新連線到 PSSession，請使用 **Availability** 屬性。 [ **無** ] 值表示您可以連線至會話。 「 **忙碌** 」值表示您無法連接到 PSSession，因為它已連接到另一個會話。

下列範例會在同一部電腦上的兩個 PowerShell 會話中執行。
請注意，當 PSSession 中斷連接並重新連線時，每個會話中 **狀態** 和 **可用性** 屬性的變更值。

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

中斷連線的會話會一直保留在遠端電腦上，直到您將它們刪除為止，例如使用 `Remove-PSSession` Cmdlet 或它們超時。PSSession 的 **IdleTimeout** 屬性會決定已中斷連線的會話在被刪除之前的維護時間。

當 **心跳執行緒** 沒有收到回應時，pssession 就會閒置。
中斷會話的連線可讓它閒置並啟動 **IdleTimeout** 時鐘，即使命令仍在已中斷連線的會話中執行也是如此。 PowerShell 會將已中斷連線的會話視為作用中，但為閒置狀態。

建立和中斷會話的連線時，請確認 PSSession 中的閒置超時時間夠長，足以維持會話的需求，但前提是它在遠端電腦上耗用不必要的資源。

會話設定的 **IdleTimeoutMs** 屬性會決定使用會話設定之會話的預設閒置超時時間。 您可以覆寫預設值，但您使用的值不能超過會話設定的 **MaxIdleTimeoutMs** 屬性。

若要尋找會話設定的 **IdleTimeoutMs** 和 **MaxIdleTimeoutMs** 值的值，請使用下列命令格式。

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

您可以覆寫會話設定中的預設值，並在建立 PSSession 以及中斷連接時，設定 PSSession 的閒置時間。

如果您是遠端電腦上 Administrators 群組的成員，您可以建立並變更會話設定的 **IdleTimeoutMs** 和 **MaxIdleTimeoutMs** 屬性。

## <a name="idle-timeout-values"></a>閒置超時值

會話設定和會話選項的閒置超時值是以毫秒為單位。 會話和會話設定選項的閒置超時值（以秒為單位）。

您可以在建立 PSSession (`New-PSSession` 、 `Invoke-Command`) 和 () 中斷連接時，設定 pssession 的閒置時間 `Disconnect-PSSession` 。 但是，當您連接到 **IdleTimeout** PSSession (`Connect-PSSession`) 或)  (取得結果時，無法變更 IdleTimeout 值 `Receive-PSSession` 。

`Connect-PSSession`和 `Receive-PSSession` Cmdlet 具有 **SessionOption** 參數，該參數會採用 **SessionOption** 物件，例如 Cmdlet 所傳回的物件 `New-PSSessionOption` 。 **SessionOption** 物件中的 **idletimeout** 值和喜好設定變數中的 **idletimeout** 值 `$PSSessionOption` 不會變更或命令中 PSSession 的 **idletimeout** 值 `Connect-PSSession` `Receive-PSSession` 。

若要建立具有特定閒置超時值的 PSSession，請建立 `$PSSessionOption` 喜好設定變數。 將 [ **IdleTimeout** ] 屬性的值設定為所需的值， (以毫秒為單位) 。

當您建立 Pssession 時，變數中的值 `$PSSessionOption` 會優先于會話設定中的值。

例如，下列命令會將閒置的時間設定為48小時：

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

若要建立具有特定閒置超時值的 PSSession，請使用 Cmdlet 的 **IdleTimeoutMSec** 參數 `New-PSSessionOption` 。 然後，在或 Cmdlet 的 **SessionOption** 參數值中使用 session 選項 `New-PSSession` `Invoke-Command` 。

建立會話時所設定的值會優先于 `$PSSessionOption` 喜好設定變數和會話設定中所設定的值。

例如：

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

若要在中斷連接時變更 PSSession 的閒置時間，請使用 Cmdlet 的 **IdleTimeoutSec** 參數 `Disconnect-PSSession` 。

例如：

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

若要建立具有特定閒置 timeout 和最大閒置超時時間的會話設定，請使用 Cmdlet 的 **IdleTimeoutSec** 和 **MaxIdleTimeoutSec** 參數 `New-PSTransportOption` 。 然後，在的 **TransportOption** 參數值中使用 transport 選項 `Register-PSSessionConfiguration` 。

例如：

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

若要變更會話設定的預設閒置 timeout 和最大閒置時間，請使用 Cmdlet 的 **IdleTimeoutSec** 和 **MaxIdleTimeoutSec** 參數 `New-PSTransportOption` 。 然後，在的 **TransportOption** 參數值中使用 transport 選項 `Set-PSSessionConfiguration` 。

例如：

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a>輸出緩衝模式

PSSession 的輸出緩衝處理模式會決定當 PSSession 的輸出緩衝區已滿時，如何管理命令輸出。

在中斷連線的會話中，輸出緩衝處理模式會在會話中斷連線時，有效地判斷命令是否繼續執行。

有效的值如下：

- **封鎖** 。 當輸出緩衝區已滿時，會暫停執行直到清除緩衝區為止。 預設值。
- **卸除** ： 當輸出緩衝區已滿時，會繼續執行。 當產生新的輸出時，會捨棄最舊的輸出。

**區塊** 會保留資料，但可能會中斷命令。 **Drop** 值允許命令完成，但可能會遺失資料。 使用 **Drop** 值時，請將命令輸出重新導向至磁碟上的檔案。 此值建議用於已中斷連線的會話。

會話設定的 **OutputBufferingMode** 屬性會決定使用會話設定之會話的預設輸出緩衝處理模式。

若要尋找會話設定的 **OutputBufferingMode** 值，您可以使用下列其中一種命令格式：

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

您可以覆寫會話設定中的預設值，並在您建立 PSSession、中斷連線和重新連線時，設定 PSSession 的輸出緩衝模式。

如果您是遠端電腦上 Administrators 群組的成員，您可以建立及變更會話設定的輸出緩衝處理模式。

若要使用 **drop** 的輸出緩衝處理模式來建立 PSSession，請建立一個 `$PSSessionOption` 喜好設定變數，其中 **OutputBufferingMode** 屬性的值為 **drop** 。

當您建立 Pssession 時，變數中的值 `$PSSessionOption` 會優先于會話設定中的值。

例如：

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

若要使用 **drop** 的輸出緩衝處理模式來建立 PSSession，請使用指令程式的 **OutputBufferingMode** 參數 `New-PSSessionOption` 來建立具有 **drop** 值的會話選項。 然後，在或 Cmdlet 的 **SessionOption** 參數值中使用 session 選項 `New-PSSession` `Invoke-Command` 。

建立會話時所設定的值會優先于 `$PSSessionOption` 喜好設定變數和會話設定中所設定的值。

例如：

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

若要在中斷連接時變更 PSSession 的輸出緩衝處理模式，請使用 Cmdlet 的 **OutputBufferingMode** 參數 `Disconnect-PSSession` 。

例如：

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

若要在重新連接時變更 PSSession 的輸出緩衝處理模式，請使用指令程式的 **OutputBufferingMode** 參數 `New-PSSessionOption` 來建立具有 **Drop** 值的會話選項。 然後，在或的 **SessionOption** 參數值中使用 session 選項 `Connect-PSSession` `Receive-PSSession` 。

例如：

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

若要建立具有預設輸出緩衝處理模式的會話設定 **，請** 使用指令程式的 **OutputBufferingMode** 參數 `New-PSTransportOption` 來建立具有 **drop** 值的傳輸選項物件。 然後，在的 **TransportOption** 參數值中使用 transport 選項 `Register-PSSessionConfiguration` 。

例如：

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

若要變更會話設定的預設輸出緩衝處理模式，請使用 Cmdlet 的 **OutputBufferingMode** 參數 `New-PSTransportOption` 來建立具有 **Drop** 值的傳輸選項。 然後，在的 **SessionOption** 參數值中使用 Transport 選項 `Set-PSSessionConfiguration` 。

例如：

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a>中斷回送會話

回送會話（或本機會話）是在同一部電腦上產生和終止的 Pssession。 如同其他 Pssession，作用中的回送會話會在本機電腦)  (連接的遠端電腦上維護，因此您可以中斷連線，並重新連線到回送會話。

根據預設，系統會使用網路安全性權杖來建立回送會話，而不允許在會話中執行命令來存取其他電腦。 您可以從本機電腦或遠端電腦上的任何會話，重新連接具有網路安全性權杖的回送會話。

但是，如果您使用、 **EnableNetworkAccess** 或 Cmdlet 的 EnableNetworkAccess `New-PSSession` 參數 `Enter-PSSession` `Invoke-Command` ，則會使用互動式安全性權杖來建立回送會話。 互動式權杖可讓您在回送會話中執行的命令，從其他電腦取得資料。

您可以中斷與互動式權杖的回送會話，然後從相同的會話或相同電腦上的不同會話重新連線至這些會話。
不過，若要防止惡意存取，您只能從其建立所在的電腦，使用互動式權杖重新連接回送會話。

## <a name="waiting-for-jobs-in-disconnected-sessions"></a>正在等待已中斷連線的會話中的工作

此 `Wait-Job` Cmdlet 會等到作業完成，然後再回到命令提示字元或下一個命令。 根據預設， `Wait-Job` 如果正在執行工作的會話已中斷連線，則會傳回。 若要指示 `Wait-Job` Cmdlet 在會話重新連線之前等候，請在 [已 **開啟** ] 狀態下，使用 **Force** 參數。 如需詳細資訊，請參閱 [等候工作](xref:Microsoft.PowerShell.Core.Wait-Job)。

## <a name="robust-sessions-and-unintentional-disconnection"></a>健全的會話和不慎中斷連接

PSSession 可能因為電腦失敗或網路中斷而意外中斷連線。 PowerShell 會嘗試復原 PSSession，但其成功與否取決於原因的嚴重性和持續時間。

不慎中斷連線的 PSSession 狀態可能已 **中斷** 或關閉，但也可能 **已****中斷** 連線。 如果 **狀態** 的值已 **中斷連接** ，您可以使用相同的技術來管理 PSSession，就像是在會話已刻意中斷連線的情況下一樣。 例如，您可以使用 `Connect-PSSession` 指令程式重新連線到會話，並使用 `Receive-PSSession` 指令程式取得會話中斷連線時執行的命令結果。

如果您關閉 (exit) 在 PSSession 中執行命令時，會在其中建立 PSSession 的會話，則 PowerShell 會在遠端電腦上維持 **中斷連接** 狀態的 pssession。 如果您關閉 (exit) 已建立 PSSession 的會話，但 PSSession 中沒有執行任何命令，則 PowerShell 不會嘗試維護 PSSession。

## <a name="see-also"></a>另請參閱

[about_Jobs](about_Jobs.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Session_Configurations](about_Session_Configurations.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Disconnect-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Receive-PSSession](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
