---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892679"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="62953-103">MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="62953-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="62953-104">移除設定檔。</span><span class="sxs-lookup"><span data-stu-id="62953-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="62953-105">語法</span><span class="sxs-lookup"><span data-stu-id="62953-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="62953-106">參數</span><span class="sxs-lookup"><span data-stu-id="62953-106">Parameters</span></span>

<span data-ttu-id="62953-107">*Stage* \[in\] 指定要移除的設定文件。</span><span class="sxs-lookup"><span data-stu-id="62953-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="62953-108">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="62953-108">The following values are valid:</span></span>

|<span data-ttu-id="62953-109">值</span><span class="sxs-lookup"><span data-stu-id="62953-109">Value</span></span> |<span data-ttu-id="62953-110">描述</span><span class="sxs-lookup"><span data-stu-id="62953-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="62953-111">**1**</span><span class="sxs-lookup"><span data-stu-id="62953-111">**1**</span></span> | <span data-ttu-id="62953-112">**目前的**設定文件 (current.mof)。</span><span class="sxs-lookup"><span data-stu-id="62953-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="62953-113">**2**</span><span class="sxs-lookup"><span data-stu-id="62953-113">**2**</span></span> | <span data-ttu-id="62953-114">**擱置中的**設定文件 (pending.mof)。</span><span class="sxs-lookup"><span data-stu-id="62953-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="62953-115">**4**</span><span class="sxs-lookup"><span data-stu-id="62953-115">**4**</span></span> | <span data-ttu-id="62953-116">**之前的**設定文件 (previous.mof)。</span><span class="sxs-lookup"><span data-stu-id="62953-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="62953-117">*Force* \[in\] **true** 表示強制移除設定。</span><span class="sxs-lookup"><span data-stu-id="62953-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="62953-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="62953-118">Return value</span></span>

<span data-ttu-id="62953-119">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="62953-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="62953-120">備註</span><span class="sxs-lookup"><span data-stu-id="62953-120">Remarks</span></span>

<span data-ttu-id="62953-121">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="62953-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="62953-122">需求</span><span class="sxs-lookup"><span data-stu-id="62953-122">Requirements</span></span>

<span data-ttu-id="62953-123">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="62953-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="62953-124">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="62953-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="62953-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62953-125">See also</span></span>

[<span data-ttu-id="62953-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="62953-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)