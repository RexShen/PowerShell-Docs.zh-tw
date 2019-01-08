---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047416"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="68aff-103">MSFT_DSCLocalConfigurationManager 類別的 GetMetaConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="68aff-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="68aff-104">取得用於控制設定代理程式的本機設定管理員設定。</span><span class="sxs-lookup"><span data-stu-id="68aff-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="68aff-105">語法</span><span class="sxs-lookup"><span data-stu-id="68aff-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="68aff-106">參數</span><span class="sxs-lookup"><span data-stu-id="68aff-106">Parameters</span></span>

<span data-ttu-id="68aff-107">*MetaConfiguration* \[out\] 傳回時，包含定義設定之 **MSFT_DSCMetaConfiguration** 類別的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="68aff-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="68aff-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="68aff-108">Return value</span></span>

<span data-ttu-id="68aff-109">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="68aff-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="68aff-110">備註</span><span class="sxs-lookup"><span data-stu-id="68aff-110">Remarks</span></span>

<span data-ttu-id="68aff-111">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="68aff-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="68aff-112">需求</span><span class="sxs-lookup"><span data-stu-id="68aff-112">Requirements</span></span>

<span data-ttu-id="68aff-113">MOF\*\*DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="68aff-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="68aff-114">-NamespaceRoot\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="68aff-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="68aff-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68aff-115">See also</span></span>

[<span data-ttu-id="68aff-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="68aff-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)