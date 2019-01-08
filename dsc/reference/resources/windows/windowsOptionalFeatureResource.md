---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC WindowsOptionalFeature 資源
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047330"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="48d1b-103">DSC WindowsOptionalFeature 資源</span><span class="sxs-lookup"><span data-stu-id="48d1b-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="48d1b-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="48d1b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="48d1b-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsOptionalFeature** 資源提供一個機制，確保可在目標節點上啟用選用功能。</span><span class="sxs-lookup"><span data-stu-id="48d1b-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="48d1b-106">語法</span><span class="sxs-lookup"><span data-stu-id="48d1b-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="48d1b-107">Properties</span><span class="sxs-lookup"><span data-stu-id="48d1b-107">Properties</span></span>

|  <span data-ttu-id="48d1b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="48d1b-108">Property</span></span>  |  <span data-ttu-id="48d1b-109">描述</span><span class="sxs-lookup"><span data-stu-id="48d1b-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="48d1b-110">名稱</span><span class="sxs-lookup"><span data-stu-id="48d1b-110">Name</span></span>| <span data-ttu-id="48d1b-111">表示您想要確保啟用或停用的功能名稱。</span><span class="sxs-lookup"><span data-stu-id="48d1b-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="48d1b-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="48d1b-112">Ensure</span></span>| <span data-ttu-id="48d1b-113">指定是否啟用功能。</span><span class="sxs-lookup"><span data-stu-id="48d1b-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="48d1b-114">若要確保將功能啟用，請將此屬性設定為 "Enable"。若要確保將功能停用，請將此屬性設定為 "Disable"。</span><span class="sxs-lookup"><span data-stu-id="48d1b-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="48d1b-115">來源</span><span class="sxs-lookup"><span data-stu-id="48d1b-115">Source</span></span>| <span data-ttu-id="48d1b-116">未實作。</span><span class="sxs-lookup"><span data-stu-id="48d1b-116">Not implemented.</span></span>|
| <span data-ttu-id="48d1b-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="48d1b-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="48d1b-118">指定在搜尋來源檔案以啟用功能時，DISM 是否連絡 Windows Update (WU)。</span><span class="sxs-lookup"><span data-stu-id="48d1b-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="48d1b-119">如果是 $true，則 DISM 不連絡 WU。</span><span class="sxs-lookup"><span data-stu-id="48d1b-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="48d1b-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="48d1b-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="48d1b-121">停用時 (亦即 **Ensure** 設為 "Absent")，設為 **$true** 會移除所有與此功能相關聯的檔案。</span><span class="sxs-lookup"><span data-stu-id="48d1b-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="48d1b-122">LogLevel</span><span class="sxs-lookup"><span data-stu-id="48d1b-122">LogLevel</span></span>| <span data-ttu-id="48d1b-123">記錄中顯示的最大輸出等級。</span><span class="sxs-lookup"><span data-stu-id="48d1b-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="48d1b-124">接受的值包括："ErrorsOnly"（僅記錄錯誤）、"ErrorsAndWarning"（記錄錯誤與警告），和"ErrorsAndWarningAndInformation"（錯誤、 警告和偵錯資訊已登入）。</span><span class="sxs-lookup"><span data-stu-id="48d1b-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="48d1b-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="48d1b-125">LogPath</span></span>| <span data-ttu-id="48d1b-126">要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="48d1b-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="48d1b-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="48d1b-127">DependsOn</span></span>| <span data-ttu-id="48d1b-128">指定必須先執行另一項資源的設定，再設定這項資源。</span><span class="sxs-lookup"><span data-stu-id="48d1b-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="48d1b-129">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="48d1b-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|