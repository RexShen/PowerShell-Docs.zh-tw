---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078754"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8e1d3-103">MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="8e1d3-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8e1d3-104">啟用 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="8e1d3-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e1d3-105">語法</span><span class="sxs-lookup"><span data-stu-id="8e1d3-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="8e1d3-106">參數</span><span class="sxs-lookup"><span data-stu-id="8e1d3-106">Parameters</span></span>

<span data-ttu-id="8e1d3-107">*BreakAll* \[in\] 在資源指令碼的每一行中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="8e1d3-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="8e1d3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e1d3-108">Return value</span></span>

<span data-ttu-id="8e1d3-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8e1d3-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e1d3-110">備註</span><span class="sxs-lookup"><span data-stu-id="8e1d3-110">Remarks</span></span>

<span data-ttu-id="8e1d3-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="8e1d3-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8e1d3-112">需求</span><span class="sxs-lookup"><span data-stu-id="8e1d3-112">Requirements</span></span>

<span data-ttu-id="8e1d3-113">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8e1d3-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8e1d3-114">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8e1d3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8e1d3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e1d3-115">See also</span></span>

[<span data-ttu-id="8e1d3-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8e1d3-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)