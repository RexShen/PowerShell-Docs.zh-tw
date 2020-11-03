---
description: PowerShell Core 的設定檔，取代登錄設定。
keywords: powershell
Locale: en-US
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: fd4467845cf2b895401a55cbb7abd88b7b72af76
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207295"
---
# <a name="about-powershell-config"></a>關於 PowerShell 設定

## <a name="short-description"></a>簡短描述
PowerShell Core 的設定檔，取代登錄設定。

## <a name="long-description"></a>詳細描述

檔案 `powershell.config.json` 包含 PowerShell Core 的設定。 PowerShell 會在啟動時載入此設定。 您也可以在執行時間修改這些設定。 先前，這些設定會儲存在適用于 PowerShell 的 Windows 登錄中，但現在會包含在檔案中，以啟用 macOS 和 Linux 上的設定。

> [!WARNING]
> 如果檔案 `powershell.config.json` 包含不正確 JSON PowerShell，則無法啟動互動式會話。
> 如果發生這種情況，您必須修正設定檔案。

> [!NOTE]
> 無法辨識的金鑰或設定檔中的無效值將會以無訊息方式略過。

### <a name="allusers-shared-configuration"></a>AllUsers (共用) 設定

`powershell.config.json`目錄中的檔案 `$PSHOME` 會定義從該 PowerShell Core 安裝執行的所有 PowerShell Core 會話的設定。

> [!NOTE]
> `$PSHOME`位置會定義為與執行中 System.Management.Automation.dll 元件相同的目錄。 這也適用于託管的 PowerShell SDK 實例。

### <a name="currentuser-per-user-configurations"></a>CurrentUser (每位使用者) 設定

您也可以將檔案放在使用者範圍設定目錄中，以每個使用者為基礎來設定 PowerShell。 您可以使用命令，在各平臺上找到使用者設定目錄 `Split-Path $PROFILE.CurrentUserCurrentHost` 。

## <a name="general-configuration-settings"></a>一般組態設定

### <a name="executionpolicy"></a>ExecutionPolicy

> [!IMPORTANT]
> 此設定僅適用于 Windows 平臺。

設定 PowerShell 會話的執行原則，以決定可執行檔腳本。 根據預設，PowerShell 會使用現有的執行原則。

針對 AllUsers 設定，這會設定 **LocalMachine** 執行原則。
針對 CurrentUser 設定，這會設定 **currentuser** 執行原則。

> [!NOTE]
> [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)當以叫用時，此 Cmdlet 會修改 AllUsers 設定檔中的這項設定 `-Scope LocalMachine` ，並在使用叫用時，修改 CurrentUser 設定檔中的這項設定 `-Scope CurrentUser` 。

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

其中：

- `<shell-id>` 指的是目前 PowerShell 主機的識別碼。
  若是正常 PowerShell Core，則為 `Microsoft.PowerShell` 。
  在任何 PowerShell 會話中，您都可以使用來探索它 `$ShellId` 。
- `<execution-policy>` 參考有效的執行原則名稱。

下列範例會將 PowerShell 的執行原則設定為 `RemoteSigned` 。

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

在 Windows 中，可以在和下找到對等的登錄機碼 `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` `HKEY_LOCAL_MACHINE` `HKEY_CURRENT_USER` 。

### <a name="psmodulepath"></a>PSModulePath

覆寫此 PowerShell 會話的 PSModulePath 元件。 如果設定是針對目前的使用者，則設定 CurrentUser 模組路徑。 如果設定適用于所有使用者，請設定 AllUser 模組路徑。

> [!WARNING]
> 在這裡設定 AllUsers 或 CurrentUser 模組路徑，並不會變更 PowerShellGet 模組的限域安裝位置，例如 [Install 模組](/powershell/module/powershellget/install-module)。
> 這些 Cmdlet 一律會使用 *預設* 的模組路徑。

如果未設定任何值，則會使用各自模組路徑元件的預設值。 如需這些預設值的詳細資訊，請參閱 [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) 。

這項設定可讓您使用環境變數，方法是將它們嵌入 `%` 字元（例如 `"%HOME%\Documents\PowerShell\Modules"` ），方法與 CMD 允許的相同。 此語法也適用于 Linux 和 macOS。 如需範例，請參閱下文。

```Schema
"PSModulePath": "<ps-module-path>"
```

其中：

- `<ps-module-path>` 這是模組目錄的絕對路徑。 針對所有使用者設定，這是 AllUsers 共用模組目錄。 針對目前的使用者設定，這是 CurrentUser 模組目錄。

此範例顯示 Windows 環境的 PSModulePath 設定：

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

此範例顯示 macOS 或 Linux 環境的 PSModulePath 設定：

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

此範例示範如何在 PSModulePath 設定中內嵌環境變數。 請注意，使用 `HOME` 環境變數和 `/` 目錄分隔符號時，這會在 Windows、MacOS 和 Linux 上運作。

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

此範例示範如何在 PSModulePath 設定中內嵌環境變數，此環境變數只會在 macOS 和 Linux 上運作：

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> PowerShell 變數無法內嵌在 PSModulePath 設定中。
> Linux 和 macOS 上的 PSModulePath 設定會區分大小寫。 PSModulePath 設定必須針對平臺使用有效的目錄分隔符號。 在 macOS 和 Linux 上，這表示 `/` 。 在 Windows 中， `/` 和都 `\` 可以運作。

### <a name="experimentalfeatures"></a>ExperimentalFeatures

要在 PowerShell 中啟用的實驗性功能名稱。
依預設，不會啟用任何實驗性功能。
預設值為空陣列。

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

其中：

- `<experimental-feature-name>` 這是要啟用的實驗性功能名稱。

下列範例會啟用 PowerShell 啟動時的 **PSImplicitRemoting** 和 **PSUseAbbreviationExpansion** 實驗性功能。

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

如需實驗性功能的詳細資訊，請參閱 [POWERSHELL RFC 29][RFC0029]。

## <a name="non-windows-logging-configuration"></a>非 Windows 記錄設定

> [!IMPORTANT]
> 本節中的設定選項僅適用于 macOS 和 Linux。
> Windows 的記錄是由 Windows 事件檢視器所管理。

您可以在 PowerShell 設定檔中設定 PowerShell 在 macOS 和 Linux 上的記錄。 如需非 Windows 系統 PowerShell 記錄的完整說明，請參閱 [關於記錄](./about_Logging_Non-Windows.md)。

### <a name="logidentity"></a>LogIdentity

> [!IMPORTANT]
> 這項設定只能在 macOS 和 Linux 中使用。

設定用來寫入系統記錄檔的身分識別名稱。 預設值為 "powershell"。

```Schema
"LogIdentity": "<log-identity>"
```

其中：

- `<log-identity>` 這是 PowerShell 應用來寫入 syslog 的字串識別。

> [!NOTE]
> 您可能會想要針對每個已安裝的不同 PowerShell 實例，各有不同的 **LogIdentity** 值。

在此範例中，我們會設定 PowerShell 預覽版本的 **LogIdentity** 。

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a>LogLevel

> [!IMPORTANT]
> 這項設定只能在 macOS 和 Linux 中使用。

指定 PowerShell 應記錄的最低嚴重性層級。

```Schema
"LogLevel": "<log-level>|default"
```

其中：

- `<log-level>` 是下列其中一項：
  - 一律
  - 重大
  - [錯誤]
  - 警告
  - 資訊
  - 「詳細資訊」
  - 偵錯

> [!NOTE]
> 設定記錄層級會啟用其上方的所有記錄層級。

將此設定設為 [ **預設** 值]，將會被視為預設值。
預設值為 [ **資訊** ]。

下列範例會將值設定為 **Verbose** 。

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a>LogChannels

> [!IMPORTANT]
> 這項設定只能在 macOS 和 Linux 中使用。

決定要啟用的記錄通道。

```Schema
"LogChannels": "<log-channel>,..."
```

其中：

- `<log-channel>` 是下列其中一項：
  - 操作-記錄 PowerShell 活動的基本資訊
  - 分析-記錄更詳細的診斷資訊

預設值為 [可 **操作** ]。 若要同時啟用這兩個通道，請將這兩個值都包含為以逗號分隔的單一字串。 例如：

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a>LogKeywords

> [!IMPORTANT]
> 這項設定只能在 macOS 和 Linux 中使用。

決定要記錄的 PowerShell 部分。 預設會啟用所有的記錄關鍵字。 若要啟用多個關鍵字，請以單一逗號分隔字串列出值。

```Schema
"LogKeywords": "<log-keyword>,..."
```

其中：

- `<log-keyword>` 是下列其中一項：
  - 運行時-運行時管理
  - 管線管線作業
  - 通訊協定通訊通訊協定處理，例如 PSRP
  - 傳輸-傳輸層支援，例如 SSH
  - 主機-PowerShell 主機功能，例如主控台互動
  - Cmdlet-PowerShell 內建 Cmdlet
  - 序列化程式-序列化邏輯
  - 會話-PowerShell 會話狀態
  - ManagedPlugin-WSMan 外掛程式

> [!NOTE]
> 通常建議您將此值保留為未設定，除非您嘗試在 PowerShell 的已知部分中診斷特定行為。
> 變更此值只會減少記錄的資訊量。

此範例會將記錄限制為運行空間作業、管線邏輯和 Cmdlet 使用。 將會忽略所有其他記錄。

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a>更多範例設定

### <a name="example-windows-configuration"></a>Windows 設定範例

此設定會明確設定更多設定：

- 此 PowerShell 安裝的執行原則是 `AllSigned`
- CurrentUser 模組路徑設定為共用磁片磁碟機上的模組目錄
- `PSImplicitRemotingBatching`實驗性功能已啟用

> [!NOTE]
> `ExecutionPolicy`這裡的和 `PSModulePath` 設定只能在 Windows 平臺上運作，因為模組路徑使用 `\` 和 `;` 分隔字元，而且執行原則不 `Unrestricted` () UNIX 平臺上唯一允許的原則。

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a>非 Windows 設定範例

這項設定會設定一些選項，這些選項只適用于 macOS 或 Linux：

- CurrentUser 模組路徑設定為中的自訂模組目錄 `$HOME`
- 已啟用 **PSImplicitRemotingBatching** 實驗性功能
- PowerShell 記錄層級設定為 [ **詳細** 資訊]，以進行詳細記錄
- 此 PowerShell 安裝會使用 **home PowerShell** 身分識別來寫入記錄。

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a>另請參閱

[關於執行原則](./about_Execution_Policies.md)

[關於自動變數](./about_Automatic_Variables.md)

[RFC0029]: https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md

