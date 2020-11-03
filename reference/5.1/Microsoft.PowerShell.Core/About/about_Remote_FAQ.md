---
description: 包含有關在 PowerShell 中執行遠端命令的問題和解答。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: da70a3a563031a04aeffd1ead692d9a605f14042
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207935"
---
# <a name="about-remote-faq"></a>關於遠端常見問題集

## <a name="short-description"></a>簡短描述
包含有關在 PowerShell 中執行遠端命令的問題和解答。

## <a name="long-description"></a>完整描述

當您從遠端工作時，您會在一部電腦上的 PowerShell 中輸入命令 (稱為「本機電腦」 ) ，但是命令會在另一部電腦上執行， (稱為「遠端電腦」 ) 。 從遠端工作的體驗應該就像直接在遠端電腦上工作一樣。

注意：若要使用 PowerShell 遠端處理，必須設定遠端電腦以進行遠端處理。 如需詳細資訊，請參閱[about_Remote_Requirements](about_Remote_Requirements.md)。

### <a name="must-both-computers-have-powershell-installed"></a>這兩部電腦都必須安裝 PowerShell 嗎？

是。 若要從遠端工作，本機和遠端電腦必須具有 PowerShell、Microsoft .NET Framework，以及管理 (WS-MANAGEMENT) 通訊協定的 Web 服務。 執行特定命令所需的任何檔案和其他資源都必須位於遠端電腦上。

執行 Windows PowerShell 3.0 的電腦和執行 Windows PowerShell 2.0 的電腦都可以從遠端連線，並執行遠端命令。
不過，某些功能（例如從會話中斷連線並重新連接）的功能，只有在兩部電腦都執行 Windows PowerShell 3.0 時才會運作。

您必須具有連線到遠端電腦的許可權、執行 PowerShell 的許可權，以及存取資料存放區的許可權 (例如) 的檔案和資料夾，以及遠端電腦上的登錄。

如需詳細資訊，請參閱[about_Remote_Requirements](about_Remote_Requirements.md)。

### <a name="how-does-remoting-work"></a>遠端處理的運作方式為何？

當您提交遠端命令時，命令會經由網路傳輸至遠端電腦上的 PowerShell 引擎，並在遠端電腦上的 PowerShell 用戶端中執行。 命令結果會傳送回本機電腦，並顯示在本機電腦上的 PowerShell 會話中。

為了傳輸命令並接收輸出，PowerShell 會使用 WS-Management 的通訊協定。 如需 WS-Management 通訊協定的相關資訊，請參閱 Windows 檔中的 [WS-Management 通訊協定](/windows/win32/winrm/ws-management-protocol) 。

從 Windows PowerShell 3.0 開始，遠端會話會儲存在遠端電腦上。 這可讓您從會話中斷連線，然後從不同的會話或不同的電腦重新連接，而不會中斷命令或遺失狀態。

### <a name="is-powershell-remoting-secure"></a>PowerShell 遠端處理是否安全？

當您連線到遠端電腦時，系統會使用本機電腦上的使用者名稱和密碼認證，或您在命令中提供的認證將您登入遠端電腦。 認證和傳輸的其餘部分都會加密。

若要新增額外的保護，您可以將遠端電腦設定為使用安全通訊端層 (SSL) 而非 HTTP 來接聽 Windows 遠端管理 (WinRM) 要求。 然後， **UseSSL** `Invoke-Command` `New-PSSession` `Enter-PSSession` 當建立連接時，使用者可以使用、和 Cmdlet 的 UseSSL 參數。 此選項會使用更安全的 HTTPS 通道，而不是 HTTP。

### <a name="do-all-remote-commands-require-powershell-remoting"></a>所有遠端命令都需要 PowerShell 遠端處理嗎？

否。 有數個 Cmdlet 具有 **ComputerName** 參數，可讓您從遠端電腦取得物件。

這些 Cmdlet 不會使用 PowerShell 遠端處理。 因此，您可以在任何執行 PowerShell 的電腦上使用它們，即使電腦未設定 PowerShell 遠端功能，或電腦不符合 PowerShell 遠端處理的需求。

這些 Cmdlet 包含下列各項：

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

若要尋找具有 **ComputerName** 參數的所有 Cmdlet，請輸入：

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

若要判斷特定 Cmdlet 的 **ComputerName** 參數是否需要 PowerShell 遠端處理，請參閱參數描述。 若要顯示參數描述，請輸入：

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

例如：

```powershell
Get-Help Get-Process -Parameter ComputerName
```

若為所有其他命令，請使用 `Invoke-Command` Cmdlet。

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a>如何? 在遠端電腦上執行命令？

若要在遠端電腦上執行命令，請使用 `Invoke-Command` Cmdlet。

以大括弧括住命令 (`{}`) 將它設為腳本區塊。 使用的 **ScriptBlock** 參數 `Invoke-Command` 來指定命令。

您可以使用的 **ComputerName** 參數 `Invoke-Command` 來指定遠端電腦。 或者，您可以建立遠端電腦的持續連線 (會話) 然後使用的 **session** 參數 `Invoke-Command` 在會話中執行命令。

例如，下列命令會 `Get-Process` 從遠端執行命令。

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

若要中斷遠端命令，請輸入<kbd>CTRL</kbd> + <kbd>C</kbd>。 中斷要求會傳遞至遠端電腦，並在該處終止遠端命令。

如需遠端命令的詳細資訊，請參閱 about_Remote 以及支援遠端處理之 Cmdlet 的說明主題。

### <a name="can-i-just-telnet-into-a-remote-computer"></a>我可以只是 telnet 進入遠端電腦嗎？

您可以使用此 `Enter-PSSession` Cmdlet 來啟動遠端電腦的互動式會話。

在 PowerShell 提示字元中，輸入：

```powershell
Enter-PSSession <ComputerName>
```

命令提示字元會變更，顯示您已連線到遠端電腦。

```
<ComputerName>\C:>
```

現在，您輸入的命令會在遠端電腦上執行，就像您直接在遠端電腦上輸入一樣。

若要結束互動式工作階段，請輸入：

```powershell
Exit-PSSession
```

互動式會話是使用 WS-Management 通訊協定的持續性會話。 這與使用 Telnet 不同，但提供類似的體驗。

如需詳細資訊，請參閱`Enter-PSSession`。

### <a name="can-i-create-a-persistent-connection"></a>我可以建立持續性連接嗎？

是。 您可以指定遠端電腦的名稱、NetBIOS 名稱或其 IP 位址，以執行遠端命令。 或者，您可以指定連接至遠端電腦 (PSSession) 的 PowerShell 會話，以執行遠端命令。

當您使用或的 **ComputerName** 參數 `Invoke-Command` 時 `Enter-PSSession` ，PowerShell 會建立暫時的連接。 PowerShell 會使用連接來只執行目前的命令，然後關閉連接。 這是一種非常有效率的方法，可執行單一命令或數個不相關的命令，即使在許多遠端電腦上也一樣。

當您使用 `New-PSSession` Cmdlet 建立 pssession 時，PowerShell 會為 pssession 建立持續連線。 然後，您可以在 PSSession 中執行多個命令，包括共用資料的命令。

一般來說，您會建立 PSSession 來執行一系列共用資料的相關命令。 否則， **ComputerName** 參數所建立的暫時連接就足以滿足大部分的命令。

如需會話的詳細資訊，請參閱 about_PSSessions。

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a>我可以一次在一部以上的電腦上執行命令嗎？

是。 Cmdlet 的 **ComputerName** 參數 `Invoke-Command` 接受多個電腦名稱稱，而 **Session** 參數則接受多個 pssession。

當您執行 `Invoke-Command` 命令時，PowerShell 會在所有指定的電腦或所有指定的 pssession 中執行命令。

PowerShell 可以管理數以百計的並行遠端連線。 不過，您可以傳送的遠端命令數目可能會受限於您的電腦資源及其建立和維護多個網路連線的容量。

如需詳細資訊，請參閱說明主題中的範例 `Invoke-Command` 。

### <a name="where-are-my-profiles"></a>我的設定檔在哪裡？

PowerShell 設定檔不會自動在遠端會話中執行，因此設定檔新增的命令不會出現在會話中。 此外，在 `$profile` 遠端會話中不會填入自動變數。

若要在會話中執行設定檔，請使用 `Invoke-Command` Cmdlet。

例如，下列命令會從的會話中的本機電腦執行適用設定檔 `$s` 。

```
Invoke-Command -Session $s -FilePath $profile
```

下列命令會從會話中的遠端電腦執行適用設定檔 `$s` 。 因為 `$profile` 未填入變數，所以命令會使用設定檔的明確路徑。

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

執行此命令之後，就可以在中使用設定檔新增至會話的命令 `$s` 。

您也可以在會話設定中使用啟動腳本，以在每個使用會話設定的遠端會話中執行設定檔。

如需 PowerShell 設定檔的詳細資訊，請參閱 about_Profiles。
如需會話設定的詳細資訊，請參閱 `Register-PSSessionConfiguration` 。

### <a name="how-does-throttling-work-on-remote-commands"></a>節流在遠端命令上的運作方式為何？

為了協助您管理本機電腦上的資源，PowerShell 包含每個命令的節流功能，可讓您限制針對每個命令所建立的並行遠端連線數目。

預設值為32同時連線，但您可以使用 Cmdlet 的 **ThrottleLimit** 參數來設定特定命令的自訂節流限制。

當您使用節流功能時，請記住它會套用至每個命令，而不是套用至整個會話或電腦。 如果您在數個會話或 Pssession 中同時執行命令，並行連接數目就是所有會話中並行連接的總和。

若要使用 **ThrottleLimit** 參數尋找 Cmdlet，請輸入：

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a>遠端命令的輸出與本機輸出有何不同？

當您在本機使用 PowerShell 時，您會傳送和接收「即時」 .NET Framework 物件;「即時」物件是與實際程式或系統元件相關聯的物件。 當您叫用方法或變更即時物件的屬性時，變更會影響實際的程式或元件。 此外，當程式或元件的屬性變更時，代表它們的物件屬性也會變更。

不過，因為大部分的即時物件無法透過網路傳輸，所以 PowerShell 會「序列化」遠端命令中傳送的大部分物件，也就是說，它會將每個物件轉換成 XML (條件約束語言（XML [CLiXML]） ) 資料元素以進行傳輸。

當 PowerShell 收到序列化的物件時，它會將 XML 轉換成還原序列化的物件類型。 還原序列化的物件是在上一次程式或元件的屬性正確記錄，但不再是「即時」，也就是它不再與元件直接相關聯。 而且會移除這些方法，因為這些方法不再有效。

一般而言，您可以使用已還原序列化的物件，就像使用即時物件一樣，但是您必須知道其限制。 此外，Cmdlet 所傳回的物件 `Invoke-Command` 會有其他屬性，可協助您判斷命令的來源。

某些物件類型（例如 DirectoryInfo 物件和 Guid）會在收到時轉換回即時物件。 這些物件不需要任何特殊處理或格式化。

如需有關解讀和格式化遠端輸出的詳細資訊，請參閱 [about_Remote_Output](about_Remote_Output.md)。

### <a name="can-i-run-background-jobs-remotely"></a>我可以從遠端執行背景工作嗎？

是。 PowerShell 背景工作是非同步執行的 PowerShell 命令，而不需要與會話互動。 當您啟動背景工作時，命令提示字元會立即傳回，而且您可以在工作執行時繼續在會話中工作，即使執行時間有一段很長的時間。

即使正在執行其他命令，您也可以啟動背景工作，因為背景工作一律會在暫時會話中以非同步方式執行。

您可以在本機或遠端電腦上執行背景工作。 根據預設，背景工作會在本機電腦上執行。 不過，您可以使用 Cmdlet 的 **AsJob** 參數， `Invoke-Command` 以背景工作的形式執行任何遠端命令。 而且，您可以使用 `Invoke-Command` `Start-Job` 從遠端執行命令。

如需 PowerShell 中背景工作的詳細資訊，請參閱 [about_Jobs (about_Jobs md) ] 和 [about_Remote_Jobs (about_Remote_Jobs md) ]。

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a>我可以在遠端電腦上執行 windows 程式嗎？

您可以使用 PowerShell 遠端命令，在遠端電腦上執行以 Windows 為基礎的程式。 例如，您可以 `Shutdown.exe` `Ipconfig.exe` 在遠端電腦上執行或。

不過，您無法使用 PowerShell 命令來開啟遠端電腦上任何程式的使用者介面。

當您在遠端電腦上啟動 Windows 程式時，命令不會完成，且 PowerShell 命令提示字元不會傳回，直到程式完成為止，或直到您按下<kbd>CTRL</kbd> + <kbd>C</kbd>以中斷命令。 例如，如果您在 `Ipconfig.exe` 遠端電腦上執行程式，則在完成之前，命令提示字元不會傳回 `Ipconfig.exe` 。

如果您使用遠端命令來啟動具有使用者介面的程式，則程式進程會啟動，但不會顯示使用者介面。 PowerShell 命令未完成，而且在您停止程式進程或直到您按下<kbd>CTRL</kbd> + <kbd>C</kbd>（會中斷命令並停止進程）之前，命令提示字元都不會傳回。

例如，如果您使用 PowerShell 命令 `Notepad` 在遠端電腦上執行，則會在遠端電腦上啟動「記事本」處理常式，但不會顯示「記事本」使用者介面。 若要中斷命令並還原命令提示字元，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a>我可以限制使用者可以在我的電腦上遠端執行的命令嗎？

是。 每個遠端會話都必須使用遠端電腦上的其中一個會話設定。 您可以管理電腦上的會話設定 (以及這些會話設定的許可權) 來判斷誰可以在您的電腦上遠端執行命令，以及他們可以執行的命令。

會話設定會設定會話的環境。 您可以使用會執行新設定類別的元件，或使用在會話中執行的腳本來定義設定。 設定可以判斷會話中可用的命令。
此外，設定可以包含保護電腦的設定，例如限制會話可在單一物件或命令中從遠端接收的資料量的設定。 您也可以指定安全描述項，以決定使用設定時所需的許可權。

此 `Enable-PSRemoting` Cmdlet 會在您的電腦上建立預設會話設定： microsoft.powershell32 (64 位作業系統，但僅) 。 `Enable-PSRemoting` 將設定的安全描述項設定為只允許您電腦上 Administrators 群組的成員使用它們。

您可以使用會話設定 Cmdlet 來編輯預設會話設定、建立新的會話設定，以及變更所有會話設定的安全描述項。

從 Windows PowerShell 3.0 開始，此 `New-PSSessionConfigurationFile` Cmdlet 可讓您使用文字檔來建立自訂會話設定。 此檔案包含設定語言模式的選項，以及指定在使用會話設定的會話中可用的 Cmdlet 和模組的選項。

當使用者使用 `Invoke-Command` 、 `New-PSSession` 或 Cmdlet 時 `Enter-PSSession` ，可以使用 **ConfigurationName** 參數來表示會話所使用的會話設定。 此外，他們可以變更會話中喜好設定變數的值，藉以變更會話使用的預設設定 `$PSSessionConfigurationName` 。

如需會話設定的詳細資訊，請參閱 session configuration Cmdlet 的說明。 若要尋找會話設定 Cmdlet，請輸入：

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a>什麼是傳入和傳出的設定？

涉及多部電腦最常見的 PowerShell 遠端處理案例是一對多的設定，其中一部本機電腦 (系統管理員的電腦) 在多部遠端電腦上執行 PowerShell 命令。 這就是所謂的「展開傳送」案例。

不過，在某些企業中，設定是多對一的，其中許多用戶端電腦會連線到執行 PowerShell 的單一遠端電腦，例如檔案伺服器或 kiosk。 這就是所謂的「收合傳送」設定。

PowerShell 遠端支援展開和收合傳送的設定。

針對展開傳送設定，PowerShell 會使用 Web 服務進行管理 (WS-MANAGEMENT) 通訊協定，以及支援 Microsoft WS-MANAGEMENT 的 WinRM 服務。 當本機電腦連線到遠端電腦時，WS-Management 會建立連線，並使用適用于 PowerShell 的外掛程式，在遠端電腦上啟動 PowerShell 主機進程 ( # A0) 。 使用者可以指定替代埠、替代會話設定，以及其他自訂遠端連線的功能。

為了支援「收合傳送」設定，PowerShell 會使用網際網路資訊服務 (IIS) 來裝載 WS-MANAGEMENT、載入 PowerShell 外掛程式，以及啟動 PowerShell。 在此案例中，您不會在個別進程中啟動每個 PowerShell 會話，而是在相同的主機進程中執行所有的 PowerShell 會話。

在 Windows XP 或 Windows Server 2003 中，不支援 IIS 裝載和扇入遠端系統管理。

在 [收合傳送] 設定中，使用者可以指定連接 URI 和 HTTP 端點，包括傳輸、電腦名稱稱、埠和應用程式名稱。
IIS 會將具有指定應用程式名稱的所有要求轉送至應用程式。 預設值為 WS-MANAGEMENT，可裝載 PowerShell。

您也可以指定驗證機制，並禁止或允許從 HTTP 和 HTTPS 端點重新導向。

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a>我可以在不在網域中的單一電腦上測試遠端功能嗎？

是。 即使本機電腦不在網域中，也可以使用 PowerShell 遠端功能。 您可以使用遠端功能連接到會話，並在同一部電腦上建立會話。 這些功能的運作方式與連接到遠端電腦時相同。

若要在工作組中的電腦上執行遠端命令，請變更電腦上的下列 Windows 設定。

注意：這些設定會影響系統上的所有使用者，而且可以讓系統更容易遭受惡意攻擊。 進行這些變更時請務必小心。

- Windows Vista、Windows 7、Windows 8：

  建立下列登錄專案，然後將其值設定為1： LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`

  您可以使用下列 PowerShell 命令來新增此專案：

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- Windows Server 2003、Windows Server 2008、Windows Server 2012、Windows Server 2012 R2：

  因為 [網路存取：共用和本機帳戶的安全性模型] 原則的預設設定為 [傳統]，所以不需要進行任何變更。 如果設定變更，請驗證設定。

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a>我可以在另一個網域的電腦上執行遠端命令嗎？

是。 一般而言，命令會在沒有錯誤的情況下執行，不過您可能需要使用、或 Cmdlet 的 **Credential** 參數， `Invoke-Command` `New-PSSession` `Enter-PSSession` 以提供遠端電腦上 Administrators 群組成員的認證。 即使目前的使用者是本機電腦和遠端電腦上的 Administrators 群組成員，有時還是需要這麼做。

但是，如果遠端電腦不是在本機電腦信任的網域中，則遠端電腦可能無法驗證使用者的認證。

若要啟用驗證，請使用下列命令，將遠端電腦新增至 WinRM 中本機電腦的受信任主機清單。 在 PowerShell 提示字元中輸入命令。

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

例如，若要將 Server01 電腦新增至本機電腦上的受信任主機清單，請在 PowerShell 提示字元中輸入下列命令：

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```


## <a name="see-also"></a>另請參閱

[about_Remote](about_Remote.md)

[about_Profiles](about_Profiles.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote_Jobs](about_Remote_Jobs.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
