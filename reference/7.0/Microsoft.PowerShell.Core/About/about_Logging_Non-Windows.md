---
description: PowerShell 會記錄引擎、提供者和 Cmdlet 的內部作業。
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_non-windows?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging_Non-Windows
ms.openlocfilehash: 48f5177ed72c676056422307fa3915be9415952e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207384"
---
# <a name="about-logging-non-windows"></a>關於記錄非 Windows

## <a name="short-description"></a>簡短描述

PowerShell 會記錄引擎、提供者和 Cmdlet 的內部作業。

## <a name="long-description"></a>完整描述

Powershell 會記錄 PowerShell 作業的詳細資料。 例如，PowerShell 會記錄作業，例如啟動和停止引擎，以及啟動和停止提供者。 它也會記錄 PowerShell 命令的詳細資料。

PowerShell 記錄檔的位置取決於目標平臺。 在 **Linux** 上，您可以使用 PowerShell 記錄到 **syslog** 和 **rsyslog** 。 如需詳細資訊，請參閱 Linux 電腦的本機 `man` 頁面。 在 **macOS** 上，會使用 **os_log** 記錄系統。 如需詳細資訊，請參閱 [os_log 開發人員檔](https://developer.apple.com/documentation/os/os_log)。

## <a name="viewing-powershell-log-output-on-linux"></a>在 Linux 上查看 PowerShell 記錄檔輸出

PowerShell 記錄至 Linux 上的 **syslog** 以及通常用來查看 **syslog** 內容的任何工具。

記錄專案的格式會使用下列範本：

```
TIMESTAMP MACHINENAME powershell[PID]: (COMMITID:TID:CID)
  [EVENTID:TASK.OPCODE.LEVEL] MESSAGE
```

|欄位        |描述                                             |
|-------------|--------------------------------------------------------|
|`TIMESTAMP`  |產生記錄專案的日期/時間。            |
|`MACHINENAME`|產生記錄檔的系統名稱。      |
|`PID`        |寫入記錄專案之進程的處理序識別碼。 |
|`COMMITID`   |`git commit`用來產生組建的識別碼或標記。   |
|`TID`        |寫入記錄專案之執行緒的執行緒識別碼。   |
|`CID`        |記錄專案的十六進位通道識別碼。            |
|             |10 = 操作，11 = 分析                         |
|`EVENTID`    |記錄專案的事件識別碼。                  |
|`TASK`       |事件專案的工作識別碼                 |
|`OPCODE`     |事件專案的 opcode                          |
|`LEVEL`      |事件專案的記錄層級                       |
|`MESSAGE`    |與事件專案相關聯的訊息             |

> [!NOTE]
> `EVENTID`、 `TASK` 、 `OPCODE` 和在 `LEVEL` 記錄至 Windows 事件記錄檔時所使用的值相同。

### <a name="filtering-powershell-log-entries-using-rsyslog"></a>使用 rsyslog 篩選 PowerShell 記錄專案

一般來說，PowerShell 記錄檔專案會寫入 syslog 的預設值 `location/file` 。 **syslog** 不過，您可以將專案重新導向至自訂檔案。

1. 建立適用于 PowerShell 記錄檔設定的會議，並為) 提供小於 50 (的數位 `50-default.conf` ，例如 `40-powershell.conf` 。 檔案應放置在下方 `/etc/rsyslog.d` 。

1. 在檔案中新增下列專案：

   ```
   :syslogtag, contains, "powershell[" /var/log/powershell.log
   & stop
   ```

1. 請確定 `/etc/rsyslog.conf` 包含新的檔案。 通常，它會有類似下列設定的一般 include 語句：

   `$IncludeConfig /etc/rsyslog.d/*.conf`

   如果沒有，您必須手動加入 include 語句。

1. 請確定已適當設定屬性和許可權。

   ```
   -rw-r--r-- 1 root root   67 Nov 28 12:51 40-powershell.conf
   ```

1. 將擁有權設定為 **root** 。

   ```
   chown root:root /etc/rsyslog.d/40-powershell.conf
   ```

1. 設定存取權限： **根** 具有讀取/寫入， **使用者** 已讀取。

   ```
   chmod 644 /etc/rsyslog.d/40-powershell.conf
   ```

## <a name="viewing-powershell-log-output-on-macos"></a>在 macOS 上查看 PowerShell 記錄檔輸出

在 macOS 上查看 PowerShell 記錄檔輸出的最簡單方法是使用 **主控台** 應用程式。

1. 搜尋 **主控台** 應用程式並加以啟動。
1. 選取 [ **裝置** ] 下的電腦名稱稱。
1. 在 [ **搜尋** ] 欄位中，輸入 `pwsh` PowerShell 主要二進位檔。
1. 將搜尋篩選準則從變更 `Any` 為 `Process` 。
1. 執行作業。
1. （選擇性）儲存搜尋以供日後使用。

若要在 **主控台** 中篩選特定的 PowerShell 進程實例，變數 `$pid` 包含處理序識別碼。

1. 在 [ **搜尋** ] 欄位中輸入 **PID** (處理序識別碼) 。
1. 將搜尋篩選準則變更為 `PID` 。
1. 執行作業。

### <a name="viewing-powershell-log-output-from-a-command-line"></a>從命令列查看 PowerShell 記錄檔輸出

`log`命令可用於從命令列查看 PowerShell 記錄專案。

```
sudo log stream --predicate 'process == "pwsh"' --info
```

### <a name="persisting-powershell-log-output"></a>保存 PowerShell 記錄檔輸出

根據預設，PowerShell 會在 macOS 上使用預設僅限記憶體的記錄。 您可以使用命令來變更此行為，以啟用持續性 `log config` 。

下列腳本會啟用資訊層級記錄和持續性：

```
log config --subsystem com.microsoft.powershell --mode=persist:info,level:info
```

下列命令會將 PowerShell 記錄還原為預設狀態：

```
log config --subsystem com.microsoft.powershell --mode=persist:default,level:default
```

啟用持續性之後，您 `log show` 可以使用命令來匯出記錄專案。 此命令會提供選項，讓您匯出最後 N 個專案、指定時間之後的專案，或指定時間範圍內的專案。

例如，下列命令會在之後匯出專案 `9am on April 5 of 2018` ：

```
log show --info --start "2018-04-05 09:00:00" --predicate "process = 'pwsh'"
```

您可以藉 `log` 由 `log show --help` 執行以取得其他詳細資料，以取得的說明。

> [!TIP]
> 從 PowerShell 提示字元或腳本執行任何記錄檔命令時，請使用雙引號括住整個述詞字串和單引號內的單引號。 這樣就不需要在述詞字串內的雙引號字元之間進行換用。

您也可能想要考慮將事件記錄檔儲存至更安全的位置，例如中央事件記錄檔收集器，或 [SIEM][] 匯總工具。 您可以在 Azure 中設定 SIEM。 如需詳細資訊，請參閱 [泛型 SIEM 整合](/cloud-app-security/siem)。

## <a name="configuring-logging-on-a-non-windows-system"></a>在非 Windows 系統上設定記錄

在 Windows 上，您可以藉由建立 ETW 追蹤接聽項或使用事件檢視器來啟用分析記錄來設定記錄。 在 Linux 和 macOS 上，記錄是使用檔案進行設定 `powershell.config.json` 。 本節的其餘部分將討論如何在非 Windows 系統上設定 PowerShell 記錄。

PowerShell 預設會啟用操作通道的資訊記錄。 這表示，PowerShell 所產生的任何記錄輸出，都會標示為可操作，而且會記錄 (追蹤) 層級大於資訊的記錄。 診斷有時可能需要額外的記錄輸出，例如詳細資訊記錄檔輸出或啟用分析記錄檔輸出。

檔案 `powershell.config.json` 是位於 PowerShell 目錄中的 **JSON** 格式檔案 `$PSHOME` 。 PowerShell 的每個安裝都會使用自己的此檔案複本。 若為正常操作，此檔案會保持不變。 雖然它可能很有用，但若要變更檔案中的某些設定，以進行診斷或區分相同系統上的多個 PowerShell 版本，或甚至多個相同版本的複本 (請參閱 `LogIdentity` 下表) 。

下列程式碼是範例設定：

```json
{
  "Microsoft.PowerShell:ExecutionPolicy": "RemoteSigned",
  "PowerShellPolicies": {
    "ScriptExecution": {
      "ExecutionPolicy": "RemoteSigned",
      "EnableScripts": true
    },
    "ScriptBlockLogging": {
      "EnableScriptBlockInvocationLogging": true,
      "EnableScriptBlockLogging": true
    },
    "ModuleLogging": {
      "EnableModuleLogging": false,
      "ModuleNames": [
        "PSReadline",
        "PowerShellGet"
      ]
    },
    "ProtectedEventLogging": {
      "EnableProtectedEventLogging": false,
      "EncryptionCertificate": [
        "Joe"
      ]
    },
    "Transcription": {
      "EnableTranscripting": true,
      "EnableInvocationHeader": true,
      "OutputDirectory": "F:\\tmp\\new"
    },
    "UpdatableHelp": {
      "DefaultSourcePath": "f:\\temp"
    },
    "ConsoleSessionConfiguration": {
      "EnableConsoleSessionConfiguration": false,
      "ConsoleSessionConfigurationName": "name"
    }
  },
  "LogLevel": "verbose"
}
```

下表列出設定 PowerShell 記錄的屬性。 以星號標示的值（例如 `Operational*` ）表示檔案中未提供任何值時的預設值。

|屬性   |值        |描述                                  |
|-----------|--------------|---------------------------------------------|
|`LogIdentity`| (字串名稱)  |記錄時要使用的名稱。 根據預設，  |
|           |powershell   |powershell 是身分識別。 此值可以是|
|           |              |用來分辨兩者之間的差異      |
|           |              |PowerShell 安裝的實例，例如 |
|           |              |發行版本和搶鮮版（Beta）。 此值為 |
|           |              |也可用來將記錄檔輸出重新導向至        |
|           |              |Linux 上的個別檔案。 請參閱|
|           |              |**rsyslog** 以上。                           |
|`LogChannels`|手術  |要啟用的通道。 分隔值|
|           |分析      |指定多個時使用逗號。  |
|`LogLevel`   |一律        |指定單一值。 值會啟用  |
|           |重大      |本身和其上方的所有值        |
|           |錯誤         |列出左邊。                            |
|           |警告       |                                             |
|           |資訊|                                             |
|           |「詳細資訊」       |                                             |
|           |偵錯         |                                             |
|`LogKeywords`|Runspace      |關鍵字提供限制記錄的功能|
|           |管線      |PowerShell 內的特定元件。 依據 |
|           |通訊協定      |預設會啟用並變更所有關鍵詞 |
|           |傳輸     |此值僅適用于非常           |
|           |主機          |專門的疑難排解。                |
|           |指令程式       |                                             |
|           |serializer    |                                             |
|           |工作階段       |                                             |
|           |ManagedPlugin |                                             |

## <a name="see-also"></a>另請參閱

針對 Linux **syslog** 和 **rsyslog** 資訊，請參閱 linux 電腦的本機 `man` 頁面。

如需 macOS **os_log** 資訊，請參閱 [os_log 開發人員檔](https://developer.apple.com/documentation/os/os_log)。

[about_Logging_Windows](about_Logging_Windows.md)

[一般 SIEM 整合](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
