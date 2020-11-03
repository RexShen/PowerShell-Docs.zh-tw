---
description: 描述更簡單、更自然語言的物件集合腳本篩選方式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_simplified_syntax?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Simplified_Syntax
ms.openlocfilehash: ffa499fd618d0d31dec470b0c35c902eba26eb0a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207908"
---
# <a name="about_simplified_syntax"></a><span data-ttu-id="11256-104">about_Simplified_Syntax</span><span class="sxs-lookup"><span data-stu-id="11256-104">about_Simplified_Syntax</span></span>

## <a name="short-description"></a><span data-ttu-id="11256-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="11256-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="11256-106">描述更簡單、更自然語言的物件集合腳本篩選方式。</span><span class="sxs-lookup"><span data-stu-id="11256-106">Describes easier, more natural-language ways of scripting filters for collections of objects.</span></span>

## <a name="long-description"></a><span data-ttu-id="11256-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="11256-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="11256-108">簡化的語法，在 Windows PowerShell 3.0 中引進，可讓您建立一些篩選命令，而不需要使用腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="11256-108">Simplified syntax, introduced in Windows PowerShell 3.0, lets you build some filter commands without using script blocks.</span></span> <span data-ttu-id="11256-109">簡化的語法與自然語言更相似，而且主要是用於輸送至命令的物件集合及其對應的 `Where-Object` `ForEach-Object` 別名 `where` 和 `foreach` 。</span><span class="sxs-lookup"><span data-stu-id="11256-109">The simplified syntax more closely resembles natural language, and is primarily useful with collections of objects that get piped into commands `Where-Object` and `ForEach-Object` and their corresponding aliases `where` and `foreach`.</span></span>

<span data-ttu-id="11256-110">您可以在集合的成員上使用方法 (最常見的陣列) ，而不會參考 `$_` 腳本區塊內的自動變數。</span><span class="sxs-lookup"><span data-stu-id="11256-110">You can use a method on the members of a collection (most commonly, an array) without referring to the automatic variable `$_` inside a script block.</span></span>

<span data-ttu-id="11256-111">請考慮下列兩個調用：</span><span class="sxs-lookup"><span data-stu-id="11256-111">Consider the following two invocations:</span></span>

### <a name="standard-syntax"></a><span data-ttu-id="11256-112">標準語法</span><span class="sxs-lookup"><span data-stu-id="11256-112">Standard Syntax</span></span>

```powershell
dir Cert:\LocalMachine\Root | where { $_.FriendlyName -eq 'Verisign' }
dir Cert:\ -Recurse | foreach { $_.GetKeyAlgorithm() }
```

### <a name="simplified-syntax"></a><span data-ttu-id="11256-113">簡化的語法</span><span class="sxs-lookup"><span data-stu-id="11256-113">Simplified syntax</span></span>

<span data-ttu-id="11256-114">在簡化的語法下，對集合中的物件成員運作的比較運算子會被視為參數。</span><span class="sxs-lookup"><span data-stu-id="11256-114">Under the simplified syntax, comparison operators that work on members of objects in a collection are treated as parameters.</span></span> <span data-ttu-id="11256-115">您可以對集合中的物件叫用方法，而不需要參考 `$_` 腳本區塊內的自動變數。</span><span class="sxs-lookup"><span data-stu-id="11256-115">You can invoke a method on objects in a collection without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="11256-116">將下列兩個調用與先前範例的兩個調用做比較：</span><span class="sxs-lookup"><span data-stu-id="11256-116">Compare the following two invocations to those of the previous example:</span></span>

```powershell
dir Cert:\LocalMachine\Root | where FriendlyName -eq 'Verisign'
dir Cert:\ -Recurse | foreach GetKeyAlgorithm
```

<span data-ttu-id="11256-117">雖然這兩個語法都能運作，但簡化的語法會傳回結果，而不會參考 `$_` 腳本區塊內的自動變數。</span><span class="sxs-lookup"><span data-stu-id="11256-117">While both syntaxes work, the simplified syntax returns results without referring to the automatic variable `$_` inside a script block.</span></span>
<span data-ttu-id="11256-118">方法名稱 `GetKeyAlgorithm` 會被視為的參數 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="11256-118">The method name `GetKeyAlgorithm` is treated as a parameter of `ForEach-Object`.</span></span>
<span data-ttu-id="11256-119">第二個命令會傳回相同的結果，但不會發生錯誤，因為簡化的語法不會嘗試傳回未套用指定引數之專案的結果。</span><span class="sxs-lookup"><span data-stu-id="11256-119">The second command returns the same results, but without errors, because the simplified syntax does not attempt to return results for items for which the specified argument did not apply.</span></span>

<span data-ttu-id="11256-120">在此範例中， `Process` 會將屬性做 `Description` 為成員名稱參數傳遞至 `ForEach-Object` 命令。</span><span class="sxs-lookup"><span data-stu-id="11256-120">In this example, the `Process` property `Description` is passed as the member name parameter to the `ForEach-Object` command.</span></span> <span data-ttu-id="11256-121">結果是使用中進程的描述。</span><span class="sxs-lookup"><span data-stu-id="11256-121">The results are descriptions of active processes.</span></span>

```powershell
Get-Process | foreach Description
```

<span data-ttu-id="11256-122">在此範例中， `DirectoryInfo` 方法 `GetFiles` 會以命令的成員名稱參數形式傳遞 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="11256-122">In this example, the `DirectoryInfo` method `GetFiles` is passed as the member name parameter of the `ForEach-Object` command.</span></span>  
<span data-ttu-id="11256-123">使用搜尋模式參數來呼叫方法 `.*` 。</span><span class="sxs-lookup"><span data-stu-id="11256-123">The method is called with the search pattern parameter `.*`.</span></span>  
<span data-ttu-id="11256-124">結果是 `FileInfo` 使用者主目錄中所有 Unix 樣式隱藏檔案的記錄。</span><span class="sxs-lookup"><span data-stu-id="11256-124">The results are `FileInfo` records for all Unix-style hidden files in user home directories.</span></span> 

```powershell
Get-ChildItem /home -Directory | foreach GetFiles .*
```

## <a name="see-also"></a><span data-ttu-id="11256-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11256-125">SEE ALSO</span></span>

- [<span data-ttu-id="11256-126">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="11256-126">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="11256-127">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="11256-127">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="11256-128">Where-Object</span><span class="sxs-lookup"><span data-stu-id="11256-128">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
- [<span data-ttu-id="11256-129">Foreach-Object</span><span class="sxs-lookup"><span data-stu-id="11256-129">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
