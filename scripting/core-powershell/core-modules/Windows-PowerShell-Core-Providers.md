---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 核心提供者"
ms.assetid: 6e24bf6d-4c70-4edf-956a-1e8e4779ba10
ms.openlocfilehash: fdfdfee86884d3ac18a33ac424828faa96ecd8bd
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-core-providers"></a><span data-ttu-id="db863-103">Windows PowerShell 核心提供者</span><span class="sxs-lookup"><span data-stu-id="db863-103">Windows PowerShell Core Providers</span></span>
<span data-ttu-id="db863-104">本節包含描述 **Microsoft.PowerShell.Core** 模組中 Windows PowerShell 提供者的說明主題。</span><span class="sxs-lookup"><span data-stu-id="db863-104">This section contains help topics that describe the Windows PowerShell providers in the **Microsoft.PowerShell.Core** module.</span></span>

<span data-ttu-id="db863-105">Windows PowerShell 提供者是 .NET 程式，可讓特殊資料存放區中的資料在 Windows PowerShell 中使用，讓您可以輕鬆地檢視並管理它。</span><span class="sxs-lookup"><span data-stu-id="db863-105">Windows PowerShell providers are .NET programs that make the data in a specialized data store available in Windows PowerShell so that you can easily view and manage it.</span></span> <span data-ttu-id="db863-106">提供者所公開的資料會出現在磁碟機中，非常類似檔案系統磁碟機。</span><span class="sxs-lookup"><span data-stu-id="db863-106">The data that a provider exposes appears in a drive, much like a file system drive.</span></span> <span data-ttu-id="db863-107">如需詳細資訊，請參閱 [about_Providers [v4]](https://technet.microsoft.com/en-us/library/2d9b3f32-be78-49ad-a547-21231c803242)。</span><span class="sxs-lookup"><span data-stu-id="db863-107">For more information, see [about_Providers [v4]](https://technet.microsoft.com/en-us/library/2d9b3f32-be78-49ad-a547-21231c803242).</span></span>

|<span data-ttu-id="db863-108">提供者</span><span class="sxs-lookup"><span data-stu-id="db863-108">Provider</span></span>|<span data-ttu-id="db863-109">描述</span><span class="sxs-lookup"><span data-stu-id="db863-109">Description</span></span>|
|------------|---------------|
|[<span data-ttu-id="db863-110">別名提供者 [v3]</span><span class="sxs-lookup"><span data-stu-id="db863-110">Alias Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/dce3f872-aeff-4eb2-8b38-876cd612fc29)|<span data-ttu-id="db863-111">提供 Windows PowerShell 別名及其值的存取。</span><span class="sxs-lookup"><span data-stu-id="db863-111">Provides access to the Windows PowerShell aliases and their values.</span></span>|
|[<span data-ttu-id="db863-112">環境提供者 [v3]</span><span class="sxs-lookup"><span data-stu-id="db863-112">Environment Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/94fcd05d-e702-4706-9b7d-ad7e5fd0ec09)|<span data-ttu-id="db863-113">提供 Windows 環境變數的存取。</span><span class="sxs-lookup"><span data-stu-id="db863-113">Provides access to the Windows environment variables.</span></span>|
|[<span data-ttu-id="db863-114">FileSystem 提供者 [v3]</span><span class="sxs-lookup"><span data-stu-id="db863-114">FileSystem Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/0e494537-dfdf-437a-8b27-c21e30aa1f9f)|<span data-ttu-id="db863-115">提供檔案與目錄的存取。</span><span class="sxs-lookup"><span data-stu-id="db863-115">Provides access to files and directories.</span></span>|
|[<span data-ttu-id="db863-116">函式提供者 [v3]</span><span class="sxs-lookup"><span data-stu-id="db863-116">Function Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/7dfc92f4-9a88-4399-978d-6d5d224b3e76)|<span data-ttu-id="db863-117">提供 Windows PowerShell 中定義之函式的存取。</span><span class="sxs-lookup"><span data-stu-id="db863-117">Provides access to the functions defined in Windows PowerShell.</span></span>|
|[<span data-ttu-id="db863-118">登錄提供者 [v3]</span><span class="sxs-lookup"><span data-stu-id="db863-118">Registry Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/d3c8013c-8caa-48d7-9feb-bfef0d95926e)|<span data-ttu-id="db863-119">提供系統登錄機碼與值的存取。</span><span class="sxs-lookup"><span data-stu-id="db863-119">Provides access to the system registry keys and values.</span></span>|
|[<span data-ttu-id="db863-120">變數提供者 [v3]</span><span class="sxs-lookup"><span data-stu-id="db863-120">Variable Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/78dbcbbd-7946-4b9b-b75b-146f247f821c)|<span data-ttu-id="db863-121">提供 Windows PowerShell 變數及其值的存取。</span><span class="sxs-lookup"><span data-stu-id="db863-121">Provides access to Windows PowerShell variables and their values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="db863-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db863-122">See Also</span></span>
- [<span data-ttu-id="db863-123">憑證提供者 [v3]</span><span class="sxs-lookup"><span data-stu-id="db863-123">Certificate Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/3f743541-d0c6-4670-809a-b16fb01f7c4d)
- [<span data-ttu-id="db863-124">WSMan 提供者 [v3]</span><span class="sxs-lookup"><span data-stu-id="db863-124">WSMan Provider [v3]</span></span>](https://technet.microsoft.com/en-us/library/4c3d8d36-4f7a-4211-996f-64110e4b2eb7)
- [<span data-ttu-id="db863-125">about_Providers [v4]</span><span class="sxs-lookup"><span data-stu-id="db863-125">about_Providers [v4]</span></span>](https://technet.microsoft.com/en-us/library/2d9b3f32-be78-49ad-a547-21231c803242)
- [<span data-ttu-id="db863-126">Microsoft.PowerShell.Core 模組</span><span class="sxs-lookup"><span data-stu-id="db863-126">Microsoft.PowerShell.Core Module</span></span>](Microsoft.PowerShell.Core-Module.md)

