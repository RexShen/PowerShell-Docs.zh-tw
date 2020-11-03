---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 6a8f1379c90b3af97b705266152f9d2407bf0132
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "93205796"
---
# Get-Help

## 概要
顯示 PowerShell 命令和概念的相關資訊。

## SYNTAX

### AllUsersView (預設) 

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### DetailedView

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Detailed] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### 範例

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Examples] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### 參數

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### 線上

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [-Online] [<CommonParameters>]
```

### ShowWindow

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [-ShowWindow] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-Help` Cmdlet 會顯示 PowerShell 概念和命令的相關資訊，包括 Cmdlet、函式、通用訊息模型 (CIM) 命令、工作流程、提供者、別名和腳本。

若要取得 PowerShell Cmdlet 的說明，請輸入 `Get-Help` 後面接著 Cmdlet 名稱，例如： `Get-Help Get-Process` 。

PowerShell 中的概念性說明文章的開頭是 **about_** ，例如 **about_Comparison_Operators** 。 若要查看所有 **about_** 文章，請輸入 `Get-Help about_*` 。 若要查看特定的文章，請輸入 `Get-Help about_<article-name>` ，例如 `Get-Help about_Comparison_Operators` 。

若要取得 PowerShell 提供者的說明，請輸入， `Get-Help` 後面接著提供者名稱。 例如，若要取得憑證提供者的說明，請輸入 `Get-Help Certificate` 。

您也可以輸入 `help` 或 `man` ，一次顯示一個螢幕的文字。 或者，與 `<cmdlet-name> -?` 相同 `Get-Help` ，但僅適用于 Cmdlet。

`Get-Help` 取得從電腦的說明檔中顯示的說明內容。 如果沒有說明檔，則 `Get-Help` 只會顯示有關 Cmdlet 的基本資訊。 有些 PowerShell 模組包含說明檔。 從 PowerShell 3.0 開始，Windows 作業系統隨附的模組不會包含說明檔。 若要下載或更新 PowerShell 3.0 中模組的說明檔，請使用 `Update-Help` Cmdlet。

您也可以在 Microsoft Docs 的線上查看 PowerShell 說明文件。若要取得說明檔的線上版本，請使用 **online** 參數，例如： `Get-Help Get-Process -Online` 。 若要閱讀所有的 PowerShell 檔，請參閱 Microsoft Docs [Powershell 檔](/powershell)集。

如果您輸入的 `Get-Help` 是說明文章的完整名稱，或說明文章的唯一單字，則會 `Get-Help` 顯示文章的內容。 如果您指定命令別名的完整名稱，則會 `Get-Help` 顯示原始命令的說明。 如果您輸入在數個說明文章標題中出現的單字或單字模式，則會 `Get-Help` 顯示相符標題的清單。 如果您輸入任何不會出現在任何說明文章標題中的文字，則會 `Get-Help` 顯示其內容中包含該文字的文章清單。

`Get-Help` 可以取得所有支援的語言和地區設定的說明文章。 `Get-Help` 先在 Windows 的地區設定中尋找說明檔，然後在父地區設定中尋找說明檔， **例如 pt** **-BR** ，然後在回溯地區設定中。 從 PowerShell 3.0 開始，如果在回溯 `Get-Help` 地區設定中找不到說明，則會在傳回錯誤訊息或顯示自動產生的說明之前，先尋找英文（ **en-us** ）的說明文章。

如需 `Get-Help` 在命令語法圖表中顯示之符號的詳細資訊，請參閱 [about_Command_Syntax](./About/about_Command_Syntax.md)。
如需參數屬性的相關資訊，例如 [ **必要** ] 和 [ **位置** ]，請參閱 [about_Parameters](./About/about_Parameters.md)。

>[!NOTE]
> 在 PowerShell 3.0 和 PowerShell 4.0 中， `Get-Help` 除非將模組匯入目前的會話，否則找不到模組中的 **相關** 文章。 這是已知的問題。 若要取得模組中的 **相關** 文章，請使用 `Import-Module` Cmdlet 或執行模組中包含的 Cmdlet 來匯入模組。

## 範例

### 範例1：顯示有關 Cmdlet 的基本說明資訊

這些範例會顯示 Cmdlet 的基本說明資訊 `Format-Table` 。

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

`Get-Help <cmdlet-name>` 是 Cmdlet 的最簡單和預設語法 `Get-Help` 。 您可以省略 **Name** 參數。

語法 `<cmdlet-name> -?` 只適用于 Cmdlet。

### 範例2：一次顯示一個頁面的基本資訊

這些範例會 `Format-Table` 一次顯示一頁 Cmdlet 的基本說明資訊。

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

`help` 是一種函式，會在 `Get-Help` 內部執行 Cmdlet，並一次顯示一個頁面的結果。

`man` 這是函數的別名 `help` 。

`Get-Help Format-Table` 將物件沿著管線向下傳送。 `Out-Host -Paging` 接收管線的輸出，並一次顯示一個頁面。 如需詳細資訊，請參閱 [Out-Host](Out-Host.md)。

### 範例3：顯示 Cmdlet 的詳細資訊

這些範例會顯示更詳細的 Cmdlet 說明資訊 `Format-Table` 。

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

**詳細** 的參數會顯示說明文章的詳細資訊，其中包含參數說明和範例。

**Full** 參數會顯示說明文章的完整視圖，其中包含參數描述、範例、輸入和輸出物件類型，以及其他注意事項。

**詳細** 的和 **完整** 參數只適用于電腦上已安裝說明檔的命令。 這些參數對概念 ( **about_** ) 說明文章而言是不正確。

### 範例4：使用參數顯示 Cmdlet 的選取部分

這些範例會顯示 Cmdlet 說明的選取部分 `Format-Table` 。

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

**範例** 參數會顯示說明檔的 **名稱** 和 **概要** 區段，以及所有範例。 您無法指定範例編號，因為 **範例** 參數是切換參數。

**參數** 參數只會顯示指定參數的描述。 如果您只指定星號 (`*`) 萬用字元，則會顯示所有參數的描述。
當 **參數** 指定參數名稱（例如 **GroupBy** ）時，就會顯示該參數的相關資訊。

這些參數對概念 ( **about_** ) 說明文章而言是不正確。

### 範例5：顯示線上版本的說明

此範例會 `Format-Table` 在您的預設網頁瀏覽器中顯示此 Cmdlet 的說明文章的線上版本。

```powershell
Get-Help Format-Table -Online
```

### 範例6：顯示 help 系統的說明

`Get-Help`沒有參數的 Cmdlet 會顯示 PowerShell 說明系統的相關資訊。

```powershell
Get-Help
```

### 範例7：顯示可用的說明文章

此範例會顯示電腦上可用的所有說明文章清單。

```powershell
Get-Help *
```

### 範例8：顯示概念性文章清單

此範例會顯示 PowerShell 說明中包含的概念性文章清單。 這些文章都是以 **about_** 的字元開頭。 若要顯示特定的說明檔，請輸入 `Get-Help \<about_article-name\>` ，例如 `Get-Help about_Signing` 。

只會顯示在您的電腦上安裝說明檔的概念性文章。 如需有關在 PowerShell 3.0 中下載和安裝說明檔的詳細資訊，請參閱 [update-help](Update-Help.md)。

```powershell
Get-Help about_*
```

### 範例9：在 Cmdlet 說明中搜尋單字

此範例示範如何在 Cmdlet 說明文章中搜尋單字。

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

`Get-Help` 使用 **Full** 參數來取得的說明資訊 `Add-Member` 。 **MamlCommandHelpInfo** 物件會沿著管線向下傳送。 `Out-String` 使用 **資料流程** 參數將物件轉換成字串。 `Select-String` 使用 **Pattern** 參數來搜尋字串以進行 **Clixml** 。

### 範例10：顯示包含單字的文章清單

此範例會顯示包含「 **遠端處理** 」一字的文章清單。

當您輸入未出現在任何文章標題中的單字時，會 `Get-Help` 顯示包含該單字的文章清單。

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### 範例11：顯示提供者特定說明

這個範例示範兩種取得提供者特定說明的方式 `Get-Item` 。 這些命令會取得說明如何 `Get-Item` 在 PowerShell SQL Server 提供者的 **DataCollection** 節點中使用 Cmdlet。

第一個範例會使用 `Get-Help` **Path** 參數來指定 SQL Server 提供者的路徑。
由於已指定提供者的路徑，因此您可以從任何路徑位置執行此命令。

第二個範例會使用 `Set-Location` 來流覽至 SQL Server 提供者的路徑。 從該位置中，不需要 **Path** 參數 `Get-Help` 來取得提供者特定的說明。

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### 範例12：顯示腳本的說明

這個範例會取得的說明 `MyScript.ps1 script` 。 如需如何撰寫函數和腳本說明的相關資訊，請參閱 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)。

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## PARAMETERS

### -Category

僅針對指定類別中的項目顯示說明及其別名。 概念文章位於 [功能 **説明** ] 分類中。

此參數可接受的值如下：

- Alias
- Cmdlet
- 提供者
- 一般
- 常見問題集
- 詞彙
- HelpFile
- ScriptCommand
- 函式
- Filter
- ExternalScript
- 全部
- DefaultHelp
- 工作流程
- DscResource
- 類別
- 組態

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -元件

顯示具有指定元件值的命令，例如 **Exchange** 。 輸入元件名稱。
允許使用萬用字元。 此參數不會影響概念性 ( **About_** ) 說明的顯示。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Detailed

將參數說明和範例新增到基本的說明顯示中。 只有當電腦上已安裝說明檔時，此參數才會生效。 它不會影響概念性 ( **About_** ) 說明的顯示。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Examples

只顯示名稱、概要和範例。 若只要顯示範例，請輸入 `(Get-Help \<cmdlet-name\>).Examples` 。

只有當電腦上已安裝說明檔時，此參數才會生效。 它不會影響概念性 ( **About_** ) 說明的顯示。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full

顯示 Cmdlet 的整個說明文章。 **Full** 包含參數說明和屬性、範例、輸入和輸出物件類型，以及其他注意事項。

只有當電腦上已安裝說明檔時，此參數才會生效。 它不會影響概念性 ( **About_** ) 說明的顯示。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -功能

顯示具有指定功能的項目說明。 輸入功能。 允許使用萬用字元。 此參數不會影響概念性 ( **About_** ) 說明的顯示。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

取得指定命令或概念的相關說明。 輸入 Cmdlet、函式、提供者、腳本或工作流程的名稱，例如概念發行項 `Get-Member` 名稱（例如 `about_Objects` ）或別名（例如） `ls` 。 Cmdlet 和提供者名稱中允許使用萬用字元，但是您不能使用萬用字元來尋找函式說明和腳本說明文章的名稱。

若要取得不是位於環境變數所列路徑中的腳本說明 `$env:Path` ，請輸入腳本的路徑和檔案名。

如果您輸入說明文章的完整名稱，則會 `Get-Help` 顯示文章內容。

如果您輸入在數個說明文章標題中出現的單字或單字模式，則會 `Get-Help` 顯示相符標題的清單。

如果您輸入任何不符合任何說明文章標題的文字，則會 `Get-Help` 在其內容中顯示包含該文字的文章清單。

概念文章的名稱（例如 `about_Objects` ）必須以英文輸入，即使是在非英文版的 PowerShell 中也一樣。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Online

在預設瀏覽器中顯示說明文章的線上版本。 此參數僅適用于 Cmdlet、函式、工作流程和腳本說明文章。 您無法 **Online** `Get-Help` 在遠端會話中使用 Online 參數。

如需有關在您撰寫的說明文章中支援這項功能的詳細資訊，請參閱 [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)和 [支援線上說明](/powershell/scripting/developer/module/supporting-online-help)，以及 [撰寫 PowerShell Cmdlet 的](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)說明。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Parameter

只顯示指定參數的詳細說明。 允許使用萬用字元。 此參數不會影響概念性 ( **About_** ) 說明的顯示。

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

取得說明 Cmdlet 如何在指定的提供者路徑中運作的說明。 輸入 PowerShell 提供者路徑。

此參數會取得 Cmdlet 說明文章的自訂版本，說明該 Cmdlet 如何在指定的 PowerShell 提供者路徑中運作。 此參數僅適用于提供者 Cmdlet 的說明，而且只有在提供者于其說明檔中包含自訂版本的提供者 Cmdlet 說明文章時才會生效。 若要使用這個參數，請針對包含提供者的模組安裝說明檔。

若要查看提供者路徑的自訂 Cmdlet 說明，請移至提供者路徑位置並輸入 `Get-Help` 命令，或從任何路徑位置，使用的 **path** 參數 `Get-Help` 指定提供者路徑。 您也可以在 [說明] 文章的 [提供者說明] 區段中，線上找到自訂的 Cmdlet 說明。

如需 PowerShell 提供者的詳細資訊，請參閱 [about_Providers](./About/about_Providers.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Role

顯示針對指定使用者角色自訂的說明。 輸入角色。 允許使用萬用字元。

輸入使用者在組織中扮演的角色。 某些 Cmdlet 會根據這個參數值，在說明檔中顯示不同的文字。 這個參數不會對核心 Cmdlet 的說明產生任何影響。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowWindow

在視窗中顯示說明主題，以便更容易閱讀。 此視窗包含 [ **尋找** 搜尋] 功能和 **[設定]** 方塊，可讓您設定顯示器的選項，包括只顯示所選說明主題區段的選項。

**ShowWindow** 參數支援命令的說明主題 (Cmdlet、函式、CIM 命令、腳本) 和概念 **相關** 的文章。 它不支援提供者說明。

PowerShell 7.0 中已重新引入此參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法將物件沿著管線向下傳送至 `Get-Help` 。

## 輸出

### ExtendedCmdletHelpInfo

如果您在沒有說明檔的 `Get-Help` 命令上執行，則會傳回代表自動產生說明的 `Get-Help` **ExtendedCmdletHelpInfo** 物件。

### System.String

如果您取得概念性說明文章，則 `Get-Help` 會以字串形式傳回。

### MamlCommandHelpInfo

如果您收到具有說明檔的命令，則會傳回 `Get-Help` **MamlCommandHelpInfo** 物件。

## 注意

PowerShell 3.0 不包含說明檔。 若要下載並安裝讀取的說明檔 `Get-Help` ，請使用 `Update-Help` Cmdlet。 您可以使用指令程式 `Update-Help` 來下載並安裝 PowerShell 隨附的核心命令的說明檔，以及您安裝的任何模組。 您也可以使用它來更新說明檔，讓電腦上的說明永遠都不會過期。

您也可以閱讀有關 PowerShell online 命令的說明文章，從 [消費者入門與 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)開始。

`Get-Help` 在針對 Windows 作業系統設定的地區設定中，或在該地區設定的備用語言中顯示說明。 如果您沒有主要或備用地區設定的說明檔，其 `Get-Help` 行為就如同電腦上沒有說明檔一樣。 若要取得不同地區設定的說明，請使用主控台中的 **地區** 和 **語言** 來變更設定。 在 Windows 10、 **設定** 、 **時間 & 語言** 。

[說明] 的完整觀點包括參數的相關資訊表。 該表格包含下列欄位：

- **必要** 。 指出參數是否為必要 (true) 或選擇性 (false)。

- **位置** 。 指出參數的名稱是否為或 (數值) 的位置。 位置參數必須出現在命令中指定的位置。

- **指名** 的表示參數名稱是必要的，但參數可以出現在命令中的任何位置。

- **數值** 表示參數名稱是選擇性的，但若省略名稱，參數必須位於數位所指定的位置。 例如， `2` 指出當省略參數名稱時，參數必須是命令中的第二個或唯一未命名的參數。 使用參數名稱時，參數可以出現在命令中的任何位置。

- **預設值** 。 如果您未在命令中包含參數，則 PowerShell 會使用的參數值或預設行為。

- 接受管線輸入。 指出您是否可以 (true) 或無法 (false) 透過管線將物件傳送至參數。 **根據屬性名稱** ，表示管線物件必須具有與參數名稱相同名稱的屬性。

- **接受萬用字元** 。 指出參數值是否可以包含萬用字元，例如星號 (`*`) 或 () 的問號 `?` 。

## 相關連結

[about_Command_Syntax](About/about_Command_Syntax.md)

[about_Comment_Based_Help](./About/about_Comment_Based_Help.md)

[Get-Command](Get-Command.md)

[支援可更新的說明](/powershell/scripting/developer/module/supporting-updatable-help)

[Update-Help](Update-Help.md)

[撰寫註解型說明主題](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[撰寫 PowerShell Cmdlet 的說明](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)
