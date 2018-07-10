---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892394"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e6334-103">MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="e6334-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e6334-104">啟用 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="e6334-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6334-105">語法</span><span class="sxs-lookup"><span data-stu-id="e6334-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="e6334-106">參數</span><span class="sxs-lookup"><span data-stu-id="e6334-106">Parameters</span></span>

<span data-ttu-id="e6334-107">*BreakAll* \[in\] 在資源指令碼的每一行中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="e6334-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="e6334-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6334-108">Return value</span></span>

<span data-ttu-id="e6334-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e6334-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6334-110">備註</span><span class="sxs-lookup"><span data-stu-id="e6334-110">Remarks</span></span>

<span data-ttu-id="e6334-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="e6334-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6334-112">需求</span><span class="sxs-lookup"><span data-stu-id="e6334-112">Requirements</span></span>

<span data-ttu-id="e6334-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e6334-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e6334-114">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e6334-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e6334-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6334-115">See also</span></span>

[<span data-ttu-id="e6334-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e6334-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)