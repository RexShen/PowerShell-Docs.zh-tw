---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxScript 資源
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372157"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="8725a-103">DSC for Linux nxScript 資源</span><span class="sxs-lookup"><span data-stu-id="8725a-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="8725a-104">PowerShell 預期狀態設定 (DSC) 的 **nxScript** 資源會提供一個機制，在 Linux 節點上執行 Linux 指令碼。</span><span class="sxs-lookup"><span data-stu-id="8725a-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="8725a-105">語法</span><span class="sxs-lookup"><span data-stu-id="8725a-105">Syntax</span></span>

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="8725a-106">Properties</span><span class="sxs-lookup"><span data-stu-id="8725a-106">Properties</span></span>

|  <span data-ttu-id="8725a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8725a-107">Property</span></span> |  <span data-ttu-id="8725a-108">描述</span><span class="sxs-lookup"><span data-stu-id="8725a-108">Description</span></span> |
|---|---|
| <span data-ttu-id="8725a-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="8725a-109">GetScript</span></span>| <span data-ttu-id="8725a-110">提供指令碼以傳回機器目前狀態。</span><span class="sxs-lookup"><span data-stu-id="8725a-110">Provides a script to return current status of the machine.</span></span>  <span data-ttu-id="8725a-111">當您叫用 [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，此指令碼會執行。</span><span class="sxs-lookup"><span data-stu-id="8725a-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="8725a-112">指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 #!/bin/bash。</span><span class="sxs-lookup"><span data-stu-id="8725a-112">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="8725a-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="8725a-113">SetScript</span></span>| <span data-ttu-id="8725a-114">提供讓機器處於正確狀態的指令碼。</span><span class="sxs-lookup"><span data-stu-id="8725a-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="8725a-115">當您叫用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，**TestScript** 會先執行。</span><span class="sxs-lookup"><span data-stu-id="8725a-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="8725a-116">如果 **TestScript** 區塊傳回的結束代碼不是 0，則 **SetScript** 區塊將會執行。</span><span class="sxs-lookup"><span data-stu-id="8725a-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="8725a-117">如果 **TestScript** 傳回的結束代碼是 0，則 **SetScript** 區塊將不會執行。</span><span class="sxs-lookup"><span data-stu-id="8725a-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="8725a-118">指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 `#!/bin/bash`。</span><span class="sxs-lookup"><span data-stu-id="8725a-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="8725a-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="8725a-119">TestScript</span></span>| <span data-ttu-id="8725a-120">提供評估節點目前是否處於正確狀態的指令碼。</span><span class="sxs-lookup"><span data-stu-id="8725a-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="8725a-121">當您叫用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，此指令碼會執行。</span><span class="sxs-lookup"><span data-stu-id="8725a-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="8725a-122">如果傳回的結束代碼不是 0，則 SetScript 將會執行。</span><span class="sxs-lookup"><span data-stu-id="8725a-122">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="8725a-123">如果傳回的結束代碼是 0，則 **SetScript** 將不會執行。</span><span class="sxs-lookup"><span data-stu-id="8725a-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="8725a-124">當您叫用 [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，**TestScript** 也會執行。</span><span class="sxs-lookup"><span data-stu-id="8725a-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="8725a-125">不過，在此情況下，無論從 **TestScript** 傳回何種結束碼，**SetScript** 都不會執行。</span><span class="sxs-lookup"><span data-stu-id="8725a-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="8725a-126">如果實際設定符合目前的預期狀態設定，則 **TestScript** 必須包含內容且傳回的結束代碼必須為 0，如果不符合，則結束碼不是 0。</span><span class="sxs-lookup"><span data-stu-id="8725a-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="8725a-127">(目前的預期狀態設定是上次使用 DSC 的節點上制定的設定)。</span><span class="sxs-lookup"><span data-stu-id="8725a-127">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="8725a-128">指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 1#!/bin/bash.1。</span><span class="sxs-lookup"><span data-stu-id="8725a-128">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="8725a-129">使用者</span><span class="sxs-lookup"><span data-stu-id="8725a-129">User</span></span>| <span data-ttu-id="8725a-130">要執行指令碼的使用者。</span><span class="sxs-lookup"><span data-stu-id="8725a-130">The user to run the script as.</span></span>|
| <span data-ttu-id="8725a-131">群組</span><span class="sxs-lookup"><span data-stu-id="8725a-131">Group</span></span>| <span data-ttu-id="8725a-132">要執行指令碼的群組。</span><span class="sxs-lookup"><span data-stu-id="8725a-132">The group to run the script as.</span></span>|
| <span data-ttu-id="8725a-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8725a-133">DependsOn</span></span> | <span data-ttu-id="8725a-134">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="8725a-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8725a-135">例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="8725a-135">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="8725a-136">範例</span><span class="sxs-lookup"><span data-stu-id="8725a-136">Example</span></span>

<span data-ttu-id="8725a-137">下列範例示範如何使用 **nxScript** 資源來執行其他設定管理。</span><span class="sxs-lookup"><span data-stu-id="8725a-137">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```
