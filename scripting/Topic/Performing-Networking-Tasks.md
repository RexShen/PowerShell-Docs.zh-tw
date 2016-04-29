---
title: 執行網路工作
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
---
# 執行網路工作
由於 TCP/IP 是最常使用的網路通訊協定，因此大多數低階網路通訊協定管理工作都涉及 TCP/IP。 在本節中，我們使用 Windows PowerShell 和 WMI 來執行這些工作。

### 列出電腦的 IP 位址
若要取得本機電腦上所有使用中的 IP 位址，請使用下列命令︰

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Format-Table -Property IPAddress
```

此命令的輸出與大多數屬性清單不同，因為值會以大括弧括住︰

<pre>IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}</pre>

若要了解為何會出現大括弧，請使用 Get-Member Cmdlet 來查看 **IPAddress** 屬性︰

<pre>PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Get-Member -Name IPAddress
TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapter
設定
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}</pre>

每個網路介面卡的 IPAddress 屬性其實是一個陣列。 定義中的大括弧表示 **IPAddress** 不是 **System.String** 值，而是 **System.String** 值的陣列。

### 列出 IP 設定資料
若要顯示每個網路介面卡的詳細 IP 設定資料，請使用下列命令︰

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName .
```

網路介面卡設定物件的預設顯示是一組經過縮減的的可用資訊。 如需深入檢查和疑難排解，請使用 Select-Object 或格式化 Cmdlet (例如 Format-List) 指定要顯示的屬性。

如果您對新式 TCP/IP 網路中可能會有的 IPX 或 WINS 屬性不感興趣，您可以使用 Select-Object 的 ExcludeProperty 參數隱藏名稱開頭為 "WINS" 或 "IPX" 的屬性：

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

此命令會傳回有關 DHCP、DNS、路由和其他次要 IP 設定屬性的詳細資訊。

### 對電腦執行 Ping
您可以使用 **Win32_PingStatus**，對電腦執行簡單的 Ping。 下列命令會執行 Ping，但傳回冗長的輸出：

```
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

下列命令會產生更實用的摘要資訊格式，顯示 Address、ResponseTime 和 StatusCode 屬性。 Format-Table 的 Autosize 參數可調整資料表資料行的大小，以在 Windows PowerShell 中正確顯示。

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
A status code of 0 indicates a successful ping.
```

您可以使用陣列，透過單一命令對多部電腦執行 Ping。 因為有多個位址，所以會使用 **ForEach-Object** 分別對每個位址執行 Ping︰

```
"127.0.0.1","localhost","research.microsoft.com" | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

您可以使用相同的命令格式，對子網路上的所有電腦執行 Ping，例如使用網路編號 192.168.1.0 的私人網路和標準類別 C 子網路遮罩 (255.255.255.0)。只有 192.168.1.1 到 192.168.1.254 範圍內的位址是合法的本機位址 (0 一律會保留給網路編號，而 255 是子網路廣播位址)。

若要表示 Windows PowerShell 中從 1 到 254 的數值陣列，請使用陳述式 **1..254**。 您可以藉由產生陣列，再將值新增至 Ping 陳述式中的部分位址，來執行完整的子網路 Ping︰

```
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

請注意，您也可以在其他地方使用產生位址範圍的這項技術。 如此一來，您可以產生一組完整的位址︰

`$ips = 1..254 | ForEach-Object -Process {"192.168.1." + $_}`

### 擷取網路介面卡內容
稍早在本使用者指南中，我們曾提及您可以使用 **Win32_NetworkAdapterConfiguration** 擷取一般設定屬性。 雖然這並不完全是 TCP/IP 資訊，但 MAC 位址和介面卡類型等網路介面卡資訊對於了解電腦上所發生的情況還是很有用。 若要取得這項資訊的摘要，請使用下列命令︰

```
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### 將 DNS 網域指派給網路介面卡
若要將 DNS 網域指派給自動名稱解析，請使用 **Win32_NetworkAdapterConfiguration SetDNSDomain** 方法。 因為您會針對每個網路介面卡設定獨立指派 DNS 網域，所以需要使用 **ForEach-Object** 陳述式將網域指派給每個介面卡：

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain("fabrikam.com") }
```

需要篩選陳述式 "IPEnabled=true"，因為即使在只使用 TCP/IP 的網路上，電腦上還是有幾個網路介面卡設定不是真正的 TCP/IP 介面卡；它們是支援所有介面卡之 RAS、PPTP、QoS 及其他服務的一般軟體項目，因此沒有自己的位址。

您可以使用 **Where-Object** Cmdlet (而不是使用 **Get-WmiObject** 篩選器) 來篩選命令。

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain("fabrikam.com")}
```

### 執行 DHCP 設定工作
修改 DHCP 詳細資料與 DNS 設定一樣，都需要使用一組網路介面卡。 您可以使用 WMI 執行幾個不同的動作，我們將逐步介紹其中一些常見的動作。

#### 判斷已啟用 DHCP 的介面卡
若要在電腦上尋找已啟用 DHCP 的介面卡，請使用下列命令︰

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName .
```

若要排除有 IP 設定問題的介面卡，您可以擷取只啟用 IP 的介面卡︰

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName .
```

#### 擷取 DHCP 內容
因為介面卡的 DHCP 相關內容通常會以 "DHCP" 為開頭，所以您可以使用 Format-Table 的 Property 參數只僅顯示這些內容︰

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName . | Format-Table -Property DHCP*
```

#### 在每個介面卡上啟用 DHCP
若要在所有介面卡上啟用 DHCP，請使用下列命令︰

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

您可以使用 **Filter** 陳述式 "IPEnabled=true and DHCPEnabled=false" 避免在已啟用 DHCP 的情況下再次啟用，但省略此步驟並不會造成錯誤。

#### 釋出和更新特定介面卡上的 DHCP 租用
**Win32_NetworkAdapterConfiguration** 類別具有 **ReleaseDHCPLease** 和 **RenewDHCPLease** 方法。 兩者使用方式皆相同。 在一般情況下，只有在需要釋出或更新特定子網路上介面卡的位址時，才會使用這些方法。 在子網路上篩選介面卡的最簡單方式，是只選擇使用該子網路閘道的介面卡設定。 例如，下列命令會釋出本機電腦上從 192.168.1.254 取得 DHCP 租用之介面卡上的所有 DHCP 租用︰

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

更新 DHCP 租用的唯一變更是使用 **RenewDHCPLease** 方法，而不是 **ReleaseDHCPLease** 方法：

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> 在遠端電腦上使用這些方法時，請注意，如果透過已釋出或更新租用的介面卡連線到遠端系統，可能無法存取遠端系統。

#### 釋出和更新所有介面卡上的 DHCP 租用
您可以使用 **Win32_NetworkAdapterConfiguration** 方法 **ReleaseDHCPLeaseAll** 和 **RenewDHCPLeaseAll**，在所有介面卡上執行全域 DHCP 位址釋出或更新。 不過，此命令必須套用至 WMI 類別，而不是特定介面卡，因為全域釋出和更新租用會在類別上執行，而不是在特定介面卡上執行。

您可以列出所有 WMI 類別，然後依名稱只選取所需的類別，來取得 WMI 類別的參考，而不是類別執行個體。 例如，下列命令會傳回 Win32_NetworkAdapterConfiguration 類別︰

```
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"}
```

您可以將整個命令視為類別，然後對其叫用 **ReleaseDHCPAdapterLease** 方法。 在下列命令中，括住 **Get-WmiObject** 和 **Where-Object** 管線項目的括弧會指示 Windows PowerShell 先對其進行評估︰

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).ReleaseDHCPLeaseAll()
```

您可以使用相同的命令格式來叫用 **RenewDHCPLeaseAll** 方法︰

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).RenewDHCPLeaseAll()
```

### 建立網路共用
若要建立網路共用，請使用 **Win32_Share Create** 方法︰

```
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Win32_Share"}).Create("C:\temp","TempShare",0,25,"test share of the temp folder")
```

您也可以在 Windows PowerShell 中使用 **net share** 建立共用︰

```
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### 移除網路共用
您可以使用 **Win32_Share** 移除網路共用，但此處理程序與建立共用稍微不同，因為您必須擷取要移除的特定共用，而不是 **Win32_Share** 類別。 下列陳述式會刪除共用 "TempShare"：

```
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

您也可以使用 **Net share**︰

```
PS> net share tempshare /delete
tempshare was deleted successfully.
```

### 連線到可存取的 Windows 網路磁碟機
**New-PSDrive** Cmdlet 會建立 Windows PowerShell 磁碟機，但以此方式建立的磁碟機僅適用於 Windows PowerShell。 若要建立新的網路磁碟機，您可以使用 **WScript.Network** COM 物件。 下列命令會將共用 \\FPS01\users 對應至本機磁碟機 B：

```
(New-Object -ComObject WScript.Network).MapNetworkDrive("B:", "\\FPS01\users")
```

您也可以使用 **net use**︰

```
net use B: \\FPS01\users
```

以 **WScript.Network** 或 net use 對應的磁碟機可立即供 Windows PowerShell 使用。



<!--HONumber=Apr16_HO1-->


