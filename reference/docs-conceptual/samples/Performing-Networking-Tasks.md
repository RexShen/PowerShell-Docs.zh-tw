---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 執行網路工作
ms.openlocfilehash: e0aa3b8ef3d911ab0fe851f6621d70e1265c5bd4
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737197"
---
# <a name="performing-networking-tasks"></a>執行網路工作

由於 TCP/IP 是最常使用的網路通訊協定，因此大多數低階網路通訊協定管理工作都涉及 TCP/IP。 在此節中，我們會使用 PowerShell 和 WMI 來執行這些工作。

## <a name="listing-ip-addresses-for-a-computer"></a>列出電腦的 IP 位址

若要取得本機電腦上所有使用中的 IP 位址，請使用下列命令︰

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

此命令的輸出與大多數屬性清單不同，因為值會以大括弧括住︰

```Output
10.0.0.1
fe80::60ea:29a7:a233:7cb7
2601:600:a27f:a470:f532:6451:5630:ec8b
2601:600:a27f:a470:e167:477d:6c5c:342d
2601:600:a27f:a470:b021:7f0d:eab9:6299
2601:600:a27f:a470:a40e:ebce:1a8c:a2f3
2601:600:a27f:a470:613c:12a2:e0e0:bd89
2601:600:a27f:a470:444f:17ec:b463:7edd
2601:600:a27f:a470:10fd:7063:28e9:c9f3
2601:600:a27f:a470:60ea:29a7:a233:7cb7
2601:600:a27f:a470::2ec1
```

若要了解為何會出現大括弧，請使用 `Get-Member`Cmdlet 來查看 **IPAddress** 屬性︰

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Get-Member -Name IPAddress
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_NetworkAdapterConfiguration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   string[] IPAddress {get;}
```

每個網路介面卡的 IPAddress 屬性其實是一個陣列。 定義中的大括弧表示 **IPAddress** 不是 **System.String** 值，而是 **System.String** 值的陣列。

## <a name="listing-ip-configuration-data"></a>列出 IP 設定資料

若要顯示每個網路介面卡的詳細 IP 設定資料，請使用下列命令︰

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

網路介面卡設定物件的預設顯示是一組經過縮減的的可用資訊。 如需深入檢查和疑難排解，請使用 `Select-Object` 或格式設定 Cmdlet (例如 `Format-List`) 來指定要顯示的屬性。

在新式 TCP/IP 網路中，您可能對 IPX 或 WINS 屬性不感興趣。 您可以使用 `Select-Object` 的 **ExcludeProperty** 參數來隱藏名稱開頭為 "WINS" 或 "IPX" 的屬性。

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

此命令會傳回有關 DHCP、DNS、路由和其他次要 IP 設定屬性的詳細資訊。

## <a name="pinging-computers"></a>對電腦執行 Ping

您可以使用 **Win32_PingStatus**，對電腦執行簡單的 Ping。 下列命令會執行 Ping，但傳回冗長的輸出：

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

下列命令會產生更實用的摘要資訊格式，顯示 Address、ResponseTime 和 StatusCode 屬性。 `Format-Table` 的 **Autosize** 參數可調整資料表資料行的大小，以在 PowerShell 中正確顯示。

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

StatusCode 為 0 表示成功執行 Ping。

您可以使用陣列，透過單一命令對多部電腦執行 Ping。 因為有多個位址，所以請使用 `ForEach-Object` 來分別 Ping 每個位址︰

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

您可以使用相同的命令格式，對子網路上的所有電腦執行 Ping，例如使用網路編號 192.168.1.0 的私人網路和標準類別 C 子網路遮罩 (255.255.255.0)。只有 192.168.1.1 到 192.168.1.254 範圍內的位址是合法的本機位址 (0 一律會保留給網路編號，而 255 是子網路廣播位址)。

若要以 PowerShell 表示 1 到 254 的數字陣列，請使用 **1..254** 陳述式。
您可以藉由產生陣列，再將值新增至 Ping 陳述式中的部分位址，來執行完整的子網路 Ping︰

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

請注意，您也可以在其他地方使用產生位址範圍的這項技術。 如此一來，您可以產生一組完整的位址︰

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>擷取網路介面卡內容

稍早，我們曾提及您可以使用 **Win32_NetworkAdapterConfiguration** 類別來擷取一般設定屬性。 雖然這並不完全是 TCP/IP 資訊，但 MAC 位址和介面卡類型等網路介面卡資訊對於了解電腦上所發生的情況還是很有用。 若要取得這項資訊的摘要，請使用下列命令︰

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>將 DNS 網域指派給網路介面卡

若要指派 DNS 網域來進行自動名稱解析，請使用 **Win32_NetworkAdapterConfiguration** 的 **SetDNSDomain** 方法。 由於您會為每個網路介面卡設定獨立指派 DNS 網域，因此需要使用 `ForEach-Object` 陳述式將網域指派給每個介面卡：

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

`IPEnabled=$true` 篩選陳述式是必要的，因為即使在只使用 TCP/IP 的網路上，電腦上還是有數個網路介面卡設定不是真正的 TCP/IP 介面卡；它們是支援所有介面卡之 RAS、PPTP、QoS 及其他服務的一般軟體元素，因此沒有自己的位址。

您可以使用 `Where-Object` Cmdlet (而不是使用 `Get-CimInstance` 篩選條件) 來篩選命令。

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>執行 DHCP 設定工作

修改 DHCP 詳細資料與 DNS 設定一樣，都需要使用一組網路介面卡。 您可以使用 WMI 執行幾個不同的動作，我們將逐步介紹其中一些常見的動作。

### <a name="determining-dhcp-enabled-adapters"></a>判斷已啟用 DHCP 的介面卡

若要在電腦上尋找已啟用 DHCP 的介面卡，請使用下列命令︰

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

若要排除有 IP 設定問題的介面卡，您可以擷取只啟用 IP 的介面卡︰

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a>擷取 DHCP 內容

由於介面卡的 DHCP 相關屬性通常會以 `DHCP` 為開頭，因此您可以使用 `Format-Table` 的 Property 參數來只僅顯示這些屬性︰

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>在每個介面卡上啟用 DHCP

若要在所有介面卡上啟用 DHCP，請使用下列命令︰

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

您可以使用 **Filter** 陳述式 `IPEnabled=$true and DHCPEnabled=$false` 來避免在已啟用 DHCP 的情況下再次啟用，但省略此步驟並不會造成錯誤。

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>釋出和更新特定介面卡上的 DHCP 租用

**Win32_NetworkAdapterConfiguration** 類別具有 **ReleaseDHCPLease** 和 **RenewDHCPLease** 方法。 兩者使用方式皆相同。 在一般情況下，只有在需要釋出或更新特定子網路上介面卡的位址時，才會使用這些方法。 在子網路上篩選介面卡的最簡單方式，是只選擇使用該子網路閘道的介面卡設定。 例如，下列命令會釋出本機電腦上從 192.168.1.254 取得 DHCP 租用之介面卡上的所有 DHCP 租用︰

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

更新 DHCP 租用的唯一變更是使用 **RenewDHCPLease** 方法，而不是 **ReleaseDHCPLease** 方法：

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> 在遠端電腦上使用這些方法時，請注意，如果透過已釋出或更新租用的介面卡連線到遠端系統，可能無法存取遠端系統。

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>釋出和更新所有介面卡上的 DHCP 租用

您可以使用 **Win32_NetworkAdapterConfiguration** 方法 (**ReleaseDHCPLeaseAll** 和 **RenewDHCPLeaseAll**)，在所有介面卡上執行全域 DHCP 位址釋出或更新。
不過，此命令必須套用至 WMI 類別，而不是特定介面卡，因為全域釋出和更新租用會在類別上執行，而不是在特定介面卡上執行。

您可以列出所有 WMI 類別，然後依名稱只選取所需的類別，來取得 WMI 類別的參考，而不是類別執行個體。 例如，下列命令會傳回 **Win32_NetworkAdapterConfiguration** 類別︰

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

您可以將整個命令視為類別，然後對其叫用 **ReleaseDHCPAdapterLease** 方法。 在下列命令中，括住 `Get-CimInstance` 和 `Where-Object` 管線元素的括弧會指示 PowerShell 先對它們進行評估︰

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

您可以使用相同的命令格式來叫用 **RenewDHCPLeaseAll** 方法︰

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>建立網路共用

若要建立網路共用，請使用 **Win32_Share** 的 **Create** 方法︰

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

您也可以在 Windows 上的 PowerShell 中使用 `net share` 來建立共用︰

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>移除網路共用

您可以使用 **Win32_Share** 移除網路共用，但此處理程序與建立共用稍微不同，因為您必須擷取要移除的特定共用，而不是 **Win32_Share** 類別。 下列陳述式會刪除 **TempShare** 共用：

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

在 Windows 中，`net share` 也可發揮相同作用︰

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>連線到可存取的 Windows 網路磁碟機

`New-PSDrive` Cmdlet 會建立 PowerShell 磁碟機，但以此方式建立的磁碟機僅可供 PowerShell 使用。 若要建立新的網路磁碟機，您可以使用 **WScript.Network** COM 物件。 下列命令會將 `\\FPS01\users` 共用對應至本機磁碟機 `B:`。

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

在 Windows 上，`net use` 命令也可發揮相同作用：

```powershell
net use B: \\FPS01\users
```

以 **WScript.Network** 或 `net use` 對應的磁碟機可立即供 PowerShell 使用。
