---
title: PowerShell Core 6.2 的新功能
description: PowerShell Core 6.2 中發行的新功能與變更
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750047"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="fab71-103">PowerShell Core 6.2 的新功能</span><span class="sxs-lookup"><span data-stu-id="fab71-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="fab71-104">以下是 PowerShell Core 6.2 中已引進的一些主要新功能與變更精選。</span><span class="sxs-lookup"><span data-stu-id="fab71-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="fab71-105">還有**許多**「乏味的項目」讓 PowerShell 變得更快且更穩定 (外加許許多多的 Bug 修正)！</span><span class="sxs-lookup"><span data-stu-id="fab71-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="fab71-106">如需變更的完整清單，請參閱 [GitHub 上的變更記錄](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)。</span><span class="sxs-lookup"><span data-stu-id="fab71-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="fab71-107">此外，除了下文所提到的一些名字，我們也感謝[所有社群參與者](https://github.com/PowerShell/PowerShell/graphs/contributors)協助實現這次的發行。</span><span class="sxs-lookup"><span data-stu-id="fab71-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="fab71-108">引擎更新與修正</span><span class="sxs-lookup"><span data-stu-id="fab71-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="fab71-109">新增 PowerShell 遠端啟用/停用 Cmdlet 警告訊息 ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="fab71-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="fab71-110">`FormatTable`遠端還原序列化迴歸 ([#9116][]) 的修正</span><span class="sxs-lookup"><span data-stu-id="fab71-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="fab71-111">更新新增至 PowerShell 且以工作為基礎的 `async` API，以直接傳回工作物件 ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="fab71-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="fab71-112">新增 5 個`InvokeAsync` 多載和 `StopAsync` 至 `PowerShell` 型別 ([#8056][]) (感謝 @KirkMunro！)</span><span class="sxs-lookup"><span data-stu-id="fab71-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="fab71-113">一般 Cmdlet 更新與修正</span><span class="sxs-lookup"><span data-stu-id="fab71-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="fab71-114">透過儲存純文字以啟用非 Windows 的 `SecureString` Cmdlet ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="fab71-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="fab71-115">新增已淘汰的訊息至 `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="fab71-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="fab71-116">修正 `Restart-Computer` 以在沒有 WinRM 時於 `localhost` 中運作 ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="fab71-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="fab71-117">讓 `Start-Job` 在裝載 PowerShell 時擲回終止錯誤 ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="fab71-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="fab71-118">更新 `PowerShell.Native` 的版本並裝載測試 ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="fab71-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="fab71-119">重大變更</span><span class="sxs-lookup"><span data-stu-id="fab71-119">Breaking Changes</span></span>

<span data-ttu-id="fab71-120">修正 Write-Output 中的 -NoEnumerate 行為，以與 Windows PowerShell 一致 ([#9069][]) (感謝 @vexx32！)</span><span class="sxs-lookup"><span data-stu-id="fab71-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
