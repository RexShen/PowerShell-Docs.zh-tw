---
ms.date: 08/28/2020
ms.topic: reference
title: DSC WindowsOptionalFeature 資源
description: DSC WindowsOptionalFeature 資源
ms.openlocfilehash: 1c7e888ea49b0d1710cc22c975cb618999238f67
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143053"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="e66dd-103">DSC WindowsOptionalFeature 資源</span><span class="sxs-lookup"><span data-stu-id="e66dd-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="e66dd-104">適用於：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="e66dd-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="e66dd-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsOptionalFeature** 資源提供一個機制，確保可在目標節點上啟用選用功能。</span><span class="sxs-lookup"><span data-stu-id="e66dd-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

> [!NOTE]
> <span data-ttu-id="e66dd-106">**WindowsOptionalFeature** 僅適用於 Windows 用戶端電腦，例如 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="e66dd-106">**WindowsOptionalFeature** only works on Windows client machines like Windows 10.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="e66dd-107">語法</span><span class="sxs-lookup"><span data-stu-id="e66dd-107">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="e66dd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e66dd-108">Properties</span></span>

|<span data-ttu-id="e66dd-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e66dd-109">Property</span></span> |<span data-ttu-id="e66dd-110">描述</span><span class="sxs-lookup"><span data-stu-id="e66dd-110">Description</span></span> |
|---|---|
|<span data-ttu-id="e66dd-111">名稱</span><span class="sxs-lookup"><span data-stu-id="e66dd-111">Name</span></span> |<span data-ttu-id="e66dd-112">表示您想要確保啟用或停用的功能名稱。</span><span class="sxs-lookup"><span data-stu-id="e66dd-112">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="e66dd-113">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="e66dd-113">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="e66dd-114">指定在搜尋來源檔案以啟用功能時，DISM 是否連絡 Windows Update (WU)。</span><span class="sxs-lookup"><span data-stu-id="e66dd-114">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="e66dd-115">若為 `$true`，則 DISM 不連絡 WU。</span><span class="sxs-lookup"><span data-stu-id="e66dd-115">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="e66dd-116">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="e66dd-116">RemoveFilesOnDisable</span></span> |<span data-ttu-id="e66dd-117">當 **Ensure** 設定為 **Absent** 時，設定為 `$true` 可移除與此功能建立關聯的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="e66dd-117">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent** .</span></span> |
|<span data-ttu-id="e66dd-118">LogLevel</span><span class="sxs-lookup"><span data-stu-id="e66dd-118">LogLevel</span></span> |<span data-ttu-id="e66dd-119">記錄中顯示的最大輸出等級。</span><span class="sxs-lookup"><span data-stu-id="e66dd-119">The maximum output level shown in the logs.</span></span> <span data-ttu-id="e66dd-120">接受的值為： **ErrorsOnly** 、 **ErrorsAndWarning** 和 **ErrorsAndWarningAndInformation** 。</span><span class="sxs-lookup"><span data-stu-id="e66dd-120">The accepted values are: **ErrorsOnly** , **ErrorsAndWarning** , and **ErrorsAndWarningAndInformation** .</span></span> |
|<span data-ttu-id="e66dd-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="e66dd-121">LogPath</span></span> |<span data-ttu-id="e66dd-122">要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="e66dd-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e66dd-123">通用屬性</span><span class="sxs-lookup"><span data-stu-id="e66dd-123">Common properties</span></span>

|<span data-ttu-id="e66dd-124">屬性</span><span class="sxs-lookup"><span data-stu-id="e66dd-124">Property</span></span> |<span data-ttu-id="e66dd-125">描述</span><span class="sxs-lookup"><span data-stu-id="e66dd-125">Description</span></span> |
|---|---|
|<span data-ttu-id="e66dd-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e66dd-126">DependsOn</span></span> |<span data-ttu-id="e66dd-127">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="e66dd-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e66dd-128">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="e66dd-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e66dd-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="e66dd-129">Ensure</span></span> |<span data-ttu-id="e66dd-130">指定是否已啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="e66dd-130">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="e66dd-131">若要確保已啟用此功能，請將此屬性設定為 _Enable_ 。</span><span class="sxs-lookup"><span data-stu-id="e66dd-131">To ensure that the feature is enabled, set this property to _Enable_ .</span></span> <span data-ttu-id="e66dd-132">若要確保已停用此功能，請將此屬性設定為 _Disable_ 。</span><span class="sxs-lookup"><span data-stu-id="e66dd-132">To ensure that the feature is disabled, set the property to _Disable_ .</span></span> <span data-ttu-id="e66dd-133">預設值為 _Enable_ 。</span><span class="sxs-lookup"><span data-stu-id="e66dd-133">The default value is _Enable_ .</span></span> |
|<span data-ttu-id="e66dd-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e66dd-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="e66dd-135">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="e66dd-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="e66dd-136">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="e66dd-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="e66dd-137">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="e66dd-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
