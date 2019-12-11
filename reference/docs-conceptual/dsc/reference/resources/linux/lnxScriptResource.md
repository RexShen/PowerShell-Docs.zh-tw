---
ms.date: 09/20/2019
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxScript 資源
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953185"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="41a52-103">DSC for Linux nxScript 資源</span><span class="sxs-lookup"><span data-stu-id="41a52-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="41a52-104">PowerShell 預期狀態設定 (DSC) 的 **nxScript** 資源會提供一個機制，在 Linux 節點上執行 Linux 指令碼。</span><span class="sxs-lookup"><span data-stu-id="41a52-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="41a52-105">語法</span><span class="sxs-lookup"><span data-stu-id="41a52-105">Syntax</span></span>

```Syntax
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

## <a name="properties"></a><span data-ttu-id="41a52-106">Properties</span><span class="sxs-lookup"><span data-stu-id="41a52-106">Properties</span></span>

|<span data-ttu-id="41a52-107">屬性</span><span class="sxs-lookup"><span data-stu-id="41a52-107">Property</span></span> |<span data-ttu-id="41a52-108">描述</span><span class="sxs-lookup"><span data-stu-id="41a52-108">Description</span></span> |
|---|---|
|<span data-ttu-id="41a52-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="41a52-109">GetScript</span></span> |<span data-ttu-id="41a52-110">提供指令碼以傳回機器目前狀態。</span><span class="sxs-lookup"><span data-stu-id="41a52-110">Provides a script to return current status of the machine.</span></span> <span data-ttu-id="41a52-111">當您叫用 [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，此指令碼會執行。</span><span class="sxs-lookup"><span data-stu-id="41a52-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="41a52-112">指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 `#!/bin/bash`。</span><span class="sxs-lookup"><span data-stu-id="41a52-112">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="41a52-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="41a52-113">SetScript</span></span> |<span data-ttu-id="41a52-114">提供讓機器處於正確狀態的指令碼。</span><span class="sxs-lookup"><span data-stu-id="41a52-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="41a52-115">當您叫用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，**TestScript** 會先執行。</span><span class="sxs-lookup"><span data-stu-id="41a52-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="41a52-116">如果 **TestScript** 區塊傳回的結束代碼不是 0，則 **SetScript** 區塊將會執行。</span><span class="sxs-lookup"><span data-stu-id="41a52-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="41a52-117">如果 **TestScript** 傳回的結束代碼是 0，則 **SetScript** 區塊將不會執行。</span><span class="sxs-lookup"><span data-stu-id="41a52-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="41a52-118">指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 `#!/bin/bash`。</span><span class="sxs-lookup"><span data-stu-id="41a52-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="41a52-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="41a52-119">TestScript</span></span> |<span data-ttu-id="41a52-120">提供評估節點目前是否處於正確狀態的指令碼。</span><span class="sxs-lookup"><span data-stu-id="41a52-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="41a52-121">當您叫用 [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，此指令碼會執行。</span><span class="sxs-lookup"><span data-stu-id="41a52-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="41a52-122">如果傳回的結束代碼不是 0，則 **SetScript** 將會執行。</span><span class="sxs-lookup"><span data-stu-id="41a52-122">If it returns an exit code other than 0, the **SetScript** will run.</span></span> <span data-ttu-id="41a52-123">如果傳回的結束代碼是 0，則 **SetScript** 將不會執行。</span><span class="sxs-lookup"><span data-stu-id="41a52-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="41a52-124">當您叫用 [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) \(英文\) 指令碼時，**TestScript** 也會執行。</span><span class="sxs-lookup"><span data-stu-id="41a52-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="41a52-125">不過，在此情況下，無論從 **TestScript** 傳回何種結束碼，**SetScript** 都不會執行。</span><span class="sxs-lookup"><span data-stu-id="41a52-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="41a52-126">如果實際設定符合目前的預期狀態設定，則 **TestScript** 必須包含內容且傳回的結束代碼必須為 0，如果不符合，則結束碼不是 0。</span><span class="sxs-lookup"><span data-stu-id="41a52-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="41a52-127">目前的預期狀態設定，是上次使用 DSC 之節點上施行的設定。</span><span class="sxs-lookup"><span data-stu-id="41a52-127">The current desired state configuration is the last configuration enacted on the node that is using DSC.</span></span> <span data-ttu-id="41a52-128">指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 `#!/bin/bash`。</span><span class="sxs-lookup"><span data-stu-id="41a52-128">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="41a52-129">使用者</span><span class="sxs-lookup"><span data-stu-id="41a52-129">User</span></span> |<span data-ttu-id="41a52-130">要執行指令碼的使用者。</span><span class="sxs-lookup"><span data-stu-id="41a52-130">The user to run the script as.</span></span> |
|<span data-ttu-id="41a52-131">群組</span><span class="sxs-lookup"><span data-stu-id="41a52-131">Group</span></span> |<span data-ttu-id="41a52-132">要執行指令碼的群組。</span><span class="sxs-lookup"><span data-stu-id="41a52-132">The group to run the script as.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="41a52-133">通用屬性</span><span class="sxs-lookup"><span data-stu-id="41a52-133">Common properties</span></span>

|<span data-ttu-id="41a52-134">屬性</span><span class="sxs-lookup"><span data-stu-id="41a52-134">Property</span></span> |<span data-ttu-id="41a52-135">描述</span><span class="sxs-lookup"><span data-stu-id="41a52-135">Description</span></span> |
|---|---|
|<span data-ttu-id="41a52-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="41a52-136">DependsOn</span></span> |<span data-ttu-id="41a52-137">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="41a52-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="41a52-138">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="41a52-138">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="41a52-139">範例</span><span class="sxs-lookup"><span data-stu-id="41a52-139">Example</span></span>

<span data-ttu-id="41a52-140">下列範例示範如何使用 **nxScript** 資源來執行其他設定管理。</span><span class="sxs-lookup"><span data-stu-id="41a52-140">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

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
