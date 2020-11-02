---
ms.date: 07/16/2020
ms.topic: reference
title: DSC 環境資源
description: DSC 環境資源
ms.openlocfilehash: c7995fc5e7efdfb9a1dbae3da9f824d33c67085c
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142577"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="466e9-103">DSC 環境資源</span><span class="sxs-lookup"><span data-stu-id="466e9-103">DSC Environment Resource</span></span>

> <span data-ttu-id="466e9-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="466e9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="466e9-105">Windows PowerShell 預期狀態設定 (DSC) 的 **環境** 資源會提供管理系統環境變數的機制。</span><span class="sxs-lookup"><span data-stu-id="466e9-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="466e9-106">語法</span><span class="sxs-lookup"><span data-stu-id="466e9-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="466e9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="466e9-107">Properties</span></span>

|<span data-ttu-id="466e9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="466e9-108">Property</span></span> |<span data-ttu-id="466e9-109">描述</span><span class="sxs-lookup"><span data-stu-id="466e9-109">Description</span></span> |
|---|---|
|<span data-ttu-id="466e9-110">名稱</span><span class="sxs-lookup"><span data-stu-id="466e9-110">Name</span></span> |<span data-ttu-id="466e9-111">指出您要確保其特定狀態的環境變數名稱。</span><span class="sxs-lookup"><span data-stu-id="466e9-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="466e9-112">Path</span><span class="sxs-lookup"><span data-stu-id="466e9-112">Path</span></span> |<span data-ttu-id="466e9-113">定義設定中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="466e9-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="466e9-114">如果變數是 **Path** 變數，請將這個屬性設定為 `$true`；否則請設定為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="466e9-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="466e9-115">預設值為 `$false`。</span><span class="sxs-lookup"><span data-stu-id="466e9-115">The default is `$false`.</span></span> <span data-ttu-id="466e9-116">如果要設定的變數是 **Path** 變數，則透過 **Value** 屬性提供的值就會附加至現有的值。</span><span class="sxs-lookup"><span data-stu-id="466e9-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="466e9-117">值</span><span class="sxs-lookup"><span data-stu-id="466e9-117">Value</span></span> |<span data-ttu-id="466e9-118">要指派給環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="466e9-118">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="466e9-119">通用屬性</span><span class="sxs-lookup"><span data-stu-id="466e9-119">Common properties</span></span>

|<span data-ttu-id="466e9-120">屬性</span><span class="sxs-lookup"><span data-stu-id="466e9-120">Property</span></span> |<span data-ttu-id="466e9-121">描述</span><span class="sxs-lookup"><span data-stu-id="466e9-121">Description</span></span> |
|---|---|
|<span data-ttu-id="466e9-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="466e9-122">DependsOn</span></span> |<span data-ttu-id="466e9-123">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="466e9-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="466e9-124">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="466e9-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="466e9-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="466e9-125">Ensure</span></span> |<span data-ttu-id="466e9-126">指出變數是否存在。</span><span class="sxs-lookup"><span data-stu-id="466e9-126">Indicates if a variable exists.</span></span> <span data-ttu-id="466e9-127">如果沒有環境變數，請將這個屬性設為 **Present** 以建立環境變數；或如果已有變數，則確保其值符合透過 **Value** 屬性所提供的值。</span><span class="sxs-lookup"><span data-stu-id="466e9-127">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="466e9-128">如果有變數，將它設為 **Absent** 可刪除變數。</span><span class="sxs-lookup"><span data-stu-id="466e9-128">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="466e9-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="466e9-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="466e9-130">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="466e9-130">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="466e9-131">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="466e9-131">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="466e9-132">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="466e9-132">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="466e9-133">範例</span><span class="sxs-lookup"><span data-stu-id="466e9-133">Example</span></span>

<span data-ttu-id="466e9-134">下例確保 TestEnvironmentVariable 存在，且有值 _TestValue_ 。</span><span class="sxs-lookup"><span data-stu-id="466e9-134">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_ .</span></span> <span data-ttu-id="466e9-135">如果不存在，就會建立它。</span><span class="sxs-lookup"><span data-stu-id="466e9-135">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
