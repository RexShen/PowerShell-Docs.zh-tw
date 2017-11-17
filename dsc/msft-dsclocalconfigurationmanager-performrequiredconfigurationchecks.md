---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法"
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="51f78-103">MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法</span><span class="sxs-lookup"><span data-stu-id="51f78-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="51f78-104">使用工作排程器開始一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="51f78-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="51f78-105">語法</span><span class="sxs-lookup"><span data-stu-id="51f78-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="51f78-106">參數</span><span class="sxs-lookup"><span data-stu-id="51f78-106">Parameters</span></span>
----------

<span data-ttu-id="51f78-107">*Flags* \[in\]</span><span class="sxs-lookup"><span data-stu-id="51f78-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="51f78-108">位元遮罩，指定要執行的一致性檢查類型。</span><span class="sxs-lookup"><span data-stu-id="51f78-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="51f78-109">下列值有效，且可以透過位元 **OR** 運算進行結合︰</span><span class="sxs-lookup"><span data-stu-id="51f78-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="51f78-110">值</span><span class="sxs-lookup"><span data-stu-id="51f78-110">Value</span></span> |<span data-ttu-id="51f78-111">描述</span><span class="sxs-lookup"><span data-stu-id="51f78-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="51f78-112">**1**</span><span class="sxs-lookup"><span data-stu-id="51f78-112">**1**</span></span> | <span data-ttu-id="51f78-113">標準的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="51f78-113">A normal consistency check.</span></span> |
|<span data-ttu-id="51f78-114">**2**</span><span class="sxs-lookup"><span data-stu-id="51f78-114">**2**</span></span> | <span data-ttu-id="51f78-115">重新開機後持續的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="51f78-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="51f78-116">此值不應與其他值結合。</span><span class="sxs-lookup"><span data-stu-id="51f78-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="51f78-117">**4**</span><span class="sxs-lookup"><span data-stu-id="51f78-117">**4**</span></span> | <span data-ttu-id="51f78-118">應從節點中繼設定中所指定的提取伺服器，提取設定。</span><span class="sxs-lookup"><span data-stu-id="51f78-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="51f78-119">此值應一律使用 **5** 的值和 **1** 結合。</span><span class="sxs-lookup"><span data-stu-id="51f78-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="51f78-120">**8**</span><span class="sxs-lookup"><span data-stu-id="51f78-120">**8**</span></span> | <span data-ttu-id="51f78-121">將狀態傳送到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="51f78-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="51f78-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="51f78-122">Return value</span></span>
------------

<span data-ttu-id="51f78-123">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="51f78-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="51f78-124">備註</span><span class="sxs-lookup"><span data-stu-id="51f78-124">Remarks</span></span>

<span data-ttu-id="51f78-125">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="51f78-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="51f78-126">需求</span><span class="sxs-lookup"><span data-stu-id="51f78-126">Requirements</span></span>
------------
><span data-ttu-id="51f78-127">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="51f78-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="51f78-128">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="51f78-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="51f78-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51f78-129">See also</span></span>


[<span data-ttu-id="51f78-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="51f78-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



