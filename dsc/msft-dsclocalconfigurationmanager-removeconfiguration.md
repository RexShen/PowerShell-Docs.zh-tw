---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="02648-103">MSFT_DSCLocalConfigurationManager 類別的 RemoveConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="02648-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="02648-104">移除設定檔。</span><span class="sxs-lookup"><span data-stu-id="02648-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="02648-105">語法</span><span class="sxs-lookup"><span data-stu-id="02648-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="02648-106">參數</span><span class="sxs-lookup"><span data-stu-id="02648-106">Parameters</span></span>
----------

<span data-ttu-id="02648-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="02648-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="02648-108">指定要移除的設定文件。</span><span class="sxs-lookup"><span data-stu-id="02648-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="02648-109">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="02648-109">The following values are valid:</span></span>

|<span data-ttu-id="02648-110">值</span><span class="sxs-lookup"><span data-stu-id="02648-110">Value</span></span> |<span data-ttu-id="02648-111">描述</span><span class="sxs-lookup"><span data-stu-id="02648-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="02648-112">**1**</span><span class="sxs-lookup"><span data-stu-id="02648-112">**1**</span></span> | <span data-ttu-id="02648-113">**目前的**設定文件 (current.mof)。</span><span class="sxs-lookup"><span data-stu-id="02648-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="02648-114">**2**</span><span class="sxs-lookup"><span data-stu-id="02648-114">**2**</span></span> | <span data-ttu-id="02648-115">**擱置中的**設定文件 (pending.mof)。</span><span class="sxs-lookup"><span data-stu-id="02648-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="02648-116">**4**</span><span class="sxs-lookup"><span data-stu-id="02648-116">**4**</span></span> | <span data-ttu-id="02648-117">**之前的**設定文件 (previous.mof)。</span><span class="sxs-lookup"><span data-stu-id="02648-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="02648-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="02648-118">*Force* \[in\]</span></span>  
<span data-ttu-id="02648-119">**true** 表示強制移除設定。</span><span class="sxs-lookup"><span data-stu-id="02648-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="02648-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="02648-120">Return value</span></span>
------------

<span data-ttu-id="02648-121">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="02648-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="02648-122">備註</span><span class="sxs-lookup"><span data-stu-id="02648-122">Remarks</span></span>

<span data-ttu-id="02648-123">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="02648-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="02648-124">需求</span><span class="sxs-lookup"><span data-stu-id="02648-124">Requirements</span></span>
------------
><span data-ttu-id="02648-125">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="02648-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="02648-126">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="02648-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="02648-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02648-127">See also</span></span>


[<span data-ttu-id="02648-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="02648-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



