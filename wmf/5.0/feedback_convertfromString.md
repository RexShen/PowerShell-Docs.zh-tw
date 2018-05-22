---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: e4588e8c69efb965cd33c273ad09a8bef8e9bf16
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a><span data-ttu-id="60e4f-102">從字串擷取和剖析結構化物件</span><span class="sxs-lookup"><span data-stu-id="60e4f-102">Extract and Parse Structured Objects out of String</span></span>
<span data-ttu-id="60e4f-103">本主題也將介紹 ConvertFrom-String Cmdlet 的一些額外功能︰</span><span class="sxs-lookup"><span data-stu-id="60e4f-103">This also introduces some additional functionality for the ConvertFrom-String cmdlet:</span></span>

-   <span data-ttu-id="60e4f-104">預設情況下會移除範圍文字屬性，</span><span class="sxs-lookup"><span data-stu-id="60e4f-104">Removes the extent text property by default.</span></span> <span data-ttu-id="60e4f-105">您可以使用 IncludeExtent 參數將此屬性加入。</span><span class="sxs-lookup"><span data-stu-id="60e4f-105">You can include it with the -IncludeExtent parameter.</span></span>

-   <span data-ttu-id="60e4f-106">許多 MVP 和社群意見反應的學習演算法 Bug 修正。</span><span class="sxs-lookup"><span data-stu-id="60e4f-106">Many learning algorithm bug fixes from MVP and community feedback.</span></span>

-   <span data-ttu-id="60e4f-107">新的 -UpdateTemplate 參數，可將學習演算法的結果儲存成範本檔案中的註解，</span><span class="sxs-lookup"><span data-stu-id="60e4f-107">A new -UpdateTemplate parameter to save the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="60e4f-108">使得學習程序 (最慢的階段) 成為單次成本。</span><span class="sxs-lookup"><span data-stu-id="60e4f-108">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="60e4f-109">現在使用包含已編碼學習演算法的範本，幾乎可以瞬間執行 Convert-String。</span><span class="sxs-lookup"><span data-stu-id="60e4f-109">Running Convert-String with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>


<a name="extract-and-parse-structured-objects-out-of-string-content"></a><span data-ttu-id="60e4f-110">從字串內容擷取和剖析結構化物件</span><span class="sxs-lookup"><span data-stu-id="60e4f-110">Extract and parse structured objects out of string content</span></span>
----------------------------------------------------------

<span data-ttu-id="60e4f-111">在與 [Microsoft Research](http://research.microsoft.com/) 合作之下，已新增 **ConvertFrom-String** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="60e4f-111">In collaboration with [Microsoft Research](http://research.microsoft.com/), a new **ConvertFrom-String** cmdlet has been added.</span></span>

<span data-ttu-id="60e4f-112">這個 Cmdlet 支援兩種模式︰基本的分隔剖析和自動產生的範例驅動剖析。</span><span class="sxs-lookup"><span data-stu-id="60e4f-112">This cmdlet supports two modes: basic delimited parsing, and auto generated example-driven parsing.</span></span>

<span data-ttu-id="60e4f-113">根據預設，分隔的剖析將輸入從空白字元位置分割，並將屬性名稱指派給產生的群組。</span><span class="sxs-lookup"><span data-stu-id="60e4f-113">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span> <span data-ttu-id="60e4f-114">您可以自訂分隔符號︰</span><span class="sxs-lookup"><span data-stu-id="60e4f-114">You can customize the delimiter:</span></span>

> <span data-ttu-id="60e4f-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="60e4f-115">1 \[C:\\temp\] &gt;&gt; "Hello World" | ConvertFrom-String | Format-Table -Auto</span></span>

<span data-ttu-id="60e4f-116">P1    P2</span><span class="sxs-lookup"><span data-stu-id="60e4f-116">P1    P2</span></span>
--    --

<span data-ttu-id="60e4f-117">此 Cmdlet 也會根據 [Microsoft Research](http://research.microsoft.com) 中的 [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) 研究工作，支援自動產生範例驅動剖析。</span><span class="sxs-lookup"><span data-stu-id="60e4f-117">The cmdlet also supports auto-generated example-driven parsing based on the [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) research work in [Microsoft Research](http://research.microsoft.com).</span></span>

<span data-ttu-id="60e4f-118">若要開始，請考慮使用以文字為基礎的通訊錄︰</span><span class="sxs-lookup"><span data-stu-id="60e4f-118">To get started, consider a text-based address book:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA

<span data-ttu-id="60e4f-119">將幾個範例複製到要作為範本使用的檔案中︰</span><span class="sxs-lookup"><span data-stu-id="60e4f-119">Copy a few examples into a file, which you will use as your template:</span></span>

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA



<span data-ttu-id="60e4f-120">以大括號括住您想要擷取的資料，在這麼做的時候，提供一個名稱。</span><span class="sxs-lookup"><span data-stu-id="60e4f-120">Put curly braces around data that you want to extract, giving it a name as you do so.</span></span> <span data-ttu-id="60e4f-121">因為 **Name** 屬性 (和與其相關聯的其他屬性) 可以出現多次，所以請使用星號 (\*)，表示這會產生多筆記錄 (而非將一大堆內容擷取成一個記錄)︰</span><span class="sxs-lookup"><span data-stu-id="60e4f-121">Because the **Name** property (and its associated other properties) can appear multiple times, use an asterisk (\*) to indicate that this results in multiple records (rather than extracting a bunch of properties into one record):</span></span>

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

<span data-ttu-id="60e4f-122">在這組範例中，**ConvertFrom-String** 現在可以自動從輸入檔擷取具類似結構、以物件為基礎的輸出。</span><span class="sxs-lookup"><span data-stu-id="60e4f-122">From this set of examples, **ConvertFrom-String** can now automatically extract object-based output from input files with similar structure.</span></span>

> <span data-ttu-id="60e4f-123">2 \[C:\\temp\]</span><span class="sxs-lookup"><span data-stu-id="60e4f-123">2 \[C:\\temp\]</span></span>
>
> <span data-ttu-id="60e4f-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span><span class="sxs-lookup"><span data-stu-id="60e4f-124">&gt;&gt; Get-Content .\\addresses.output.txt | ConvertFrom-String -TemplateFile .\\addresses.template.txt | &gt;&gt;&gt; Format-Table -Auto</span></span>
>
> <span data-ttu-id="60e4f-125">ExtentText                     Name               City     State</span><span class="sxs-lookup"><span data-stu-id="60e4f-125">ExtentText                     Name               City     State</span></span>
> ----------                     ----               ----     -----
> <span data-ttu-id="60e4f-126">Ana Trujillo...              Ana Trujillo       Redmond  WA Antonio Moreno...            Antonio Moreno     Renton   WA Thomas Hardy...              Thomas Hardy       Seattle  WA Christina Berglund...        Christina Berglund Redmond  WA Hanna Moos...                Hanna Moos         Puyallup WA</span><span class="sxs-lookup"><span data-stu-id="60e4f-126">Ana Trujillo...                Ana Trujillo       Redmond  WA Antonio Moreno...              Antonio Moreno     Renton   WA Thomas Hardy...                Thomas Hardy       Seattle  WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos         Puyallup WA</span></span>

<span data-ttu-id="60e4f-127">若要在擷取的文字上執行其他資料操作，**ExtentText** 屬性可從擷取記錄中擷取未經處理的文字。</span><span class="sxs-lookup"><span data-stu-id="60e4f-127">To do additional data manipulation on extracted text, the **ExtentText** property captures the raw text from which the record was extracted.</span></span> <span data-ttu-id="60e4f-128">若要提供這項功能的意見反應，或共用您在撰寫時遇到困難的範例內容，請寄電子郵件至 <psdmfb@microsoft.com>。</span><span class="sxs-lookup"><span data-stu-id="60e4f-128">To provide feedback on this feature, or to share content for which you are having difficulty writing examples, please email <psdmfb@microsoft.com>.</span></span>
