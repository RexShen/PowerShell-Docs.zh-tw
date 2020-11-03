---
description: 描述您可以用來根據條件式測試結果執行命令區塊的語言語句。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: d53077ba54e0680eea6addc87f4e9aeb3eafc4fe
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207876"
---
# <a name="about-while"></a><span data-ttu-id="464b0-104">關於 While</span><span class="sxs-lookup"><span data-stu-id="464b0-104">About While</span></span>

## <a name="short-description"></a><span data-ttu-id="464b0-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="464b0-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="464b0-106">描述您可以用來根據條件式測試結果執行命令區塊的語言語句。</span><span class="sxs-lookup"><span data-stu-id="464b0-106">Describes a language statement that you can use to run a command block based on the results of a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="464b0-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="464b0-107">LONG DESCRIPTION</span></span>
<span data-ttu-id="464b0-108">While 語句 (也稱為 While 迴圈) 是一種語言結構，可用於建立在命令區塊中執行命令的迴圈（只要條件式測試評估為 true）。</span><span class="sxs-lookup"><span data-stu-id="464b0-108">The While statement (also known as a While loop) is a language construct for creating a loop that runs commands in a command block as long as a conditional test evaluates to true.</span></span> <span data-ttu-id="464b0-109">While 語句比 For 語句更容易建立，因為其語法較不復雜。</span><span class="sxs-lookup"><span data-stu-id="464b0-109">The While statement is easier to construct than a For statement because its syntax is less complicated.</span></span> <span data-ttu-id="464b0-110">此外，它比 Foreach 語句更有彈性，因為您在 While 語句中指定條件式測試來控制迴圈執行的次數。</span><span class="sxs-lookup"><span data-stu-id="464b0-110">In addition, it is more flexible than the Foreach statement because you specify a conditional test in the While statement to control how many times the loop runs.</span></span>

<span data-ttu-id="464b0-111">以下顯示 While 語句語法：</span><span class="sxs-lookup"><span data-stu-id="464b0-111">The following shows the While statement syntax:</span></span>

```powershell
while (<condition>){<statement list>}
```

<span data-ttu-id="464b0-112">當您執行 While 語句時，PowerShell 會 `<condition>` 先評估語句的區段，然後再輸入 `<statement list>` 區段。</span><span class="sxs-lookup"><span data-stu-id="464b0-112">When you run a While statement, PowerShell evaluates the `<condition>` section of the statement before entering the `<statement list>` section.</span></span> <span data-ttu-id="464b0-113">語句的條件部分會解析為 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="464b0-113">The condition portion of the statement resolves to either true or false.</span></span> <span data-ttu-id="464b0-114">只要條件維持為 true，PowerShell 就會重新運行 `<statement list>` 區段。</span><span class="sxs-lookup"><span data-stu-id="464b0-114">As long as the condition remains true, PowerShell reruns the `<statement list>` section.</span></span>

<span data-ttu-id="464b0-115">`<statement list>`語句的區段包含一或多個在每次輸入或重複迴圈時都會執行的命令。</span><span class="sxs-lookup"><span data-stu-id="464b0-115">The `<statement list>` section of the statement contains one or more commands that are run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="464b0-116">例如，如果未建立 $val 變數，或是已建立 $val 變數，並將其初始化為0，則下列 While 語句會顯示數位1到3。</span><span class="sxs-lookup"><span data-stu-id="464b0-116">For example, the following While statement displays the numbers 1 through 3 if the $val variable has not been created or if the $val variable has been created and initialized to 0.</span></span>

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

<span data-ttu-id="464b0-117">在此範例中， ($val 的條件不等於 3) 在 $val \= 0、1、2時為 true。</span><span class="sxs-lookup"><span data-stu-id="464b0-117">In this example, the condition ($val is not equal to 3) is true while $val \= 0, 1, 2.</span></span> <span data-ttu-id="464b0-118">每次執行迴圈時，$val 會使用 \+ \+ 一元遞增運算子 ($val) 遞增 1 \+ \+ 。</span><span class="sxs-lookup"><span data-stu-id="464b0-118">Each time through the loop, $val is incremented by 1 using the \+\+ unary increment operator ($val\+\+).</span></span> <span data-ttu-id="464b0-119">最後一次執行迴圈，$val \= 3。</span><span class="sxs-lookup"><span data-stu-id="464b0-119">The last time through the loop, $val \= 3.</span></span> <span data-ttu-id="464b0-120">當 $val 等於3時，條件陳述式會評估為 false，而且迴圈會結束。</span><span class="sxs-lookup"><span data-stu-id="464b0-120">When $val equals 3, the condition statement evaluates to false, and the loop exits.</span></span>

<span data-ttu-id="464b0-121">若要在 PowerShell 命令提示字元中方便地寫入此命令，您可以透過下列方式輸入：</span><span class="sxs-lookup"><span data-stu-id="464b0-121">To conveniently write this command at the PowerShell command prompt, you can enter it in the following way:</span></span>

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

<span data-ttu-id="464b0-122">請注意，分號會分隔第一個命令，此命令會將 $val 的值寫入主控台，而第二個命令會將1新增至 $val。</span><span class="sxs-lookup"><span data-stu-id="464b0-122">Notice that the semicolon separates the first command that adds 1 to $val from the second command that writes the value of $val to the console.</span></span>

## <a name="see-also"></a><span data-ttu-id="464b0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="464b0-123">SEE ALSO</span></span>

[<span data-ttu-id="464b0-124">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="464b0-124">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="464b0-125">about_Do</span><span class="sxs-lookup"><span data-stu-id="464b0-125">about_Do</span></span>](about_Do.md)

[<span data-ttu-id="464b0-126">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="464b0-126">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="464b0-127">about_For</span><span class="sxs-lookup"><span data-stu-id="464b0-127">about_For</span></span>](about_For.md)

[<span data-ttu-id="464b0-128">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="464b0-128">about_Language_Keywords</span></span>](about_Language_Keywords.md)
