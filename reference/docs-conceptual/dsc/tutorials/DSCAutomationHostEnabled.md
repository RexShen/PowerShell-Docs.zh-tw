---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSCAutomationHostEnabled 登錄機碼
description: 此文章定義可在 DSCAutomationHostEnabled 登錄機碼中設定的值
ms.openlocfilehash: 50f752dd882e9b0787ed4a4cbc22731fc1d608f5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656189"
---
# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="4d987-104">DSCAutomationHostEnabled 登錄機碼</span><span class="sxs-lookup"><span data-stu-id="4d987-104">DSCAutomationHostEnabled registry key</span></span>

> <span data-ttu-id="4d987-105">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4d987-105">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4d987-106">DSC 使用 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** 下的 **DSCAutomationHostEnabled** 登錄機碼，在初始開機時啟用電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="4d987-106">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span> <span data-ttu-id="4d987-107">**DSCAutomationHostEnabled** 支援三個模式：</span><span class="sxs-lookup"><span data-stu-id="4d987-107">**DSCAutomationHostEnabled** supports three modes:</span></span>

| <span data-ttu-id="4d987-108">DSCAutomationHostEnabled 值</span><span class="sxs-lookup"><span data-stu-id="4d987-108">DSCAutomationHostEnabled Value</span></span> |                                              <span data-ttu-id="4d987-109">描述</span><span class="sxs-lookup"><span data-stu-id="4d987-109">Description</span></span>                                              |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="4d987-110">0</span><span class="sxs-lookup"><span data-stu-id="4d987-110">0</span></span>                              | <span data-ttu-id="4d987-111">不允許在開機時設定電腦。</span><span class="sxs-lookup"><span data-stu-id="4d987-111">Disable configuring the machine at boot-up.</span></span>                                                           |
| <span data-ttu-id="4d987-112">1</span><span class="sxs-lookup"><span data-stu-id="4d987-112">1</span></span>                              | <span data-ttu-id="4d987-113">允許在開機時設定電腦。</span><span class="sxs-lookup"><span data-stu-id="4d987-113">Enable configuring the machine at boot-up.</span></span>                                                            |
| <span data-ttu-id="4d987-114">2</span><span class="sxs-lookup"><span data-stu-id="4d987-114">2</span></span>                              | <span data-ttu-id="4d987-115">僅當 DSC 處於暫止或目前的狀態時，才允許設定電腦。</span><span class="sxs-lookup"><span data-stu-id="4d987-115">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="4d987-116">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4d987-116">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="4d987-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d987-117">See Also</span></span>

<span data-ttu-id="4d987-118">如需如何使用此功能在初始機時執行設定的範例，請參閱[使用 DSC 在初始開機時設定虛擬機器](bootstrapDsc.md)。</span><span class="sxs-lookup"><span data-stu-id="4d987-118">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
