---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 執行網路工作
ms.openlocfilehash: e581296b4b7609b374f206c447c4f797e3e2c400
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030869"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="a08e5-103">執行網路工作</span><span class="sxs-lookup"><span data-stu-id="a08e5-103">Performing Networking Tasks</span></span>

<span data-ttu-id="a08e5-104">由於 TCP/IP 是最常使用的網路通訊協定，因此大多數低階網路通訊協定管理工作都涉及 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="a08e5-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="a08e5-105">在本節中，我們使用 Windows PowerShell 和 WMI 來執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="a08e5-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="a08e5-106">列出電腦的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="a08e5-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="a08e5-107">若要取得本機電腦上所有使用中的 IP 位址，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="a08e5-108">此命令的輸出與大多數屬性清單不同，因為值會以大括弧括住︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="a08e5-109">若要了解為何會出現大括弧，請使用 Get-Member Cmdlet 來檢查 **IPAddress** 屬性︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="a08e5-110">每個網路介面卡的 IPAddress 屬性其實是一個陣列。</span><span class="sxs-lookup"><span data-stu-id="a08e5-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="a08e5-111">定義中的大括弧表示 **IPAddress** 不是 **System.String** 值，而是 **System.String** 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="a08e5-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="a08e5-112">列出 IP 設定資料</span><span class="sxs-lookup"><span data-stu-id="a08e5-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="a08e5-113">若要顯示每個網路介面卡的詳細 IP 設定資料，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="a08e5-114">網路介面卡設定物件的預設顯示是一組經過縮減的的可用資訊。</span><span class="sxs-lookup"><span data-stu-id="a08e5-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="a08e5-115">如需深入檢查和疑難排解，請使用 Select-Object 或格式化 Cmdlet (例如 Format-List) 指定要顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="a08e5-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="a08e5-116">如果您對新式 TCP/IP 網路中可能會有的 IPX 或 WINS 屬性不感興趣，您可以使用 Select-Object 的 ExcludeProperty 參數隱藏名稱開頭為 "WINS" 或 "IPX" 的屬性：</span><span class="sxs-lookup"><span data-stu-id="a08e5-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="a08e5-117">此命令會傳回有關 DHCP、DNS、路由和其他次要 IP 設定屬性的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a08e5-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="a08e5-118">對電腦執行 Ping</span><span class="sxs-lookup"><span data-stu-id="a08e5-118">Pinging Computers</span></span>

<span data-ttu-id="a08e5-119">您可以使用 **Win32_PingStatus**，對電腦執行簡單的 Ping。</span><span class="sxs-lookup"><span data-stu-id="a08e5-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="a08e5-120">下列命令會執行 Ping，但傳回冗長的輸出：</span><span class="sxs-lookup"><span data-stu-id="a08e5-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="a08e5-121">下列命令會產生更實用的摘要資訊格式，顯示 Address、ResponseTime 和 StatusCode 屬性。</span><span class="sxs-lookup"><span data-stu-id="a08e5-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="a08e5-122">Format-Table 的 Autosize 參數可調整資料表資料行的大小，以在 Windows PowerShell 中正確顯示。</span><span class="sxs-lookup"><span data-stu-id="a08e5-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="a08e5-123">StatusCode 為 0 表示成功執行 Ping。</span><span class="sxs-lookup"><span data-stu-id="a08e5-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="a08e5-124">您可以使用陣列，透過單一命令對多部電腦執行 Ping。</span><span class="sxs-lookup"><span data-stu-id="a08e5-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="a08e5-125">因為有多個位址，所以請使用 **ForEach-Object** 分別對每個位址執行 Ping︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="a08e5-126">您可以使用相同的命令格式，對子網路上的所有電腦執行 Ping，例如使用網路編號 192.168.1.0 的私人網路和標準類別 C 子網路遮罩 (255.255.255.0)。只有 192.168.1.1 到 192.168.1.254 範圍內的位址是合法的本機位址 (0 一律會保留給網路編號，而 255 是子網路廣播位址)。</span><span class="sxs-lookup"><span data-stu-id="a08e5-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="a08e5-127">若要表示 Windows PowerShell 中從 1 到 254 的數值陣列，請使用陳述式 **1..254**。</span><span class="sxs-lookup"><span data-stu-id="a08e5-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="a08e5-128">您可以藉由產生陣列，再將值新增至 Ping 陳述式中的部分位址，來執行完整的子網路 Ping︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="a08e5-129">請注意，您也可以在其他地方使用產生位址範圍的這項技術。</span><span class="sxs-lookup"><span data-stu-id="a08e5-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="a08e5-130">如此一來，您可以產生一組完整的位址︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="a08e5-131">擷取網路介面卡內容</span><span class="sxs-lookup"><span data-stu-id="a08e5-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="a08e5-132">稍早在本使用者指南中，我們曾提及您可以使用 **Win32_NetworkAdapterConfiguration** 擷取一般設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a08e5-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="a08e5-133">雖然這並不完全是 TCP/IP 資訊，但 MAC 位址和介面卡類型等網路介面卡資訊對於了解電腦上所發生的情況還是很有用。</span><span class="sxs-lookup"><span data-stu-id="a08e5-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="a08e5-134">若要取得這項資訊的摘要，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="a08e5-135">將 DNS 網域指派給網路介面卡</span><span class="sxs-lookup"><span data-stu-id="a08e5-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="a08e5-136">若要將 DNS 網域指派給自動名稱解析，請使用 **Win32_NetworkAdapterConfiguration SetDNSDomain** 方法。</span><span class="sxs-lookup"><span data-stu-id="a08e5-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="a08e5-137">因為您會針對每個網路介面卡設定獨立指派 DNS 網域，所以需要使用 **ForEach-Object** 陳述式將網域指派給每個介面卡：</span><span class="sxs-lookup"><span data-stu-id="a08e5-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="a08e5-138">需要篩選陳述式 "IPEnabled=$true"，因為即使在只使用 TCP/IP 的網路上，電腦上還是有幾個網路介面卡設定不是真正的 TCP/IP 介面卡；它們是支援所有介面卡之 RAS、PPTP、QoS 及其他服務的一般軟體項目，因此沒有自己的位址。</span><span class="sxs-lookup"><span data-stu-id="a08e5-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="a08e5-139">您可以使用 **Where-Object** Cmdlet (而不是使用 **Get-WmiObject** 篩選器) 來篩選命令。</span><span class="sxs-lookup"><span data-stu-id="a08e5-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="a08e5-140">執行 DHCP 設定工作</span><span class="sxs-lookup"><span data-stu-id="a08e5-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="a08e5-141">修改 DHCP 詳細資料與 DNS 設定一樣，都需要使用一組網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="a08e5-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="a08e5-142">您可以使用 WMI 執行幾個不同的動作，我們將逐步介紹其中一些常見的動作。</span><span class="sxs-lookup"><span data-stu-id="a08e5-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="a08e5-143">判斷已啟用 DHCP 的介面卡</span><span class="sxs-lookup"><span data-stu-id="a08e5-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="a08e5-144">若要在電腦上尋找已啟用 DHCP 的介面卡，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="a08e5-145">若要排除有 IP 設定問題的介面卡，您可以擷取只啟用 IP 的介面卡︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="a08e5-146">擷取 DHCP 內容</span><span class="sxs-lookup"><span data-stu-id="a08e5-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="a08e5-147">因為介面卡的 DHCP 相關內容通常會以 "DHCP" 為開頭，所以您可以使用 Format-Table 的 Property 參數只僅顯示這些內容︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="a08e5-148">在每個介面卡上啟用 DHCP</span><span class="sxs-lookup"><span data-stu-id="a08e5-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="a08e5-149">若要在所有介面卡上啟用 DHCP，請使用下列命令︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="a08e5-150">您可以使用 **Filter** 陳述式 "IPEnabled=true and DHCPEnabled=false" 避免在已啟用 DHCP 的情況下再次啟用，但省略此步驟並不會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="a08e5-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="a08e5-151">釋出和更新特定介面卡上的 DHCP 租用</span><span class="sxs-lookup"><span data-stu-id="a08e5-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="a08e5-152">**Win32_NetworkAdapterConfiguration** 類別具有 **ReleaseDHCPLease** 和 **RenewDHCPLease** 方法。</span><span class="sxs-lookup"><span data-stu-id="a08e5-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="a08e5-153">兩者使用方式皆相同。</span><span class="sxs-lookup"><span data-stu-id="a08e5-153">Both are used in the same way.</span></span> <span data-ttu-id="a08e5-154">在一般情況下，只有在需要釋出或更新特定子網路上介面卡的位址時，才會使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="a08e5-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="a08e5-155">在子網路上篩選介面卡的最簡單方式，是只選擇使用該子網路閘道的介面卡設定。</span><span class="sxs-lookup"><span data-stu-id="a08e5-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="a08e5-156">例如，下列命令會釋出本機電腦上從 192.168.1.254 取得 DHCP 租用之介面卡上的所有 DHCP 租用︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="a08e5-157">更新 DHCP 租用的唯一變更是使用 **RenewDHCPLease** 方法，而不是 **ReleaseDHCPLease** 方法：</span><span class="sxs-lookup"><span data-stu-id="a08e5-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="a08e5-158">在遠端電腦上使用這些方法時，請注意，如果透過已釋出或更新租用的介面卡連線到遠端系統，可能無法存取遠端系統。</span><span class="sxs-lookup"><span data-stu-id="a08e5-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="a08e5-159">釋出和更新所有介面卡上的 DHCP 租用</span><span class="sxs-lookup"><span data-stu-id="a08e5-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="a08e5-160">您可以使用 **Win32_NetworkAdapterConfiguration** 方法 (**ReleaseDHCPLeaseAll** 和 **RenewDHCPLeaseAll**)，在所有介面卡上執行全域 DHCP 位址釋出或更新。</span><span class="sxs-lookup"><span data-stu-id="a08e5-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="a08e5-161">不過，此命令必須套用至 WMI 類別，而不是特定介面卡，因為全域釋出和更新租用會在類別上執行，而不是在特定介面卡上執行。</span><span class="sxs-lookup"><span data-stu-id="a08e5-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="a08e5-162">您可以列出所有 WMI 類別，然後依名稱只選取所需的類別，來取得 WMI 類別的參考，而不是類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="a08e5-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="a08e5-163">例如，下列命令會傳回 Win32_NetworkAdapterConfiguration 類別︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="a08e5-164">您可以將整個命令視為類別，然後對其叫用 **ReleaseDHCPAdapterLease** 方法。</span><span class="sxs-lookup"><span data-stu-id="a08e5-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="a08e5-165">在下列命令中，括住 **Get-WmiObject** 和 **Where-Object** 管線項目的括弧會指示 Windows PowerShell 先對其進行評估︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="a08e5-166">您可以使用相同的命令格式來叫用 **RenewDHCPLeaseAll** 方法︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="a08e5-167">建立網路共用</span><span class="sxs-lookup"><span data-stu-id="a08e5-167">Creating a Network Share</span></span>

<span data-ttu-id="a08e5-168">若要建立網路共用，請使用 **Win32_Share Create** 方法︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="a08e5-169">您也可以在 Windows PowerShell 中使用 **net share** 建立共用︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="a08e5-170">移除網路共用</span><span class="sxs-lookup"><span data-stu-id="a08e5-170">Removing a Network Share</span></span>

<span data-ttu-id="a08e5-171">您可以使用 **Win32_Share** 移除網路共用，但此處理程序與建立共用稍微不同，因為您必須擷取要移除的特定共用，而不是 **Win32_Share** 類別。</span><span class="sxs-lookup"><span data-stu-id="a08e5-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="a08e5-172">下列陳述式會刪除共用 "TempShare"：</span><span class="sxs-lookup"><span data-stu-id="a08e5-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="a08e5-173">您也可以使用 **Net share**︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="a08e5-174">連線到可存取的 Windows 網路磁碟機</span><span class="sxs-lookup"><span data-stu-id="a08e5-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="a08e5-175">**New-PSDrive** Cmdlet 會建立 Windows PowerShell 磁碟機，但以此方式建立的磁碟機僅適用於 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a08e5-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="a08e5-176">若要建立新的網路磁碟機，您可以使用 **WScript.Network** COM 物件。</span><span class="sxs-lookup"><span data-stu-id="a08e5-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="a08e5-177">下列命令會將共用的 \\\\FPS01\\users 對應至本機磁碟機 B：</span><span class="sxs-lookup"><span data-stu-id="a08e5-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="a08e5-178">您也可以使用 **net use**︰</span><span class="sxs-lookup"><span data-stu-id="a08e5-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="a08e5-179">以 **WScript.Network** 或 net use 對應的磁碟機可立即供 Windows PowerShell 使用。</span><span class="sxs-lookup"><span data-stu-id="a08e5-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>
