---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法"
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f05a2-103">MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="f05a2-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f05a2-104">取得用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="f05a2-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="f05a2-105">語法</span><span class="sxs-lookup"><span data-stu-id="f05a2-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="f05a2-106">參數</span><span class="sxs-lookup"><span data-stu-id="f05a2-106">Parameters</span></span>
----------

<span data-ttu-id="f05a2-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="f05a2-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="f05a2-108">傳回時，包含定義設定之 **MSFT_DSCMetaConfiguration** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="f05a2-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="f05a2-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="f05a2-109">Return value</span></span>
------------

<span data-ttu-id="f05a2-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="f05a2-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f05a2-111">備註</span><span class="sxs-lookup"><span data-stu-id="f05a2-111">Remarks</span></span>

<span data-ttu-id="f05a2-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="f05a2-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f05a2-113">需求</span><span class="sxs-lookup"><span data-stu-id="f05a2-113">Requirements</span></span>
------------
><span data-ttu-id="f05a2-114">**MOF：**DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f05a2-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f05a2-115">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f05a2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f05a2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f05a2-116">See also</span></span>


[<span data-ttu-id="f05a2-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f05a2-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



