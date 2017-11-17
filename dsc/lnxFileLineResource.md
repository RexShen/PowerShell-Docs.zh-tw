---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "DSC for Linux nxFileLine 資源"
ms.openlocfilehash: bde42bbe217fc9acf5a3f2ee0136d30e2b5f2415
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="6fce3-103">DSC for Linux nxFileLine 資源</span><span class="sxs-lookup"><span data-stu-id="6fce3-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="6fce3-104">PowerShell 預期狀態設定 (DSC) 的 **nxFileLine** 資源會提供在 Linux 節點上管理設定檔案內各行的機制。</span><span class="sxs-lookup"><span data-stu-id="6fce3-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fce3-105">語法</span><span class="sxs-lookup"><span data-stu-id="6fce3-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="6fce3-106">[內容]</span><span class="sxs-lookup"><span data-stu-id="6fce3-106">Properties</span></span>

|  <span data-ttu-id="6fce3-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6fce3-107">Property</span></span> |  <span data-ttu-id="6fce3-108">描述</span><span class="sxs-lookup"><span data-stu-id="6fce3-108">Description</span></span> | 
|---|---|
| <span data-ttu-id="6fce3-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="6fce3-109">FilePath</span></span>| <span data-ttu-id="6fce3-110">在目標節點上要管理程式碼行的檔案完整路徑。</span><span class="sxs-lookup"><span data-stu-id="6fce3-110">The full path to the file to manage lines in on the target node.</span></span>| 
| <span data-ttu-id="6fce3-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="6fce3-111">ContainsLine</span></span>| <span data-ttu-id="6fce3-112">確保存在於檔案中的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="6fce3-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="6fce3-113">如果不存在於檔案中，這一行就會附加至檔案。</span><span class="sxs-lookup"><span data-stu-id="6fce3-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="6fce3-114">**ContainsLine** 是必要的，但如不需要，也可以設為空字串 (`ContainsLine = ‘’`\`)。</span><span class="sxs-lookup"><span data-stu-id="6fce3-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ‘’`\`) if it is not needed.</span></span>| 
| <span data-ttu-id="6fce3-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="6fce3-115">DoesNotContainPattern</span></span>| <span data-ttu-id="6fce3-116">不應該存在於檔案中的程式碼行的規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="6fce3-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="6fce3-117">對於存在於符合這個規則運算式檔案中的任何程式碼行，會從檔案中移除該行。</span><span class="sxs-lookup"><span data-stu-id="6fce3-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>| 
| <span data-ttu-id="6fce3-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6fce3-118">DependsOn</span></span> | <span data-ttu-id="6fce3-119">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="6fce3-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6fce3-120">例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="6fce3-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="6fce3-121">範例</span><span class="sxs-lookup"><span data-stu-id="6fce3-121">Example</span></span>

<span data-ttu-id="6fce3-122">這個範例示範如何使用 **nxFileLine** 資源來設定 `/etc/sudoers` 檔案，如此可確保 user: monuser 已設定為不是 requiretty。</span><span class="sxs-lookup"><span data-stu-id="6fce3-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```

