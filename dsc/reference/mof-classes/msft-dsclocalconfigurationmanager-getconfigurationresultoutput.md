---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078636"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="323ed-103">MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="323ed-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="323ed-104">擷取與特定工作相關聯的設定代理程式輸出。</span><span class="sxs-lookup"><span data-stu-id="323ed-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="323ed-105">語法</span><span class="sxs-lookup"><span data-stu-id="323ed-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="323ed-106">參數</span><span class="sxs-lookup"><span data-stu-id="323ed-106">Parameters</span></span>

<span data-ttu-id="323ed-107">*jobId* \[in\] 取得輸出資料之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="323ed-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="323ed-108">*resumeOutputBookmark* \[in\] 指定輸出應該接續前一個書籤。</span><span class="sxs-lookup"><span data-stu-id="323ed-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="323ed-109">*output* \[out\] 指定之工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="323ed-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="323ed-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="323ed-110">Return value</span></span>

<span data-ttu-id="323ed-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="323ed-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="323ed-112">備註</span><span class="sxs-lookup"><span data-stu-id="323ed-112">Remarks</span></span>

<span data-ttu-id="323ed-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="323ed-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="323ed-114">需求</span><span class="sxs-lookup"><span data-stu-id="323ed-114">Requirements</span></span>

<span data-ttu-id="323ed-115">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="323ed-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="323ed-116">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="323ed-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="323ed-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="323ed-117">See also</span></span>

[<span data-ttu-id="323ed-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="323ed-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)