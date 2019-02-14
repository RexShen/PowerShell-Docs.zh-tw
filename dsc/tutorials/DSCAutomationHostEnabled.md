---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSCAutomationHostEnabled 登錄機碼
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676682"
---
><span data-ttu-id="63284-103">適用對象：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="63284-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="63284-104">DSCAutomationHostEnabled 登錄機碼</span><span class="sxs-lookup"><span data-stu-id="63284-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="63284-105">使用 DSC **DSCAutomationHostEnabled**登錄機碼下的**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System**啟用初始的機器組態啟動。</span><span class="sxs-lookup"><span data-stu-id="63284-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="63284-106">**DSCAutomationHostEnabled** 支援三個模式：</span><span class="sxs-lookup"><span data-stu-id="63284-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="63284-107">DSCAutomationHostEnabled 值</span><span class="sxs-lookup"><span data-stu-id="63284-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="63284-108">描述</span><span class="sxs-lookup"><span data-stu-id="63284-108">Description</span></span>   |
|---|---|
<span data-ttu-id="63284-109">0</span><span class="sxs-lookup"><span data-stu-id="63284-109">0</span></span> | <span data-ttu-id="63284-110">不允許在開機時設定電腦。</span><span class="sxs-lookup"><span data-stu-id="63284-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="63284-111">1</span><span class="sxs-lookup"><span data-stu-id="63284-111">1</span></span> | <span data-ttu-id="63284-112">允許在開機時設定電腦。</span><span class="sxs-lookup"><span data-stu-id="63284-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="63284-113">2</span><span class="sxs-lookup"><span data-stu-id="63284-113">2</span></span> | <span data-ttu-id="63284-114">僅當 DSC 處於暫止或目前的狀態時，才允許設定電腦。</span><span class="sxs-lookup"><span data-stu-id="63284-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="63284-115">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="63284-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="63284-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63284-116">See Also</span></span>

<span data-ttu-id="63284-117">如需如何使用此功能在初始機時執行設定的範例，請參閱[使用 DSC 在初始開機時設定虛擬機器](bootstrapDsc.md)。</span><span class="sxs-lookup"><span data-stu-id="63284-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
