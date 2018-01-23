---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法"
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="541f0-103">MSFT_DSCLocalConfigurationManager 類別的 RollBack 方法</span><span class="sxs-lookup"><span data-stu-id="541f0-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="541f0-104">將設定復原回先前的版本。</span><span class="sxs-lookup"><span data-stu-id="541f0-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="541f0-105">語法</span><span class="sxs-lookup"><span data-stu-id="541f0-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="541f0-106">參數</span><span class="sxs-lookup"><span data-stu-id="541f0-106">Parameters</span></span>
----------

<span data-ttu-id="541f0-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="541f0-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="541f0-108">指定要求的設定。</span><span class="sxs-lookup"><span data-stu-id="541f0-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="541f0-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="541f0-109">Return value</span></span>
------------

<span data-ttu-id="541f0-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="541f0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="541f0-111">備註</span><span class="sxs-lookup"><span data-stu-id="541f0-111">Remarks</span></span>

<span data-ttu-id="541f0-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="541f0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="541f0-113">需求</span><span class="sxs-lookup"><span data-stu-id="541f0-113">Requirements</span></span>
------------
><span data-ttu-id="541f0-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="541f0-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="541f0-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="541f0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="541f0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="541f0-116">See also</span></span>


[<span data-ttu-id="541f0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="541f0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



