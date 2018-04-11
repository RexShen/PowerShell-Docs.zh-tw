---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ab35f-103">MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="ab35f-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ab35f-104">啟用 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="ab35f-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="ab35f-105">語法</span><span class="sxs-lookup"><span data-stu-id="ab35f-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="ab35f-106">參數</span><span class="sxs-lookup"><span data-stu-id="ab35f-106">Parameters</span></span>
----------

<span data-ttu-id="ab35f-107">*BreakAll* \[in\] 在資源指令碼的每一行中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="ab35f-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="ab35f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="ab35f-108">Return value</span></span>
------------

<span data-ttu-id="ab35f-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ab35f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab35f-110">備註</span><span class="sxs-lookup"><span data-stu-id="ab35f-110">Remarks</span></span>

<span data-ttu-id="ab35f-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="ab35f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab35f-112">需求</span><span class="sxs-lookup"><span data-stu-id="ab35f-112">Requirements</span></span>
------------
><span data-ttu-id="ab35f-113">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ab35f-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ab35f-114">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab35f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ab35f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab35f-115">See also</span></span>


[<span data-ttu-id="ab35f-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ab35f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)