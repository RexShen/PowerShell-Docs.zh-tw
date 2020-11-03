---
description: 描述 PowerShell 中收集的遙測資料，以及如何退出。
keywords: powershell
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: 4aeab828d66d1f015946051419facd81ce2b78c1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206552"
---
# <a name="about-telemetry"></a><span data-ttu-id="2658a-104">關於遙測</span><span class="sxs-lookup"><span data-stu-id="2658a-104">About Telemetry</span></span>

## <a name="short-description"></a><span data-ttu-id="2658a-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="2658a-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="2658a-106">描述 PowerShell 中收集的遙測資料，以及如何退出。</span><span class="sxs-lookup"><span data-stu-id="2658a-106">Describes the telemetry collected in PowerShell and how to opt-out.</span></span>

## <a name="long-description"></a><span data-ttu-id="2658a-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="2658a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="2658a-108">PowerShell 會將基本遙測資料傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="2658a-108">PowerShell sends basic telemetry data to Microsoft.</span></span>
<span data-ttu-id="2658a-109">這項資料可讓我們更加了解使用 PowerShell 的環境，並讓我們排列新功能和修正的優先順序。</span><span class="sxs-lookup"><span data-stu-id="2658a-109">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>
<span data-ttu-id="2658a-110">記錄的遙測資料點如下：</span><span class="sxs-lookup"><span data-stu-id="2658a-110">The following telemetry points are recorded:</span></span>

- <span data-ttu-id="2658a-111">PowerShell 的計數會以類型 (API 與主控台) </span><span class="sxs-lookup"><span data-stu-id="2658a-111">Count of PowerShell Starts by type (API vs console)</span></span>
- <span data-ttu-id="2658a-112">唯一 PowerShell 使用量的計數</span><span class="sxs-lookup"><span data-stu-id="2658a-112">Count of unique PowerShell usage</span></span>
- <span data-ttu-id="2658a-113">下列執行類型的計數：</span><span class="sxs-lookup"><span data-stu-id="2658a-113">Count of the following execution types:</span></span>
  - <span data-ttu-id="2658a-114">應用程式 (原生命令) </span><span class="sxs-lookup"><span data-stu-id="2658a-114">Application (native commands)</span></span>
  - <span data-ttu-id="2658a-115">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="2658a-115">ExternalScript</span></span>
  - <span data-ttu-id="2658a-116">指令碼</span><span class="sxs-lookup"><span data-stu-id="2658a-116">Script</span></span>
  - <span data-ttu-id="2658a-117">函式</span><span class="sxs-lookup"><span data-stu-id="2658a-117">Function</span></span>
  - <span data-ttu-id="2658a-118">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2658a-118">Cmdlet</span></span>
- <span data-ttu-id="2658a-119">PowerShell 隨附的已啟用 Microsoft 擁有實驗性功能或實驗性功能計數</span><span class="sxs-lookup"><span data-stu-id="2658a-119">Count of enabled Microsoft owned experimental features or experimental features shipped with PowerShell</span></span>
- <span data-ttu-id="2658a-120">託管會話的計數</span><span class="sxs-lookup"><span data-stu-id="2658a-120">Count of hosted sessions</span></span>
- <span data-ttu-id="2658a-121">已載入的 Microsoft 擁有模組計數</span><span class="sxs-lookup"><span data-stu-id="2658a-121">Count of Microsoft owned modules loaded</span></span>

<span data-ttu-id="2658a-122">此資料包含 OS 名稱、作業系統版本、PowerShell 版本和散發通道。</span><span class="sxs-lookup"><span data-stu-id="2658a-122">This data includes the OS name, OS version, the PowerShell version, and the distribution channel.</span></span>

<span data-ttu-id="2658a-123">若要退出此遙測，請將環境變數 POWERSHELL_TELEMETRY_OPTOUT 設定為 [true]、[是] 或1。</span><span class="sxs-lookup"><span data-stu-id="2658a-123">To opt-out of this telemetry, set the environment variable POWERSHELL_TELEMETRY_OPTOUT to true, yes, or 1.</span></span>
