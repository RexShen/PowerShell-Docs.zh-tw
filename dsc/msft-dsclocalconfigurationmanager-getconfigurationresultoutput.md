---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b9092-103">MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="b9092-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b9092-104">擷取與特定工作相關聯的設定代理程式輸出。</span><span class="sxs-lookup"><span data-stu-id="b9092-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="b9092-105">語法</span><span class="sxs-lookup"><span data-stu-id="b9092-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="b9092-106">參數</span><span class="sxs-lookup"><span data-stu-id="b9092-106">Parameters</span></span>
----------

<span data-ttu-id="b9092-107">*jobId* \[in\] 取得輸出資料之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9092-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="b9092-108">*resumeOutputBookmark* \[in\] 指定輸出應該接續前一個書籤。</span><span class="sxs-lookup"><span data-stu-id="b9092-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="b9092-109">*output* \[out\] 指定之工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="b9092-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="b9092-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="b9092-110">Return value</span></span>
------------

<span data-ttu-id="b9092-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b9092-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9092-112">備註</span><span class="sxs-lookup"><span data-stu-id="b9092-112">Remarks</span></span>

<span data-ttu-id="b9092-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="b9092-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b9092-114">需求</span><span class="sxs-lookup"><span data-stu-id="b9092-114">Requirements</span></span>
------------
><span data-ttu-id="b9092-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b9092-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b9092-116">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b9092-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b9092-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9092-117">See also</span></span>


[<span data-ttu-id="b9092-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b9092-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)