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
# <a name="whats-new-in-powershell-core-62"></a>PowerShell Core 6.2 的新功能

以下是 PowerShell Core 6.2 中已引進的一些主要新功能與變更精選。

還有**許多**「乏味的項目」讓 PowerShell 變得更快且更穩定 (外加許許多多的 Bug 修正)！
如需變更的完整清單，請參閱 [GitHub 上的變更記錄](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)。

此外，除了下文所提到的一些名字，我們也感謝[所有社群參與者](https://github.com/PowerShell/PowerShell/graphs/contributors)協助實現這次的發行。

## <a name="engine-updates-and-fixes"></a>引擎更新與修正

- 新增 PowerShell 遠端啟用/停用 Cmdlet 警告訊息 ([#9203][])
- `FormatTable`遠端還原序列化迴歸 ([#9116][]) 的修正
- 更新新增至 PowerShell 且以工作為基礎的 `async` API，以直接傳回工作物件 ([#9079][])
- 新增 5 個`InvokeAsync` 多載和 `StopAsync` 至 `PowerShell` 型別 ([#8056][]) (感謝 @KirkMunro！)

## <a name="general-cmdlet-updates-and-fixes"></a>一般 Cmdlet 更新與修正

- 透過儲存純文字以啟用非 Windows 的 `SecureString` Cmdlet ([#9199][])
- 新增已淘汰的訊息至 `Send-MailMessage` ([#9178][])
- 修正 `Restart-Computer` 以在沒有 WinRM 時於 `localhost` 中運作 ([#9160][])
- 讓 `Start-Job` 在裝載 PowerShell 時擲回終止錯誤 ([#9128][])
- 更新 `PowerShell.Native` 的版本並裝載測試 ([#8983][])

## <a name="breaking-changes"></a>重大變更

修正 Write-Output 中的 -NoEnumerate 行為，以與 Windows PowerShell 一致 ([#9069][]) (感謝 @vexx32！)

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
