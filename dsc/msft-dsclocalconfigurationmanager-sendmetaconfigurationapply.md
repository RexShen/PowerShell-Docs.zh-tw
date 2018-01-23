---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法"
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="47c06-103">MSFT_DSCLocalConfigurationManager 類別的 SendMetaConfigurationApply 方法</span><span class="sxs-lookup"><span data-stu-id="47c06-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="47c06-104">設定用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="47c06-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="47c06-105">語法</span><span class="sxs-lookup"><span data-stu-id="47c06-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="47c06-106">參數</span><span class="sxs-lookup"><span data-stu-id="47c06-106">Parameters</span></span>
----------

<span data-ttu-id="47c06-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="47c06-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="47c06-108">設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="47c06-108">The environment data for the configuration.</span></span>

<span data-ttu-id="47c06-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="47c06-109">*force* \[in\]</span></span>  
<span data-ttu-id="47c06-110">**true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="47c06-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="47c06-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="47c06-111">Return value</span></span>
------------

<span data-ttu-id="47c06-112">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="47c06-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="47c06-113">備註</span><span class="sxs-lookup"><span data-stu-id="47c06-113">Remarks</span></span>

<span data-ttu-id="47c06-114">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="47c06-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="47c06-115">需求</span><span class="sxs-lookup"><span data-stu-id="47c06-115">Requirements</span></span>
------------
><span data-ttu-id="47c06-116">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="47c06-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="47c06-117">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="47c06-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="47c06-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47c06-118">See also</span></span>


[<span data-ttu-id="47c06-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="47c06-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



