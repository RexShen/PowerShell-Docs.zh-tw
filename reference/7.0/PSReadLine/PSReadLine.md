---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113630
Help Version: 7.0.1.0
keywords: powershell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: e14d322fb2f964f06c064c1f9878dc3033947520
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "93206487"
---
# PSReadLine 模組

## 描述

PSReadLine 模組包含可讓您在 PowerShell 中自訂命令列編輯環境的 Cmdlet。 這些文章記載 PSReadLine v2.0。 此版本隨附于 PowerShell v6 和 Windows 10 2018 年10月更新 (組建 1809) 。

> [!NOTE]
> 從 PowerShell 7.0 開始，如果偵測到螢幕讀取程式，PowerShell 會略過在 Windows 上自動載入 PSReadLine。 PSReadLine 目前無法與螢幕讀取器順利搭配運作。 Windows 上 PowerShell 7.0 的預設轉譯和格式可正常運作。 如有必要，您可以手動載入模組。

## PSReadLine Cmdlet

### [PSConsoleHostReadLine](PSConsoleHostReadLine.md)
PSReadLine 的主要進入點。

### [PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)
取得 PSReadLine 模組的索引鍵系結。

### [PSReadLineOption](Get-PSReadLineOption.md)
取得可設定之選項的值。

### [PSConsoleHostReadLine](PSConsoleHostReadLine.md)
此函數是 PSReadLine 的主要進入點。

### [移除-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)
移除索引鍵系結。

### [設定-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)
將索引鍵系結至使用者定義或 PSReadLine 的索引鍵處理函式。

### [設定-PSReadLineOption](Set-PSReadLineOption.md)
自訂 **PSReadLine** 中的命令列編輯行為。

