---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxEnvironment 資源
ms.openlocfilehash: 3c9f39760e0fba7fac060f29f9e808a3a434401f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189477"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="f4d73-103">DSC for Linux nxEnvironment 資源</span><span class="sxs-lookup"><span data-stu-id="f4d73-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="f4d73-104">PowerShell 預期狀態設定 (DSC) 的 **nxEnvironment** 資源會提供在 Linux 節點上管理系統環境變數的機制。</span><span class="sxs-lookup"><span data-stu-id="f4d73-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4d73-105">語法</span><span class="sxs-lookup"><span data-stu-id="f4d73-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="f4d73-106">Properties</span><span class="sxs-lookup"><span data-stu-id="f4d73-106">Properties</span></span>

|  <span data-ttu-id="f4d73-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f4d73-107">Property</span></span> |  <span data-ttu-id="f4d73-108">描述</span><span class="sxs-lookup"><span data-stu-id="f4d73-108">Description</span></span> |
|---|---|
| <span data-ttu-id="f4d73-109">名稱</span><span class="sxs-lookup"><span data-stu-id="f4d73-109">Name</span></span>| <span data-ttu-id="f4d73-110">指出您要確保其特定狀態的環境變數名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d73-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="f4d73-111">值</span><span class="sxs-lookup"><span data-stu-id="f4d73-111">Value</span></span>| <span data-ttu-id="f4d73-112">要指派給環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="f4d73-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="f4d73-113">Ensure</span><span class="sxs-lookup"><span data-stu-id="f4d73-113">Ensure</span></span>| <span data-ttu-id="f4d73-114">決定是否要檢查變數存在。</span><span class="sxs-lookup"><span data-stu-id="f4d73-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="f4d73-115">將此屬性設定為 "Present" 以確保變數存在。</span><span class="sxs-lookup"><span data-stu-id="f4d73-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="f4d73-116">設為 "Absent" 以確保此變數不存在。</span><span class="sxs-lookup"><span data-stu-id="f4d73-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="f4d73-117">預設值為 "Present"。</span><span class="sxs-lookup"><span data-stu-id="f4d73-117">The default value is "Present".</span></span>|
| <span data-ttu-id="f4d73-118">路徑</span><span class="sxs-lookup"><span data-stu-id="f4d73-118">Path</span></span>| <span data-ttu-id="f4d73-119">定義設定中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="f4d73-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="f4d73-120">如果變數是 **Path** 變數，請將這個屬性設為 **$true**，否則請設為 **$false**。</span><span class="sxs-lookup"><span data-stu-id="f4d73-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="f4d73-121">預設值為 **$false**。</span><span class="sxs-lookup"><span data-stu-id="f4d73-121">The default is **$false**.</span></span> <span data-ttu-id="f4d73-122">如果要設定的變數是 **Path** 變數，則透過 **Value** 屬性提供的值就會附加至現有的值。</span><span class="sxs-lookup"><span data-stu-id="f4d73-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="f4d73-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f4d73-123">DependsOn</span></span> | <span data-ttu-id="f4d73-124">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="f4d73-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f4d73-125">例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="f4d73-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="f4d73-126">其他資訊</span><span class="sxs-lookup"><span data-stu-id="f4d73-126">Additional Information</span></span>

* <span data-ttu-id="f4d73-127">如果 **Path** 不存在，或設為 **$false**，環境變數會在 `/etc/environment` 中受到管理。</span><span class="sxs-lookup"><span data-stu-id="f4d73-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="f4d73-128">您的程式或指令碼可能需要設定為以 `/etc/environment` 檔為來源，以存取受管理的環境變數。</span><span class="sxs-lookup"><span data-stu-id="f4d73-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="f4d73-129">如果 **Path** 設為 **$true**，則環境變數會在檔案 `/etc/profile.d/DSCenvironment.sh` 中受到管理。</span><span class="sxs-lookup"><span data-stu-id="f4d73-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="f4d73-130">如果不存在，則會建立這個檔案。</span><span class="sxs-lookup"><span data-stu-id="f4d73-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="f4d73-131">如果 **Ensure** 設定成 "Absent"，而 **Path** 設定成 **$true**，則現有的環境變數只會從 `/etc/profile.d/DSCenvironment.sh` 中移除，而不會從其他檔案中移除。</span><span class="sxs-lookup"><span data-stu-id="f4d73-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="f4d73-132">範例</span><span class="sxs-lookup"><span data-stu-id="f4d73-132">Example</span></span>

<span data-ttu-id="f4d73-133">下列範例示範如何使用 **nxEnvironment** 資源以確保 **TestEnvironmentVariable** 存在且具有值 "Test-Value"。</span><span class="sxs-lookup"><span data-stu-id="f4d73-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="f4d73-134">如果 **TestEnvironmentVariable** 不存在，就會加以建立。</span><span class="sxs-lookup"><span data-stu-id="f4d73-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```