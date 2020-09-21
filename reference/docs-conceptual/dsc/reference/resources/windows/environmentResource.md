---
ms.date: 07/16/2020
keywords: dsc,powershell,設定,安裝
title: DSC 環境資源
ms.openlocfilehash: d8519a66d457767dcbc0e08b01a69a9264997479
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464412"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="0565c-103">DSC 環境資源</span><span class="sxs-lookup"><span data-stu-id="0565c-103">DSC Environment Resource</span></span>

> <span data-ttu-id="0565c-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="0565c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="0565c-105">Windows PowerShell 預期狀態設定 (DSC) 的**環境**資源會提供管理系統環境變數的機制。</span><span class="sxs-lookup"><span data-stu-id="0565c-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="0565c-106">語法</span><span class="sxs-lookup"><span data-stu-id="0565c-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Target = [string] { Process | Machine } ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="0565c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0565c-107">Properties</span></span>

|<span data-ttu-id="0565c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0565c-108">Property</span></span> |<span data-ttu-id="0565c-109">描述</span><span class="sxs-lookup"><span data-stu-id="0565c-109">Description</span></span> |
|---|---|
|<span data-ttu-id="0565c-110">名稱</span><span class="sxs-lookup"><span data-stu-id="0565c-110">Name</span></span> |<span data-ttu-id="0565c-111">指出您要確保其特定狀態的環境變數名稱。</span><span class="sxs-lookup"><span data-stu-id="0565c-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="0565c-112">Path</span><span class="sxs-lookup"><span data-stu-id="0565c-112">Path</span></span> |<span data-ttu-id="0565c-113">定義設定中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="0565c-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="0565c-114">如果變數是 **Path** 變數，請將這個屬性設定為 `$true`；否則請設定為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="0565c-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="0565c-115">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="0565c-115">The default is `$false`.</span></span> <span data-ttu-id="0565c-116">如果要設定的變數是 **Path** 變數，則透過 **Value** 屬性提供的值就會附加至現有的值。</span><span class="sxs-lookup"><span data-stu-id="0565c-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="0565c-117">目標</span><span class="sxs-lookup"><span data-stu-id="0565c-117">Target</span></span>| <span data-ttu-id="0565c-118">指出擷取變數的位置：電腦或處理序。</span><span class="sxs-lookup"><span data-stu-id="0565c-118">Indicates where to retrieve the variable: The machine or the process.</span></span> <span data-ttu-id="0565c-119">若同時指定兩者，則只會傳回來自電腦的值。</span><span class="sxs-lookup"><span data-stu-id="0565c-119">If both are indicated then only the value from the machine is returned.</span></span> <span data-ttu-id="0565c-120">預設為兩者，因為這是資源其餘部分的預設。</span><span class="sxs-lookup"><span data-stu-id="0565c-120">The default is both since that is the default for the rest of the resource.</span></span> |
|<span data-ttu-id="0565c-121">值</span><span class="sxs-lookup"><span data-stu-id="0565c-121">Value</span></span> |<span data-ttu-id="0565c-122">要指派給環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="0565c-122">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0565c-123">通用屬性</span><span class="sxs-lookup"><span data-stu-id="0565c-123">Common properties</span></span>

|<span data-ttu-id="0565c-124">屬性</span><span class="sxs-lookup"><span data-stu-id="0565c-124">Property</span></span> |<span data-ttu-id="0565c-125">描述</span><span class="sxs-lookup"><span data-stu-id="0565c-125">Description</span></span> |
|---|---|
|<span data-ttu-id="0565c-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0565c-126">DependsOn</span></span> |<span data-ttu-id="0565c-127">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="0565c-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0565c-128">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="0565c-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0565c-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="0565c-129">Ensure</span></span> |<span data-ttu-id="0565c-130">指出變數是否存在。</span><span class="sxs-lookup"><span data-stu-id="0565c-130">Indicates if a variable exists.</span></span> <span data-ttu-id="0565c-131">如果沒有環境變數，請將這個屬性設為 **Present** 以建立環境變數；或如果已有變數，則確保其值符合透過 **Value** 屬性所提供的值。</span><span class="sxs-lookup"><span data-stu-id="0565c-131">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="0565c-132">如果有變數，將它設為 **Absent** 可刪除變數。</span><span class="sxs-lookup"><span data-stu-id="0565c-132">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="0565c-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0565c-133">PsDscRunAsCredential</span></span> |<span data-ttu-id="0565c-134">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="0565c-134">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="0565c-135">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="0565c-135">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="0565c-136">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="0565c-136">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="0565c-137">範例</span><span class="sxs-lookup"><span data-stu-id="0565c-137">Example</span></span>

<span data-ttu-id="0565c-138">下例確保 TestEnvironmentVariable 存在，且有值 _TestValue_。</span><span class="sxs-lookup"><span data-stu-id="0565c-138">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="0565c-139">如果不存在，就會建立它。</span><span class="sxs-lookup"><span data-stu-id="0565c-139">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
