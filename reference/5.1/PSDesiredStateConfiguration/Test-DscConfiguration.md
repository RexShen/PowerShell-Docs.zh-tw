---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203075"
---
# Test-DscConfiguration

## 概要
測試節點上的實際設定是否符合預期設定。

## SYNTAX

### ComputerNameSet (預設值)

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### ComputerNameAndPathSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### ComputerNameAndReferenceConfigurationSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionAndPathSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### CimSessionAndReferenceConfigurationSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## DESCRIPTION
**Test-DscConfiguration** Cmdlet 會測試節點上的實際設定是否符合預期設定。
使用電腦名稱或通用訊息模型 (CIM) 工作階段，來指定您想要測試設定的電腦。
如果您沒有指定目標電腦，此 Cmdlet 會測試本機電腦的設定。

如果所需的與實際設定相符，此 Cmdlet 會傳回字串值 ' True '。
否則，它會傳回字串值 ' False '。

## 範例

### 範例 1：測試本機電腦的設定

```
PS C:\> Test-DscConfiguration
```

此命令會測試本機電腦的設定。

### 範例 2：測試指定電腦的設定

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

這個範例會測試 CIM 工作階段所指定之電腦上的設定。
這個範例會針對名為 Server01 的電腦，建立一個搭配此 Cmdlet 使用的 CIM 工作階段。
或者，建立一個 CIM 工作階段的陣列，以便將該 Cmdlet 套用到多部指定的電腦。

第一個命令會使用 **New-CimSession** Cmdlet 建立 CIM 工作階段，然後再以 $Session 變數儲存 **CimSession** 物件。
此命令會提示您輸入密碼。
如需詳細資訊，請鍵入 `Get-Help New-CimSession`。

第二個命令會測試以 $Session 變數儲存的 **CimSession** 物件所識別之電腦的設定，在此案例中是名為 Server01 的電腦。

### 範例 3︰測試設定並提供詳細的結果

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

此命令會針對 *ComputerName* 參數所指定一組電腦測試設定並傳回詳細資訊，包括整體狀態、處於預期狀態的資源、未處於預期狀態的資源及電腦名稱。

### 範例 4：測試資料夾中指定的設定

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

此命令會測試 *Path* 參數所指定資料夾中定義的設定。
設定都是針對一組電腦進行測試，每一個都是依設定檔的檔案名稱來識別。

### 範例 5：測試檔案中指定的設定

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

此命令會根據 *ComputerName* 參數所指定的一組電腦，來測試檔案中定義的設定。

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
輸入電腦名稱稱或會話物件，例如 [CimSession](/powershell/module/cimcmdlets/new-cimsession) 或 [CimSession](/powershell/module/cimcmdlets/get-cimsession) Cmdlet 的輸出。
預設為本機電腦上的目前工作階段。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
指定此 Cmdlet 測試設定所在的電腦名稱陣列。
此 Cmdlet 會在 *Path* 參數所指定的位置中，對這些電腦測試設定文件。

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
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
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Detailed
指出此 Cmdlet 會傳回比較設定文件與節點預期狀態的詳細結果。
結果包括整體狀態、處於預期狀態的資源、未處於預期狀態的資源，以及電腦名稱等資訊。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
指定包含設定文件檔的資料夾路徑。
此 Cmdlet 會針對 *ComputerName* 或 *CimSession* 參數所指定的電腦預期狀態測試設定。

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceConfiguration
指定設定文件檔案的路徑。
此 Cmdlet 會針對 *ComputerName* 或 *CimSession* 參數所指定的電腦實際狀態測試設定。

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

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

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

## 注意

## 相關連結

[Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)
