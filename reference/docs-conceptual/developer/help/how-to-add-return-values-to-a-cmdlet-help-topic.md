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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367797"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>如何新增傳回值至 Cmdlet 說明主題

本節說明如何將 [輸出] 區段新增至 Windows PowerShell® Cmdlet 說明主題。 [輸出] 區段會列出 Cmdlet 傳回或沿著管線向下傳遞之物件的 .NET 類別。

您可以新增至 [輸出] 區段的類別數目沒有限制。 Cmdlet 的傳回型別會括在 \<命令中： returnValues > node，其中每個類別都包含在 \<命令中： returnValue > 元素。

如果 Cmdlet 不會產生任何輸出，請使用此區段來表示沒有輸出。 例如，若要取代類別名稱，請寫入 "None" 並提供簡短說明。 如果 Cmdlet 有條件地產生輸出，請使用此節點來說明條件並描述條件式輸出。

架構包含兩個 \<maml：描述 > 每個 \<命令中的元素： returnValue > 專案。 不過，`Get-Help` Cmdlet 只會顯示 \<命令的內容： returnValue >/\<maml： description > 元素。

從 Windows PowerShell 3.0 開始，`Get-Help` Cmdlet 會顯示 \<maml： uri > 元素的內容。 此元素可讓您將使用者引導至描述 .NET 類別的主題。

下列 XML 顯示 \<maml： returnValues > 節點。

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

下列 XML 顯示使用 \<maml： returnValues > 節點來記錄輸出類型的範例。

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



