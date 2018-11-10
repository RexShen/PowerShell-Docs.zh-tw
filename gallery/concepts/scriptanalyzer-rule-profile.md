---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 資源庫的 ScriptAnazlyer 規則設定檔
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002491"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="1a9d7-103">資源庫的 ScriptAnazlyer 規則設定檔</span><span class="sxs-lookup"><span data-stu-id="1a9d7-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="1a9d7-104">為了確保發行至 PowerShell 資源庫的套件品質，我們會執行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 規則，判斷提交的指令碼中是否有任何違規。</span><span class="sxs-lookup"><span data-stu-id="1a9d7-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="1a9d7-105">您可以在 ScriptAnalyzer [GitHub 頁面](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1)找到我們所執行的規則清單。</span><span class="sxs-lookup"><span data-stu-id="1a9d7-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="1a9d7-106">如果您對我們執行的規則有任何疑慮，請連絡 PowerShell 資源庫系統管理員，或提出 ScriptAnalzyer 問題。</span><span class="sxs-lookup"><span data-stu-id="1a9d7-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="1a9d7-107">在之後的版本中，ScriptAnalyzer 結果將於資源庫的每個個別套件頁面中顯示。</span><span class="sxs-lookup"><span data-stu-id="1a9d7-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="1a9d7-108">建議套件擁有者檢查自己的套件，以確保發行的套件中沒有任何嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a9d7-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
