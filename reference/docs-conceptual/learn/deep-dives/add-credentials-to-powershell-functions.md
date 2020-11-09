---
title: 新增認證支援到 PowerShell 函式
description: 如何將認證參數新增至您的 PowerShell 指令碼、函式與 Cmdlet。
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: 3e4a3f41ccbca1cf97f2e96fd60f22d89be7bc5a
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354621"
---
# <a name="add-credential-support-to-powershell-functions"></a>新增認證支援到 PowerShell 函式

> [!NOTE]
> 本文的[原始版本][]出現在 [@joshduffney][] 所撰寫的部落格中。 此文章已經過編輯並刊登於此網站上。 PowerShell 小組感謝 Josh 分享此內容。 請查看他在 [duffney.io][] 上的部落格。

此文章說明如何將認證參數新增至 PowerShell 函式，以及您想要這樣做的原因。 認證參數可讓您以不同的使用者身分執行函式或 Cmdlet。 最常見的用法是以提高權限的使用者帳戶執行函式或 Cmdlet。

例如，Cmdlet `New-ADUser` 具有 **Credential** 參數，您可以提供網域系統管理員認證來建立網域中的帳戶。 假設您執行 PowerShell 工作階段的一般帳戶尚未擁有該存取權。

## <a name="creating-credential-object"></a>建立認證物件

[PSCredential][] 物件代表一組安全性認證，例如，使用者名稱與密碼。 此物件可以當作參數傳遞到函式，該函式會以該認證物件中的使用者帳戶執行。 有幾種方式可讓您建立認證物件。 建立認證物件的第一種方式是使用 PowerShell Cmdlet `Get-Credential`。 當您在沒有參數的情況下執行時，其會提示您輸入使用者名稱與密碼。 或者，您可以使用一些選擇性參數來呼叫 Cmdlet。

若要提前指定網域名稱與使用者名稱，您可以使用 **Credential** 或 **UserName** 參數。 當您使用 **UserName** 參數時，也必須提供 **Message** 值。 下列程式碼示範如何使用 Cmdlet。 您也可以將認證物件儲存在變數中，如此便可多次使用該認證。 在下面的範例中，認證物件會儲存於 `$Cred` 變數中。

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

有時，您無法使用互動式方法來建立先前範例所示的認證物件。 大部分的自動化工具都需要非互動式方法。 若要在沒有使用者互動的情況下建立認證，請建立包含密碼的安全字串。 接著，將安全字串與使用者名稱傳遞到 `System.Management.Automation.PSCredential()` 方法。

使用下列命令來建立包含密碼的安全字串：

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

**AsPlainText** 與 **Force** 參數都是必要參數。 如果沒有那些參數，您就會收到一則訊息，警告您不應將純文字傳遞到安全字串。 PowerShell 會傳回此警告，因為純文字密碼會記錄於各種記錄中。 建立安全字串之後，您必須將其傳遞到 `PSCredential()` 方法以建立認證物件。 在下面的範例中，`$password` 變數包含安全字串，而 `$Cred` 包含認證物件。

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

既然您已了解如何建立認證物件，現在，您可以將認證參數新增到 PowerShell 函式。

## <a name="adding-a-credential-parameter"></a>新增認證參數

就像任何其他參數一樣，您可以透過在函式的 `param` 區塊中新增此參數來開始。
建議您將參數命名為 `$Credential`，因為那是現有 PowerShell Cmdlet 所使用的名稱。 參數的類型應該是 `[System.Management.Automation.PSCredential]`。

下列範例顯示名為 `Get-Something` 之函式的參數區塊。 其具有兩個參數：`$Name` 與 `$Credential`。

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

此範例中的程式碼就足以擁有運作中的認證參數，不過，您可以新增一些內容，以使其更為強固。

- 新增 `[ValidateNotNull()]` 驗證屬性，以檢查要傳遞到 **Credential** 的值。 如果參數值為 Null，此屬性就會防止函式以無效的認證執行。

- 加入 `[System.Management.Automation.Credential()]`。 這可讓您以字串形式傳入使用者名稱，並以互動式提示輸入密碼。

- 將 `$Credential` 參數的預設值設定為 `[System.Management.Automation.PSCredential]::Empty`。 您的函式可能會將此 `$Credential` 物件傳遞到現有的 PowerShell Cmdlet。 為函式內呼叫的 Cmdlet 提供 Null 值會造成錯誤。 提供空白的認證物件可避免這個錯誤。

> [!TIP]
> 某些接受認證參數的 Cmdlet 不應支援 `[System.Management.Automation.PSCredential]::Empty`。 如需因應措施，請參閱[處理舊版 Cmdlet](#dealing-with-legacy-cmdlets) 一節。

## <a name="using-credential-parameters"></a>使用認證參數

下列範例示範如何使用認證參數。 此範例顯示名為 `Set-RemoteRegistryValue` 的函式，而其不在 [The Pester Book][] 中。 此函式會使用上一節所述的技術來定義認證參數。 此函式會使用函式所建立的 `$Credential` 變數來呼叫 `Invoke-Command`。 這可讓您變更正在執行 `Invoke-Command` 的使用者。 由於 `$Credential` 的預設值是空白認證，因此，函式可以在未提供認證的情況下執行。

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

下列各節說明提供認證給 `Set-RemoteRegistryValue` 的不同方法。

### <a name="prompting-for-credentials"></a>提示輸入認證

在執行階段使用以括弧 `()` 括起來的 `Get-Credential`，會導致先執行 `Get-credential`。 系統會提示您輸入使用者名稱和密碼。 您可以使用 `Get-credential` 的 **Credential** 或 **UserName** 參數，預先填入使用者名稱與網域。 下列範例使用稱為展開的技術，將參數傳遞到 `Set-RemoteRegistryValue` 函式。 如需有關展開的詳細資訊，請參閱 [about_Splatting][] 文章。

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![在執行階段取得認證](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

使用 `(Get-Credential)` 似乎很繁瑣。 一般來說，當您只搭配使用者名稱使用 **Credential** 參數時，此 Cmdlet 會自動提示輸入密碼。 `[System.Management.Automation.Credential()]` 屬性會啟用此行為。

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![提示輸入認證](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> 為了設定顯示的登錄值，這些範例假設您已安裝 Windows 的 **Web 伺服器** 功能。 在必要時執行 `Install-WindowsFeature Web-Server` 與 `Install-WindowsFeature web-mgmt-tools`。

### <a name="provide-credentials-in-a-variable"></a>在變數中提供認證。

您也可以提前填入認證變數，並將其傳遞到 `Set-RemoteRegistryValue` 函式的 **Credential** 參數。 使用此方法搭配持續整合/持續部署 (CI/CD) 工具，例如 Jenkins、TeamCity 與 Octopus Deploy。 如需使用 Jenkins 的範例，請參閱 Hodge 的部落格文章：[在 Windows 上使用 Jenkins 和 PowerShell 進行自動化 - 第 2 部分][]。

此範例會使用 .NET 方法，來建立認證物件與要傳入密碼的安全字串。

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

在此範例中，安全字串會使用純文字密碼來建立。 先前提到的所有 CI/CD 都有一個安全方法，可在執行階段提供該密碼。 使用那些工具時，請以您使用之 CI/CD 工具內定義的變數取代純文字密碼。

### <a name="run-without-credentials"></a>在沒有認證的情況下執行

由於 `$Credential` 預設為空白的認證物件，因此，您可以在沒有認證的情況下執行命令，如下列範例所示：

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a>處理舊版 Cmdlet

並非所有 Cmdlet 都支援認證物件或允許空白認證。 相反地，此 Cmdlet 需要使用者名稱與密碼參數作為字串。 有幾種方法可以解決此限制。

### <a name="using-if-else-to-handle-empty-credentials"></a>使用 if-else 來處理空白認證

在此案例中，您想要執行的 Cmdlet 不接受空白的認證物件。 此範例只會在其不是空白時，將 **Credential** 參數新增至 `Invoke-Command`。 否則，其會在沒有 **Credential** 參數情況下執行 `Invoke-Command`。

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a>使用展開來處理空白認證

此範例會使用參數展開來呼叫舊版 Cmdlet。 `$Credential` 物件已有條件地新增至雜湊表以進行展開，並避免重複執行 `Invoke-Command` 指令碼區塊的需求。 若要深入了解如何在函式內部展開，請參閱[展開進階函式中的參數][]部落格文章。

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a>使用字串密碼

`Invoke-Sqlcmd` Cmdlet 是接受字串作為密碼的 Cmdlet 範例。
`Invoke-Sqlcmd` 可讓您執行簡單的 SQL 插入、更新及刪除陳述式。 `Invoke-Sqlcmd` 需要純文字的使用者名稱與密碼，而不是更安全的認證物件。 此範例示範如何從認證物件擷取使用者名稱與密碼。

此範例中的 `Get-AllSQLDatabases` 函式會呼叫 `Invoke-Sqlcmd` Cmdlet，來查詢 SQL 伺服器中的所有資料庫。 此函式會使用先前範例中所使用的相同屬性，來定義 **Credential** 參數。 由於使用者名稱與密碼存在於 `$Credential` 變數中，因此，您可以擷取那些值來與 `Invoke-Sqlcmd` 搭配使用。

使用者名稱可以從 `$Credential` 變數的 **UserName** 屬性中取得。 若要取得密碼，您必須使用 `$Credential` 物件的 `GetNetworkCredential()` 方法。 值均會擷取到變數中，而變數會新增到可用來將參數展開到 `Invoke-Sqlcmd` 的雜湊表中。

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a>持續了解認證管理

安全地建立及儲存認證物件可能很難。 下列資源可協助您維護 PowerShell 認證。

- [BetterCredentials][]
- [Azure Key Vault][]
- [Vault 專案][]
- [SecretManagement 模組][]

<!-- link references -->
[原始版本]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Vault 專案]: https://www.vaultproject.io/
[展開進階函式中的參數]: https://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[在 Windows 上使用 Jenkins 和 PowerShell 進行自動化 - 第 2 部分]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2 \(英文\)
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[The Pester Book]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[SecretManagement 模組]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
