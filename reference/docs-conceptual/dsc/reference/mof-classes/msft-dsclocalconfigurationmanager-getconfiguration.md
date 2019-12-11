---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: GetConfiguration 方法
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71955045"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="5ede0-103">GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="5ede0-103">GetConfiguration method</span></span>

<span data-ttu-id="5ede0-104">將設定文件傳送到受管理的節點，並使用設定代理程式的 **Get** 方法來套用設定。</span><span class="sxs-lookup"><span data-stu-id="5ede0-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ede0-105">語法</span><span class="sxs-lookup"><span data-stu-id="5ede0-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="5ede0-106">參數</span><span class="sxs-lookup"><span data-stu-id="5ede0-106">Parameters</span></span>

<span data-ttu-id="5ede0-107">*configurationData* \[in\] 指定要傳送的設定資料。</span><span class="sxs-lookup"><span data-stu-id="5ede0-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="5ede0-108">*configurations* \[out\] 傳回時，包含設定的內嵌執行個體。</span><span class="sxs-lookup"><span data-stu-id="5ede0-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ede0-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5ede0-109">Return value</span></span>

<span data-ttu-id="5ede0-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="5ede0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ede0-111">備註</span><span class="sxs-lookup"><span data-stu-id="5ede0-111">Remarks</span></span>

<span data-ttu-id="5ede0-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="5ede0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ede0-113">需求</span><span class="sxs-lookup"><span data-stu-id="5ede0-113">Requirements</span></span>

<span data-ttu-id="5ede0-114">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5ede0-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5ede0-115">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ede0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5ede0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ede0-116">See also</span></span>

[<span data-ttu-id="5ede0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5ede0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
