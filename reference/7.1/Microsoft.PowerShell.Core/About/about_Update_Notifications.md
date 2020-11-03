---
description: 通知使用者啟動 PowerShell 時，已發行新版的 PowerShell。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 258eb9316ba063069d032bc115bdeb4614666f37
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208376"
---
# <a name="about-update-notifications"></a>關於更新通知

## <a name="short-description"></a>簡短描述

通知使用者啟動 PowerShell 時，已發行新版的 PowerShell。

## <a name="long-description"></a>詳細描述

從 PowerShell 7.0 開始，PowerShell 會使用更新通知來警示使用者是否存在 PowerShell 更新。 PowerShell 會以每天一次的頻率來查詢線上服務，以判斷是否有較新版本可供使用。

> [!NOTE]
> 雖然更新檢查會在指定的24小時期間發生于第一個會話期間，但基於效能的考慮，只有在後續的會話開始時，才會顯示通知。 此外，基於效能考慮，檢查將不會啟動，直到會話開始的時間至少為3秒。

根據預設，PowerShell 會依據其版本/分支，訂閱兩個不同通知通道的其中一個。 支援、正式推出 (GA) 的 PowerShell 版本只會傳回已更新 GA 版本的通知。 預覽和候選版 (RC) 版本會通知預覽、RC 和 GA 版本的更新。

更新通知行為可以使用 `POWERSHELL_UPDATECHECK` 環境變數來變更。 支援下列值：

- `Off` 關閉更新通知功能
- `Default` 與未定義相同 `POWERSHELL_UPDATECHECK` ：
  - GA 版本會通知 GA 版本的更新
  - 預覽/RC 版本會通知 GA 和預覽版本的更新
- `LTS` 只會通知長期維護 (LTS) GA 版本的更新

下列端點目前用來判斷每個通道的最新版本：

- `LTS`: https://aka.ms/pwsh-buildinfo-lts
- `Stable`: https://aka.ms/pwsh-buildinfo-stable
- `Preview`: https://aka.ms/pwsh-buildinfo-preview

更新通知不會提供任何自動更新 PowerShell 的方式。 未來，在 PowerShell 中可能會有更多的指示或功能更新，但現在，您應該使用您用來安裝 PowerShell 的相同安裝機制來更新它。

