---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 ResourceTest 方法"
ms.openlocfilehash: 799b1cd91dfacf25c0e5e734ca96d20a776103f0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="69ea5-103">MSFT_DSCLocalConfigurationManager 類別的 ResourceTest 方法</span><span class="sxs-lookup"><span data-stu-id="69ea5-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="69ea5-104">直接呼叫 DSC 資源的 **Test** 方法。</span><span class="sxs-lookup"><span data-stu-id="69ea5-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="69ea5-105">語法</span><span class="sxs-lookup"><span data-stu-id="69ea5-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="69ea5-106">參數</span><span class="sxs-lookup"><span data-stu-id="69ea5-106">Parameters</span></span>
----------

<span data-ttu-id="69ea5-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="69ea5-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="69ea5-108">要呼叫的資源名稱。</span><span class="sxs-lookup"><span data-stu-id="69ea5-108">The name of the resource to call.</span></span>

<span data-ttu-id="69ea5-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="69ea5-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="69ea5-110">包含要呼叫之資源的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="69ea5-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="69ea5-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="69ea5-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="69ea5-112">在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。</span><span class="sxs-lookup"><span data-stu-id="69ea5-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="69ea5-113">使用 [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) Cmdlet，探索資源的屬性和其類型。</span><span class="sxs-lookup"><span data-stu-id="69ea5-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="69ea5-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="69ea5-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="69ea5-115">傳回時，如果目標節點是想要的狀態，這個屬性會設定為 **true**。</span><span class="sxs-lookup"><span data-stu-id="69ea5-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="69ea5-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="69ea5-116">Return value</span></span>
------------

<span data-ttu-id="69ea5-117">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="69ea5-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="69ea5-118">備註</span><span class="sxs-lookup"><span data-stu-id="69ea5-118">Remarks</span></span>

<span data-ttu-id="69ea5-119">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="69ea5-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="69ea5-120">需求</span><span class="sxs-lookup"><span data-stu-id="69ea5-120">Requirements</span></span>
------------
><span data-ttu-id="69ea5-121">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="69ea5-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="69ea5-122">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="69ea5-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="69ea5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69ea5-123">See also</span></span>


[<span data-ttu-id="69ea5-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="69ea5-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



