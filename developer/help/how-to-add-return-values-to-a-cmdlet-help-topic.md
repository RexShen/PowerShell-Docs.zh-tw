---
title: 如何將傳回值的 Cmdlet 說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859434"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="7fce7-102">如何新增傳回值至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7fce7-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7fce7-103">本節說明如何將 OUTPUTS 區段新增至 Windows PowerShell® cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="7fce7-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="7fce7-104">OUTPUTS 區段列出的.NET 類別的指令程式傳回或傳遞到管線的物件。</span><span class="sxs-lookup"><span data-stu-id="7fce7-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="7fce7-105">沒有任何限制，您可以將它新增至 [輸出] 區段的類別數目。</span><span class="sxs-lookup"><span data-stu-id="7fce7-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="7fce7-106">Cmdlet 的傳回型別會括住\<命令： returnValues > 節點，並以括住每個類別\<命令： returnValue > 項目。</span><span class="sxs-lookup"><span data-stu-id="7fce7-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="7fce7-107">如果 cmdlet 不會產生任何輸出，請使用本節來表示沒有任何輸出。</span><span class="sxs-lookup"><span data-stu-id="7fce7-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="7fce7-108">比方說，來取代類別名稱中，撰寫 「 無 」，並提供簡短說明。</span><span class="sxs-lookup"><span data-stu-id="7fce7-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="7fce7-109">如果 cmdlet 有條件地產生輸出，請使用此節點來說明條件及描述的條件式的輸出。</span><span class="sxs-lookup"><span data-stu-id="7fce7-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="7fce7-110">結構描述包含兩個\<maml:description > 中每個項目\<命令： returnValue > 項目。</span><span class="sxs-lookup"><span data-stu-id="7fce7-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="7fce7-111">不過， `Get-Help` cmdlet 會顯示的內容\<命令： returnValue > /\<maml:description > 項目。</span><span class="sxs-lookup"><span data-stu-id="7fce7-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="7fce7-112">在 Windows PowerShell 3.0 中，從`Get-Help`cmdlet 會顯示的內容\<maml:uri > 項目。</span><span class="sxs-lookup"><span data-stu-id="7fce7-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="7fce7-113">這個項目可讓您將使用者導向至主題會說明.NET 類別。</span><span class="sxs-lookup"><span data-stu-id="7fce7-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="7fce7-114">下列 XML 會說明\<maml:returnValues > 節點。</span><span class="sxs-lookup"><span data-stu-id="7fce7-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="7fce7-115">下列 XML 顯示的使用範例\<maml:returnValues > 文件的輸出類型的節點。</span><span class="sxs-lookup"><span data-stu-id="7fce7-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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



