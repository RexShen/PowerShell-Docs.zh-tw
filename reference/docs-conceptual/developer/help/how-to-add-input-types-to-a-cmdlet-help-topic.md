---
title: 如何新增輸入類型至 Cmdlet 說明主題
ms.date: 09/12/2016
ms.openlocfilehash: d41c49ff48cf361c2ba694d11576e84a9367eef5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893419"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="0b40b-102">如何新增輸入類型至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="0b40b-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="0b40b-103">本節說明如何將**輸入**區段新增至 PowerShell Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="0b40b-103">This section describes how to add an **INPUTS** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="0b40b-104">[**輸入**] 區段會以傳值或屬性名稱的形式，列出 Cmdlet 接受做為輸入的物件的 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="0b40b-104">The **INPUTS** section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="0b40b-105">您可以新增至**輸入**區段的類別數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="0b40b-105">There is no limit to the number of classes that you can add to an **INPUTS** section.</span></span> <span data-ttu-id="0b40b-106">輸入類型會括在節點中 `<command:inputTypes>` ，每個類別都包含在專案中 `<command:inputType>` 。</span><span class="sxs-lookup"><span data-stu-id="0b40b-106">The input types are enclosed in a `<command:inputTypes>` node, with each class enclosed in a `<command:inputType>` element.</span></span>

<span data-ttu-id="0b40b-107">架構 `<maml:description>` 在每個元素中都包含兩個元素 `<command:inputType>` 。</span><span class="sxs-lookup"><span data-stu-id="0b40b-107">The schema includes two `<maml:description>` elements in each `<command:inputType>` element.</span></span>
<span data-ttu-id="0b40b-108">不過，此 `Get-Help` Cmdlet 只會顯示元素的內容 `<command:inputType>/<maml:description>` 。</span><span class="sxs-lookup"><span data-stu-id="0b40b-108">However, the `Get-Help` cmdlet displays only the content of the `<command:inputType>/<maml:description>` element.</span></span>

<span data-ttu-id="0b40b-109">從 PowerShell 3.0 開始，此 `Get-Help` Cmdlet 會顯示元素的內容 `<maml:uri>` 。</span><span class="sxs-lookup"><span data-stu-id="0b40b-109">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="0b40b-110">此元素可讓您將使用者引導至描述 .NET 類別的主題。</span><span class="sxs-lookup"><span data-stu-id="0b40b-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="0b40b-111">下列 XML 會顯示 `<maml:inputTypes>` 節點。</span><span class="sxs-lookup"><span data-stu-id="0b40b-111">The following XML shows the `<maml:inputTypes>` node.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

<span data-ttu-id="0b40b-112">下列 XML 顯示使用 `<maml:inputTypes>` 節點記錄輸入類型的範例。</span><span class="sxs-lookup"><span data-stu-id="0b40b-112">The following XML shows an example of using the `<maml:inputTypes>` node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
