---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678899"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d1ed5-103">MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法</span><span class="sxs-lookup"><span data-stu-id="d1ed5-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d1ed5-104">使用工作排程器開始一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1ed5-105">語法</span><span class="sxs-lookup"><span data-stu-id="d1ed5-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="d1ed5-106">參數</span><span class="sxs-lookup"><span data-stu-id="d1ed5-106">Parameters</span></span>

<span data-ttu-id="d1ed5-107">*Flags* \[in\] 位元遮罩，指定要執行的一致性檢查類型。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="d1ed5-108">下列值有效，且可以透過位元 **OR** 運算進行結合︰</span><span class="sxs-lookup"><span data-stu-id="d1ed5-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="d1ed5-109">值</span><span class="sxs-lookup"><span data-stu-id="d1ed5-109">Value</span></span> |<span data-ttu-id="d1ed5-110">描述</span><span class="sxs-lookup"><span data-stu-id="d1ed5-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="d1ed5-111">**1**</span><span class="sxs-lookup"><span data-stu-id="d1ed5-111">**1**</span></span> | <span data-ttu-id="d1ed5-112">標準的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-112">A normal consistency check.</span></span> |
|<span data-ttu-id="d1ed5-113">**2**</span><span class="sxs-lookup"><span data-stu-id="d1ed5-113">**2**</span></span> | <span data-ttu-id="d1ed5-114">重新開機後持續的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="d1ed5-115">此值不應與其他值結合。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="d1ed5-116">**4**</span><span class="sxs-lookup"><span data-stu-id="d1ed5-116">**4**</span></span> | <span data-ttu-id="d1ed5-117">應從節點中繼設定中所指定的提取伺服器，提取設定。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="d1ed5-118">此值應一律使用 **5** 的值和 **1** 結合。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="d1ed5-119">**8**</span><span class="sxs-lookup"><span data-stu-id="d1ed5-119">**8**</span></span> | <span data-ttu-id="d1ed5-120">將狀態傳送到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="d1ed5-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1ed5-121">Return value</span></span>

<span data-ttu-id="d1ed5-122">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1ed5-123">備註</span><span class="sxs-lookup"><span data-stu-id="d1ed5-123">Remarks</span></span>

<span data-ttu-id="d1ed5-124">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d1ed5-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d1ed5-125">需求</span><span class="sxs-lookup"><span data-stu-id="d1ed5-125">Requirements</span></span>

<span data-ttu-id="d1ed5-126">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d1ed5-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d1ed5-127">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d1ed5-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d1ed5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1ed5-128">See also</span></span>

[<span data-ttu-id="d1ed5-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d1ed5-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)