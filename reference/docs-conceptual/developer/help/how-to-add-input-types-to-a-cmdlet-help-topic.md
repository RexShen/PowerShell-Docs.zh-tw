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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361237"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>如何新增輸入類型至 Cmdlet 說明主題

本節說明如何將輸入區段新增至 Windows PowerShell® Cmdlet 說明主題。 [輸入] 區段會以傳值或屬性名稱的形式，列出 Cmdlet 接受做為輸入的物件的 .NET 類別。

您可以新增至輸入區段的類別數目沒有限制。 輸入類型會括在 \<命令中： inputTypes > 節點，其中每個類別都包含在 \<命令中： inputType > 元素。

此架構包含兩個 \<maml：描述 > 每個 \<命令中的元素： inputType > 專案。 不過，`Get-Help` Cmdlet 只會顯示 \<命令的內容： inputType >/\<maml： description >）元素。

從 Windows PowerShell 3.0 開始，`Get-Help` Cmdlet 會顯示 \<maml： uri > 元素的內容。 此元素可讓您將使用者引導至描述 .NET 類別的主題。

下列 XML 顯示 \<maml： inputTypes > 節點。

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

下列 XML 顯示使用 \<maml： inputTypes > 節點來記錄輸入類型的範例。

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