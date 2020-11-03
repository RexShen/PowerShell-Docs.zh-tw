---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202316"
---
# Export-Console

## 概要
將目前工作階段中的嵌入式管理單元名稱匯出到主控台檔案。

## SYNTAX

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**匯出主控台** Cmdlet 會將目前會話中 Windows PowerShell 嵌入式管理單元的名稱匯出至 Windows PowerShell 主控台檔案 (. console01.psc1) 。
您可以使用這個 Cmdlet 來儲存嵌入式管理單元，以供未來的工作階段使用。

若要將 console01.psc1 主控台檔案中的嵌入式管理單元新增至會話，請使用 Cmd.exe 或另一個 Windows PowerShell 會話，在命令列啟動 Windows PowerShell ( # A0) ，然後使用 Powershell.exe 的 *PSConsoleFile* 參數來指定主控台檔案。

如需有關 Windows PowerShell 嵌入式管理單元的詳細資訊，請參閱 about_PSSnapins。

## 範例

### 範例1：匯出目前會話中嵌入式管理單元的名稱

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

此命令會將目前會話中 Windows PowerShell 嵌入式管理單元的名稱，匯出至 Windows PowerShell 安裝資料夾 $pshome 的 [主控台] 資料夾中的 Consoles1.psc1. console01.psc1 檔案。

### 範例2：將嵌入式管理單元的名稱匯出至最新的主控台檔案

```
PS C:\> Export-Console
```

此命令會將 Windows PowerShell 嵌入式管理單元名稱，從目前工作階段匯出到目前工作階段中最近使用的 Windows PowerShell 主控台檔案。
它會覆寫先前的檔案內容。

如果您未在目前工作階段期間匯出主控台檔案，會提示您同意繼續進行，並提示您輸入檔案名稱。

### 範例3：新增嵌入式管理單元並匯出嵌入式管理單元的名稱

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

這些命令會將 NewPSSnapin Windows PowerShell 嵌入式管理單元新增到目前的工作階段、將目前工作階段中的 Windows PowerShell 嵌入式管理單元名稱匯出到主控台檔案，然後利用主控台檔案啟動 Windows PowerShell 工作階段。

第一個命令使用 **PSSnapin** Cmdlet 將 NewPSSnapin 嵌入式管理單元新增至目前的會話。
您也可以僅新增您系統上已註冊的 Windows PowerShell 嵌入式管理單元。

第二個命令將 Windows PowerShell 嵌入式管理單元名稱匯出到 NewPSSnapinConsole.psc1 檔案。

第三個命令使用 NewPSSnapinConsole.psc1 檔案來啟動 Windows PowerShell。
因為主控台檔案包含 Windows PowerShell 嵌入式管理單元名稱，嵌入式管理單元中的 Cmdlet 與提供者可用於目前的工作階段。

### 範例4：將嵌入式管理單元的名稱匯出到指定的位置

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

此命令會將目前工作階段中的 Windows PowerShell 嵌入式管理單元名稱匯出到目前目錄中的 Console01.psc1 檔案。

第二個命令在 [記事本] 中顯示 Console01.psc1 檔案的內容。

### 範例5：判斷要更新的主控台檔案

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

此範例示範如何使用 $ConsoleFileName 自動變數來判斷當您使用不含 *路徑* 參數值的 **Export 主控台** 時，將會更新的主控台檔案。

第一個命令使用 PowerShell.exe 的 *PSConsoleFile* 參數，以 console01.psc1 console01.psc1 檔案開啟 Windows PowerShell。

第二個命令會使用 **PSSnapin** Cmdlet，將 MySnapin Windows PowerShell 嵌入式管理單元新增至目前的會話。

第三個命令使用 **匯出主控台** Cmdlet 將會話中所有 Windows PowerShell 嵌入式管理單元的名稱匯出至 newconsole.psc1. console01.psc1 檔案。

第四個命令會顯示 $ConsoleFileName 變數。
它包含最近使用的主控台檔案。
範例輸出顯示 NewConsole.ps1 為最近使用的檔案。

第五個命令將 SnapIn03 新增至目前主控台。

第六個命令使用不含 *Path* 參數的 **Export 主控台** Cmdlet。
此命令會將目前工作階段中所有 Windows PowerShell 嵌入式管理單元名稱匯出到最近使用的檔案 NewConsole.psc1。

## PARAMETERS

### -Force
指出此 Cmdlet 會覆寫主控台檔案中的資料而不發出警告，即使檔案具有唯讀屬性也一樣。
當命令完成時，唯讀屬性已變更且不會重設。

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

### -NoClobber
指出此 Cmdlet 不會覆寫現有的主控台檔案。
根據預設，如果檔案發生在指定的路徑中，則 **匯出主控台** 會覆寫檔案而不發出警告。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
指定主控台檔案 (*.psc1) 的路徑和檔案名稱。
輸入選擇性的路徑和名稱。
不允許使用萬用字元。

如果您只指定檔案名，則 [ **匯出主控台** ] 會在目前的目錄中建立具有該名稱和副檔名為 console01.psc1 的檔案。

除非您已使用 *PSConsoleFile* 參數開啟 Windows PowerShell，或在目前的會話期間匯出主控台檔案，否則此為必要參數。
當您使用 *NoClobber* 參數來防止目前的主控台檔案遭到覆寫時，也需要使用此參數。

如果您省略此參數，則 **匯出主控台** 會覆寫此會話中最近使用的主控台檔案。
最近使用的主控台檔案的路徑會儲存在 $ConsoleFileName 自動變數的值中。
如需詳細資訊，請參閱 about_Automatic_Variables。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System.String
您可以使用管線將路徑字串傳送至此 Cmdlet。

## 輸出

### System.IO.FileInfo
此 Cmdlet 會建立包含匯出別名的檔案。

## 注意

* 當使用主控台檔案 (.psc1) 來啟動工作階段，主控台檔案的名稱會自動儲存在 $ConsoleFileName 自動變數中。 當您使用 **Export 主控台** 的 *Path* 參數指定新的主控台檔案時，會更新 $ConsoleFileName 的值。 未使用任何主控台檔案時，$ConsoleFileName ($Null) 沒有任何值。

  如果要在新的工作階段中使用 Windows PowerShell 主控台檔案，請使用使用下列語法啟動 Windows PowerShell：

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  您也可以將 Add-PSSnapin 命令新增到 Windows PowerShell 設定檔，儲存 Windows PowerShell 嵌入式管理單元以供未來工作階段使用。
如需詳細資訊，請參閱 about_Profiles。


## 相關連結

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
