---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法"
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d2acd-103">MSFT_DSCLocalConfigurationManager 類別的 StopConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="d2acd-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d2acd-104">停止進行中的設定變更。</span><span class="sxs-lookup"><span data-stu-id="d2acd-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="d2acd-105">語法</span><span class="sxs-lookup"><span data-stu-id="d2acd-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="d2acd-106">參數</span><span class="sxs-lookup"><span data-stu-id="d2acd-106">Parameters</span></span>
----------

<span data-ttu-id="d2acd-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d2acd-107">*force* \[in\]</span></span>  
<span data-ttu-id="d2acd-108">**true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="d2acd-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2acd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d2acd-109">Return value</span></span>
------------

<span data-ttu-id="d2acd-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d2acd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2acd-111">備註</span><span class="sxs-lookup"><span data-stu-id="d2acd-111">Remarks</span></span>

<span data-ttu-id="d2acd-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d2acd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2acd-113">需求</span><span class="sxs-lookup"><span data-stu-id="d2acd-113">Requirements</span></span>
------------
><span data-ttu-id="d2acd-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d2acd-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d2acd-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2acd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d2acd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2acd-116">See also</span></span>


[<span data-ttu-id="d2acd-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d2acd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



