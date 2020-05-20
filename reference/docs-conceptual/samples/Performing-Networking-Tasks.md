---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 執行網路工作
ms.openlocfilehash: e0aa3b8ef3d911ab0fe851f6621d70e1265c5bd4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737197"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="2fca6-103">執行網路工作</span><span class="sxs-lookup"><span data-stu-id="2fca6-103">Performing Networking Tasks</span></span>

<span data-ttu-id="2fca6-104">由於 TCP/IP 是最常使用的網路通訊協定，因此大多數低階網路通訊協定管理工作都涉及 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="2fca6-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="2fca6-105">在此節中，我們會使用 PowerShell 和 WMI 來執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="2fca6-105">In this section, we use PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="2fca6-106">列出電腦的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="2fca6-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="2fca6-107">若要取得本機電腦上所有使用中的 IP 位址，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

<span data-ttu-id="2fca6-108">此命令的輸出與大多數屬性清單不同，因為值會以大括弧括住︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

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

<span data-ttu-id="2fca6-109">若要了解為何會出現大括弧，請使用 `Get-Member`Cmdlet 來查看 **IPAddress** 屬性︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-109">To understand why the braces appear, use the `Get-Member` cmdlet to examine the **IPAddress** property:</span></span>

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

<span data-ttu-id="2fca6-110">每個網路介面卡的 IPAddress 屬性其實是一個陣列。</span><span class="sxs-lookup"><span data-stu-id="2fca6-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="2fca6-111">定義中的大括弧表示 **IPAddress** 不是 **System.String** 值，而是 **System.String** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="2fca6-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="2fca6-112">列出 IP 設定資料</span><span class="sxs-lookup"><span data-stu-id="2fca6-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="2fca6-113">若要顯示每個網路介面卡的詳細 IP 設定資料，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

<span data-ttu-id="2fca6-114">網路介面卡設定物件的預設顯示是一組經過縮減的的可用資訊。</span><span class="sxs-lookup"><span data-stu-id="2fca6-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="2fca6-115">如需深入檢查和疑難排解，請使用 `Select-Object` 或格式設定 Cmdlet (例如 `Format-List`) 來指定要顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="2fca6-115">For in-depth inspection and troubleshooting, use `Select-Object` or a formatting cmdlet, such as `Format-List`, to specify the properties to be displayed.</span></span>

<span data-ttu-id="2fca6-116">在新式 TCP/IP 網路中，您可能對 IPX 或 WINS 屬性不感興趣。</span><span class="sxs-lookup"><span data-stu-id="2fca6-116">In modern TCP/IP networks you are probably not interested in IPX or WINS properties.</span></span> <span data-ttu-id="2fca6-117">您可以使用 `Select-Object` 的 **ExcludeProperty** 參數來隱藏名稱開頭為 "WINS" 或 "IPX" 的屬性。</span><span class="sxs-lookup"><span data-stu-id="2fca6-117">You can use the **ExcludeProperty** parameter of `Select-Object` to hide properties with names that begin with "WINS" or "IPX".</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="2fca6-118">此命令會傳回有關 DHCP、DNS、路由和其他次要 IP 設定屬性的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2fca6-118">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="2fca6-119">對電腦執行 Ping</span><span class="sxs-lookup"><span data-stu-id="2fca6-119">Pinging Computers</span></span>

<span data-ttu-id="2fca6-120">您可以使用 **Win32_PingStatus**，對電腦執行簡單的 Ping。</span><span class="sxs-lookup"><span data-stu-id="2fca6-120">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="2fca6-121">下列命令會執行 Ping，但傳回冗長的輸出：</span><span class="sxs-lookup"><span data-stu-id="2fca6-121">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

<span data-ttu-id="2fca6-122">下列命令會產生更實用的摘要資訊格式，顯示 Address、ResponseTime 和 StatusCode 屬性。</span><span class="sxs-lookup"><span data-stu-id="2fca6-122">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="2fca6-123">`Format-Table` 的 **Autosize** 參數可調整資料表資料行的大小，以在 PowerShell 中正確顯示。</span><span class="sxs-lookup"><span data-stu-id="2fca6-123">The **Autosize** parameter of `Format-Table` resizes the table columns so that they display properly in PowerShell.</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="2fca6-124">StatusCode 為 0 表示成功執行 Ping。</span><span class="sxs-lookup"><span data-stu-id="2fca6-124">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="2fca6-125">您可以使用陣列，透過單一命令對多部電腦執行 Ping。</span><span class="sxs-lookup"><span data-stu-id="2fca6-125">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="2fca6-126">因為有多個位址，所以請使用 `ForEach-Object` 來分別 Ping 每個位址︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-126">Because there is more than one address, use the `ForEach-Object` to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

<span data-ttu-id="2fca6-127">您可以使用相同的命令格式，對子網路上的所有電腦執行 Ping，例如使用網路編號 192.168.1.0 的私人網路和標準類別 C 子網路遮罩 (255.255.255.0)。只有 192.168.1.1 到 192.168.1.254 範圍內的位址是合法的本機位址 (0 一律會保留給網路編號，而 255 是子網路廣播位址)。</span><span class="sxs-lookup"><span data-stu-id="2fca6-127">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="2fca6-128">若要以 PowerShell 表示 1 到 254 的數字陣列，請使用 **1..254** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2fca6-128">To represent an array of the numbers from 1 through 254 in PowerShell, use the statement **1..254.**</span></span>
<span data-ttu-id="2fca6-129">您可以藉由產生陣列，再將值新增至 Ping 陳述式中的部分位址，來執行完整的子網路 Ping︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-129">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="2fca6-130">請注意，您也可以在其他地方使用產生位址範圍的這項技術。</span><span class="sxs-lookup"><span data-stu-id="2fca6-130">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="2fca6-131">如此一來，您可以產生一組完整的位址︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-131">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="2fca6-132">擷取網路介面卡內容</span><span class="sxs-lookup"><span data-stu-id="2fca6-132">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="2fca6-133">稍早，我們曾提及您可以使用 **Win32_NetworkAdapterConfiguration** 類別來擷取一般設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2fca6-133">Earlier, we mentioned that you could retrieve general configuration properties using the **Win32_NetworkAdapterConfiguration** class.</span></span> <span data-ttu-id="2fca6-134">雖然這並不完全是 TCP/IP 資訊，但 MAC 位址和介面卡類型等網路介面卡資訊對於了解電腦上所發生的情況還是很有用。</span><span class="sxs-lookup"><span data-stu-id="2fca6-134">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="2fca6-135">若要取得這項資訊的摘要，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-135">To get a summary of this information, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="2fca6-136">將 DNS 網域指派給網路介面卡</span><span class="sxs-lookup"><span data-stu-id="2fca6-136">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="2fca6-137">若要指派 DNS 網域來進行自動名稱解析，請使用 **Win32_NetworkAdapterConfiguration** 的 **SetDNSDomain** 方法。</span><span class="sxs-lookup"><span data-stu-id="2fca6-137">To assign the DNS domain for automatic name resolution, use the **SetDNSDomain** method of the **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="2fca6-138">由於您會為每個網路介面卡設定獨立指派 DNS 網域，因此需要使用 `ForEach-Object` 陳述式將網域指派給每個介面卡：</span><span class="sxs-lookup"><span data-stu-id="2fca6-138">Because you assign the DNS domain for each network adapter configuration independently, you need to use a `ForEach-Object` statement to assign the domain to each adapter:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="2fca6-139">`IPEnabled=$true` 篩選陳述式是必要的，因為即使在只使用 TCP/IP 的網路上，電腦上還是有數個網路介面卡設定不是真正的 TCP/IP 介面卡；它們是支援所有介面卡之 RAS、PPTP、QoS 及其他服務的一般軟體元素，因此沒有自己的位址。</span><span class="sxs-lookup"><span data-stu-id="2fca6-139">The filtering statement `IPEnabled=$true` is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="2fca6-140">您可以使用 `Where-Object` Cmdlet (而不是使用 `Get-CimInstance` 篩選條件) 來篩選命令。</span><span class="sxs-lookup"><span data-stu-id="2fca6-140">You can filter the command by using the `Where-Object` cmdlet, instead of using the `Get-CimInstance` filter.</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="2fca6-141">執行 DHCP 設定工作</span><span class="sxs-lookup"><span data-stu-id="2fca6-141">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="2fca6-142">修改 DHCP 詳細資料與 DNS 設定一樣，都需要使用一組網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="2fca6-142">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="2fca6-143">您可以使用 WMI 執行幾個不同的動作，我們將逐步介紹其中一些常見的動作。</span><span class="sxs-lookup"><span data-stu-id="2fca6-143">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="2fca6-144">判斷已啟用 DHCP 的介面卡</span><span class="sxs-lookup"><span data-stu-id="2fca6-144">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="2fca6-145">若要在電腦上尋找已啟用 DHCP 的介面卡，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-145">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

<span data-ttu-id="2fca6-146">若要排除有 IP 設定問題的介面卡，您可以擷取只啟用 IP 的介面卡︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-146">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="2fca6-147">擷取 DHCP 內容</span><span class="sxs-lookup"><span data-stu-id="2fca6-147">Retrieving DHCP Properties</span></span>

<span data-ttu-id="2fca6-148">由於介面卡的 DHCP 相關屬性通常會以 `DHCP` 為開頭，因此您可以使用 `Format-Table` 的 Property 參數來只僅顯示這些屬性︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-148">Because DHCP-related properties for an adapter generally begin with `DHCP`, you can use the Property parameter of `Format-Table` to display only those properties:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="2fca6-149">在每個介面卡上啟用 DHCP</span><span class="sxs-lookup"><span data-stu-id="2fca6-149">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="2fca6-150">若要在所有介面卡上啟用 DHCP，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-150">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="2fca6-151">您可以使用 **Filter** 陳述式 `IPEnabled=$true and DHCPEnabled=$false` 來避免在已啟用 DHCP 的情況下再次啟用，但省略此步驟並不會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="2fca6-151">You can use the **Filter** statement `IPEnabled=$true and DHCPEnabled=$false` to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="2fca6-152">釋出和更新特定介面卡上的 DHCP 租用</span><span class="sxs-lookup"><span data-stu-id="2fca6-152">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="2fca6-153">**Win32_NetworkAdapterConfiguration** 類別具有 **ReleaseDHCPLease** 和 **RenewDHCPLease** 方法。</span><span class="sxs-lookup"><span data-stu-id="2fca6-153">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="2fca6-154">兩者使用方式皆相同。</span><span class="sxs-lookup"><span data-stu-id="2fca6-154">Both are used in the same way.</span></span> <span data-ttu-id="2fca6-155">在一般情況下，只有在需要釋出或更新特定子網路上介面卡的位址時，才會使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="2fca6-155">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="2fca6-156">在子網路上篩選介面卡的最簡單方式，是只選擇使用該子網路閘道的介面卡設定。</span><span class="sxs-lookup"><span data-stu-id="2fca6-156">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="2fca6-157">例如，下列命令會釋出本機電腦上從 192.168.1.254 取得 DHCP 租用之介面卡上的所有 DHCP 租用︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-157">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="2fca6-158">更新 DHCP 租用的唯一變更是使用 **RenewDHCPLease** 方法，而不是 **ReleaseDHCPLease** 方法：</span><span class="sxs-lookup"><span data-stu-id="2fca6-158">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="2fca6-159">在遠端電腦上使用這些方法時，請注意，如果透過已釋出或更新租用的介面卡連線到遠端系統，可能無法存取遠端系統。</span><span class="sxs-lookup"><span data-stu-id="2fca6-159">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="2fca6-160">釋出和更新所有介面卡上的 DHCP 租用</span><span class="sxs-lookup"><span data-stu-id="2fca6-160">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="2fca6-161">您可以使用 **Win32_NetworkAdapterConfiguration** 方法 (**ReleaseDHCPLeaseAll** 和 **RenewDHCPLeaseAll**)，在所有介面卡上執行全域 DHCP 位址釋出或更新。</span><span class="sxs-lookup"><span data-stu-id="2fca6-161">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span>
<span data-ttu-id="2fca6-162">不過，此命令必須套用至 WMI 類別，而不是特定介面卡，因為全域釋出和更新租用會在類別上執行，而不是在特定介面卡上執行。</span><span class="sxs-lookup"><span data-stu-id="2fca6-162">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="2fca6-163">您可以列出所有 WMI 類別，然後依名稱只選取所需的類別，來取得 WMI 類別的參考，而不是類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="2fca6-163">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="2fca6-164">例如，下列命令會傳回 **Win32_NetworkAdapterConfiguration** 類別︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-164">For example, the following command returns the **Win32_NetworkAdapterConfiguration** class:</span></span>

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="2fca6-165">您可以將整個命令視為類別，然後對其叫用 **ReleaseDHCPAdapterLease** 方法。</span><span class="sxs-lookup"><span data-stu-id="2fca6-165">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="2fca6-166">在下列命令中，括住 `Get-CimInstance` 和 `Where-Object` 管線元素的括弧會指示 PowerShell 先對它們進行評估︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-166">In the following command, the parentheses surrounding the `Get-CimInstance` and `Where-Object` pipeline elements direct PowerShell to evaluate them first:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="2fca6-167">您可以使用相同的命令格式來叫用 **RenewDHCPLeaseAll** 方法︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-167">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="2fca6-168">建立網路共用</span><span class="sxs-lookup"><span data-stu-id="2fca6-168">Creating a Network Share</span></span>

<span data-ttu-id="2fca6-169">若要建立網路共用，請使用 **Win32_Share** 的 **Create** 方法︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-169">To create a network share, use the **Create** method of **Win32_Share**:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

<span data-ttu-id="2fca6-170">您也可以在 Windows 上的 PowerShell 中使用 `net share` 來建立共用︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-170">You can also create the share by using `net share` in PowerShell on Windows:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="2fca6-171">移除網路共用</span><span class="sxs-lookup"><span data-stu-id="2fca6-171">Removing a Network Share</span></span>

<span data-ttu-id="2fca6-172">您可以使用 **Win32_Share** 移除網路共用，但此處理程序與建立共用稍微不同，因為您必須擷取要移除的特定共用，而不是 **Win32_Share** 類別。</span><span class="sxs-lookup"><span data-stu-id="2fca6-172">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="2fca6-173">下列陳述式會刪除 **TempShare** 共用：</span><span class="sxs-lookup"><span data-stu-id="2fca6-173">The following statement deletes the share **TempShare**:</span></span>

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="2fca6-174">在 Windows 中，`net share` 也可發揮相同作用︰</span><span class="sxs-lookup"><span data-stu-id="2fca6-174">In Windows, `net share` works as well:</span></span>

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="2fca6-175">連線到可存取的 Windows 網路磁碟機</span><span class="sxs-lookup"><span data-stu-id="2fca6-175">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="2fca6-176">`New-PSDrive` Cmdlet 會建立 PowerShell 磁碟機，但以此方式建立的磁碟機僅可供 PowerShell 使用。</span><span class="sxs-lookup"><span data-stu-id="2fca6-176">The `New-PSDrive` cmdlets creates a PowerShell drive, but drives created this way are available only to PowerShell.</span></span> <span data-ttu-id="2fca6-177">若要建立新的網路磁碟機，您可以使用 **WScript.Network** COM 物件。</span><span class="sxs-lookup"><span data-stu-id="2fca6-177">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="2fca6-178">下列命令會將 `\\FPS01\users` 共用對應至本機磁碟機 `B:`。</span><span class="sxs-lookup"><span data-stu-id="2fca6-178">The following command maps the share `\\FPS01\users` to local drive `B:`,</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="2fca6-179">在 Windows 上，`net use` 命令也可發揮相同作用：</span><span class="sxs-lookup"><span data-stu-id="2fca6-179">On Windows, the `net use` command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="2fca6-180">以 **WScript.Network** 或 `net use` 對應的磁碟機可立即供 PowerShell 使用。</span><span class="sxs-lookup"><span data-stu-id="2fca6-180">Drives mapped with either **WScript.Network** or `net use` are immediately available to PowerShell.</span></span>
