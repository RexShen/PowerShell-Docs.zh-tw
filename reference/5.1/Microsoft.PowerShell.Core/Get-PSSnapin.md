---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 472a4c8fbb9eb0d37827aff4fcfd6bb9a67f4743
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202287"
---
# Get-PSSnapin

## 概要
取得電腦上的 Windows PowerShell 嵌入式管理單元。

## SYNTAX

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## DESCRIPTION
**PSSnapin** 指令程式會取得已新增至目前會話或已在系統上註冊的 Windows PowerShell 嵌入式管理單元。
此 Cmdlet 會以偵測到的順序列出嵌入式管理單元。

**PSSnapin** 只會取得已註冊的嵌入式管理單元。若要註冊 Windows PowerShell 嵌入式管理單元，請使用 Microsoft .NET Framework 2.0 隨附的 Installutil.exe 工具。
如需詳細資訊，請參閱 MSDN library 中的 [如何註冊 Cmdlet、提供者和主機應用程式](https://go.microsoft.com/fwlink/?LinkID=143619) 。

從 Windows PowerShell 3.0 開始，Windows PowerShell 中包含的核心命令已經封裝成模組。
**Microsoft.PowerShell.Core** 是一個例外，它是一個嵌入式管理單元 (PSSnapin)。
依照預設，只會新增 **Microsoft.PowerShell.Core** 嵌入式管理單元至工作階段。
模組會在第一次使用時自動匯入，而您可以使用 Import-Module Cmdlet 來匯入它們。

## 範例

### 範例 1︰取得目前載入的嵌入式管理單元

```
PS C:\> Get-PSSnapIn
```

此命令取得工作階段中目前載入的 Windows PowerShell 嵌入式管理單元。
這包括隨 Windows PowerShell 安裝，以及已新增至工作階段的嵌入式管理單元。

### 範例 2︰取得已註冊的嵌入式管理單元

```
PS C:\> get-PSSnapIn -Registered
```

此命令取得已在電腦上註冊 (包括已新增至工作階段) 的 Windows PowerShell 嵌入式管理單元。
輸出不包括隨 Windows PowerShell 或 Windows PowerShell 嵌入式管理單元動態連結程式庫 (DLL) 安裝，但尚未在系統上註冊的嵌入式管理單元。

### 範例 3︰取得目前的嵌入式管理單元中符合字串的項目

```
PS C:\> Get-PSSnapIn -Name smp*
```

此命令取得目前工作階段中名稱以 smp 開頭的 Windows PowerShell 嵌入式管理單元。

## PARAMETERS

### -Name
指定嵌入式管理單元名稱陣列。
此 Cmdlet 只會取得指定的 Windows PowerShell 嵌入式管理單元。允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Registered
指示此 Cmdlet 取得已在系統上註冊的 Windows PowerShell 嵌入式管理單元 (即使它們尚未新增至工作階段)。

隨 Windows PowerShell 安裝的嵌入式管理單元不會出現在此清單中。

如果沒有這個參數， **PSSnapin** 會取得已新增至會話的 Windows PowerShell 嵌入式管理單元。

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

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Management.Automation.PSSnapInInfo
Get-PSSnapin 對於取得的每個嵌入式管理單元，會傳回一個物件。

## 注意

* 從 Windows PowerShell 3.0 開始，與 Windows PowerShell 一起安裝的核心命令已經封裝成模組。 在 Windows PowerShell 2.0，以及在較新版本之 Windows PowerShell 中建立舊式工作階段的主機程式中，核心命令是封裝成嵌入式管理單元 ( **PSSnapin** )。 **Microsoft.PowerShell.Core** 是一個例外，它一律是一個嵌入式管理單元。 此外，遠端工作階段 (例如由 New-PSSession cmdlet 所啟動的遠端工作階段) 都是包含核心嵌入式管理單元的舊式工作階段。

  如需有關使用核心模組建立較新樣式會話的 **CreateDefault2** 方法的詳細資訊，請參閱 MSDN library 中的 [CreateDefault2 方法](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) 。

## 相關連結

[Add-PSSnapin](Add-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
