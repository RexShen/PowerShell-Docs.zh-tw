---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC WindowsOptionalFeatureSet 資源"
ms.openlocfilehash: 3bf6a993d0ec9ce71c1e9222ddaa3bb429accb15
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="0f468-103">DSC WindowsOptionalFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="0f468-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="0f468-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0f468-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0f468-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsOptionalFeatureSet** 資源提供一個機制，確保可在目標節點上啟用選用功能。</span><span class="sxs-lookup"><span data-stu-id="0f468-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="0f468-106">此資源是為 `Name` 屬性中指定的每項功能呼叫 [WindowsOptionalFeature 資源](windowsOptionalFeatureResource.md)的[複合資源](authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="0f468-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="0f468-107">當您想要將多個 Windows 選用功能設定成相同的狀態，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="0f468-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f468-108">語法</span><span class="sxs-lookup"><span data-stu-id="0f468-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="0f468-109">[內容]</span><span class="sxs-lookup"><span data-stu-id="0f468-109">Properties</span></span>

|  <span data-ttu-id="0f468-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0f468-110">Property</span></span>  |  <span data-ttu-id="0f468-111">描述</span><span class="sxs-lookup"><span data-stu-id="0f468-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="0f468-112">名稱</span><span class="sxs-lookup"><span data-stu-id="0f468-112">Name</span></span>| <span data-ttu-id="0f468-113">表示您想要確保啟用或停用的功能名稱。</span><span class="sxs-lookup"><span data-stu-id="0f468-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>| 
| <span data-ttu-id="0f468-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="0f468-114">Ensure</span></span>| <span data-ttu-id="0f468-115">指定是否啟用功能。</span><span class="sxs-lookup"><span data-stu-id="0f468-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="0f468-116">若要確保將功能啟用，請將此屬性設定為 "Enable"。若要確保將功能停用，請將此屬性設定為 "Disable"。</span><span class="sxs-lookup"><span data-stu-id="0f468-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="0f468-117">來源</span><span class="sxs-lookup"><span data-stu-id="0f468-117">Source</span></span>| <span data-ttu-id="0f468-118">未實作。</span><span class="sxs-lookup"><span data-stu-id="0f468-118">Not implemented.</span></span>|
| <span data-ttu-id="0f468-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="0f468-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="0f468-120">指定在搜尋來源檔案以啟用功能時，DISM 是否連絡 Windows Update (WU)。</span><span class="sxs-lookup"><span data-stu-id="0f468-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="0f468-121">如果是 $true，則 DISM 不連絡 WU。</span><span class="sxs-lookup"><span data-stu-id="0f468-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="0f468-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="0f468-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="0f468-123">停用時 (亦即 **Ensure** 設為 "Absent")，設為 **$true** 會移除所有與這些功能相關聯的檔案。</span><span class="sxs-lookup"><span data-stu-id="0f468-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="0f468-124">LogLevel</span><span class="sxs-lookup"><span data-stu-id="0f468-124">LogLevel</span></span>| <span data-ttu-id="0f468-125">記錄中顯示的最大輸出等級。</span><span class="sxs-lookup"><span data-stu-id="0f468-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="0f468-126">接受的值包括："ErrorsOnly" (僅記錄錯誤)、"ErrorsAndWarning" (記錄錯誤與警告)，以及 "ErrorsAndWarningAndInformation" (記錄錯誤、警告和偵錯資訊)。</span><span class="sxs-lookup"><span data-stu-id="0f468-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="0f468-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="0f468-127">LogPath</span></span>| <span data-ttu-id="0f468-128">要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="0f468-128">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="0f468-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0f468-129">DependsOn</span></span>| <span data-ttu-id="0f468-130">指定必須先執行另一項資源的設定，再設定這項資源。</span><span class="sxs-lookup"><span data-stu-id="0f468-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0f468-131">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="0f468-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



