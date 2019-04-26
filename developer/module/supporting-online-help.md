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
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082136"
---
# <a name="supporting-online-help"></a><span data-ttu-id="9490b-102">支援線上說明</span><span class="sxs-lookup"><span data-stu-id="9490b-102">Supporting Online Help</span></span>

<span data-ttu-id="9490b-103">從 Windows PowerShell 3.0 開始，有兩種方式，以支援`Get-Help`Windows PowerShell 命令的線上功能。</span><span class="sxs-lookup"><span data-stu-id="9490b-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="9490b-104">本主題說明如何實作此功能，針對不同的命令類型。</span><span class="sxs-lookup"><span data-stu-id="9490b-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="9490b-105">關於線上說明</span><span class="sxs-lookup"><span data-stu-id="9490b-105">About Online Help</span></span>

<span data-ttu-id="9490b-106">線上說明一直是 Windows PowerShell 中不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="9490b-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="9490b-107">雖然`Get-Help`cmdlet 會顯示 [說明] 主題，在命令提示字元中，許多使用者偏好的線上閱讀，包含色彩編碼、 超連結及社群內容和 wiki 文件中的共用想法的體驗。</span><span class="sxs-lookup"><span data-stu-id="9490b-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="9490b-108">最重要的是，可更新的說明問世之前, 的線上說明所提供說明檔案的最新的版本。</span><span class="sxs-lookup"><span data-stu-id="9490b-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="9490b-109">隨著可更新的說明，在 Windows PowerShell 3.0 中，線上說明，仍扮演重要角色。</span><span class="sxs-lookup"><span data-stu-id="9490b-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="9490b-110">除了彈性的使用者體驗，線上說明會提供給使用者，對於沒有或無法使用可更新的說明下載說明主題的說明。</span><span class="sxs-lookup"><span data-stu-id="9490b-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="9490b-111">如何取得說明-線上的運作方式</span><span class="sxs-lookup"><span data-stu-id="9490b-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="9490b-112">若要協助使用者尋找線上 [說明] 主題的命令，`Get-Help`命令有線上的參數，在使用者的預設網際網路瀏覽器中開啟命令的說明主題的線上版本。</span><span class="sxs-lookup"><span data-stu-id="9490b-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="9490b-113">例如，下列命令會開啟線上說明主題的`Invoke-Command`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9490b-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="9490b-114">若要實作`Get-Help`-線上`Get-Help`cmdlet 看起來的統一資源識別元 (URI) 的線上版本說明主題，在下列位置。</span><span class="sxs-lookup"><span data-stu-id="9490b-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="9490b-115">命令的說明主題的相關連結 區段中的第一個連結。</span><span class="sxs-lookup"><span data-stu-id="9490b-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="9490b-116">在使用者電腦上必須安裝 [說明] 主題。</span><span class="sxs-lookup"><span data-stu-id="9490b-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="9490b-117">在 Windows PowerShell 2.0 引進這項功能。</span><span class="sxs-lookup"><span data-stu-id="9490b-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="9490b-118">任何命令的 HelpUri 屬性。</span><span class="sxs-lookup"><span data-stu-id="9490b-118">The HelpUri property of any command.</span></span> <span data-ttu-id="9490b-119">即使命令的 [說明] 主題未安裝在使用者電腦上存取的 HelpUri 屬性。</span><span class="sxs-lookup"><span data-stu-id="9490b-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="9490b-120">這項功能是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="9490b-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="9490b-121">`Get-Help` 取得 HelpUri 屬性值之前尋找相關連結 區段中的第一個項目中的 URI。</span><span class="sxs-lookup"><span data-stu-id="9490b-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="9490b-122">如果屬性值不正確，或已變更，您可以在第一個相關連結中輸入不同的值來覆寫它。</span><span class="sxs-lookup"><span data-stu-id="9490b-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="9490b-123">不過，第一個相關連結僅適用於使用者的電腦上已安裝的說明主題。</span><span class="sxs-lookup"><span data-stu-id="9490b-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="9490b-124">將 URI 新增至命令的說明主題的第一個相關連結</span><span class="sxs-lookup"><span data-stu-id="9490b-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="9490b-125">您可以在支援`Get-Help`-線上的任何命令，以 XML 為基礎的說明主題之命令的相關連結 區段中的第一個項目中加入有效的 URI。</span><span class="sxs-lookup"><span data-stu-id="9490b-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="9490b-126">此選項僅適用於以 XML 為基礎的說明主題，且只有在使用者的電腦上已安裝的說明主題時，才會運作。</span><span class="sxs-lookup"><span data-stu-id="9490b-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="9490b-127">安裝 [說明] 主題，並會填入 URI，這個值會優先**HelpUri**命令的屬性。</span><span class="sxs-lookup"><span data-stu-id="9490b-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="9490b-128">以 XML 為基礎命令的說明主題的相關資訊，請參閱[Writing XML-Based 命令的說明主題](../help/writing-xml-based-help-topics-for-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="9490b-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="9490b-129">若要支援這項功能，URI 必須出現在`maml:uri`置於第一個項目`maml:relatedLinks/maml:navigationLink`中的項目`maml:relatedLinks`項目。</span><span class="sxs-lookup"><span data-stu-id="9490b-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="9490b-130">下列 XML 顯示正確的 URI 位置。</span><span class="sxs-lookup"><span data-stu-id="9490b-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="9490b-131">「 線上版本:"中的文字`maml:linkText`項目是最佳作法，但並非必要。</span><span class="sxs-lookup"><span data-stu-id="9490b-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="9490b-132">將 HelpUri 屬性加入至命令</span><span class="sxs-lookup"><span data-stu-id="9490b-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="9490b-133">本節說明如何將 HelpUri 屬性加入至不同類型的命令。</span><span class="sxs-lookup"><span data-stu-id="9490b-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="9490b-134">將 HelpUri 屬性加入至指令程式</span><span class="sxs-lookup"><span data-stu-id="9490b-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="9490b-135">以撰寫的 cmdlet C#，新增**HelpUri**屬性設定為在 Cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="9490b-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="9490b-136">屬性的值必須是以"http"或"https"開頭的 URI。</span><span class="sxs-lookup"><span data-stu-id="9490b-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="9490b-137">下列程式碼顯示的 HelpUri 屬性`Get-History`cmdlet 類別。</span><span class="sxs-lookup"><span data-stu-id="9490b-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="9490b-138">新增進階的函式的 HelpUri 屬性</span><span class="sxs-lookup"><span data-stu-id="9490b-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="9490b-139">進階的函式中，新增**HelpUri**屬性設**CmdletBinding**屬性。</span><span class="sxs-lookup"><span data-stu-id="9490b-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="9490b-140">屬性的值必須是以"http"或"https"開頭的 URI。</span><span class="sxs-lookup"><span data-stu-id="9490b-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="9490b-141">下列程式碼會顯示新行事曆函式的 HelpUri 屬性</span><span class="sxs-lookup"><span data-stu-id="9490b-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="9490b-142">將 HelpUri 屬性加入至 CIM 命令</span><span class="sxs-lookup"><span data-stu-id="9490b-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="9490b-143">如需 CIM 命令，新增**HelpUri**屬性設定為**CmdletMetadata** CDXML 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="9490b-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="9490b-144">屬性的值必須是以"http"或"https"開頭的 URI。</span><span class="sxs-lookup"><span data-stu-id="9490b-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="9490b-145">下列程式碼會顯示 開始偵錯 CIM 命令的 HelpUri 屬性</span><span class="sxs-lookup"><span data-stu-id="9490b-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="9490b-146">加入至工作流程的 HelpUri 屬性</span><span class="sxs-lookup"><span data-stu-id="9490b-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="9490b-147">以 Windows PowerShell 語言撰寫的工作流程，新增 **。ExternalHelp**註解指示詞，以便在工作流程程式碼。</span><span class="sxs-lookup"><span data-stu-id="9490b-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="9490b-148">指示詞的值必須是以"http"或"https"開頭的 URI。</span><span class="sxs-lookup"><span data-stu-id="9490b-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="9490b-149">在 Windows PowerShell 中的 XAML 型工作流程不支援的 HelpUri 屬性。</span><span class="sxs-lookup"><span data-stu-id="9490b-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="9490b-150">下列程式碼所示。在工作流程檔案 ExternalHelp 指示詞。</span><span class="sxs-lookup"><span data-stu-id="9490b-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```