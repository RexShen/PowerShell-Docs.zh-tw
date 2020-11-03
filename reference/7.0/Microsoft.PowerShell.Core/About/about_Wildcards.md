---
description: 描述如何在 PowerShell 中使用萬用字元。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 3a3146210a7d133190631f177d3a69ca120d1432
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206767"
---
# <a name="about-wildcards"></a><span data-ttu-id="d33e4-104">關於萬用字元</span><span class="sxs-lookup"><span data-stu-id="d33e4-104">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="d33e4-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="d33e4-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="d33e4-106">描述如何在 PowerShell 中使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d33e4-106">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d33e4-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="d33e4-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="d33e4-108">萬用字元代表一或多個字元。</span><span class="sxs-lookup"><span data-stu-id="d33e4-108">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="d33e4-109">您可以使用它們，在命令中建立單字模式。</span><span class="sxs-lookup"><span data-stu-id="d33e4-109">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="d33e4-110">例如，若要取得具有副檔名的目錄中的所有檔案 `C:\Techdocs` `.ppt` ，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d33e4-110">For example, to get all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="d33e4-111">在此情況下，星號 (`*`) 萬用字元表示在副檔名之前出現的任何字元 `.ppt` 。</span><span class="sxs-lookup"><span data-stu-id="d33e4-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="d33e4-112">PowerShell 支援下列萬用字元：</span><span class="sxs-lookup"><span data-stu-id="d33e4-112">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="d33e4-113">萬用字元</span><span class="sxs-lookup"><span data-stu-id="d33e4-113">Wildcard</span></span>|<span data-ttu-id="d33e4-114">描述</span><span class="sxs-lookup"><span data-stu-id="d33e4-114">Description</span></span>               |<span data-ttu-id="d33e4-115">範例</span><span class="sxs-lookup"><span data-stu-id="d33e4-115">Example</span></span> |<span data-ttu-id="d33e4-116">相符項目</span><span class="sxs-lookup"><span data-stu-id="d33e4-116">Match</span></span>        |<span data-ttu-id="d33e4-117">無相符</span><span class="sxs-lookup"><span data-stu-id="d33e4-117">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="d33e4-118">符合零或多個字元</span><span class="sxs-lookup"><span data-stu-id="d33e4-118">Match zero or more characters</span></span> | <span data-ttu-id="d33e4-119">的\*</span><span class="sxs-lookup"><span data-stu-id="d33e4-119">a\*</span></span>  | <span data-ttu-id="d33e4-120">aA、ag、Apple</span><span class="sxs-lookup"><span data-stu-id="d33e4-120">aA, ag, Apple</span></span> | <span data-ttu-id="d33e4-121">香蕉</span><span class="sxs-lookup"><span data-stu-id="d33e4-121">banana</span></span> |
|<span data-ttu-id="d33e4-122">?</span><span class="sxs-lookup"><span data-stu-id="d33e4-122">?</span></span>       |<span data-ttu-id="d33e4-123">符合該位置中的一個字元</span><span class="sxs-lookup"><span data-stu-id="d33e4-123">Match one character in that position</span></span> | <span data-ttu-id="d33e4-124">？ n</span><span class="sxs-lookup"><span data-stu-id="d33e4-124">?n</span></span> | <span data-ttu-id="d33e4-125">a、in、on</span><span class="sxs-lookup"><span data-stu-id="d33e4-125">an, in, on</span></span> | <span data-ttu-id="d33e4-126">跑</span><span class="sxs-lookup"><span data-stu-id="d33e4-126">ran</span></span> |
|<span data-ttu-id="d33e4-127">\[ \]</span><span class="sxs-lookup"><span data-stu-id="d33e4-127">\[ \]</span></span>   |<span data-ttu-id="d33e4-128">符合字元範圍</span><span class="sxs-lookup"><span data-stu-id="d33e4-128">Match a range of characters</span></span> | <span data-ttu-id="d33e4-129">\[a-l \] ook</span><span class="sxs-lookup"><span data-stu-id="d33e4-129">\[a-l\]ook</span></span> | <span data-ttu-id="d33e4-130">著作、庫、尋找</span><span class="sxs-lookup"><span data-stu-id="d33e4-130">book, cook, look</span></span> | <span data-ttu-id="d33e4-131">接管</span><span class="sxs-lookup"><span data-stu-id="d33e4-131">took</span></span> |
|<span data-ttu-id="d33e4-132">\[ \]</span><span class="sxs-lookup"><span data-stu-id="d33e4-132">\[ \]</span></span>   |<span data-ttu-id="d33e4-133">符合特定字元</span><span class="sxs-lookup"><span data-stu-id="d33e4-133">Match specific characters</span></span> | <span data-ttu-id="d33e4-134">\[bc \] ook</span><span class="sxs-lookup"><span data-stu-id="d33e4-134">\[bc\]ook</span></span> | <span data-ttu-id="d33e4-135">書籍，庫</span><span class="sxs-lookup"><span data-stu-id="d33e4-135">book, cook</span></span> | <span data-ttu-id="d33e4-136">鉤</span><span class="sxs-lookup"><span data-stu-id="d33e4-136">hook</span></span> |

<span data-ttu-id="d33e4-137">您可以在相同的字組模式中包含多個萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d33e4-137">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="d33e4-138">例如，若要尋找名稱開頭為字母 **a** 到 **l** 的文字檔，請輸入：</span><span class="sxs-lookup"><span data-stu-id="d33e4-138">For example, to find text files with names that begin with the letters **a** through **l** , type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="d33e4-139">許多 Cmdlet 接受參數值中的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d33e4-139">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="d33e4-140">每個 Cmdlet 的說明主題會說明哪些參數接受萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d33e4-140">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="d33e4-141">對於接受萬用字元的參數，其用法不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="d33e4-141">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="d33e4-142">您可以在命令和腳本區塊中使用萬用字元，例如，建立代表屬性值的文字模式。</span><span class="sxs-lookup"><span data-stu-id="d33e4-142">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="d33e4-143">例如，下列命令會取得 **ServiceType** 屬性值包含 **互動式** 的服務。</span><span class="sxs-lookup"><span data-stu-id="d33e4-143">For example, the following command gets services in which the **ServiceType** property value includes **Interactive** .</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="d33e4-144">在下列範例中， `If` 語句包含使用萬用字元來尋找屬性值的條件。</span><span class="sxs-lookup"><span data-stu-id="d33e4-144">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="d33e4-145">如果還原點的 **描述** 包含 **PowerShell** ，此命令會將還原點的 **CreationTime** 屬性值新增至記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d33e4-145">If the restore point's **Description** includes **PowerShell** , the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="d33e4-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d33e4-146">SEE ALSO</span></span>

[<span data-ttu-id="d33e4-147">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="d33e4-147">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="d33e4-148">about_If</span><span class="sxs-lookup"><span data-stu-id="d33e4-148">about_If</span></span>](about_If.md)

[<span data-ttu-id="d33e4-149">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="d33e4-149">about_Script_Blocks</span></span>](about_Script_Blocks.md)
