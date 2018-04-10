---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: DSC ServiceSet 資源
ms.openlocfilehash: a7516120f0c4bc1c91031adc8aabf6a59b845246
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="0adf5-103">DSC ServiceSet 資源</span><span class="sxs-lookup"><span data-stu-id="0adf5-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="0adf5-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0adf5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="0adf5-105">Windows PowerShell 預期狀態設定 (DSC) 的 **ServiceSet** 資源提供了管理目標節點服務的機制。</span><span class="sxs-lookup"><span data-stu-id="0adf5-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="0adf5-106">此資源是為 `Name` 屬性中指定的每項服務呼叫 [Service 資源](serviceResource.md)的[複合資源](authoringResourceComposite.md)。</span><span class="sxs-lookup"><span data-stu-id="0adf5-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="0adf5-107">當您想要將多項服務設定成相同的狀態，請使用此資源。</span><span class="sxs-lookup"><span data-stu-id="0adf5-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="0adf5-108">語法</span><span class="sxs-lookup"><span data-stu-id="0adf5-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="0adf5-109">Properties</span><span class="sxs-lookup"><span data-stu-id="0adf5-109">Properties</span></span>

|  <span data-ttu-id="0adf5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0adf5-110">Property</span></span>  |  <span data-ttu-id="0adf5-111">描述</span><span class="sxs-lookup"><span data-stu-id="0adf5-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="0adf5-112">名稱</span><span class="sxs-lookup"><span data-stu-id="0adf5-112">Name</span></span>| <span data-ttu-id="0adf5-113">表示服務名稱。</span><span class="sxs-lookup"><span data-stu-id="0adf5-113">Indicates the service names.</span></span> <span data-ttu-id="0adf5-114">請注意，有時候和顯示名稱不同。</span><span class="sxs-lookup"><span data-stu-id="0adf5-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="0adf5-115">您可以使用 [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) Cmdlet 取得服務清單及其目前狀態。</span><span class="sxs-lookup"><span data-stu-id="0adf5-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="0adf5-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="0adf5-116">StartupType</span></span>| <span data-ttu-id="0adf5-117">表示服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="0adf5-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="0adf5-118">這個屬性所允許的值為：**Automatic**、**Disabled** 和 **Manual**</span><span class="sxs-lookup"><span data-stu-id="0adf5-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="0adf5-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="0adf5-119">BuiltInAccount</span></span>| <span data-ttu-id="0adf5-120">表示用於服務的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="0adf5-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="0adf5-121">這個屬性所允許的值為：**LocalService**、**LocalSystem** 和 **NetworkService**。</span><span class="sxs-lookup"><span data-stu-id="0adf5-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="0adf5-122">State</span><span class="sxs-lookup"><span data-stu-id="0adf5-122">State</span></span>| <span data-ttu-id="0adf5-123">表示您要確保的服務狀態：**已停止**或**正在執行**。</span><span class="sxs-lookup"><span data-stu-id="0adf5-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="0adf5-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="0adf5-124">Ensure</span></span>| <span data-ttu-id="0adf5-125">表示系統上是否有服務。</span><span class="sxs-lookup"><span data-stu-id="0adf5-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="0adf5-126">請將此屬性設為 **Absent** 以確保服務不存在。</span><span class="sxs-lookup"><span data-stu-id="0adf5-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="0adf5-127">屬性設定為 **Present** (預設值)，可確保目標服務存在。</span><span class="sxs-lookup"><span data-stu-id="0adf5-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="0adf5-128">認證</span><span class="sxs-lookup"><span data-stu-id="0adf5-128">Credential</span></span>| <span data-ttu-id="0adf5-129">表示執行服務資源的帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="0adf5-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="0adf5-130">這個屬性與 **BuiltinAccount** 屬性不能同時使用。</span><span class="sxs-lookup"><span data-stu-id="0adf5-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="0adf5-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0adf5-131">DependsOn</span></span>| <span data-ttu-id="0adf5-132">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="0adf5-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0adf5-133">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 *ResourceName*，而它的類型是 *ResourceType*，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="0adf5-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="0adf5-134">範例</span><span class="sxs-lookup"><span data-stu-id="0adf5-134">Example</span></span>

<span data-ttu-id="0adf5-135">下列設定會啟動「Windows 音訊」和「遠端桌面服務」服務。</span><span class="sxs-lookup"><span data-stu-id="0adf5-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```