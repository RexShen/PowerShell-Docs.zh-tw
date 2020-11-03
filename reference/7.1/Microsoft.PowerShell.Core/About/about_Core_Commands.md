---
description: 列出專為搭配 PowerShell 提供者使用而設計的 Cmdlet。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 90723e286c3cc85a9ae9196721f3c0c6909d62ab
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207348"
---
# <a name="about-core-commands"></a>關於核心命令

## <a name="short-description"></a>簡短描述
列出專為搭配 PowerShell 提供者使用而設計的 Cmdlet。

## <a name="long-description"></a>詳細描述

PowerShell 包含一組 Cmdlet，專門設計來管理 PowerShell 提供者所公開之資料存放區中的專案。
您可以用相同的方式使用這些 Cmdlet 來管理提供者提供給您的所有不同資料類型。 如需提供者的詳細資訊，請輸入 "get-help about_providers"。

例如，您可以使用 Get-ChildItem Cmdlet 列出檔案系統目錄中的檔案、登錄機碼底下的機碼，或您撰寫或下載的提供者所公開的專案。

以下是專為與提供者搭配使用而設計的 PowerShell Cmdlet 清單：

Get-childitem Cmdlet

- Get-ChildItem

Content Cmdlet

- Add-Content
- Clear-Content
- Get-Content
- Set-Content

Item Cmdlet

- Clear-Item
- Copy-Item
- Get-Item
- Invoke-Item
- Move-Item
- New-Item
- Remove-Item
- Rename-Item
- Set-Item

ItemProperty Cmdlet

- Clear-ItemProperty
- Copy-ItemProperty
- Get-ItemProperty
- Move-ItemProperty
- New-ItemProperty
- Remove-ItemProperty
- Rename-ItemProperty
- Set-ItemProperty

Location Cmdlet

- Get-Location
- Pop-Location
- Push-Location
- Set-Location

路徑 Cmdlet

- Join-Path
- Convert-Path
- Split-Path
- Resolve-Path
- Test-Path

New-psdrive Cmdlet

- Get-PSDrive
- New-PSDrive
- Remove-PSDrive

PSProvider Cmdlet

- Get-PSProvider

如需有關 Cmdlet 的詳細資訊，請輸入 `get-help <cmdlet-name>` 。

## <a name="see-also"></a>另請參閱

[about_Providers](about_Providers.md)

