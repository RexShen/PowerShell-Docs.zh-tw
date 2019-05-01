---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078640"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d2807-103">MSFT_DSCLocalConfigurationManager 類別的 GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="d2807-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d2807-104">將設定文件傳送到受管理的節點，並使用設定代理程式的 **Get** 方法來套用設定。</span><span class="sxs-lookup"><span data-stu-id="d2807-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2807-105">語法</span><span class="sxs-lookup"><span data-stu-id="d2807-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="d2807-106">參數</span><span class="sxs-lookup"><span data-stu-id="d2807-106">Parameters</span></span>

<span data-ttu-id="d2807-107">*configurationData* \[in\] 指定要傳送的設定資料。</span><span class="sxs-lookup"><span data-stu-id="d2807-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="d2807-108">*configurations* \[out\] 傳回時，包含設定的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="d2807-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="d2807-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d2807-109">Return value</span></span>

<span data-ttu-id="d2807-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d2807-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2807-111">備註</span><span class="sxs-lookup"><span data-stu-id="d2807-111">Remarks</span></span>

<span data-ttu-id="d2807-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d2807-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d2807-113">需求</span><span class="sxs-lookup"><span data-stu-id="d2807-113">Requirements</span></span>

<span data-ttu-id="d2807-114">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d2807-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d2807-115">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d2807-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d2807-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2807-116">See also</span></span>

[<span data-ttu-id="d2807-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d2807-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)