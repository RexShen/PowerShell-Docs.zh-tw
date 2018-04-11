---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法
ms.openlocfilehash: 07ae48dd456e68be4ad0b09127ba9801359fd101
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="dd098-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="dd098-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="dd098-104">將設定文件傳送到受管理的節點，並將其儲存為擱置變更。</span><span class="sxs-lookup"><span data-stu-id="dd098-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="dd098-105">語法</span><span class="sxs-lookup"><span data-stu-id="dd098-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="dd098-106">參數</span><span class="sxs-lookup"><span data-stu-id="dd098-106">Parameters</span></span>
----------

<span data-ttu-id="dd098-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="dd098-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="dd098-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="dd098-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="dd098-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="dd098-109">Return value</span></span>
------------

<span data-ttu-id="dd098-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="dd098-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd098-111">備註</span><span class="sxs-lookup"><span data-stu-id="dd098-111">Remarks</span></span>

<span data-ttu-id="dd098-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="dd098-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dd098-113">需求</span><span class="sxs-lookup"><span data-stu-id="dd098-113">Requirements</span></span>
------------
><span data-ttu-id="dd098-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="dd098-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="dd098-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dd098-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="dd098-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd098-116">See also</span></span>


[<span data-ttu-id="dd098-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dd098-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)