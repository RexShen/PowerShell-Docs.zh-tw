---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203968"
---
# Get-DscConfigurationStatus

## 概要
抓取已完成設定執行的相關資料。

## SYNTAX

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## DESCRIPTION
Get-dscconfigurationstatus 指令 Cmdlet 會 **取得** 系統上已完成設定執行的詳細資訊。
根據預設，它會傳回上次設定執行的相關資訊。
此 Cmdlet 適用于尋找設定執行的歷程記錄資訊，例如執行設定的時間、執行的狀態、設定中的資源數目，以及哪些資源成功或失敗。

## 範例

### 範例1：取得上次設定執行的資訊

```
PS C:\> Get-DscConfigurationStatus
```

此命令會取得最後一次設定執行的資訊。

### 範例2：取得所有設定的資訊

```
PS C:\> Get-DscConfigurationStatus -All
```

此命令會取得系統上執行之所有設定的相關資訊，包括 Windows PowerShell Desired State Configuration (DSC) 一致性檢查。

### 範例3：取得在遠端電腦上執行設定的資訊

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

此命令會取得名為 Server01 之遠端電腦的設定執行詳細資料。
這會使用 WSMan 傳輸來連接遠端電腦，並要求連接的使用者必須是遠端電腦上的系統管理員。

## PARAMETERS

### -All
指出此 Cmdlet 會抓取電腦上所有設定執行的相關資訊，包括設定應用程式與一致性檢查。

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

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
