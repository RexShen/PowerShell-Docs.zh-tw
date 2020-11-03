---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: 443186a63819809a42d953b60232c9745818fb4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204948"
---
# Update-ScriptFileInfo

## 概要
更新腳本的資訊。

## SYNTAX

### PathParameterSet (預設) 

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPathParameterSet

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Update-ScriptFileInfo` Cmdlet 會更新腳本的屬性值。 例如，[版本]、[作者] 或 [描述] 的值。

## 範例

### 範例1：更新指令檔的版本

在此範例中，會以新的屬性值更新現有的腳本檔案。

展開用來將參數傳遞給 `Update-ScriptFileInfo` Cmdlet。 如需詳細資訊，請參閱 [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)。

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "2.0"
  Author = "bob@contoso.com"
  CompanyName = "Contoso"
  Description = "This is the updated description"
  }
Update-ScriptFileInfo @Parms -PassThru
```

```Output
<#PSScriptInfo

.VERSION 2.0

.GUID 4609f00c-e850-4d3f-9c69-3741e56e4133

.AUTHOR bob@contoso.com

.COMPANYNAME Contoso

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

.PRIVATEDATA

#>

<#

.DESCRIPTION
This is the updated description

#>
Param()
```

`$Parms` 儲存 **路徑** 、 **版本** 、 **作者** 、 **公司名稱** 和 **描述** 的參數值。 `Update-ScriptFileInfo` 從取得參數值 `@Parms` ，並更新腳本。 **PassThru** 參數會在 PowerShell 主控台中顯示腳本的內容。

## PARAMETERS

### -作者

指定腳本作者。

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

### -公司名稱

指定建立腳本的公司或廠商。

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

### -Confirm

在執行之前提示您確認 `Update-ScriptFileInfo` 。

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

### -著作權

指定腳本的著作權語句。

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

### -Description

指定腳本的描述。

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

### -ExternalModuleDependencies

指定外部模組相依性的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExternalScriptDependencies

指定外部腳本相依性的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制 `Update-ScriptFileInfo` 執行而不要求使用者確認。

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

### -Guid

指定腳本的唯一識別碼。

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IconUri

指定腳本圖示的 URL。 指定的圖示會顯示在腳本的資源庫網頁上。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseUri

指定授權條款的 URL。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定一個或多個位置的路徑。 **LiteralPath** 參數的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含 escape 字元，請用單引號括住。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之專案的物件。 依預設， `Update-ScriptFileInfo` 不會產生任何輸出。

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

指定腳本檔的位置。 允許使用萬用字元。

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PrivateData

指定腳本的私用資料。

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

### -ProjectUri

指定與這個專案相關之網頁的 URL。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReleaseNotes

指定字串陣列，其中包含您想要用於此版本腳本的版本資訊或批註。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredModules

指定必須在全域工作階段狀態的模組。 如果必要的模組不在全域會話狀態中，則 PowerShell 會將它們匯入。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredScripts

指定必要腳本的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tags

指定標記的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

指定腳本的版本。

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

### -WhatIf

顯示執行時所發生 `Update-ScriptFileInfo` 的情況。 不會執行此 Cmdlet。

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

## 輸出

### System.Object

## 注意

使用 `Test-ScriptFileInfo` Cmdlet 來驗證腳本的中繼資料。 腳本必須包含版本、GUID、描述和作者的值。

## 相關連結

[New-ScriptFileInfo](New-ScriptFileInfo.md)

[Test-ScriptFileInfo](Test-ScriptFileInfo.md)

