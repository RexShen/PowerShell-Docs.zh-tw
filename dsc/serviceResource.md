---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC Service 資源"
ms.openlocfilehash: 611729e5d971ebaf15ac947454cffadc6797927b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-service-resource"></a><span data-ttu-id="583f9-103">DSC Service 資源</span><span class="sxs-lookup"><span data-stu-id="583f9-103">DSC Service Resource</span></span>

> <span data-ttu-id="583f9-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="583f9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="583f9-105">Windows PowerShell 預期狀態設定 (DSC) 的 **Service** 資源提供了管理目標節點服務的機制。</span><span class="sxs-lookup"><span data-stu-id="583f9-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="583f9-106">語法</span><span class="sxs-lookup"><span data-stu-id="583f9-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="583f9-107">[內容]</span><span class="sxs-lookup"><span data-stu-id="583f9-107">Properties</span></span>

|  <span data-ttu-id="583f9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="583f9-108">Property</span></span>  |  <span data-ttu-id="583f9-109">描述</span><span class="sxs-lookup"><span data-stu-id="583f9-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="583f9-110">名稱</span><span class="sxs-lookup"><span data-stu-id="583f9-110">Name</span></span>| <span data-ttu-id="583f9-111">表示服務名稱。</span><span class="sxs-lookup"><span data-stu-id="583f9-111">Indicates the service name.</span></span> <span data-ttu-id="583f9-112">請注意，有時候和顯示名稱不同。</span><span class="sxs-lookup"><span data-stu-id="583f9-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="583f9-113">您可以使用 Get-Service Cmdlet 取得服務清單及其目前狀態。</span><span class="sxs-lookup"><span data-stu-id="583f9-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>| 
| <span data-ttu-id="583f9-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="583f9-114">BuiltInAccount</span></span>| <span data-ttu-id="583f9-115">表示用於服務的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="583f9-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="583f9-116">這個屬性所允許的值為：**LocalService**、**LocalSystem** 和 **NetworkService**。</span><span class="sxs-lookup"><span data-stu-id="583f9-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="583f9-117">認證</span><span class="sxs-lookup"><span data-stu-id="583f9-117">Credential</span></span>| <span data-ttu-id="583f9-118">表示執行服務的帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="583f9-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="583f9-119">這個屬性與 __BuiltinAccount__ 屬性不能同時使用。</span><span class="sxs-lookup"><span data-stu-id="583f9-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>| 
| <span data-ttu-id="583f9-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="583f9-120">DependsOn</span></span>| <span data-ttu-id="583f9-121">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="583f9-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="583f9-122">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="583f9-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="583f9-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="583f9-123">StartupType</span></span>| <span data-ttu-id="583f9-124">表示服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="583f9-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="583f9-125">這個屬性所允許的值為：**Automatic**、**Disabled** 和 **Manual**</span><span class="sxs-lookup"><span data-stu-id="583f9-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>| 
| <span data-ttu-id="583f9-126">State</span><span class="sxs-lookup"><span data-stu-id="583f9-126">State</span></span>| <span data-ttu-id="583f9-127">表示您要確保的服務狀態。</span><span class="sxs-lookup"><span data-stu-id="583f9-127">Indicates the state you want to ensure for the service.</span></span>| 
| <span data-ttu-id="583f9-128">描述</span><span class="sxs-lookup"><span data-stu-id="583f9-128">Description</span></span> | <span data-ttu-id="583f9-129">表示目標服務的描述。</span><span class="sxs-lookup"><span data-stu-id="583f9-129">Indicates the description of the target service.</span></span>| 
| <span data-ttu-id="583f9-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="583f9-130">DisplayName</span></span> | <span data-ttu-id="583f9-131">表示目標服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="583f9-131">Indicates the display name of the target service.</span></span>| 
| <span data-ttu-id="583f9-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="583f9-132">Ensure</span></span> | <span data-ttu-id="583f9-133">表示系統上是否有目標服務。</span><span class="sxs-lookup"><span data-stu-id="583f9-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="583f9-134">請將此屬性設定為**Absent** 以確保目標服務不存在。</span><span class="sxs-lookup"><span data-stu-id="583f9-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="583f9-135">屬性設定為 **Present** (預設值)，可確保目標服務存在。</span><span class="sxs-lookup"><span data-stu-id="583f9-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="583f9-136">路徑</span><span class="sxs-lookup"><span data-stu-id="583f9-136">Path</span></span> | <span data-ttu-id="583f9-137">表示新服務的二進位檔路徑。</span><span class="sxs-lookup"><span data-stu-id="583f9-137">Indicates the path to the binary file for a new service.</span></span>| 

## <a name="example"></a><span data-ttu-id="583f9-138">範例</span><span class="sxs-lookup"><span data-stu-id="583f9-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

