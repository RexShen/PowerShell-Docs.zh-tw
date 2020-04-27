---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: EnableDebugConfiguration 方法
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953435"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="f2207-103">EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="f2207-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="f2207-104">啟用 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="f2207-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2207-105">語法</span><span class="sxs-lookup"><span data-stu-id="f2207-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="f2207-106">參數</span><span class="sxs-lookup"><span data-stu-id="f2207-106">Parameters</span></span>

<span data-ttu-id="f2207-107">*BreakAll* \[in\] 在資源指令碼的每一行中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="f2207-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="f2207-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f2207-108">Return value</span></span>

<span data-ttu-id="f2207-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="f2207-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2207-110">備註</span><span class="sxs-lookup"><span data-stu-id="f2207-110">Remarks</span></span>

<span data-ttu-id="f2207-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="f2207-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2207-112">需求</span><span class="sxs-lookup"><span data-stu-id="f2207-112">Requirements</span></span>

<span data-ttu-id="f2207-113">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f2207-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f2207-114">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2207-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f2207-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2207-115">See also</span></span>

[<span data-ttu-id="f2207-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f2207-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
