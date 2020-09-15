---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC WindowsOptionalFeatureSet 資源
ms.openlocfilehash: e4f88f1cae6d7ddb3596ab4f27eb3766259f1a31
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464157"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="7f7f2-103">DSC WindowsOptionalFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="7f7f2-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="7f7f2-104">適用於：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="7f7f2-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="7f7f2-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsOptionalFeatureSet** 資源提供一個機制，確保可在目標節點上啟用選用功能。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="7f7f2-106">此資源是針對**Name** 屬性中所指定每項功能呼叫 [WindowsOptionalFeature 資源](windowsOptionalFeatureResource.md)的[複合資源](../../../resources/authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="7f7f2-107">當您想要將多個 Windows 選用功能設定成相同的狀態，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f7f2-108">語法</span><span class="sxs-lookup"><span data-stu-id="7f7f2-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7f7f2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7f7f2-109">Properties</span></span>

|<span data-ttu-id="7f7f2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7f7f2-110">Property</span></span> |<span data-ttu-id="7f7f2-111">描述</span><span class="sxs-lookup"><span data-stu-id="7f7f2-111">Description</span></span> |
|---|---|
|<span data-ttu-id="7f7f2-112">名稱</span><span class="sxs-lookup"><span data-stu-id="7f7f2-112">Name</span></span> |<span data-ttu-id="7f7f2-113">表示您想要確保啟用或停用的功能名稱。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="7f7f2-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="7f7f2-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="7f7f2-115">指定在搜尋來源檔案以啟用功能時，DISM 是否連絡 Windows Update (WU)。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="7f7f2-116">若為 `$true`，則 DISM 不連絡 WU。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="7f7f2-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="7f7f2-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="7f7f2-118">當 **Ensure** 設定為 **Absent** 時，設定為 `$true` 可移除與此功能建立關聯的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-118">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="7f7f2-119">LogLevel</span><span class="sxs-lookup"><span data-stu-id="7f7f2-119">LogLevel</span></span> |<span data-ttu-id="7f7f2-120">記錄中顯示的最大輸出等級。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="7f7f2-121">接受的值為：**ErrorsOnly**、**ErrorsAndWarning** 和 **ErrorsAndWarningAndInformation**。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="7f7f2-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="7f7f2-122">LogPath</span></span> |<span data-ttu-id="7f7f2-123">要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7f7f2-124">通用屬性</span><span class="sxs-lookup"><span data-stu-id="7f7f2-124">Common properties</span></span>

|<span data-ttu-id="7f7f2-125">屬性</span><span class="sxs-lookup"><span data-stu-id="7f7f2-125">Property</span></span> |<span data-ttu-id="7f7f2-126">描述</span><span class="sxs-lookup"><span data-stu-id="7f7f2-126">Description</span></span> |
|---|---|
|<span data-ttu-id="7f7f2-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7f7f2-127">DependsOn</span></span> |<span data-ttu-id="7f7f2-128">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7f7f2-129">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7f7f2-130">Ensure</span><span class="sxs-lookup"><span data-stu-id="7f7f2-130">Ensure</span></span> |<span data-ttu-id="7f7f2-131">指定是否啟用功能。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-131">Specifies whether the features are enabled.</span></span> <span data-ttu-id="7f7f2-132">若要確保已啟用此功能，請將此屬性設定為 **Enable**。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-132">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="7f7f2-133">若要確保已停用此功能，請將此屬性設定為 **Disable**。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-133">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="7f7f2-134">預設值為 **Enable**。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-134">The default value is **Enable**.</span></span> |
|<span data-ttu-id="7f7f2-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7f7f2-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="7f7f2-136">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7f7f2-137">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7f7f2-138">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="7f7f2-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
