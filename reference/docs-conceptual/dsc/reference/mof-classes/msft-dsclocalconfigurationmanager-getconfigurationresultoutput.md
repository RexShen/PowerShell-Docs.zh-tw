---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationResultOutput 方法
description: GetConfigurationResultOutput 方法
ms.openlocfilehash: 7c885109b3078189b7ac653733a5fb24db66312e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644716"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="50829-103">GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="50829-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="50829-104">擷取與特定工作相關聯的設定代理程式輸出。</span><span class="sxs-lookup"><span data-stu-id="50829-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="50829-105">語法</span><span class="sxs-lookup"><span data-stu-id="50829-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="50829-106">參數</span><span class="sxs-lookup"><span data-stu-id="50829-106">Parameters</span></span>

<span data-ttu-id="50829-107">**jobId** \[in\] 要取得輸出資料之作業的識別碼。</span><span class="sxs-lookup"><span data-stu-id="50829-107">**jobId** \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="50829-108">**resumeOutputBookmark** \[in\] 指定輸出應該接續前一個書籤。</span><span class="sxs-lookup"><span data-stu-id="50829-108">**resumeOutputBookmark** \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="50829-109">**output** \[out\] 指定之工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="50829-109">**output** \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="50829-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="50829-110">Return value</span></span>

<span data-ttu-id="50829-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="50829-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="50829-112">備註</span><span class="sxs-lookup"><span data-stu-id="50829-112">Remarks</span></span>

<span data-ttu-id="50829-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="50829-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="50829-114">需求</span><span class="sxs-lookup"><span data-stu-id="50829-114">Requirements</span></span>

<span data-ttu-id="50829-115">**MOF** ：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="50829-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="50829-116">**命名空間** ：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="50829-116">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="50829-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50829-117">See also</span></span>

[<span data-ttu-id="50829-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="50829-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
