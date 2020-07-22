---
title: 如何新增傳回值至 Cmdlet 說明主題
ms.date: 09/12/2016
ms.openlocfilehash: c164556cd06b332d04857987360c98f740a150b5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893351"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="8399c-102">如何新增傳回值至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="8399c-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="8399c-103">本節說明如何將輸出區段新增至 PowerShell Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="8399c-103">This section describes how to add an OUTPUTS section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="8399c-104">[**輸出**] 區段會列出 Cmdlet 傳回或沿著管線向下傳遞之物件的 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="8399c-104">The **OUTPUTS** section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="8399c-105">您可以新增至 [**輸出**] 區段的類別數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="8399c-105">There is no limit to the number of classes that you can add to the **OUTPUTS** section.</span></span> <span data-ttu-id="8399c-106">Cmdlet 的傳回型別會括在節點中 `<command:returnValues>` ，每個類別都包含在專案中 `<command:returnValue>` 。</span><span class="sxs-lookup"><span data-stu-id="8399c-106">The return types of a cmdlet are enclosed in a `<command:returnValues>` node, with each class enclosed in a `<command:returnValue>` element.</span></span>

<span data-ttu-id="8399c-107">如果 Cmdlet 不會產生任何輸出，請使用此區段來表示沒有輸出。</span><span class="sxs-lookup"><span data-stu-id="8399c-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="8399c-108">例如，若要取代類別名稱，請撰寫**None**並提供簡短說明。</span><span class="sxs-lookup"><span data-stu-id="8399c-108">For example, in place of the class name, write **None** and provide a brief explanation.</span></span> <span data-ttu-id="8399c-109">如果 Cmdlet 有條件地產生輸出，請使用此節點來說明條件並描述條件式輸出。</span><span class="sxs-lookup"><span data-stu-id="8399c-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="8399c-110">架構 `<maml:description>` 在每個元素中都包含兩個元素 `<command:returnValue>` 。</span><span class="sxs-lookup"><span data-stu-id="8399c-110">The schema includes two `<maml:description>` elements in each `<command:returnValue>` element.</span></span>
<span data-ttu-id="8399c-111">不過，此 `Get-Help` Cmdlet 只會顯示元素的內容 `<command:returnValue>/<maml:description>` 。</span><span class="sxs-lookup"><span data-stu-id="8399c-111">However, the `Get-Help` cmdlet displays only the content of the `<command:returnValue>/<maml:description>` element.</span></span>

<span data-ttu-id="8399c-112">從 PowerShell 3.0 開始，此 `Get-Help` Cmdlet 會顯示元素的內容 `<maml:uri>` 。</span><span class="sxs-lookup"><span data-stu-id="8399c-112">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="8399c-113">此元素可讓您將使用者引導至描述 .NET 類別的主題。</span><span class="sxs-lookup"><span data-stu-id="8399c-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="8399c-114">下列 XML 會顯示 `<maml:returnValues>` 節點。</span><span class="sxs-lookup"><span data-stu-id="8399c-114">The following XML shows the `<maml:returnValues>` node.</span></span>

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

<span data-ttu-id="8399c-115">下列 XML 顯示使用 `<maml:returnValues>` 節點來記錄輸出類型的範例。</span><span class="sxs-lookup"><span data-stu-id="8399c-115">The following XML shows an example of using the `<maml:returnValues>` node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
