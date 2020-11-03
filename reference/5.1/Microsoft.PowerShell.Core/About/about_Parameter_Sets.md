---
description: 描述如何在 advanced 函數中定義和使用參數集。
title: about_Parameter_Sets
ms.date: 02/11/2020
ms.openlocfilehash: e4cfbc13f981bcc93c8a0a3c799851e83df7746c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207979"
---
# <a name="about-parameter-sets"></a><span data-ttu-id="79335-103">關於參數集</span><span class="sxs-lookup"><span data-stu-id="79335-103">About parameter sets</span></span>

## <a name="short-description"></a><span data-ttu-id="79335-104">簡短描述</span><span class="sxs-lookup"><span data-stu-id="79335-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="79335-105">描述如何在 advanced 函數中定義和使用參數集。</span><span class="sxs-lookup"><span data-stu-id="79335-105">Describes how to define and use parameter sets in advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="79335-106">詳細描述</span><span class="sxs-lookup"><span data-stu-id="79335-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="79335-107">PowerShell 會使用參數集，讓您撰寫可針對不同案例執行不同動作的單一函式。</span><span class="sxs-lookup"><span data-stu-id="79335-107">PowerShell uses parameter sets to enable you to write a single function that can do different actions for different scenarios.</span></span> <span data-ttu-id="79335-108">參數集可讓您向使用者公開不同的參數。</span><span class="sxs-lookup"><span data-stu-id="79335-108">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="79335-109">和，根據使用者指定的參數傳回不同的資訊。</span><span class="sxs-lookup"><span data-stu-id="79335-109">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="parameter-set-requirements"></a><span data-ttu-id="79335-110">參數集需求</span><span class="sxs-lookup"><span data-stu-id="79335-110">Parameter set requirements</span></span>

<span data-ttu-id="79335-111">下列需求適用于所有參數集。</span><span class="sxs-lookup"><span data-stu-id="79335-111">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="79335-112">每個參數集都必須至少有一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="79335-112">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="79335-113">可能的話，請將此參數設為必要參數。</span><span class="sxs-lookup"><span data-stu-id="79335-113">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="79335-114">包含多個位置參數的參數集必須定義每個參數的唯一位置。</span><span class="sxs-lookup"><span data-stu-id="79335-114">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="79335-115">沒有兩個位置參數可以指定相同的位置。</span><span class="sxs-lookup"><span data-stu-id="79335-115">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="79335-116">只有一個集合中的參數可以宣告 `ValueFromPipeline` 具有值的關鍵字 `true` 。</span><span class="sxs-lookup"><span data-stu-id="79335-116">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="79335-117">多個參數可以定義 `ValueFromPipelineByPropertyName` 具有值的關鍵字 `true` 。</span><span class="sxs-lookup"><span data-stu-id="79335-117">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="79335-118">如果未指定參數的參數集，參數將屬於所有參數集。</span><span class="sxs-lookup"><span data-stu-id="79335-118">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="79335-119">有32參數集的限制。</span><span class="sxs-lookup"><span data-stu-id="79335-119">There is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="79335-120">預設參數集</span><span class="sxs-lookup"><span data-stu-id="79335-120">Default parameter sets</span></span>

<span data-ttu-id="79335-121">定義多個參數集時， `DefaultParameterSetName` **CmdletBinding** 屬性的關鍵字會指定預設參數集。</span><span class="sxs-lookup"><span data-stu-id="79335-121">When multiple parameter sets are defined, the `DefaultParameterSetName` keyword of the **CmdletBinding** attribute specifies the default parameter set.</span></span>
<span data-ttu-id="79335-122">當 PowerShell 無法根據提供給命令的資訊判斷要使用的參數時，就會使用預設參數集。</span><span class="sxs-lookup"><span data-stu-id="79335-122">PowerShell uses the default parameter set when it can't determine the parameter set to use based on the information provided to the command.</span></span> <span data-ttu-id="79335-123">如需 **CmdletBinding** 屬性的詳細資訊，請參閱 [about_functions_Cmdletbindingattribute](about_functions_cmdletbindingattribute.md)。</span><span class="sxs-lookup"><span data-stu-id="79335-123">For more information about the **CmdletBinding** attribute, see [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="79335-124">宣告參數集</span><span class="sxs-lookup"><span data-stu-id="79335-124">Declaring parameter sets</span></span>

<span data-ttu-id="79335-125">若要建立參數集，您必須 `ParameterSetName` 針對參數集內的每個參數，指定 **參數** 屬性的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="79335-125">To create a parameter set, you must specify the `ParameterSetName` keyword of the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="79335-126">對於屬於多個參數集的參數，請為每個參數集加入 **參數** 屬性。</span><span class="sxs-lookup"><span data-stu-id="79335-126">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span>

<span data-ttu-id="79335-127">**Parameter** 屬性可讓您針對每個參數集定義不同的參數。</span><span class="sxs-lookup"><span data-stu-id="79335-127">The **Parameter** attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="79335-128">例如，您可以在一個集合中將參數定義為強制，並在另一個集合中定義選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="79335-128">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="79335-129">不過，每個參數集都必須包含至少一個唯一的參數。</span><span class="sxs-lookup"><span data-stu-id="79335-129">However, each parameter set must contain at least one unique parameter.</span></span>

<span data-ttu-id="79335-130">未指派參數集名稱的參數，屬於所有參數集。</span><span class="sxs-lookup"><span data-stu-id="79335-130">Parameters that don't have an assigned parameter set name belong to all parameter sets.</span></span>

### <a name="example"></a><span data-ttu-id="79335-131">範例</span><span class="sxs-lookup"><span data-stu-id="79335-131">Example</span></span>

<span data-ttu-id="79335-132">下列範例函數會計算文字檔中的數位行、字元和單字。</span><span class="sxs-lookup"><span data-stu-id="79335-132">The following example function counts the number lines, characters, and words in a text file.</span></span> <span data-ttu-id="79335-133">您可以使用參數來指定要傳回的值，以及要測量的檔案。</span><span class="sxs-lookup"><span data-stu-id="79335-133">Using parameters, you can specify which values you want returned and which files you want to measure.</span></span> <span data-ttu-id="79335-134">有四個參數集已定義：</span><span class="sxs-lookup"><span data-stu-id="79335-134">There are four parameter sets defined:</span></span>

- <span data-ttu-id="79335-135">路徑</span><span class="sxs-lookup"><span data-stu-id="79335-135">Path</span></span>
- <span data-ttu-id="79335-136">PathAll</span><span class="sxs-lookup"><span data-stu-id="79335-136">PathAll</span></span>
- <span data-ttu-id="79335-137">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="79335-137">LiteralPath</span></span>
- <span data-ttu-id="79335-138">LiteralPathAll</span><span class="sxs-lookup"><span data-stu-id="79335-138">LiteralPathAll</span></span>

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

<span data-ttu-id="79335-139">每個參數集都必須有唯一的參數或唯一的參數組合。</span><span class="sxs-lookup"><span data-stu-id="79335-139">Each parameter set must have a unique parameter or a unique combination of parameters.</span></span> <span data-ttu-id="79335-140">`Path`和 `PathAll` 參數集非常類似，但 **All** 參數對參數集而言是唯一的 `PathAll` 。</span><span class="sxs-lookup"><span data-stu-id="79335-140">The `Path` and `PathAll` parameter sets are very similar but the **All** parameter is unique to the `PathAll` parameter set.</span></span> <span data-ttu-id="79335-141">`LiteralPath`和參數集也是如此 `LiteralPathAll` 。</span><span class="sxs-lookup"><span data-stu-id="79335-141">The same is true with the `LiteralPath` and `LiteralPathAll` parameter sets.</span></span> <span data-ttu-id="79335-142">即使 `PathAll` 和 `LiteralPathAll` 參數設定都有 **All** 參數， **Path** 和 **LiteralPath** 參數還是會區分它們。</span><span class="sxs-lookup"><span data-stu-id="79335-142">Even though the `PathAll` and `LiteralPathAll` parameter sets both have the **All** parameter, the **Path** and **LiteralPath** parameters differentiate them.</span></span>

<span data-ttu-id="79335-143">使用 `Get-Command -Syntax` 會顯示每個參數集的語法。</span><span class="sxs-lookup"><span data-stu-id="79335-143">Use `Get-Command -Syntax` shows you the syntax of each parameter set.</span></span> <span data-ttu-id="79335-144">但是，它不會顯示參數集的名稱。</span><span class="sxs-lookup"><span data-stu-id="79335-144">However it does not show the name of the parameter set.</span></span> <span data-ttu-id="79335-145">下列範例顯示每個參數集可使用的參數。</span><span class="sxs-lookup"><span data-stu-id="79335-145">The following example shows which parameters can be used in each parameter set.</span></span>

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a><span data-ttu-id="79335-146">作用中的參數集</span><span class="sxs-lookup"><span data-stu-id="79335-146">Parameter sets in action</span></span>

<span data-ttu-id="79335-147">在此範例中，我們使用 `PathAll` 參數集。</span><span class="sxs-lookup"><span data-stu-id="79335-147">In this example, we are using the `PathAll` parameter set.</span></span>

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```
