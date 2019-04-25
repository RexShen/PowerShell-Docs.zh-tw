---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 環境資源
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077529"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="52777-103">DSC 環境資源</span><span class="sxs-lookup"><span data-stu-id="52777-103">DSC Environment Resource</span></span>

> <span data-ttu-id="52777-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="52777-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="52777-105">Windows PowerShell 預期狀態設定 (DSC) 的__環境__資源會提供管理系統環境變數的機制。</span><span class="sxs-lookup"><span data-stu-id="52777-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="52777-106">語法</span><span class="sxs-lookup"><span data-stu-id="52777-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="52777-107">Properties</span><span class="sxs-lookup"><span data-stu-id="52777-107">Properties</span></span>

|  <span data-ttu-id="52777-108">屬性</span><span class="sxs-lookup"><span data-stu-id="52777-108">Property</span></span>  |  <span data-ttu-id="52777-109">描述</span><span class="sxs-lookup"><span data-stu-id="52777-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="52777-110">名稱</span><span class="sxs-lookup"><span data-stu-id="52777-110">Name</span></span>| <span data-ttu-id="52777-111">指出您要確保其特定狀態的環境變數名稱。</span><span class="sxs-lookup"><span data-stu-id="52777-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="52777-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="52777-112">Ensure</span></span>| <span data-ttu-id="52777-113">指出變數是否存在。</span><span class="sxs-lookup"><span data-stu-id="52777-113">Indicates if a variable exists.</span></span> <span data-ttu-id="52777-114">如果沒有環境變數，請將這個屬性設為 __Present__ 以建立環境變數；或如果已有變數，則確保其值符合透過 __Value__ 屬性所提供的值。</span><span class="sxs-lookup"><span data-stu-id="52777-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="52777-115">如果有變數，將它設為 __Absent__ 可刪除變數。</span><span class="sxs-lookup"><span data-stu-id="52777-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="52777-116">路徑</span><span class="sxs-lookup"><span data-stu-id="52777-116">Path</span></span>| <span data-ttu-id="52777-117">定義設定中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="52777-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="52777-118">如果變數是 __Path__ 變數，請將這個屬性設為 __$true__，否則請設為 __$false__。</span><span class="sxs-lookup"><span data-stu-id="52777-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="52777-119">預設值為 __$false__。</span><span class="sxs-lookup"><span data-stu-id="52777-119">The default is __$false__.</span></span> <span data-ttu-id="52777-120">如果要設定的變數是 __Path__ 變數，則透過 __Value__ 屬性提供的值就會附加至現有的值。</span><span class="sxs-lookup"><span data-stu-id="52777-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="52777-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="52777-121">DependsOn</span></span> | <span data-ttu-id="52777-122">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="52777-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="52777-123">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="52777-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="52777-124">值</span><span class="sxs-lookup"><span data-stu-id="52777-124">Value</span></span>| <span data-ttu-id="52777-125">要指派給環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="52777-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="52777-126">範例</span><span class="sxs-lookup"><span data-stu-id="52777-126">Example</span></span>

<span data-ttu-id="52777-127">下例確保 __TestEnvironmentVariable__ 存在，且有值 __TestValue__。</span><span class="sxs-lookup"><span data-stu-id="52777-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="52777-128">如果不存在，就會建立它。</span><span class="sxs-lookup"><span data-stu-id="52777-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```