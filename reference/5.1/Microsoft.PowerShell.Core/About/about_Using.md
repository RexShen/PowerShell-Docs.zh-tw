---
description: 可讓您指定要在會話中使用的命名空間。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: ff6b43c3af1deddb5cb1b4c2e2c86a2cc2cac5d4
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208759"
---
# <a name="about-using"></a><span data-ttu-id="ae42c-104">關於使用</span><span class="sxs-lookup"><span data-stu-id="ae42c-104">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="ae42c-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="ae42c-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ae42c-106">可讓您指定要在會話中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ae42c-106">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="ae42c-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="ae42c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="ae42c-108">`using`語句可讓您指定要在會話中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ae42c-108">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="ae42c-109">新增命名空間可簡化 .NET 類別和成員的使用，並可讓您從腳本模組和元件匯入類別。</span><span class="sxs-lookup"><span data-stu-id="ae42c-109">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="ae42c-110">`using`語句必須在腳本中的任何其他語句之前。</span><span class="sxs-lookup"><span data-stu-id="ae42c-110">The `using` statements must come before any other statements in a script.</span></span>

<span data-ttu-id="ae42c-111">`using`語句不應該與 `using:` 變數的範圍修飾詞混淆。</span><span class="sxs-lookup"><span data-stu-id="ae42c-111">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="ae42c-112">如需詳細資訊，請參閱 [about_Remote_Variables](about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="ae42c-112">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="ae42c-113">Syntax</span><span class="sxs-lookup"><span data-stu-id="ae42c-113">Syntax</span></span>

<span data-ttu-id="ae42c-114">若要指定要從中解析類型的 .NET 命名空間：</span><span class="sxs-lookup"><span data-stu-id="ae42c-114">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="ae42c-115">若要從 PowerShell 模組載入類別：</span><span class="sxs-lookup"><span data-stu-id="ae42c-115">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="ae42c-116">若要從 .NET 元件預先載入類型：</span><span class="sxs-lookup"><span data-stu-id="ae42c-116">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
using assembly <.NET-namespace>
```

<span data-ttu-id="ae42c-117">指定命名空間可讓您依名稱的簡短名稱來更輕鬆地參考類型。</span><span class="sxs-lookup"><span data-stu-id="ae42c-117">Specifying a namespace makes it easier to reference types by their short names.</span></span>

<span data-ttu-id="ae42c-118">將元件從該元件載入的 .NET 型別載入至腳本的剖析階段。</span><span class="sxs-lookup"><span data-stu-id="ae42c-118">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="ae42c-119">這可讓您建立新的 PowerShell 類別，以使用預先載入之元件中的類型。</span><span class="sxs-lookup"><span data-stu-id="ae42c-119">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="ae42c-120">在 Windows PowerShell 5.1 中，您可以依路徑名稱或名稱載入元件。</span><span class="sxs-lookup"><span data-stu-id="ae42c-120">In Windows PowerShell 5.1 you can load the assembly by path name or by name.</span></span> <span data-ttu-id="ae42c-121">當您使用此名稱時，PowerShell 會在 .NET 全域組件快取中搜尋相關元件的 (GAC) 。</span><span class="sxs-lookup"><span data-stu-id="ae42c-121">When you use the name, PowerShell searches the .NET Global Assembly Cache (GAC) for the associated assembly.</span></span>

<span data-ttu-id="ae42c-122">如果您不是建立新的 PowerShell 類別，請改用 `Add-Type` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae42c-122">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="ae42c-123">如需詳細資訊，請參閱 [Add 類型](xref:Microsoft.PowerShell.Utility.Add-Type)。</span><span class="sxs-lookup"><span data-stu-id="ae42c-123">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="ae42c-124">範例</span><span class="sxs-lookup"><span data-stu-id="ae42c-124">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="ae42c-125">範例 1-新增 typename 解析的命名空間</span><span class="sxs-lookup"><span data-stu-id="ae42c-125">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="ae42c-126">下列腳本會取得 "Hello World" 字串的密碼編譯雜湊。</span><span class="sxs-lookup"><span data-stu-id="ae42c-126">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="ae42c-127">請注意 `using namespace System.Text` ，和如何簡化在和和中對的 `using namespace System.IO` 參考 `[UnicodeEncoding]` `System.Text` `[Stream]` `[MemoryStream]` `System.IO` 。</span><span class="sxs-lookup"><span data-stu-id="ae42c-127">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="ae42c-128">範例 2-從腳本模組載入類別</span><span class="sxs-lookup"><span data-stu-id="ae42c-128">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="ae42c-129">在此範例中，我們有一個名為 **CardGames** 的 PowerShell 腳本模組，可定義下列類別：</span><span class="sxs-lookup"><span data-stu-id="ae42c-129">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="ae42c-130">**CardGames**</span><span class="sxs-lookup"><span data-stu-id="ae42c-130">**CardGames.Deck**</span></span>
- <span data-ttu-id="ae42c-131">**CardGames 卡片**</span><span class="sxs-lookup"><span data-stu-id="ae42c-131">**CardGames.Card**</span></span>

<span data-ttu-id="ae42c-132">`Import-Module` 和語句只會匯入模組函式 `#requires` 、別名和變數，如模組所定義。</span><span class="sxs-lookup"><span data-stu-id="ae42c-132">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="ae42c-133">未匯入類別。</span><span class="sxs-lookup"><span data-stu-id="ae42c-133">Classes are not imported.</span></span> <span data-ttu-id="ae42c-134">此 `using module` 命令會匯入模組，也會載入類別定義。</span><span class="sxs-lookup"><span data-stu-id="ae42c-134">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="ae42c-135">範例 3-從元件載入類別</span><span class="sxs-lookup"><span data-stu-id="ae42c-135">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="ae42c-136">這個範例會載入元件，讓它的類別可以用來建立新的 PowerShell 類別。</span><span class="sxs-lookup"><span data-stu-id="ae42c-136">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="ae42c-137">下列腳本會建立一個衍生自 **DirectoryCoNtext** 類別的新 PowerShell 類別。</span><span class="sxs-lookup"><span data-stu-id="ae42c-137">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```
