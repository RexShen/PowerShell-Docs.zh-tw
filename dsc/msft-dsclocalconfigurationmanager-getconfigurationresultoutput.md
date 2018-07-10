---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893938"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1b0c4-103">MSFT_DSCLocalConfigurationManager 類別的 GetConfigurationResultOutput 方法</span><span class="sxs-lookup"><span data-stu-id="1b0c4-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1b0c4-104">擷取與特定工作相關聯的設定代理程式輸出。</span><span class="sxs-lookup"><span data-stu-id="1b0c4-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b0c4-105">語法</span><span class="sxs-lookup"><span data-stu-id="1b0c4-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="1b0c4-106">參數</span><span class="sxs-lookup"><span data-stu-id="1b0c4-106">Parameters</span></span>

<span data-ttu-id="1b0c4-107">*jobId* \[in\] 取得輸出資料之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1b0c4-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="1b0c4-108">*resumeOutputBookmark* \[in\] 指定輸出應該接續前一個書籤。</span><span class="sxs-lookup"><span data-stu-id="1b0c4-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="1b0c4-109">*output* \[out\] 指定之工作的輸出。</span><span class="sxs-lookup"><span data-stu-id="1b0c4-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="1b0c4-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="1b0c4-110">Return value</span></span>

<span data-ttu-id="1b0c4-111">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="1b0c4-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b0c4-112">備註</span><span class="sxs-lookup"><span data-stu-id="1b0c4-112">Remarks</span></span>

<span data-ttu-id="1b0c4-113">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="1b0c4-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b0c4-114">需求</span><span class="sxs-lookup"><span data-stu-id="1b0c4-114">Requirements</span></span>

<span data-ttu-id="1b0c4-115">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1b0c4-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1b0c4-116">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1b0c4-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1b0c4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b0c4-117">See also</span></span>

[<span data-ttu-id="1b0c4-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1b0c4-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)