---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: DSCAutomationHostEnabled 登錄機碼
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="0acae-103">適用對象：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0acae-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="0acae-104">DSCAutomationHostEnabled 登錄機碼</span><span class="sxs-lookup"><span data-stu-id="0acae-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="0acae-105">DSC 使用 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** 下的 **DSCAutomationHostEnabled** 登錄機碼，在初始開機時啟用電腦的設定。</span><span class="sxs-lookup"><span data-stu-id="0acae-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="0acae-106">DSCAutomationHostEnabled 支援三種模式︰</span><span class="sxs-lookup"><span data-stu-id="0acae-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="0acae-107">DSCAutomationHostEnabled 值</span><span class="sxs-lookup"><span data-stu-id="0acae-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="0acae-108">描述</span><span class="sxs-lookup"><span data-stu-id="0acae-108">Description</span></span>   |
|---|---|
<span data-ttu-id="0acae-109">0</span><span class="sxs-lookup"><span data-stu-id="0acae-109">0</span></span> | <span data-ttu-id="0acae-110">不允許在開機時設定電腦。</span><span class="sxs-lookup"><span data-stu-id="0acae-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="0acae-111">1</span><span class="sxs-lookup"><span data-stu-id="0acae-111">1</span></span> | <span data-ttu-id="0acae-112">允許在開機時設定電腦。</span><span class="sxs-lookup"><span data-stu-id="0acae-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="0acae-113">2</span><span class="sxs-lookup"><span data-stu-id="0acae-113">2</span></span> | <span data-ttu-id="0acae-114">僅當 DSC 處於暫止或目前的狀態時，才允許設定電腦。</span><span class="sxs-lookup"><span data-stu-id="0acae-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="0acae-115">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="0acae-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0acae-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0acae-116">See Also</span></span>

<span data-ttu-id="0acae-117">如需如何使用此功能在初始機時執行設定的範例，請參閱[使用 DSC 在初始開機時設定虛擬機器](bootstrapDsc.md)。</span><span class="sxs-lookup"><span data-stu-id="0acae-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>