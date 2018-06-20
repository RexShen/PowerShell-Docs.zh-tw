---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189732"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a5f49-103">MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="a5f49-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a5f49-104">移除設定檔。</span><span class="sxs-lookup"><span data-stu-id="a5f49-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="a5f49-105">語法</span><span class="sxs-lookup"><span data-stu-id="a5f49-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="a5f49-106">參數</span><span class="sxs-lookup"><span data-stu-id="a5f49-106">Parameters</span></span>
----------

<span data-ttu-id="a5f49-107">*Stage* \[in\] 指定要移除的設定文件。</span><span class="sxs-lookup"><span data-stu-id="a5f49-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="a5f49-108">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="a5f49-108">The following values are valid:</span></span>

|<span data-ttu-id="a5f49-109">值</span><span class="sxs-lookup"><span data-stu-id="a5f49-109">Value</span></span> |<span data-ttu-id="a5f49-110">描述</span><span class="sxs-lookup"><span data-stu-id="a5f49-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="a5f49-111">**1**</span><span class="sxs-lookup"><span data-stu-id="a5f49-111">**1**</span></span> | <span data-ttu-id="a5f49-112">**目前的**設定文件 (current.mof)。</span><span class="sxs-lookup"><span data-stu-id="a5f49-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="a5f49-113">**2**</span><span class="sxs-lookup"><span data-stu-id="a5f49-113">**2**</span></span> | <span data-ttu-id="a5f49-114">**擱置中的**設定文件 (pending.mof)。</span><span class="sxs-lookup"><span data-stu-id="a5f49-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="a5f49-115">**4**</span><span class="sxs-lookup"><span data-stu-id="a5f49-115">**4**</span></span> | <span data-ttu-id="a5f49-116">**之前的**設定文件 (previous.mof)。</span><span class="sxs-lookup"><span data-stu-id="a5f49-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="a5f49-117">*Force* \[in\] **true** 表示強制移除設定。</span><span class="sxs-lookup"><span data-stu-id="a5f49-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a5f49-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="a5f49-118">Return value</span></span>
------------

<span data-ttu-id="a5f49-119">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a5f49-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5f49-120">備註</span><span class="sxs-lookup"><span data-stu-id="a5f49-120">Remarks</span></span>

<span data-ttu-id="a5f49-121">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="a5f49-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a5f49-122">需求</span><span class="sxs-lookup"><span data-stu-id="a5f49-122">Requirements</span></span>
------------
><span data-ttu-id="a5f49-123">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a5f49-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a5f49-124">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a5f49-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a5f49-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5f49-125">See also</span></span>


[<span data-ttu-id="a5f49-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a5f49-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)