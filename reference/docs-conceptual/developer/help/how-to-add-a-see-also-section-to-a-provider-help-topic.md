---
title: 如何新增＜另請參閱＞小節至提供者說明主題
ms.date: 09/12/2016
ms.openlocfilehash: 54adf4bb941888583eb749b7b5322b27d84c7af7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893470"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="74b08-102">如何新增＜另請參閱＞小節至提供者說明主題</span><span class="sxs-lookup"><span data-stu-id="74b08-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="74b08-103">本節說明如何填入提供者說明主題的 [**另請參閱**] 區段。</span><span class="sxs-lookup"><span data-stu-id="74b08-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="74b08-104">[**另請參閱**] 區段是由與提供者相關的主題清單所組成，或可能有助於使用者進一步瞭解並使用該提供者。</span><span class="sxs-lookup"><span data-stu-id="74b08-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="74b08-105">主題清單可包含 Windows PowerShell 中的 Cmdlet 說明、提供者說明和概念性（「關於」）說明主題。</span><span class="sxs-lookup"><span data-stu-id="74b08-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="74b08-106">它也可以包含書籍、論文和線上主題的參考，包括目前提供者說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="74b08-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="74b08-107">當您參考線上主題時，請以純文字提供 URI 或搜尋詞彙。</span><span class="sxs-lookup"><span data-stu-id="74b08-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="74b08-108">此 `Get-Help` Cmdlet 不會連結或重新導向至清單中的任何主題。</span><span class="sxs-lookup"><span data-stu-id="74b08-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="74b08-109">此外， `Online` Cmdlet 的參數 `Get-Help` 無法與提供者說明搭配運作。</span><span class="sxs-lookup"><span data-stu-id="74b08-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="74b08-110">[**另請參閱**] 區段是從 `RelatedLinks` 元素及其包含的標記建立而來。</span><span class="sxs-lookup"><span data-stu-id="74b08-110">The **See Also** section is created from the `RelatedLinks` element and the tags that it contains.</span></span>
<span data-ttu-id="74b08-111">下列 XML 顯示如何新增標記。</span><span class="sxs-lookup"><span data-stu-id="74b08-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="74b08-112">加入另請參閱主題</span><span class="sxs-lookup"><span data-stu-id="74b08-112">To Add SEE ALSO Topics</span></span>

1. <span data-ttu-id="74b08-113">在檔案中 `<AssemblyName>.dll-help.xml` 的專案內 `providerHelp` ，加入 `RelatedLinks` 元素。</span><span class="sxs-lookup"><span data-stu-id="74b08-113">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="74b08-114">`RelatedLinks`元素應該是元素中的最後一個元素 `providerHelp` 。</span><span class="sxs-lookup"><span data-stu-id="74b08-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="74b08-115">`RelatedLinks`每個提供者說明主題中只允許一個元素。</span><span class="sxs-lookup"><span data-stu-id="74b08-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="74b08-116">例如：</span><span class="sxs-lookup"><span data-stu-id="74b08-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. <span data-ttu-id="74b08-117">針對 [**另請參閱**] 區段中的每個主題，在 `RelatedLinks` 元素內加入 `navigationLink` 元素。</span><span class="sxs-lookup"><span data-stu-id="74b08-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="74b08-118">然後，在每個 `navigationLink` 元素內加入一個專案 `linkText` 和一個專案 `uri` 。</span><span class="sxs-lookup"><span data-stu-id="74b08-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="74b08-119">如果您不是使用專案 `uri` ，您可以將它新增為空的元素（ \<uri/> ）。</span><span class="sxs-lookup"><span data-stu-id="74b08-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="74b08-120">例如：</span><span class="sxs-lookup"><span data-stu-id="74b08-120">For example:</span></span>

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

1. <span data-ttu-id="74b08-121">在標記之間輸入主題名稱 `linkText` 。</span><span class="sxs-lookup"><span data-stu-id="74b08-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="74b08-122">如果您要提供 URI，請在標記之間輸入 `uri` 。</span><span class="sxs-lookup"><span data-stu-id="74b08-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="74b08-123">若要指出目前提供者說明主題的線上版本，請在 `linkText` 標記之間輸入「線上版本：」，而不是主題名稱。</span><span class="sxs-lookup"><span data-stu-id="74b08-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="74b08-124">一般而言，「線上版本：」連結是 [另請參閱主題] 清單中的第一個主題。</span><span class="sxs-lookup"><span data-stu-id="74b08-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="74b08-125">下列範例包含三個 [另請參閱] 主題。</span><span class="sxs-lookup"><span data-stu-id="74b08-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="74b08-126">第一個參考目前主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="74b08-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="74b08-127">第二個則是指 Windows PowerShell Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="74b08-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="74b08-128">第三個參考另一個線上主題。</span><span class="sxs-lookup"><span data-stu-id="74b08-128">The third refers to another online topic.</span></span>

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
