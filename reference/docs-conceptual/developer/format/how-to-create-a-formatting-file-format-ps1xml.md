---
ms.date: 09/13/2016
ms.topic: reference
title: 如何建立格式設定檔案 (.format.ps1xml)
description: 如何建立格式設定檔案 (.format.ps1xml)
ms.openlocfilehash: 5bbc1ba40bfccf13636abc0f0751938aa724b761
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652002"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>如何建立格式設定檔案 (.format.ps1xml)

本主題說明如何建立 ( # B0 xml) 的格式化檔案。

> [!NOTE]
> 您也可以建立 Windows PowerShell 所提供的其中一個檔案的複本，以建立格式化檔案。 如果您複製現有的檔案，請刪除現有的數位簽章，並將您自己的簽章新增至新的檔案。

### <a name="to-create-a-formatps1xml-file"></a>建立 .format.ps1的 xml 檔。

1. 使用記事本之類的文字編輯器建立文字檔 ( .txt) 。

2. 將下列幾行複製到格式設定檔中。

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - 這些 `<Configuration></Configuration>` 標記會定義根 `Configuration` 節點。 所有其他的 XML 標記將會包含在此節點內。

   - 這些 `<ViewDefinitions></ViewDefinitions>` 標記會定義 `ViewDefinitions` 節點。 所有視圖都是在此節點中定義。

3. 將檔案儲存到 Windows PowerShell 安裝資料夾、模組資料夾或模組資料夾的子資料夾。 當您儲存檔案時，請使用下列名稱格式：  `MyFile.format.ps1xml` 。 格式化檔案必須使用 `.format.ps1xml` 擴充功能。

   您現在已準備好將視圖新增至格式化檔案。 在格式化檔案中可定義的視圖數目沒有任何限制。 您可以為每個物件、相同物件的多個視圖，或多個物件使用的單一視圖，新增單一視圖。

## <a name="see-also"></a>另請參閱

[寫入 Windows PowerShell 格式和類型檔案](./writing-a-powershell-formatting-file.md)
