---
external help file: Remove-DscConfigurationDocument.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-DscConfigurationDocument
ms.openlocfilehash: d3e9b15dfeea94921503247adc08b291eed9d7d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203936"
---
# Remove-DscConfigurationDocument

## 概要
從 DSC 設定存放區移除設定文件。

## SYNTAX

```
Remove-DscConfigurationDocument -Stage <Stage> [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>]
 [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
`Remove-DscConfigurationDocument`Cmdlet 會從 Windows PowerShell Desired State Configuration (DSC) 設定存放區移除設定檔 ( mof 檔案) 。
在設定期間，此 `Start-DscConfiguration` Cmdlet 會將 mof 檔案複製到目的電腦上的資料夾。
此 Cmdlet 會移除該設定文件，並進行其他清除工作。

此 Cmdlet 僅適用于2014年11月更新彙總套件的一部分，可從 Microsoft 支援服務程式庫 [Windows RT 8.1、Windows 8.1 和 Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) 。

## 範例

### 範例 1：移除目前的設定文件

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Remove-DscConfigurationDocument -Stage Current -CimSession $Session
```

第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 $Session 變數儲存 **CimSession** 物件。
此命令會提示您輸入密碼。
如需詳細資訊，請鍵入 `Get-Help New-CimSession`。

第二個命令會針對 $Session 中儲存之 **CimSession** 所指定的電腦移除目前設定文件。

## PARAMETERS

### -AsJob
指出此 Cmdlet 會以背景工作方式執行命令。

如果您指定 *AsJob* 參數，此命令就會傳回代表工作的物件，然後顯示命令提示字元。
您可以繼續在工作階段中運作，直到工作完成。
工作會在本機電腦上建立，而來自遠端電腦的結果則會自動傳回到本機電腦。
若要管理工作，請使用各項 Job Cmdlet。
若要取得工作結果，請使用 Receive-Job Cmdlet。

若要使用這個參數，本機電腦和遠端電腦必須針對遠端執行功能進行設定，並且在 Windows Vista 和更新版本的 Windows 作業系統上，您必須使用 [以系統管理員身分執行] 選項來開啟 Windows PowerShell。
如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。

如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 和 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)。

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
輸入電腦名稱稱或會話物件，例如 **CimSession** 或 **CimSession** Cmdlet 的輸出。

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

### -Force
指出此 Cmdlet 會在移除設定文件之前，先停止執行中的設定工作。
強制執行命令而不要求使用者確認。

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

### -Stage
指定要移除的設定文件。
您可以指定多份文件。
此參數可接受的值為：

- Current。
移除說明系統目前狀態的設定文件。
- Pending。
移除說明系統暫止狀態的設定文件。
- Previous。
移除說明系統先前狀態的設定文件。

```yaml
Type: Microsoft.PowerShell.Cmdletization.GeneratedTypes.RemoveDscConfigurationDocument.Stage
Parameter Sets: (All)
Aliases:
Accepted values: Current, Pending, Previous

Required: True
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

### -Confirm
在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

## 輸出

### 無

## 注意

## 相關連結

[Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)
