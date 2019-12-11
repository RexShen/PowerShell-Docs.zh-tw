---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: SendConfiguration 方法
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953385"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="a8d0a-103">SendConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="a8d0a-103">SendConfiguration method</span></span>

<span data-ttu-id="a8d0a-104">將設定文件傳送到受管理的節點，並將其儲存為擱置變更。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="a8d0a-105">語法</span><span class="sxs-lookup"><span data-stu-id="a8d0a-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="a8d0a-106">參數</span><span class="sxs-lookup"><span data-stu-id="a8d0a-106">Parameters</span></span>

<span data-ttu-id="a8d0a-107">*ConfigurationData* \[in\] 設定的環境資料。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="a8d0a-108">*force* \[in\] **true** 表示強制停止該設定。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="a8d0a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a8d0a-109">Return value</span></span>

<span data-ttu-id="a8d0a-110">若成功即傳回零；否則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8d0a-111">備註</span><span class="sxs-lookup"><span data-stu-id="a8d0a-111">Remarks</span></span>

<span data-ttu-id="a8d0a-112">此為靜態方法。</span><span class="sxs-lookup"><span data-stu-id="a8d0a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8d0a-113">需求</span><span class="sxs-lookup"><span data-stu-id="a8d0a-113">Requirements</span></span>

<span data-ttu-id="a8d0a-114">**MOF**：DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a8d0a-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a8d0a-115">**命名空間**：Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a8d0a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a8d0a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8d0a-116">See also</span></span>

[<span data-ttu-id="a8d0a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a8d0a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
