---
title: 如何建立 Cmdlet 說明檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083241"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>如何建立 Cmdlet 說明檔案

本節說明如何建立有效的 XML 檔案，包含 Windows PowerShell cmdlet 說明主題的內容。 本節討論如何命名的說明檔、 如何新增適當的 XML 標頭，以及如何加入將包含 cmdlet 的說明內容的各區段的節點。

> [!NOTE]
> 說明檔案，開啟其中一個 dll Help.xml 檔案位於 Windows PowerShell 安裝目錄的完整檢視。 比方說，Microsoft.PowerShell.Commands.Management.dll Help.xml 檔案會包含內容的數個 Windows PowerShell cmdlet。

### <a name="how-to-create-a-cmdlet-help-file"></a>如何建立 Cmdlet 說明檔

1. 建立文字檔案，並將它使用 UTF8 編碼方式儲存。 檔案名稱必須以下列格式，使 Windows PowerShell 可以偵測到它的 cmdlet 說明檔。

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. 文字檔案中加入下列的 XML 標頭。 請注意，將會針對多重代理程式模型化語言 （maml） 進行結構描述驗證的檔案。 目前，Windows PowerShell 不提供任何工具來驗證檔案。

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. 命令將節點新增至組件中的每個 cmdlet 的 cmdlet 說明檔。 命令節點內的每個節點與相關的 cmdlet 說明主題各區段。

   下表列出每個節點，後面接著描述每個節點的 XML 項目。

   |節點|描述|
   |----------|-----------------|
   |`<details>`|新增 cmdlet 說明主題的名稱和概要區段的內容。 如需詳細資訊，請參閱 <<c0> [ 如何將 Cmdlet 名稱和概要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)。|
   |`<maml:description>`|新增 [描述] 部分的 cmdlet 說明主題的內容。 如需詳細資訊，請參閱 < [how to Add Cmdlet 說明主題的詳細說明如何](./how-to-add-a-cmdlet-description.md)。|
   |`<command:syntax>`|新增 cmdlet 說明主題語法 」 一節的內容。 如需詳細資訊，請參閱 <<c0> [ 如何新增語法 Cmdlet 說明主題](./how-to-add-syntax-to-a-cmdlet-help-topic.md)。|
   |`<command:parameters>`|將參數區段的 cmdlet 說明主題的內容。 如需詳細資訊，請參閱 <<c0> [ 如何將參數加入 Cmdlet 說明主題](./how-to-add-parameter-information.md)。|
   |`<command:inputTypes>`|將輸入區段的 cmdlet 說明主題的內容。 如需詳細資訊，請參閱 <<c0> [ 新增至 Cmdlet 說明主題的輸入類型如何](./how-to-add-input-types-to-a-cmdlet-help-topic.md)。|
   |`<command:returnValues>`|新增 cmdlet 說明主題的輸出區段的內容。 如需詳細資訊，請參閱 <<c0> [ 如何將傳回值 Cmdlet 說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)。|
   |`<maml:alertset>`|將內容加入提示 > 一節中的 cmdlet 說明主題。 如需詳細資訊，請參閱 <<c0> [ 如何新增備忘稿的 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)。|
   |`<command:examples>`|新增 cmdlet 說明主題的範例 > 一節的內容。 如需詳細資訊，請參閱 <<c0> [ 範例新增至 Cmdlet 說明主題的如何](./how-to-add-examples-to-a-cmdlet-help-topic.md)。|
   |`<maml:relatedLinks>`|新增 cmdlet 說明主題的相關連結 區段的內容。 如需詳細資訊，請參閱 <<c0> [ 如何將相關連結 Cmdlet 說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)。|

## <a name="example"></a>範例

 以下是命令節點 （包括 cmdlet 說明主題的各個區段的節點） 的範例。

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>另請參閱

 [如何將 Cmdlet 名稱和概要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [如何將詳細的說明新增至 Cmdlet 的說明主題](./how-to-add-a-cmdlet-description.md)

 [如何將 Cmdlet 說明主題中的語法](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [如何將參數新增至 Cmdlet 的說明主題](./how-to-add-parameter-information.md)

 [如何將 Cmdlet 說明主題中的輸入的類型](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [如何將傳回的值新增至 Cmdlet 的說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [如何新增備忘稿的 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [如何新增 Cmdlet 說明主題的範例](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [如何將相關的連結新增至 Cmdlet 的說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)