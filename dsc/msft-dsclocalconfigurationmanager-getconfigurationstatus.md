---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationStatus 方法"
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bac12-103">MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationStatus 方法</span><span class="sxs-lookup"><span data-stu-id="bac12-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bac12-104">取得設定狀態歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="bac12-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="bac12-105">語法</span><span class="sxs-lookup"><span data-stu-id="bac12-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="bac12-106">參數</span><span class="sxs-lookup"><span data-stu-id="bac12-106">Parameters</span></span>
----------

<span data-ttu-id="bac12-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bac12-107">*All* \[in\]</span></span>  
<span data-ttu-id="bac12-108">若此方法應傳回機器上所執行所有設定的相關資訊，包括設定應用程式與一致性檢查，即為 **true**。</span><span class="sxs-lookup"><span data-stu-id="bac12-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="bac12-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="bac12-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="bac12-110">在傳回時會包含定義設定的 **MSFT_DSCConfigurationStatus** 類別之內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="bac12-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="bac12-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="bac12-111">Return value</span></span>
------------

<span data-ttu-id="bac12-112">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bac12-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bac12-113">備註</span><span class="sxs-lookup"><span data-stu-id="bac12-113">Remarks</span></span>

<span data-ttu-id="bac12-114">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="bac12-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bac12-115">需求</span><span class="sxs-lookup"><span data-stu-id="bac12-115">Requirements</span></span>
------------
><span data-ttu-id="bac12-116">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bac12-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bac12-117">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bac12-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bac12-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bac12-118">See also</span></span>


[<span data-ttu-id="bac12-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bac12-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



