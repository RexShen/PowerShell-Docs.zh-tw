---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2020
ms.locfileid: "93205295"
---
# Set-DscLocalConfigurationManager

## 概要

將本機 Configuration Manager (LCM) 設定套用至節點。

## SYNTAX

### ComputerNameSet (預設值)

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Set-DscLocalConfigurationManager` Cmdlet 會將 LCM 設定或中繼設定套用至節點。 透過指定電腦名稱或使用通用訊息模型 (CIM) 工作階段指定電腦。 如果您沒有指定目標電腦，此 Cmdlet 會將設定套用到本機電腦。

## 範例

### 範例1：套用 LCM 設定

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

此命令會將 LCM 設定套用 `C:\DSC\Configurations\` 至目標節點。 收到設定之後，LCM 會進行處理。

> [!WARNING]
> 如果相同的電腦上有多個中繼 mof 儲存在指定的資料夾中，則只會套用第一個中繼 mof。

### 範例2：使用 CIM 會話套用 LCM 設定

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

此範例會將 LCM 設定套用至電腦，並套用設定。 這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。 或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。

第一個命令會使用 Cmdlet 建立 CIM 會話 `New-CimSession` ，然後將 **CimSession** 物件儲存在 `$Session` 變數中。 此命令會提示您輸入密碼。 如需詳細資訊，請鍵入 `Get-Help New-CimSession`。

第二個命令會將目標節點的 LCM 設定套用 `C:\DSC\Configurations\` 至儲存在變數中的 **CimSession** 物件所識別的電腦 `$Session` 。 在此範例中， `$Session` 變數只會包含名為 Server01 之電腦的 CIM 會話。 此命令會套用這些設定。 收到設定之後，LCM 會進行處理。

## PARAMETERS

### -CimSession

在遠端工作階段或遠端電腦上執行 Cmdlet。 輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/CimCmdlets/New-CimSession) 或 [CimSession](/powershell/module/CimCmdlets/Get-CimSession) Cmdlet 的輸出。
預設為本機電腦上的目前工作階段。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

指定電腦名稱的陣列。 此參數會將 **Path** 參數中具有中繼設定檔的電腦限制為數組中指定的電腦。

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential

指定目標電腦的使用者名稱和密碼，做為 **PSCredential** 物件。 若要取得 **PSCredential** 物件，請使用 Get-credential Cmdlet。 如需詳細資訊，請鍵入 `Get-Help Get-Credential`。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

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

### -Path

指定包含組態設定檔之資料夾的檔案路徑。 此 Cmdlet 會發佈這些 LCM 設定，並將這些 LCM 設定套用至在指定路徑中具有設定檔案的電腦。 每個目標節點都必須具有下列格式的設定檔： `NetBIOS Name.meta.mof` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定為執行 Cmdlet 可建立的最大並行作業數。 如果省略此參數或輸入的值 `0` ，則 Windows PowerShell 會根據電腦上執行的 CIM Cmdlet 數目，計算 Cmdlet 的最佳節流限制。 節流限制僅適用於目前 Cmdlet，不適用於工作階段或電腦。

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

## 輸出

## 注意

## 相關連結

[Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/overview)

[Get-DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)
