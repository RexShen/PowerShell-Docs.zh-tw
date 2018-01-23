---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法"
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bb915-103">MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="bb915-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bb915-104">將設定文件傳送到受管理的節點，並使用設定代理程式的 **Get** 方法來套用設定。</span><span class="sxs-lookup"><span data-stu-id="bb915-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="bb915-105">語法</span><span class="sxs-lookup"><span data-stu-id="bb915-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="bb915-106">參數</span><span class="sxs-lookup"><span data-stu-id="bb915-106">Parameters</span></span>
----------

<span data-ttu-id="bb915-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bb915-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="bb915-108">指定要傳送的設定資料。</span><span class="sxs-lookup"><span data-stu-id="bb915-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="bb915-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="bb915-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="bb915-110">傳回時，包含設定的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="bb915-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="bb915-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="bb915-111">Return value</span></span>
------------

<span data-ttu-id="bb915-112">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bb915-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb915-113">備註</span><span class="sxs-lookup"><span data-stu-id="bb915-113">Remarks</span></span>

<span data-ttu-id="bb915-114">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="bb915-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb915-115">需求</span><span class="sxs-lookup"><span data-stu-id="bb915-115">Requirements</span></span>
------------
><span data-ttu-id="bb915-116">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bb915-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bb915-117">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb915-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bb915-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb915-118">See also</span></span>


[<span data-ttu-id="bb915-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bb915-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



