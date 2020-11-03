---
description: 提供 PowerShell 中物件的基本資訊。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: b845dc8b55a19bb642c194398b0c9f5f13d24cb3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208119"
---
# <a name="about-objects"></a><span data-ttu-id="b4158-104">關於物件</span><span class="sxs-lookup"><span data-stu-id="b4158-104">About Objects</span></span>

## <a name="short-description"></a><span data-ttu-id="b4158-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="b4158-105">Short Description</span></span>
<span data-ttu-id="b4158-106">提供 PowerShell 中物件的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="b4158-106">Provides essential information about objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b4158-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="b4158-107">Long Description</span></span>

<span data-ttu-id="b4158-108">您在 PowerShell 中採取的每個動作都是在物件的內容中進行。</span><span class="sxs-lookup"><span data-stu-id="b4158-108">Every action you take in PowerShell occurs within the context of objects.</span></span> <span data-ttu-id="b4158-109">當資料從某個命令移至下一個命令時，會移動為一或多個可識別的物件。</span><span class="sxs-lookup"><span data-stu-id="b4158-109">As data moves from one command to the next, it moves as one or more identifiable objects.</span></span> <span data-ttu-id="b4158-110">物件，則是代表專案的資料集合。</span><span class="sxs-lookup"><span data-stu-id="b4158-110">An object, then, is a collection of data that represents an item.</span></span> <span data-ttu-id="b4158-111">物件是由三種類型的資料所組成：物件類型、其方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="b4158-111">An object is made up of three types of data: the objects type, its methods, and its properties.</span></span>

## <a name="types-methods-and-properties"></a><span data-ttu-id="b4158-112">類型、方法和屬性</span><span class="sxs-lookup"><span data-stu-id="b4158-112">Types, Methods, and Properties</span></span>

<span data-ttu-id="b4158-113">物件類型會告訴它是哪種類型的物件。</span><span class="sxs-lookup"><span data-stu-id="b4158-113">The object type tells what kind of object it is.</span></span> <span data-ttu-id="b4158-114">例如，代表檔案的物件是 FileInfo 物件。</span><span class="sxs-lookup"><span data-stu-id="b4158-114">For example, an object that represents a file is a FileInfo object.</span></span>

<span data-ttu-id="b4158-115">物件方法是您可以在物件上執行的動作。</span><span class="sxs-lookup"><span data-stu-id="b4158-115">The object methods are actions that you can perform on the object.</span></span>
<span data-ttu-id="b4158-116">例如，FileInfo 物件具有可供您用來複製檔案的 CopyTo 方法。</span><span class="sxs-lookup"><span data-stu-id="b4158-116">For example, FileInfo objects have a CopyTo method that you can use to copy the file.</span></span>

<span data-ttu-id="b4158-117">物件屬性會儲存物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b4158-117">Object properties store information about the object.</span></span> <span data-ttu-id="b4158-118">例如，FileInfo 物件具有 LastWriteTime 屬性，可儲存最近存取檔案的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="b4158-118">For example, FileInfo objects have a LastWriteTime property that stores the date and time that the file was most recently accessed.</span></span>

<span data-ttu-id="b4158-119">使用物件時，您可以在命令中使用其方法和屬性，以採取動作和管理資料。</span><span class="sxs-lookup"><span data-stu-id="b4158-119">When working with objects, you can use their methods and properties in commands to take action and manage data.</span></span>

## <a name="objects-in-pipelines"></a><span data-ttu-id="b4158-120">管線中的物件</span><span class="sxs-lookup"><span data-stu-id="b4158-120">Objects in Pipelines</span></span>

<span data-ttu-id="b4158-121">當命令在管線中合併時，它們會將資訊以物件的形式傳遞給彼此。</span><span class="sxs-lookup"><span data-stu-id="b4158-121">When commands are combined in a pipeline, they pass information to each other as objects.</span></span> <span data-ttu-id="b4158-122">當第一個命令執行時，它會將一個或多個物件向下傳送至第二個命令。</span><span class="sxs-lookup"><span data-stu-id="b4158-122">When the first command runs, it sends one or more objects down the pipeline to the second command.</span></span> <span data-ttu-id="b4158-123">第二個命令會從第一個命令接收物件、處理物件，然後將新的或修改過的物件傳遞至管線中的下一個命令。</span><span class="sxs-lookup"><span data-stu-id="b4158-123">The second command receives the objects from the first command, processes the objects, and then passes new or revised objects to the next command in the pipeline.</span></span>
<span data-ttu-id="b4158-124">這會繼續執行，直到管線中的所有命令都執行為止。</span><span class="sxs-lookup"><span data-stu-id="b4158-124">This continues until all commands in the pipeline run.</span></span>

<span data-ttu-id="b4158-125">下列範例示範如何從一個命令傳遞物件到下一個命令：</span><span class="sxs-lookup"><span data-stu-id="b4158-125">The following example demonstrates how objects are passed from one command to the next:</span></span>

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

<span data-ttu-id="b4158-126">第一個命令會 `Get-ChildItem C:` 針對檔案系統根目錄中的每個專案傳回檔案或目錄物件。</span><span class="sxs-lookup"><span data-stu-id="b4158-126">The first command `Get-ChildItem C:` returns a file or directory object for each item in the root directory of the file system.</span></span> <span data-ttu-id="b4158-127">檔案和目錄物件會沿著管線向下傳遞至第二個命令。</span><span class="sxs-lookup"><span data-stu-id="b4158-127">The file and directory objects are passed down the pipeline to the second command.</span></span>

<span data-ttu-id="b4158-128">第二個命令 `where { $_.PsIsContainer -eq $false }` 會使用所有檔案系統物件的 PsIsContainer 屬性，只選取檔案，其 PsIsContainer 屬性中的值為 false (\$ false) 。</span><span class="sxs-lookup"><span data-stu-id="b4158-128">The second command `where { $_.PsIsContainer -eq $false }` uses the PsIsContainer property of all file system objects to select only files, which have a value of False (\$false) in their PsIsContainer property.</span></span> <span data-ttu-id="b4158-129">在 PsIsContainer 屬性中，資料夾（容器和）的值為 True (\$ true) ，則不會選取。</span><span class="sxs-lookup"><span data-stu-id="b4158-129">Folders, which are containers and, thus, have a value of True (\$true) in their PsIsContainer property, are not selected.</span></span>

<span data-ttu-id="b4158-130">第二個命令只會將檔案物件傳遞至第三個命令 `Format-List` ，這會在清單中顯示檔案物件。</span><span class="sxs-lookup"><span data-stu-id="b4158-130">The second command passes only the file objects to the third command `Format-List`, which displays the file objects in a list.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4158-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4158-131">See Also</span></span>

[<span data-ttu-id="b4158-132">about_Methods</span><span class="sxs-lookup"><span data-stu-id="b4158-132">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="b4158-133">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="b4158-133">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="b4158-134">about_Properties</span><span class="sxs-lookup"><span data-stu-id="b4158-134">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="b4158-135">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="b4158-135">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="b4158-136">Get-Member</span><span class="sxs-lookup"><span data-stu-id="b4158-136">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
