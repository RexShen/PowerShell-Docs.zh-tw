---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203931"
---
# Start-DscConfiguration

## 概要
將組態套用至節點。

## SYNTAX

### ComputerNameAndPathSet (預設) 

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimSessionAndPathSet

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**Start-DscConfiguration** Cmdlet 會將組態套用至節點。
搭配 *UseExisting* 參數使用時，會套用目的電腦上的現有設定。
藉由指定電腦名稱稱或使用通用訊息模型 (CIM) 會話，指定您想要將設定套用到哪些電腦。

根據預設，此 Cmdlet 會建立工作，並傳回 **Job** 物件。
如需背景工作的詳細資訊，請輸入 `Get-Help about_Jobs` 。
若要以互動方式使用此 Cmdlet，請指定 *Wait* 參數。

指定 *Verbose* 參數，以查看此 Cmdlet 在套用組態設定時如何運作的詳細資料。

## 範例

### 範例1：套用設定

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

此命令會將組態設定從 C:\DSC\Configurations\ 套用至該資料夾中包含設定的每部電腦。
此命令會為所部署的每個目標節點，傳回 **Job** 物件。

### 範例2：套用設定並等候設定完成

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

此命令會將組態從 C:\DSC\Configurations\ 套用到本機電腦。
此命令會為所部署的每個目標節點，傳回 **Job** 物件，在此案例中，只有本機電腦。
這個範例會指定 *Verbose* 參數。
因此，此命令會在繼續進行時，將訊息傳送至主控台。
此命令包含 *Wait* 參數。
因此，您無法使用主控台，直到命令完成所有設定工作。

### 範例3：使用 CIM 會話套用設定設定

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

這個範例會將組態設定套用至指定的電腦。
這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。
或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。

第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 $Session 變數儲存 **CimSession** 物件。
此命令會提示您輸入密碼。
如需詳細資訊，請鍵入 `Get-Help NewCimSession`。

第二個命令會將設定從 C:\dsc\configurations\ 套用套用至儲存在 $Session 變數中的 **CimSession** 物件所識別的電腦。
在這個範例中，$Session 變數對於名為 Server01 的電腦，僅包含 CIM 工作階段。
此命令會套用該組態。
此命令會為每部已設定的電腦建立 **Job** 物件。

## PARAMETERS

### -CimSession
在遠端工作階段或遠端電腦上執行 Cmdlet。
輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。
預設為本機電腦上的目前工作階段。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
指定電腦名稱的陣列。
此參數會將 *路徑* 參數中具有設定檔的電腦限制為數組中指定的電腦。

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
指定目標電腦的使用者名稱和密碼，做為 **PSCredential** 物件。
若要取得 **PSCredential** 物件，請使用 Get-credential Cmdlet。
如需詳細資訊，請鍵入 `Get-Help Get-Credential`。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
停止目的電腦上目前正在執行的設定作業，並開始新的 Start-Configuration 作業。
如果本機 Configuration Manager 的 **RefreshMode** 屬性設定為 **Pull** ，則指定此參數會將它變更為 **Push** 。

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

### -JobName
指定工作的好記名稱。
如果您指定這個參數，Cmdlet 就會當做一個工作執行，而且它會傳回 **Job** 物件。

根據預設，Windows PowerShell 會指派名稱 JobN，其中 N 是整數。

如果您指定 *Wait* 參數，請不要指定此參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
指定包含組態設定檔之資料夾的檔案路徑。
此 Cmdlet 會發佈這些設定，並將這些設定套用到在指定路徑中具有設定檔案的電腦。
每個目標節點都必須具有下列格式的設定檔： NetBIOS 名稱. mof。

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
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

### -UseExisting
指出此 Cmdlet 會套用現有的設定。
設定可以存在於目的電腦上，方法是使用 **update-dscconfiguration** 或使用 Publish-DscConfiguration Cmdlet 的發行集制定。

在您為此 Cmdlet 指定此參數之前，請先參閱[Windows PowerShell 5.0 的新功能](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50)中的資訊。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait
指出此 Cmdlet 會封鎖主控台，直到完成所有設定工作為止。

如果您指定此參數，請不要指定 *JobName* 參數。

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

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Stop-DscConfiguration](Stop-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Update-DscConfiguration](Update-DscConfiguration.md)
