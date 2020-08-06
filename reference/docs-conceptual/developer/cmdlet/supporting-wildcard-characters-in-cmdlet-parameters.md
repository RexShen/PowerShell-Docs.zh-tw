---
title: 在 Cmdlet 參數中支援萬用字元
ms.date: 08/26/2019
ms.openlocfilehash: 062e3d50dddd0bc84e57f5254a93289acbabe38b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786402"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="c423d-102">在 Cmdlet 參數中支援萬用字元</span><span class="sxs-lookup"><span data-stu-id="c423d-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="c423d-103">通常，您必須設計 Cmdlet 來針對一組資源執行，而不是針對單一資源。</span><span class="sxs-lookup"><span data-stu-id="c423d-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="c423d-104">例如，Cmdlet 可能需要找出資料存放區中具有相同名稱或副檔名的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="c423d-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="c423d-105">當您設計將針對一組資源執行的 Cmdlet 時，必須提供萬用字元支援。</span><span class="sxs-lookup"><span data-stu-id="c423d-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="c423d-106">使用萬用字元有時稱為*通配*。</span><span class="sxs-lookup"><span data-stu-id="c423d-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="c423d-107">使用萬用字元的 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c423d-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="c423d-108">許多 Windows PowerShell Cmdlet 都支援其參數值的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c423d-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="c423d-109">例如，幾乎每個具有或參數的 Cmdlet 都 `Name` `Path` 支援這些參數的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c423d-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="c423d-110"> (，雖然具有參數的大多數 Cmdlet `Path` 也具有 `LiteralPath` 不支援萬用字元的參數。 ) 下列命令會顯示如何使用萬用字元來傳回目前會話中名稱包含 Get 動詞的所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c423d-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="c423d-111">支援的萬用字元</span><span class="sxs-lookup"><span data-stu-id="c423d-111">Supported Wildcard Characters</span></span>

<span data-ttu-id="c423d-112">Windows PowerShell 支援下列萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c423d-112">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="c423d-113">萬用字元</span><span class="sxs-lookup"><span data-stu-id="c423d-113">Wildcard</span></span> |                             <span data-ttu-id="c423d-114">描述</span><span class="sxs-lookup"><span data-stu-id="c423d-114">Description</span></span>                             |  <span data-ttu-id="c423d-115">範例</span><span class="sxs-lookup"><span data-stu-id="c423d-115">Example</span></span>   |     <span data-ttu-id="c423d-116">相符項</span><span class="sxs-lookup"><span data-stu-id="c423d-116">Matches</span></span>      | <span data-ttu-id="c423d-117">不符合</span><span class="sxs-lookup"><span data-stu-id="c423d-117">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="c423d-118">符合零或多個字元，從指定的位置開始</span><span class="sxs-lookup"><span data-stu-id="c423d-118">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="c423d-119">A、ag、Apple</span><span class="sxs-lookup"><span data-stu-id="c423d-119">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="c423d-120">?</span><span class="sxs-lookup"><span data-stu-id="c423d-120">?</span></span>        | <span data-ttu-id="c423d-121">符合指定位置的任何字元</span><span class="sxs-lookup"><span data-stu-id="c423d-121">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="c423d-122">中的、</span><span class="sxs-lookup"><span data-stu-id="c423d-122">An, in, on</span></span>       | <span data-ttu-id="c423d-123">延續</span><span class="sxs-lookup"><span data-stu-id="c423d-123">ran</span></span>            |
| <span data-ttu-id="c423d-124">[ ]</span><span class="sxs-lookup"><span data-stu-id="c423d-124">[ ]</span></span>      | <span data-ttu-id="c423d-125">符合字元範圍</span><span class="sxs-lookup"><span data-stu-id="c423d-125">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="c423d-126">著作、庫、尋找</span><span class="sxs-lookup"><span data-stu-id="c423d-126">book, cook, look</span></span> | <span data-ttu-id="c423d-127">nook，花費了</span><span class="sxs-lookup"><span data-stu-id="c423d-127">nook, took</span></span>     |
| <span data-ttu-id="c423d-128">[ ]</span><span class="sxs-lookup"><span data-stu-id="c423d-128">[ ]</span></span>      | <span data-ttu-id="c423d-129">符合指定的字元</span><span class="sxs-lookup"><span data-stu-id="c423d-129">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="c423d-130">書籍、nook</span><span class="sxs-lookup"><span data-stu-id="c423d-130">book, nook</span></span>       | <span data-ttu-id="c423d-131">庫、外觀</span><span class="sxs-lookup"><span data-stu-id="c423d-131">cook, look</span></span>     |

<span data-ttu-id="c423d-132">當您設計支援萬用字元的 Cmdlet 時，允許組合萬用字元。</span><span class="sxs-lookup"><span data-stu-id="c423d-132">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="c423d-133">例如，下列命令 `Get-ChildItem` 會使用 Cmdlet 來取出 c:\Techdocs 資料夾中的所有 .txt 檔案，並以字母 "a" 到 "l."</span><span class="sxs-lookup"><span data-stu-id="c423d-133">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="c423d-134">先前的命令會使用範圍萬用字元 `[a-l]` 來指定檔案名的開頭應為 "a" 到 "l" 字元，並使用 `*` 萬用字元做為檔案名的第一個字母和 **.txt**副檔名之間任何字元的預留位置。</span><span class="sxs-lookup"><span data-stu-id="c423d-134">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="c423d-135">下列範例使用的範圍萬用字元模式會排除字母 "d"，但會包含 "a" 到 "f" 的所有其他字母。</span><span class="sxs-lookup"><span data-stu-id="c423d-135">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="c423d-136">處理萬用字元模式中的常值字元</span><span class="sxs-lookup"><span data-stu-id="c423d-136">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="c423d-137">如果您指定的萬用字元模式包含不應該解釋為萬用字元的常值字元，請使用倒引號字元 (`` ` ``) 做為逸出字元。</span><span class="sxs-lookup"><span data-stu-id="c423d-137">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="c423d-138">當您指定常值字元 int PowerShell API 時，請使用單一倒引號。</span><span class="sxs-lookup"><span data-stu-id="c423d-138">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="c423d-139">當您在 PowerShell 命令提示字元中指定常值時，請使用兩個倒引號。</span><span class="sxs-lookup"><span data-stu-id="c423d-139">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="c423d-140">例如，下列模式包含兩個必須逐字採用的括弧。</span><span class="sxs-lookup"><span data-stu-id="c423d-140">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="c423d-141">當用於 PowerShell API 時，請使用：</span><span class="sxs-lookup"><span data-stu-id="c423d-141">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="c423d-142">"John Smith \` [\* ']"</span><span class="sxs-lookup"><span data-stu-id="c423d-142">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="c423d-143">從 PowerShell 命令提示字元使用時：</span><span class="sxs-lookup"><span data-stu-id="c423d-143">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="c423d-144">"John Smith \` \` [\* \` ']"</span><span class="sxs-lookup"><span data-stu-id="c423d-144">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="c423d-145">此模式符合 "John Smith [Marketing]" 或 "John Smith [開發]"。</span><span class="sxs-lookup"><span data-stu-id="c423d-145">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="c423d-146">例如：</span><span class="sxs-lookup"><span data-stu-id="c423d-146">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="c423d-147">Cmdlet 輸出和萬用字元</span><span class="sxs-lookup"><span data-stu-id="c423d-147">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="c423d-148">當 Cmdlet 參數支援萬用字元時，作業通常會產生陣列輸出。</span><span class="sxs-lookup"><span data-stu-id="c423d-148">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="c423d-149">有時候，支援陣列輸出並不合理，因為使用者可能只會使用單一專案。</span><span class="sxs-lookup"><span data-stu-id="c423d-149">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="c423d-150">例如，此 `Set-Location` Cmdlet 不支援陣列輸出，因為使用者只會設定一個位置。</span><span class="sxs-lookup"><span data-stu-id="c423d-150">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="c423d-151">在此情況下，Cmdlet 仍然支援萬用字元，但會強制解析成單一位置。</span><span class="sxs-lookup"><span data-stu-id="c423d-151">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="c423d-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c423d-152">See Also</span></span>

[<span data-ttu-id="c423d-153">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c423d-153">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="c423d-154">WildcardPattern 類別</span><span class="sxs-lookup"><span data-stu-id="c423d-154">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
