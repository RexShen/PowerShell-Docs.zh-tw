---
title: PowerShell Core 6.1 的新功能
description: PowerShell Core 6.1 中發行的新功能與變更
ms.date: 09/13/2018
ms.openlocfilehash: 16159059285f89c2ddd85b506b0920f0aa8748ae
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90846910"
---
# <a name="whats-new-in-powershell-core-61"></a><span data-ttu-id="98e95-103">PowerShell Core 6.1 的新功能</span><span class="sxs-lookup"><span data-stu-id="98e95-103">What's New in PowerShell Core 6.1</span></span>

<span data-ttu-id="98e95-104">以下是 PowerShell Core 6.1 中已引進的一些主要新功能與變更精選。</span><span class="sxs-lookup"><span data-stu-id="98e95-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.1.</span></span>

<span data-ttu-id="98e95-105">還有**許多**「乏味的項目」讓 PowerShell 變得更快且更穩定 (外加許許多多的 Bug 修正)！</span><span class="sxs-lookup"><span data-stu-id="98e95-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span> <span data-ttu-id="98e95-106">如需變更的完整清單，請參閱 [GitHub 上的變更記錄](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)。</span><span class="sxs-lookup"><span data-stu-id="98e95-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="98e95-107">此外，除了下文所提到的一些名字，我們也感謝[所有社群參與者](https://github.com/PowerShell/PowerShell/graphs/contributors)協助實現這次的發行。</span><span class="sxs-lookup"><span data-stu-id="98e95-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="98e95-108">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="98e95-108">.NET Core 2.1</span></span>

<span data-ttu-id="98e95-109">PowerShell Core 6.1 已移至 [5 月發行](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/)的 .NET Core 2.1，並對 PowerShell 做出許多改善，包括：</span><span class="sxs-lookup"><span data-stu-id="98e95-109">PowerShell Core 6.1 moved to .NET Core 2.1 after it was [released in May](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), resulting in a number of improvements to PowerShell, including:</span></span>

- <span data-ttu-id="98e95-110">效能改善 (請參閱[下文](#performance-improvements))</span><span class="sxs-lookup"><span data-stu-id="98e95-110">performance improvements (see [below](#performance-improvements))</span></span>
- <span data-ttu-id="98e95-111">Alpine Linux 支援 (預覽)</span><span class="sxs-lookup"><span data-stu-id="98e95-111">Alpine Linux support (preview)</span></span>
- <span data-ttu-id="98e95-112">[.NET 通用工具支援](/dotnet/core/tools/global-tools) - 即將在 PowerShell 中推出</span><span class="sxs-lookup"><span data-stu-id="98e95-112">[.NET global tool support](/dotnet/core/tools/global-tools) - coming soon to PowerShell</span></span>
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a><span data-ttu-id="98e95-113">適用於 .NET Core 的 Windows 相容性套件</span><span class="sxs-lookup"><span data-stu-id="98e95-113">Windows Compatibility Pack for .NET Core</span></span>

<span data-ttu-id="98e95-114">在 Windows 上，.NET 小組提供[適用於 .NET Core 的 Windows 相容性套件](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/)，此組件集將一些已移除的 API 重新新增至 Windows 上的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="98e95-114">On Windows, the .NET team shipped the [Windows Compatibility Pack for .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), a set of assemblies that add a number of removed APIs back to .NET Core on Windows.</span></span>

<span data-ttu-id="98e95-115">我們已將 Windows 相容性套件新增至 PowerShell Core 6.1 版，讓任何使用這些 API 的模組或指令碼都可以依賴這些套件提供使用。</span><span class="sxs-lookup"><span data-stu-id="98e95-115">We've added the Windows Compatibility Pack to PowerShell Core 6.1 release so that any modules or scripts that use these APIs can rely on them being available.</span></span>

<span data-ttu-id="98e95-116">Windows 相容性組件可讓 PowerShell Core 使用**隨附於 Windows 10 2018 年 10 月更新和 Windows Server 2019 中 1900 個以上的 Cmdlet**。</span><span class="sxs-lookup"><span data-stu-id="98e95-116">The Windows Compatibility Pack enables PowerShell Core to use **more than 1900 cmdlets that ship with Windows 10 October 2018 Update and Windows Server 2019**.</span></span>

## <a name="support-for-application-allow-lists"></a><span data-ttu-id="98e95-117">支援應用程式允許清單</span><span class="sxs-lookup"><span data-stu-id="98e95-117">Support for Application allow lists</span></span>

<span data-ttu-id="98e95-118">PowerShell Core 6.1 與 Windows PowerShell 5.1 同樣支援 [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) 和 [Device Guard](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) 應用程式允許清單。</span><span class="sxs-lookup"><span data-stu-id="98e95-118">PowerShell Core 6.1 has parity with Windows PowerShell 5.1 supporting [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) and [Device Guard](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) application allow lists.</span></span> <span data-ttu-id="98e95-119">應用程式允許清單可供細微控制哪些二進位檔才能搭配使用 PowerShell [受限語言模式](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/)執行。</span><span class="sxs-lookup"><span data-stu-id="98e95-119">Application allow lists allow granular control of what binaries are allowed to be executed used with PowerShell [Constrained Language mode](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).</span></span>

## <a name="performance-improvements"></a><span data-ttu-id="98e95-120">效能改善</span><span class="sxs-lookup"><span data-stu-id="98e95-120">Performance improvements</span></span>

<span data-ttu-id="98e95-121">PowerShell Core 6.0 已做出一些重大的效能改善。</span><span class="sxs-lookup"><span data-stu-id="98e95-121">PowerShell Core 6.0 made some significant performance improvements.</span></span> <span data-ttu-id="98e95-122">PowerShell Core 6.1 將持續改善特定作業的速度。</span><span class="sxs-lookup"><span data-stu-id="98e95-122">PowerShell Core 6.1 continues to improve the speed of certain operations.</span></span>

<span data-ttu-id="98e95-123">例如，`Group-Object` 已加速 66%：</span><span class="sxs-lookup"><span data-stu-id="98e95-123">For example, `Group-Object` has been sped up by 66%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|    <span data-ttu-id="98e95-124">計量</span><span class="sxs-lookup"><span data-stu-id="98e95-124">Metric</span></span>    | <span data-ttu-id="98e95-125">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="98e95-125">Windows PowerShell 5.1</span></span> | <span data-ttu-id="98e95-126">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="98e95-126">PowerShell Core 6.0</span></span> | <span data-ttu-id="98e95-127">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="98e95-127">PowerShell Core 6.1</span></span> |
| ------------ | ---------------------- | ------------------- | ------------------- |
| <span data-ttu-id="98e95-128">時間 (秒)</span><span class="sxs-lookup"><span data-stu-id="98e95-128">Time (sec)</span></span>   | <span data-ttu-id="98e95-129">25.178</span><span class="sxs-lookup"><span data-stu-id="98e95-129">25.178</span></span>                 | <span data-ttu-id="98e95-130">19.653</span><span class="sxs-lookup"><span data-stu-id="98e95-130">19.653</span></span>              | <span data-ttu-id="98e95-131">6.641</span><span class="sxs-lookup"><span data-stu-id="98e95-131">6.641</span></span>               |
| <span data-ttu-id="98e95-132">加速 (%)</span><span class="sxs-lookup"><span data-stu-id="98e95-132">Speed-up (%)</span></span> | <span data-ttu-id="98e95-133">N/A</span><span class="sxs-lookup"><span data-stu-id="98e95-133">N/A</span></span>                    | <span data-ttu-id="98e95-134">21.9%</span><span class="sxs-lookup"><span data-stu-id="98e95-134">21.9%</span></span>               | <span data-ttu-id="98e95-135">66.2%</span><span class="sxs-lookup"><span data-stu-id="98e95-135">66.2%</span></span>               |

<span data-ttu-id="98e95-136">同樣地，類似如下的排序案例已改善超過 15%：</span><span class="sxs-lookup"><span data-stu-id="98e95-136">Similarly, sorting scenarios like this one have improved by more than 15%:</span></span>

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|    <span data-ttu-id="98e95-137">計量</span><span class="sxs-lookup"><span data-stu-id="98e95-137">Metric</span></span>    | <span data-ttu-id="98e95-138">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="98e95-138">Windows PowerShell 5.1</span></span> | <span data-ttu-id="98e95-139">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="98e95-139">PowerShell Core 6.0</span></span> | <span data-ttu-id="98e95-140">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="98e95-140">PowerShell Core 6.1</span></span> |
| ------------ | ---------------------- | ------------------- | ------------------- |
| <span data-ttu-id="98e95-141">時間 (秒)</span><span class="sxs-lookup"><span data-stu-id="98e95-141">Time (sec)</span></span>   | <span data-ttu-id="98e95-142">12.170</span><span class="sxs-lookup"><span data-stu-id="98e95-142">12.170</span></span>                 | <span data-ttu-id="98e95-143">8.493</span><span class="sxs-lookup"><span data-stu-id="98e95-143">8.493</span></span>               | <span data-ttu-id="98e95-144">7.08</span><span class="sxs-lookup"><span data-stu-id="98e95-144">7.08</span></span>                |
| <span data-ttu-id="98e95-145">加速 (%)</span><span class="sxs-lookup"><span data-stu-id="98e95-145">Speed-up (%)</span></span> | <span data-ttu-id="98e95-146">N/A</span><span class="sxs-lookup"><span data-stu-id="98e95-146">N/A</span></span>                    | <span data-ttu-id="98e95-147">30.2%</span><span class="sxs-lookup"><span data-stu-id="98e95-147">30.2%</span></span>               | <span data-ttu-id="98e95-148">16.6%</span><span class="sxs-lookup"><span data-stu-id="98e95-148">16.6%</span></span>               |

<span data-ttu-id="98e95-149">`Import-Csv` 從 Windows PowerShell 迴歸之後也已大幅加速。</span><span class="sxs-lookup"><span data-stu-id="98e95-149">`Import-Csv` has also been sped up significantly after a regression from Windows PowerShell.</span></span>
<span data-ttu-id="98e95-150">下列範例針對 26,616 個資料列和 6 個資料行使用測試 CSV：</span><span class="sxs-lookup"><span data-stu-id="98e95-150">The following example uses a test CSV with 26,616 rows and six columns:</span></span>

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|    <span data-ttu-id="98e95-151">計量</span><span class="sxs-lookup"><span data-stu-id="98e95-151">Metric</span></span>    | <span data-ttu-id="98e95-152">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="98e95-152">Windows PowerShell 5.1</span></span> | <span data-ttu-id="98e95-153">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="98e95-153">PowerShell Core 6.0</span></span> |  <span data-ttu-id="98e95-154">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="98e95-154">PowerShell Core 6.1</span></span>   |
| ------------ | ---------------------- | ------------------- | ---------------------- |
| <span data-ttu-id="98e95-155">時間 (秒)</span><span class="sxs-lookup"><span data-stu-id="98e95-155">Time (sec)</span></span>   | <span data-ttu-id="98e95-156">0.441</span><span class="sxs-lookup"><span data-stu-id="98e95-156">0.441</span></span>                  | <span data-ttu-id="98e95-157">1.069</span><span class="sxs-lookup"><span data-stu-id="98e95-157">1.069</span></span>               | <span data-ttu-id="98e95-158">0.268</span><span class="sxs-lookup"><span data-stu-id="98e95-158">0.268</span></span>                  |
| <span data-ttu-id="98e95-159">加速 (%)</span><span class="sxs-lookup"><span data-stu-id="98e95-159">Speed-up (%)</span></span> | <span data-ttu-id="98e95-160">N/A</span><span class="sxs-lookup"><span data-stu-id="98e95-160">N/A</span></span>                    | <span data-ttu-id="98e95-161">-142.4%</span><span class="sxs-lookup"><span data-stu-id="98e95-161">-142.4%</span></span>             | <span data-ttu-id="98e95-162">74.9% (39.2% 來自 WPS)</span><span class="sxs-lookup"><span data-stu-id="98e95-162">74.9% (39.2% from WPS)</span></span> |

<span data-ttu-id="98e95-163">最後，從 JSON 到 `PSObject` 的轉換自 Windows PowerShell 之後已加速超過 50%。</span><span class="sxs-lookup"><span data-stu-id="98e95-163">Lastly, conversion from JSON into `PSObject` has been sped up by more than 50% since Windows PowerShell.</span></span>
<span data-ttu-id="98e95-164">下列範例使用 ~2MB 測試 JSON 檔案：</span><span class="sxs-lookup"><span data-stu-id="98e95-164">The following example uses a ~2MB test JSON file:</span></span>

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|    <span data-ttu-id="98e95-165">計量</span><span class="sxs-lookup"><span data-stu-id="98e95-165">Metric</span></span>    | <span data-ttu-id="98e95-166">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="98e95-166">Windows PowerShell 5.1</span></span> | <span data-ttu-id="98e95-167">PowerShell Core 6.0</span><span class="sxs-lookup"><span data-stu-id="98e95-167">PowerShell Core 6.0</span></span> |  <span data-ttu-id="98e95-168">PowerShell Core 6.1</span><span class="sxs-lookup"><span data-stu-id="98e95-168">PowerShell Core 6.1</span></span>   |
| ------------ | ---------------------- | ------------------- | ---------------------- |
| <span data-ttu-id="98e95-169">時間 (秒)</span><span class="sxs-lookup"><span data-stu-id="98e95-169">Time (sec)</span></span>   | <span data-ttu-id="98e95-170">0.259</span><span class="sxs-lookup"><span data-stu-id="98e95-170">0.259</span></span>                  | <span data-ttu-id="98e95-171">0.577</span><span class="sxs-lookup"><span data-stu-id="98e95-171">0.577</span></span>               | <span data-ttu-id="98e95-172">0.125</span><span class="sxs-lookup"><span data-stu-id="98e95-172">0.125</span></span>                  |
| <span data-ttu-id="98e95-173">加速 (%)</span><span class="sxs-lookup"><span data-stu-id="98e95-173">Speed-up (%)</span></span> | <span data-ttu-id="98e95-174">N/A</span><span class="sxs-lookup"><span data-stu-id="98e95-174">N/A</span></span>                    | <span data-ttu-id="98e95-175">-122.8%</span><span class="sxs-lookup"><span data-stu-id="98e95-175">-122.8%</span></span>             | <span data-ttu-id="98e95-176">78.3% (51.7% 來自 WPS)</span><span class="sxs-lookup"><span data-stu-id="98e95-176">78.3% (51.7% from WPS)</span></span> |

## <a name="check-system32-for-compatible-built-in-modules-on-windows"></a><span data-ttu-id="98e95-177">查看 `system32` 中是否有符合 Windows 規範的內建模組</span><span class="sxs-lookup"><span data-stu-id="98e95-177">Check `system32` for compatible built-in modules on Windows</span></span>

<span data-ttu-id="98e95-178">在 Windows 10 1809 更新和 Windows Server 2019 中，我們更新了一些內建 PowerShell 模組以將其標記為符合 PowerShell Core 規範。</span><span class="sxs-lookup"><span data-stu-id="98e95-178">In the Windows 10 1809 update and Windows Server 2019, we updated a number of built-in PowerShell modules to mark them as compatible with PowerShell Core.</span></span>

<span data-ttu-id="98e95-179">當 PowerShell Core 6.1 啟動時，它會自動包含 `$windir\System32` 作為 `PSModulePath` 環境變數的一部分。</span><span class="sxs-lookup"><span data-stu-id="98e95-179">When PowerShell Core 6.1 starts up, it will automatically include `$windir\System32` as part of the `PSModulePath` environment variable.</span></span> <span data-ttu-id="98e95-180">不過，如果其 `CompatiblePSEdition` 標示為與 `Core` 相容，則只會對 `Get-Module` 和 `Import-Module` 公開模組。</span><span class="sxs-lookup"><span data-stu-id="98e95-180">However, it only exposes modules to `Get-Module` and `Import-Module` if its `CompatiblePSEdition` is marked as compatible with `Core`.</span></span>

```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> <span data-ttu-id="98e95-181">根據所安裝的角色和功能，您可能會看到不同的可用模組。</span><span class="sxs-lookup"><span data-stu-id="98e95-181">You may see different available modules depending on what roles and features are installed.</span></span>

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

<span data-ttu-id="98e95-182">您可以使用 `-SkipEditionCheck` 切換參數來覆寫此行為以顯示所有模組。</span><span class="sxs-lookup"><span data-stu-id="98e95-182">You can override this behavior to show all modules using the `-SkipEditionCheck` switch parameter.</span></span>
<span data-ttu-id="98e95-183">我們也將 `PSEdition` 屬性新增至資料表輸出。</span><span class="sxs-lookup"><span data-stu-id="98e95-183">We've also added a `PSEdition` property to the table output.</span></span>

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

<span data-ttu-id="98e95-184">如需此行為的詳細資訊，請參閱 [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="98e95-184">For more information about this behavior, check out [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).</span></span>

## <a name="markdown-cmdlets-and-rendering"></a><span data-ttu-id="98e95-185">Markdown Cmdlet 和轉譯</span><span class="sxs-lookup"><span data-stu-id="98e95-185">Markdown cmdlets and rendering</span></span>

<span data-ttu-id="98e95-186">Markdown 是用於建立可讀取純文字文件的一項標準，這些文件具有基本格式，可轉譯為 HTML。</span><span class="sxs-lookup"><span data-stu-id="98e95-186">Markdown is a standard for creating readable plaintext documents with basic formatting that can be rendered into HTML.</span></span>

<span data-ttu-id="98e95-187">我們在 6.1 版中新增了一些 Cmdlet，可讓您轉換和轉譯主控台中的 Markdown 文件，包括：</span><span class="sxs-lookup"><span data-stu-id="98e95-187">We've added some cmdlets in 6.1 that allow you to convert and render Markdown documents in the console, including:</span></span>

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

<span data-ttu-id="98e95-188">例如，`Show-Markdown` 會轉譯主控台中的 Markdown 檔案：</span><span class="sxs-lookup"><span data-stu-id="98e95-188">For example, `Show-Markdown` renders a Markdown file in the console:</span></span>

![Show-Markdown 範例](media/What-s-New-in-PowerShell-Core-61/markdown_example.png)

<span data-ttu-id="98e95-190">如需這些 Cmdlet 運作方式的詳細資訊，請參閱[此 RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="98e95-190">For more information about how these cmdlets work, check out [this RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).</span></span>

## <a name="experimental-feature-flags"></a><span data-ttu-id="98e95-191">實驗性功能旗標</span><span class="sxs-lookup"><span data-stu-id="98e95-191">Experimental feature flags</span></span>

<span data-ttu-id="98e95-192">我們已啟用對[實驗性功能][]的支援。</span><span class="sxs-lookup"><span data-stu-id="98e95-192">We enabled support for [Experimental Features][].</span></span> <span data-ttu-id="98e95-193">這可讓 PowerShell 開發人員在設計完成之前，先提供新功能並取得意見反應。</span><span class="sxs-lookup"><span data-stu-id="98e95-193">This allows PowerShell developers to deliver new features and get feedback before the design is complete.</span></span> <span data-ttu-id="98e95-194">我們也能藉此避免在設計演變的過程中進行重大變更。</span><span class="sxs-lookup"><span data-stu-id="98e95-194">This way we avoid making breaking changes as the design evolves.</span></span>

<span data-ttu-id="98e95-195">請使用 `Get-ExperimentalFeature` 取得一份可用實驗性功能的清單。</span><span class="sxs-lookup"><span data-stu-id="98e95-195">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="98e95-196">您可以使用 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` 啟用或停用這些功能。</span><span class="sxs-lookup"><span data-stu-id="98e95-196">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

<span data-ttu-id="98e95-197">您可以在 [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md) 中深入了解這項功能。</span><span class="sxs-lookup"><span data-stu-id="98e95-197">You can learn more about this feature in [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).</span></span>

## <a name="web-cmdlet-improvements"></a><span data-ttu-id="98e95-198">Web Cmdlet 改善</span><span class="sxs-lookup"><span data-stu-id="98e95-198">Web cmdlet improvements</span></span>

<span data-ttu-id="98e95-199">感謝 [@markekraus](https://github.com/markekraus)，下列 Web Cmdlet 已做出許多改善：[`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span><span class="sxs-lookup"><span data-stu-id="98e95-199">Thanks to [@markekraus](https://github.com/markekraus), a whole slew of improvements have been made to our web cmdlets: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)</span></span>
<span data-ttu-id="98e95-200">和 [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod)。</span><span class="sxs-lookup"><span data-stu-id="98e95-200">and [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).</span></span>

- <span data-ttu-id="98e95-201">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - `application-json` 回應的預設編碼設為 UTF-8</span><span class="sxs-lookup"><span data-stu-id="98e95-201">[PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - default encoding set to UTF-8 for `application-json` responses</span></span>
- <span data-ttu-id="98e95-202">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` 參數可允許不符合標準的 `Content-Type` 標頭</span><span class="sxs-lookup"><span data-stu-id="98e95-202">[PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` parameter to allow `Content-Type` headers that aren't standards-compliant</span></span>
- <span data-ttu-id="98e95-203">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` 參數可支援簡化的 `multipart/form-data` 支援</span><span class="sxs-lookup"><span data-stu-id="98e95-203">[PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` parameter to support simplified `multipart/form-data` support</span></span>
- <span data-ttu-id="98e95-204">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - 以符合規範且不區分大小寫的方式來處理關聯索引鍵</span><span class="sxs-lookup"><span data-stu-id="98e95-204">[PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - Compliant, case-insensitive handling of relation keys</span></span>
- <span data-ttu-id="98e95-205">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - 在 Web Cmdlet 中新增 `-Resume` 參數</span><span class="sxs-lookup"><span data-stu-id="98e95-205">[PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - Add `-Resume` parameter for web cmdlets</span></span>

## <a name="remoting-improvements"></a><span data-ttu-id="98e95-206">遠端功能改善</span><span class="sxs-lookup"><span data-stu-id="98e95-206">Remoting improvements</span></span>

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a><span data-ttu-id="98e95-207">適用於容器的 PowerShell Direct 會先嘗試使用 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="98e95-207">PowerShell Direct for Containers tries to use PowerShell Core first</span></span>

<span data-ttu-id="98e95-208">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) 是 PowerShell 和 Hyper-V 的功能，可讓您連線到 Hyper-V VM 或容器，而不需要網路連線或其他遠端管理服務。</span><span class="sxs-lookup"><span data-stu-id="98e95-208">[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) is a feature of PowerShell and Hyper-V that allows you to connect to a Hyper-V VM or Container without network connectivity or other remote management services.</span></span>

<span data-ttu-id="98e95-209">過去，PowerShell Direct 使用容器上的內建 Windows PowerShell 執行個體進行連線。</span><span class="sxs-lookup"><span data-stu-id="98e95-209">In the past, PowerShell Direct connected using the built-in Windows PowerShell instance on the Container.</span></span> <span data-ttu-id="98e95-210">現在，PowerShell 會先嘗試使用 `PATH` 環境變數上的任何可用 `pwsh.exe` 進行連線。</span><span class="sxs-lookup"><span data-stu-id="98e95-210">Now, PowerShell Direct first attempts to connect using any available `pwsh.exe` on the `PATH` environment variable.</span></span> <span data-ttu-id="98e95-211">如果沒有 `pwsh.exe`，PowerShell Direct 會改為使用 `powershell.exe`。</span><span class="sxs-lookup"><span data-stu-id="98e95-211">If `pwsh.exe` isn't available, PowerShell Direct falls back to use `powershell.exe`.</span></span>

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a><span data-ttu-id="98e95-212">`Enable-PSRemoting` 現在會為預覽版本建立個別遠端端點</span><span class="sxs-lookup"><span data-stu-id="98e95-212">`Enable-PSRemoting` now creates separate remoting endpoints for preview versions</span></span>

<span data-ttu-id="98e95-213">`Enable-PSRemoting` 現在會建立兩個遠端工作階段設定：</span><span class="sxs-lookup"><span data-stu-id="98e95-213">`Enable-PSRemoting` now creates two remoting session configurations:</span></span>

- <span data-ttu-id="98e95-214">一個用於 PowerShell 的主要版本。</span><span class="sxs-lookup"><span data-stu-id="98e95-214">One for the major version of PowerShell.</span></span> <span data-ttu-id="98e95-215">例如： `PowerShell.6` 。</span><span class="sxs-lookup"><span data-stu-id="98e95-215">For example, `PowerShell.6`.</span></span> <span data-ttu-id="98e95-216">在次要版本更新之間，可依賴此端點作為「全系統」的 PowerShell 6 工作階段設定</span><span class="sxs-lookup"><span data-stu-id="98e95-216">This endpoint that can be relied upon across minor version updates as the "system-wide" PowerShell 6 session configuration</span></span>
- <span data-ttu-id="98e95-217">一個版本特定的工作階段設定，例如：`PowerShell.6.1.0`</span><span class="sxs-lookup"><span data-stu-id="98e95-217">One version-specific session configuration, for example: `PowerShell.6.1.0`</span></span>

<span data-ttu-id="98e95-218">如果您想要在相同電腦上安裝多個 PowerShell 6 版本以供存取，此行為會很有用。</span><span class="sxs-lookup"><span data-stu-id="98e95-218">This behavior is useful if you want to have multiple PowerShell 6 versions installed and accessible on the same machine.</span></span>

<span data-ttu-id="98e95-219">此外，PowerShell 的預覽版本現在可在執行 `Enable-PSRemoting` Cmdlet 之後，取得自己的遠端工作階段設定：</span><span class="sxs-lookup"><span data-stu-id="98e95-219">Additionally, preview versions of PowerShell now get their own remoting session configurations after running the `Enable-PSRemoting` cmdlet:</span></span>

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

<span data-ttu-id="98e95-220">如果您之前尚未設定 WinRM，您的輸出可能會不同。</span><span class="sxs-lookup"><span data-stu-id="98e95-220">Your output may be different if you haven't set up WinRM before.</span></span>

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

<span data-ttu-id="98e95-221">然後，您可以看到 PowerShell 6 預覽和穩定組建以及每個特定版本的個別 PowerShell 工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="98e95-221">Then you can see separate PowerShell session configurations for the preview and stable builds of PowerShell 6, and for each specific version.</span></span>

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a><span data-ttu-id="98e95-222">SSH 支援 `user@host:port` 語法</span><span class="sxs-lookup"><span data-stu-id="98e95-222">`user@host:port` syntax supported for SSH</span></span>

<span data-ttu-id="98e95-223">SSH 用戶端通常支援 `user@host:port` 格式的連接字串。</span><span class="sxs-lookup"><span data-stu-id="98e95-223">SSH clients typically support a connection string in the format `user@host:port`.</span></span> <span data-ttu-id="98e95-224">透過新增 SSH 作為 PowerShell 遠端通訊協定，我們已新增對此連接字串格式的支援：</span><span class="sxs-lookup"><span data-stu-id="98e95-224">With the addition of SSH as a protocol for PowerShell Remoting, we've added support for this format of connection string:</span></span>

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a><span data-ttu-id="98e95-225">在 Windows 上新增檔案總管殼層操作功能表的 MSI 選項</span><span class="sxs-lookup"><span data-stu-id="98e95-225">MSI option to add explorer shell context menu on Windows</span></span>

<span data-ttu-id="98e95-226">感謝 [@bergmeister](https://github.com/bergmeister)，現在您可以在 Windows 上啟用操作功能表。</span><span class="sxs-lookup"><span data-stu-id="98e95-226">Thanks to [@bergmeister](https://github.com/bergmeister), now you can enable a context menu on Windows.</span></span> <span data-ttu-id="98e95-227">現在，您可以從 Windows 檔案總管中的任何資料夾開啟 PowerShell 6.1 的全系統安裝：</span><span class="sxs-lookup"><span data-stu-id="98e95-227">Now you can open your system-wide installation of PowerShell 6.1 from any folder in the Windows Explorer:</span></span>

![PowerShell 6 的殼層操作功能表](media/What-s-New-in-PowerShell-Core-61/shell_context_menu.png)

## <a name="goodies"></a><span data-ttu-id="98e95-229">很棒的功能</span><span class="sxs-lookup"><span data-stu-id="98e95-229">Goodies</span></span>

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a><span data-ttu-id="98e95-230">Windows 捷徑清單中的 [以系統管理員身分執行]</span><span class="sxs-lookup"><span data-stu-id="98e95-230">"Run as Administrator" in the Windows shortcut jump list</span></span>

<span data-ttu-id="98e95-231">感謝 [@bergmeister](https://github.com/bergmeister)，PowerShell Core 捷徑清單現在包含 [以系統管理員身分執行]：</span><span class="sxs-lookup"><span data-stu-id="98e95-231">Thanks to [@bergmeister](https://github.com/bergmeister), the PowerShell Core shortcut's jump list now includes "Run as Administrator":</span></span>

![PowerShell 6 捷徑清單中的 [以系統管理員身分執行]](media/What-s-New-in-PowerShell-Core-61/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a><span data-ttu-id="98e95-233">`cd -` 返回上一個目錄</span><span class="sxs-lookup"><span data-stu-id="98e95-233">`cd -` returns to previous directory</span></span>

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

<span data-ttu-id="98e95-234">或在 Linux 上：</span><span class="sxs-lookup"><span data-stu-id="98e95-234">Or on Linux:</span></span>

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

<span data-ttu-id="98e95-235">此外，`cd` 和 `cd --` 變更為 `$HOME`。</span><span class="sxs-lookup"><span data-stu-id="98e95-235">Also, `cd` and `cd --` change to `$HOME`.</span></span>

### `Test-Connection`

<span data-ttu-id="98e95-236">感謝 [@iSazonov](https://github.com/iSazonov)，[`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) Cmdlet 已移植到 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="98e95-236">Thanks to [@iSazonov](https://github.com/iSazonov), the [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet has been ported to PowerShell Core.</span></span>

### <a name="update-help-as-non-admin"></a><span data-ttu-id="98e95-237">以非系統管理員身分執行 `Update-Help`</span><span class="sxs-lookup"><span data-stu-id="98e95-237">`Update-Help` as non-admin</span></span>

<span data-ttu-id="98e95-238">經熱烈要求，`Update-Help` 不再需要以系統管理員身分執行。</span><span class="sxs-lookup"><span data-stu-id="98e95-238">By popular demand, `Update-Help` no longer needs to be run as an administrator.</span></span> <span data-ttu-id="98e95-239">`Update-Help` 現在預設會將說明儲存至使用者範圍的資料夾。</span><span class="sxs-lookup"><span data-stu-id="98e95-239">`Update-Help` now defaults to saving help to a user-scoped folder.</span></span>

### <a name="new-methodsproperties-on-pscustomobject"></a><span data-ttu-id="98e95-240">`PSCustomObject` 上的新方法/屬性</span><span class="sxs-lookup"><span data-stu-id="98e95-240">New methods/properties on `PSCustomObject`</span></span>

<span data-ttu-id="98e95-241">感謝 [@iSazonov](https://github.com/iSazonov)，我們已新增方法和屬性至 `PSCustomObject`。</span><span class="sxs-lookup"><span data-stu-id="98e95-241">Thanks to [@iSazonov](https://github.com/iSazonov), we've added new methods and properties to `PSCustomObject`.</span></span> <span data-ttu-id="98e95-242">`PSCustomObject` 現在類似其他物件包含 `Count`/`Length` 屬性。</span><span class="sxs-lookup"><span data-stu-id="98e95-242">`PSCustomObject` now includes a `Count`/`Length` property like other objects.</span></span>

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

<span data-ttu-id="98e95-243">這項工作也包含 `ForEach` 和 `Where` 方法，可讓您操作並篩選 `PSCustomObject` 項目：</span><span class="sxs-lookup"><span data-stu-id="98e95-243">This work also includes `ForEach` and `Where` methods that allow you to operate and filter on `PSCustomObject` items:</span></span>

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

<span data-ttu-id="98e95-244">感謝 @SimonWahlin，我們已將 `-Not` 參數新增至 `Where-Object`。</span><span class="sxs-lookup"><span data-stu-id="98e95-244">Thanks to @SimonWahlin, we've added the `-Not` parameter to `Where-Object`.</span></span> <span data-ttu-id="98e95-245">現在，您可以依不存在的屬性或 Null/空白屬性值來篩選管線上的物件。</span><span class="sxs-lookup"><span data-stu-id="98e95-245">Now you can filter an object at the pipeline for the non-existence of a property, or a null/empty property value.</span></span>

<span data-ttu-id="98e95-246">例如，此命令會傳回未定義任何相依服務的所有服務：</span><span class="sxs-lookup"><span data-stu-id="98e95-246">For example, this command returns all services that don't have any dependent services defined:</span></span>

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a><span data-ttu-id="98e95-247">`New-ModuleManifest` 會建立無 BOM 的 UTF-8 文件</span><span class="sxs-lookup"><span data-stu-id="98e95-247">`New-ModuleManifest` creates a BOM-less UTF-8 document</span></span>

<span data-ttu-id="98e95-248">由於我們在 PowerShell 6.0 中移至無 BOM 的 UTF-8，我們已更新 `New-ModuleManifest` Cmdlet 建立無 BOM 的 UTF-8 文件，而不是 UTF-16 文件。</span><span class="sxs-lookup"><span data-stu-id="98e95-248">Given our move to BOM-less UTF-8 in PowerShell 6.0, we've updated the `New-ModuleManifest` cmdlet to create a BOM-less UTF-8 document instead of a UTF-16 one.</span></span>

### <a name="conversions-from-psmethod-to-delegate"></a><span data-ttu-id="98e95-249">從 PSMethod 轉換成委派</span><span class="sxs-lookup"><span data-stu-id="98e95-249">Conversions from PSMethod to Delegate</span></span>

<span data-ttu-id="98e95-250">感謝 [@powercode](https://github.com/powercode)，我們現在支援從 `PSMethod` 轉換成委派。</span><span class="sxs-lookup"><span data-stu-id="98e95-250">Thanks to [@powercode](https://github.com/powercode), we now support the conversion of a `PSMethod` into a delegate.</span></span> <span data-ttu-id="98e95-251">這可讓您執行將 `PSMethod` `[M]::DoubleStrLen` 當作委派值傳入 `[M]::AggregateString` 之類的動作：</span><span class="sxs-lookup"><span data-stu-id="98e95-251">This allows you to do things like passing `PSMethod` `[M]::DoubleStrLen` as a delegate value into `[M]::AggregateString`:</span></span>

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

<span data-ttu-id="98e95-252">如需這項變更的詳細資訊，請參閱 [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287)。</span><span class="sxs-lookup"><span data-stu-id="98e95-252">For more info on this change, check out [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).</span></span>

### <a name="standard-deviation-in-measure-object"></a><span data-ttu-id="98e95-253">`Measure-Object` 中的標準差</span><span class="sxs-lookup"><span data-stu-id="98e95-253">Standard deviation in `Measure-Object`</span></span>

<span data-ttu-id="98e95-254">感謝 [@CloudyDino](https://github.com/CloudyDino)，我們已將 `StandardDeviation` 屬性新增至 `Measure-Object`：</span><span class="sxs-lookup"><span data-stu-id="98e95-254">Thanks to [@CloudyDino](https://github.com/CloudyDino), we've added a `StandardDeviation` property to `Measure-Object`:</span></span>

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

<span data-ttu-id="98e95-255">感謝 [@maybe-hello-world](https://github.com/maybe-hello-world)，`Get-PfxCertificate` 現在包含接受 `SecureString` 的 `Password` 參數。</span><span class="sxs-lookup"><span data-stu-id="98e95-255">Thanks to [@maybe-hello-world](https://github.com/maybe-hello-world), `Get-PfxCertificate` now has the `Password` parameter, which takes a `SecureString`.</span></span> <span data-ttu-id="98e95-256">這可讓您以非互動方式使用它：</span><span class="sxs-lookup"><span data-stu-id="98e95-256">This allows you to use it non-interactively:</span></span>

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a><span data-ttu-id="98e95-257">移除 `more` 函式</span><span class="sxs-lookup"><span data-stu-id="98e95-257">Removal of the `more` function</span></span>

<span data-ttu-id="98e95-258">在過去，PowerShell 在 Windows 上提供用來包裝 `more.com` 的函式，稱為 `more`。</span><span class="sxs-lookup"><span data-stu-id="98e95-258">In the past, PowerShell shipped a function on Windows called `more` that wrapped `more.com`.</span></span> <span data-ttu-id="98e95-259">該函式現在已移除。</span><span class="sxs-lookup"><span data-stu-id="98e95-259">That function has now been removed.</span></span>

<span data-ttu-id="98e95-260">此外，`help` 函式已變更為使用 `more.com` (在 Windows 上) 或 `$env:PAGER` 所指定系統的預設頁面巡覽區 (非 Windows 平台上)。</span><span class="sxs-lookup"><span data-stu-id="98e95-260">Also, the `help` function changed to use `more.com` on Windows, or the system's default pager specified by `$env:PAGER` on non-Windows platforms.</span></span>

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a><span data-ttu-id="98e95-261">`cd DriveName:` 現在會讓使用者返回該磁碟機中的目前工作目錄</span><span class="sxs-lookup"><span data-stu-id="98e95-261">`cd DriveName:` now returns users to the current working directory in that drive</span></span>

<span data-ttu-id="98e95-262">之前，使用 `Set-Location` 或 `cd` 返回 PSDrive 會將使用者傳送至該磁碟機的預設位置。</span><span class="sxs-lookup"><span data-stu-id="98e95-262">Previously, using `Set-Location` or `cd` to return to a PSDrive sent users to the default location for that drive.</span></span>

<span data-ttu-id="98e95-263">感謝 [@mcbobke](https://github.com/mcbobke)，使用者現在會傳送至該工作階段的上一個已知目前工作目錄。</span><span class="sxs-lookup"><span data-stu-id="98e95-263">Thanks to [@mcbobke](https://github.com/mcbobke), users are now sent to the last known current working directory for that session.</span></span>

### <a name="windows-powershell-type-accelerators"></a><span data-ttu-id="98e95-264">Windows PowerShell 類型快速鍵</span><span class="sxs-lookup"><span data-stu-id="98e95-264">Windows PowerShell type accelerators</span></span>

<span data-ttu-id="98e95-265">在 Windows PowerShell 中，我們會包含下列類型快速鍵，以更輕鬆地搭配其各自類型來運作：</span><span class="sxs-lookup"><span data-stu-id="98e95-265">In Windows PowerShell, we included the following type accelerators to make it easier to work with their respective types:</span></span>

- <span data-ttu-id="98e95-266">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span><span class="sxs-lookup"><span data-stu-id="98e95-266">`[adsi]`: `System.DirectoryServices.DirectoryEntry`</span></span>
- <span data-ttu-id="98e95-267">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span><span class="sxs-lookup"><span data-stu-id="98e95-267">`[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`</span></span>
- <span data-ttu-id="98e95-268">`[wmi]`: `System.Management.ManagementObject`</span><span class="sxs-lookup"><span data-stu-id="98e95-268">`[wmi]`: `System.Management.ManagementObject`</span></span>
- <span data-ttu-id="98e95-269">`[wmiclass]`: `System.Management.ManagementClass`</span><span class="sxs-lookup"><span data-stu-id="98e95-269">`[wmiclass]`: `System.Management.ManagementClass`</span></span>
- <span data-ttu-id="98e95-270">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span><span class="sxs-lookup"><span data-stu-id="98e95-270">`[wmisearcher]`: `System.Management.ManagementObjectSearcher`</span></span>

<span data-ttu-id="98e95-271">這些類型快速鍵並未包含在 PowerShell 6 中，但已新增至 Windows 上執行的 PowerShell 6.1。</span><span class="sxs-lookup"><span data-stu-id="98e95-271">These type accelerators were not included in PowerShell 6, but have been added to PowerShell 6.1 running on Windows.</span></span>

<span data-ttu-id="98e95-272">這些類型可方便您建構 AD 和 WMI 物件。</span><span class="sxs-lookup"><span data-stu-id="98e95-272">These types are useful in easily constructing AD and WMI objects.</span></span>

<span data-ttu-id="98e95-273">例如，您可以使用 LDAP 進行查詢：</span><span class="sxs-lookup"><span data-stu-id="98e95-273">For example, you can query using LDAP:</span></span>

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

<span data-ttu-id="98e95-274">下列範例會建立 Win32_OperatingSystem CIM 物件：</span><span class="sxs-lookup"><span data-stu-id="98e95-274">Following example creates a Win32_OperatingSystem CIM object:</span></span>

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

<span data-ttu-id="98e95-275">此範例會傳回 Win32_OperatingSystem 類別的 ManagementClass 物件。</span><span class="sxs-lookup"><span data-stu-id="98e95-275">This example returns a ManagementClass object for Win32_OperatingSystem class.</span></span>

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a><span data-ttu-id="98e95-276">用於所有 `-LiteralPath` 參數的 `-lp` 別名</span><span class="sxs-lookup"><span data-stu-id="98e95-276">`-lp` alias for all `-LiteralPath` parameters</span></span>

<span data-ttu-id="98e95-277">感謝 [@kvprasoon](https://github.com/kvprasoon)，具有 `-LiteralPath` 參數的所有內建 PowerShell Cmdlet 現在有一個參數別名 `-lp`。</span><span class="sxs-lookup"><span data-stu-id="98e95-277">Thanks to [@kvprasoon](https://github.com/kvprasoon), we now have a parameter alias `-lp` for all the built-in PowerShell cmdlets that have a `-LiteralPath` parameter.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="98e95-278">重大變更</span><span class="sxs-lookup"><span data-stu-id="98e95-278">Breaking Changes</span></span>

### <a name="msi-based-installation-paths-on-windows"></a><span data-ttu-id="98e95-279">Windows 上的 MSI 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="98e95-279">MSI-based installation paths on Windows</span></span>

<span data-ttu-id="98e95-280">在 Windows 上，MSI 套件現在會安裝到下列路徑：</span><span class="sxs-lookup"><span data-stu-id="98e95-280">On Windows, the MSI package now installs to the following path:</span></span>

- <span data-ttu-id="98e95-281">若是 6.x 的穩定安裝，則為 `$env:ProgramFiles\PowerShell\6\`</span><span class="sxs-lookup"><span data-stu-id="98e95-281">`$env:ProgramFiles\PowerShell\6\` for the stable installation of 6.x</span></span>
- <span data-ttu-id="98e95-282">若是 6.x 的預覽安裝，則為 `$env:ProgramFiles\PowerShell\6-preview\`</span><span class="sxs-lookup"><span data-stu-id="98e95-282">`$env:ProgramFiles\PowerShell\6-preview\` for the preview installation of 6.x</span></span>

<span data-ttu-id="98e95-283">這項變更會確保 PowerShell Core 可透過 Microsoft Update 來更新或接受服務。</span><span class="sxs-lookup"><span data-stu-id="98e95-283">This change ensures that PowerShell Core can be updated/serviced by Microsoft Update.</span></span>

<span data-ttu-id="98e95-284">如需詳細資訊，請參閱 [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md)。</span><span class="sxs-lookup"><span data-stu-id="98e95-284">For more information, check out [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).</span></span>

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a><span data-ttu-id="98e95-285">遙測只能透過環境變數停用</span><span class="sxs-lookup"><span data-stu-id="98e95-285">Telemetry can only be disabled with an environment variable</span></span>

<span data-ttu-id="98e95-286">PowerShell Core 會在啟動時將基本遙測資料傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="98e95-286">PowerShell Core sends basic telemetry data to Microsoft when it is launched.</span></span> <span data-ttu-id="98e95-287">該資料包括作業系統名稱、作業系統版本和 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="98e95-287">The data includes the OS name, OS version, and PowerShell version.</span></span> <span data-ttu-id="98e95-288">這項資料可讓我們更加了解使用 PowerShell 的環境，並讓我們排列新功能和修正的優先順序。</span><span class="sxs-lookup"><span data-stu-id="98e95-288">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>

<span data-ttu-id="98e95-289">若要退出此遙測，請將環境變數 `POWERSHELL_TELEMETRY_OPTOUT` 設定為 `true`、`yes` 或 `1`。</span><span class="sxs-lookup"><span data-stu-id="98e95-289">To opt-out of this telemetry, set the environment variable `POWERSHELL_TELEMETRY_OPTOUT` to `true`, `yes`, or `1`.</span></span> <span data-ttu-id="98e95-290">我們不再支援透過刪除 `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` 檔案來停用遙測。</span><span class="sxs-lookup"><span data-stu-id="98e95-290">We no longer support deletion of the file `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` to disable telemetry.</span></span>

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a><span data-ttu-id="98e95-291">UNIX 平台上的 PowerShell 遠端功能不允許透過 HTTP 進行基本驗證</span><span class="sxs-lookup"><span data-stu-id="98e95-291">Disallowed Basic Auth over HTTP in PowerShell Remoting on Unix platforms</span></span>

<span data-ttu-id="98e95-292">為了避免使用未加密的流量，UNIX 平台上的 PowerShell 遠端功能現在需要使用 NTLM/交涉或 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="98e95-292">To prevent the use of unencrypted traffic, PowerShell Remoting on Unix platforms now requires usage of NTLM/Negotiate or HTTPS.</span></span>

<span data-ttu-id="98e95-293">如需這些變更的詳細資訊，請參閱[問題 #6779](https://github.com/PowerShell/PowerShell/issues/6779)。</span><span class="sxs-lookup"><span data-stu-id="98e95-293">For more information on these changes, check out [Issue #6779](https://github.com/PowerShell/PowerShell/issues/6779).</span></span>

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a><span data-ttu-id="98e95-294">已將 `VisualBasic` 從 Add-Type 支援的語言中移除</span><span class="sxs-lookup"><span data-stu-id="98e95-294">Removed `VisualBasic` as a supported language in Add-Type</span></span>

<span data-ttu-id="98e95-295">在過去，您可以使用 `Add-Type` Cmdlet 編譯 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="98e95-295">In the past, you could compile Visual Basic code using the `Add-Type` cmdlet.</span></span> <span data-ttu-id="98e95-296">Visual Basic 很少用於 `Add-Type`。</span><span class="sxs-lookup"><span data-stu-id="98e95-296">Visual Basic was rarely used with `Add-Type`.</span></span> <span data-ttu-id="98e95-297">我們已移除這項功能來縮減 PowerShell 的大小。</span><span class="sxs-lookup"><span data-stu-id="98e95-297">We removed this feature to reduce the size of PowerShell.</span></span>

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a><span data-ttu-id="98e95-298">已清除 `CommandTypes.Workflow` 和 `WorkflowInfoCleaned` 的使用</span><span class="sxs-lookup"><span data-stu-id="98e95-298">Cleaned up uses of `CommandTypes.Workflow` and `WorkflowInfoCleaned`</span></span>

<span data-ttu-id="98e95-299">如需這些變更的詳細資訊，請參閱 [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708)。</span><span class="sxs-lookup"><span data-stu-id="98e95-299">For more information on these changes, check out [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).</span></span>

### <a name="group-object-now-sorts-the-groups"></a><span data-ttu-id="98e95-300">Group-Object 現在會對群組進行排序</span><span class="sxs-lookup"><span data-stu-id="98e95-300">Group-Object now sorts the groups</span></span>

<span data-ttu-id="98e95-301">作為效能改進的一部分，`Group-Object` 現在會傳回已排序的群組清單。</span><span class="sxs-lookup"><span data-stu-id="98e95-301">As part of the performance improvement, `Group-Object` now returns a sorted listing of the groups.</span></span>
<span data-ttu-id="98e95-302">雖然您不應該依賴順序，但如果您想要第一個群組，則可能會被此變更中斷。</span><span class="sxs-lookup"><span data-stu-id="98e95-302">Although you should not rely on the order, you could be broken by this change if you wanted the first group.</span></span> <span data-ttu-id="98e95-303">我們認為這種效能改進值得改變，因為依賴於先前行為的影響很小。</span><span class="sxs-lookup"><span data-stu-id="98e95-303">We decided that this performance improvement was worth the change since the impact of being dependent on previous behavior is low.</span></span>

<span data-ttu-id="98e95-304">如需此變更的詳細資訊，請參閱 [問題 #7409](https://github.com/PowerShell/PowerShell/issues/7409) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="98e95-304">For more information on this change, see [Issue #7409](https://github.com/PowerShell/PowerShell/issues/7409).</span></span>

<!-- URL references -->
[實驗性功能]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
