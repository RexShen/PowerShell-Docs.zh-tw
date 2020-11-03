---
description: WSMan
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: WSMan 提供者
ms.openlocfilehash: 011383112d453a4fa88745c69b52e432709aa9d3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206800"
---
# <a name="wsman-provider"></a>WSMan 提供者

## <a name="provider-name"></a>提供者名稱

WSMan

## <a name="drives"></a>磁碟機

`WSMan:`

## <a name="short-description"></a>簡短描述

提供存取適用於管理的 Web 服務 (WS-Management) 設定資訊。

## <a name="detailed-description"></a>詳細描述

適用于 PowerShell 的 **WSMan** 提供者可讓您在本機或遠端電腦上新增、變更、清除和刪除 WS-Management 設定資料。

**WSMan** 提供者會公開 PowerShell 磁片磁碟機，其目錄結構對應于 WS-Management 設定的邏輯群組。 這些群組稱為容器。

從 Windows PowerShell 3.0 開始， **WSMan** 提供者已更新，可支援會話設定的新屬性，例如 **OutputBufferingMode** 。 會話設定會顯示為磁片磁碟機外掛程式目錄中的專案 `WSMan:` ，而這些屬性會在每個會話設定中顯示為專案。

**WSMan** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> 您可以使用磁片磁碟機中的命令 `WSMan:` 來變更新屬性的值。 不過，您無法使用 `WSMan:` PowerShell 2.0 中的磁片磁碟機來變更 Windows PowerShell 3.0 中引進的屬性。
> 雖然不會產生任何錯誤，但命令對於變更這些設定並不有效，請使用 Windows PowerShell 3.0 中的 **WSMan** 磁片磁碟機。

### <a name="organization-of-the-wsman-drive"></a>WSMan：磁片磁碟機的組織

- **用戶端** ：您可以設定 WS-Management 用戶端的各種層面。 設定資訊是儲存在登錄中。

- **服務** ：您可以設定 WS-Management 服務的各種層面。
  設定資訊是儲存在登錄中。
  > [!NOTE]
  > 服務設定有時稱為「伺服器設定」。

- **Shell** ：您可以設定 WS-Management Shell 的各個層面，例如允許遠端 Shell 存取的設定 ( **AllowRemoteShellAccess** ) 以及 ( **MaxConcurrentUsers** ) 允許的並行使用者數目上限。

- 接聽 **程式：您** 可以建立及設定接聽程式。 接聽程式是一種管理服務，可實作 WS-Management 通訊協定來傳送及接收訊息。

- **外掛程式** ： WS-Management 服務載入和使用外掛程式，以提供各種功能。 PowerShell 預設會提供三個外掛程式：
  - 事件轉送外掛程式。
  - Microsoft PowerShell 外掛程式。
  - Windows Management Instrumentation (WMI) 提供者外掛程式。
  這三個外掛程式支援事件轉送、設定和 WMI 存取。

- **ClientCertificate** ：您可以建立並設定用戶端憑證。
  將 WS-Management 用戶端設定為使用憑證驗證時，會使用用戶端憑證。

### <a name="directory-hierarchy-of-the-wsman-provider"></a>WSMan 提供者的目錄階層

本機電腦的 WSMan 提供者目錄階層如下所示。

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

遠端電腦的 WSMan 提供者目錄階層和本機電腦的目錄階層相同。 不過，若要存取遠端電腦的組態設定，您需要使用 [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan) 連線到遠端電腦。 一旦連線到遠端電腦之後，遠端電腦的名稱就會顯示於提供者中。

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a>流覽 WSMan：磁片磁碟機

此命令會使用 `Set-Location` Cmdlet 將目前的位置變更為 `WSMan:` 磁片磁碟機。

```powershell
Set-Location WSMan:
```

若要返回檔案系統磁碟機，請輸入磁碟機名稱。 例如，輸入。

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a>流覽至遠端系統存放區位置

此命令會使用 `Set-Location` 命令將目前的位置變更為遠端系統存放區位置中的根位置。 使用反斜線 `\` 或正斜線 `/` 來指出磁片磁碟機的層級 `WSMan:` 。

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> 上述命令假設遠端系統的連線已經存在。

## <a name="displaying-the-contents-of-the-wsman-drive"></a>顯示 WSMan：磁片磁碟機的內容

此命令會使用 `Get-Childitem` Cmdlet 來顯示 Localhost 存放區位置中的 WS-Management 存放區。

```powershell
Get-ChildItem -path WSMan:\Localhost
```

如果您是在 `WSMan:` 磁片磁碟機中，您可以省略磁片磁碟機名稱。

此命令會使用 `Get-Childitem` Cmdlet 來顯示遠端電腦 "SERVER01" 存放區位置中的 WS-Management 存放區。

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> 上述命令假設遠端系統的連線已經存在。

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a>設定 WSMAN：磁片磁碟機中的專案值

您可以使用 `Set-Item` Cmdlet 來變更磁片磁碟機中的設定 `WSMAN` 。 下列範例會將 **TrustedHosts** 值設定為接受尾碼為 "contoso.com" 的所有主機。

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

此 `Set-Item` Cmdlet 支援附加值的額外參數 `-Concatenate` ，而不是變更它。 下列範例會將新值 "*. domain2.com" 附加至儲存在中的舊值 `TrustedHost:`

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a>在 WSMAN：磁片磁碟機中建立專案

### <a name="creating-a-new-listener"></a>建立新的接聽程式

`New-Item`Cmdlet 會在提供者磁片磁碟機中建立專案。 每個提供者都有您可以建立的不同專案類型。 在 `WSMAN:` 磁片磁碟機中，您可以建立接聽程式，並設定接聽 *程式以* 接收和回應遠端要求。 下列命令會使用 Cmdlet 建立新的 HTTP 接聽程式 `New-Item` 。

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a>建立新外掛程式

此命令會建立適用於 WS-Management 服務的 (暫存器) 外掛程式。

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a>建立新的資源專案

此命令會在 TestPlugin 的 Resources 目錄中建立資源專案。 此命令假設已使用個別命令建立 TestPlugin。

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a>建立資源的新安全性專案

此命令會在 Resource_5967683 (特定資源) 的 [安全性] 目錄中建立安全性項目。 此命令假設已使用個別命令建立資源專案。

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a>建立新的用戶端憑證

此命令會建立 WS-Management 用戶端可以使用的 **ClientCertificate** 專案。 新的 **ClientCertificate** 會在 **ClientCertificate** 目錄下顯示為 "ClientCertificate_1234567890"。 所有的參數都是必要項。 **簽發者必須是簽發者** 憑證的指紋。

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a>建立新的初始化參數

此命令會在 "InitializationParameters" 目錄中建立名為 "testparametername" 的初始化參數。 此命令假設已使用個別的命令來建立 "TestPlugin"。

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a>動態參數

動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。

### <a name="address-string"></a>Address \<String\>

指定為其建立此接聽程式的位址。 這個值可以是下列值之一：

- 常值字串 "*"。  (萬用字元字元 (`*`) 讓命令系結所有網路介面卡上的所有 IP 位址。 ) 
- 常值字串 "IP："，後面接著 IPv4 以點分隔的十進位格式或 IPv6 複製的十六進位格式的有效 IP 位址。
- 常值字串 "MAC："，後面接著介面卡的 MAC 位址。
  例如： MAC： 32-a3-58-90-cc。

> [!NOTE]
> Address 值是在建立接聽程式時建立的。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a>Capability \<Enumeration\>

使用 *外掛程式* 時，此參數會指定此統一資源識別項 (URI) 所支援的作業。 您必須針對 URI 支援的每個操作類型建立一個項目。 如果作業支援指定的作業，您可以指定任何有效的屬性。

這些屬性包含 **SupportsFiltering** 和 **SupportsFragment** 。

- **Create** ： URI 上支援建立作業。
  - 如果建立作業支援這個概念，就會使用 **SupportFragment**  屬性。
  - **SupportFiltering** 屬性對 Create 作業無效，應設定為 "False"。
  > [!NOTE]
  > 如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。
- **Delete** ： URI 支援刪除作業。
  - 如果刪除作業支援這個概念，就會使用 **SupportFragment** 屬性。
  - **SupportFiltering** 屬性對刪除作業而言無效，應設定為 "False"。
  > [!NOTE]
  > 如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。
- **列舉** ： URI 支援列舉作業。
  - 列舉作業不支援 **SupportFragment** 屬性，應設定為 False。
  - **SupportFiltering** 屬性是有效的，而且如果外掛程式支援篩選，這個屬性應該設定為 "True"。
  > [!NOTE]
  > 如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。
- **Get** ： URI 支援 get 作業。
  - 如果 Get 作業支援這個概念，就會使用 **SupportFragment** 屬性。
  - **SupportFiltering** 屬性對 Get 作業無效，應設定為 "False"。
  > [!NOTE]
  > 如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。
- **Invoke** ： URI 支援 invoke 作業。
  - Invoke 作業不支援 **SupportFragment** 屬性，應設定為 False。
  - **SupportFiltering** 屬性無效，應設定為 "False"。
  > [!NOTE]
  > 如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。
- **Put** ： URI 支援 put 作業。
  - 如果 Put 作業支援這個概念，就會使用 **SupportFragment** 屬性。
  - **SupportFiltering** 屬性對 Put 作業無效，應設定為 "False"。
  > [!NOTE]
  > 如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。
- **訂閱** ： URI 支援訂閱作業。
  - 訂閱作業不支援 **SupportFragment** 屬性，應設定為 False。
  - **SupportFiltering** 屬性對訂閱作業而言無效，應設定為 "False"。
  > [!NOTE]
  > 如果同時支援 Shell 操作，則這個操作對 URI 而言是無效的。
- **Shell** ： URI 支援 shell 作業。
  - Shell 作業不支援 **SupportFragment** 屬性，應設定為 "False"。
  - **SupportFiltering** 屬性對 Shell 作業無效，應設定為 "False"。
  > [!NOTE]
  > 如果也支援任何其他作業，則這項作業對 URI 而言是不正確。
  > [!NOTE]
  > 如果已針對 URI 設定 Shell 操作，則會在 WS-Management (WinRM) 服務內部處理 Get、Put、Create、Delete、Invoke 及 Enumerate 操作來管理殼層。 因此，外掛程式無法處理這些操作。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a>CertificateThumbprint \<String\>

指定服務憑證的指紋。

這個值表示憑證 [指紋] 欄位中兩位數十六進位值的字串。 它會為有權執行此動作的使用者帳戶指定數位公開金鑰憑證 (X509)。 憑證將用於用戶端憑證式驗證。 它們只能對應到本機使用者帳戶，無法用於網域帳戶。 若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell 磁片磁碟機中的或 Cmdlet `Cert:` 。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a>Enabled \<Boolean\>

指定接聽程式已啟用或停用。 預設值為 True。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a>FileName (Plugin) \<String\>

指定作業外掛程式的檔案名。 當收到要求時，將會在使用者的內容中展開任何放置於此專案中的環境變數。 由於每個使用者可能會有不同版本的相同環境變數，因此每個使用者可能會有不同的外掛程式。 這個專案不能空白，且必須指向有效的外掛程式。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a>HostName \<String\>

指定 WS-Management (WinRM) 服務執行所在之電腦的主機名稱。

值必須是完整網域名稱、IPv4 或 IPv6 常值字串，或是萬用字元。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a>Issuer \<String\>

指定簽發憑證的憑證授權單位名稱。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a>外掛程式 \<\> WS-Management 外掛程式是 (dll 的原生動態連結程式庫) 

這會插入並擴充 WS-Management 的功能。 WSW-Management 外掛程式 API 提供的功能，可讓使用者藉由針對支援的資源 Uri 和作業來執行某些 Api 來寫入外掛程式。 針對 WS-Management (WinRM) 服務或 Internet Information Services (IIS) 設定外掛程式之後，就會分別在 WS-Management 主機或 IIS 主機上載入外掛程式。 系統會將遠端要求路由傳送到這些外掛程式的進入點來執行操作。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a>Port \<Unsigned Short Integer\>

指定為其建立此接聽程式的 TCP 連接埠。 您可以指定 1 到 65535 之間的任何值。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

指定代表不同類型的管理操作或值的端點。 服務會公開一或多個資源，而有些資源可具有一個以上的執行個體。 管理資源類似 WMI 類別或資料庫資料表，而執行個體類似類別的執行個體或資料表中的資料列。 例如， **Win32_LogicalDisk** 類別代表資源。 `Win32_LogicalDisk="C:\\"` 是資源的特定實例。

統一資源識別項 (URI) 包含資源的前置詞與路徑。
例如：

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

指定統一資源識別項 (URI) 來識別電腦上特定類型的資源，例如，磁碟或處理程序。

URI 是由前置詞與資源路徑所組成。 例如：

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a>SDKVersion \<String\>

指定 SDK 中 WS-Management 外掛程式的版本。 唯一有效的值是
1.

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a>Subject \<String\>

指定由憑證識別的實體。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a>Transport \<String\>

指定要用來傳送和接收 WS-Management 通訊協定的要求和回應的傳輸。 值必須是 HTTP 或 HTTPS。

注意：建立接聽程式時，會設定傳輸值。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a>URI \<String\>

識別要根據 Sddl 參數值授權存取的 URI。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a>URLPrefix \<String\>

要接受 HTTP 或 HTTPS 要求的 URL 首碼。 這是一個字串，其中只包含字元 `[a-z]` 、 `[A-Z]` 、 `[9-0]` 、底線 (`_`) 和反斜線 (`/`) 。 字串不能以反斜線開頭或結尾， (`/`) 。 例如，如果電腦名稱稱為 "SampleComputer"，WS-Management 用戶端會 `http://SampleMachine/URLPrefix` 在目的地位址中指定。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a>Value \<String\>

指定初始化參數的值，這是用來指定設定選項的外掛程式特定值。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a>XMLRenderingType \<String\>

指定透過 **WSMAN_DATA** 物件將 XML 傳遞至外掛程式的格式。 以下是有效值：

- Text：傳入的 XML 資料會包含在 **WSMAN_DATA_TYPE_TEXT** 結構中，這表示 xml 做為 **PCWSTR** 記憶體緩衝區。
- XMLReader：內送 XML 資料包含在 **WSMAN_DATA_TYPE_WS_XML_READER** 結構中，它會將 xml 表示為 **XmlReader** 物件，該物件定義于 "WebServices .h" 標頭檔中。

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>使用管線

提供者 Cmdlet 接受管線輸入。 您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。
若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。

## <a name="getting-help"></a>取得說明

從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。

若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 的參數來指定檔案系統磁片磁碟機。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a>另請參閱

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)
