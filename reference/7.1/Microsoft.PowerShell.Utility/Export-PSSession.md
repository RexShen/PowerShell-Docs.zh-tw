---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 5d5841720c6187863902a929632e15d1687685e1
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389397"
---
# Export-PSSession

## 概要

從另一個會話匯出命令，並將其儲存在 PowerShell 模組中。

## SYNTAX

### 全部

```
Export-PSSession [-OutputModule] <String> [-Force] [-Encoding <Encoding>]
 [[-CommandName] <String[]>] [-AllowClobber] [-ArgumentList <Object[]>]
 [-CommandType <CommandTypes>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-FormatTypeName] <String[]>] [-Certificate <X509Certificate2>] [-Session] <PSSession>
 [<CommonParameters>]
```

## DESCRIPTION

`Export-PSSession`Cmdlet 會從另一個 powershell 會話取得 Cmdlet、函式、別名和其他命令類型 (PSSession) 在本機或遠端電腦上，並將它們儲存在 PowerShell 模組中。 若要將模組中的命令新增至目前的會話，請使用 `Import-Module` Cmdlet。

不同于 `Import-PSSession` 從另一個 PSSession 將命令匯入目前會話的，會 `Export-PSSession` 將命令儲存在模組中。 這些命令不會匯入目前的工作階段。

若要匯出命令，請使用指令 `New-PSSession` 程式來建立具有您想要匯出之命令的 PSSession。 然後使用 `Export-PSSession` Cmdlet 來匯出命令。

為了防止命令名稱衝突，的預設值 `Export-PSSession` 是匯出所有命令，但目前會話中有命令除外。 您可以使用 **CommandName** 參數來指定要匯出的命令。

此 `Export-PSSession` Cmdlet 會使用 PowerShell 的隱含遠端功能。 當您將命令匯入目前的會話時，它們會以隱含方式在原始會話中或在來源電腦上類似的會話中執行。

## 範例

### 範例1：從 PSSession 匯出命令

此範例會從本機電腦建立新的 PSSession 至 Server01 電腦。 除了存在於目前會話中的所有命令，都會匯出至本機電腦上名為 Server01 的模組。 匯出包含命令的格式化資料。

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

此 `New-PSSession` 命令會在 Server01 電腦上建立 PSSession。 PSSession 會儲存在變數中 `$S` 。 此 `Export-PSSession` 命令會匯出 `$S` 變數的命令，並將資料格式化為 Server01 模組。

### 範例2：匯出 Get 和 Set 命令

此範例會 `Get` 從伺服器匯出所有和 `Set` 命令。

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

這些命令會將 `Get` 和 `Set` 命令從遠端電腦上的 Microsoft exchange Server 嵌入式管理單元，匯出到本機電腦上目錄中的 Exchange 模組 `$PSHOME\Modules` 。
將模組放在目錄中，可供 `$PSHOME\Modules` 電腦的所有使用者存取。

### 範例3：從遠端電腦匯出命令

此範例會從遠端電腦上的 PSSession 匯出 Cmdlet，並將它們儲存在本機電腦上的模組中。 模組中的 Cmdlet 會新增至目前的會話，讓您可以使用它們。

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

此 `New-PSSession` 命令會在 Server01 電腦上建立 PSSession，並將它儲存在 `$S` 變數中。 此 `Export-PSSession` 命令會將名稱開頭為 Test 的 Cmdlet，從的 PSSession 匯出 `$S` 到本機電腦上的 TestCmdlets 模組。

`Remove-PSSession`Cmdlet 會刪除目前會話中的 PSSession `$S` 。 此命令顯示 PSSession 不需要使用中，即可使用從會話匯入的命令。 `Import-Module`Cmdlet 會將 TestCmdlets 模組中的 Cmdlet 新增到目前的會話。 您可以隨時在任何會話中執行此命令。

`Get-Help`Cmdlet 會取得名稱開頭為 Test 之 Cmdlet 的說明。 將模組中的命令新增至目前的會話之後，您可以使用 `Get-Help` 和 `Get-Command` Cmdlet 來瞭解匯入的命令。 `Test-Files`Cmdlet 是從 Server01 電腦匯出，並新增至會話。 此 `Test-Files` Cmdlet 會在匯入命令的電腦上的遠端會話中執行。 PowerShell 會從儲存在 TestCmdlets 模組中的資訊建立會話。

### 範例4：在目前的會話中匯出和 clobber 命令

此範例會將儲存在變數中的命令匯出到目前的會話。

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

此 `Export-PSSession` 命令會將所有命令和所有格式設定資料從變數中的 PSSession 匯出 `$S` 到目前的會話。 **AllowClobber** 參數包含與目前會話中的命令具有相同名稱的命令。

### 範例5：從封閉式 PSSession 匯出命令

此範例示範如何在建立匯出命令的 PSSession 關閉時，以特殊選項執行匯出的命令。

當匯入模組時，如果原始遠端會話已關閉，此模組將會使用任何連接到原始電腦的開啟遠端會話。 如果來源電腦沒有目前的會話，模組將會重新建立會話。

若要在遠端會話中使用特殊選項來執行匯出的命令，您必須先建立具有這些選項的遠端會話，然後再匯入模組。 使用 `New-PSSession` Cmdlet 搭配 **SessionOption** 參數

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

此 `New-PSSessionOption` Cmdlet 會建立 **PSSessionOption** 物件，並將物件儲存在變數中 `$Options` 。 此 `New-PSSession` 命令會在 Server01 電腦上建立 PSSession。
**SessionOption** 參數會使用中儲存的物件 `$Options` 。 會話會儲存在變數中 `$S` 。

此 `Export-PSSession` Cmdlet 會將來自 PSSession 的命令匯出 `$S` 至 Server01 模組。
此 `Remove-PSSession` Cmdlet 會刪除變數中的 PSSession `$S` 。

此 `New-PSSession` Cmdlet 會建立連接到 Server01 電腦的新 PSSession。 **SessionOption** 參數會使用中儲存的物件 `$Options` 。 `Import-Module`Cmdlet 會從 Server01 模組匯入命令。 模組中的命令會在 Server01 電腦上的 PSSession 中執行。

## PARAMETERS

### -AllowClobber

匯出指定的命令，即使它們的名稱與目前工作階段中的命令相同。

如果您匯出的命令與目前會話中的命令名稱相同，則匯出的命令會隱藏或取代原始命令。 如需詳細資訊，請參閱 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)。

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

### -ArgumentList

匯出因使用指定的引數 (參數值) 而產生之命令的變體。

例如，若要匯出憑證中的命令變異數 `Get-Item` (Cert： ) 磁片磁碟機中的 PSSession `$S` ，請輸入 `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Certificate

指定用來簽署格式檔案 ( * .Format.ps1xml) 或腳本模組檔案的用戶端憑證 (. .psm1) 在建立的模組中。 `Export-PSSession` 輸入包含憑證的變數，或可取得憑證的命令或運算式。

若要尋找憑證，請使用 `Get-PfxCertificate` Cmdlet 或使用 `Get-ChildItem` 憑證 (Cert： ) 磁片磁碟機中的 Cmdlet。 若憑證無效或權限不足，則命令會失敗。

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandName

只匯出具有指定的名稱或名稱模式的命令。 允許使用萬用字元。 使用 **CommandName** 或其別名 **Name** 。

根據預設， `Export-PSSession` 會從 PSSession 匯出所有命令，但與目前會話中的命令具有相同名稱的命令除外。 這可防止在目前會話中隱藏或取代命令的命令。 若要匯出所有命令，甚至是隱藏或取代其他命令的命令，請使用 **AllowClobber** 參數。

如果您使用 **CommandName** 參數，除非您使用 **FormatTypeName** 參數，否則不會匯出命令的格式設定檔案。 同樣地，如果您使用 **FormatTypeName** 參數，除非您使用 **CommandName** 參數，否則不會匯出任何命令。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### -CommandType

只匯出指定類型的命令物件。 使用 **CommandType** 或它的別名 **Type** 。

此參數可接受的值如下：

- 別名。 目前會話中的所有 PowerShell 別名。
- 全部。 所有命令類型。 這相當於 `Get-Command -Name *` 。
- 應用程式。 Path 環境變數所列路徑中的 PowerShell 檔案以外的所有檔案 (`$env:path`) ，包括 .txt、.exe 和 .dll 檔案。
- Cmdlet。 目前工作階段中的 Cmdlet。 Cmdlet 是預設值。
- 設定。 PowerShell 設定。 如需詳細資訊，請參閱 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)。
- ExternalScript. Path 環境變數所列路徑中的所有 ps1 檔案都 (`$env:path`) 。
- 篩選和函數。 所有 PowerShell 函數。
- 指令碼： 目前工作階段中的指令碼區塊。
- 流程。 PowerShell 工作流程。 如需詳細資訊，請參閱 [about_Workflows](/powershell/module/PSWorkflow/About/about_Workflows)。

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

指定目標檔案的編碼類型。 預設值是 `utf8NoBOM`。

此參數可接受的值如下：

- `ascii`：使用 ASCII (7 位) 字元集的編碼方式。
- `bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `bigendianutf32`：使用位元組由大到小的順序，以 UTF-32 格式編碼。
- `oem`：針對 MS-DOS 和主控台程式使用預設編碼。
- `unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `utf7`：以 UTF-7 格式編碼。
- `utf8`：以 UTF-8 格式編碼。
- `utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式
- `utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) 
- `utf32`：以 UTF-32 格式編碼。

從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。 如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

即使一或多個現有的輸出檔案具有唯讀屬性，仍覆寫檔案。

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

### -FormatTypeName

只匯出指定之 Microsoft .NET Framework 類型的格式設定指示。 輸入類型名稱。 根據預設， `Export-PSSession` 會針對不在 **System. Management. Automation** 命名空間中的所有 .NET Framework 類型，匯出格式設定指示。

此參數的值必須是要從中匯 `Get-FormatData` 入命令之來源會話中的命令所傳回之類型的名稱。 若要取得遠端會話中的所有格式設定資料，請輸入 `*` 。

如果您使用 **FormatTypeName** 參數，除非您使用 **CommandName** 參數，否則不會匯出任何命令。

如果您使用 **CommandName** 參數，除非您使用 **FormatTypeName** 參數，否則不會匯出命令的格式設定檔案。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

指定以 **ModuleSpecification** 物件形式指定之名稱的模組。 請參閱 [ModuleSpecification (雜湊表) ](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)的「備註」一節。

例如， **FullyQualifiedModule** 參數會接受以下列其中一種格式指定的模組名稱：

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。 您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。 這兩個參數是互斥的。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

只匯出指定 PowerShell 嵌入式管理單元和模組中的命令。 請輸入嵌入式管理單元和模組名稱。 不允許使用萬用字元。

如需詳細資訊，請參閱 `Import-Module` 和 [about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputModule

為所建立的模組指定選擇性的路徑和名稱 `Export-PSSession` 。 預設路徑為 `$home\Documents\WindowsPowerShell\Modules`。 這是必要參數。

如果模組子目錄或所建立的任何檔案 `Export-PSSession` 已經存在，則命令會失敗。 若要覆寫現有的檔案，請使用 **Force** 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定要從中匯出命令的 PSSession。 輸入包含會話物件的變數，或輸入可取得會話物件的命令，例如 `Get-PSSession` 命令。 這是必要參數。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法透過管道傳送物件至 `Export-PSSession` 。

## 輸出

### System.IO.FileInfo

`Export-PSSession` 傳回包含它所建立之模組的檔案清單。

## 注意

`Export-PSSession` 依賴 PowerShell 遠端基礎結構。 若要使用此 Cmdlet，電腦必須針對遠端功能做設定。 如需詳細資訊，請參閱[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。

您無法使用 `Export-PSSession` 匯出 PowerShell 提供者。

匯出的命令會在從中匯出它們的來源 PSSession 中以隱含的方式執行。 從遠端執行命令的詳細資料會由 PowerShell 完全處理。 執行匯出之命令的方式與執行本機命令的方式一樣。

`Export-ModuleMember` 在所匯出的模組中，捕捉和儲存 PSSession 的相關資訊。 當您匯入模組時，如果已匯出命令的 PSSession 已關閉，且沒有使用中的 Pssession 到同一部電腦，則模組中的命令會嘗試重新建立 PSSession。 如果嘗試重新建立 PSSession 失敗，匯出的命令將不會執行。

在模組中捕捉和儲存的會話資訊不 `Export-ModuleMember` 包含會話選項，例如您在喜好設定變數中指定的會話， `$PSSessionOption` 或使用 **SessionOption** `New-PSSession` 、或 Cmdlet 的 SessionOption 參數 `Enter-PSSession` `Invoke-Command` 。 在您匯入模組時，如果原始 PSSession 已關閉，模組將會使用另一個連到同一部電腦的 PSSession (如果有的話)。 若要讓匯入的命令在正確設定的工作階段中執行，請在匯入模組之前，先使用您想要的選項來建立 PSSession。

若要尋找要匯出的命令，請 `Export-PSSession` 使用 `Invoke-Command` Cmdlet `Get-Command` 在 PSSession 中執行命令。 為了取得並儲存命令的格式設定資料，它會使用 `Get-FormatData` 和 `Export-FormatData` Cmdlet。 `Invoke-Command` `Get-Command` `Get-FormatData` `Export-FormatData` 當您執行命令時，您可能會在、、和中看到錯誤訊息 `Export-PSSession` 。 此外， `Export-PSSession` 無法從不包含 `Get-Command` 、 `Get-FormatData` 、 `Select-Object` 和 Cmdlet 的會話匯出命令 `Get-Help` 。

`Export-PSSession` 使用 `Write-Progress` Cmdlet 來顯示命令的進度。 當命令執行時，您可以看到進度列。

匯出的命令與其他遠端命令具有相同的限制，包括無法以使用者介面啟動程式，例如「記事本」。

因為 PowerShell 設定檔不是在 Pssession 中執行，所以無法使用設定檔新增至會話的命令 `Export-PSSession` 。 若要從設定檔匯出命令，請在 `Invoke-Command` 匯出命令之前，先使用命令手動在 PSSession 中執行設定檔。

所建立的模組 `Export-PSSession` 可能包含格式化檔案，即使命令沒有匯入格式化資料。 如果命令不會匯入格式設定資料，所建立的任何格式檔案都將不會包含格式設定資料。

## 相關連結

[about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)

[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[Import-Module](../Microsoft.PowerShell.Core/Import-Module.md)

[Import-PSSession](Import-PSSession.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSSessionOption](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[Remove-PSSession](../Microsoft.PowerShell.Core/Remove-PSSession.md)
