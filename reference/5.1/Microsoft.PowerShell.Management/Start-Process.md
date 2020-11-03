---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: b6147b35a8818cf448b1e23f5458550d1c6e5c50
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "93205815"
---
# Start-Process

## 概要
啟動本機電腦上的一或多個處理程序。

## SYNTAX

### Default (預設值)

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [<CommonParameters>]
```

### UseShellExecute

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [<CommonParameters>]
```

## DESCRIPTION

`Start-Process`Cmdlet 會在本機電腦上啟動一或多個處理常式。 依預設， `Start-Process` 會建立新的進程，以繼承目前進程中定義的所有環境變數。

如果要指定在處理程序中執行的程式，請輸入可執行檔或指令碼檔案，或可使用電腦上的程式開啟的檔案。 如果您指定無法執行的檔案，則 `Start-Process` 會啟動與檔案相關聯的程式，類似于 `Invoke-Item` Cmdlet。

您可以使用的參數 `Start-Process` 來指定選項，例如載入使用者設定檔、在新視窗中啟動進程，或使用替代認證。

## 範例

### 範例1：啟動使用預設值的處理常式

此範例會啟動使用目前資料夾中之檔案的處理常式 `Sort.exe` 。 此命令會使用所有預設值，包括預設視窗樣式、工作資料夾和認證。

```powershell
Start-Process -FilePath "sort.exe"
```

### 範例2：列印文字檔

此範例會啟動列印檔案的處理常式 `C:\PS-Test\MyFile.txt` 。

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### 範例3：啟動將專案排序至新檔案的進程

此範例會啟動一個進程，以排序檔案中 `Testsort.txt` 的專案，並傳回檔案中已排序的專案 `Sorted.txt` 。 任何錯誤都會寫入至檔案 `SortError.txt` 。

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

**UseNewEnvironment** 參數會指定進程會以自己的環境變數執行。

### 範例4：在最大化的視窗中啟動進程

此範例會啟動 `Notepad.exe` 進程。 在處理程序完成前，它會最大化視窗並保留視窗。

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### 範例5：以系統管理員身分啟動 PowerShell

此範例會使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### 範例6：使用不同的動詞來啟動處理常式

此範例顯示如何尋找啟動處理常式時可使用的動詞命令。 可用的動詞取決於處理常式中執行之檔案的檔案名副檔名。

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

此範例會使用 `New-Object` 來建立 **PowerShell.exe** 的 **ProcessStartInfo** 物件，這是在 PowerShell 處理常式中執行的檔案。 **ProcessStartInfo** 物件的 **動詞** 屬性顯示您可以使用 **Open** 和 **RunAs** 動詞搭配或執行檔案的 `PowerShell.exe` 任何進程 `.exe` 。

### 範例7：指定進程的引數

這兩個命令都會啟動 Windows 命令直譯器，並 `dir` 在資料夾上發出命令 `Program Files` 。 因為此資料夾包含空格，所以值需要以引號括住。
請注意，第一個命令會將字串指定為 **ArgumentList** 。 第二個命令是字串陣列。

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## PARAMETERS

### -ArgumentList

指定此 Cmdlet 啟動進程時要使用的參數或參數值。 引數可以接受為具有以空格分隔之引數的單一字串，或是以逗號分隔的字串陣列。

如果參數或參數值包含空格，則必須以換用雙引號括住。 如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 根據預設，Cmdlet 會使用目前使用者的認證。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定在處理常式中執行之程式的選擇性路徑和檔案名。 輸入 `.txt` `.doc` 與電腦上程式相關聯之可執行檔或檔（例如或檔案）的名稱。 這是必要參數。

如果您只指定檔案名，請使用 **WorkingDirectory** 參數來指定路徑。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LoadUserProfile

指出此 Cmdlet 會載入儲存在目前使用者的登錄機碼中的 Windows 使用者設定檔 `HKEY_USERS` 。

此參數不會影響 PowerShell 設定檔。 如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewWindow

在目前的主控台視窗中啟動新的處理程序。 PowerShell 預設會開啟新的視窗。

您不能在同一個命令中同時使用 **NoNewWindow** 和 **WindowStyle** 參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回此 Cmdlet 啟動之每個處理程序的處理程序物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### -RedirectStandardError

指定檔案。 此 Cmdlet 會將進程產生的任何錯誤傳送至您指定的檔案。
輸入路徑和檔案名。 根據預設，錯誤會顯示在主控台中。

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardInput

指定檔案。 此 Cmdlet 會從指定的檔案讀取輸入。 輸入輸入檔的路徑和檔案名。 根據預設，處理程序會從鍵盤取得其輸入。

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardOutput

指定檔案。 此 Cmdlet 會將進程產生的輸出傳送至您指定的檔案。
輸入路徑和檔案名。 根據預設，輸出會顯示在主控台中。

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseNewEnvironment

指出此 Cmdlet 會使用為處理常式指定的新環境變數。 根據預設，啟動的進程會以繼承自父進程的環境變數執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verb

指定此 Cmdlet 啟動進程時要使用的動詞命令。 可用的動詞取決於處理常式中執行之檔案的檔案名副檔名。

下表顯示一些常見之處理程序檔案類型的動詞。

| 檔案類型 |                動詞                |
| --------- | ----------------------------------- |
| .cmd      | 編輯、開啟、列印、RunAs、RunAsUser |
| .exe      | Open、RunAs、RunAsUser              |
| .txt      | Open、Print、PrintTo                |
| .wav      | 開啟、播放                          |

若要尋找可搭配在處理常式中執行之檔案使用的動詞，請使用 `New-Object` Cmdlet 來建立檔案的 **ProcessStartInfo** 物件。 可用的動詞位於 **ProcessStartInfo** 物件的 **動詞** 屬性中。 如需詳細資訊，請參閱範例。

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

指出此 Cmdlet 會等待指定的進程及其下階完成，再接受更多輸入。 此參數會抑制命令提示字元或保留視窗，直到處理程式完成為止。

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

### -WindowStyle

指定用於新處理程序之視窗的狀態。 此參數可接受的值包括： **Normal** 、 **Hidden** 、 **最小化** 和 **最大化** 。 預設值為 **Normal** 。

您不能在同一個命令中同時使用 **WindowStyle** 和 **NoNewWindow** 參數。

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkingDirectory

指定新進程的開始位置。 預設值是要啟動的可執行檔或檔的位置。 不支援萬用字元。 路徑名稱不能包含會被視為萬用字元的字元。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無，系統診斷。進程

如果您指定 **PassThru** 參數，此 Cmdlet 會產生 **system.object** 物件。 否則，此 Cmdlet 不會傳回任何輸出。

## 注意

- 這個 Cmdlet 是使用 system.string 類別的 **Start** 方法來執行 **。** 如需此方法的詳細資訊，請參閱 [Process. Start 方法](/dotnet/api/system.diagnostics.process.start#overloads)。

- 在 Windows 上，當您使用 **UseNewEnvironment** 時，新的進程只會啟動針對 **電腦** 範圍定義的預設環境變數。 這會影響 `$env:USERNAME` 設為 **SYSTEM** 的端。 不包含 **使用者** 範圍中的任何變數。

## 相關連結

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Service](Start-Service.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
