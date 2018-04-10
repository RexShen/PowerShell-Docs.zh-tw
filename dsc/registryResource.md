---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: DSC 登錄資源
ms.openlocfilehash: fcd24b1dd729dbb0abd697a4a628dce01fdd5422
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="e8795-103">DSC 登錄資源</span><span class="sxs-lookup"><span data-stu-id="e8795-103">DSC Registry Resource</span></span>

> <span data-ttu-id="e8795-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e8795-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e8795-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Registry** 資源會提供一個機制，在目標節點管理登錄機碼和值。</span><span class="sxs-lookup"><span data-stu-id="e8795-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8795-106">語法</span><span class="sxs-lookup"><span data-stu-id="e8795-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="e8795-107">Properties</span><span class="sxs-lookup"><span data-stu-id="e8795-107">Properties</span></span>
|  <span data-ttu-id="e8795-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e8795-108">Property</span></span>  |  <span data-ttu-id="e8795-109">描述</span><span class="sxs-lookup"><span data-stu-id="e8795-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="e8795-110">按鍵</span><span class="sxs-lookup"><span data-stu-id="e8795-110">Key</span></span>| <span data-ttu-id="e8795-111">指出您要確保其特定狀態的登錄機碼路徑。</span><span class="sxs-lookup"><span data-stu-id="e8795-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="e8795-112">此路徑必須包含登錄區。</span><span class="sxs-lookup"><span data-stu-id="e8795-112">This path must include the hive.</span></span>|
| <span data-ttu-id="e8795-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="e8795-113">ValueName</span></span>| <span data-ttu-id="e8795-114">指出登錄值的名稱。</span><span class="sxs-lookup"><span data-stu-id="e8795-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="e8795-115">若要新增或移除登錄機碼，請將此屬性指定為空字串，且不指定 ValueType 或 ValueData。</span><span class="sxs-lookup"><span data-stu-id="e8795-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="e8795-116">若要修改或移除登錄機碼的預設值，請將此屬性指定為空字串，同時也指定 ValueType 或 ValueData。</span><span class="sxs-lookup"><span data-stu-id="e8795-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="e8795-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="e8795-117">Ensure</span></span>| <span data-ttu-id="e8795-118">指出金鑰和值是否存在。</span><span class="sxs-lookup"><span data-stu-id="e8795-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="e8795-119">若要確定存在，可將此屬性設定為 "Present"。</span><span class="sxs-lookup"><span data-stu-id="e8795-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="e8795-120">若要確定不存在，可將此屬性設定為 "Absent"。</span><span class="sxs-lookup"><span data-stu-id="e8795-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="e8795-121">預設值為 "Present"。</span><span class="sxs-lookup"><span data-stu-id="e8795-121">The default value is "Present".</span></span>|
| <span data-ttu-id="e8795-122">Force</span><span class="sxs-lookup"><span data-stu-id="e8795-122">Force</span></span>| <span data-ttu-id="e8795-123">如果指定的登錄機碼存在，__Force__ 會以新值覆寫登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="e8795-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="e8795-124">如果要刪除含有子機碼的登錄機碼，這必須是 __$true__</span><span class="sxs-lookup"><span data-stu-id="e8795-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>|
| <span data-ttu-id="e8795-125">Hex</span><span class="sxs-lookup"><span data-stu-id="e8795-125">Hex</span></span>| <span data-ttu-id="e8795-126">指出資料是否以十六進位格式表示。</span><span class="sxs-lookup"><span data-stu-id="e8795-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="e8795-127">如果指定為 Hex，則 DWORD/QWORD 值資料會以十六進位格式顯示。</span><span class="sxs-lookup"><span data-stu-id="e8795-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="e8795-128">不適用於其他類型。</span><span class="sxs-lookup"><span data-stu-id="e8795-128">Not valid for other types.</span></span> <span data-ttu-id="e8795-129">預設值為 __$false__。</span><span class="sxs-lookup"><span data-stu-id="e8795-129">The default value is __$false__.</span></span>|
| <span data-ttu-id="e8795-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e8795-130">DependsOn</span></span>| <span data-ttu-id="e8795-131">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="e8795-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e8795-132">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="e8795-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="e8795-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="e8795-133">ValueData</span></span>| <span data-ttu-id="e8795-134">登錄值的資料。</span><span class="sxs-lookup"><span data-stu-id="e8795-134">The data for the registry value.</span></span>|
| <span data-ttu-id="e8795-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="e8795-135">ValueType</span></span>| <span data-ttu-id="e8795-136">指出值的類型。</span><span class="sxs-lookup"><span data-stu-id="e8795-136">Indicates the type of the value.</span></span> <span data-ttu-id="e8795-137">支援的類型包括：</span><span class="sxs-lookup"><span data-stu-id="e8795-137">The supported types are:</span></span>
<ul><li><span data-ttu-id="e8795-138">字串 (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="e8795-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="e8795-139">二進位 (REG-BINARY)</span><span class="sxs-lookup"><span data-stu-id="e8795-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="e8795-140">Dword 32 位元 (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="e8795-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="e8795-141">Qword 64 位元 (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="e8795-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="e8795-142">多字串 (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="e8795-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="e8795-143">可擴充的字串 (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="e8795-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="e8795-144">範例</span><span class="sxs-lookup"><span data-stu-id="e8795-144">Example</span></span>
<span data-ttu-id="e8795-145">此範例可確保 **HKEY\_LOCAL\_MACHINE** 登錄區包含名為"ExampleKey"的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e8795-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

><span data-ttu-id="e8795-146">**注意︰**變更 **HKEY\_CURRENT\_USER** 中的登錄設定必須以使用者認證執行設定，而不是使用系統。</span><span class="sxs-lookup"><span data-stu-id="e8795-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="e8795-147">您可以使用 **PsDscRunAsCredential** 屬性指定設定時所要使用的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="e8795-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="e8795-148">如需範例，請參閱＜[使用使用者認證執行 DSC](runAsUser.md)＞</span><span class="sxs-lookup"><span data-stu-id="e8795-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>