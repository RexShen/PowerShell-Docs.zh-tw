---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203431"
---
# Get-OperationValidation

## 概要
取得作業驗證架構測試。

## SYNTAX

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## DESCRIPTION
**OperationValidation** 指令程式會取得已安裝模組的作業驗證架構測試。

系統會檢查包含診斷資料夾的模組，以在簡單或完整的子資料夾中進行 Pester 測試，或同時檢查兩者。

## 範例

### 範例1：取得作業驗證測試

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

此命令會從 C:\temp\modules 資料夾中名為 AddNumbers 的模組取得驗證測試。

## PARAMETERS

### -ModuleName
指定模組名稱的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### ->testtype
指定測試類型的陣列。
有效值為 Simple、綜合性或 both。
預設值為「簡單、完整」。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
您無法透過管道傳送任何輸入至此 Cmdlet。

## 輸出

### PSCustomObject
**PSCustomObject** 會描述驗證。

## 注意

## 相關連結

[Invoke-OperationValidation](Invoke-OperationValidation.md)
