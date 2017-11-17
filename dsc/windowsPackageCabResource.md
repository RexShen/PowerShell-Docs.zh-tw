---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC WindowsPackageCab 資源"
ms.openlocfilehash: 9b1bf3cb95abcbe46976ae0fd328280a3a8d7f28
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="b57f7-103">DSC WindowsPackageCab 資源</span><span class="sxs-lookup"><span data-stu-id="b57f7-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="b57f7-104">適用於︰Windows PowerShell 5.1 及更新版本</span><span class="sxs-lookup"><span data-stu-id="b57f7-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="b57f7-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **WindowsPackageCab** 資源提供一個機制，可在目標節點上安裝或解除安裝 Windows 封包 (.cab) 套件。</span><span class="sxs-lookup"><span data-stu-id="b57f7-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="b57f7-106">目標節點上必須安裝 DISM PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="b57f7-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="b57f7-107">如需相關資訊，請參閱[在 Windows PowerShell 中使用 DISM](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14)。</span><span class="sxs-lookup"><span data-stu-id="b57f7-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span> 


## <a name="syntax"></a><span data-ttu-id="b57f7-108">語法</span><span class="sxs-lookup"><span data-stu-id="b57f7-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="b57f7-109">[內容]</span><span class="sxs-lookup"><span data-stu-id="b57f7-109">Properties</span></span>

|  <span data-ttu-id="b57f7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b57f7-110">Property</span></span>  |  <span data-ttu-id="b57f7-111">描述</span><span class="sxs-lookup"><span data-stu-id="b57f7-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="b57f7-112">名稱</span><span class="sxs-lookup"><span data-stu-id="b57f7-112">Name</span></span>| <span data-ttu-id="b57f7-113">指出您想要確保其特定狀態的套件名稱。</span><span class="sxs-lookup"><span data-stu-id="b57f7-113">Indicates the name of the package for you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="b57f7-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="b57f7-114">Ensure</span></span>| <span data-ttu-id="b57f7-115">指出是否要安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="b57f7-115">Indicates if the package is installed.</span></span> <span data-ttu-id="b57f7-116">設定此屬性為 "Absent" 以確保不會安裝此套件 (或如果已安裝，則解除安裝此套件)。</span><span class="sxs-lookup"><span data-stu-id="b57f7-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="b57f7-117">將它設定為 "Present" (預設值) 以確保已安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="b57f7-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="b57f7-118">路徑</span><span class="sxs-lookup"><span data-stu-id="b57f7-118">Path</span></span>| <span data-ttu-id="b57f7-119">指出套件所在的檔案路徑</span><span class="sxs-lookup"><span data-stu-id="b57f7-119">Indicates the path where the package resides.</span></span>| 
| <span data-ttu-id="b57f7-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="b57f7-120">LogPath</span></span>| <span data-ttu-id="b57f7-121">指出您想要提供者儲存記錄檔來安裝或解除安裝此套件的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b57f7-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>| 
| <span data-ttu-id="b57f7-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b57f7-122">DependsOn</span></span> | <span data-ttu-id="b57f7-123">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="b57f7-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b57f7-124">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="b57f7-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example"></a><span data-ttu-id="b57f7-125">範例</span><span class="sxs-lookup"><span data-stu-id="b57f7-125">Example</span></span>

<span data-ttu-id="b57f7-126">以下範例設定會接受輸入參數，並確保安裝 `$Name` 參數所指定的 .cab 檔案。</span><span class="sxs-lookup"><span data-stu-id="b57f7-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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

