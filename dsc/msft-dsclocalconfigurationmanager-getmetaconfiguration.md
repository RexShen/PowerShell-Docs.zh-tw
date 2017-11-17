---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法"
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1c801-103">MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="1c801-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1c801-104">取得用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="1c801-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="1c801-105">語法</span><span class="sxs-lookup"><span data-stu-id="1c801-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="1c801-106">參數</span><span class="sxs-lookup"><span data-stu-id="1c801-106">Parameters</span></span>
----------

<span data-ttu-id="1c801-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="1c801-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="1c801-108">傳回時，包含定義設定之 **MSFT_DSCMetaConfiguration** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c801-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="1c801-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1c801-109">Return value</span></span>
------------

<span data-ttu-id="1c801-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="1c801-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c801-111">備註</span><span class="sxs-lookup"><span data-stu-id="1c801-111">Remarks</span></span>

<span data-ttu-id="1c801-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="1c801-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c801-113">需求</span><span class="sxs-lookup"><span data-stu-id="1c801-113">Requirements</span></span>
------------
><span data-ttu-id="1c801-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1c801-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1c801-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1c801-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1c801-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c801-116">See also</span></span>


[<span data-ttu-id="1c801-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1c801-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



