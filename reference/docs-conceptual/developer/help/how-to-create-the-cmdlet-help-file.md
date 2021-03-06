---
ms.date: 09/13/2016
ms.topic: reference
title: 如何建立 Cmdlet 說明檔案
description: 如何建立 Cmdlet 說明檔案
ms.openlocfilehash: 40259c8f9496b10380805a78f3711aed6f1bf2e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659096"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>如何建立 Cmdlet 說明檔案

本節說明如何建立包含 Windows PowerShell Cmdlet 說明主題內容的有效 XML 檔。 本節討論如何命名說明檔、如何新增適當的 XML 標頭，以及如何加入將包含 Cmdlet 說明內容不同區段的節點。

> [!NOTE]
> 如需說明檔的完整資訊，請開啟 `dll-Help.xml` 位於 Windows PowerShell 安裝目錄中的其中一個檔案。 例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。

### <a name="how-to-create-a-cmdlet-help-file"></a>如何建立 Cmdlet 說明檔

1. 建立文字檔，並使用 UTF8 編碼來儲存它。 檔案名必須具有下列格式，才能讓 Windows PowerShell 偵測為 Cmdlet 說明檔。

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. 將下列 XML 標頭新增至文字檔。 請注意，檔案會根據 Microsoft 協助標記語言進行驗證， (MAML) 架構。 PowerShell 目前未提供任何工具來驗證檔案。

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. 針對元件中的每個 Cmdlet，將 **命令** 節點新增至 Cmdlet 說明檔。 **命令** 節點內的每個節點都與 Cmdlet 說明主題的不同區段有關。

   下表列出每個節點的 XML 元素，後面接著每個節點的描述。

   |           節點           |                                                                                                     說明                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | 新增 Cmdlet 說明主題之 [名稱] 和 [摘要] 區段的內容。 如需詳細資訊，請參閱 [如何新增 Cmdlet 名稱和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)。 |
   | `<maml:description>`     | 新增 Cmdlet 說明主題之 [描述] 區段的內容。 如需詳細資訊，請參閱 [如何將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)。                    |
   | `<command:syntax>`       | 新增 Cmdlet 說明主題之語法區段的內容。 如需詳細資訊，請參閱 [如何將語法新增至 Cmdlet 說明主題](./how-to-add-syntax-to-a-cmdlet-help-topic.md)。                                  |
   | `<command:parameters>`   | 新增 Cmdlet 說明主題之 PARAMETERS 區段的內容。 如需詳細資訊，請參閱 [如何將參數新增至 Cmdlet 說明主題](./how-to-add-parameter-information.md)。                                  |
   | `<command:inputTypes>`   | 新增 Cmdlet 說明主題之 [輸入] 區段的內容。 如需詳細資訊，請參閱 [如何將輸入類型新增至 Cmdlet 說明主題](./how-to-add-input-types-to-a-cmdlet-help-topic.md)。                        |
   | `<command:returnValues>` | 新增 Cmdlet 說明主題之 [輸出] 區段的內容。 如需詳細資訊，請參閱 [如何將傳回值新增至 Cmdlet 說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)。                   |
   | `<maml:alertset>`        | 新增 Cmdlet 說明主題之 NOTES 區段的內容。 如需詳細資訊，請參閱 [如何將附注新增至 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)。                                      |
   | `<command:examples>`     | 新增 Cmdlet 說明主題之 [範例] 區段的內容。 如需詳細資訊，請參閱 [如何將範例新增至 Cmdlet 說明主題](./how-to-add-examples-to-a-cmdlet-help-topic.md)。                            |
   | `<maml:relatedLinks>`    | 新增 Cmdlet 說明主題之 [相關連結] 區段的內容。 如需詳細資訊，請參閱 [如何將相關連結新增至 Cmdlet 說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)。             |

## <a name="example"></a>範例

 以下是 **命令** 節點的範例，其中包含 Cmdlet 說明主題各區段的節點。

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

 [如何新增 Cmdlet 名稱和摘要](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [如何將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)

 [如何新增語法至 Cmdlet 說明主題](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [如何將參數新增至 Cmdlet 說明主題](./how-to-add-parameter-information.md)

 [如何新增輸入類型至 Cmdlet 說明主題](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [如何新增傳回值至 Cmdlet 說明主題](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [如何將附注新增至 Cmdlet 說明主題](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [如何新增範例至 Cmdlet 說明主題](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [如何新增相關連結至 Cmdlet 說明主題](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
