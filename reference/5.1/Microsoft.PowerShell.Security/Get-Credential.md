---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 26c4f8c8dcc1fbd56e29f55a6a8c2e6aa37a2842
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "93208888"
---
# Get-Credential

## 概要
依據使用者名稱與密碼取得認證物件。

## SYNTAX

### CredentialSet (預設值)

```
Get-Credential [-Credential] <PSCredential> [<CommonParameters>]
```

### MessageSet

```
Get-Credential -Message <String> [[-UserName] <String>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Credential`Cmdlet 會為指定的使用者名稱和密碼建立認證物件。 您可以在安全性作業中使用認證物件。

從 PowerShell 3.0 開始，您可以使用 **Message** 參數，在提示使用者輸入其名稱和密碼的對話方塊上指定自訂的訊息。

此 `Get-Credential` Cmdlet 會提示使用者輸入密碼或使用者名稱和密碼。 根據預設，會出現驗證對話方塊提示使用者。 不過，在某些主機程式中，例如 PowerShell 主控台，您可以藉由變更登錄專案在命令列提示使用者。 如需有關此登錄項目的詳細資訊，請參閱附註和範例。

## 範例

### 範例 1

```powershell
$c = Get-Credential
```

此命令會取得認證物件，並將它儲存在 `$c` 變數中。

當您輸入命令時，會出現對話方塊要求使用者名稱和密碼。 當您輸入要求的資訊時，Cmdlet 會建立代表使用者認證的 **PSCredential** 物件，並將其儲存在 `$c` 變數中。

您可以使用該物件做為要求使用者驗證的 Cmdlet 輸入，例如那些包含 **Credential** 參數的 Cmdlet。 不過，某些隨 PowerShell 安裝的提供者不支援 **Credential** 參數。

### 範例 2

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

這些命令會使用 Cmdlet 傳回的認證物件， `Get-Credential` 來驗證遠端電腦上的使用者，讓他們可以使用 Windows Management Instrumentation (WMI) 來管理電腦。

第一個命令會取得認證物件，並將它儲存在 `$c` 變數中。 第二個命令會在命令中使用 credential 物件 `Get-CimInstance` 。 此命令取得 Server01 電腦上磁碟機的相關資訊。

### 範例 3

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

此命令顯示如何 `Get-Credential` 在命令中包含命令  `Get-CimInstance` 。

此命令會使用 `Get-CimInstance` Cmdlet 來取得 Server01 電腦上 BIOS 的相關資訊。 它會使用 **credential** 參數來驗證使用者、Domain01\User01 和 `Get-Credential` 命令，作為 **Credential** 參數的值。

### 範例 4

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

此範例建立的認證包含沒有網域名稱的使用者名稱。

第一個命令取得具有使用者名稱 User01 的認證，並將它儲存在 `$c` 變數中。
第二個命令顯示產生之認證物件的 **Username** 屬性值。

### 範例 5

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

此命令使用 **PromptForCredential** 方法提示使用者輸入使用者名稱和密碼。 此命令會將產生的認證儲存在 `$Credential` 變數中。

**PromptForCredential** 方法是使用 Cmdlet 的替代方法 `Get-Credential` 。 當您使用 **PromptForCredential** 時可以指定標題、訊息和訊息方塊中顯示的使用者名稱。

如需詳細資訊，請參閱 SDK 中的 [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) 檔。

### 範例 6

```powershell
Set-ItemProperty "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds" -Name ConsolePrompting -Value $true
```

此範例示範如何修改登錄，以在命令列提示使用者，而不是使用對話方塊。

該命令會建立 **ConsolePrompting** 登錄項目，並將它的值設為 True。 若要執行此命令，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。

若要使用對話方塊來提示，請將 ConsolePrompting 的值設定為 false ($false) 或使用 `Remove-ItemProperty` Cmdlet 來刪除它。

ConsolePrompting 登錄專案適用于某些主機程式，例如 PowerShell 主控台。 它可能不適用於所有的主機程式。

### 範例 7

這個範例示範如何建立認證物件，此物件與傳回的物件完全相同， `Get-Credential` 而不會提示使用者。 此方法需要純文字密碼，這可能會違反某些企業的安全性標準。

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

第一個命令會將使用者帳戶名稱儲存在 `$User` 參數中。 該值必須具有 "Domain\User" 或 "ComputerName\User" 格式。

第二個命令會使用 `ConvertTo-SecureString` Cmdlet，從純文字密碼建立安全字串。 命令使用 **AsPlainText** 參數指示字串為純文字，並使用 **Force** 參數確認您了解使用純文字的風險。

第三個命令會使用 `New-Object` Cmdlet，從和變數中的值建立 **PSCredential** 物件 `$User` `$PWord` 。

### 範例 8

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

此命令會使用 Cmdlet 的 **Message** 和 **UserName** 參數 `Get-Credential` 。 此命令的格式是為共用的指令碼和函式而設計。 在本例中，訊息會告知使用者為什麼需要認證，並讓使用者相信此為合法要求。

### 範例 9

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

此命令會從 Server01 遠端電腦取得認證。 此命令會使用 `Invoke-Command` Cmdlet `Get-Credential` 在遠端電腦上執行命令。 輸出會顯示 `Get-Credential` 驗證提示中包含的遠端安全性訊息。

## PARAMETERS

### -Credential

指定認證的使用者名稱，例如 **User01** 或 **Domain01\User01** 。 參數名稱 `-Credential` 是選擇性的。

當您提交命令並指定使用者名稱時，系統會提示您輸入密碼。 如果您省略此參數，系統就會提示您輸入使用者名稱和密碼。

從 PowerShell 3.0 開始，如果您輸入不含網域的使用者名稱，則 `Get-Credential` 不會再于名稱之前插入反斜線。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Message

指定顯示在驗證提示中的訊息。 此參數是針對在函式或指令碼中使用而設計。 您可以使用該訊息向使用者說明為何要求認證，以及認證的用途。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

指定使用者名稱。 驗證提示要求使用者名稱的密碼。 根據預設，使用者名稱是空白的，且驗證提示會要求使用者名稱和密碼。

當驗證提示出現在對話方塊時，使用者可以編輯指定的使用者名稱。
不過，當提示出現在命令列時，使用者無法變更使用者名稱。 當您在共用的函式或指令碼中使用此參數時，請考慮所有可能的呈現方式。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Management.Automation.PSCredential

`Get-Credential` 傳回 credential 物件。

## 注意

您可以使用 **PSCredential** `Get-Credential` 在 Cmdlet 中建立並要求使用者驗證的 PSCredential 物件，例如具有 **Credential** 參數的使用者驗證。

根據預設，驗證提示會出現在對話方塊中。 若要在命令列顯示驗證提示，請將 **ConsolePrompting** 登錄專案新增 (`HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting`) ，並將其值設定為 **True** 。
如果 **ConsolePrompting** 登錄項目不存在，或其值為 False，驗證提示會出現在對話方塊。 如需指示，請參閱範例。

**ConsolePrompting** 登錄專案適用于 PowerShell 主控台，但無法在所有主機程式中運作。

例如，在 (ISE) 的 PowerShell 整合式腳本環境中，它不會有任何作用。 如需 **ConsolePrompting** 登錄項目效果的相關資訊，請參閱主機程式的說明主題。

使用 PowerShell 安裝的所有提供者都不支援 **Credential** 參數。
從 PowerShell 3.0 開始，選取的 Cmdlet （例如和 Cmdlet）支援此 `Get-Content` 功能 `New-PSDrive` 。

## 相關連結

[PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
