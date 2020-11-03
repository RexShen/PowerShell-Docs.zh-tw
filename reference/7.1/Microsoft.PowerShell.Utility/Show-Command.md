---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: 86253a8a0bd02a60980cc3655af7bb961acf88ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202168"
---
# Show-Command

## 概要
在圖形視窗中顯示 PowerShell 命令資訊。

## SYNTAX

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

此 `Show-Command` Cmdlet 可讓您在命令視窗中建立 PowerShell 命令。 您可以使用命令視窗的功能來執行命令，或讓它向您傳回命令。

`Show-Command` 是非常有用的教學與學習工具。 `Show-Command` 適用于所有命令類型，包括 Cmdlet、函式、工作流程及 CIM 命令。

如果沒有參數， `Show-Command` 則會顯示命令視窗，其中會列出所有已安裝模組中的所有可用命令。 若要尋找模組中的命令，請從模組下拉式清單中選取模組。 若要選取命令，請按一下命令名稱。

若要使用命令視窗，請選取命令，方法是使用名稱，或按一下 **命令清單中** 的命令名稱。 每個參數集都會顯示在個別的索引標籤上。星號表示必要參數。 若要輸入參數值，請在文字方塊中輸入值，或從下拉式清單方塊中選取值。 若要新增切換參數，請按一下參數核取方塊來加以選取。

當您準備好時，您可以按一下 **Copy** 來將您已經建立的命令複製到剪貼簿或按一下 **Run** 來執行命令。 您也可以使用 **PassThru** 參數將命令傳回到主機程式，例如 PowerShell 主控台。 若要取消命令選取範圍並返回顯示所有命令的視圖，請按 Ctrl 並按一下選取的命令。

在 (ISE) 的 PowerShell 整合式腳本環境中， `Show-Command` 預設會顯示視窗的變化。 如需使用此命令視窗的詳細資訊，請參閱 PowerShell ISE 說明主題。

PowerShell 7 中已重新引入此 Cmdlet。 

由於此 Cmdlet 需要使用者介面，因此無法在 Windows Server Core 或 Windows Nano Server 上運作。 只有支援 Windows 桌面的 Windows 系統才能使用此 Cmdlet。

## 範例

### 範例1：開啟 [命令] 視窗

此範例會顯示視窗的預設視圖 `Show-Command` 。 [ **命令** ] 視窗會顯示電腦上已安裝的所有模組中所有命令的清單。

```powershell
Show-Command
```

### 範例2：在 [命令] 視窗中開啟 Cmdlet

此範例會 `Invoke-Command` 在 **命令** 視窗中顯示 Cmdlet。 您可以使用此顯示來執行 `Invoke-Command` 命令。

```powershell
Show-Command -Name "Invoke-Command"
```

### 範例3：使用指定的參數開啟 Cmdlet

此命令會開啟 `Show-Command` Cmdlet 的視窗 `Connect-PSSession` 。

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

**Height** 和 **Width** 參數指定命令視窗的維度。 **ErrorPopup** 參數會顯示錯誤命令視窗。

當您按一下 [ **執行** ] 時， `Connect-PSSession` 命令就會執行，就如同您在 `Connect-PSSession` 命令列輸入命令一樣。

### 範例4：指定 Cmdlet 的新預設參數值

此範例會使用 `$PSDefaultParameterValues` 自動變數，為 Cmdlet 的 **高度** 、 **寬度** 和 **ErrorPopup** 參數設定新的預設值 `Show-Command` 。

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

現在當您執行 `Show-Command` 命令時，會自動套用新的預設值。 若要在每個 PowerShell 會話中使用這些預設值，請將 `$PSDefaultParameterValues` 變數新增至您的 powershell 設定檔。 如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) 和 [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md)。

### 範例5：將輸出傳送至方格視圖

此命令顯示如何 `Show-Command` 搭配使用和 `Out-GridView` Cmdlet。

```powershell
Show-Command Get-ChildItem | Out-GridView
```

此命令會使用 `Show-Command` Cmdlet 來開啟 Cmdlet 的命令視窗 `Get-ChildItem` 。
當您按一下 [ **執行** ] 按鈕時， `Get-ChildItem` 命令會執行並產生輸出。 管線運算子 ( |) 將命令的輸出傳送 `Get-ChildItem` 至 `Out-GridView` Cmdlet，此 Cmdlet 會 `Get-ChildItem` 在互動式視窗中顯示輸出。

### 範例6：顯示您在命令視窗中建立的命令

此範例顯示您在視窗中建立的命令 `Show-Command` 。 此命令會使用 **PassThru** 參數，它會 `Show-Command` 在字串中傳回結果。

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

例如，如果您使用此 `Show-Command` 視窗來建立一個命令，以 `Get-EventLog` 取得 Windows PowerShell 事件記錄檔中的五個最新事件，然後按一下 **[確定]** ，命令會傳回上面顯示的輸出。 查看命令字串可協助您瞭解 PowerShell。

### 範例7：將命令儲存至變數

此範例示範如何執行當您使用 Cmdlet 的 **PassThru** 參數時所取得的命令字串 `Show-Command` 。 這項策略可讓您看到命令並使用命令。

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

第一個命令會使用 Cmdlet 的 **PassThru** 參數 `Show-Command` ，並將命令的結果儲存在變數中 `$C` 。 在此情況下，我們會使用 `Show-Command` 視窗來建立 `Get-EventLog` 命令，以取得 Windows PowerShell 事件記錄檔中的五個最新事件。 當您按一下 **[確定]** 時， `Show-Command` 會傳回命令字串，該字串會儲存在 `$C` 變數中。

### 範例8：將命令的輸出儲存至變數

此範例使用 **ErrorPopup** 參數，將命令的輸出儲存在變數中。

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

除了在視窗中顯示錯誤之外， **ErrorPopup** 還會將命令輸出傳回目前的命令，而不是建立新的命令。 當您執行此命令時， `Show-Command` 會開啟視窗。 您可以使用視窗功能來設定參數值。 若要執行命令，請按一下視窗中的 [ **執行** `Show-Command` ] 按鈕。

## PARAMETERS

### -ErrorPopup

指出 Cmdlet 除了在命令列顯示錯誤之外，還會在快顯視窗中顯示錯誤。 根據預設，當視窗中執行的命令 `Show-Command` 產生錯誤時，錯誤只會在命令列中顯示。

此外，當您使用視窗) 中的 [ **執行** ] 按鈕來執行命令 (時 `Show-Command` ， **ErrorPopup** 參數會將命令結果傳回給目前的命令，而不是執行命令並將其輸出傳回至新的命令。 您可以使用這項功能將命令結果儲存在變數中。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -高度

指定視窗的高度（ `Show-Command` 以圖元為單位）。 輸入一個介於 300 和螢幕解析度像素數目之間的值。 如果值太大而無法在畫面上顯示命令視窗，則會 `Show-Command` 產生錯誤。 預設高度為 600 像素。 針對 `Show-Command` 包含 **Name** 參數的命令，預設高度為300圖元。

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

顯示指定命令的命令視窗。 輸入一個命令的名稱，例如 Cmdlet、function 或 CIM 命令的名稱。 如果您省略此參數，則會 `Show-Command` 顯示命令視窗，其中會列出電腦上安裝的所有模組中的所有 PowerShell 命令。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCommonParameter

指出此 Cmdlet 會省略命令顯示的一般參數區段。 根據預設，一般參數會出現在命令視窗底部的可展開區段中。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之項目的物件。 根據預設，此 Cmdlet 不會產生任何輸出。 若要執行命令字串，請在命令提示字元中複製並貼上，或將它儲存在變數中，然後使用 `Invoke-Expression` Cmdlet 來執行變數中的字串。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Width

指定視窗的寬度 `Show-Command` （以圖元為單位）。 輸入一個介於 300 和螢幕解析度像素數目之間的值。 如果值太大而無法在畫面上顯示命令視窗，則會 `Show-Command` 產生錯誤。 預設寬度為 300 像素。

```yaml
Type: System.Double
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

您無法透過管道傳送輸入 `Show-Command` 。

## 輸出

### None、System.string、System.object

當您使用 **PassThru** 參數時，會傳回 `Show-Command` 命令字串。 當您使用 **ErrorPopup** 參數時，會將 `Show-Command` 命令輸出 (任何物件) 傳回。 否則，不 `Show-Command` 會產生任何輸出。

## 注意

`Show-Command` 在遠端會話中無法運作。

## 相關連結

