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
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>如何新增傳回值至 Cmdlet 說明主題

本節說明如何將輸出區段新增至 PowerShell Cmdlet 說明主題。 [**輸出**] 區段會列出 Cmdlet 傳回或沿著管線向下傳遞之物件的 .net 類別。

您可以新增至 [**輸出**] 區段的類別數目沒有限制。 Cmdlet 的傳回型別會括在節點中 `<command:returnValues>` ，每個類別都包含在專案中 `<command:returnValue>` 。

如果 Cmdlet 不會產生任何輸出，請使用此區段來表示沒有輸出。 例如，若要取代類別名稱，請撰寫**None**並提供簡短說明。 如果 Cmdlet 有條件地產生輸出，請使用此節點來說明條件並描述條件式輸出。

架構 `<maml:description>` 在每個元素中都包含兩個元素 `<command:returnValue>` 。
不過，此 `Get-Help` Cmdlet 只會顯示元素的內容 `<command:returnValue>/<maml:description>` 。

從 PowerShell 3.0 開始，此 `Get-Help` Cmdlet 會顯示元素的內容 `<maml:uri>` 。
此元素可讓您將使用者引導至描述 .NET 類別的主題。

下列 XML 會顯示 `<maml:returnValues>` 節點。

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

下列 XML 顯示使用 `<maml:returnValues>` 節點來記錄輸出類型的範例。

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
