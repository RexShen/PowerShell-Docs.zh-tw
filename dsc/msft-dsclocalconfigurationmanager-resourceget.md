---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 ResourceGet 方法
ms.openlocfilehash: 3fd7ae54eb3ae782156dc4619ee0b6905dfb1212
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e96f6-103">MSFT_DSCLocalConfigurationManager 類別的 ResourceGet 方法</span><span class="sxs-lookup"><span data-stu-id="e96f6-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e96f6-104">直接呼叫 DSC 資源的 **Get** 方法。</span><span class="sxs-lookup"><span data-stu-id="e96f6-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="e96f6-105">語法</span><span class="sxs-lookup"><span data-stu-id="e96f6-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="e96f6-106">參數</span><span class="sxs-lookup"><span data-stu-id="e96f6-106">Parameters</span></span>
----------

<span data-ttu-id="e96f6-107">*ResourceType* \[in\] 要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="e96f6-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="e96f6-108">*ModuleName* \[in\] 包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="e96f6-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="e96f6-109">*resourceProperty* \[in\] 在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="e96f6-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="e96f6-110">使用 [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="e96f6-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="e96f6-111">*configurations* \[out\] 傳回時，包含設定的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="e96f6-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="e96f6-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="e96f6-112">Return value</span></span>
------------

<span data-ttu-id="e96f6-113">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e96f6-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e96f6-114">備註</span><span class="sxs-lookup"><span data-stu-id="e96f6-114">Remarks</span></span>

<span data-ttu-id="e96f6-115">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="e96f6-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e96f6-116">需求</span><span class="sxs-lookup"><span data-stu-id="e96f6-116">Requirements</span></span>
------------
><span data-ttu-id="e96f6-117">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e96f6-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e96f6-118">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e96f6-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e96f6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e96f6-119">See also</span></span>


[<span data-ttu-id="e96f6-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e96f6-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)