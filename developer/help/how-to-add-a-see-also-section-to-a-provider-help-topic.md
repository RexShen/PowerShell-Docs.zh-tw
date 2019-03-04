---
title: 操作說明，請參閱也將區段新增至提供者說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858344"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="dfb23-102">如何新增＜另請參閱＞小節至提供者說明主題</span><span class="sxs-lookup"><span data-stu-id="dfb23-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="dfb23-103">本節說明如何以填入**另請參閱**區段的提供者說明主題。</span><span class="sxs-lookup"><span data-stu-id="dfb23-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="dfb23-104">**另請參閱**區段包含的主題相關的提供者，或可能有幫助使用者深入了解，並使用提供者清單。</span><span class="sxs-lookup"><span data-stu-id="dfb23-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="dfb23-105">主題清單可以包含 cmdlet 的說明，請提供者說明和概念性 （「 關於 」） 在 Windows PowerShell 中的 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="dfb23-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="dfb23-106">它也可以包含書籍、 文件及線上主題，包括目前的提供者說明主題的線上版本的參考。</span><span class="sxs-lookup"><span data-stu-id="dfb23-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="dfb23-107">當您參考線上主題時，提供 URI 或搜尋詞彙，以純文字。</span><span class="sxs-lookup"><span data-stu-id="dfb23-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="dfb23-108">`Get-Help` Cmdlet 不會連結或重新導向至任何清單中的主題。</span><span class="sxs-lookup"><span data-stu-id="dfb23-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="dfb23-109">此外，`Online`參數的`Get-Help`cmdlet 與提供者說明無法運作。</span><span class="sxs-lookup"><span data-stu-id="dfb23-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="dfb23-110">另請參閱 > 一節從建立`RelatedLinks`項目和它所包含的標記。</span><span class="sxs-lookup"><span data-stu-id="dfb23-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="dfb23-111">下列 XML 示範如何新增標記。</span><span class="sxs-lookup"><span data-stu-id="dfb23-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="dfb23-112">若要新增 「 另請參閱 」 主題</span><span class="sxs-lookup"><span data-stu-id="dfb23-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="dfb23-113">在  *AssemblyName*.dll help.xml 檔案，內`providerHelp`項目，新增`RelatedLinks`項目。</span><span class="sxs-lookup"><span data-stu-id="dfb23-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="dfb23-114">`RelatedLinks`元素應該是中的最後一個項目`providerHelp`項目。</span><span class="sxs-lookup"><span data-stu-id="dfb23-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="dfb23-115">只有一個`RelatedLinks`允許每個提供者說明主題中的項目。</span><span class="sxs-lookup"><span data-stu-id="dfb23-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="dfb23-116">例如：</span><span class="sxs-lookup"><span data-stu-id="dfb23-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="dfb23-117">每個主題中**另請參閱**區段中，內`RelatedLinks`項目，新增`navigationLink`項目。</span><span class="sxs-lookup"><span data-stu-id="dfb23-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="dfb23-118">然後，在各`navigationLink`項目，新增一個`linkText`項目和一個`uri`項目。</span><span class="sxs-lookup"><span data-stu-id="dfb23-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="dfb23-119">如果您不使用`uri`項目，您可以將它新增為空項目 (\<uri / >)。</span><span class="sxs-lookup"><span data-stu-id="dfb23-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="dfb23-120">例如：</span><span class="sxs-lookup"><span data-stu-id="dfb23-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="dfb23-121">輸入主題名稱之間`linkText`標記。</span><span class="sxs-lookup"><span data-stu-id="dfb23-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="dfb23-122">如果您要提供的 URI，它之間輸入`uri`標記。</span><span class="sxs-lookup"><span data-stu-id="dfb23-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="dfb23-123">若要指出目前的提供者說明主題的線上版本之間`linkText`標記中，輸入 「 線上版本:"而不是主題名稱。</span><span class="sxs-lookup"><span data-stu-id="dfb23-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="dfb23-124">一般而言，「 線上版本:"連結是在 < 另請參閱主題清單中的第一個主題。</span><span class="sxs-lookup"><span data-stu-id="dfb23-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="dfb23-125">下列範例包含三個另請參閱主題。</span><span class="sxs-lookup"><span data-stu-id="dfb23-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="dfb23-126">第一個參考目前主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="dfb23-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="dfb23-127">第二個是指 Windows PowerShell cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="dfb23-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="dfb23-128">第三個指的是另一個線上主題。</span><span class="sxs-lookup"><span data-stu-id="dfb23-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```