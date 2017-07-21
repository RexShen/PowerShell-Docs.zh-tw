---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationStatus 方法"
ms.openlocfilehash: e02ed81a7b8436323bc68aaa2587a445e6a5adf9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d96de-103">MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationStatus 方法</span><span class="sxs-lookup"><span data-stu-id="d96de-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d96de-104">取得設定狀態歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="d96de-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="d96de-105">語法</span><span class="sxs-lookup"><span data-stu-id="d96de-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="d96de-106">參數</span><span class="sxs-lookup"><span data-stu-id="d96de-106">Parameters</span></span>
----------

<span data-ttu-id="d96de-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d96de-107">*All* \[in\]</span></span>  
<span data-ttu-id="d96de-108">若此方法應傳回機器上所執行所有設定的相關資訊，包括設定應用程式與一致性檢查，即為 **true**。</span><span class="sxs-lookup"><span data-stu-id="d96de-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="d96de-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="d96de-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="d96de-110">在傳回時會包含定義設定的 **MSFT_DSCConfigurationStatus** 類別之內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="d96de-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d96de-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d96de-111">Return value</span></span>
------------

<span data-ttu-id="d96de-112">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d96de-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d96de-113">備註</span><span class="sxs-lookup"><span data-stu-id="d96de-113">Remarks</span></span>

<span data-ttu-id="d96de-114">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d96de-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d96de-115">需求</span><span class="sxs-lookup"><span data-stu-id="d96de-115">Requirements</span></span>
------------
><span data-ttu-id="d96de-116">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d96de-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d96de-117">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d96de-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d96de-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d96de-118">See also</span></span>


[<span data-ttu-id="d96de-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d96de-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



