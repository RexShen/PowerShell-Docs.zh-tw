---
ms.date: 09/12/2016
ms.topic: reference
title: 如何新增輸入類型至 Cmdlet 說明主題
description: 如何新增輸入類型至 Cmdlet 說明主題
ms.openlocfilehash: f2ad87c54230bcdd7e0ea708e9a1869daef7495f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "94391097"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="4c70b-103">如何新增輸入類型至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="4c70b-103">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="4c70b-104">本節說明如何將 **輸入** 區段新增至 PowerShell Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="4c70b-104">This section describes how to add an **INPUTS** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="4c70b-105">[ **輸入** ] 區段會列出 Cmdlet 以傳值方式或屬性名稱的形式，從管線接受的物件 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="4c70b-105">The **INPUTS** section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="4c70b-106">您可以新增至 **輸入** 區段的類別數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="4c70b-106">There is no limit to the number of classes that you can add to an **INPUTS** section.</span></span> <span data-ttu-id="4c70b-107">輸入類型會包含在節點中 `<command:inputTypes>` ，每個類別都包含在 `<command:inputType>` 元素中。</span><span class="sxs-lookup"><span data-stu-id="4c70b-107">The input types are enclosed in a `<command:inputTypes>` node, with each class enclosed in a `<command:inputType>` element.</span></span>

<span data-ttu-id="4c70b-108">架構會 `<maml:description>` 在每個專案中包含兩個元素 `<command:inputType>` 。</span><span class="sxs-lookup"><span data-stu-id="4c70b-108">The schema includes two `<maml:description>` elements in each `<command:inputType>` element.</span></span>
<span data-ttu-id="4c70b-109">不過，此 `Get-Help` Cmdlet 只會顯示元素的內容 `<command:inputType>/<maml:description>` 。</span><span class="sxs-lookup"><span data-stu-id="4c70b-109">However, the `Get-Help` cmdlet displays only the content of the `<command:inputType>/<maml:description>` element.</span></span>

<span data-ttu-id="4c70b-110">從 PowerShell 3.0 開始，此 `Get-Help` Cmdlet 會顯示元素的內容 `<maml:uri>` 。</span><span class="sxs-lookup"><span data-stu-id="4c70b-110">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="4c70b-111">此元素可讓您將使用者導向描述 .NET 類別的主題。</span><span class="sxs-lookup"><span data-stu-id="4c70b-111">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="4c70b-112">下列 XML 會顯示 `<maml:inputTypes>` 節點。</span><span class="sxs-lookup"><span data-stu-id="4c70b-112">The following XML shows the `<maml:inputTypes>` node.</span></span>

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

<span data-ttu-id="4c70b-113">下列 XML 顯示使用 `<maml:inputTypes>` 節點來記錄輸入類型的範例。</span><span class="sxs-lookup"><span data-stu-id="4c70b-113">The following XML shows an example of using the `<maml:inputTypes>` node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name>System.DateTime</maml:name>
      <maml:uri>https://docs.microsoft.com/dotnet/api/system.datetime</maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
