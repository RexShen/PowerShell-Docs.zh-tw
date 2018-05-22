---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC WindowsOptionalFeature 資源
ms.openlocfilehash: 1866bc9cd2194a62de23eaabee8a9c5049a84946
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="7dc70-103">DSC WindowsOptionalFeature 資源</span><span class="sxs-lookup"><span data-stu-id="7dc70-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="7dc70-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7dc70-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7dc70-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsOptionalFeature** 資源提供一個機制，確保可在目標節點上啟用選用功能。</span><span class="sxs-lookup"><span data-stu-id="7dc70-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7dc70-106">語法</span><span class="sxs-lookup"><span data-stu-id="7dc70-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="7dc70-107">Properties</span><span class="sxs-lookup"><span data-stu-id="7dc70-107">Properties</span></span>

|  <span data-ttu-id="7dc70-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7dc70-108">Property</span></span>  |  <span data-ttu-id="7dc70-109">描述</span><span class="sxs-lookup"><span data-stu-id="7dc70-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="7dc70-110">名稱</span><span class="sxs-lookup"><span data-stu-id="7dc70-110">Name</span></span>| <span data-ttu-id="7dc70-111">表示您想要確保啟用或停用的功能名稱。</span><span class="sxs-lookup"><span data-stu-id="7dc70-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="7dc70-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="7dc70-112">Ensure</span></span>| <span data-ttu-id="7dc70-113">指定是否啟用功能。</span><span class="sxs-lookup"><span data-stu-id="7dc70-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="7dc70-114">若要確保將功能啟用，請將此屬性設定為 "Enable"。若要確保將功能停用，請將此屬性設定為 "Disable"。</span><span class="sxs-lookup"><span data-stu-id="7dc70-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="7dc70-115">來源</span><span class="sxs-lookup"><span data-stu-id="7dc70-115">Source</span></span>| <span data-ttu-id="7dc70-116">未實作。</span><span class="sxs-lookup"><span data-stu-id="7dc70-116">Not implemented.</span></span>|
| <span data-ttu-id="7dc70-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="7dc70-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="7dc70-118">指定在搜尋來源檔案以啟用功能時，DISM 是否連絡 Windows Update (WU)。</span><span class="sxs-lookup"><span data-stu-id="7dc70-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="7dc70-119">如果是 $true，則 DISM 不連絡 WU。</span><span class="sxs-lookup"><span data-stu-id="7dc70-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="7dc70-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="7dc70-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="7dc70-121">停用時 (亦即 **Ensure** 設為 "Absent")，設為 **$true** 會移除所有與此功能相關聯的檔案。</span><span class="sxs-lookup"><span data-stu-id="7dc70-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="7dc70-122">LogLevel</span><span class="sxs-lookup"><span data-stu-id="7dc70-122">LogLevel</span></span>| <span data-ttu-id="7dc70-123">記錄中顯示的最大輸出等級。</span><span class="sxs-lookup"><span data-stu-id="7dc70-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="7dc70-124">接受的值包括："ErrorsOnly" (僅記錄錯誤)、"ErrorsAndWarning" (記錄錯誤與警告)，以及 "ErrorsAndWarningAndInformation" (記錄錯誤、警告和偵錯資訊)。</span><span class="sxs-lookup"><span data-stu-id="7dc70-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="7dc70-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="7dc70-125">LogPath</span></span>| <span data-ttu-id="7dc70-126">要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="7dc70-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="7dc70-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7dc70-127">DependsOn</span></span>| <span data-ttu-id="7dc70-128">指定必須先執行另一項資源的設定，再設定這項資源。</span><span class="sxs-lookup"><span data-stu-id="7dc70-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7dc70-129">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="7dc70-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|