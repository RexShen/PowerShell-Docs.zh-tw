---
ms.date: 09/13/2016
ms.topic: reference
title: 如何建立 Cmdlet 說明檔案
description: 如何建立 Cmdlet 說明檔案
ms.openlocfilehash: 40259c8f9496b10380805a78f3711aed6f1bf2e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659096"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="7c5cd-103">如何建立 Cmdlet 說明檔案</span><span class="sxs-lookup"><span data-stu-id="7c5cd-103">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="7c5cd-104">本節說明如何建立包含 Windows PowerShell Cmdlet 說明主題內容的有效 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-104">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="7c5cd-105">本節討論如何命名說明檔、如何新增適當的 XML 標頭，以及如何加入將包含 Cmdlet 說明內容不同區段的節點。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-105">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="7c5cd-106">如需說明檔的完整資訊，請開啟 `dll-Help.xml` 位於 Windows PowerShell 安裝目錄中的其中一個檔案。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="7c5cd-107">例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="7c5cd-108">如何建立 Cmdlet 說明檔</span><span class="sxs-lookup"><span data-stu-id="7c5cd-108">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="7c5cd-109">建立文字檔，並使用 UTF8 編碼來儲存它。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-109">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="7c5cd-110">檔案名必須具有下列格式，才能讓 Windows PowerShell 偵測為 Cmdlet 說明檔。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-110">The filename must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. <span data-ttu-id="7c5cd-111">將下列 XML 標頭新增至文字檔。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-111">Add the following XML headers to the text file.</span></span> <span data-ttu-id="7c5cd-112">請注意，檔案會根據 Microsoft 協助標記語言進行驗證， (MAML) 架構。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-112">Be aware that the file will be validated against the Microsoft Assistance Markup Language (MAML) schema.</span></span> <span data-ttu-id="7c5cd-113">PowerShell 目前未提供任何工具來驗證檔案。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-113">Currently, PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. <span data-ttu-id="7c5cd-114">針對元件中的每個 Cmdlet，將 **命令** 節點新增至 Cmdlet 說明檔。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-114">Add a **Command** node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="7c5cd-115">**命令** 節點內的每個節點都與 Cmdlet 說明主題的不同區段有關。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-115">Each node within the **Command** node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="7c5cd-116">下表列出每個節點的 XML 元素，後面接著每個節點的描述。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-116">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |           <span data-ttu-id="7c5cd-117">節點</span><span class="sxs-lookup"><span data-stu-id="7c5cd-117">Node</span></span>           |                                                                                                     <span data-ttu-id="7c5cd-118">說明</span><span class="sxs-lookup"><span data-stu-id="7c5cd-118">Description</span></span>                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | <span data-ttu-id="7c5cd-119">新增 Cmdlet 說明主題之 [名稱] 和 [摘要] 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-119">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="7c5cd-120">如需詳細資訊，請參閱 [如何新增 Cmdlet 名稱和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-120">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span> |
   | `<maml:description>`     | <span data-ttu-id="7c5cd-121">新增 Cmdlet 說明主題之 [描述] 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-121">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="7c5cd-122">如需詳細資訊，請參閱 [如何將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-122">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>                    |
   | `<command:syntax>`       | <span data-ttu-id="7c5cd-123">新增 Cmdlet 說明主題之語法區段的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-123">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="7c5cd-124">如需詳細資訊，請參閱 [如何將語法新增至 Cmdlet 說明主題](./how-to-add-syntax-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-124">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>                                  |
   | `<command:parameters>`   | <span data-ttu-id="7c5cd-125">新增 Cmdlet 說明主題之 PARAMETERS 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-125">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="7c5cd-126">如需詳細資訊，請參閱 [如何將參數新增至 Cmdlet 說明主題](./how-to-add-parameter-information.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-126">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>                                  |
   | `<command:inputTypes>`   | <span data-ttu-id="7c5cd-127">新增 Cmdlet 說明主題之 [輸入] 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-127">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="7c5cd-128">如需詳細資訊，請參閱 [如何將輸入類型新增至 Cmdlet 說明主題](./how-to-add-input-types-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-128">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>                        |
   | `<command:returnValues>` | <span data-ttu-id="7c5cd-129">新增 Cmdlet 說明主題之 [輸出] 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-129">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="7c5cd-130">如需詳細資訊，請參閱 [如何將傳回值新增至 Cmdlet 說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-130">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>                   |
   | `<maml:alertset>`        | <span data-ttu-id="7c5cd-131">新增 Cmdlet 說明主題之 NOTES 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-131">Adds content for the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="7c5cd-132">如需詳細資訊，請參閱 [如何將附注新增至 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-132">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>                                      |
   | `<command:examples>`     | <span data-ttu-id="7c5cd-133">新增 Cmdlet 說明主題之 [範例] 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-133">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="7c5cd-134">如需詳細資訊，請參閱 [如何將範例新增至 Cmdlet 說明主題](./how-to-add-examples-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-134">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>                            |
   | `<maml:relatedLinks>`    | <span data-ttu-id="7c5cd-135">新增 Cmdlet 說明主題之 [相關連結] 區段的內容。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-135">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="7c5cd-136">如需詳細資訊，請參閱 [如何將相關連結新增至 Cmdlet 說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-136">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>             |

## <a name="example"></a><span data-ttu-id="7c5cd-137">範例</span><span class="sxs-lookup"><span data-stu-id="7c5cd-137">Example</span></span>

 <span data-ttu-id="7c5cd-138">以下是 **命令** 節點的範例，其中包含 Cmdlet 說明主題各區段的節點。</span><span class="sxs-lookup"><span data-stu-id="7c5cd-138">Here is an example of a **Command** node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7c5cd-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c5cd-139">See Also</span></span>

 [<span data-ttu-id="7c5cd-140">如何新增 Cmdlet 名稱和摘要</span><span class="sxs-lookup"><span data-stu-id="7c5cd-140">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="7c5cd-141">如何將詳細描述新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7c5cd-141">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="7c5cd-142">如何新增語法至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7c5cd-142">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="7c5cd-143">如何將參數新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7c5cd-143">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="7c5cd-144">如何新增輸入類型至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7c5cd-144">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="7c5cd-145">如何新增傳回值至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7c5cd-145">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="7c5cd-146">如何將附注新增至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7c5cd-146">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="7c5cd-147">如何新增範例至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7c5cd-147">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="7c5cd-148">如何新增相關連結至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7c5cd-148">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="7c5cd-149">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7c5cd-149">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
