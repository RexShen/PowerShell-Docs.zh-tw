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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>如何新增輸入類型至 Cmdlet 說明主題

本節說明如何將輸入區段新增至 Windows PowerShell® cmdlet 說明主題。 輸入一節列出的.NET 類別的 cmdlet 會接受從管線中，輸入作為，傳值或屬性名稱的物件。

沒有任何限制，您可以新增要在輸入區段的類別數目。 輸入型別會括住\<命令： inputTypes > 節點，並以括住每個類別\<命令： inputType > 項目。

結構描述包含兩個\<maml:description > 中每個項目\<命令： inputType > 項目。 不過， `Get-Help` cmdlet 會顯示的內容\<命令： inputType > /\<maml:description >) 項目。

在 Windows PowerShell 3.0 中，從`Get-Help`cmdlet 會顯示的內容\<maml:uri > 項目。 這個項目可讓您將使用者導向至主題會說明.NET 類別。

下列 XML 會說明\<maml:inputTypes > 節點。

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

下列 XML 顯示的使用範例\<maml:inputTypes > 文件的輸入的類型的節點。

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