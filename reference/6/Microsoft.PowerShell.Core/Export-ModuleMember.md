---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: ed08e68279b436ea5a3c040729d70990700ebdfa
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204907"
---
# Export-ModuleMember

## 概要
指定要匯出的模組成員。

## SYNTAX

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## DESCRIPTION

**Export-modulemember 指令程式** 會指定從腳本模組匯出的模組成員 (. .psm1) 檔案，或從使用 New-Module Cmdlet 所建立的動態模組。
模組成員包含 Cmdlet、函式、變數和別名。
此 Cmdlet 只能用在指令碼模組檔案或動態模組中。

如果腳本模組未包含 **export-modulemember** 命令，則會匯出腳本模組中的函式和別名，但變數不會。
當腳本模組包含 **export-modulemember** 命令時，只會匯出 **匯出 export-modulemember** 命令中指定的成員。
您也可以使用 **export-modulemember** 來抑制或匯出腳本模組從其他模組匯入的成員。

**Export-modulemember** 命令是選擇性的，但這是最佳作法。
即使命令已確認預設值，它仍會示範模組作者的意圖。

## 範例

### 範例1：匯出腳本模組中的函式和別名

```powershell
Export-ModuleMember -Function * -Alias *
```

此命令會匯出腳本模組中定義的所有函式和別名。

### 範例2：匯出特定別名和函式

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

此命令匯出指令碼模組中定義的三個別名與三個函式。

您可以使用此命令格式來指定模組成員的名稱。

### 範例3：不匯出成員

```powershell
Export-ModuleMember
```

此命令指定不要匯出指令碼模組中定義的任何成員。

此命令可防止匯出模組成員，但是不會隱藏成員。
使用者可以讀取和複製模組成員，或使用呼叫運算子 (&) 來呼叫不會匯出的模組成員。

### 範例4：匯出特定變數

```powershell
Export-ModuleMember -Variable increment
```

此命令只會從指令碼模組匯出 $increment 變數。
不會匯出其他成員。

如果您想要匯出變數，除了匯出模組中的函式外，Export-modulemember 命令必須包含所有函 **式** 的名稱和變數的名稱。

### 範例5：多個匯出命令

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

這些命令會示範如何在腳本模組中解讀多個 **匯出 export-modulemember** 命令， (. .psm1) 檔。

這些命令建立三個函式和一個別名，接著它們會匯出兩個函式和別名。

如果沒有 **export-modulemember** 命令，則會匯出三個函式和別名。
使用 **export-modulemember** 命令時，只會匯出 **新的測試** 和 **開始測試** 函數和 STT 別名。

### 範例6：匯出動態模組中的成員

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

此命令示範如何在使用 **New module** Cmdlet 建立的動態模組中使用 Export-ModuleMember。

在此範例中，Export-modulemember 用來匯出動態模組中的 Hi 別名和 **SayHello** 函 **式** 。

### 範例7：在單一命令中宣告和匯出函數

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

此範例包含名為 **Export** 的函式，該函式會宣告函式或建立變數，然後寫入函式 `Export-ModuleMember` 或變數的命令。
這可讓您宣告和匯出單一命令中的函式或變數。

若要使用 **Export** 函式，請將它包含在腳本模組中。
若要匯出函式，請在 `Export` **function** 關鍵字前面輸入。

如果要匯出變數，請使用下列格式來宣告變數並設定其值：

`Export variable <variable-name> <value>`

此範例中的命令會顯示正確的格式。
在此範例中，只會匯出 **新的測試** 函數和 $Interval 變數。

## PARAMETERS

### -Alias

指定從指令碼模組檔案匯出的別名。
輸入別名名稱。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Cmdlet

指定從指令碼模組檔案匯出的 Cmdlet。
輸入 Cmdlet 名稱。
允許使用萬用字元。

您無法在指令碼模組檔案中建立 Cmdlet，但可將二進位模組中的 Cmdlet 匯入指令碼模組，然後從指令碼模組重新匯出它們。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Function

指定從指令碼模組檔案匯出的函式。
輸入函式名稱。
允許使用萬用字元。
您也可以透過管線將函式名稱字串傳送至 **export-modulemember** 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Variable

指定從指令碼模組檔案匯出的變數。
輸入不含貨幣符號的變數名稱。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以透過管道將函式名稱字串傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

* 若要從匯出的成員清單中排除成員，請新增 **export-modulemember** 命令來列出所有其他成員，但省略您要排除的成員。

## 相關連結

[Get-Module](Get-Module.md)

[Import-Module](Import-Module.md)

[Remove-Module](Remove-Module.md)
