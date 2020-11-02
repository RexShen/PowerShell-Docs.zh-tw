---
ms.date: 07/16/2020
ms.topic: reference
title: DSC 登錄資源
description: DSC 登錄資源
ms.openlocfilehash: 075f64abffb429b83958d859b0328b4eeec4cee6
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142492"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="f622c-103">DSC 登錄資源</span><span class="sxs-lookup"><span data-stu-id="f622c-103">DSC Registry Resource</span></span>

> <span data-ttu-id="f622c-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="f622c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="f622c-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Registry** 資源會提供一個機制，在目標節點管理登錄機碼和值。</span><span class="sxs-lookup"><span data-stu-id="f622c-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a><span data-ttu-id="f622c-106">語法</span><span class="sxs-lookup"><span data-stu-id="f622c-106">Syntax</span></span>

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f622c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f622c-107">Properties</span></span>

|<span data-ttu-id="f622c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f622c-108">Property</span></span> |<span data-ttu-id="f622c-109">描述</span><span class="sxs-lookup"><span data-stu-id="f622c-109">Description</span></span> |
|---|---|
|<span data-ttu-id="f622c-110">Key</span><span class="sxs-lookup"><span data-stu-id="f622c-110">Key</span></span> |<span data-ttu-id="f622c-111">指出您要確保其特定狀態的登錄機碼路徑。</span><span class="sxs-lookup"><span data-stu-id="f622c-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="f622c-112">此路徑必須包含登錄區。</span><span class="sxs-lookup"><span data-stu-id="f622c-112">This path must include the hive.</span></span> |
|<span data-ttu-id="f622c-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="f622c-113">ValueName</span></span> |<span data-ttu-id="f622c-114">指出登錄值的名稱。</span><span class="sxs-lookup"><span data-stu-id="f622c-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="f622c-115">若要新增或移除登錄機碼，請將此屬性指定為空字串，且不指定 **ValueType** 或 **ValueData** 。</span><span class="sxs-lookup"><span data-stu-id="f622c-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData** .</span></span> <span data-ttu-id="f622c-116">若要修改或移除登錄機碼的預設值，請將此屬性指定為空字串，同時也指定 **ValueType** 或 **ValueData** 。</span><span class="sxs-lookup"><span data-stu-id="f622c-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData** .</span></span> |
|<span data-ttu-id="f622c-117">Force</span><span class="sxs-lookup"><span data-stu-id="f622c-117">Force</span></span> |<span data-ttu-id="f622c-118">如果指定的登錄機碼存在， **Force** 會以新值覆寫登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="f622c-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="f622c-119">如果要刪除含有子機碼的登錄機碼，這必須是 `$true`。</span><span class="sxs-lookup"><span data-stu-id="f622c-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="f622c-120">Hex</span><span class="sxs-lookup"><span data-stu-id="f622c-120">Hex</span></span> |<span data-ttu-id="f622c-121">指出資料是否以十六進位格式表示。</span><span class="sxs-lookup"><span data-stu-id="f622c-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="f622c-122">如果指定為 Hex，則 DWORD/QWORD 值資料會以十六進位格式顯示。</span><span class="sxs-lookup"><span data-stu-id="f622c-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="f622c-123">不適用於其他類型。</span><span class="sxs-lookup"><span data-stu-id="f622c-123">Not valid for other types.</span></span> <span data-ttu-id="f622c-124">預設值是 `$false`。</span><span class="sxs-lookup"><span data-stu-id="f622c-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="f622c-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="f622c-125">ValueData</span></span> |<span data-ttu-id="f622c-126">登錄值的資料。</span><span class="sxs-lookup"><span data-stu-id="f622c-126">The data for the registry value.</span></span> |
|<span data-ttu-id="f622c-127">ValueType</span><span class="sxs-lookup"><span data-stu-id="f622c-127">ValueType</span></span> |<span data-ttu-id="f622c-128">指出值的類型。</span><span class="sxs-lookup"><span data-stu-id="f622c-128">Indicates the type of the value.</span></span> <span data-ttu-id="f622c-129">支援的類型包括： **String** (REG_SZ)、 **Binary** (REG-BINARY)、 **Dword** (32 位元 REG_DWORD)、 **Qword** (64 位元 REG_QWORD)、 **MultiString** (REG_MULTI_SZ)、 **ExpandString** (REG_EXPAND_SZ)。</span><span class="sxs-lookup"><span data-stu-id="f622c-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f622c-130">通用屬性</span><span class="sxs-lookup"><span data-stu-id="f622c-130">Common properties</span></span>

|<span data-ttu-id="f622c-131">屬性</span><span class="sxs-lookup"><span data-stu-id="f622c-131">Property</span></span> |<span data-ttu-id="f622c-132">描述</span><span class="sxs-lookup"><span data-stu-id="f622c-132">Description</span></span> |
|---|---|
|<span data-ttu-id="f622c-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f622c-133">DependsOn</span></span> |<span data-ttu-id="f622c-134">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="f622c-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f622c-135">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="f622c-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f622c-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="f622c-136">Ensure</span></span> |<span data-ttu-id="f622c-137">指出金鑰和值是否存在。</span><span class="sxs-lookup"><span data-stu-id="f622c-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="f622c-138">若要確定存在，可將此屬性設定為 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="f622c-138">To ensure that they do, set this property to **Present** .</span></span> <span data-ttu-id="f622c-139">若要確定不存在，可將此屬性設定為 **Absent** 。</span><span class="sxs-lookup"><span data-stu-id="f622c-139">To ensure that they do not exist, set the property to **Absent** .</span></span> <span data-ttu-id="f622c-140">預設值為 **Present** 。</span><span class="sxs-lookup"><span data-stu-id="f622c-140">The default value is **Present** .</span></span> |
|<span data-ttu-id="f622c-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f622c-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="f622c-142">設定用於執行整個資源的認證。</span><span class="sxs-lookup"><span data-stu-id="f622c-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f622c-143">已在 WMF 5.0 中新增 **PsDscRunAsCredential** 通用屬性，以允許在其他認證的內容中執行任何 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="f622c-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f622c-144">如需詳細資訊，請參閱[搭配 DSC 資源使用認證](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="f622c-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f622c-145">範例</span><span class="sxs-lookup"><span data-stu-id="f622c-145">Examples</span></span>

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a><span data-ttu-id="f622c-146">範例 1：確定指定的值和資料位於指定的登錄機碼下</span><span class="sxs-lookup"><span data-stu-id="f622c-146">Example 1: Ensure specified Value and Data under specified registry key</span></span>

<span data-ttu-id="f622c-147">這個範例可確認位於名為 "ExampleKey1" 機碼下的登錄值 "TestValue" 存在於 `HKEY\_LOCAL\_MACHINE` 登錄區中，且包含資料 "TestData"。</span><span class="sxs-lookup"><span data-stu-id="f622c-147">This example ensures that the registry value "TestValue" under a key named "ExampleKey1" is present in the `HKEY\_LOCAL\_MACHINE` hive and has the data "TestData".</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey1"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

### <a name="example-2-ensure-specified-registry-key-exists"></a><span data-ttu-id="f622c-148">範例 2：確定指定的登錄機碼是否存在</span><span class="sxs-lookup"><span data-stu-id="f622c-148">Example 2: Ensure specified registry key exists</span></span>

<span data-ttu-id="f622c-149">這個範例可確認名為 "ExampleKey2" 的機碼存在於 **HKEY\_LOCAL\_MACHINE** 登錄區中。</span><span class="sxs-lookup"><span data-stu-id="f622c-149">This example ensures that a key named "ExampleKey2" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey2"
        ValueName   = ""
    }
}
```

> [!NOTE]
> <span data-ttu-id="f622c-150">變更 `HKEY_CURRENT_USER` 登錄區中的登錄設定必須以使用者認證執行設定，而不是使用系統認證。</span><span class="sxs-lookup"><span data-stu-id="f622c-150">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="f622c-151">您可以使用 **PsDscRunAsCredential** 屬性指定設定時所要使用的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="f622c-151">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="f622c-152">如需範例，請參閱[以使用者認證執行 DSC](../../../configurations/runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="f622c-152">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
