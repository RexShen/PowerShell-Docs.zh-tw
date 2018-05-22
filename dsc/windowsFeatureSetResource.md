---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC WindowsFeatureSet 資源
ms.openlocfilehash: 582f9b1f439056118680f6f814d2c202d0e823be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="b87cf-103">DSC WindowsFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="b87cf-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="b87cf-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b87cf-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b87cf-105">Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsFeatureSet** 資源提供一個機制，確保可在目標節點上新增或移除角色和功能。</span><span class="sxs-lookup"><span data-stu-id="b87cf-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="b87cf-106">此資源是為 `Name` 屬性中指定的每項功能呼叫 [WindowsFeature 資源](windowsfeatureResource.md)的[複合資源](authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="b87cf-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="b87cf-107">當您想要將多個 Windows 功能設定成相同的狀態，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="b87cf-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="b87cf-108">語法</span><span class="sxs-lookup"><span data-stu-id="b87cf-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="b87cf-109">Properties</span><span class="sxs-lookup"><span data-stu-id="b87cf-109">Properties</span></span>

|  <span data-ttu-id="b87cf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b87cf-110">Property</span></span>  |  <span data-ttu-id="b87cf-111">描述</span><span class="sxs-lookup"><span data-stu-id="b87cf-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="b87cf-112">名稱</span><span class="sxs-lookup"><span data-stu-id="b87cf-112">Name</span></span>| <span data-ttu-id="b87cf-113">您想要確保新增或移除的角色或功能名稱。</span><span class="sxs-lookup"><span data-stu-id="b87cf-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="b87cf-114">這與 [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) Cmdlet 的 **Name** 屬性相同，且不是角色或功能的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="b87cf-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="b87cf-115">認證</span><span class="sxs-lookup"><span data-stu-id="b87cf-115">Credential</span></span>| <span data-ttu-id="b87cf-116">用以新增或移除角色或功能的認證。</span><span class="sxs-lookup"><span data-stu-id="b87cf-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="b87cf-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="b87cf-117">Ensure</span></span>| <span data-ttu-id="b87cf-118">表示是否已新增角色或功能。</span><span class="sxs-lookup"><span data-stu-id="b87cf-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="b87cf-119">若要確保新增角色或功能，這個屬性請設為 "Present"。若要確保移除角色或功能，請將屬性設定為 "Absent"。</span><span class="sxs-lookup"><span data-stu-id="b87cf-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="b87cf-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="b87cf-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="b87cf-121">這個屬性設為 **$true** 可讓您使用以 **Name** 屬性指定的功能包含所有必要的子功能。</span><span class="sxs-lookup"><span data-stu-id="b87cf-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="b87cf-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="b87cf-122">LogPath</span></span>| <span data-ttu-id="b87cf-123">要讓資源提供者記錄作業的記錄檔路徑。</span><span class="sxs-lookup"><span data-stu-id="b87cf-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="b87cf-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b87cf-124">DependsOn</span></span>| <span data-ttu-id="b87cf-125">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="b87cf-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b87cf-126">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="b87cf-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="b87cf-127">來源</span><span class="sxs-lookup"><span data-stu-id="b87cf-127">Source</span></span>| <span data-ttu-id="b87cf-128">如有必要，表示用於安裝的來源檔案位置。</span><span class="sxs-lookup"><span data-stu-id="b87cf-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="b87cf-129">範例</span><span class="sxs-lookup"><span data-stu-id="b87cf-129">Example</span></span>

<span data-ttu-id="b87cf-130">下列設定可確保安裝 **Web 伺服器** (IIS) 和 **SMTP 伺服器**功能及其各自的所有子功能。</span><span class="sxs-lookup"><span data-stu-id="b87cf-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```