---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成"
ms.technology: powershell
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: f2eec644055c228dd1a16a2c20a09996666ca6e1
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>如何在指令碼窗格和主控台窗格中使用 TAB 鍵自動完成
Tab 鍵自動完成功能可以在您在 [指令碼窗格] 或 [命令窗格] 中輸入時，自動為您提供協助。 使用下列步驟以利用這項功能︰

## <a name="to-automatically-complete-a-command-entry"></a>自動完成命令項目
在命令窗格或指令碼窗格中，輸入命令的幾個字元，然後按 TAB 鍵選取所需的完成文字。 如果有多個項目以您初始輸入的文字為開頭，請連續按 TAB 鍵，直到出現您想要的項目。 TAB 鍵自動完成可協助輸入 Cmdlet 名稱、參數名稱、變數名稱、物件屬性名稱或檔案路徑。

> [!NOTE]
> 在指令碼窗格中，只有在編輯 .ps1、.psd1 或 .psm1 檔案時，按 TAB 鍵才會自動完成命令。 任何時候當您在命令窗格中輸入時，都可以使用 TAB 鍵自動完成。

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>自動完成 Cmdlet 參數項目
在命令窗格或指令碼窗格中輸入一個 Cmdlet，後面接著虛線，然後按 TAB 鍵。

例如，輸入 `Get-Process -`，然後按 TAB 鍵多次，輪流顯示 Cmdlet 的每個參數。

## <a name="see-also"></a>另請參閱
- [使用 Windows PowerShell ISE](using-the-windows-powershell-ise.md)
- [如何建立 PowerShell 索引標籤](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

