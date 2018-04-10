---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_scriptanalyzer_rule_profile
ms.openlocfilehash: ff575ab56f07312658d111bccd7793b64ac071ea
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a><span data-ttu-id="0f6c8-103">資源庫的 ScriptAnazlyer 規則設定檔</span><span class="sxs-lookup"><span data-stu-id="0f6c8-103">ScriptAnazlyer Rule Profile for Gallery</span></span>
<span data-ttu-id="0f6c8-104">為了確保發行至 PowerShell 資源庫的項目品質，我們會執行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 規則，判斷提交的指令碼中是否有任何違規。</span><span class="sxs-lookup"><span data-stu-id="0f6c8-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="0f6c8-105">您可以在 ScriptAnalyzer [GitHub 頁面](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1)找到我們所執行的規則清單。</span><span class="sxs-lookup"><span data-stu-id="0f6c8-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="0f6c8-106">如果您對我們執行的規則有任何疑慮，請連絡 PowerShell 資源庫系統管理員，或提出 ScriptAnalzyer 問題。</span><span class="sxs-lookup"><span data-stu-id="0f6c8-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="0f6c8-107">在之後的版本中，ScriptAnalyzer 結果將於資源庫的每個個別項目頁面中顯示。</span><span class="sxs-lookup"><span data-stu-id="0f6c8-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="0f6c8-108">建議項目擁有者檢查自己的項目，以確保發行的項目中沒有任何嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f6c8-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>