---
description: 可讓您指定要在會話中使用的命名空間。
Locale: en-US
ms.date: 11/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: b48cd85e200f44cdf9fdf278de78e07a918386c8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891341"
---
# <a name="about-using"></a><span data-ttu-id="a5a6a-103">關於使用</span><span class="sxs-lookup"><span data-stu-id="a5a6a-103">About Using</span></span>

## <a name="short-description"></a><span data-ttu-id="a5a6a-104">簡短描述</span><span class="sxs-lookup"><span data-stu-id="a5a6a-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a5a6a-105">可讓您指定要在會話中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-105">Allows you to indicate which namespaces are used in the session.</span></span>

## <a name="long-description"></a><span data-ttu-id="a5a6a-106">詳細描述</span><span class="sxs-lookup"><span data-stu-id="a5a6a-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="a5a6a-107">`using`語句可讓您指定要在會話中使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-107">The `using` statement allows you to specify which namespaces are used in the session.</span></span> <span data-ttu-id="a5a6a-108">新增命名空間可簡化 .NET 類別和成員的使用，並可讓您從腳本模組和元件匯入類別。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-108">Adding namespaces simplifies usage of .NET classes and member and allows you to import classes from script modules and assemblies.</span></span>

<span data-ttu-id="a5a6a-109">`using`語句必須在腳本中的任何其他語句之前。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-109">The `using` statements must come before any other statements in a script.</span></span>

<span data-ttu-id="a5a6a-110">`using`語句不應該與 `using:` 變數的範圍修飾詞混淆。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-110">The `using` statement should not be confused with the `using:` scope modifier for variables.</span></span> <span data-ttu-id="a5a6a-111">如需詳細資訊，請參閱 [about_Remote_Variables](about_Remote_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-111">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

## <a name="namespace-syntax"></a><span data-ttu-id="a5a6a-112">命名空間語法</span><span class="sxs-lookup"><span data-stu-id="a5a6a-112">Namespace syntax</span></span>

<span data-ttu-id="a5a6a-113">若要指定要從中解析類型的 .NET 命名空間：</span><span class="sxs-lookup"><span data-stu-id="a5a6a-113">To specify .NET namespaces from which to resolve types:</span></span>

```
using namespace <.NET-namespace>
```

<span data-ttu-id="a5a6a-114">指定命名空間可讓您依名稱的簡短名稱來更輕鬆地參考類型。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-114">Specifying a namespace makes it easier to reference types by their short names.</span></span>

## <a name="module-syntax"></a><span data-ttu-id="a5a6a-115">模組語法</span><span class="sxs-lookup"><span data-stu-id="a5a6a-115">Module syntax</span></span>

<span data-ttu-id="a5a6a-116">若要從 PowerShell 模組載入類別：</span><span class="sxs-lookup"><span data-stu-id="a5a6a-116">To load classes from a PowerShell module:</span></span>

```
using module <module-name>
```

<span data-ttu-id="a5a6a-117">的值 `<module-name>` 可以是模組名稱、完整的模組規格或模組檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-117">The value of `<module-name>` can be a module name, a full module specification, or a path to a module file.</span></span>

<span data-ttu-id="a5a6a-118">當 `<module-name>` 是路徑時，路徑可以是完整或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-118">When `<module-name>` is a path, the path can be fully qualified or relative.</span></span> <span data-ttu-id="a5a6a-119">相對於包含 using 語句的腳本，會解析相對路徑。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-119">A relative path is resolved relative to the script that contains the using statement.</span></span>

<span data-ttu-id="a5a6a-120">當 `<module-name>` 是名稱或模組規格時，PowerShell 會在 **PSModulePath** 中搜尋指定的模組。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-120">When `<module-name>` is a name or module specification, PowerShell searches the **PSModulePath** for the specified module.</span></span>

<span data-ttu-id="a5a6a-121">模組規格是具有下列索引鍵的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-121">A module specification is a hash table that has the following keys.</span></span>

- <span data-ttu-id="a5a6a-122">`ModuleName` - **必要** 指定模組名稱。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-122">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="a5a6a-123">`GUID` - **選擇性** 指定模組的 GUID。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-123">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="a5a6a-124">您也 **必須** 指定下列三個索引鍵中的其中一個。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-124">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="a5a6a-125">這些金鑰無法一起使用。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-125">These keys can't be used together.</span></span>
  - <span data-ttu-id="a5a6a-126">`ModuleVersion` -指定模組可接受的最小版本。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-126">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="a5a6a-127">`RequiredVersion` -指定完全必要的模組版本。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-127">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="a5a6a-128">`MaximumVersion` -指定模組可接受的最大版本。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-128">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

## <a name="assembly-syntax"></a><span data-ttu-id="a5a6a-129">元件語法</span><span class="sxs-lookup"><span data-stu-id="a5a6a-129">Assembly syntax</span></span>

<span data-ttu-id="a5a6a-130">若要從 .NET 元件預先載入類型：</span><span class="sxs-lookup"><span data-stu-id="a5a6a-130">To preload types from a .NET assembly:</span></span>

```
using assembly <.NET-assembly-path>
using assembly <.NET-namespace>
```

<span data-ttu-id="a5a6a-131">將元件從該元件載入的 .NET 型別載入至腳本的剖析階段。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-131">Loading an assembly preloads .NET types from that assembly into a script at parse time.</span></span> <span data-ttu-id="a5a6a-132">這可讓您建立新的 PowerShell 類別，以使用預先載入之元件中的類型。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-132">This allows you to create new PowerShell classes that use types from the preloaded assembly.</span></span>

<span data-ttu-id="a5a6a-133">在 Windows PowerShell 5.1 中，您可以依路徑名稱或名稱載入元件。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-133">In Windows PowerShell 5.1 you can load the assembly by path name or by name.</span></span> <span data-ttu-id="a5a6a-134">當您使用此名稱時，PowerShell 會在 .NET 全域組件快取中搜尋相關元件的 (GAC) 。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-134">When you use the name, PowerShell searches the .NET Global Assembly Cache (GAC) for the associated assembly.</span></span>

<span data-ttu-id="a5a6a-135">如果您不是建立新的 PowerShell 類別，請改用 `Add-Type` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-135">If you are not creating new PowerShell classes, use the `Add-Type` cmdlet instead.</span></span> <span data-ttu-id="a5a6a-136">如需詳細資訊，請參閱 [Add 類型](xref:Microsoft.PowerShell.Utility.Add-Type)。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-136">For more information, see [Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type).</span></span>

## <a name="examples"></a><span data-ttu-id="a5a6a-137">範例</span><span class="sxs-lookup"><span data-stu-id="a5a6a-137">Examples</span></span>

### <a name="example-1---add-namespaces-for-typename-resolution"></a><span data-ttu-id="a5a6a-138">範例 1-新增 typename 解析的命名空間</span><span class="sxs-lookup"><span data-stu-id="a5a6a-138">Example 1 - Add namespaces for typename resolution</span></span>

<span data-ttu-id="a5a6a-139">下列腳本會取得 "Hello World" 字串的密碼編譯雜湊。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-139">The following script gets the cryptographic hash for the "Hello World" string.</span></span>

<span data-ttu-id="a5a6a-140">請注意 `using namespace System.Text` ，和如何簡化在和和中對的 `using namespace System.IO` 參考 `[UnicodeEncoding]` `System.Text` `[Stream]` `[MemoryStream]` `System.IO` 。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-140">Note how the `using namespace System.Text` and `using namespace System.IO` simplify the references to `[UnicodeEncoding]` in `System.Text` and `[Stream]` and to `[MemoryStream]` in `System.IO`.</span></span>

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

### <a name="example-2---load-classes-from-a-script-module"></a><span data-ttu-id="a5a6a-141">範例 2-從腳本模組載入類別</span><span class="sxs-lookup"><span data-stu-id="a5a6a-141">Example 2 - Load classes from a script module</span></span>

<span data-ttu-id="a5a6a-142">在此範例中，我們有一個名為 **CardGames** 的 PowerShell 腳本模組，可定義下列類別：</span><span class="sxs-lookup"><span data-stu-id="a5a6a-142">In this example, we have a PowerShell script module named **CardGames** that defines the following classes:</span></span>

- <span data-ttu-id="a5a6a-143">**CardGames**</span><span class="sxs-lookup"><span data-stu-id="a5a6a-143">**CardGames.Deck**</span></span>
- <span data-ttu-id="a5a6a-144">**CardGames 卡片**</span><span class="sxs-lookup"><span data-stu-id="a5a6a-144">**CardGames.Card**</span></span>

<span data-ttu-id="a5a6a-145">`Import-Module` 和語句只會匯入模組函式 `#requires` 、別名和變數，如模組所定義。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-145">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="a5a6a-146">未匯入類別。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-146">Classes are not imported.</span></span> <span data-ttu-id="a5a6a-147">此 `using module` 命令會匯入模組，也會載入類別定義。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-147">The `using module` command imports the module and also loads the class definitions.</span></span>

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a><span data-ttu-id="a5a6a-148">範例 3-從元件載入類別</span><span class="sxs-lookup"><span data-stu-id="a5a6a-148">Example 3 - Load classes from an assembly</span></span>

<span data-ttu-id="a5a6a-149">這個範例會載入元件，讓它的類別可以用來建立新的 PowerShell 類別。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-149">This example loads an assembly so that its classes can be used to create new PowerShell classes.</span></span> <span data-ttu-id="a5a6a-150">下列腳本會建立一個衍生自 **DirectoryCoNtext** 類別的新 PowerShell 類別。</span><span class="sxs-lookup"><span data-stu-id="a5a6a-150">The following script creates a new PowerShell class that is derived from **DirectoryContext** class.</span></span>

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
