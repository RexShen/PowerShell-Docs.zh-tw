---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法"
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="40d30-103">MSFT_DSCLocalConfigurationManager 類別的 SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="40d30-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="40d30-104">將設定文件傳送到受管理的節點，並將其儲存為擱置變更。</span><span class="sxs-lookup"><span data-stu-id="40d30-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="40d30-105">語法</span><span class="sxs-lookup"><span data-stu-id="40d30-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="40d30-106">參數</span><span class="sxs-lookup"><span data-stu-id="40d30-106">Parameters</span></span>
----------

<span data-ttu-id="40d30-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="40d30-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="40d30-108">設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="40d30-108">The environment data for the configuration.</span></span>

<span data-ttu-id="40d30-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="40d30-109">*force* \[in\]</span></span>  
<span data-ttu-id="40d30-110">**true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="40d30-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="40d30-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="40d30-111">Return value</span></span>
------------

<span data-ttu-id="40d30-112">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="40d30-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="40d30-113">備註</span><span class="sxs-lookup"><span data-stu-id="40d30-113">Remarks</span></span>

<span data-ttu-id="40d30-114">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="40d30-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="40d30-115">需求</span><span class="sxs-lookup"><span data-stu-id="40d30-115">Requirements</span></span>
------------
><span data-ttu-id="40d30-116">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="40d30-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="40d30-117">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="40d30-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="40d30-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40d30-118">See also</span></span>


[<span data-ttu-id="40d30-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="40d30-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



