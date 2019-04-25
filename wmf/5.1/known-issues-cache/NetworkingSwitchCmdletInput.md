---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.topic: conceptual
contributor: vaibch
title: 網路交換器管理員 Cmdlet 失敗
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084975"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="bc6a5-103">網路交換器管理員 Cmdlet 失敗</span><span class="sxs-lookup"><span data-stu-id="bc6a5-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="bc6a5-104">網路交換器管理員 Cmdlet 可用來透過 WSMAN 管理網路交換器。</span><span class="sxs-lookup"><span data-stu-id="bc6a5-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="bc6a5-105">此模組的數個 Cmdlet 都能接受來自管線的值。</span><span class="sxs-lookup"><span data-stu-id="bc6a5-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="bc6a5-106">在 WMF 5.1 Preview 中，當值未透過管線傳遞時，可接受來自管線之值的 Cmdlet 即無法執行。</span><span class="sxs-lookup"><span data-stu-id="bc6a5-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="bc6a5-107">若未使用 "InputObject" 參數，Cmdlet 應可繼續執行而不會失敗。</span><span class="sxs-lookup"><span data-stu-id="bc6a5-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="bc6a5-108">以下是受影響的 Cmdlet 清單，意即這些 Cmdlet 可接受來自管線的 "InputObject" 參數值。</span><span class="sxs-lookup"><span data-stu-id="bc6a5-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="bc6a5-109">若此值未透過管線傳遞，Cmdlet 便會執行失敗。</span><span class="sxs-lookup"><span data-stu-id="bc6a5-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="bc6a5-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="bc6a5-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="bc6a5-111">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="bc6a5-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="bc6a5-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="bc6a5-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="bc6a5-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="bc6a5-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="bc6a5-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="bc6a5-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="bc6a5-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="bc6a5-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="bc6a5-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="bc6a5-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="bc6a5-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="bc6a5-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="bc6a5-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="bc6a5-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="bc6a5-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="bc6a5-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="bc6a5-120">解決方法</span><span class="sxs-lookup"><span data-stu-id="bc6a5-120">Resolution</span></span>

<span data-ttu-id="bc6a5-121">當 InputObject 參數值透過管線傳遞其中時，Cmdlet 即會正常執行。</span><span class="sxs-lookup"><span data-stu-id="bc6a5-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="bc6a5-122">適用於上述 Cmdlet 的範例包括︰</span><span class="sxs-lookup"><span data-stu-id="bc6a5-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```