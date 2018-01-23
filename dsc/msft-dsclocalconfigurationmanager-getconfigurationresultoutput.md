---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法"
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c6ec1-103">MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="c6ec1-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c6ec1-104">擷取與特定工作相關聯的設定代理程式輸出。</span><span class="sxs-lookup"><span data-stu-id="c6ec1-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="c6ec1-105">語法</span><span class="sxs-lookup"><span data-stu-id="c6ec1-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="c6ec1-106">參數</span><span class="sxs-lookup"><span data-stu-id="c6ec1-106">Parameters</span></span>
----------

<span data-ttu-id="c6ec1-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c6ec1-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="c6ec1-108">取得輸出資料之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c6ec1-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="c6ec1-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c6ec1-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="c6ec1-110">指定輸出應該接續前一個書籤。</span><span class="sxs-lookup"><span data-stu-id="c6ec1-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="c6ec1-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="c6ec1-111">*output* \[out\]</span></span>  
<span data-ttu-id="c6ec1-112">所指定之工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="c6ec1-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="c6ec1-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="c6ec1-113">Return value</span></span>
------------

<span data-ttu-id="c6ec1-114">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c6ec1-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c6ec1-115">備註</span><span class="sxs-lookup"><span data-stu-id="c6ec1-115">Remarks</span></span>

<span data-ttu-id="c6ec1-116">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="c6ec1-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c6ec1-117">需求</span><span class="sxs-lookup"><span data-stu-id="c6ec1-117">Requirements</span></span>
------------
><span data-ttu-id="c6ec1-118">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c6ec1-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c6ec1-119">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c6ec1-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c6ec1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6ec1-120">See also</span></span>


[<span data-ttu-id="c6ec1-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c6ec1-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



