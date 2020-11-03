---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/invoke-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-OperationValidation
ms.openlocfilehash: 6c9d4001392de48032a0fe1ba3667db90ea614fc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203428"
---
# Invoke-OperationValidation

## 概要

叫用作業驗證架構測試。

## SYNTAX

### FileAndTest (預設) 

```
Invoke-OperationValidation [-TestInfo <PSObject[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### 路徑

```
Invoke-OperationValidation [-testFilePath <String[]>] [-IncludePesterOutput] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### UseGetOperationTest

```
Invoke-OperationValidation [-ModuleName <String[]>] [-TestType <String[]>] [-IncludePesterOutput] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**OperationValidation 指令程式** 會叫用指定模組的作業驗證架構測試。

## 範例

### 範例1：叫用作業驗證測試

```
PS C:\> Get-OperationValidation -ModuleName "OperationValidation" | Invoke-OperationValidation -IncludePesterOutput
Describing Simple Test Suite
 [+] first Operational test 20ms
 [+] second Operational test 19ms
 [+] third Operational test 9ms
Tests completed in 48ms
Passed: 3 Failed: 0 Skipped: 0 Pending: 0
Describing Scenario targeted tests
   Context The RemoteAccess service
    [+] The service is running 37ms
   Context The Firewall Rules
    [+] A rule for TCP port 3389 is enabled 1.19s
    [+] A rule for UDP port 3389 is enabled 11ms
Tests completed in 1.24s
Passed: 3 Failed: 0 Skipped: 0 Pending: 0




   Module: OperationValidation




Result  Name
------- --------
Passed  Simple Test Suite::first Operational test
Passed  Simple Test Suite::second Operational test
Passed  Simple Test Suite::third Operational test
Passed  Scenario targeted tests:The RemoteAccess service:The service is running
Passed  Scenario targeted tests:The Firewall Rules:A rule for TCP port 3389 is enabled
Passed  Scenario targeted tests:The Firewall Rules:A rule for UDP port 3389 is enabled
```

此命令會取得名為 OperationValidation 的模組，並使用管線運算子將它傳遞給執行測試的 **OperationValidation** Cmdlet。

## PARAMETERS

### -IncludePesterOutput

包含 Pester 測試輸出。
預設值為 $False。

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

### -ModuleName

指定模組名稱的陣列。

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -testFilePath

指定作業驗證架構測試檔案的路徑。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TestInfo

指定自訂物件，指定檔案的路徑，以及要執行之測試的名稱。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: FileAndTest
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### ->testtype

指定測試類型的陣列。
有效值為 Simple、綜合性或 both。
預設值為「簡單、完整」。

```yaml
Type: System.String[]
Parameter Sets: UseGetOperationTest
Aliases:
Accepted values: Simple, Comprehensive

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

### PSCustomObject

您可以透過管道將 **OperationValidation** 的輸出傳送給此 Cmdlet。

## 輸出

### PSCustomObject

**PSCustomObject** 描述驗證是否成功。

## 注意

## 相關連結

[Get-OperationValidation](Get-OperationValidation.md)
