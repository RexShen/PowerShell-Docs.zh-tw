---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: 36232f96f8d9e51b4151b971321b1b91a8a3fb00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204767"
---
# Test-ModuleManifest

## 概要
驗證模組資訊清單檔案可精確地說明模組的內容。

## SYNTAX

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## DESCRIPTION

**Test-ModuleManifest** Cmdlet 會驗證模組資訊清單 (.psd1) 檔案中所列的檔案實際位於指定的路徑。

這個 Cmdlet 是設計來協助模組作者測試其資訊清單檔案。
模組使用者也可以在執行相依於模組的指令碼之前，於指令碼和命令中使用這個 Cmdlet 來偵測錯誤。

**Test-ModuleManifest** 會傳回代表模組的物件。
這與 Get-Module 傳回的物件類型相同。
若有檔案不在資訊清單中指定的位置，此 Cmdlet 也會針對每個遺失的檔案產生錯誤。

## 範例

### 範例 1：測試資訊清單

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

此命令測試 TestModule.psd1 模組資訊清單。

### 範例 2︰使用管線測試資訊清單

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

此命令會使用管線運算子 (|) 將路徑字串傳送至 **ModuleManifest** 。

命令輸出顯示測試失敗，因為找不到資訊清單中所列的 TestTypes.ps1xml 檔案。

### 範例 3：撰寫函式以測試模組資訊清單

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

此函式和 **Test-ModuleManifest** 相同，但它會傳回布林值。
如果資訊清單通過測試，函式會傳回 $True，否則會傳回 $False。

此函式使用 Get-ChildItem Cmdlet (別名 = dir)，來取得 $path 變數所指定的模組資訊清單。
命令使用管線運算子 (|)，將檔案物件傳送至 **Test-ModuleManifest** 。

**Test-ModuleManifest** 命令使用 *ErrorAction* 一般參數搭配 SilentlyContinue 的值，來抑制顯示命令所產生的任何錯誤。
它也會將 **Test-ModuleManifest** 傳回的 **PSModuleInfo** 物件儲存於 $a 變數中。
因此該物件不會顯示。

然後，在個別命令中，函式會顯示 $?
自動變數的值。
如果前一個命令未產生任何錯誤，此命令會顯示 $True，否則為 $False。

您可以在條件陳述式中使用這個函式，例如，可能在 **import-module** 命令之前的函式或使用模組的命令。

## PARAMETERS

### -Path

指定資訊清單檔案的路徑和檔案名稱。
輸入具有 .psd1 副檔名之模組資訊清單檔案的選擇性路徑和名稱。
預設位置是目前的目錄。
支援使用萬用字元，但必須解析為單一模組資訊清單檔案。
這是必要參數。
您也可以使用管線將路徑傳送至 **測試 ModuleManifest** 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將模組資訊清單的路徑傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.PSModuleInfo

此 Cmdlet 會傳回代表模組的 **PSModuleInfo** 物件。
即使資訊清單發生錯誤，它還是會傳回這個物件。

## 注意

## 相關連結

[Export-ModuleMember](Export-ModuleMember.md)

[Get-Module](Get-Module.md)

[Import-Module](Import-Module.md)

[New-Module](New-Module.md)

[New-ModuleManifest](New-ModuleManifest.md)

[Remove-Module](Remove-Module.md)

[about_Modules](About/about_Modules.md)

