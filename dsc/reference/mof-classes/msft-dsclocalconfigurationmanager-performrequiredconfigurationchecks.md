---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: PerformRequiredConfigurationChecks 方法
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734399"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="4982b-103">PerformRequiredConfigurationChecks 方法</span><span class="sxs-lookup"><span data-stu-id="4982b-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="4982b-104">使用工作排程器開始一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="4982b-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="4982b-105">語法</span><span class="sxs-lookup"><span data-stu-id="4982b-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="4982b-106">參數</span><span class="sxs-lookup"><span data-stu-id="4982b-106">Parameters</span></span>

<span data-ttu-id="4982b-107">*Flags* \[in\] 位元遮罩，指定要執行的一致性檢查類型。</span><span class="sxs-lookup"><span data-stu-id="4982b-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="4982b-108">下列值有效，且可以透過位元 **OR** 運算進行結合︰</span><span class="sxs-lookup"><span data-stu-id="4982b-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="4982b-109">值</span><span class="sxs-lookup"><span data-stu-id="4982b-109">Value</span></span> |<span data-ttu-id="4982b-110">描述</span><span class="sxs-lookup"><span data-stu-id="4982b-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="4982b-111">**1**</span><span class="sxs-lookup"><span data-stu-id="4982b-111">**1**</span></span> | <span data-ttu-id="4982b-112">標準的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="4982b-112">A normal consistency check.</span></span> |
|<span data-ttu-id="4982b-113">**2**</span><span class="sxs-lookup"><span data-stu-id="4982b-113">**2**</span></span> | <span data-ttu-id="4982b-114">重新開機後持續的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="4982b-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="4982b-115">此值不應與其他值結合。</span><span class="sxs-lookup"><span data-stu-id="4982b-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="4982b-116">**4**</span><span class="sxs-lookup"><span data-stu-id="4982b-116">**4**</span></span> | <span data-ttu-id="4982b-117">應從節點中繼設定中所指定的提取伺服器，提取設定。</span><span class="sxs-lookup"><span data-stu-id="4982b-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="4982b-118">此值應一律使用 **5** 的值和 **1** 結合。</span><span class="sxs-lookup"><span data-stu-id="4982b-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="4982b-119">**8**</span><span class="sxs-lookup"><span data-stu-id="4982b-119">**8**</span></span> | <span data-ttu-id="4982b-120">將狀態傳送到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4982b-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="4982b-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="4982b-121">Return value</span></span>

<span data-ttu-id="4982b-122">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4982b-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4982b-123">備註</span><span class="sxs-lookup"><span data-stu-id="4982b-123">Remarks</span></span>

<span data-ttu-id="4982b-124">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="4982b-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4982b-125">需求</span><span class="sxs-lookup"><span data-stu-id="4982b-125">Requirements</span></span>

<span data-ttu-id="4982b-126">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4982b-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4982b-127">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4982b-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4982b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4982b-128">See also</span></span>

[<span data-ttu-id="4982b-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4982b-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
