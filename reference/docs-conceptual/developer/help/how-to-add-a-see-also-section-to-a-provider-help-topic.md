---
ms.date: 09/12/2016
ms.topic: reference
title: 如何新增＜另請參閱＞小節至提供者說明主題
description: 如何新增＜另請參閱＞小節至提供者說明主題
ms.openlocfilehash: df0b14ba84e04baf404081944ef62ef6745d74b2
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667652"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="4bdc2-103">如何新增＜另請參閱＞小節至提供者說明主題</span><span class="sxs-lookup"><span data-stu-id="4bdc2-103">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="4bdc2-104">本節說明如何填入提供者說明主題的 [另 **請參閱** ] 區段。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-104">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="4bdc2-105">[另 **請參閱** ] 區段包含與提供者相關的主題清單，或可能有助於使用者更瞭解並使用提供者。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-105">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="4bdc2-106">主題清單可以包含 Cmdlet 說明、提供者說明和概念性 ( Windows PowerShell 中的「關於」 ) 說明主題。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-106">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="4bdc2-107">它也可以包含書籍、紙張和線上主題的參考，包括目前提供者說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-107">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="4bdc2-108">當您參考線上主題時，請以純文字提供 URI 或搜尋字詞。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-108">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="4bdc2-109">`Get-Help`Cmdlet 不會連結或重新導向至清單中的任何主題。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-109">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="4bdc2-110">此外， `Online` Cmdlet 的參數 `Get-Help` 無法與提供者說明一起使用。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-110">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="4bdc2-111">[ **另請參閱** ] 區段是從專案 `RelatedLinks` 和它所包含的標記所建立。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-111">The **See Also** section is created from the `RelatedLinks` element and the tags that it contains.</span></span>
<span data-ttu-id="4bdc2-112">下列 XML 說明如何加入標記。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-112">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="4bdc2-113">若要加入，請參閱主題</span><span class="sxs-lookup"><span data-stu-id="4bdc2-113">To Add SEE ALSO Topics</span></span>

1. <span data-ttu-id="4bdc2-114">在檔案中 `<AssemblyName>.dll-help.xml` 的專案內 `providerHelp` ，加入 `RelatedLinks` 元素。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-114">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="4bdc2-115">`RelatedLinks`元素應該是專案中的最後一個元素 `providerHelp` 。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-115">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="4bdc2-116">`RelatedLinks`每個提供者說明主題中只允許一個元素。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-116">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="4bdc2-117">例如：</span><span class="sxs-lookup"><span data-stu-id="4bdc2-117">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. <span data-ttu-id="4bdc2-118">針對 [ **另請參閱** ] 區段中的每個主題，在專案中 `RelatedLinks` 加入一個 `navigationLink` 元素。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-118">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="4bdc2-119">然後，在每個專案中 `navigationLink` 加入一個專案 `linkText` 和一個 `uri` 元素。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-119">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="4bdc2-120">如果您未使用專案 `uri` ，您可以將它新增為空白元素， (\<uri/>) 。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-120">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="4bdc2-121">例如：</span><span class="sxs-lookup"><span data-stu-id="4bdc2-121">For example:</span></span>

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

1. <span data-ttu-id="4bdc2-122">輸入標記之間的主題名稱 `linkText` 。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-122">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="4bdc2-123">如果您要提供 URI，請在標記之間輸入 `uri` 。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-123">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="4bdc2-124">若要指出目前提供者說明主題的線上版本，請在 `linkText` 標記之間輸入 "online version："，而不是主題名稱。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-124">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="4bdc2-125">一般而言，[線上版本：] 連結是 [另請參閱主題] 清單中的第一個主題。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-125">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="4bdc2-126">下列範例包含三個另請參閱主題。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-126">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="4bdc2-127">第一個參考目前主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-127">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="4bdc2-128">第二個是指 Windows PowerShell 的 Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-128">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="4bdc2-129">第三個是另一個線上主題。</span><span class="sxs-lookup"><span data-stu-id="4bdc2-129">The third refers to another online topic.</span></span>

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
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
