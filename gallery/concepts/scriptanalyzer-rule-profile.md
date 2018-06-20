---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 資源庫的 ScriptAnazlyer 規則設定檔
ms.openlocfilehash: 54100f7a530cbc769e4a0e2dbff18dbc5de88fa6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225737"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="019b9-103">資源庫的 ScriptAnazlyer 規則設定檔</span><span class="sxs-lookup"><span data-stu-id="019b9-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="019b9-104">為了確保發行至 PowerShell 資源庫的項目品質，我們會執行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 規則，判斷提交的指令碼中是否有任何違規。</span><span class="sxs-lookup"><span data-stu-id="019b9-104">To ensure the quality of items published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="019b9-105">您可以在 ScriptAnalyzer [GitHub 頁面](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1)找到我們所執行的規則清單。</span><span class="sxs-lookup"><span data-stu-id="019b9-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="019b9-106">如果您對我們執行的規則有任何疑慮，請連絡 PowerShell 資源庫系統管理員，或提出 ScriptAnalzyer 問題。</span><span class="sxs-lookup"><span data-stu-id="019b9-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="019b9-107">在之後的版本中，ScriptAnalyzer 結果將於資源庫的每個個別項目頁面中顯示。</span><span class="sxs-lookup"><span data-stu-id="019b9-107">ScriptAnalyzer results will be displayed on each individual item page in Gallery in the coming release.</span></span> <span data-ttu-id="019b9-108">建議項目擁有者檢查自己的項目，以確保發行的項目中沒有任何嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="019b9-108">We encourage item owners to check their items to make sure there are no severe errors in published items.</span></span>
