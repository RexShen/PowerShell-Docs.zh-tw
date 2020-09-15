---
ms.date: 07/17/2020
keywords: dsc,powershell,設定,安裝
title: GetConfigurationResultOutput 方法
ms.openlocfilehash: 9c81082c28b2ffcc329264d29784782deaa9779d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464072"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="67af6-103">GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="67af6-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="67af6-104">擷取與特定工作相關聯的設定代理程式輸出。</span><span class="sxs-lookup"><span data-stu-id="67af6-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="67af6-105">語法</span><span class="sxs-lookup"><span data-stu-id="67af6-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="67af6-106">參數</span><span class="sxs-lookup"><span data-stu-id="67af6-106">Parameters</span></span>

<span data-ttu-id="67af6-107">**jobId** \[in\] 要取得輸出資料之作業的識別碼。</span><span class="sxs-lookup"><span data-stu-id="67af6-107">**jobId** \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="67af6-108">**resumeOutputBookmark** \[in\] 指定輸出應該接續前一個書籤。</span><span class="sxs-lookup"><span data-stu-id="67af6-108">**resumeOutputBookmark** \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="67af6-109">**output** \[out\] 指定之工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="67af6-109">**output** \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="67af6-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="67af6-110">Return value</span></span>

<span data-ttu-id="67af6-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="67af6-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="67af6-112">備註</span><span class="sxs-lookup"><span data-stu-id="67af6-112">Remarks</span></span>

<span data-ttu-id="67af6-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="67af6-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="67af6-114">需求</span><span class="sxs-lookup"><span data-stu-id="67af6-114">Requirements</span></span>

<span data-ttu-id="67af6-115">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="67af6-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="67af6-116">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="67af6-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="67af6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67af6-117">See also</span></span>

[<span data-ttu-id="67af6-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="67af6-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
