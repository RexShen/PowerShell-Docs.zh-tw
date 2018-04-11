---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="766be-103">MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="766be-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="766be-104">移除設定檔。</span><span class="sxs-lookup"><span data-stu-id="766be-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="766be-105">語法</span><span class="sxs-lookup"><span data-stu-id="766be-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="766be-106">參數</span><span class="sxs-lookup"><span data-stu-id="766be-106">Parameters</span></span>
----------

<span data-ttu-id="766be-107">*Stage* \[in\] 指定要移除的設定文件。</span><span class="sxs-lookup"><span data-stu-id="766be-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="766be-108">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="766be-108">The following values are valid:</span></span>

|<span data-ttu-id="766be-109">值</span><span class="sxs-lookup"><span data-stu-id="766be-109">Value</span></span> |<span data-ttu-id="766be-110">描述</span><span class="sxs-lookup"><span data-stu-id="766be-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="766be-111">**1**</span><span class="sxs-lookup"><span data-stu-id="766be-111">**1**</span></span> | <span data-ttu-id="766be-112">**目前的**設定文件 (current.mof)。</span><span class="sxs-lookup"><span data-stu-id="766be-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="766be-113">**2**</span><span class="sxs-lookup"><span data-stu-id="766be-113">**2**</span></span> | <span data-ttu-id="766be-114">**擱置中的**設定文件 (pending.mof)。</span><span class="sxs-lookup"><span data-stu-id="766be-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="766be-115">**4**</span><span class="sxs-lookup"><span data-stu-id="766be-115">**4**</span></span> | <span data-ttu-id="766be-116">**之前的**設定文件 (previous.mof)。</span><span class="sxs-lookup"><span data-stu-id="766be-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="766be-117">*Force* \[in\] **true** 表示強制移除設定。</span><span class="sxs-lookup"><span data-stu-id="766be-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="766be-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="766be-118">Return value</span></span>
------------

<span data-ttu-id="766be-119">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="766be-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="766be-120">備註</span><span class="sxs-lookup"><span data-stu-id="766be-120">Remarks</span></span>

<span data-ttu-id="766be-121">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="766be-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="766be-122">需求</span><span class="sxs-lookup"><span data-stu-id="766be-122">Requirements</span></span>
------------
><span data-ttu-id="766be-123">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="766be-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="766be-124">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="766be-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="766be-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="766be-125">See also</span></span>


[<span data-ttu-id="766be-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="766be-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)