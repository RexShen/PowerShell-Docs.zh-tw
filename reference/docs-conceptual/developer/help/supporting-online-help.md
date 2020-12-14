---
ms.date: 09/13/2016
ms.topic: reference
title: 支援線上說明
description: 支援線上說明
ms.openlocfilehash: 0164b5e6c6c8d66a6ab2467a8adfb7efffe0fe17
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645422"
---
# <a name="supporting-online-help"></a><span data-ttu-id="1ab90-103">支援線上說明</span><span class="sxs-lookup"><span data-stu-id="1ab90-103">Supporting Online Help</span></span>

<span data-ttu-id="1ab90-104">從 PowerShell 3.0 開始，有兩種方式可以支援 `Get-Help` PowerShell 命令的線上功能。</span><span class="sxs-lookup"><span data-stu-id="1ab90-104">Beginning in PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for PowerShell commands.</span></span> <span data-ttu-id="1ab90-105">本主題說明如何針對不同的命令類型來執行這項功能。</span><span class="sxs-lookup"><span data-stu-id="1ab90-105">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="1ab90-106">關於線上說明</span><span class="sxs-lookup"><span data-stu-id="1ab90-106">About Online Help</span></span>

<span data-ttu-id="1ab90-107">線上說明一直是 PowerShell 的重要部分。</span><span class="sxs-lookup"><span data-stu-id="1ab90-107">Online help has always been a vital part of PowerShell.</span></span> <span data-ttu-id="1ab90-108">雖然指令程式會 `Get-Help` 在命令提示字元中顯示說明主題，但是許多使用者都偏好線上閱讀的體驗，包括色彩編碼、超連結，以及在社區內容和以 wiki 為基礎的檔中共用想法。</span><span class="sxs-lookup"><span data-stu-id="1ab90-108">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="1ab90-109">最重要的是，在有可更新的說明之前，線上說明提供最新版本的說明檔。</span><span class="sxs-lookup"><span data-stu-id="1ab90-109">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="1ab90-110">隨著 PowerShell 3.0 中的可更新說明，線上說明仍扮演重要的角色。</span><span class="sxs-lookup"><span data-stu-id="1ab90-110">With the advent of Updatable Help in PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="1ab90-111">除了有彈性的使用者體驗之外，線上說明也可提供協助，讓沒有或無法使用「可更新的說明」的使用者下載說明主題。</span><span class="sxs-lookup"><span data-stu-id="1ab90-111">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="1ab90-112">Get-Help-Online 的運作方式</span><span class="sxs-lookup"><span data-stu-id="1ab90-112">How Get-Help -Online Works</span></span>

<span data-ttu-id="1ab90-113">為了協助使用者找到命令的線上說明主題， `Get-Help` 命令具有線上參數，可在使用者的預設網際網路瀏覽器中開啟命令的線上版說明主題。</span><span class="sxs-lookup"><span data-stu-id="1ab90-113">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default internet browser.</span></span>

<span data-ttu-id="1ab90-114">例如，下列命令會開啟 Cmdlet 的線上說明主題 `Invoke-Command` 。</span><span class="sxs-lookup"><span data-stu-id="1ab90-114">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="1ab90-115">為了執行 `Get-Help -Online` ，此 `Get-Help` Cmdlet 會在下列位置中尋找線上版本說明主題的統一資源識別項 (URI) 。</span><span class="sxs-lookup"><span data-stu-id="1ab90-115">To implement `Get-Help -Online`, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="1ab90-116">命令之說明主題的 [ **相關連結** ] 區段中的第一個連結。</span><span class="sxs-lookup"><span data-stu-id="1ab90-116">The first link in the **Related Links** section of the help topic for the command.</span></span> <span data-ttu-id="1ab90-117">您必須在使用者的電腦上安裝說明主題。</span><span class="sxs-lookup"><span data-stu-id="1ab90-117">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="1ab90-118">這項功能是在 PowerShell 2.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="1ab90-118">This feature was introduced in PowerShell 2.0.</span></span>

- <span data-ttu-id="1ab90-119">任何命令的 **HelpUri** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1ab90-119">The **HelpUri** property of any command.</span></span> <span data-ttu-id="1ab90-120">即使使用者的電腦上未安裝命令的說明主題，也可以存取 **HelpUri** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1ab90-120">The **HelpUri** property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="1ab90-121">這項功能是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="1ab90-121">This feature was introduced in PowerShell 3.0.</span></span>

  <span data-ttu-id="1ab90-122">`Get-Help`取得 **HelpUri** 屬性值之前，請在 [**相關連結**] 區段的第一個專案中尋找 URI。</span><span class="sxs-lookup"><span data-stu-id="1ab90-122">`Get-Help` looks for a URI in the first entry in the **Related Links** section before getting the **HelpUri** property value.</span></span> <span data-ttu-id="1ab90-123">如果屬性值不正確或已變更，您可以在第一個相關連結中輸入不同的值來覆寫它。</span><span class="sxs-lookup"><span data-stu-id="1ab90-123">If the property value is incorrect or has changed, you can override it by entering a different value in the first related link.</span></span> <span data-ttu-id="1ab90-124">不過，第一個相關的連結只適用于在使用者電腦上安裝說明主題時。</span><span class="sxs-lookup"><span data-stu-id="1ab90-124">However, the first related link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="1ab90-125">將 URI 新增至命令說明主題的第一個相關連結</span><span class="sxs-lookup"><span data-stu-id="1ab90-125">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="1ab90-126">您可以針對 `Get-Help -Online` 命令的 XML 型說明主題之 [ **相關連結** ] 區段中的第一個專案新增有效的 URI，以支援任何命令。</span><span class="sxs-lookup"><span data-stu-id="1ab90-126">You can support `Get-Help -Online` for any command by adding a valid URI to the first entry in the **Related Links** section of the XML-based help topic for the command.</span></span> <span data-ttu-id="1ab90-127">此選項只適用于以 XML 為基礎的說明主題，而且只有在說明主題安裝在使用者的電腦上時才適用。</span><span class="sxs-lookup"><span data-stu-id="1ab90-127">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="1ab90-128">安裝說明主題並填入 URI 之後，這個值的優先順序會高於命令的 **HelpUri** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1ab90-128">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="1ab90-129">若要支援這項功能，URI 必須出現在元素中第一個元素底下的專案中 `maml:uri` `maml:relatedLinks/maml:navigationLink` `maml:relatedLinks` 。</span><span class="sxs-lookup"><span data-stu-id="1ab90-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="1ab90-130">下列 XML 會顯示 URI 的正確位置。</span><span class="sxs-lookup"><span data-stu-id="1ab90-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="1ab90-131">專案 `Online version:` 中的文字 `maml:linkText` 是最佳做法，但不是必要的。</span><span class="sxs-lookup"><span data-stu-id="1ab90-131">The `Online version:` text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

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

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="1ab90-132">將 HelpUri 屬性新增至命令</span><span class="sxs-lookup"><span data-stu-id="1ab90-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="1ab90-133">本節說明如何將 HelpUri 屬性新增至不同類型的命令。</span><span class="sxs-lookup"><span data-stu-id="1ab90-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="1ab90-134">將 HelpUri 屬性新增至 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1ab90-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="1ab90-135">針對以 c # 撰寫的 Cmdlet，請將 **HelpUri** 屬性新增至 **Cmdlet** 類別。</span><span class="sxs-lookup"><span data-stu-id="1ab90-135">For cmdlets written in C#, add a **HelpUri** attribute to the **Cmdlet** class.</span></span> <span data-ttu-id="1ab90-136">屬性的值必須是以或開頭的 URI `http` `https` 。</span><span class="sxs-lookup"><span data-stu-id="1ab90-136">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="1ab90-137">下列程式碼顯示 Cmdlet 類別的 **HelpUri** 屬性 `Get-History` 。</span><span class="sxs-lookup"><span data-stu-id="1ab90-137">The following code shows the **HelpUri** attribute of the `Get-History` cmdlet class.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="1ab90-138">將 HelpUri 屬性加入至 Advanced 函數</span><span class="sxs-lookup"><span data-stu-id="1ab90-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="1ab90-139">若為 advanced 函數，請將 **HelpUri** 屬性加入至 **CmdletBinding** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1ab90-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="1ab90-140">屬性的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。</span><span class="sxs-lookup"><span data-stu-id="1ab90-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="1ab90-141">下列程式碼顯示函數的 **HelpUri** 屬性。 `New-Calendar`</span><span class="sxs-lookup"><span data-stu-id="1ab90-141">The following code shows the **HelpUri** attribute of the `New-Calendar` function</span></span>

```powershell
function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="1ab90-142">將 HelpUri 屬性新增至 CIM 命令</span><span class="sxs-lookup"><span data-stu-id="1ab90-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="1ab90-143">若為 CIM 命令，請將 **HelpUri** 屬性加入至 CDXML 檔案中的 **CmdletMetadata** 元素。</span><span class="sxs-lookup"><span data-stu-id="1ab90-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span>
<span data-ttu-id="1ab90-144">屬性的值必須是以或開頭的 URI `http` `https` 。</span><span class="sxs-lookup"><span data-stu-id="1ab90-144">The value of the attribute must be a URI that begins with `http` or `https`.</span></span>

<span data-ttu-id="1ab90-145">下列程式碼顯示 CIM 命令的 HelpUri 屬性 `Start-Debug`</span><span class="sxs-lookup"><span data-stu-id="1ab90-145">The following code shows the HelpUri attribute of the `Start-Debug` CIM command</span></span>

```xml
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="1ab90-146">將 HelpUri 屬性加入至工作流程</span><span class="sxs-lookup"><span data-stu-id="1ab90-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="1ab90-147">針對以 PowerShell 語言撰寫的工作流程，請新增 **。** 將批註指示詞 .externalhelp 至工作流程程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ab90-147">For workflows that are written in the PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="1ab90-148">指示詞的值必須是以或開頭的 URI `http` `https` 。</span><span class="sxs-lookup"><span data-stu-id="1ab90-148">The value of the directive must be a URI that begins with `http` or `https`.</span></span>

> [!NOTE]
> <span data-ttu-id="1ab90-149">PowerShell 中以 XAML 為基礎的工作流程不支援 HelpUri 屬性。</span><span class="sxs-lookup"><span data-stu-id="1ab90-149">The HelpUri property is not supported for XAML-based workflows in PowerShell.</span></span>

<span data-ttu-id="1ab90-150">下列程式碼顯示。工作流程檔案中的 .Externalhelp 指示詞。</span><span class="sxs-lookup"><span data-stu-id="1ab90-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
