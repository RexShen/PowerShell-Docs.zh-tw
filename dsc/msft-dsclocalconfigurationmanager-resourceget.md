---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 ResourceGet 方法"
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3cecf-103">MSFT_DSCLocalConfigurationManager 類別的 ResourceGet 方法</span><span class="sxs-lookup"><span data-stu-id="3cecf-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3cecf-104">直接呼叫 DSC 資源的 **Get** 方法。</span><span class="sxs-lookup"><span data-stu-id="3cecf-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="3cecf-105">語法</span><span class="sxs-lookup"><span data-stu-id="3cecf-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="3cecf-106">參數</span><span class="sxs-lookup"><span data-stu-id="3cecf-106">Parameters</span></span>
----------

<span data-ttu-id="3cecf-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3cecf-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="3cecf-108">要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="3cecf-108">The name of the resource to call.</span></span>

<span data-ttu-id="3cecf-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3cecf-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="3cecf-110">包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="3cecf-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="3cecf-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3cecf-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="3cecf-112">在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="3cecf-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="3cecf-113">使用 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="3cecf-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="3cecf-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="3cecf-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="3cecf-115">傳回時，包含設定的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="3cecf-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="3cecf-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="3cecf-116">Return value</span></span>
------------

<span data-ttu-id="3cecf-117">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3cecf-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cecf-118">備註</span><span class="sxs-lookup"><span data-stu-id="3cecf-118">Remarks</span></span>

<span data-ttu-id="3cecf-119">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="3cecf-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3cecf-120">需求</span><span class="sxs-lookup"><span data-stu-id="3cecf-120">Requirements</span></span>
------------
><span data-ttu-id="3cecf-121">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3cecf-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3cecf-122">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3cecf-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3cecf-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cecf-123">See also</span></span>


[<span data-ttu-id="3cecf-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3cecf-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



