---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 TestConfiguration 方法"
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="781fa-103">MSFT_DSCLocalConfigurationManager 類別的 TestConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="781fa-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="781fa-104">將設定文件傳送到受管理的節點，並對文件驗證目前的設定。</span><span class="sxs-lookup"><span data-stu-id="781fa-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="781fa-105">語法</span><span class="sxs-lookup"><span data-stu-id="781fa-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="781fa-106">參數</span><span class="sxs-lookup"><span data-stu-id="781fa-106">Parameters</span></span>
----------

<span data-ttu-id="781fa-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="781fa-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="781fa-108">設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="781fa-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="781fa-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="781fa-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="781fa-110">傳回時，指定受管理的節點是否為設定文件所指定的狀態。</span><span class="sxs-lookup"><span data-stu-id="781fa-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="781fa-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="781fa-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="781fa-112">傳回時，包含指定資源為所需狀態之 **MSFT_ResourceInDesiredState** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="781fa-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="781fa-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="781fa-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="781fa-114">傳回時，包含指定資源不為所需狀態之 **MSFT_ResourceNotInDesiredState** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="781fa-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="781fa-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="781fa-115">Return value</span></span>
------------

<span data-ttu-id="781fa-116">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="781fa-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="781fa-117">備註</span><span class="sxs-lookup"><span data-stu-id="781fa-117">Remarks</span></span>

<span data-ttu-id="781fa-118">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="781fa-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="781fa-119">需求</span><span class="sxs-lookup"><span data-stu-id="781fa-119">Requirements</span></span>
------------
><span data-ttu-id="781fa-120">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="781fa-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="781fa-121">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="781fa-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="781fa-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="781fa-122">See also</span></span>


[<span data-ttu-id="781fa-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="781fa-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



