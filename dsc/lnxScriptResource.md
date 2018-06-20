---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: DSC for Linux nxScript 資源
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189324"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="ede8c-103">DSC for Linux nxScript 資源</span><span class="sxs-lookup"><span data-stu-id="ede8c-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="ede8c-104">PowerShell 預期狀態設定 (DSC) 的 **nxScript** 資源會提供一個機制，在 Linux 節點上執行 Linux 指令碼。</span><span class="sxs-lookup"><span data-stu-id="ede8c-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ede8c-105">語法</span><span class="sxs-lookup"><span data-stu-id="ede8c-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="ede8c-106">Properties</span><span class="sxs-lookup"><span data-stu-id="ede8c-106">Properties</span></span>

|  <span data-ttu-id="ede8c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ede8c-107">Property</span></span> |  <span data-ttu-id="ede8c-108">描述</span><span class="sxs-lookup"><span data-stu-id="ede8c-108">Description</span></span> |
|---|---|
| <span data-ttu-id="ede8c-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="ede8c-109">GetScript</span></span>| <span data-ttu-id="ede8c-110">提供當您叫用 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) Cmdlet 時所執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="ede8c-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="ede8c-111">指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 #!/bin/bash。</span><span class="sxs-lookup"><span data-stu-id="ede8c-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="ede8c-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="ede8c-112">SetScript</span></span>| <span data-ttu-id="ede8c-113">提供指令碼。</span><span class="sxs-lookup"><span data-stu-id="ede8c-113">Provides a script.</span></span> <span data-ttu-id="ede8c-114">當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，**TestScript** 會先執行。</span><span class="sxs-lookup"><span data-stu-id="ede8c-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="ede8c-115">如果 **TestScript** 區塊傳回的結束代碼不是 0，則 **SetScript** 區塊將會執行。</span><span class="sxs-lookup"><span data-stu-id="ede8c-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="ede8c-116">如果 **TestScript** 傳回的結束代碼是 0，則 **SetScript** 區塊將不會執行。</span><span class="sxs-lookup"><span data-stu-id="ede8c-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="ede8c-117">指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 `#!/bin/bash`。</span><span class="sxs-lookup"><span data-stu-id="ede8c-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="ede8c-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="ede8c-118">TestScript</span></span>| <span data-ttu-id="ede8c-119">提供指令碼。</span><span class="sxs-lookup"><span data-stu-id="ede8c-119">Provides a script.</span></span> <span data-ttu-id="ede8c-120">當您叫用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) Cmdlet 時，這個指令碼會先執行。</span><span class="sxs-lookup"><span data-stu-id="ede8c-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="ede8c-121">如果傳回的結束代碼不是 0，則 SetScript 將會執行。</span><span class="sxs-lookup"><span data-stu-id="ede8c-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="ede8c-122">如果傳回的結束代碼是 0，則 **SetScript** 將不會執行。</span><span class="sxs-lookup"><span data-stu-id="ede8c-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="ede8c-123">**TestScript** 也會在叫用 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) Cmdlet 時執行。</span><span class="sxs-lookup"><span data-stu-id="ede8c-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="ede8c-124">不過，在此情況下，無論從 **TestScript** 傳回何種結束碼，**SetScript** 都不會執行。</span><span class="sxs-lookup"><span data-stu-id="ede8c-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="ede8c-125">如果實際的設定符合目前的預期狀態設定，則 **TestScript** 傳回的結束代碼必須為 0，如果不符合，則結束碼不是 0。</span><span class="sxs-lookup"><span data-stu-id="ede8c-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="ede8c-126">(目前的預期狀態設定是上次使用 DSC 的節點上制定的設定)。</span><span class="sxs-lookup"><span data-stu-id="ede8c-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="ede8c-127">指令碼的開頭必須是由井號和驚嘆號構成的字元序列，例如 1#!/bin/bash.1。</span><span class="sxs-lookup"><span data-stu-id="ede8c-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="ede8c-128">使用者</span><span class="sxs-lookup"><span data-stu-id="ede8c-128">User</span></span>| <span data-ttu-id="ede8c-129">要執行指令碼的使用者。</span><span class="sxs-lookup"><span data-stu-id="ede8c-129">The user to run the script as.</span></span>|
| <span data-ttu-id="ede8c-130">群組</span><span class="sxs-lookup"><span data-stu-id="ede8c-130">Group</span></span>| <span data-ttu-id="ede8c-131">要執行指令碼的群組。</span><span class="sxs-lookup"><span data-stu-id="ede8c-131">The group to run the script as.</span></span>|
| <span data-ttu-id="ede8c-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ede8c-132">DependsOn</span></span> | <span data-ttu-id="ede8c-133">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="ede8c-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ede8c-134">例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="ede8c-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="ede8c-135">範例</span><span class="sxs-lookup"><span data-stu-id="ede8c-135">Example</span></span>

<span data-ttu-id="ede8c-136">下列範例示範如何使用 **nxScript** 資源來執行其他設定管理。</span><span class="sxs-lookup"><span data-stu-id="ede8c-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

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