---
title: 如何將 Cmdlet 說明主題中的輸入的類型 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860804"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="6c7bd-102">如何新增輸入類型至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="6c7bd-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="6c7bd-103">本節說明如何將輸入區段新增至 Windows PowerShell® cmdlet 說明主題。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="6c7bd-104">輸入一節列出的.NET 類別的 cmdlet 會接受從管線中，輸入作為，傳值或屬性名稱的物件。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="6c7bd-105">沒有任何限制，您可以新增要在輸入區段的類別數目。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="6c7bd-106">輸入型別會括住\<命令： inputTypes > 節點，並以括住每個類別\<命令： inputType > 項目。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="6c7bd-107">結構描述包含兩個\<maml:description > 中每個項目\<命令： inputType > 項目。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="6c7bd-108">不過， `Get-Help` cmdlet 會顯示的內容\<命令： inputType > /\<maml:description >) 項目。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="6c7bd-109">在 Windows PowerShell 3.0 中，從`Get-Help`cmdlet 會顯示的內容\<maml:uri > 項目。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="6c7bd-110">這個項目可讓您將使用者導向至主題會說明.NET 類別。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="6c7bd-111">下列 XML 會說明\<maml:inputTypes > 節點。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="6c7bd-112">下列 XML 顯示的使用範例\<maml:inputTypes > 文件的輸入的類型的節點。</span><span class="sxs-lookup"><span data-stu-id="6c7bd-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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