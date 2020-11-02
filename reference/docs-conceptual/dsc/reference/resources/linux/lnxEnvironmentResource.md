---
ms.date: 07/17/2020
ms.topic: reference
title: DSC for Linux nxEnvironment 資源
description: DSC for Linux nxEnvironment 資源
ms.openlocfilehash: 86ed538732254967cb4a3bb55af4f6b179947e52
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644667"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="6a910-103">DSC for Linux nxEnvironment 資源</span><span class="sxs-lookup"><span data-stu-id="6a910-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="6a910-104">PowerShell 預期狀態設定 (DSC) 的 **nxEnvironment** 資源會提供在 Linux 節點上管理系統環境變數的機制。</span><span class="sxs-lookup"><span data-stu-id="6a910-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a910-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a910-105">Syntax</span></span>

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="6a910-106">屬性</span><span class="sxs-lookup"><span data-stu-id="6a910-106">Properties</span></span>

|<span data-ttu-id="6a910-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6a910-107">Property</span></span> |<span data-ttu-id="6a910-108">描述</span><span class="sxs-lookup"><span data-stu-id="6a910-108">Description</span></span> |
|---|---|
|<span data-ttu-id="6a910-109">名稱</span><span class="sxs-lookup"><span data-stu-id="6a910-109">Name</span></span> |<span data-ttu-id="6a910-110">指出您要確保其特定狀態的環境變數名稱。</span><span class="sxs-lookup"><span data-stu-id="6a910-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="6a910-111">值</span><span class="sxs-lookup"><span data-stu-id="6a910-111">Value</span></span> |<span data-ttu-id="6a910-112">要指派給環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="6a910-112">The value to assign to the environment variable.</span></span> |
|<span data-ttu-id="6a910-113">Path</span><span class="sxs-lookup"><span data-stu-id="6a910-113">Path</span></span> |<span data-ttu-id="6a910-114">定義設定中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="6a910-114">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="6a910-115">如果變數是 **Path** 變數，請將這個屬性設定為 `$true`；否則請設定為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="6a910-115">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="6a910-116">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="6a910-116">The default is `$false`.</span></span> <span data-ttu-id="6a910-117">如果要設定的變數是 **Path** 變數，則透過 **Value** 屬性提供的值就會附加至現有的值。</span><span class="sxs-lookup"><span data-stu-id="6a910-117">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6a910-118">通用屬性</span><span class="sxs-lookup"><span data-stu-id="6a910-118">Common properties</span></span>

|<span data-ttu-id="6a910-119">屬性</span><span class="sxs-lookup"><span data-stu-id="6a910-119">Property</span></span> |<span data-ttu-id="6a910-120">描述</span><span class="sxs-lookup"><span data-stu-id="6a910-120">Description</span></span> |
|---|---|
|<span data-ttu-id="6a910-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6a910-121">DependsOn</span></span> |<span data-ttu-id="6a910-122">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="6a910-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6a910-123">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="6a910-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="6a910-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="6a910-124">Ensure</span></span> |<span data-ttu-id="6a910-125">決定是否要檢查變數存在。</span><span class="sxs-lookup"><span data-stu-id="6a910-125">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="6a910-126">將此屬性設定為 **Present** 以確保變數存在。</span><span class="sxs-lookup"><span data-stu-id="6a910-126">Set this property to **Present** to ensure the variable exists.</span></span> <span data-ttu-id="6a910-127">將其設定為 **Absent** 以確保此變數不存在。</span><span class="sxs-lookup"><span data-stu-id="6a910-127">Set it to **Absent** to ensure the variable does not exist.</span></span> <span data-ttu-id="6a910-128">預設值為 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="6a910-128">The default value is **Present** .</span></span> |

## <a name="additional-information"></a><span data-ttu-id="6a910-129">其他資訊</span><span class="sxs-lookup"><span data-stu-id="6a910-129">Additional Information</span></span>

- <span data-ttu-id="6a910-130">如果 **Path** 不存在，或設定為 `$false`，則環境變數會在 `/etc/environment` 中受到管理。</span><span class="sxs-lookup"><span data-stu-id="6a910-130">If **Path** is absent or set to `$false`, environment variables are managed in `/etc/environment`.</span></span>
  <span data-ttu-id="6a910-131">您的程式或指令碼可能需要設定為以 `/etc/environment` 檔為來源，以存取受管理的環境變數。</span><span class="sxs-lookup"><span data-stu-id="6a910-131">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
- <span data-ttu-id="6a910-132">如果 **Path** 設定為 `$true`，則環境變數會在檔案 `/etc/profile.d/DSCenvironment.sh` 中受到管理。</span><span class="sxs-lookup"><span data-stu-id="6a910-132">If **Path** is set to `$true`, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="6a910-133">如果不存在，則會建立這個檔案。</span><span class="sxs-lookup"><span data-stu-id="6a910-133">This file will be created if it does not exist.</span></span> <span data-ttu-id="6a910-134">如果 **Ensure** 設定成 **Absent** ，而 **Path** 設定成 `$true`，則現有的環境變數只會從 `/etc/profile.d/DSCenvironment.sh` 中移除，而不會從其他檔案中移除。</span><span class="sxs-lookup"><span data-stu-id="6a910-134">If **Ensure** is set to **Absent** and **Path** is set to `$true`, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="6a910-135">範例</span><span class="sxs-lookup"><span data-stu-id="6a910-135">Example</span></span>

<span data-ttu-id="6a910-136">下列範例示範如何使用 **nxEnvironment** 資源以確保 **TestEnvironmentVariable** 存在且具有值 "Test-Value"。</span><span class="sxs-lookup"><span data-stu-id="6a910-136">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="6a910-137">如果 **TestEnvironmentVariable** 不存在，就會加以建立。</span><span class="sxs-lookup"><span data-stu-id="6a910-137">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
