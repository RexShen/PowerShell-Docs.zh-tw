---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC 登錄資源
ms.openlocfilehash: 8d74473d167b70182c3a16c1d39d2a9e797afb1b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267716"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="8828f-103">DSC 登錄資源</span><span class="sxs-lookup"><span data-stu-id="8828f-103">DSC Registry Resource</span></span>

<span data-ttu-id="8828f-104">_適用於：Windows PowerShell 4.0、Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="8828f-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="8828f-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Registry** 資源會提供一個機制，在目標節點管理登錄機碼和值。</span><span class="sxs-lookup"><span data-stu-id="8828f-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8828f-106">語法</span><span class="sxs-lookup"><span data-stu-id="8828f-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="8828f-107">Properties</span><span class="sxs-lookup"><span data-stu-id="8828f-107">Properties</span></span>

| <span data-ttu-id="8828f-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8828f-108">Property</span></span> | <span data-ttu-id="8828f-109">描述</span><span class="sxs-lookup"><span data-stu-id="8828f-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8828f-110">按鍵</span><span class="sxs-lookup"><span data-stu-id="8828f-110">Key</span></span>| <span data-ttu-id="8828f-111">指出您要確保其特定狀態的登錄機碼路徑。</span><span class="sxs-lookup"><span data-stu-id="8828f-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="8828f-112">此路徑必須包含登錄區。</span><span class="sxs-lookup"><span data-stu-id="8828f-112">This path must include the hive.</span></span>|
| <span data-ttu-id="8828f-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="8828f-113">ValueName</span></span>| <span data-ttu-id="8828f-114">指出登錄值的名稱。</span><span class="sxs-lookup"><span data-stu-id="8828f-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="8828f-115">若要新增或移除登錄機碼，請將此屬性指定為空字串，且不指定 ValueType 或 ValueData。</span><span class="sxs-lookup"><span data-stu-id="8828f-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="8828f-116">若要修改或移除登錄機碼的預設值，請將此屬性指定為空字串，同時也指定 ValueType 或 ValueData。</span><span class="sxs-lookup"><span data-stu-id="8828f-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="8828f-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="8828f-117">Ensure</span></span>| <span data-ttu-id="8828f-118">指出金鑰和值是否存在。</span><span class="sxs-lookup"><span data-stu-id="8828f-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="8828f-119">若要確定存在，可將此屬性設定為 "Present"。</span><span class="sxs-lookup"><span data-stu-id="8828f-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="8828f-120">若要確定不存在，可將此屬性設定為 "Absent"。</span><span class="sxs-lookup"><span data-stu-id="8828f-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="8828f-121">預設值為 "Present"。</span><span class="sxs-lookup"><span data-stu-id="8828f-121">The default value is "Present".</span></span>|
| <span data-ttu-id="8828f-122">Force</span><span class="sxs-lookup"><span data-stu-id="8828f-122">Force</span></span>| <span data-ttu-id="8828f-123">如果指定的登錄機碼存在，**Force** 會以新值覆寫登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="8828f-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="8828f-124">如果要刪除含有子機碼的登錄機碼，這必須是 **$true**</span><span class="sxs-lookup"><span data-stu-id="8828f-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="8828f-125">Hex</span><span class="sxs-lookup"><span data-stu-id="8828f-125">Hex</span></span>| <span data-ttu-id="8828f-126">指出資料是否以十六進位格式表示。</span><span class="sxs-lookup"><span data-stu-id="8828f-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="8828f-127">如果指定為 Hex，則 DWORD/QWORD 值資料會以十六進位格式顯示。</span><span class="sxs-lookup"><span data-stu-id="8828f-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="8828f-128">不適用於其他類型。</span><span class="sxs-lookup"><span data-stu-id="8828f-128">Not valid for other types.</span></span> <span data-ttu-id="8828f-129">預設值為 **$false**。</span><span class="sxs-lookup"><span data-stu-id="8828f-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="8828f-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8828f-130">DependsOn</span></span>| <span data-ttu-id="8828f-131">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="8828f-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8828f-132">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="8828f-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="8828f-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="8828f-133">ValueData</span></span>| <span data-ttu-id="8828f-134">登錄值的資料。</span><span class="sxs-lookup"><span data-stu-id="8828f-134">The data for the registry value.</span></span>|
| <span data-ttu-id="8828f-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="8828f-135">ValueType</span></span>| <span data-ttu-id="8828f-136">指出值的類型。</span><span class="sxs-lookup"><span data-stu-id="8828f-136">Indicates the type of the value.</span></span> <span data-ttu-id="8828f-137">支援的型別包括：字串 (REG_SZ)、二進位 (REG-BINARY)、Dword 32 位元 (REG_DWORD)、Qword 64 位元 (REG_QWORD)、多字串 (REG_MULTI_SZ)、可擴充的字串 (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="8828f-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="8828f-138">範例</span><span class="sxs-lookup"><span data-stu-id="8828f-138">Example</span></span>

<span data-ttu-id="8828f-139">此範例可確保 **HKEY\_LOCAL\_MACHINE** 登錄區包含名為"ExampleKey"的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8828f-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

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

> [!NOTE]
> <span data-ttu-id="8828f-140">變更 `HKEY\CURRENT\USER` 登錄區中的登錄設定必須以使用者認證執行設定，而不是使用系統認證。</span><span class="sxs-lookup"><span data-stu-id="8828f-140">Changing a registry setting in the `HKEY\CURRENT\USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="8828f-141">您可以使用 **PsDscRunAsCredential** 屬性指定設定時所要使用的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="8828f-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="8828f-142">如需範例，請參閱[以使用者認證執行 DSC](runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="8828f-142">For an example, see [Running DSC with user credentials](runAsUser.md).</span></span>