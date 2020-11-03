---
external help file: Get-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfiguration
ms.openlocfilehash: 42b24e72de4c4bcc9326d52861c08a05853b18e0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203964"
---
# Get-DscConfiguration

## 概要
取得節點的目前設定。

## SYNTAX

```
Get-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [<CommonParameters>]
```

## DESCRIPTION
如果設定存在， **update-dscconfiguration 指令程式** 會取得目前的節點設定。
使用通用訊息模型 (CIM) 工作階段指定電腦。
如果您沒有指定目標電腦，此 Cmdlet 會從本機電腦取得設定。

## 範例

### 範例1：取得本機電腦的設定

```
PS C:\> Get-DscConfiguration
```

此命令會取得本機電腦的目前狀態。

### 範例2：取得指定電腦的設定

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Get-DscConfiguration -CimSession $Session
```

此範例會從 CIM 會話指定的電腦取得目前的狀態。
這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。
或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。

第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 **$Session** 變數儲存 **CimSession** 物件。
此命令會提示您輸入密碼。
如需詳細資訊，請鍵入 `Get-Help New-CimSession`。

第二個命令會取得以 **$Session** 變數儲存的 **CimSession** 物件所識別之電腦的目前設定，在此案例中為名為 Server01 的電腦。

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
在遠端工作階段或遠端電腦上執行 Cmdlet。
輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。
預設為本機電腦上的目前工作階段。

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
如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。
節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。

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

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
