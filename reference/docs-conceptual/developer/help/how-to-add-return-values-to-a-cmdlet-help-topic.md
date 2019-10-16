---
title: 如何將傳回值新增至 Cmdlet 說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367797"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="6b2e1-102">如何新增傳回值至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="6b2e1-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="6b2e1-103">本節說明如何將 [輸出] 區段新增至 Windows PowerShell® Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="6b2e1-104">[輸出] 區段會列出 Cmdlet 傳回或沿著管線向下傳遞之物件的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="6b2e1-105">您可以新增至 [輸出] 區段的類別數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="6b2e1-106">Cmdlet 的傳回型別會括在 @no__t 0command： returnValues > 節點中，每個類別都包含在 \<command： returnValue > 元素中。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="6b2e1-107">如果 Cmdlet 不會產生任何輸出，請使用此區段來表示沒有輸出。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="6b2e1-108">例如，若要取代類別名稱，請寫入 "None" 並提供簡短說明。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="6b2e1-109">如果 Cmdlet 有條件地產生輸出，請使用此節點來說明條件並描述條件式輸出。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="6b2e1-110">架構在每個 \<command： returnValue > 元素中都包含兩個 @no__t 0maml： description > 元素。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="6b2e1-111">不過，`Get-Help` Cmdlet 只會顯示 \<command： returnValue >/\<maml： description > 元素的內容。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="6b2e1-112">從 Windows PowerShell 3.0 開始，`Get-Help` Cmdlet 會顯示 \<maml： uri > 元素的內容。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="6b2e1-113">此元素可讓您將使用者引導至描述 .NET 類別的主題。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="6b2e1-114">下列 XML 顯示 @no__t 0maml： returnValues > 節點。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-114">The following XML shows the \<maml:returnValues> node.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

<span data-ttu-id="6b2e1-115">下列 XML 顯示使用 \<maml： returnValues > 節點來記錄輸出類型的範例。</span><span class="sxs-lookup"><span data-stu-id="6b2e1-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



