---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC WindowsOptionalFeature 資源
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954645"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="85ab0-103">DSC WindowsOptionalFeature 資源</span><span class="sxs-lookup"><span data-stu-id="85ab0-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="85ab0-104">適用於：Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="85ab0-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="85ab0-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsOptionalFeature** 資源提供一個機制，確保可在目標節點上啟用選用功能。</span><span class="sxs-lookup"><span data-stu-id="85ab0-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="85ab0-106">語法</span><span class="sxs-lookup"><span data-stu-id="85ab0-106">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="85ab0-107">Properties</span><span class="sxs-lookup"><span data-stu-id="85ab0-107">Properties</span></span>

|<span data-ttu-id="85ab0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="85ab0-108">Property</span></span> |<span data-ttu-id="85ab0-109">描述</span><span class="sxs-lookup"><span data-stu-id="85ab0-109">Description</span></span> |
|---|---|
|<span data-ttu-id="85ab0-110">名稱</span><span class="sxs-lookup"><span data-stu-id="85ab0-110">Name</span></span> |<span data-ttu-id="85ab0-111">表示您想要確保啟用或停用的功能名稱。</span><span class="sxs-lookup"><span data-stu-id="85ab0-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="85ab0-112">來源</span><span class="sxs-lookup"><span data-stu-id="85ab0-112">Source</span></span> |<span data-ttu-id="85ab0-113">未實作。</span><span class="sxs-lookup"><span data-stu-id="85ab0-113">Not implemented.</span></span> |
|<span data-ttu-id="85ab0-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="85ab0-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="85ab0-115">指定在搜尋來源檔案以啟用功能時，DISM 是否連絡 Windows Update (WU)。</span><span class="sxs-lookup"><span data-stu-id="85ab0-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="85ab0-116">若為 `$true`，則 DISM 不連絡 WU。</span><span class="sxs-lookup"><span data-stu-id="85ab0-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="85ab0-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="85ab0-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="85ab0-118">當 **Ensure** 設定為 **Absent** 時，設定為 `$true` 可移除與此功能建立關聯的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="85ab0-118">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="85ab0-119">LogLevel</span><span class="sxs-lookup"><span data-stu-id="85ab0-119">LogLevel</span></span> |<span data-ttu-id="85ab0-120">記錄中顯示的最大輸出等級。</span><span class="sxs-lookup"><span data-stu-id="85ab0-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="85ab0-121">接受的值為：**ErrorsOnly**、**ErrorsAndWarning** 和 **ErrorsAndWarningAndInformation**。</span><span class="sxs-lookup"><span data-stu-id="85ab0-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="85ab0-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="85ab0-122">LogPath</span></span> |<span data-ttu-id="85ab0-123">要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="85ab0-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="85ab0-124">通用屬性</span><span class="sxs-lookup"><span data-stu-id="85ab0-124">Common properties</span></span>

|<span data-ttu-id="85ab0-125">屬性</span><span class="sxs-lookup"><span data-stu-id="85ab0-125">Property</span></span> |<span data-ttu-id="85ab0-126">描述</span><span class="sxs-lookup"><span data-stu-id="85ab0-126">Description</span></span> |
|---|---|
|<span data-ttu-id="85ab0-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="85ab0-127">DependsOn</span></span> |<span data-ttu-id="85ab0-128">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="85ab0-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="85ab0-129">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="85ab0-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="85ab0-130">Ensure</span><span class="sxs-lookup"><span data-stu-id="85ab0-130">Ensure</span></span> |<span data-ttu-id="85ab0-131">指定是否啟用功能。</span><span class="sxs-lookup"><span data-stu-id="85ab0-131">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="85ab0-132">若要確保已啟用此功能，請將此屬性設定為 _Enable_。</span><span class="sxs-lookup"><span data-stu-id="85ab0-132">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="85ab0-133">若要確保已停用此功能，請將此屬性設定為 _Disable_。</span><span class="sxs-lookup"><span data-stu-id="85ab0-133">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="85ab0-134">預設值為 _Enable_。</span><span class="sxs-lookup"><span data-stu-id="85ab0-134">The default value is _Enable_.</span></span> |
|<span data-ttu-id="85ab0-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="85ab0-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="85ab0-136">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="85ab0-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="85ab0-137">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="85ab0-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="85ab0-138">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="85ab0-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>