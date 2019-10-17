---
title: 如何建立 Cmdlet 說明檔 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361197"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="d7eae-102">如何建立 Cmdlet 說明檔案</span><span class="sxs-lookup"><span data-stu-id="d7eae-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="d7eae-103">本節說明如何建立包含 Windows PowerShell Cmdlet 說明主題內容的有效 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d7eae-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="d7eae-104">本節討論如何命名說明檔、如何新增適當的 XML 標頭，以及如何新增將包含 Cmdlet 說明內容之不同區段的節點。</span><span class="sxs-lookup"><span data-stu-id="d7eae-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="d7eae-105">如需說明檔的完整視圖，請開啟位於 Windows PowerShell 安裝目錄中的其中一個 dll-Help 檔案。</span><span class="sxs-lookup"><span data-stu-id="d7eae-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="d7eae-106">例如，dll-Help 檔案包含數個 Windows PowerShell 指令程式的內容（content）。</span><span class="sxs-lookup"><span data-stu-id="d7eae-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="d7eae-107">如何建立 Cmdlet 說明檔</span><span class="sxs-lookup"><span data-stu-id="d7eae-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="d7eae-108">建立文字檔，並使用 UTF8 編碼來儲存它。</span><span class="sxs-lookup"><span data-stu-id="d7eae-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="d7eae-109">檔案名必須具有下列格式，Windows PowerShell 才能將其偵測為 Cmdlet 說明檔。</span><span class="sxs-lookup"><span data-stu-id="d7eae-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="d7eae-110">將下列 XML 標頭加入至文字檔。</span><span class="sxs-lookup"><span data-stu-id="d7eae-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="d7eae-111">請注意，檔案將會針對多代理程式模型語言（MAML）架構進行驗證。</span><span class="sxs-lookup"><span data-stu-id="d7eae-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="d7eae-112">目前，Windows PowerShell 不會提供任何工具來驗證檔案。</span><span class="sxs-lookup"><span data-stu-id="d7eae-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="d7eae-113">將命令節點新增至元件中每個 Cmdlet 的 Cmdlet 說明檔。</span><span class="sxs-lookup"><span data-stu-id="d7eae-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="d7eae-114">命令節點中的每個節點都與 Cmdlet 說明主題的不同區段相關。</span><span class="sxs-lookup"><span data-stu-id="d7eae-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="d7eae-115">下表列出每個節點的 XML 元素，後面接著每個節點的說明。</span><span class="sxs-lookup"><span data-stu-id="d7eae-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="d7eae-116">節點</span><span class="sxs-lookup"><span data-stu-id="d7eae-116">Node</span></span>|<span data-ttu-id="d7eae-117">描述</span><span class="sxs-lookup"><span data-stu-id="d7eae-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="d7eae-118">新增 Cmdlet 說明主題之名稱和概要區段的內容。</span><span class="sxs-lookup"><span data-stu-id="d7eae-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="d7eae-119">如需詳細資訊，請參閱[如何新增 Cmdlet 名稱和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eae-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="d7eae-120">新增 Cmdlet 說明主題之 [描述] 部分的內容。</span><span class="sxs-lookup"><span data-stu-id="d7eae-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="d7eae-121">如需詳細資訊，請參閱[如何將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eae-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="d7eae-122">新增 Cmdlet 說明主題的語法章節內容。</span><span class="sxs-lookup"><span data-stu-id="d7eae-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="d7eae-123">如需詳細資訊，請參閱[如何將語法新增至 Cmdlet 說明主題](./how-to-add-syntax-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eae-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="d7eae-124">新增 Cmdlet 說明主題之 PARAMETERS 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="d7eae-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="d7eae-125">如需詳細資訊，請參閱[如何將參數新增至 Cmdlet 說明主題](./how-to-add-parameter-information.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eae-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="d7eae-126">新增 Cmdlet 說明主題之輸入區段的內容。</span><span class="sxs-lookup"><span data-stu-id="d7eae-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="d7eae-127">如需詳細資訊，請參閱[如何將輸入類型新增至 Cmdlet 說明主題](./how-to-add-input-types-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eae-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="d7eae-128">新增 Cmdlet 說明主題的 [輸出] 區段內容。</span><span class="sxs-lookup"><span data-stu-id="d7eae-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="d7eae-129">如需詳細資訊，請參閱[如何將傳回值新增至 Cmdlet 說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eae-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="d7eae-130">將內容新增至 Cmdlet 說明主題的 NOTES 區段。</span><span class="sxs-lookup"><span data-stu-id="d7eae-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="d7eae-131">如需詳細資訊，請參閱[如何將附注新增至 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eae-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="d7eae-132">新增 Cmdlet 說明主題之範例區段的內容。</span><span class="sxs-lookup"><span data-stu-id="d7eae-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="d7eae-133">如需詳細資訊，請參閱[如何將範例新增至 Cmdlet 說明主題](./how-to-add-examples-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eae-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="d7eae-134">新增 Cmdlet 說明主題之 [相關連結] 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="d7eae-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="d7eae-135">如需詳細資訊，請參閱[如何將相關連結新增至 Cmdlet 說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="d7eae-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="d7eae-136">範例</span><span class="sxs-lookup"><span data-stu-id="d7eae-136">Example</span></span>

 <span data-ttu-id="d7eae-137">以下是命令節點的範例，其中包含 Cmdlet 說明主題各區段的節點。</span><span class="sxs-lookup"><span data-stu-id="d7eae-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d7eae-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7eae-138">See Also</span></span>

 [<span data-ttu-id="d7eae-139">如何新增 Cmdlet 名稱和摘要</span><span class="sxs-lookup"><span data-stu-id="d7eae-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d7eae-140">如何將詳細描述新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="d7eae-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="d7eae-141">如何將語法新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="d7eae-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d7eae-142">如何將參數新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="d7eae-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="d7eae-143">如何將輸入類型新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="d7eae-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d7eae-144">如何將傳回值新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="d7eae-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d7eae-145">如何將附注新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="d7eae-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d7eae-146">如何將範例新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="d7eae-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d7eae-147">如何將相關連結新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="d7eae-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="d7eae-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d7eae-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)