---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: c29115a65b46d38039d78b10eee293e6944cede5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202839"
---
# Get-Error

## 概要

取得並顯示目前會話中最近的錯誤訊息。

## SYNTAX

### 最新 (預設) 

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### 錯誤

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-Error` Cmdlet 會取得 **PSExtendedError** 物件，該物件代表會話中最後一個錯誤的目前錯誤詳細資料。

您可以使用 `Get-Error` 來顯示目前會話中使用 **最新** 參數所發生的指定錯誤數目。

此 `Get-Error` Cmdlet 也會從集合接收錯誤物件（例如 `$Error` ），以顯示目前會話的多個錯誤。

## 範例

### 範例1：取得最新的錯誤詳細資料

在此範例中， `Get-Error` 會顯示目前會話中發生之最新錯誤的詳細資料。

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### 範例2：取得目前會話中所發生的指定錯誤訊息數目

此範例示範如何搭配 `Get-Error` **最新** 的參數使用。 在此範例中， **最新** 會傳回在此會話中所發生3個最新錯誤的詳細資料。

```powershell
Get-Error -Newest 3
```

### 範例3：傳送錯誤的集合以接收詳細訊息

`$Error`自動變數在目前的會話中包含錯誤物件的陣列。 您可以透過管道將物件陣列傳送至， `Get-Error` 以接收詳細的錯誤訊息。

在此範例中， `$Error` 會透過管道傳送至 `Get-Error` Cmdlet。 結果是一份詳細的錯誤訊息清單，類似于範例1的結果。

```powershell
$Error | Get-Error
```

## PARAMETERS

### -Newest

指定目前會話中所發生的錯誤數目。

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

此參數用於管線輸入。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### PSObject

支援來自任何 **PSObject** 的輸入，但結果會有所不同，除非提供了 **ErrorRecord** 或 **Exception** 物件。

## 輸出

### ErrorRecord # PSExtendedError。

**PSExtendedError** 物件中的輸出。

## 注意

`Get-Error` 接受管線輸入。 例如： `$Error | Get-Error` 。

## 相關連結

[about_Try_Catch_Finally](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
