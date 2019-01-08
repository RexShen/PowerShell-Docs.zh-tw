---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047455"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9ea28-103">MSFT_DSCLocalConfigurationManager 類別的 PerformRequiredConfigurationChecks 方法</span><span class="sxs-lookup"><span data-stu-id="9ea28-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9ea28-104">使用工作排程器開始一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="9ea28-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ea28-105">語法</span><span class="sxs-lookup"><span data-stu-id="9ea28-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="9ea28-106">參數</span><span class="sxs-lookup"><span data-stu-id="9ea28-106">Parameters</span></span>

<span data-ttu-id="9ea28-107">*Flags* \[in\] 位元遮罩，指定要執行的一致性檢查類型。</span><span class="sxs-lookup"><span data-stu-id="9ea28-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="9ea28-108">下列值有效，且可以透過位元 **OR** 運算進行結合︰</span><span class="sxs-lookup"><span data-stu-id="9ea28-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="9ea28-109">值</span><span class="sxs-lookup"><span data-stu-id="9ea28-109">Value</span></span> |<span data-ttu-id="9ea28-110">描述</span><span class="sxs-lookup"><span data-stu-id="9ea28-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="9ea28-111">**1**</span><span class="sxs-lookup"><span data-stu-id="9ea28-111">**1**</span></span> | <span data-ttu-id="9ea28-112">標準的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="9ea28-112">A normal consistency check.</span></span> |
|<span data-ttu-id="9ea28-113">**2**</span><span class="sxs-lookup"><span data-stu-id="9ea28-113">**2**</span></span> | <span data-ttu-id="9ea28-114">重新開機後持續的一致性檢查。</span><span class="sxs-lookup"><span data-stu-id="9ea28-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="9ea28-115">此值不應與其他值結合。</span><span class="sxs-lookup"><span data-stu-id="9ea28-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="9ea28-116">**4**</span><span class="sxs-lookup"><span data-stu-id="9ea28-116">**4**</span></span> | <span data-ttu-id="9ea28-117">應從節點中繼設定中所指定的提取伺服器，提取設定。</span><span class="sxs-lookup"><span data-stu-id="9ea28-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="9ea28-118">此值應一律使用 **5** 的值和 **1** 結合。</span><span class="sxs-lookup"><span data-stu-id="9ea28-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="9ea28-119">**8**</span><span class="sxs-lookup"><span data-stu-id="9ea28-119">**8**</span></span> | <span data-ttu-id="9ea28-120">將狀態傳送到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="9ea28-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="9ea28-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="9ea28-121">Return value</span></span>

<span data-ttu-id="9ea28-122">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="9ea28-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ea28-123">備註</span><span class="sxs-lookup"><span data-stu-id="9ea28-123">Remarks</span></span>

<span data-ttu-id="9ea28-124">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="9ea28-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ea28-125">需求</span><span class="sxs-lookup"><span data-stu-id="9ea28-125">Requirements</span></span>

<span data-ttu-id="9ea28-126">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9ea28-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9ea28-127">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9ea28-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9ea28-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ea28-128">See also</span></span>

[<span data-ttu-id="9ea28-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9ea28-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)