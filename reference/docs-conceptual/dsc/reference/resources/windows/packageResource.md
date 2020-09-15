---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC 套件資源
ms.openlocfilehash: faeebc5bac7caad733600720f1c9f3d916d4c0a8
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464004"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="1f6a4-103">DSC 套件資源</span><span class="sxs-lookup"><span data-stu-id="1f6a4-103">DSC Package Resource</span></span>

> <span data-ttu-id="1f6a4-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="1f6a4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="1f6a4-105">Windows PowerShell 預期狀態設定 (DSC) 中的 **Package** 資源，提供一個機制在目標節點上安裝或解除安裝套件，例如 Windows Installer 和 setup.exe 套件。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f6a4-106">語法</span><span class="sxs-lookup"><span data-stu-id="1f6a4-106">Syntax</span></span>

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1f6a4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1f6a4-107">Properties</span></span>

|<span data-ttu-id="1f6a4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1f6a4-108">Property</span></span> |<span data-ttu-id="1f6a4-109">描述</span><span class="sxs-lookup"><span data-stu-id="1f6a4-109">Description</span></span> |
|---|---|
|<span data-ttu-id="1f6a4-110">名稱</span><span class="sxs-lookup"><span data-stu-id="1f6a4-110">Name</span></span> |<span data-ttu-id="1f6a4-111">指出您要確保其特定狀態的套件名稱。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="1f6a4-112">Path</span><span class="sxs-lookup"><span data-stu-id="1f6a4-112">Path</span></span> |<span data-ttu-id="1f6a4-113">指出套件所在的檔案路徑</span><span class="sxs-lookup"><span data-stu-id="1f6a4-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="1f6a4-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="1f6a4-114">ProductId</span></span> |<span data-ttu-id="1f6a4-115">指出唯一識別套件的產品識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="1f6a4-116">引數</span><span class="sxs-lookup"><span data-stu-id="1f6a4-116">Arguments</span></span> |<span data-ttu-id="1f6a4-117">列出將如同所提供來傳遞至套件的引數字串。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="1f6a4-118">認證</span><span class="sxs-lookup"><span data-stu-id="1f6a4-118">Credential</span></span> |<span data-ttu-id="1f6a4-119">提供遠端來源套件的存取權。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="1f6a4-120">這個屬性不會用於安裝套件。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-120">This property is not used to install the package.</span></span> <span data-ttu-id="1f6a4-121">在本機系統上一律安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="1f6a4-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="1f6a4-122">LogPath</span></span> |<span data-ttu-id="1f6a4-123">指出您想要提供者儲存記錄檔來安裝或解除安裝此套件的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="1f6a4-124">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="1f6a4-124">ReturnCode</span></span> |<span data-ttu-id="1f6a4-125">指出預期的傳回碼。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-125">Indicates the expected return code.</span></span> <span data-ttu-id="1f6a4-126">如果實際的傳回碼不符這裡提供的預期值，此設定就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1f6a4-127">通用屬性</span><span class="sxs-lookup"><span data-stu-id="1f6a4-127">Common properties</span></span>

|<span data-ttu-id="1f6a4-128">屬性</span><span class="sxs-lookup"><span data-stu-id="1f6a4-128">Property</span></span> |<span data-ttu-id="1f6a4-129">描述</span><span class="sxs-lookup"><span data-stu-id="1f6a4-129">Description</span></span> |
|---|---|
|<span data-ttu-id="1f6a4-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1f6a4-130">DependsOn</span></span> |<span data-ttu-id="1f6a4-131">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1f6a4-132">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1f6a4-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="1f6a4-133">Ensure</span></span> |<span data-ttu-id="1f6a4-134">指出是否要安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-134">Indicates if the package is installed.</span></span> <span data-ttu-id="1f6a4-135">將此屬性設定為 **Absent** 以確保不會安裝此套件 (或如果已安裝，請解除安裝此套件)。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="1f6a4-136">將其設定為 **Present** 以確保已安裝此套件。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="1f6a4-137">預設值為 **Present**。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="1f6a4-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1f6a4-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="1f6a4-139">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1f6a4-140">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1f6a4-141">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="1f6a4-142">範例</span><span class="sxs-lookup"><span data-stu-id="1f6a4-142">Example</span></span>

<span data-ttu-id="1f6a4-143">這個範例會執行 .msi 安裝程式，其位於指定路徑，且具有指定的產品識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f6a4-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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
