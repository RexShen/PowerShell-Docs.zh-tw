---
ms.date: 06/12/2017
title: 資源庫的 ScriptAnazlyer 規則設定檔
description: 說明 PowerShell ScriptAnalyzer 如何與 PowerShell 資源庫整合。
ms.openlocfilehash: 3af710e8811f0fabfb02f5317d5b4ff9c320f29a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646773"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="a8ec4-103">資源庫的 ScriptAnazlyer 規則設定檔</span><span class="sxs-lookup"><span data-stu-id="a8ec4-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="a8ec4-104">為了確保發行至 PowerShell 資源庫的套件品質，我們會執行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 規則，判斷提交的指令碼中是否有任何違規。</span><span class="sxs-lookup"><span data-stu-id="a8ec4-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="a8ec4-105">您可以在 ScriptAnalyzer [GitHub 頁面](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1)找到我們所執行的規則清單。</span><span class="sxs-lookup"><span data-stu-id="a8ec4-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="a8ec4-106">如果您對我們執行的規則有任何疑慮，請連絡 PowerShell 資源庫管理員，或提出 ScriptAnalzyer 問題。</span><span class="sxs-lookup"><span data-stu-id="a8ec4-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="a8ec4-107">在之後的版本中，ScriptAnalyzer 結果將於資源庫的每個個別套件頁面中顯示。</span><span class="sxs-lookup"><span data-stu-id="a8ec4-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="a8ec4-108">建議套件擁有者檢查自己的套件，以確保發行的套件中沒有任何嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="a8ec4-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
