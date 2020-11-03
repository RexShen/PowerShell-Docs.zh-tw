---
description: 說明如何使用展開將參數傳遞至 PowerShell 中的命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: a64cbbe5edd40bf4fc7f9b7347421988d225e666
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207279"
---
# <a name="about-splatting"></a>關於展開

## <a name="short-description"></a>簡短描述

說明如何使用展開將參數傳遞至 PowerShell 中的命令。

## <a name="long-description"></a>完整描述

展開是將參數值的集合傳遞至命令做為單位的方法。 PowerShell 會將集合中的每個值與命令參數產生關聯。 Splatted 參數值會儲存在名為展開的變數中，這看起來像是標準變數，但以 At 符號 (`@`) ，而不是以貨幣符號 (`$`) 。 At 符號會告知 PowerShell 您要傳遞值的集合，而不是單一值。

展開可讓您的命令變得更短、更容易閱讀。 您可以在不同的命令呼叫中重複使用展開值，並使用展開將參數值從 `$PSBoundParameters` 自動變數傳遞給其他腳本和函式。

從 Windows PowerShell 3.0 開始，您也可以使用展開來代表命令的所有參數。

## <a name="syntax"></a>Syntax

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

若要提供位置參數的參數值（不需要參數名稱），請使用陣列語法。 若要提供參數名稱和值組，請使用雜湊表語法。 Splatted 值可出現在參數清單中的任何位置。

展開時，您不需要使用雜湊表或陣列來傳遞所有參數。 您可以使用展開傳遞一些參數，並依位置或依參數名稱傳遞其他參數。 此外，您可以在單一命令中 splat 多個物件，如此就不會針對每個參數傳遞多個值。

從 PowerShell 7.1，您可以藉由在命令中明確定義參數，覆寫 splatted 參數。

## <a name="splatting-with-hash-tables"></a>具有雜湊表的展開

使用雜湊表來 splat 參數名稱和值組。 您可以將此格式用於所有參數類型，包括位置和切換參數。
位置參數必須以名稱指派。

下列範例會比較兩個 `Copy-Item` 命令，以將 Test.txt 檔案複製到相同目錄中的 Test2.txt 檔案。

第一個範例會使用包含參數名稱的傳統格式。

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

第二個範例會使用雜湊表展開。 第一個命令會建立參數名稱和參數值組的雜湊表，並將它儲存在 `$HashArguments` 變數中。 第二個命令會 `$HashArguments` 在命令中使用展開的變數。 At 符號 (`@HashArguments`) 會取代命令中的貨幣符號 (`$HashArguments`) 。

若要提供 **WhatIf** 切換參數的值，請使用 `$True` 或 `$False` 。

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> 在第一個命令中，At 符號 (`@`) 表示雜湊表，而不是 splatted 值。 PowerShell 中的雜湊表語法如下： `@{<name>=<value>; <name>=<value>; ...}`

## <a name="splatting-with-arrays"></a>具有陣列的展開

使用陣列來 splat 位置參數的值，而不需要參數名稱。 這些值必須是陣列中的位置編號順序。

下列範例會比較兩個 `Copy-Item` 命令，以將 Test.txt 檔案複製到相同目錄中的 Test2.txt 檔案。

第一個範例會使用傳統格式，其中省略參數名稱。 參數值會以位置順序出現在命令中。

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

第二個範例使用陣列展開。 第一個命令會建立參數值的陣列，並將其儲存在 `$ArrayArguments` 變數中。 值是在陣列中的位置順序。 第二個命令使用 `$ArrayArguments` 展開中命令的變數。 At 符號 (`@ArrayArguments`) 會取代命令中的貨幣符號 (`$ArrayArguments`) 。

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a>使用 ArgumentList 參數

有數個 Cmdlet 具有 **ArgumentList** 參數，可用來將參數值傳遞給 Cmdlet 所執行的腳本區塊。 **ArgumentList** 參數會取得傳遞至腳本區塊的值陣列。 PowerShell 實際上使用陣列展開將值系結至腳本區塊的參數。 使用 **ArgumentList** 時，如果您需要將陣列當作系結至單一參數的單一物件傳遞，則必須將陣列包裝為另一個陣列的唯一元素。

下列範例中的腳本區塊會採用一個字串陣列的單一參數。

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```
<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
在此範例中，只有中的第一個專案 `$array` 會傳遞至腳本區塊。

```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
} -ArgumentList (,$array)
```

在此範例中， `$array` 會包裝在陣列中，以便將整個陣列以單一物件的形式傳遞至腳本區塊。

```Output
Hello World!
```

## <a name="examples"></a>範例

### <a name="example-1-reuse-splatted-parameters-in-different-commands"></a>範例1：在不同的命令中重複使用 splatted 參數

此範例顯示如何在不同的命令中重複使用 splatted 值。 此範例中的命令會使用 `Write-Host` Cmdlet 將訊息寫入至主機程式主控台。 它會使用展開來指定前景和背景色彩。

若要變更所有命令的色彩，請只變更變數的值 `$Colors` 。

第一個命令會建立參數名稱和值的雜湊表，並將雜湊表儲存在 `$Colors` 變數中。

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

第二個和第三個命令會 `$Colors` 在命令中使用展開的變數 `Write-Host` 。 若要使用 `$Colors variable` ，請以 () 的 At 符號取代貨幣符號 (`$Colors`) `@Colors` 。

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

### <a name="example-2-forward-parameters-using-psboundparameters"></a>範例2：使用 $PSBoundParameters 轉寄參數

此範例示範如何使用展開和自動變數，將其參數轉送至其他命令 `$PSBoundParameters` 。

`$PSBoundParameters`自動變數是字典物件， (的) ，其中包含執行腳本或函式時所使用的所有參數名稱和值。

在下列範例中，我們會使用 `$PSBoundParameters` 變數，將傳遞給腳本或函式的參數值轉送 `Test2` 至函式 `Test1` 。 這兩個函式呼叫都是 `Test1` `Test2` 使用展開。

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

### <a name="example-3-override-splatted-parameters-with-explicitly-defined-parameters"></a>範例3：使用明確定義的參數覆寫 splatted 參數

這個範例示範如何使用明確定義的參數覆寫 splatted 參數。 當您不想要建立新的雜湊表，或在您用來 splat 的雜湊表中變更值時，這會很有用。

`$commonParams`變數會儲存參數，以在位置中建立虛擬機器 `East US` 。 `$allVms`變數是要建立的虛擬機器清單。 我們會對清單執行迴圈，並使用 `$commonParams` splat 參數來建立每部虛擬機器。 不過，我們想要 `myVM2` 在與其他虛擬機器不同的區域中建立。 `$commonParams`您可以明確地定義中的 **Location** 參數，取代中的索引鍵值，而不是調整雜湊表 `New-AzVm` `Location` `$commonParams` 。

```powershell
$commonParams = @{
    ResourceGroupName = "myResourceGroup"
    Location = "East US"
    VirtualNetworkName = "myVnet"
    SubnetName = "mySubnet"
    SecurityGroupName = "myNetworkSecurityGroup"
    PublicIpAddressName = "myPublicIpAddress"
}

$allVms = @('myVM1','myVM2','myVM3',)

foreach ($vm in $allVms)
{
    if ($vm -eq 'myVM2')
    {
        New-AzVm @commonParams -Name $vm -Location "West US"
    }
    else
    {
        New-AzVm @commonParams -Name $vm
    }
}
```

## <a name="splatting-command-parameters"></a>展開命令參數

您可以使用展開來代表命令的參數。 當您建立 proxy 函式時（也就是呼叫另一個命令的函式），這項技術會很有用。 這項功能是在 Windows PowerShell 3.0 中引進。

若要 splat 命令的參數，請使用 `@Args` 來代表命令參數。 這項技術比列舉命令參數更為簡單，即使呼叫的命令的參數變更，也不需要修訂。

這項功能會使用 `$Args` 自動變數，其中包含所有未指派的參數值。

例如，下列函式會呼叫 `Get-Process` Cmdlet。 在此函數中， `@Args` 表示 Cmdlet 的所有參數 `Get-Process` 。

```powershell
function Get-MyProcess { Get-Process @Args }
```

當您使用 `Get-MyProcess` 函數時，所有未指派的參數和參數值都會傳遞至 `@Args` ，如下列命令所示。

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

您可以 `@Args` 在已明確宣告參數的函式中使用。 您可以在函式中使用一次以上，但您輸入的所有參數都會傳遞至的所有實例 `@Args` ，如下列範例所示。

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a>備忘稿

如果您使用 **CmdletBinding** 或 **參數** 屬性將函式變成 advanced 函數，則函式中將 `$args` 無法再使用自動變數。 Advanced 函數需要明確的參數定義。

PowerShell Desired State Configuration (DSC) 並未設計成使用展開。
您無法使用展開將值傳遞至 DSC 資源。 如需詳細資訊，請參閱 Gael Colas 的文章 [虛擬展開 DSC 資源](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)。

## <a name="see-also"></a>另請參閱

[about_Arrays](about_Arrays.md)

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Parameters](about_Parameters.md)
