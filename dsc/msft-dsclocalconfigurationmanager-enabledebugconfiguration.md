---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法"
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4c3eb-103">MSFT_DSCLocalConfigurationManager 類別的 EnableDebugConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="4c3eb-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4c3eb-104">啟用 DSC 資源偵錯。</span><span class="sxs-lookup"><span data-stu-id="4c3eb-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="4c3eb-105">語法</span><span class="sxs-lookup"><span data-stu-id="4c3eb-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="4c3eb-106">參數</span><span class="sxs-lookup"><span data-stu-id="4c3eb-106">Parameters</span></span>
----------

<span data-ttu-id="4c3eb-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4c3eb-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="4c3eb-108">在資源指令碼的每一行中設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="4c3eb-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c3eb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4c3eb-109">Return value</span></span>
------------

<span data-ttu-id="4c3eb-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4c3eb-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c3eb-111">備註</span><span class="sxs-lookup"><span data-stu-id="4c3eb-111">Remarks</span></span>

<span data-ttu-id="4c3eb-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="4c3eb-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c3eb-113">需求</span><span class="sxs-lookup"><span data-stu-id="4c3eb-113">Requirements</span></span>
------------
><span data-ttu-id="4c3eb-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4c3eb-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4c3eb-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c3eb-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4c3eb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c3eb-116">See also</span></span>


[<span data-ttu-id="4c3eb-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4c3eb-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



