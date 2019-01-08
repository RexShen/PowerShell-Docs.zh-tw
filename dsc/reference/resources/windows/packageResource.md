---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 套件資源
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047143"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="eb397-103">DSC 套件資源</span><span class="sxs-lookup"><span data-stu-id="eb397-103">DSC Package Resource</span></span>

<span data-ttu-id="eb397-104">適用於：Windows PowerShell 4.0 中，Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="eb397-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="eb397-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **Package** 資源，提供一個機制在目標節點上安裝或解除安裝套件，例如 Windows Installer 和 setup.exe 套件。</span><span class="sxs-lookup"><span data-stu-id="eb397-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb397-106">語法</span><span class="sxs-lookup"><span data-stu-id="eb397-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="eb397-107">Properties</span><span class="sxs-lookup"><span data-stu-id="eb397-107">Properties</span></span>

| <span data-ttu-id="eb397-108">屬性</span><span class="sxs-lookup"><span data-stu-id="eb397-108">Property</span></span> | <span data-ttu-id="eb397-109">描述</span><span class="sxs-lookup"><span data-stu-id="eb397-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="eb397-110">名稱</span><span class="sxs-lookup"><span data-stu-id="eb397-110">Name</span></span>| <span data-ttu-id="eb397-111">指出您要確保其特定狀態的套件名稱。</span><span class="sxs-lookup"><span data-stu-id="eb397-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="eb397-112">路徑</span><span class="sxs-lookup"><span data-stu-id="eb397-112">Path</span></span>| <span data-ttu-id="eb397-113">指出套件所在的檔案路徑</span><span class="sxs-lookup"><span data-stu-id="eb397-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="eb397-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="eb397-114">ProductId</span></span>| <span data-ttu-id="eb397-115">指出唯一識別套件的產品識別碼。</span><span class="sxs-lookup"><span data-stu-id="eb397-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="eb397-116">引數</span><span class="sxs-lookup"><span data-stu-id="eb397-116">Arguments</span></span>| <span data-ttu-id="eb397-117">列出將如同所提供來傳遞至套件的引數字串。</span><span class="sxs-lookup"><span data-stu-id="eb397-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="eb397-118">認證</span><span class="sxs-lookup"><span data-stu-id="eb397-118">Credential</span></span>| <span data-ttu-id="eb397-119">提供遠端來源套件的存取權。</span><span class="sxs-lookup"><span data-stu-id="eb397-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="eb397-120">這個屬性不會用於安裝套件。</span><span class="sxs-lookup"><span data-stu-id="eb397-120">This property is not used to install the package.</span></span> <span data-ttu-id="eb397-121">在本機系統上一律安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="eb397-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="eb397-122">Ensure</span><span class="sxs-lookup"><span data-stu-id="eb397-122">Ensure</span></span>| <span data-ttu-id="eb397-123">指出是否要安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="eb397-123">Indicates if the package is installed.</span></span> <span data-ttu-id="eb397-124">設定此屬性為 "Absent" 以確保不會安裝此套件 (或如果已安裝，則解除安裝此套件)。</span><span class="sxs-lookup"><span data-stu-id="eb397-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="eb397-125">將它設定為 "Present" (預設值) 以確保已安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="eb397-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="eb397-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="eb397-126">LogPath</span></span>| <span data-ttu-id="eb397-127">指出您想要提供者儲存記錄檔來安裝或解除安裝此套件的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="eb397-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="eb397-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="eb397-128">DependsOn</span></span> | <span data-ttu-id="eb397-129">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="eb397-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="eb397-130">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="eb397-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="eb397-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="eb397-131">ReturnCode</span></span>| <span data-ttu-id="eb397-132">指出預期的傳回碼。</span><span class="sxs-lookup"><span data-stu-id="eb397-132">Indicates the expected return code.</span></span> <span data-ttu-id="eb397-133">如果實際的傳回碼不符這裡提供的預期值，此設定就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="eb397-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="eb397-134">範例</span><span class="sxs-lookup"><span data-stu-id="eb397-134">Example</span></span>

<span data-ttu-id="eb397-135">這個範例會執行 .msi 安裝程式，其位於指定路徑，且具有指定的產品識別碼。</span><span class="sxs-lookup"><span data-stu-id="eb397-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```