---
title: 如何將輸入類型新增至 Cmdlet 說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361237"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="13c03-102">如何新增輸入類型至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="13c03-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="13c03-103">本節說明如何將輸入區段新增至 Windows PowerShell® Cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="13c03-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="13c03-104">[輸入] 區段會以傳值或屬性名稱的形式，列出 Cmdlet 接受做為輸入的物件的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="13c03-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="13c03-105">您可以新增至輸入區段的類別數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="13c03-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="13c03-106">輸入類型會括在 @no__t 0command： inputTypes > 節點中，每個類別都包含在 @no__t 1command： inputType > 元素中。</span><span class="sxs-lookup"><span data-stu-id="13c03-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="13c03-107">此架構包含兩個 @no__t 0maml： description > 元素中的每個 \<command： inputType > 元素。</span><span class="sxs-lookup"><span data-stu-id="13c03-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="13c03-108">不過，`Get-Help` Cmdlet 只會顯示 \<command： inputType >/\<maml： description >）元素的內容。</span><span class="sxs-lookup"><span data-stu-id="13c03-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="13c03-109">從 Windows PowerShell 3.0 開始，`Get-Help` Cmdlet 會顯示 \<maml： uri > 元素的內容。</span><span class="sxs-lookup"><span data-stu-id="13c03-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="13c03-110">此元素可讓您將使用者引導至描述 .NET 類別的主題。</span><span class="sxs-lookup"><span data-stu-id="13c03-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="13c03-111">下列 XML 顯示 @no__t 0maml： inputTypes > 節點。</span><span class="sxs-lookup"><span data-stu-id="13c03-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="13c03-112">下列 XML 顯示使用 \<maml： inputTypes > 節點來記錄輸入類型的範例。</span><span class="sxs-lookup"><span data-stu-id="13c03-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```