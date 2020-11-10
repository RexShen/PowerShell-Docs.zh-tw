---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: 73bc543ff9525a51b1e776ec1c24e9baca4e4f71
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390706"
---
# New-PSSessionOption

## 概要
建立包含 PSSession 之進階選項的物件。

## SYNTAX

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## DESCRIPTION

`New-PSSessionOption`Cmdlet 會建立一個物件，其中包含使用者管理的會話 ( **PSSession** ) 的 advanced 選項。 您可以使用物件作為建立 **PSSession** 之 Cmdlet 的 **SessionOption** 參數值，例如 `New-PSSession` 、 `Enter-PSSession` 和 `Invoke-Command` 。

如果沒有參數，會 `New-PSSessionOption` 產生包含所有選項之預設值的物件。 因為所有屬性都可以編輯，所以您可以使用產生的物件作為範本，然後為您的企業建立標準選項物件。

您也可以在喜好設定變數中儲存會話選項物件 `$PSSessionOption` 。 此變數的值會替工作階段選項建立新的預設值。 在沒有為工作階段設定任何工作階段選項時，它們就會生效，而且它們的優先順序高於在工作階段設定中設定的選項，但是您可以透過在建立工作階段的 Cmdlet 中，指定工作階段選項或工作階段選項物件來覆寫它們。 如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。

當您在建立工作階段的 Cmdlet 中使用工作階段選項物件時，工作階段選項值的優先順序高於在 $PSSessionOption 喜好設定變數和工作階段設定中設定的工作階段預設值。 不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

## 範例

### 範例1：建立預設會話選項

此命令會建立具有所有預設值的會話選項物件。

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### 範例2：使用會話選項物件設定會話

此範例說明如何使用工作階段選項物件設定工作階段。

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

第一個命令會建立新的會話選項物件，並將它儲存在變數的值中 `$pso` 。 第二個命令會使用 `New-PSSession` Cmdlet 在 Server01 遠端電腦上建立會話。 此命令會使用變數值中的 session 選項物件 `$pso` 做為命令的 **SessionOption** 參數值。

### 範例3：啟動互動式會話

此命令會使用 `Enter-PSSession` Cmdlet 來啟動 Server01 電腦的互動式會話。

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

**SessionOption** 參數的值是 `New-PSSessionOption` 具有 **nocompression** 和 **NoCompression** 參數的命令。

此 `New-PSSessionOption` 命令會以括弧括住，以確保它會在命令之前執行 `Enter-PSSession` 。

### 範例4：修改會話選項物件

這個範例示範您可以修改會話選項物件。 所有屬性皆具有讀取/寫入值。

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

請使用此方法為您的企業建立標準工作階段物件，然後用它來針對特定用途建立自訂版本。

### 範例5：建立喜好設定變數

此命令會建立 `$PSSessionOption` 喜好設定變數。

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

當 `$PSSessionOption` 喜好設定變數發生在會話中時，它會在使用 `New-PSSession` 、 `Enter-PSSession` 和 Cmdlet 建立的會話中，建立選項的預設值 `Invoke-Command` 。

若要讓 `$PSSessionOption` 變數在所有會話中都可使用，請將它新增至您的 powershell 會話和 powershell 設定檔。

如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。
如需設定檔的詳細資訊，請參閱 [about_Profiles](About/about_Profiles.md)。

### 範例6：滿足遠端會話設定的需求

此範例說明如何使用 **SessionOption** 物件來滿足遠端工作階段設定的要求。

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

第一個命令會使用 `New-PSSessionOption` Cmdlet 來建立具有 **SkipCNCheck** 屬性的會話選項物件。 此命令會將產生的會話物件儲存在 `$skipCN` 變數中。

第二個命令會使用 `New-PSSession` Cmdlet 在遠端電腦上建立新的會話。 `$skipCN`檢查變數會在 **SessionOption** 參數的值中使用。

因為電腦是透過其 IP 位址來識別，所以 **ComputerName** 參數的值不符合用於安全通訊端層 (SSL) 之憑證中的任何一般名稱。 因此，需要 **SkipCNCheck** 選項。

### 範例7：讓引數可供遠端會話使用

此範例示範如何使用 Cmdlet 的 **ApplicationArguments** 參數 `New-PSSessionOption` ，讓其他資料可供遠端會話使用。

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

第一個命令會建立包含兩個索引鍵（ **Team** 和 **Use** ）的雜湊表。 此命令會將雜湊表儲存在 `$team` 變數中。 如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](about/about_Hash_Tables.md)。

接下來， `New-PSSessionOption` 使用 **ApplicationArguments** 參數的 Cmdlet 會建立儲存在變數中的會話選項物件 `$team` 。 當 `New-PSSessionOption` 建立會話選項物件時，它會自動將 **ApplicationArguments** 參數值中的雜湊表轉換成基本字典，以便將資料可靠地傳輸至遠端會話。

`New-PSSession`Cmdlet 會啟動 Server01 電腦上的會話。 它會使用 **SessionOption** 參數將選項包含在變數中 `$teamOption` 。

此 `Invoke-Command` Cmdlet 會示範變數中的資料 `$team` 可供遠端會話中的命令使用。 資料會出現在自動變數的 **ApplicationArguments** 屬性中 `$PSSenderInfo` 。

最後 `Invoke-Command` 會顯示如何使用資料。

## PARAMETERS

### -ApplicationArguments

指定傳送至遠端工作階段的基本字典。 遠端會話中的命令和腳本（包括會話設定中的啟動腳本）可以在自動變數的 **ApplicationArguments** 屬性中找到此字典 `$PSSenderInfo` 。 您可以使用此參數將資料傳送至遠端工作階段。

如需詳細資訊，請參閱 [about_Hash_Tables](about/about_Hash_Tables.md)、 [about_Session_Configurations](About/about_Session_Configurations.md)和 [about_Automatic_Variables](about/about_Automatic_Variables.md)。

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CancelTimeout

判斷 PowerShell 等候取消作業 (CTRL + C) 在結束之前完成的時間。
輸入以毫秒為單位的值。

預設值為 60000 (一分鐘)。 值為 0 (零) 表示無逾時；命令會無限期繼續執行。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### -Culture

指定要用於工作階段的文化特性。 以格式輸入文化特性名稱 `<languagecode2>-<country/regioncode2>` (例如 `ja-JP`) 、包含 **cultureinfo** 物件的變數，或可取得 **cultureinfo** 物件的命令。

預設值為 `$Null` ，而在作業系統中設定的文化特性會在會話中使用。

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout

決定當遠端電腦未收到來自本機電腦的任何通訊時，會話保持開啟的時間長度。 這包括了信號信號。 當間隔時間過期時，工作階段就會關閉。

如果您想要中斷連線並重新連線到會話，閒置的超時值是很重要的。 您只能在工作階段尚未逾時時重新連線。

輸入以毫秒為單位的值。 最小值為 60000 (1 分鐘)。 最大值為工作階段設定之 **MaxIdleTimeoutms** 屬性的值。 預設值-1 不會設定閒置的超時時間。

會話會使用會話選項中設定的空閒超時時間（如果有的話）。 如果未設定 (-1) ，會話就會使用會話設定的 **IdleTimeoutMs** 屬性值或 WSMan shell 超時值 (`WSMan:\<ComputerName>\Shell\IdleTimeout`) （以最短者為准）。

如果工作階段選項中設定的閒置逾時超出工作階段設定之 **MaxIdleTimeoutMs** 屬性的值，建立工作階段的命令會失敗。

**預設的** **IdleTimeoutMs** 值為7200000毫秒 (2 小時) 。 其 **MaxIdleTimeoutMs** 值為2147483647毫秒 (\> 24 天) 。 WSMan shell 空閒超時 () 的預設值 `WSMan:\<ComputerName>\Shell\IdleTimeout` 為7200000毫秒 (2 小時) 。

從會話中斷連線或重新連線至會話時，會話的閒置超時值也可以變更。 如需詳細資訊，請參閱 `Disconnect-PSSession` 和 `Connect-PSSession`。

在 Windows PowerShell 2.0 中， **IdleTimeout** 參數的預設值為 240000 (4 分鐘)。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludePortInSPN

在服務主體名稱中包含通訊埠編號 (SPN) 用於 Kerberos 驗證，例如 `HTTP://<ComputerName>:5985` 。 此選項允許使用非預設 SPN 的用戶端，向使用 Kerberos 驗證的遠端電腦進行驗證。

此選項是針對支援 Kerberos 驗證的多項服務在不同使用者帳戶底下執行的企業所設計。 例如，允許 Kerberos 驗證的 IIS 應用程式可能需要將預設 SPN 註冊至與電腦帳戶不同的使用者帳戶。 在這種情況下，PowerShell 遠端處理無法使用 Kerberos 進行驗證，因為它需要已向電腦帳戶註冊的 SPN。 若要解決這個問題，系統管理員可以建立不同的 Spn，例如使用 **Setspn.exe** 註冊到不同的使用者帳戶，並可透過在 SPN 中包含埠號碼來區分它們。

如需詳細資訊，請參閱 [Setspn 總覽](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))。

此參數是在 Windows PowerShell 3.0 引進。

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

### -MaxConnectionRetryCount

指定當目前的嘗試因網路問題而失敗時，PowerShell 嘗試連接至目的電腦的次數。 預設值為 5。

已針對 PowerShell 5.0 版新增此參數。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedDataSizePerCommand

指定本機電腦可以在單一命令中從遠端電腦收到的位元組數上限。 輸入以位元組為單位的值。 依照預設，並沒有資料大小限制。

此選項是為了保護用戶端電腦上的資源而設計。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSize

指定本機電腦可從遠端電腦接收之物件的大小上限。 此選項是為了保護用戶端電腦上的資源而設計。 輸入以位元組為單位的值。

在 Windows PowerShell 2.0 中，如果您省略此參數，就不會有物件大小限制。 從 Windows PowerShell 3.0 開始，如果您省略此參數，預設值為 200 MB。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRedirection

判斷在連接失敗之前，PowerShell 將連接重新導向至替代統一資源識別項 (URI) 的次數。 預設值為 5。 值為 0 (零) 將禁止所有重新導向。

只有在建立會話的命令中使用 **AllowRedirection** 參數時，會話中才會使用此選項。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCompression

關閉工作階段中的封包壓縮。 壓縮會使用更多處理器週期，但是它可以加快傳輸速度。

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

### -NoEncryption

關閉資料加密。

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

### -NoMachineProfile

避免載入使用者的 Windows 使用者設定檔。 如此一來，可能可以更快速地建立工作階段，但是工作階段中將沒有使用者特定登錄設定、像是環境變數這樣的項目以及憑證可用。

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

### -OpenTimeout

決定用戶端電腦等待建立工作階段連線的時間。 當間隔時間過期時，建立連線的命令會失敗。 輸入以毫秒為單位的值。

預設值為 180000 (3 分鐘)。 值為 0 (零) 表示無逾時；命令會無限期繼續執行。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeout

決定工作階段中任何操作可以執行的最長時間。 當間隔時間過期時，操作就會失敗 輸入以毫秒為單位的值。

預設值為 180000 (3 分鐘)。 值為 0 (零) 表示無逾時；操作會無限期繼續執行。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

決定在輸出緩衝區已滿時，在中斷連線的工作階段中管理命令輸出的方式。

如果工作階段或工作階段設定中沒有設定輸出緩衝處理模式，預設值為 **Block** 。 使用者也可以在中斷連線工作階段時變更輸出緩衝處理模式。

如果您省略此參數，會話選項物件之 **OutputBufferingMode** 的值為 None。 **Block** 或 **Drop** 的值會覆寫工作階段設定中所設定的輸出緩衝模式傳輸選項。 此參數可接受的值為：

- 區塊。 當輸出緩衝區已滿時，會暫停執行直到清除緩衝區為止。
- Drop： 當輸出緩衝區已滿時，會繼續執行。 儲存新的輸出時，會捨棄最舊的輸出。
- 無。 未指定輸出緩衝模式。

如需輸出緩衝模式傳輸選項的詳細資訊，請參閱 `New-PSTransportOption` 。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType

決定使用哪一項機制來解析主機名稱。 此參數可接受的值為：

- IEConfig
- WinHttpConfig
- AutoDetect
- NoProxyServer
- 無

預設值為 None。

如需此參數值的詳細資訊，請參閱 [System.management.automation.remoting.proxyaccesstype 列舉](/dotnet/api/system.management.automation.remoting.proxyaccesstype)。

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication

指定用於 Proxy 解析的驗證方法。 此參數可接受的值包括： **基本** 、 **摘要** 和 **協商** 。 預設值為 **Negotiate** 。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

指定要用於 Proxy 驗證的認證。 輸入包含 **pscredential** 物件的變數，或輸入可取得 **pscredential** 物件的命令，例如 `Get-Credential` 命令。 如果未設定選項，就不會指定任何認證。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCACheck

指定透過 HTTPS 連線時，用戶端不會驗證伺服器憑證是否由受信任的憑證授權單位單位 (CA) 簽署。

請只在透過其他機制讓遠端電腦成為受信任的電腦時才使用此選項，例如當遠端電腦屬於受到實體防護及隔離之網路的一部分，或當遠端電腦在 WinRM 設定中列示為受信任的主機時。

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

### -SkipCNCheck

指定伺服器的憑證一般名稱 (CN) 不需要與伺服器的主機名稱相符。 此選項只有在使用 HTTPS 通訊協定的遠端操作中才會使用。

請只針對受信任的電腦使用此選項。

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

### -SkipRevocationCheck

不驗證伺服器憑證的撤銷狀態。

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

### -UICulture

指定要用於工作階段的 UI 文化特性。

有效值包括：

- 格式的文化特性名稱 `<languagecode2>-<country/regioncode2>` ，例如 `ja-JP`
- 包含 **CultureInfo** 物件的變數
- 取得 **CultureInfo** 物件的命令，例如 `Get-Culture`

預設值為 `$null` ，而且會話中會使用建立會話時在作業系統中設定的 UI 文化特性。

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseUTF16

指出此 Cmdlet 會將 UTF16 格式的要求編碼，而不是 UTF8 格式。

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

### PSSessionOption （管理）

## 注意

如果命令中沒有使用 **SessionOption** 參數來建立 **PSSession** ，則會話選項是由喜好設定變數的屬性值 `$PSSessionOption` （如果已設定）來決定。 如需變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。

工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。 此外，使用工作階段設定檔的工作階段設定會有額外的屬性。

## 相關連結

[Enter-PSSession](Enter-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)
