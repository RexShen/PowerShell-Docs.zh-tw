---
ms.date: 07/17/2020
ms.topic: reference
title: EnableDebugConfiguration 方法
description: EnableDebugConfiguration 方法
ms.openlocfilehash: 536366e6e1627a249f3bc2dc19bfd8ff3de42117
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644783"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="81ea4-103">EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="81ea4-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="81ea4-104">啟用 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="81ea4-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="81ea4-105">語法</span><span class="sxs-lookup"><span data-stu-id="81ea4-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="81ea4-106">參數</span><span class="sxs-lookup"><span data-stu-id="81ea4-106">Parameters</span></span>

<span data-ttu-id="81ea4-107">**BreakAll** \[in\] 在資源指令碼的每一行中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="81ea4-107">**BreakAll** \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="81ea4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="81ea4-108">Return value</span></span>

<span data-ttu-id="81ea4-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="81ea4-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="81ea4-110">備註</span><span class="sxs-lookup"><span data-stu-id="81ea4-110">Remarks</span></span>

<span data-ttu-id="81ea4-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="81ea4-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="81ea4-112">需求</span><span class="sxs-lookup"><span data-stu-id="81ea4-112">Requirements</span></span>

<span data-ttu-id="81ea4-113">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="81ea4-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="81ea4-114">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="81ea4-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="81ea4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81ea4-115">See also</span></span>

[<span data-ttu-id="81ea4-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="81ea4-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
