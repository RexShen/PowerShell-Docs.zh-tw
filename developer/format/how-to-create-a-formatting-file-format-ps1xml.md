---
title: 如何建立格式檔案 (。 format.ps1xml) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862964"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>如何建立格式設定檔案 (.format.ps1xml)

本主題描述如何建立格式檔案 (。 format.ps1xml)。

> [!NOTE]
> 您也可以藉由其中一個 Windows PowerShell 所提供的檔案複製建立格式化的檔案。 如果您建立一份現有的檔案時，刪除現有的數位簽章，並將您自己的簽章新增至新的檔案。

### <a name="to-create-a-formatps1xml-file"></a>若要建立。 format.ps1xml 檔案。

1. 建立文字檔 (.txt) 使用文字編輯器例如記事本。

2. 將下列幾行複製到的格式化檔案中。

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - \<組態 >\</Configuration > 標籤會定義根`Configuration`節點。 所有其他的 XML 標記會住此節點。

   - <ViewDefinitions> </ViewDefinitions>標籤會定義`ViewDefinitions`節點。 此節點內定義所有的檢視。

3. Windows PowerShell 安裝資料夾、 您的模組資料夾，或模組資料夾的子資料夾，請儲存檔案。 當您儲存檔案時，請使用下列名稱格式： `MyFile.format.ps1xml`。 格式檔案必須使用`.format.ps1xml`延伸模組。

   您現在已準備好將檢視加入至格式化檔案。 可以格式化檔案中定義的檢視表的數目沒有限制。 您可以新增每個物件、 多個檢視，針對相同的物件或單一檢視，可由多個物件的單一檢視。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 格式和類型的檔案](./writing-a-powershell-formatting-file.md)
