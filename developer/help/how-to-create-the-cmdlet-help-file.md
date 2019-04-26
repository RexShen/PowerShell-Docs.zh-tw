---
title: 如何建立 Cmdlet 說明檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083241"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="3b6f6-102">如何建立 Cmdlet 說明檔案</span><span class="sxs-lookup"><span data-stu-id="3b6f6-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="3b6f6-103">本節說明如何建立有效的 XML 檔案，包含 Windows PowerShell cmdlet 說明主題的內容。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="3b6f6-104">本節討論如何命名的說明檔、 如何新增適當的 XML 標頭，以及如何加入將包含 cmdlet 的說明內容的各區段的節點。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="3b6f6-105">說明檔案，開啟其中一個 dll Help.xml 檔案位於 Windows PowerShell 安裝目錄的完整檢視。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="3b6f6-106">比方說，Microsoft.PowerShell.Commands.Management.dll Help.xml 檔案會包含內容的數個 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="3b6f6-107">如何建立 Cmdlet 說明檔</span><span class="sxs-lookup"><span data-stu-id="3b6f6-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="3b6f6-108">建立文字檔案，並將它使用 UTF8 編碼方式儲存。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="3b6f6-109">檔案名稱必須以下列格式，使 Windows PowerShell 可以偵測到它的 cmdlet 說明檔。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="3b6f6-110">文字檔案中加入下列的 XML 標頭。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="3b6f6-111">請注意，將會針對多重代理程式模型化語言 （maml） 進行結構描述驗證的檔案。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="3b6f6-112">目前，Windows PowerShell 不提供任何工具來驗證檔案。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="3b6f6-113">命令將節點新增至組件中的每個 cmdlet 的 cmdlet 說明檔。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="3b6f6-114">命令節點內的每個節點與相關的 cmdlet 說明主題各區段。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="3b6f6-115">下表列出每個節點，後面接著描述每個節點的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="3b6f6-116">節點</span><span class="sxs-lookup"><span data-stu-id="3b6f6-116">Node</span></span>|<span data-ttu-id="3b6f6-117">描述</span><span class="sxs-lookup"><span data-stu-id="3b6f6-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="3b6f6-118">新增 cmdlet 說明主題的名稱和概要區段的內容。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="3b6f6-119">如需詳細資訊，請參閱 <<c0> [ 如何將 Cmdlet 名稱和概要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="3b6f6-120">新增 [描述] 部分的 cmdlet 說明主題的內容。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="3b6f6-121">如需詳細資訊，請參閱 < [how to Add Cmdlet 說明主題的詳細說明如何](./how-to-add-a-cmdlet-description.md)。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="3b6f6-122">新增 cmdlet 說明主題語法 」 一節的內容。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="3b6f6-123">如需詳細資訊，請參閱 <<c0> [ 如何新增語法 Cmdlet 說明主題](./how-to-add-syntax-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="3b6f6-124">將參數區段的 cmdlet 說明主題的內容。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3b6f6-125">如需詳細資訊，請參閱 <<c0> [ 如何將參數加入 Cmdlet 說明主題](./how-to-add-parameter-information.md)。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="3b6f6-126">將輸入區段的 cmdlet 說明主題的內容。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3b6f6-127">如需詳細資訊，請參閱 <<c0> [ 新增至 Cmdlet 說明主題的輸入類型如何](./how-to-add-input-types-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="3b6f6-128">新增 cmdlet 說明主題的輸出區段的內容。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3b6f6-129">如需詳細資訊，請參閱 <<c0> [ 如何將傳回值 Cmdlet 說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="3b6f6-130">將內容加入提示 > 一節中的 cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="3b6f6-131">如需詳細資訊，請參閱 <<c0> [ 如何新增備忘稿的 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="3b6f6-132">新增 cmdlet 說明主題的範例 > 一節的內容。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="3b6f6-133">如需詳細資訊，請參閱 <<c0> [ 範例新增至 Cmdlet 說明主題的如何](./how-to-add-examples-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="3b6f6-134">新增 cmdlet 說明主題的相關連結 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="3b6f6-135">如需詳細資訊，請參閱 <<c0> [ 如何將相關連結 Cmdlet 說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="3b6f6-136">範例</span><span class="sxs-lookup"><span data-stu-id="3b6f6-136">Example</span></span>

 <span data-ttu-id="3b6f6-137">以下是命令節點 （包括 cmdlet 說明主題的各個區段的節點） 的範例。</span><span class="sxs-lookup"><span data-stu-id="3b6f6-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="3b6f6-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b6f6-138">See Also</span></span>

 [<span data-ttu-id="3b6f6-139">如何將 Cmdlet 名稱和概要</span><span class="sxs-lookup"><span data-stu-id="3b6f6-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3b6f6-140">如何將詳細的說明新增至 Cmdlet 的說明主題</span><span class="sxs-lookup"><span data-stu-id="3b6f6-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="3b6f6-141">如何將 Cmdlet 說明主題中的語法</span><span class="sxs-lookup"><span data-stu-id="3b6f6-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3b6f6-142">如何將參數新增至 Cmdlet 的說明主題</span><span class="sxs-lookup"><span data-stu-id="3b6f6-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="3b6f6-143">如何將 Cmdlet 說明主題中的輸入的類型</span><span class="sxs-lookup"><span data-stu-id="3b6f6-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3b6f6-144">如何將傳回的值新增至 Cmdlet 的說明主題</span><span class="sxs-lookup"><span data-stu-id="3b6f6-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3b6f6-145">如何新增備忘稿的 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="3b6f6-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3b6f6-146">如何新增 Cmdlet 說明主題的範例</span><span class="sxs-lookup"><span data-stu-id="3b6f6-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3b6f6-147">如何將相關的連結新增至 Cmdlet 的說明主題</span><span class="sxs-lookup"><span data-stu-id="3b6f6-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="3b6f6-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3b6f6-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)