---
external help file: Get-DSCLocalConfigurationManager.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscLocalConfigurationManager
ms.openlocfilehash: 162770d8eb3a8953dcfaeb31f30742a46353b33b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203944"
---
# Get-DscLocalConfigurationManager

## 概要

取得節點的本機 Configuration Manager (LCM) 設定和狀態。

## SYNTAX

```
Get-DscLocalConfigurationManager [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Get-DscLocalConfigurationManager` Cmdlet 會取得節點的 lcm 設定、中繼設定和 lcm 的狀態。 使用通用訊息模型 (CIM) 工作階段指定電腦。 如果您沒有指定目標電腦，此 Cmdlet 會從本機電腦取得組態設定。

## 範例

### 範例1：取得本機電腦的 LCM 設定

```powershell
Get-DscLocalConfigurationManager
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 47edd8c9-2798-4827-839a-b35cc87e69fb
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName
```

此命令會取得本機電腦的 LCM 設定。

如需有關輸出之個別屬性的詳細資訊，請參閱設定 [本機 Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) 檔。

### 範例2：取得指定電腦的 LCM 設定

```powershell
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Get-DscLocalConfigurationManager -CimSession $Session
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 169dfa57-a7f9-43be-a7a5-9dd06587e052
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName                 : Server01
PSComputerName                 : Server01
```

此範例會取得 CIM 會話所指定之電腦的 LCM 設定。
這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。
或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。

第一個命令會使用 Cmdlet 建立 CIM 會話 `New-CimSession` ，然後將 **CimSession** 物件儲存在 $Session 變數中。 此命令會提示您輸入密碼。 如需詳細資訊，請鍵入 `Get-Help New-CimSession`。

第二個命令會取得儲存在 $Session 變數中的 **CimSession** 物件所識別之電腦的本機 Configuration Manager 設定。 在此案例中，名為 Server01 的電腦。

## PARAMETERS

### -AsJob

指出此 Cmdlet 會以背景工作方式執行命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

在遠端工作階段或遠端電腦上執行 Cmdlet。 輸入電腦名稱稱或會話物件，例如 `New-CimSession` 或 Cmdlet 的輸出 `Get-CimSession` 。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定為執行 Cmdlet 可建立的最大並行作業數。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

## 注意

## 相關連結

[Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/dscforengineers)

[Set-DscLocalConfigurationManager](Set-DscLocalConfigurationManager.md)
