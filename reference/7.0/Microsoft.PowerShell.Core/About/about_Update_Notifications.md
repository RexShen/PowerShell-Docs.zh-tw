---
description: 通知使用者啟動 PowerShell 時，已發行新版的 PowerShell。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: ea6b768ef62679ee039b156b72e69a7ba240389f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207491"
---
# <a name="about-update-notifications"></a><span data-ttu-id="a6028-104">關於更新通知</span><span class="sxs-lookup"><span data-stu-id="a6028-104">About Update Notifications</span></span>

## <a name="short-description"></a><span data-ttu-id="a6028-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="a6028-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="a6028-106">通知使用者啟動 PowerShell 時，已發行新版的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="a6028-106">Notifies users on startup of PowerShell that a new version of PowerShell has been released.</span></span>

## <a name="long-description"></a><span data-ttu-id="a6028-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="a6028-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a6028-108">從 PowerShell 7.0 開始，PowerShell 會使用更新通知來警示使用者是否存在 PowerShell 更新。</span><span class="sxs-lookup"><span data-stu-id="a6028-108">Beginning with PowerShell 7.0, PowerShell uses update notifications to alert users to the existence of updates to PowerShell.</span></span> <span data-ttu-id="a6028-109">PowerShell 會以每天一次的頻率來查詢線上服務，以判斷是否有較新版本可供使用。</span><span class="sxs-lookup"><span data-stu-id="a6028-109">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="a6028-110">雖然更新檢查會在指定的24小時期間發生于第一個會話期間，但基於效能的考慮，只有在後續的會話開始時，才會顯示通知。</span><span class="sxs-lookup"><span data-stu-id="a6028-110">While the update check happens during the first session in a given 24-hour period, for performance reasons, the notification will only be shown on the start of subsequent sessions.</span></span> <span data-ttu-id="a6028-111">此外，基於效能考慮，檢查將不會啟動，直到會話開始的時間至少為3秒。</span><span class="sxs-lookup"><span data-stu-id="a6028-111">Also for performance reasons, the check will not start until at least 3 seconds after the session begins.</span></span>

<span data-ttu-id="a6028-112">根據預設，PowerShell 會依據其版本/分支，訂閱兩個不同通知通道的其中一個。</span><span class="sxs-lookup"><span data-stu-id="a6028-112">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="a6028-113">支援、正式推出 (GA) 的 PowerShell 版本只會傳回已更新 GA 版本的通知。</span><span class="sxs-lookup"><span data-stu-id="a6028-113">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="a6028-114">預覽和候選版 (RC) 版本會通知預覽、RC 和 GA 版本的更新。</span><span class="sxs-lookup"><span data-stu-id="a6028-114">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="a6028-115">更新通知行為可以使用 `POWERSHELL_UPDATECHECK` 環境變數來變更。</span><span class="sxs-lookup"><span data-stu-id="a6028-115">The update notification behavior can be changed using the `POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="a6028-116">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="a6028-116">The following values are supported:</span></span>

- <span data-ttu-id="a6028-117">`Off` 關閉更新通知功能</span><span class="sxs-lookup"><span data-stu-id="a6028-117">`Off` turns off the update notification feature</span></span>
- <span data-ttu-id="a6028-118">`Default` 與未定義相同 `POWERSHELL_UPDATECHECK` ：</span><span class="sxs-lookup"><span data-stu-id="a6028-118">`Default` is the same as not defining `POWERSHELL_UPDATECHECK`:</span></span>
  - <span data-ttu-id="a6028-119">GA 版本會通知 GA 版本的更新</span><span class="sxs-lookup"><span data-stu-id="a6028-119">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="a6028-120">預覽/RC 版本會通知 GA 和預覽版本的更新</span><span class="sxs-lookup"><span data-stu-id="a6028-120">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="a6028-121">`LTS` 只會通知長期維護 (LTS) GA 版本的更新</span><span class="sxs-lookup"><span data-stu-id="a6028-121">`LTS` only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

<span data-ttu-id="a6028-122">下列端點目前用來判斷每個通道的最新版本：</span><span class="sxs-lookup"><span data-stu-id="a6028-122">The following endpoints are currently used for determining the latest version of each channel:</span></span>

- <span data-ttu-id="a6028-123">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span><span class="sxs-lookup"><span data-stu-id="a6028-123">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span></span>
- <span data-ttu-id="a6028-124">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span><span class="sxs-lookup"><span data-stu-id="a6028-124">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span></span>
- <span data-ttu-id="a6028-125">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span><span class="sxs-lookup"><span data-stu-id="a6028-125">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span></span>

<span data-ttu-id="a6028-126">更新通知不會提供任何自動更新 PowerShell 的方式。</span><span class="sxs-lookup"><span data-stu-id="a6028-126">The update notification doesn't provide any way to automatically update PowerShell.</span></span> <span data-ttu-id="a6028-127">未來，在 PowerShell 中可能會有更多的指示或功能更新，但現在，您應該使用您用來安裝 PowerShell 的相同安裝機制來更新它。</span><span class="sxs-lookup"><span data-stu-id="a6028-127">In the future, there may be more instructions or capabilities to update from within PowerShell, but today, you should use the same install mechanism you used to install PowerShell to update it.</span></span>
