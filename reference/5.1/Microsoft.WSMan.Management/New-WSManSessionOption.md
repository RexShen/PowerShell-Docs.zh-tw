---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: f32b9300fddcf9086bc670912931001557b91cd8
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208667"
---
# New-WSManSessionOption

## 概要
建立會話選項雜湊表，作為 WS-Management Cmdlet 的輸入參數使用。

## SYNTAX

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## DESCRIPTION
**New-wsmansessionoption** 指令 Cmdlet 會建立可傳遞到 wsman Cmdlet 的 wsman 會話選項雜湊表：

- Get-WSManInstance
- Set-WSManInstance
- Invoke-WSManAction
- Connect-WSMan

## 範例

### 範例1：建立使用連接選項的連接

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

此範例會使用 **new-wsmansessionoption** 定義的連接選項，建立與遠端 server01 電腦的連線。

第一個命令會使用 **New-WSManSessionOption** 將一組連線設定選項儲存到 $a 變數中。
在此案例中，工作階段選項會設定 30 秒 (30,000 毫秒) 的連線逾時。

第二個命令會使用 *SessionOption* 參數，將儲存在 $a 變數中的認證傳遞至 **連接-WSMan** 。
然後， **連接-WSMan** 使用指定的會話選項連線到遠端 server01 電腦。

**連接-wsman** 通常用於 wsman 提供者的內容中，以連接到遠端電腦，在此案例中為 server01 電腦。
不過，您可以使用該 Cmdlet 來建立與遠端電腦的連線，再變更為 WSMan 提供者。
那些連線會出現在 **ComputerName** 清單中。

## PARAMETERS

### -NoEncryption
表示連接不會針對透過 HTTP 的遠端作業使用加密。

依預設，不會啟用未加密的流量。
它必須在本機設定中啟用。

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

### -OperationTimeout
指定 WS-Management 操作的超時時間（以毫秒為單位）。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType
指定尋找 Proxy 伺服器的機制。
此參數可接受的值為：

- ProxyIEConfig.
針對目前使用者使用 Internet Explorer proxy 設定。
- ProxyWinHttpConfig.
WSMan 用戶端使用 ProxyCfg.exe 公用程式，使用針對 WinHTTP 設定的 proxy 設定。
- ProxyAutoDetect.
強制自動偵測 proxy 伺服器。
- ProxyNoProxyServer.
不使用 Proxy 伺服器：
在本機解析所有主機名稱。

預設值為 ProxyIEConfig。

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication
指定要在 Proxy 使用的驗證方法。
此參數可接受的值為：

- 基本。
Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。
- 摘要。
Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。
- Negotiate。
Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。
範例包括 Kerberos 通訊協定與 NTLM。

預設值為 Negotiate。

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential
指定有權透過中繼 Web proxy 取得存取權的使用者帳戶。

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

### -SPNPort
指定要附加至遠端伺服器 (SPN) 之連接服務主體名稱的埠號碼。
當驗證機制是 Kerberos 或 Negotiate 時，會使用 SPN。

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

### -SkipCACheck
指定當它透過 HTTPS 連線時，用戶端並不會驗證伺服器憑證是否由信任的憑證授權單位單位 (CA) 簽署。
只有當遠端電腦受其他方法信任時才使用此選項，例如，如果遠端電腦屬於實體安全且隔離的網路，或在 WS-Management 設定中將遠端電腦列為受信任的主機。

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

### -SkipCNCheck
指定伺服器的憑證一般名稱 (CN) 不需要與伺服器的主機名稱相符。
此選項只用於使用 HTTPS 的遠端操作。
此選項只應該用於信任的電腦。

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

### -SkipRevocationCheck
表示連接不會驗證伺服器憑證的撤銷狀態。

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

### -UseUTF16
表示連接會以 UTF16 格式（而不是 UTF8 格式）編碼要求。
預設值為 UTF8 編碼。

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

## 輸出

### SessionOption

## 注意

## 相關連結

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
