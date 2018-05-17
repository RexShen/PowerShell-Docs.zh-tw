---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: 資源庫的 ScriptAnazlyer 規則設定檔
ms.openlocfilehash: 22b95f0901fe95d5ad79df0e23e675ab52313fee
ms.sourcegitcommit: f8a37df92db22b9368469fb07378399b2ab90cea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2018
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>資源庫的 ScriptAnazlyer 規則設定檔

為了確保發行至 PowerShell 資源庫的項目品質，我們會執行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 規則，判斷提交的指令碼中是否有任何違規。

您可以在 ScriptAnalyzer [GitHub 頁面](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1)找到我們所執行的規則清單。
如果您對我們執行的規則有任何疑慮，請連絡 PowerShell 資源庫系統管理員，或提出 ScriptAnalzyer 問題。

在之後的版本中，ScriptAnalyzer 結果將於資源庫的每個個別項目頁面中顯示。 建議項目擁有者檢查自己的項目，以確保發行的項目中沒有任何嚴重錯誤。
