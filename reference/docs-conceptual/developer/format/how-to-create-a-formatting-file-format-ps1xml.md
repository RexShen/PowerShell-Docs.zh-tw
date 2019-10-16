---
title: 如何建立格式檔案（. 格式. types.ps1xml） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363617"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>如何建立格式設定檔案 (.format.ps1xml)

本主題說明如何建立格式檔案（. 格式. types.ps1xml）。

> [!NOTE]
> 您也可以藉由複製 Windows PowerShell 所提供的其中一個檔案，建立格式檔案。 如果您複製現有的檔案，請刪除現有的數位簽章，並將您自己的簽章新增至新的檔案。

### <a name="to-create-a-formatps1xml-file"></a>建立 types.ps1xml 檔案。

1. 使用文字編輯器（如 [記事本]）建立文字檔（.txt）。

2. 將下列幾行複製到格式檔案中。

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - @No__t 0Configuration > \</Configuration > 標記會定義根 @no__t 2 節點。 所有其他的 XML 標記都會放在這個節點內。

   - <ViewDefinitions></ViewDefinitions>標記會定義 @no__t 1 節點。 所有的視圖都會在此節點中定義。

3. 將檔案儲存至 Windows PowerShell 安裝資料夾、模組資料夾或模組資料夾的子資料夾。 當您儲存檔案時，請使用下列名稱格式： `MyFile.format.ps1xml`。 格式化檔案必須使用 `.format.ps1xml` 延伸模組。

   您現在已準備好將 views 新增至格式化檔案。 可以在格式化檔案中定義的視圖數目沒有限制。 您可以為每個物件、多個相同物件的視圖，或多個物件所使用的單一視圖加入單一視圖。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 格式化和類型檔案](./writing-a-powershell-formatting-file.md)
