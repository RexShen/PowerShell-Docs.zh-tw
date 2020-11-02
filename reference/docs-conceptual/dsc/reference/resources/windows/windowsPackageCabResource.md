---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsPackageCab 資源
description: DSC WindowsPackageCab 資源
ms.openlocfilehash: 3ac10eb2a7da502b8cac23ab8bfee869a4e26fd3
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143019"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="13d43-103">DSC WindowsPackageCab 資源</span><span class="sxs-lookup"><span data-stu-id="13d43-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="13d43-104">適用於：Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="13d43-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="13d43-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **WindowsPackageCab** 資源提供一個機制，可在目標節點上安裝或解除安裝 Windows 封包 (.cab) 套件。</span><span class="sxs-lookup"><span data-stu-id="13d43-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="13d43-106">目標節點上必須安裝 DISM PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="13d43-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="13d43-107">如需相關資訊，請參閱[在 Windows PowerShell 中使用 DISM](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14)。</span><span class="sxs-lookup"><span data-stu-id="13d43-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="13d43-108">語法</span><span class="sxs-lookup"><span data-stu-id="13d43-108">Syntax</span></span>

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="13d43-109">屬性</span><span class="sxs-lookup"><span data-stu-id="13d43-109">Properties</span></span>

|<span data-ttu-id="13d43-110">屬性</span><span class="sxs-lookup"><span data-stu-id="13d43-110">Property</span></span> |<span data-ttu-id="13d43-111">描述</span><span class="sxs-lookup"><span data-stu-id="13d43-111">Description</span></span> |
|---|---|
|<span data-ttu-id="13d43-112">名稱</span><span class="sxs-lookup"><span data-stu-id="13d43-112">Name</span></span> |<span data-ttu-id="13d43-113">指出您想要確保其特定狀態的套件名稱。</span><span class="sxs-lookup"><span data-stu-id="13d43-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="13d43-114">SourcePath</span><span class="sxs-lookup"><span data-stu-id="13d43-114">SourcePath</span></span> |<span data-ttu-id="13d43-115">指出套件所在的檔案路徑</span><span class="sxs-lookup"><span data-stu-id="13d43-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="13d43-116">LogPath</span><span class="sxs-lookup"><span data-stu-id="13d43-116">LogPath</span></span> |<span data-ttu-id="13d43-117">指出您想要提供者儲存記錄檔來安裝或解除安裝此套件的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="13d43-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="13d43-118">通用屬性</span><span class="sxs-lookup"><span data-stu-id="13d43-118">Common properties</span></span>

|<span data-ttu-id="13d43-119">屬性</span><span class="sxs-lookup"><span data-stu-id="13d43-119">Property</span></span> |<span data-ttu-id="13d43-120">描述</span><span class="sxs-lookup"><span data-stu-id="13d43-120">Description</span></span> |
|---|---|
|<span data-ttu-id="13d43-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="13d43-121">DependsOn</span></span> |<span data-ttu-id="13d43-122">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="13d43-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="13d43-123">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="13d43-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="13d43-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="13d43-124">Ensure</span></span> |<span data-ttu-id="13d43-125">指出是否要安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="13d43-125">Indicates if the package is installed.</span></span> <span data-ttu-id="13d43-126">將此屬性設定為 **Absent** 以確保不會安裝此套件 (或如果已安裝，請解除安裝此套件)。</span><span class="sxs-lookup"><span data-stu-id="13d43-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="13d43-127">將其設定為 **Present** 以確保已安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="13d43-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="13d43-128">**Ensure** 是 **WindowsPackageCab** 資源上的必要屬性。</span><span class="sxs-lookup"><span data-stu-id="13d43-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="13d43-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="13d43-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="13d43-130">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="13d43-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="13d43-131">範例</span><span class="sxs-lookup"><span data-stu-id="13d43-131">Example</span></span>

<span data-ttu-id="13d43-132">以下範例設定會接受輸入參數，並確保安裝 `$Name` 參數所指定的 .cab 檔案。</span><span class="sxs-lookup"><span data-stu-id="13d43-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```
