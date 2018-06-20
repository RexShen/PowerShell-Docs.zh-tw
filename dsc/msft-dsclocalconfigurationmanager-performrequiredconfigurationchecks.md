---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186689"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5a9cf-103">MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法</span><span class="sxs-lookup"><span data-stu-id="5a9cf-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5a9cf-104">使用工作排程器開始一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="5a9cf-105">語法</span><span class="sxs-lookup"><span data-stu-id="5a9cf-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="5a9cf-106">參數</span><span class="sxs-lookup"><span data-stu-id="5a9cf-106">Parameters</span></span>
----------

<span data-ttu-id="5a9cf-107">*Flags* \[in\] 位元遮罩，指定要執行的一致性檢查類型。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="5a9cf-108">下列值有效，且可以透過位元 **OR** 運算進行結合︰</span><span class="sxs-lookup"><span data-stu-id="5a9cf-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="5a9cf-109">值</span><span class="sxs-lookup"><span data-stu-id="5a9cf-109">Value</span></span> |<span data-ttu-id="5a9cf-110">描述</span><span class="sxs-lookup"><span data-stu-id="5a9cf-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="5a9cf-111">**1**</span><span class="sxs-lookup"><span data-stu-id="5a9cf-111">**1**</span></span> | <span data-ttu-id="5a9cf-112">標準的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-112">A normal consistency check.</span></span> |
|<span data-ttu-id="5a9cf-113">**2**</span><span class="sxs-lookup"><span data-stu-id="5a9cf-113">**2**</span></span> | <span data-ttu-id="5a9cf-114">重新開機後持續的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="5a9cf-115">此值不應與其他值結合。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="5a9cf-116">**4**</span><span class="sxs-lookup"><span data-stu-id="5a9cf-116">**4**</span></span> | <span data-ttu-id="5a9cf-117">應從節點中繼設定中所指定的提取伺服器，提取設定。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="5a9cf-118">此值應一律使用 **5** 的值和 **1** 結合。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="5a9cf-119">**8**</span><span class="sxs-lookup"><span data-stu-id="5a9cf-119">**8**</span></span> | <span data-ttu-id="5a9cf-120">將狀態傳送到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="5a9cf-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="5a9cf-121">Return value</span></span>
------------

<span data-ttu-id="5a9cf-122">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a9cf-123">備註</span><span class="sxs-lookup"><span data-stu-id="5a9cf-123">Remarks</span></span>

<span data-ttu-id="5a9cf-124">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="5a9cf-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a9cf-125">需求</span><span class="sxs-lookup"><span data-stu-id="5a9cf-125">Requirements</span></span>
------------
><span data-ttu-id="5a9cf-126">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5a9cf-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5a9cf-127">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a9cf-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5a9cf-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a9cf-128">See also</span></span>


[<span data-ttu-id="5a9cf-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5a9cf-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)