---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 08e01b73e7e44ca6fc80920e4a2dfe8856ba317f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205195"
---
# New-CimSessionOption

## 概要
指定 New-CimSession Cmdlet 的 advanced 選項。

## SYNTAX

### ProtocolTypeSet (預設) 

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### WSManParameterSet

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### DcomParameterSet

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## DESCRIPTION

此 `New-CimSessionOption` Cmdlet 會建立 CIM 會話選項物件的實例。 您可以使用 CIM 會話選項物件作為 Cmdlet 的輸入， `New-CimSession` 以指定 cim 會話的選項。

這個 Cmdlet 有兩個參數集，一個用於 WsMan 選項，另一個用於分散式元件物件模型 (DCOM) 選項。 根據您使用的參數，Cmdlet 會傳回 DCOM 會話選項的實例，或傳回 WsMan 會話選項。

## 範例

### 範例1：建立 DCOM 的 CIM 會話選項物件

這個範例會建立 DCOM 通訊協定的 CIM 會話選項物件，並將它儲存在名為的變數中 `$so` 。 然後將變數的內容傳遞給 `New-CimSession` Cmdlet。
`New-CimSession` 然後使用變數中定義的選項，以名為 Server01 的遠端伺服器建立新的 CIM 會話。

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### 範例2：建立 WsMan 的 CIM 會話選項物件

這個範例會建立 WsMan 通訊協定的 CIM 會話選項物件。 物件包含 **ProxyAuthentication** 參數所指定之 **Kerberos** 驗證模式的設定、由 **ProxyCredential** 參數指定的認證，並指定命令要略過 CA 檢查、略過 CN 檢查，然後使用 SSL。

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### 範例3：建立已指定文化特性的 CIM 會話選項物件

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

此範例會指定用於 CIM 會話的文化特性。 依預設，在執行作業時，會使用用戶端的文化特性。 不過，您可以使用 **culture** 參數覆寫預設文化特性。

## PARAMETERS

### -Culture

指定要用於 CIM 會話的使用者介面文化特性。 使用下列其中一種格式來指定此參數的值：

- 格式的文化特性名稱， `<languagecode2>-<country/regioncode2>` 例如 "en-us"。
- 包含 **CultureInfo** 物件的變數。
- 取得 **CultureInfo** 物件的命令，例如 [Get 文化](../Microsoft.PowerShell.Utility/Get-Culture.md)特性

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EncodePortInServicePrincipalName

表示 Kerberos 連接正在連接到服務主體名稱 (SPN 的服務) 包含服務埠號碼。 這種類型的連接並不常見。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

指定用於 WsMan 通訊協定的編碼方式。 此參數可接受的值為： **預設** 值、 **Utf8** 或 **Utf16** 。

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -HttpPrefix

指定電腦名稱稱和埠號碼後面的 HTTP URL 部分。 變更這種情況並不常見。 根據預設，此參數的值為 **/wsman** 。

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Impersonation

使用模擬建立 Windows Management Instrumentation (WMI) 的 DCOM 會話。

這個參數的有效值為：

- 預設： DCOM 可以選擇使用其一般安全性協調演算法的模擬等級。
- 無：用戶端對伺服器是匿名的。 伺服器進程可以模擬用戶端，但模擬權杖不包含任何資訊，也無法使用。
- 識別：允許物件查詢呼叫端的認證。
- 模擬：允許物件使用呼叫端的認證。
- Delegate：允許物件允許其他物件使用呼叫端的認證。

如果 **未** 指定模擬，Cmdlet 會 `New-CimSession` 使用模擬的值。 **Impersonate**

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxEnvelopeSizeKB

指定任一方向的 WsMan XML 訊息大小限制。

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoEncryption

指定關閉資料加密。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketIntegrity

指定建立至 WMI 的 DCOM 會話使用元件物件模型 (COM) _PacketIntegrity_ 功能。 根據預設，所有使用 DCOM 建立的 CIM 會話都會將 **PacketIntegrity** 參數設定為 **True** 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketPrivacy

使用 COM _PacketPrivacy_ 建立對 WMI 的 DCOM 會話。 根據預設，所有使用 DCOM 建立的 CIM 會話都會將 **PacketPrivacy** 參數設定為 **true** 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

指定要使用的通訊協定。 此參數可接受的值為： **DCOM** 、 **Default** 或 **Wsman** 。

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyAuthentication

指定用於 proxy 解析的驗證方法。 此參數可接受的值包括： **Default** 、 **Digest** 、 **Negotiate** 、 **Basic** 、 **Kerberos** 、 **NtlmDomain** 或 **CredSsp** 。

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCertificateThumbprint

指定用於 proxy 驗證的使用者帳戶 (x.509) 數位公開金鑰憑證。
請輸入憑證的憑證指紋。 憑證將用於用戶端憑證式驗證。 這些帳戶只能對應至本機使用者帳戶，而且無法使用網域帳戶。

若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell Cert：磁片磁碟機中的或 Cmdlet。

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

指定要用於 Proxy 驗證的認證。 輸入下列其中一項：

- 包含 PSCredential 物件的變數。
- 可取得 PSCredential 物件的命令，例如 `Get-Credential`

如果未設定此選項，則您不能指定任何認證。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyType

指定要使用的主機名稱解析機制。 此參數可接受的值為： **None** 、 **WinHttp** 、 **Auto** 或 **microsoft-windows-ie-internetexplorer** 。

此參數的預設值為 **microsoft-windows-ie-internetexplorer** 。

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCACheck

指出透過 HTTPS 連線時，用戶端不會驗證伺服器憑證是否由受信任的憑證授權單位單位 (CA) 簽署。

只有當遠端電腦是使用另一種機制來信任時，例如當遠端電腦屬於實體安全且隔離的網路時，或當遠端電腦在 WinRM 設定中列為受信任的主機時，才使用此參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCNCheck

指出伺服器的憑證一般名稱 (CN) 不需要符合伺服器的主機名稱。 此參數僅適用于使用 HTTPS 通訊協定的受信任電腦的遠端操作。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipRevocationCheck

指出已略過伺服器憑證的撤銷檢查。 此參數僅適用于受信任的電腦。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UICulture

指定要用於 CIM 會話的使用者介面文化特性。 使用下列其中一種格式來指定此參數的值：

- 格式的文化特性名稱， `<languagecode2>-<country/regioncode2>` 例如 "en-us"。
- 包含 CultureInfo 物件的變數。
- 取得 CultureInfo 物件的命令，例如 `Get-Culture` 。

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseSsl

指出應該使用 SSL 來建立與遠端電腦的連線。 預設不會使用 SSL。 WsMan 會加密透過網路傳輸的所有內容，即使是在使用 HTTP 時也一樣。

此參數可讓您指定 HTTPS （而非 HTTP）的額外保護。 如果用於連線的埠上無法使用 SSL，且您指定此參數，則命令會失敗。

建議您只有在未指定 **PacketPrivacy** 參數時，才使用此參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

此 Cmdlet 不接受任何輸入物件。

## 輸出

### CIMSessionOption

這個 Cmdlet 會傳回包含 CIM 會話選項資訊的物件。

## 注意

## 相關連結

[Get-ChildItem](../microsoft.powershell.management/get-childitem.md)

[Get-Credential](../microsoft.powershell.security/get-credential.md)

[Get-Culture](../microsoft.powershell.utility/get-culture.md)

[Get-Item](../microsoft.powershell.management/get-item.md)

[New-CimSession](New-CimSession.md)

