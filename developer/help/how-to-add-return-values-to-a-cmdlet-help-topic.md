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
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>如何新增傳回值至 Cmdlet 說明主題

本節說明如何將 OUTPUTS 區段新增至 Windows PowerShell® cmdlet 說明主題。 OUTPUTS 區段列出的.NET 類別的指令程式傳回或傳遞到管線的物件。

沒有任何限制，您可以將它新增至 [輸出] 區段的類別數目。 Cmdlet 的傳回型別會括住\<命令： returnValues > 節點，並以括住每個類別\<命令： returnValue > 項目。

如果 cmdlet 不會產生任何輸出，請使用本節來表示沒有任何輸出。 比方說，來取代類別名稱中，撰寫 「 無 」，並提供簡短說明。 如果 cmdlet 有條件地產生輸出，請使用此節點來說明條件及描述的條件式的輸出。

結構描述包含兩個\<maml:description > 中每個項目\<命令： returnValue > 項目。 不過， `Get-Help` cmdlet 會顯示的內容\<命令： returnValue > /\<maml:description > 項目。

在 Windows PowerShell 3.0 中，從`Get-Help`cmdlet 會顯示的內容\<maml:uri > 項目。 這個項目可讓您將使用者導向至主題會說明.NET 類別。

下列 XML 會說明\<maml:returnValues > 節點。

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

下列 XML 顯示的使用範例\<maml:returnValues > 文件的輸出類型的節點。

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



