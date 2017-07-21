---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法"
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4da33-103">MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="4da33-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4da33-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="4da33-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="4da33-105">語法</span><span class="sxs-lookup"><span data-stu-id="4da33-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="4da33-106">參數</span><span class="sxs-lookup"><span data-stu-id="4da33-106">Parameters</span></span>
----------

<span data-ttu-id="4da33-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4da33-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="4da33-108">指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="4da33-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="4da33-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4da33-109">Return value</span></span>
------------

<span data-ttu-id="4da33-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4da33-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4da33-111">備註</span><span class="sxs-lookup"><span data-stu-id="4da33-111">Remarks</span></span>

<span data-ttu-id="4da33-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="4da33-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4da33-113">需求</span><span class="sxs-lookup"><span data-stu-id="4da33-113">Requirements</span></span>
------------
><span data-ttu-id="4da33-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4da33-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4da33-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4da33-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4da33-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4da33-116">See also</span></span>


[<span data-ttu-id="4da33-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4da33-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



