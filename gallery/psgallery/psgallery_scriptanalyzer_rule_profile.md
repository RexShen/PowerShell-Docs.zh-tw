---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell,cmdlet,組件庫"
ms.date: 2016-10-14
contributor: manikb
title: psgallery_scriptanalyzer_rule_profile
ms.technology: powershell
ms.openlocfilehash: 3274b66203044c0ed9fc1135cea7472428eb753e
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="scriptanazlyer-rule-profile-for-gallery"></a>資源庫的 ScriptAnazlyer 規則設定檔
為了確保發行至 PowerShell 資源庫的項目品質，我們會執行 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) 規則，判斷提交的指令碼中是否有任何違規。

您可以在 ScriptAnalyzer [GitHub 頁面](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1)找到我們所執行的規則清單。
如果您對我們執行的規則有任何疑慮，請連絡 PowerShell 資源庫系統管理員，或提出 ScriptAnalzyer 問題。

在之後的版本中，ScriptAnalyzer 結果將於資源庫的每個個別項目頁面中顯示。 建議項目擁有者檢查自己的項目，以確保發行的項目中沒有任何嚴重錯誤。

