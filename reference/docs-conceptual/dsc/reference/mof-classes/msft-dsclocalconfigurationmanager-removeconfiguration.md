---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: RemoveConfiguration 方法
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953395"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="55973-103">RemoveConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="55973-103">RemoveConfiguration method</span></span>

<span data-ttu-id="55973-104">移除設定檔。</span><span class="sxs-lookup"><span data-stu-id="55973-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="55973-105">語法</span><span class="sxs-lookup"><span data-stu-id="55973-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="55973-106">參數</span><span class="sxs-lookup"><span data-stu-id="55973-106">Parameters</span></span>

<span data-ttu-id="55973-107">*Stage* \[in\] 指定要移除的設定文件。</span><span class="sxs-lookup"><span data-stu-id="55973-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="55973-108">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="55973-108">The following values are valid:</span></span>

|<span data-ttu-id="55973-109">值</span><span class="sxs-lookup"><span data-stu-id="55973-109">Value</span></span> |<span data-ttu-id="55973-110">描述</span><span class="sxs-lookup"><span data-stu-id="55973-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="55973-111">**1**</span><span class="sxs-lookup"><span data-stu-id="55973-111">**1**</span></span> | <span data-ttu-id="55973-112">**目前的**設定文件 (current.mof)。</span><span class="sxs-lookup"><span data-stu-id="55973-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="55973-113">**2**</span><span class="sxs-lookup"><span data-stu-id="55973-113">**2**</span></span> | <span data-ttu-id="55973-114">**擱置中的**設定文件 (pending.mof)。</span><span class="sxs-lookup"><span data-stu-id="55973-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="55973-115">**4**</span><span class="sxs-lookup"><span data-stu-id="55973-115">**4**</span></span> | <span data-ttu-id="55973-116">**之前的**設定文件 (previous.mof)。</span><span class="sxs-lookup"><span data-stu-id="55973-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="55973-117">*Force* \[in\] **true** 表示強制移除設定。</span><span class="sxs-lookup"><span data-stu-id="55973-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="55973-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="55973-118">Return value</span></span>

<span data-ttu-id="55973-119">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="55973-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="55973-120">備註</span><span class="sxs-lookup"><span data-stu-id="55973-120">Remarks</span></span>

<span data-ttu-id="55973-121">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="55973-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="55973-122">需求</span><span class="sxs-lookup"><span data-stu-id="55973-122">Requirements</span></span>

<span data-ttu-id="55973-123">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="55973-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="55973-124">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="55973-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="55973-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55973-125">See also</span></span>

[<span data-ttu-id="55973-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="55973-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
