---
title: "網路交換器管理員 Cmdlet 失敗"
contributor: vaibch
ms.openlocfilehash: 8495d79aec54d93f94e745e2efccb5116ad5d944
ms.sourcegitcommit: a3966253a165d193a42b43b9430a4dc76988f82f
ms.translationtype: HT
ms.contentlocale: zh-TW
---
<span data-ttu-id="1403a-102">網路交換器管理員 Cmdlet 可用來透過 WSMAN 管理網路交換器。</span><span class="sxs-lookup"><span data-stu-id="1403a-102">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="1403a-103">此模組的數個 Cmdlet 都能接受來自管線的值。</span><span class="sxs-lookup"><span data-stu-id="1403a-103">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="1403a-104">在 WMF 5.1 Preview 中，當值未透過管線傳遞時，可接受來自管線之值的 Cmdlet 即無法執行。</span><span class="sxs-lookup"><span data-stu-id="1403a-104">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="1403a-105">若未使用 "InputObject" 參數，Cmdlet 應可繼續執行而不會失敗。</span><span class="sxs-lookup"><span data-stu-id="1403a-105">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="1403a-106">以下是受影響的 Cmdlet 清單，意即這些 Cmdlet 可接受來自管線的 "InputObject" 參數值。</span><span class="sxs-lookup"><span data-stu-id="1403a-106">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="1403a-107">若此值未透過管線傳遞，Cmdlet 便會執行失敗。</span><span class="sxs-lookup"><span data-stu-id="1403a-107">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="1403a-108">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="1403a-108">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="1403a-109">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="1403a-109">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="1403a-110">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="1403a-110">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="1403a-111">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="1403a-111">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="1403a-112">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="1403a-112">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="1403a-113">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="1403a-113">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="1403a-114">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="1403a-114">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="1403a-115">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="1403a-115">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="1403a-116">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="1403a-116">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="1403a-117">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="1403a-117">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="1403a-118">解決方法</span><span class="sxs-lookup"><span data-stu-id="1403a-118">Resolution</span></span>
<span data-ttu-id="1403a-119">當 InputObject 參數值透過管線傳遞其中時，Cmdlet 即會正常執行。</span><span class="sxs-lookup"><span data-stu-id="1403a-119">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="1403a-120">適用於上述 Cmdlet 的範例包括︰</span><span class="sxs-lookup"><span data-stu-id="1403a-120">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="1403a-121">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="1403a-121">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="1403a-122">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="1403a-122">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="1403a-123">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="1403a-123">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="1403a-124">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="1403a-124">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="1403a-125">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="1403a-125">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="1403a-126">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="1403a-126">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="1403a-127">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="1403a-127">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="1403a-128">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="1403a-128">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
