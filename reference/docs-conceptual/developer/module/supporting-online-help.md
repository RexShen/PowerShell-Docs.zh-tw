---
title: 支援線上說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: de25b099e61f82891daff87c4c73bb8cad9111a4
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83559976"
---
# <a name="supporting-online-help"></a><span data-ttu-id="d871f-102">支援線上說明</span><span class="sxs-lookup"><span data-stu-id="d871f-102">Supporting Online Help</span></span>

<span data-ttu-id="d871f-103">從 Windows PowerShell 3.0 開始，有兩種方式可支援 `Get-Help` Windows powershell 命令的線上功能。</span><span class="sxs-lookup"><span data-stu-id="d871f-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="d871f-104">本主題說明如何針對不同的命令類型來執行這項功能。</span><span class="sxs-lookup"><span data-stu-id="d871f-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="d871f-105">關於線上說明</span><span class="sxs-lookup"><span data-stu-id="d871f-105">About Online Help</span></span>

<span data-ttu-id="d871f-106">線上說明一直是 Windows PowerShell 的重要部分。</span><span class="sxs-lookup"><span data-stu-id="d871f-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="d871f-107">雖然指令程式會 `Get-Help` 在命令提示字元中顯示說明主題，但許多使用者偏好使用線上閱讀的經驗，包括色彩編碼、超連結，以及在社區內容和 wiki 架構檔中共用想法。</span><span class="sxs-lookup"><span data-stu-id="d871f-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="d871f-108">最重要的是，在「可更新的說明」出現之前，線上說明已提供最新版本的說明檔。</span><span class="sxs-lookup"><span data-stu-id="d871f-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="d871f-109">隨著 Windows PowerShell 3.0 中的「可更新的說明」的出現，線上說明仍然扮演重要的角色。</span><span class="sxs-lookup"><span data-stu-id="d871f-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="d871f-110">除了彈性的使用者體驗之外，線上說明也能協助不使用「可更新的說明」下載說明主題的使用者。</span><span class="sxs-lookup"><span data-stu-id="d871f-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="d871f-111">Get-help-Online 的運作方式</span><span class="sxs-lookup"><span data-stu-id="d871f-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="d871f-112">為了協助使用者尋找命令的線上說明主題，此 `Get-Help` 命令具有線上參數，可開啟使用者的預設網際網路瀏覽器中命令的線上版本說明主題。</span><span class="sxs-lookup"><span data-stu-id="d871f-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="d871f-113">例如，下列命令會開啟 Cmdlet 的線上說明主題 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="d871f-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="d871f-114">若要進行 `Get-Help` 線上執行，此 `Get-Help` Cmdlet 會在下列位置尋找線上版本說明主題的統一資源識別元（URI）。</span><span class="sxs-lookup"><span data-stu-id="d871f-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="d871f-115">命令之說明主題的 [相關連結] 區段中的第一個連結。</span><span class="sxs-lookup"><span data-stu-id="d871f-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="d871f-116">您必須在使用者的電腦上安裝說明主題。</span><span class="sxs-lookup"><span data-stu-id="d871f-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="d871f-117">這項功能是在 Windows PowerShell 2.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="d871f-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="d871f-118">任何命令的 HelpUri 屬性。</span><span class="sxs-lookup"><span data-stu-id="d871f-118">The HelpUri property of any command.</span></span> <span data-ttu-id="d871f-119">即使未在使用者的電腦上安裝命令的說明主題，仍可存取 HelpUri 屬性。</span><span class="sxs-lookup"><span data-stu-id="d871f-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="d871f-120">這項功能是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="d871f-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="d871f-121">`Get-Help`取得 HelpUri 屬性值之前，在 [相關連結] 區段的第一個專案中尋找 URI。</span><span class="sxs-lookup"><span data-stu-id="d871f-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="d871f-122">如果屬性值不正確或已變更，您可以在第一個相關連結中輸入不同的值來覆寫它。</span><span class="sxs-lookup"><span data-stu-id="d871f-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="d871f-123">不過，第一個相關的連結僅適用于在使用者的電腦上安裝說明主題時。</span><span class="sxs-lookup"><span data-stu-id="d871f-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="d871f-124">將 URI 新增至命令說明主題的第一個相關連結</span><span class="sxs-lookup"><span data-stu-id="d871f-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="d871f-125">您可以在 `Get-Help` 命令的 XML 型說明主題的 [相關連結] 區段中，將有效的 URI 新增至第一個專案，以針對任何命令支援-Online。</span><span class="sxs-lookup"><span data-stu-id="d871f-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="d871f-126">這個選項只有在以 XML 為基礎的說明主題中才有效，而且只有在說明主題安裝在使用者的電腦上時才適用。</span><span class="sxs-lookup"><span data-stu-id="d871f-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="d871f-127">安裝說明主題並填入 URI 後，此值會優先于命令的**HelpUri**屬性。</span><span class="sxs-lookup"><span data-stu-id="d871f-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="d871f-128">若要支援這項功能，URI 必須出現在元素中 `maml:uri` 第一個專案下的元素中 `maml:relatedLinks/maml:navigationLink` `maml:relatedLinks` 。</span><span class="sxs-lookup"><span data-stu-id="d871f-128">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="d871f-129">下列 XML 會顯示正確的 URI 位置。</span><span class="sxs-lookup"><span data-stu-id="d871f-129">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="d871f-130">元素中的「線上版本：」文字 `maml:linkText` 是最佳做法，但並非必要。</span><span class="sxs-lookup"><span data-stu-id="d871f-130">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="d871f-131">將 HelpUri 屬性新增至命令</span><span class="sxs-lookup"><span data-stu-id="d871f-131">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="d871f-132">本節說明如何將 HelpUri 屬性新增至不同類型的命令。</span><span class="sxs-lookup"><span data-stu-id="d871f-132">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="d871f-133">將 HelpUri 屬性新增至 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d871f-133">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="d871f-134">針對以 c # 撰寫的 Cmdlet，將**HelpUri**屬性新增至 Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="d871f-134">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="d871f-135">屬性的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。</span><span class="sxs-lookup"><span data-stu-id="d871f-135">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="d871f-136">下列程式碼顯示 Cmdlet 類別的 HelpUri 屬性 `Get-History` 。</span><span class="sxs-lookup"><span data-stu-id="d871f-136">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="d871f-137">將 HelpUri 屬性加入至 Advanced 函數</span><span class="sxs-lookup"><span data-stu-id="d871f-137">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="d871f-138">針對 advanced 函式，將**HelpUri**屬性新增至**CmdletBinding**屬性。</span><span class="sxs-lookup"><span data-stu-id="d871f-138">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="d871f-139">屬性的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。</span><span class="sxs-lookup"><span data-stu-id="d871f-139">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="d871f-140">下列程式碼顯示新行事曆函數的 HelpUri 屬性</span><span class="sxs-lookup"><span data-stu-id="d871f-140">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="d871f-141">將 HelpUri 屬性新增至 CIM 命令</span><span class="sxs-lookup"><span data-stu-id="d871f-141">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="d871f-142">針對 CIM 命令，請將**HelpUri**屬性新增至 CDXML 檔案中的**CmdletMetadata**元素。</span><span class="sxs-lookup"><span data-stu-id="d871f-142">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="d871f-143">屬性的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。</span><span class="sxs-lookup"><span data-stu-id="d871f-143">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="d871f-144">下列程式碼顯示啟動-Debug CIM 命令的 HelpUri 屬性</span><span class="sxs-lookup"><span data-stu-id="d871f-144">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="d871f-145">將 HelpUri 屬性新增至工作流程</span><span class="sxs-lookup"><span data-stu-id="d871f-145">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="d871f-146">針對以 Windows PowerShell 語言撰寫的工作流程，請新增 **。.Externalhelp**批註指示詞至工作流程程式碼。</span><span class="sxs-lookup"><span data-stu-id="d871f-146">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="d871f-147">指示詞的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。</span><span class="sxs-lookup"><span data-stu-id="d871f-147">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="d871f-148">Windows PowerShell 中以 XAML 為基礎的工作流程不支援 HelpUri 屬性。</span><span class="sxs-lookup"><span data-stu-id="d871f-148">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="d871f-149">下列程式碼會顯示。工作流程檔案中的 .Externalhelp 指示詞。</span><span class="sxs-lookup"><span data-stu-id="d871f-149">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
