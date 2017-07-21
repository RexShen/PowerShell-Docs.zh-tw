---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 ResourceSet 方法"
ms.openlocfilehash: 9cd9c1b3f58a5862db6c4eea0488423b8dfe7310
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8ba65-103">MSFT_DSCLocalConfigurationManager 類別的 ResourceSet 方法</span><span class="sxs-lookup"><span data-stu-id="8ba65-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8ba65-104">直接呼叫 DSC 資源的 **Set** 方法。</span><span class="sxs-lookup"><span data-stu-id="8ba65-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="8ba65-105">語法</span><span class="sxs-lookup"><span data-stu-id="8ba65-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="8ba65-106">參數</span><span class="sxs-lookup"><span data-stu-id="8ba65-106">Parameters</span></span>
----------

<span data-ttu-id="8ba65-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8ba65-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="8ba65-108">要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="8ba65-108">The name of the resource to call.</span></span>

<span data-ttu-id="8ba65-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8ba65-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="8ba65-110">包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="8ba65-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="8ba65-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="8ba65-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="8ba65-112">在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="8ba65-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="8ba65-113">使用 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="8ba65-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="8ba65-114">*RebootRequired* \[out\]</span><span class="sxs-lookup"><span data-stu-id="8ba65-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="8ba65-115">傳回時，如果需要重新啟動目標節點，這個屬性會設定為 **true**。</span><span class="sxs-lookup"><span data-stu-id="8ba65-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="8ba65-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="8ba65-116">Return value</span></span>
------------

<span data-ttu-id="8ba65-117">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8ba65-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ba65-118">備註</span><span class="sxs-lookup"><span data-stu-id="8ba65-118">Remarks</span></span>

<span data-ttu-id="8ba65-119">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="8ba65-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8ba65-120">需求</span><span class="sxs-lookup"><span data-stu-id="8ba65-120">Requirements</span></span>
------------
><span data-ttu-id="8ba65-121">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8ba65-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8ba65-122">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8ba65-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8ba65-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ba65-123">See also</span></span>


[<span data-ttu-id="8ba65-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8ba65-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



