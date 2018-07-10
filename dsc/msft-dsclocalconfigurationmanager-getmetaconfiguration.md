---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892836"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bfdce-103">MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="bfdce-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bfdce-104">取得用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="bfdce-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="bfdce-105">語法</span><span class="sxs-lookup"><span data-stu-id="bfdce-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="bfdce-106">參數</span><span class="sxs-lookup"><span data-stu-id="bfdce-106">Parameters</span></span>

<span data-ttu-id="bfdce-107">*MetaConfiguration* \[out\] 傳回時，包含定義設定之 **MSFT_DSCMetaConfiguration** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="bfdce-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="bfdce-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="bfdce-108">Return value</span></span>

<span data-ttu-id="bfdce-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="bfdce-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfdce-110">備註</span><span class="sxs-lookup"><span data-stu-id="bfdce-110">Remarks</span></span>

<span data-ttu-id="bfdce-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="bfdce-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bfdce-112">需求</span><span class="sxs-lookup"><span data-stu-id="bfdce-112">Requirements</span></span>

<span data-ttu-id="bfdce-113">**MOF：** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bfdce-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bfdce-114">**Namespace**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bfdce-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bfdce-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfdce-115">See also</span></span>

[<span data-ttu-id="bfdce-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bfdce-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)