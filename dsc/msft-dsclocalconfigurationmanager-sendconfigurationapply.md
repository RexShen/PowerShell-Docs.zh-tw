---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893166"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="158bc-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="158bc-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="158bc-104">將設定文件傳送到受管理的節點，並使用設定代理程式套用設定。</span><span class="sxs-lookup"><span data-stu-id="158bc-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="158bc-105">語法</span><span class="sxs-lookup"><span data-stu-id="158bc-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="158bc-106">參數</span><span class="sxs-lookup"><span data-stu-id="158bc-106">Parameters</span></span>

<span data-ttu-id="158bc-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="158bc-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="158bc-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="158bc-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="158bc-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="158bc-109">Return value</span></span>

<span data-ttu-id="158bc-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="158bc-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="158bc-111">備註</span><span class="sxs-lookup"><span data-stu-id="158bc-111">Remarks</span></span>

<span data-ttu-id="158bc-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="158bc-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="158bc-113">需求</span><span class="sxs-lookup"><span data-stu-id="158bc-113">Requirements</span></span>

<span data-ttu-id="158bc-114">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="158bc-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="158bc-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="158bc-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="158bc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="158bc-116">See also</span></span>

[<span data-ttu-id="158bc-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="158bc-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)