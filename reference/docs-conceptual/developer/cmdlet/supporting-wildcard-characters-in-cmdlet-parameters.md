---
ms.date: 08/26/2019
ms.topic: reference
title: 在 Cmdlet 參數中支援萬用字元
description: 在 Cmdlet 參數中支援萬用字元
ms.openlocfilehash: 06693c62cd2613050bdeb9d6b12ad6e9597a9894
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646395"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="9dcf6-103">在 Cmdlet 參數中支援萬用字元</span><span class="sxs-lookup"><span data-stu-id="9dcf6-103">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="9dcf6-104">通常，您必須設計 Cmdlet 來針對一組資源執行，而不是針對單一資源。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-104">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="9dcf6-105">例如，Cmdlet 可能需要找出資料存放區中具有相同名稱或副檔名的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-105">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="9dcf6-106">當您設計會針對一組資源執行的 Cmdlet 時，您必須提供萬用字元的支援。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-106">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="9dcf6-107">使用萬用字元有時也稱為 *通配*。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-107">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="9dcf6-108">Windows PowerShell 使用萬用字元的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9dcf6-108">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="9dcf6-109">許多 Windows PowerShell Cmdlet 都支援其參數值的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-109">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="9dcf6-110">例如，幾乎每個具有或參數的 Cmdlet 都 `Name` `Path` 支援這些參數的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-110">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="9dcf6-111"> (雖然大部分具有參數的 Cmdlet `Path` 也都有不 `LiteralPath` 支援萬用字元的參數。 ) 下列命令顯示如何使用萬用字元來傳回目前會話中名稱包含 Get 動詞的所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-111">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="9dcf6-112">支援的萬用字元</span><span class="sxs-lookup"><span data-stu-id="9dcf6-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="9dcf6-113">Windows PowerShell 支援下列萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-113">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="9dcf6-114">萬用字元</span><span class="sxs-lookup"><span data-stu-id="9dcf6-114">Wildcard</span></span> |                             <span data-ttu-id="9dcf6-115">說明</span><span class="sxs-lookup"><span data-stu-id="9dcf6-115">Description</span></span>                             |  <span data-ttu-id="9dcf6-116">範例</span><span class="sxs-lookup"><span data-stu-id="9dcf6-116">Example</span></span>   |     <span data-ttu-id="9dcf6-117">相符項</span><span class="sxs-lookup"><span data-stu-id="9dcf6-117">Matches</span></span>      | <span data-ttu-id="9dcf6-118">不符合</span><span class="sxs-lookup"><span data-stu-id="9dcf6-118">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="9dcf6-119">符合零或多個字元（從指定位置開始）</span><span class="sxs-lookup"><span data-stu-id="9dcf6-119">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="9dcf6-120">A、ag、Apple</span><span class="sxs-lookup"><span data-stu-id="9dcf6-120">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="9dcf6-121">?</span><span class="sxs-lookup"><span data-stu-id="9dcf6-121">?</span></span>        | <span data-ttu-id="9dcf6-122">符合指定位置的任何字元</span><span class="sxs-lookup"><span data-stu-id="9dcf6-122">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="9dcf6-123">A、in、on</span><span class="sxs-lookup"><span data-stu-id="9dcf6-123">An, in, on</span></span>       | <span data-ttu-id="9dcf6-124">跑</span><span class="sxs-lookup"><span data-stu-id="9dcf6-124">ran</span></span>            |
| <span data-ttu-id="9dcf6-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="9dcf6-125">[ ]</span></span>      | <span data-ttu-id="9dcf6-126">符合字元範圍</span><span class="sxs-lookup"><span data-stu-id="9dcf6-126">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="9dcf6-127">著作、庫、尋找</span><span class="sxs-lookup"><span data-stu-id="9dcf6-127">book, cook, look</span></span> | <span data-ttu-id="9dcf6-128">nook，花費了</span><span class="sxs-lookup"><span data-stu-id="9dcf6-128">nook, took</span></span>     |
| <span data-ttu-id="9dcf6-129">[ ]</span><span class="sxs-lookup"><span data-stu-id="9dcf6-129">[ ]</span></span>      | <span data-ttu-id="9dcf6-130">符合指定的字元</span><span class="sxs-lookup"><span data-stu-id="9dcf6-130">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="9dcf6-131">書籍，nook</span><span class="sxs-lookup"><span data-stu-id="9dcf6-131">book, nook</span></span>       | <span data-ttu-id="9dcf6-132">庫、外觀</span><span class="sxs-lookup"><span data-stu-id="9dcf6-132">cook, look</span></span>     |

<span data-ttu-id="9dcf6-133">當您設計支援萬用字元的 Cmdlet 時，允許萬用字元的組合。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-133">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="9dcf6-134">例如，下列命令 `Get-ChildItem` 會使用 Cmdlet 取出 c:\Techdocs 資料夾中的所有 .txt 檔案，且開頭為字母 "a" 至 "l"。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-134">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="9dcf6-135">上述命令會使用範圍萬用字元 `[a-l]` 來指定檔案名的開頭應為 "a" 到 "l" 字元，並使用 `*` 萬用字元作為檔案名的第一個字母和 **.txt** 副檔名之間的任何字元的預留位置。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-135">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="9dcf6-136">下列範例使用的範圍萬用字元模式排除字母 "d"，但包含從 "a" 到 "f" 的所有其他字母。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-136">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="9dcf6-137">處理萬用字元模式中的常值字元</span><span class="sxs-lookup"><span data-stu-id="9dcf6-137">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="9dcf6-138">如果您指定的萬用字元模式包含不應解釋為萬用字元的常值字元，請使用倒引號字元 (`` ` ``) 作為 escape 字元。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-138">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="9dcf6-139">當您指定 PowerShell API 的常值字元時，請使用單一倒引號。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-139">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="9dcf6-140">當您在 PowerShell 命令提示字元中指定常值字元時，請使用兩個倒引號。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-140">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="9dcf6-141">例如，下列模式包含兩個必須真正採用的括弧。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-141">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="9dcf6-142">使用於 PowerShell API 時，請使用：</span><span class="sxs-lookup"><span data-stu-id="9dcf6-142">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="9dcf6-143">"John Smith \` [\* ']"</span><span class="sxs-lookup"><span data-stu-id="9dcf6-143">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="9dcf6-144">從 PowerShell 命令提示字元使用時：</span><span class="sxs-lookup"><span data-stu-id="9dcf6-144">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="9dcf6-145">"John Smith \` \` [\* \` ']"</span><span class="sxs-lookup"><span data-stu-id="9dcf6-145">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="9dcf6-146">此模式符合「John Smith [Marketing]」或「John Smith [開發]」。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-146">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="9dcf6-147">例如：</span><span class="sxs-lookup"><span data-stu-id="9dcf6-147">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="9dcf6-148">Cmdlet 輸出和萬用字元</span><span class="sxs-lookup"><span data-stu-id="9dcf6-148">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="9dcf6-149">當 Cmdlet 參數支援萬用字元時，此作業通常會產生陣列輸出。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-149">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="9dcf6-150">有時候，因為使用者可能只會使用單一專案，所以不會支援陣列輸出。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-150">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="9dcf6-151">例如，Cmdlet 不 `Set-Location` 支援陣列輸出，因為使用者只會設定單一位置。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-151">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="9dcf6-152">在此情況下，Cmdlet 仍然支援萬用字元，但它會強制解析成單一位置。</span><span class="sxs-lookup"><span data-stu-id="9dcf6-152">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="9dcf6-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dcf6-153">See Also</span></span>

[<span data-ttu-id="9dcf6-154">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9dcf6-154">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="9dcf6-155">WildcardPattern 類別</span><span class="sxs-lookup"><span data-stu-id="9dcf6-155">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
