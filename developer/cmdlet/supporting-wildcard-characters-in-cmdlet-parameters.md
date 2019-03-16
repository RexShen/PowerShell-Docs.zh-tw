---
title: 在 Cmdlet 參數支援萬用字元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059604"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="1f657-102">在 Cmdlet 參數中支援萬用字元</span><span class="sxs-lookup"><span data-stu-id="1f657-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="1f657-103">通常，您必須設計可執行的資源群組中，而不是針對單一資源的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1f657-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="1f657-104">比方說，cmdlet 可能需要在有相同的名稱或延伸模組的資料存放區中找出所有檔案。</span><span class="sxs-lookup"><span data-stu-id="1f657-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="1f657-105">當您設計的 cmdlet，將會針對資源群組中的執行時，您便必須提供萬用字元的支援。</span><span class="sxs-lookup"><span data-stu-id="1f657-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="1f657-106">使用萬用字元有時稱為*萬用字元*。</span><span class="sxs-lookup"><span data-stu-id="1f657-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="1f657-107">使用萬用字元的 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1f657-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="1f657-108">許多 Windows PowerShell cmdlet 的參數值支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="1f657-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="1f657-109">例如，幾乎每個 cmdlet 可`Name`或`Path`參數支援萬用字元為這些參數。</span><span class="sxs-lookup"><span data-stu-id="1f657-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="1f657-110">(雖然大多數的 cmdlet 具有`Path`參數也有`LiteralPath`不支援萬用字元的參數。)下列命令會顯示如何將萬用字元使用返回其名稱中包含 Get 動詞命令的目前工作階段中的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1f657-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="1f657-111">**PS > get 命令 get-\***</span><span class="sxs-lookup"><span data-stu-id="1f657-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="1f657-112">支援的萬用字元</span><span class="sxs-lookup"><span data-stu-id="1f657-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="1f657-113">Windows PowerShell 支援下列的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="1f657-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="1f657-114">萬用字元</span><span class="sxs-lookup"><span data-stu-id="1f657-114">Wildcard character</span></span>|<span data-ttu-id="1f657-115">描述</span><span class="sxs-lookup"><span data-stu-id="1f657-115">Description</span></span>|<span data-ttu-id="1f657-116">範例</span><span class="sxs-lookup"><span data-stu-id="1f657-116">Example</span></span>|<span data-ttu-id="1f657-117">相符項目</span><span class="sxs-lookup"><span data-stu-id="1f657-117">Matches</span></span>|<span data-ttu-id="1f657-118">不符合</span><span class="sxs-lookup"><span data-stu-id="1f657-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="1f657-119">比對零或多個字元，從指定的位置開始</span><span class="sxs-lookup"><span data-stu-id="1f657-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="1f657-120">a\*</span><span class="sxs-lookup"><span data-stu-id="1f657-120">a\*</span></span>|<span data-ttu-id="1f657-121">，ag Apple</span><span class="sxs-lookup"><span data-stu-id="1f657-121">A, ag, Apple</span></span>||
|<span data-ttu-id="1f657-122">?</span><span class="sxs-lookup"><span data-stu-id="1f657-122">?</span></span>|<span data-ttu-id="1f657-123">位於指定位置的相符項目 anycharacter</span><span class="sxs-lookup"><span data-stu-id="1f657-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="1f657-124">？ n</span><span class="sxs-lookup"><span data-stu-id="1f657-124">?n</span></span>|<span data-ttu-id="1f657-125">中，在</span><span class="sxs-lookup"><span data-stu-id="1f657-125">An, in, on</span></span>|<span data-ttu-id="1f657-126">執行</span><span class="sxs-lookup"><span data-stu-id="1f657-126">ran</span></span>|
|<span data-ttu-id="1f657-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="1f657-127">[ ]</span></span>|<span data-ttu-id="1f657-128">比對字元的範圍</span><span class="sxs-lookup"><span data-stu-id="1f657-128">Matches a range of characters</span></span>|<span data-ttu-id="1f657-129">[a-l]ook</span><span class="sxs-lookup"><span data-stu-id="1f657-129">[a-l]ook</span></span>|<span data-ttu-id="1f657-130">書籍、 cook、 外觀</span><span class="sxs-lookup"><span data-stu-id="1f657-130">book, cook, look</span></span>|<span data-ttu-id="1f657-131">花了</span><span class="sxs-lookup"><span data-stu-id="1f657-131">took</span></span>|
|<span data-ttu-id="1f657-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="1f657-132">[ ]</span></span>|<span data-ttu-id="1f657-133">符合指定的字元</span><span class="sxs-lookup"><span data-stu-id="1f657-133">Matches the specified characters</span></span>|<span data-ttu-id="1f657-134">[bc]ook</span><span class="sxs-lookup"><span data-stu-id="1f657-134">[bc]ook</span></span>|<span data-ttu-id="1f657-135">書籍、 cook</span><span class="sxs-lookup"><span data-stu-id="1f657-135">book, cook</span></span>|<span data-ttu-id="1f657-136">尋找</span><span class="sxs-lookup"><span data-stu-id="1f657-136">look</span></span>|

<span data-ttu-id="1f657-137">當您設計支援萬用字元的 cmdlet 時，允許的萬用字元的組合。</span><span class="sxs-lookup"><span data-stu-id="1f657-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="1f657-138">例如，下列命令會使用`Get-ChildItem`cmdlet 來擷取的所有.txt 檔案 c:\Techdocs 資料夾中，開頭為字母"a"到"l。"</span><span class="sxs-lookup"><span data-stu-id="1f657-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="1f657-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="1f657-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="1f657-140">前一個命令會使用範圍萬用字元 **[a-l]** 來指定，檔案名稱應該是以開頭的字元"a"到"l。"</span><span class="sxs-lookup"><span data-stu-id="1f657-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="1f657-141">此命令接著會使用 \* 萬用字元以.txt 為副檔名的檔案名稱的第一個字母之間的任何字元預留位置。</span><span class="sxs-lookup"><span data-stu-id="1f657-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="1f657-142">下列範例會使用範圍的萬用字元模式排除字母"d"，但包含從"a"到"f。 」 的所有其他字母</span><span class="sxs-lookup"><span data-stu-id="1f657-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="1f657-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="1f657-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="1f657-144">處理中萬用字元模式比對常值字元</span><span class="sxs-lookup"><span data-stu-id="1f657-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="1f657-145">如果您指定的萬用字元模式包含常值字元，做為逸出字元倒引號字元 （'）。</span><span class="sxs-lookup"><span data-stu-id="1f657-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="1f657-146">當您以程式設計方式指定常值字元時，使用單一的倒引號。</span><span class="sxs-lookup"><span data-stu-id="1f657-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="1f657-147">當您指定的命令提示字元的常值字元時，使用兩個反引號。</span><span class="sxs-lookup"><span data-stu-id="1f657-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="1f657-148">例如，下列模式包含必須純粹的兩個括號。</span><span class="sxs-lookup"><span data-stu-id="1f657-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="1f657-149">"John Smith \`[\*']"（以程式設計方式指定）</span><span class="sxs-lookup"><span data-stu-id="1f657-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="1f657-150">"John Smith \` \`[\*\`']"（在命令提示字元中指定）</span><span class="sxs-lookup"><span data-stu-id="1f657-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="1f657-151">此模式會比對"John Smith [行銷]"或"John Smith [開發]"。</span><span class="sxs-lookup"><span data-stu-id="1f657-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="1f657-152">Cmdlet 輸出和萬用字元</span><span class="sxs-lookup"><span data-stu-id="1f657-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="1f657-153">當 cmdlet 參數支援萬用字元時，則 cmdlet 作業通常會產生的陣列輸出。</span><span class="sxs-lookup"><span data-stu-id="1f657-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="1f657-154">有時候，它沒有意義支援輸出，因為使用者可能會一次使用單一項目陣列。</span><span class="sxs-lookup"><span data-stu-id="1f657-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="1f657-155">比方說，`Set-Location`指令程式支援的輸出，因為使用者設定的單一位置的陣列。</span><span class="sxs-lookup"><span data-stu-id="1f657-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="1f657-156">在此情況下，cmdlet 仍然支援萬用字元，但它會強制解析至單一位置。</span><span class="sxs-lookup"><span data-stu-id="1f657-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f657-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f657-157">See Also</span></span>

[<span data-ttu-id="1f657-158">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1f657-158">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="1f657-159">WildcardPattern 類別</span><span class="sxs-lookup"><span data-stu-id="1f657-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
