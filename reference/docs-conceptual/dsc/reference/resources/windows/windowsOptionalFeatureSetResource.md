---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC WindowsOptionalFeatureSet 資源
ms.openlocfilehash: 0930bd0c6d1955005ea607b610e004818c0ad06f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560146"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="f20d7-103">DSC WindowsOptionalFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="f20d7-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="f20d7-104">適用於：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="f20d7-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="f20d7-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsOptionalFeatureSet** 資源提供一個機制，確保可在目標節點上啟用選用功能。</span><span class="sxs-lookup"><span data-stu-id="f20d7-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="f20d7-106">此資源是針對**Name** 屬性中所指定每項功能呼叫 [WindowsOptionalFeature 資源](windowsOptionalFeatureResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="f20d7-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="f20d7-107">當您想要將多個 Windows 選用功能設定成相同的狀態，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="f20d7-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="f20d7-108">語法</span><span class="sxs-lookup"><span data-stu-id="f20d7-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f20d7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f20d7-109">Properties</span></span>

|<span data-ttu-id="f20d7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f20d7-110">Property</span></span> |<span data-ttu-id="f20d7-111">描述</span><span class="sxs-lookup"><span data-stu-id="f20d7-111">Description</span></span> |
|---|---|
|<span data-ttu-id="f20d7-112">名稱</span><span class="sxs-lookup"><span data-stu-id="f20d7-112">Name</span></span> |<span data-ttu-id="f20d7-113">表示您想要確保啟用或停用的功能名稱。</span><span class="sxs-lookup"><span data-stu-id="f20d7-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="f20d7-114">來源</span><span class="sxs-lookup"><span data-stu-id="f20d7-114">Source</span></span> |<span data-ttu-id="f20d7-115">未實作。</span><span class="sxs-lookup"><span data-stu-id="f20d7-115">Not implemented.</span></span> |
|<span data-ttu-id="f20d7-116">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="f20d7-116">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="f20d7-117">指定在搜尋來源檔案以啟用功能時，DISM 是否連絡 Windows Update (WU)。</span><span class="sxs-lookup"><span data-stu-id="f20d7-117">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="f20d7-118">若為 `$true`，則 DISM 不連絡 WU。</span><span class="sxs-lookup"><span data-stu-id="f20d7-118">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="f20d7-119">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="f20d7-119">RemoveFilesOnDisable</span></span> |<span data-ttu-id="f20d7-120">當 **Ensure** 設定為 **Absent** 時，設定為 `$true` 可移除與此功能建立關聯的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="f20d7-120">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="f20d7-121">LogLevel</span><span class="sxs-lookup"><span data-stu-id="f20d7-121">LogLevel</span></span> |<span data-ttu-id="f20d7-122">記錄中顯示的最大輸出等級。</span><span class="sxs-lookup"><span data-stu-id="f20d7-122">The maximum output level shown in the logs.</span></span> <span data-ttu-id="f20d7-123">接受的值為：**ErrorsOnly**、**ErrorsAndWarning** 和 **ErrorsAndWarningAndInformation**。</span><span class="sxs-lookup"><span data-stu-id="f20d7-123">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="f20d7-124">LogPath</span><span class="sxs-lookup"><span data-stu-id="f20d7-124">LogPath</span></span> |<span data-ttu-id="f20d7-125">要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="f20d7-125">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f20d7-126">通用屬性</span><span class="sxs-lookup"><span data-stu-id="f20d7-126">Common properties</span></span>

|<span data-ttu-id="f20d7-127">屬性</span><span class="sxs-lookup"><span data-stu-id="f20d7-127">Property</span></span> |<span data-ttu-id="f20d7-128">描述</span><span class="sxs-lookup"><span data-stu-id="f20d7-128">Description</span></span> |
|---|---|
|<span data-ttu-id="f20d7-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f20d7-129">DependsOn</span></span> |<span data-ttu-id="f20d7-130">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="f20d7-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f20d7-131">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="f20d7-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f20d7-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="f20d7-132">Ensure</span></span> |<span data-ttu-id="f20d7-133">指定是否啟用功能。</span><span class="sxs-lookup"><span data-stu-id="f20d7-133">Specifies whether the features are enabled.</span></span> <span data-ttu-id="f20d7-134">若要確保已啟用此功能，請將此屬性設定為 **Enable**。</span><span class="sxs-lookup"><span data-stu-id="f20d7-134">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="f20d7-135">若要確保已停用此功能，請將此屬性設定為 **Disable**。</span><span class="sxs-lookup"><span data-stu-id="f20d7-135">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="f20d7-136">預設值為 **Enable**。</span><span class="sxs-lookup"><span data-stu-id="f20d7-136">The default value is **Enable**.</span></span> |
|<span data-ttu-id="f20d7-137">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f20d7-137">PsDscRunAsCredential</span></span> |<span data-ttu-id="f20d7-138">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="f20d7-138">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f20d7-139">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="f20d7-139">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f20d7-140">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="f20d7-140">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
