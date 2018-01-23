---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法"
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bfd2d-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="bfd2d-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bfd2d-104">將設定文件傳送到受管理的節點，並將其儲存為擱置變更。</span><span class="sxs-lookup"><span data-stu-id="bfd2d-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="bfd2d-105">語法</span><span class="sxs-lookup"><span data-stu-id="bfd2d-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="bfd2d-106">參數</span><span class="sxs-lookup"><span data-stu-id="bfd2d-106">Parameters</span></span>
----------

<span data-ttu-id="bfd2d-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bfd2d-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="bfd2d-108">設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="bfd2d-108">The environment data for the configuration.</span></span>

<span data-ttu-id="bfd2d-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bfd2d-109">*force* \[in\]</span></span>  
<span data-ttu-id="bfd2d-110">**true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="bfd2d-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="bfd2d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="bfd2d-111">Return value</span></span>
------------

<span data-ttu-id="bfd2d-112">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bfd2d-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfd2d-113">備註</span><span class="sxs-lookup"><span data-stu-id="bfd2d-113">Remarks</span></span>

<span data-ttu-id="bfd2d-114">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="bfd2d-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bfd2d-115">需求</span><span class="sxs-lookup"><span data-stu-id="bfd2d-115">Requirements</span></span>
------------
><span data-ttu-id="bfd2d-116">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bfd2d-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bfd2d-117">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bfd2d-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bfd2d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd2d-118">See also</span></span>


[<span data-ttu-id="bfd2d-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bfd2d-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



