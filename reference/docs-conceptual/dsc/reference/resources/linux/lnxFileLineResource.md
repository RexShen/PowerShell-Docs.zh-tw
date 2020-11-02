---
ms.date: 07/17/2020
ms.topic: reference
title: DSC for Linux nxFileLine 資源
description: DSC for Linux nxFileLine 資源
ms.openlocfilehash: b342021176e4d8584afec82173f31bf5191ad264
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644757"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="54672-103">DSC for Linux nxFileLine 資源</span><span class="sxs-lookup"><span data-stu-id="54672-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="54672-104">PowerShell 預期狀態設定 (DSC) 的 **nxFileLine** 資源會提供在 Linux 節點上管理設定檔案內各行的機制。</span><span class="sxs-lookup"><span data-stu-id="54672-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="54672-105">語法</span><span class="sxs-lookup"><span data-stu-id="54672-105">Syntax</span></span>

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="54672-106">屬性</span><span class="sxs-lookup"><span data-stu-id="54672-106">Properties</span></span>

|<span data-ttu-id="54672-107">屬性</span><span class="sxs-lookup"><span data-stu-id="54672-107">Property</span></span> |<span data-ttu-id="54672-108">描述</span><span class="sxs-lookup"><span data-stu-id="54672-108">Description</span></span> |
|---|---|
|<span data-ttu-id="54672-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="54672-109">FilePath</span></span> |<span data-ttu-id="54672-110">在目標節點上要管理程式碼行的檔案完整路徑。</span><span class="sxs-lookup"><span data-stu-id="54672-110">The full path to the file to manage lines in on the target node.</span></span> |
|<span data-ttu-id="54672-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="54672-111">ContainsLine</span></span> |<span data-ttu-id="54672-112">確保存在於檔案中的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="54672-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="54672-113">如果不存在於檔案中，這一行就會附加至檔案。</span><span class="sxs-lookup"><span data-stu-id="54672-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="54672-114">**ContainsLine** 是必要的，但如不需要，也可以設為空字串 (`ContainsLine = ""`)。</span><span class="sxs-lookup"><span data-stu-id="54672-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span> |
|<span data-ttu-id="54672-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="54672-115">DoesNotContainPattern</span></span> |<span data-ttu-id="54672-116">不應該存在於檔案中的程式碼行的規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="54672-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="54672-117">對於存在於符合這個規則運算式檔案中的任何程式碼行，會從檔案中移除該行。</span><span class="sxs-lookup"><span data-stu-id="54672-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="54672-118">通用屬性</span><span class="sxs-lookup"><span data-stu-id="54672-118">Common properties</span></span>

|<span data-ttu-id="54672-119">屬性</span><span class="sxs-lookup"><span data-stu-id="54672-119">Property</span></span> |<span data-ttu-id="54672-120">描述</span><span class="sxs-lookup"><span data-stu-id="54672-120">Description</span></span> |
|---|---|
|<span data-ttu-id="54672-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="54672-121">DependsOn</span></span> |<span data-ttu-id="54672-122">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="54672-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="54672-123">例如，如果第一個想要執行的資源設定指令碼區塊識別碼是 ResourceName，而其類型是 ResourceType，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="54672-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="54672-124">範例</span><span class="sxs-lookup"><span data-stu-id="54672-124">Example</span></span>

<span data-ttu-id="54672-125">這個範例示範如何使用 **nxFileLine** 資源來設定 `/etc/sudoers` 檔案，如此可確保 user: monuser 已設定為不是 requiretty。</span><span class="sxs-lookup"><span data-stu-id="54672-125">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```
