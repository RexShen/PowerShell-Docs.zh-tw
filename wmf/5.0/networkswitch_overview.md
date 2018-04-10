---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 2b6b81d250c3d745f3ab21ebadb9a657583638b0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="ffe30-102">使用 PowerShell 管理網路交換器</span><span class="sxs-lookup"><span data-stu-id="ffe30-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="ffe30-103">**Get-NetworkSwitchEthernetPort** Cmdlet 現在會藉執行個體傳回下列其他資訊︰</span><span class="sxs-lookup"><span data-stu-id="ffe30-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="ffe30-104">IPAddress – 與連接埠相關聯的 IP 位址</span><span class="sxs-lookup"><span data-stu-id="ffe30-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="ffe30-105">PortMode – 連接埠模式︰存取、路由或主幹</span><span class="sxs-lookup"><span data-stu-id="ffe30-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="ffe30-106">AccessVLAN – 在存取模式中與這個連接埠相關聯的 VLAN 識別碼</span><span class="sxs-lookup"><span data-stu-id="ffe30-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="ffe30-107">TrunkedVLANList – 在主幹模式中與這個連接埠相關聯的VLAN 識別碼清單</span><span class="sxs-lookup"><span data-stu-id="ffe30-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="ffe30-108">使用 Windows PowerShell 管理基本的網路交換器</span><span class="sxs-lookup"><span data-stu-id="ffe30-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="ffe30-109">網路交換器 Cmdlet，在 WMF 5.0 中引進，可讓您將交換器、虛擬 LAN (VLAN) 和基本層級 2 網路交換器連接埠設定套用至 Windows Server 2012 R2 標誌認證的網路交換器。</span><span class="sxs-lookup"><span data-stu-id="ffe30-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="ffe30-110">Microsoft 努力不懈地支援[資料中心抽象](http://technet.microsoft.com/cloud/dal.aspx)層 (DAL) 的願景，並為我們的客戶和合作夥伴展現這個領域的價值。</span><span class="sxs-lookup"><span data-stu-id="ffe30-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="ffe30-111">使用這些 Cmdlet 可以執行︰</span><span class="sxs-lookup"><span data-stu-id="ffe30-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="ffe30-112">全域交換器設定，例如︰</span><span class="sxs-lookup"><span data-stu-id="ffe30-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="ffe30-113">設定主機名稱</span><span class="sxs-lookup"><span data-stu-id="ffe30-113">Set host name</span></span>
    - <span data-ttu-id="ffe30-114">設定參數橫幅</span><span class="sxs-lookup"><span data-stu-id="ffe30-114">Set switch banner</span></span>
    - <span data-ttu-id="ffe30-115">保存設定</span><span class="sxs-lookup"><span data-stu-id="ffe30-115">Persist configuration</span></span>
    - <span data-ttu-id="ffe30-116">啟用或停用功能</span><span class="sxs-lookup"><span data-stu-id="ffe30-116">Enable or disable feature</span></span>

- <span data-ttu-id="ffe30-117">VLAN 設定：</span><span class="sxs-lookup"><span data-stu-id="ffe30-117">VLAN configuration:</span></span>
    - <span data-ttu-id="ffe30-118">建立或移除 VLAN</span><span class="sxs-lookup"><span data-stu-id="ffe30-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="ffe30-119">啟用或停用 VLAN</span><span class="sxs-lookup"><span data-stu-id="ffe30-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="ffe30-120">列舉 VLAN</span><span class="sxs-lookup"><span data-stu-id="ffe30-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="ffe30-121">設定易記的 VLAN 名稱</span><span class="sxs-lookup"><span data-stu-id="ffe30-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="ffe30-122">階層 2 連接埠設定：</span><span class="sxs-lookup"><span data-stu-id="ffe30-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="ffe30-123">列舉連接埠</span><span class="sxs-lookup"><span data-stu-id="ffe30-123">Enumerate ports</span></span>
    - <span data-ttu-id="ffe30-124">啟用或停用連接埠</span><span class="sxs-lookup"><span data-stu-id="ffe30-124">Enable or disable ports</span></span>
    - <span data-ttu-id="ffe30-125">設定連接埠模式和屬性</span><span class="sxs-lookup"><span data-stu-id="ffe30-125">Set port modes and properties</span></span>
    - <span data-ttu-id="ffe30-126">將 VLAN 加入連接埠的主幹或存取或建立關聯性</span><span class="sxs-lookup"><span data-stu-id="ffe30-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="ffe30-127">探索就從尋找所有 NetworkSwitch Cmdlet 開始！</span><span class="sxs-lookup"><span data-stu-id="ffe30-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="ffe30-128">詳細資訊請參閱 Jeffrey Snover 的 WMF 5.0 Preview 公告部落格文章：<http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="ffe30-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>