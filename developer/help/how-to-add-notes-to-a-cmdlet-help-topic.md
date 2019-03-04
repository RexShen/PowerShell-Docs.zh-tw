---
title: 如何將資訊新增至 Cmdlet 的說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862264"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>如何新增附註至 Cmdlet 說明主題

本節說明如何將附註區段新增至 Windows PowerShell® cmdlet 說明主題。 附註區段用來說明不適合輕鬆地在其他結構化的區段，例如參數的詳細說明的詳細資料。 此內容可能包含與特定的提供者 cmdlet 的運作方式，一些唯一的但重要的是，會使用的 cmdlet 或如何避免可能的錯誤狀況的註解。

沒有任何限制，您可以加入提示 > 一節的附註的數目。 針對每個提示中，加入一組\<maml:alert > 標記\<maml:alertset > 節點。 每個提示的內容就會在一組\<: para><maml: > 標記。 使用空白\<: para><maml: > 標記間距。

下列 XML 會說明\<maml:alertset > 使用兩個節點的節點。 請注意，每個提示有選擇性\<title> > 標記 (項目可用來群組一組\<maml:alert > 標記)，而且每個提示有空白行遵循間距的內容。

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



