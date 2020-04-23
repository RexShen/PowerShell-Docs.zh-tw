---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 資源庫的 ScriptAnazlyer 規則設定檔
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328469"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>資源庫的 ScriptAnazlyer 規則設定檔

為了確保發行至 PowerShell 資源庫的套件品質，我們會執行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 規則，判斷提交的指令碼中是否有任何違規。

您可以在 ScriptAnalyzer [GitHub 頁面](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1)找到我們所執行的規則清單。
如果您對我們執行的規則有任何疑慮，請連絡 PowerShell 資源庫管理員，或提出 ScriptAnalzyer 問題。

在之後的版本中，ScriptAnalyzer 結果將於資源庫的每個個別套件頁面中顯示。 建議套件擁有者檢查自己的套件，以確保發行的套件中沒有任何嚴重錯誤。
