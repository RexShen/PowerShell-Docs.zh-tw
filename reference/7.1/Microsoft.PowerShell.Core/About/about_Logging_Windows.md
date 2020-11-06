---
description: PowerShell 會將引擎、提供者和 Cmdlet 的內部作業記錄至 Windows 事件記錄檔。
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: 960394838097e4bfad1af5f4f0af7a813a50e761
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355012"
---
# <a name="about-logging-windows"></a>關於記錄視窗

## <a name="short-description"></a>簡短描述
PowerShell 會將引擎、提供者和 Cmdlet 的內部作業記錄至 Windows 事件記錄檔。

## <a name="long-description"></a>完整描述

PowerShell 會記錄 PowerShell 作業的詳細資料，例如啟動和停止引擎和提供者，以及執行 PowerShell 命令。

> [!NOTE]
> Windows PowerShell 版本3.0、4.0、5.0 和5.1 包含 Windows 事件記錄檔的 **EventLog** Cmdlet。 在這些版本中，若要顯示 **EventLog** Cmdlet 的清單，請輸入： `Get-Command -Noun EventLog` 。 如需詳細資訊，請參閱 Windows PowerShell 之版本的 Cmdlet 檔和 about_EventLogs。

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a>在 Windows 上查看 PowerShell 事件記錄檔專案

您可以使用 Windows 事件檢視器來查看 PowerShell 記錄檔。 事件記錄檔位於 [應用程式和服務記錄檔] 群組中，並命名為 `PowerShellCore` 。 相關聯的 ETW 提供者 `GUID` 為 `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` 。

啟用腳本區塊記錄時，PowerShell 會將下列事件記錄到記錄檔中 `PowerShellCore/Operational` ：

|  欄位  |       值       |
| ------- | ----------------- |
| EventId | `4104` / `0x1008` |
| 通路 | `Operational`     |
| 層級   | `Verbose`         |
| OpCode  | `Create`          |
| Task    | `CommandStart`    |
| 關鍵字 | `Runspace`        |

### <a name="registering-the-powershell-event-provider-on-windows"></a>在 Windows 上註冊 PowerShell 事件提供者

不同于 Linux 或 macOS，Windows 需要註冊事件提供者，然後才能將事件寫入事件記錄檔。 若要啟用 PowerShell 事件提供者，請從已提升許可權的 PowerShell 提示字元中執行下列命令。

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a>在 Windows 上取消註冊 PowerShell 事件提供者

註冊事件提供者會在用來解碼事件的二進位程式庫中放置鎖定。 若要更新此程式庫，必須取消註冊此提供者，才能釋放此鎖定。

若要取消註冊 PowerShell 提供者，請從已提升許可權的 PowerShell 提示字元執行下列命令。

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

更新 PowerShell 之後，請執行 `$PSHOME\RegisterManifest.ps1` 以註冊更新的事件提供者。

## <a name="enabling-script-block-logging"></a>啟用腳本區塊記錄

當您啟用腳本區塊記錄時，PowerShell 會記錄其處理的所有腳本區塊的內容。 啟用之後，任何新的 PowerShell 會話都會記錄此資訊。

> [!NOTE]
> 建議您在針對診斷目的以外的任何專案使用腳本區塊記錄時，啟用受保護的事件記錄（如下所述）。

您可以透過群組原則或登錄設定來啟用腳本區塊記錄。

### <a name="using-group-policy"></a>使用群組原則

若要啟用自動轉譯，請 `Turn on PowerShell Script Block
Logging` 在群組原則中啟用此功能 `Administrative Templates -> Windows
Components -> Windows PowerShell` 。

### <a name="using-the-registry"></a>使用登錄

執行下列函式：

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a>受保護的事件記錄

提高系統上的記錄層級，可增加記錄內容可能包含機密資料的可能性。 例如，在啟用腳本記錄的情況下，您可以將腳本所使用的認證或其他機密資料寫入事件記錄檔。 當已記錄機密資料的電腦遭到入侵時，記錄檔可以為攻擊者提供延伸其觸及範圍所需的資訊。

為了保護這種資訊，Windows 10 引進了受保護的事件記錄。
受保護的事件記錄可讓參與的應用程式加密寫入事件記錄檔的機密資料。 稍後，您可以在更安全且集中式的記錄收集器上解密和處理這些記錄。

使用 IETF 密碼編譯訊息語法 (CMS) 標準來保護事件記錄檔內容。 CMS 使用公開金鑰加密。 用來加密內容和解密內容的金鑰會分開保存。

公開金鑰可以廣泛共用，而不是機密資料。 使用這個公開金鑰加密的任何內容都只能透過私密金鑰進行解密。 如需公開金鑰加密的詳細資訊，請參閱 [維琪百科-公開金鑰密碼](https://en.wikipedia.org/wiki/Public-key_cryptography)編譯。

若要啟用受保護的事件記錄原則，請將公開金鑰部署至具有要保護之事件記錄檔資料的所有電腦。 相對應的私密金鑰會用來在更安全的位置（例如中央事件記錄檔收集器，或 [SIEM][] 匯總工具）後置處理事件記錄檔。 您可以在 Azure 中設定 SIEM。 如需詳細資訊，請參閱 [泛型 SIEM 整合](/cloud-app-security/siem)。

### <a name="enabling-protected-event-logging-via-group-policy"></a>透過群組原則啟用受保護的事件記錄

若要啟用受保護的事件記錄，請 `Enable Protected Event Logging` 在群組原則中啟用此功能 `Administrative Templates -> Windows Components
-> Event Logging` 。 這項設定需要加密憑證，您可以使用下列其中一種形式提供：

- 以64編碼的 x.509 憑證的內容 (例如， `Export` 憑證管理員) 中的選項所提供的內容。
- 可在本機電腦憑證存放區中找到之憑證的指紋 (可由 PKI 基礎結構) 部署。
- 憑證 (的完整路徑可以是本機或遠端共用) 。
- 包含憑證的目錄路徑或憑證 (可以是本機或遠端共用) 。
- 可在本機電腦憑證存放區中找到之憑證的主體名稱， (可以由 PKI 基礎結構) 來部署。

產生的憑證必須有 `Document Encryption` 增強金鑰使用 `1.3.6.1.4.1.311.80.1` 方法 () ，以及 `Data Encipherment` `Key
Encipherment` 啟用或金鑰使用方式。

> [!WARNING]
> 私密金鑰不應部署至機器記錄事件。 它應該保留在您解密訊息的安全位置。

### <a name="decrypting-protected-event-logging-messages"></a>解密受保護的事件記錄訊息

下列腳本將會取得和解密，假設您有私密金鑰：

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a>請參閱

[about_Logging_Non-Windows](about_Logging_Non-Windows.md)

[PowerShell Blue Team](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[一般 SIEM 整合](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
