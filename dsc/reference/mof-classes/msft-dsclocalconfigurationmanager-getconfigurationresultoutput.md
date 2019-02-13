---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677084"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="86c53-103">MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="86c53-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="86c53-104">擷取與特定工作相關聯的設定代理程式輸出。</span><span class="sxs-lookup"><span data-stu-id="86c53-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="86c53-105">語法</span><span class="sxs-lookup"><span data-stu-id="86c53-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="86c53-106">參數</span><span class="sxs-lookup"><span data-stu-id="86c53-106">Parameters</span></span>

<span data-ttu-id="86c53-107">*jobId* \[in\] 取得輸出資料之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="86c53-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="86c53-108">*resumeOutputBookmark* \[in\] 指定輸出應該接續前一個書籤。</span><span class="sxs-lookup"><span data-stu-id="86c53-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="86c53-109">*output* \[out\] 指定之工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="86c53-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="86c53-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="86c53-110">Return value</span></span>

<span data-ttu-id="86c53-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="86c53-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="86c53-112">備註</span><span class="sxs-lookup"><span data-stu-id="86c53-112">Remarks</span></span>

<span data-ttu-id="86c53-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="86c53-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="86c53-114">需求</span><span class="sxs-lookup"><span data-stu-id="86c53-114">Requirements</span></span>

<span data-ttu-id="86c53-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="86c53-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="86c53-116">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="86c53-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="86c53-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86c53-117">See also</span></span>

[<span data-ttu-id="86c53-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="86c53-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)