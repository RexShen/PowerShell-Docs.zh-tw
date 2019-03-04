---
title: 如何新增 Cmdlet 描述 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862594"
---
# <a name="how-to-add-a-cmdlet-description"></a>如何新增 Cmdlet 描述

本節說明如何新增會顯示在 [描述] 部分的 cmdlet 說明的內容。 在說明檔案中，此內容會新增至每個 cmdlet 的命令節點。

> [!NOTE]
> 說明檔案，開啟其中一個 dll Help.xml 檔案位於 Windows PowerShell 安裝目錄的完整檢視。 比方說，Microsoft.PowerShell.Commands.Management.dll Help.xml 檔案會包含內容的數個 Windows PowerShell cmdlet。

### <a name="to-add-a-description"></a>若要加入描述

- 開始說明更多詳細資料中的指令程式的基本功能。 在許多情況下，您可以說明 cmdlet 名稱中使用的詞彙，並說明使用的範例不熟悉的概念。 例如，如果此 cmdlet 會將資料附加至檔案，說明它將資料加入至現有檔案的結尾。

- 若要尋找所有 cmdlet 的功能，請檢閱參數清單。 描述主要功能的 cmdlet，則包含其他功能和特性。 例如，如果此指令程式的主要功能是變更一個屬性，但 cmdlet 可以變更的所有屬性，說中詳細說明。 如果 cmdlet 參數可讓使用者以不同的方式請求資訊，請將其說明。

- 包含使用者可以使用 cmdlet，除了明顯的使用方式的資訊。 例如，您可以使用物件，`Get-Host`指令程式會擷取變更的 Windows PowerShell 命令視窗中的文字色彩。

  範例：「 `Get-Acl` Cmdlet 會取得代表檔案或資源的安全性描述元的物件。 安全性描述元包含資源的存取控制清單 (ACL)。 ACL 會指定使用者和使用者群組具有存取資源的權限。 」

- 詳細的描述應描述 cmdlet，但它應該描述此 cmdlet 會使用的概念。 將概念定義放在其他注意事項。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
