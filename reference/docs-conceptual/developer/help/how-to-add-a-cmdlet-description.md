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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361277"
---
# <a name="how-to-add-a-cmdlet-description"></a>如何新增 Cmdlet 描述

本節說明如何新增在 Cmdlet 說明的 [描述] 部分中顯示的內容。 在說明檔中，此內容會新增至每個 Cmdlet 的命令節點。

> [!NOTE]
> 如需說明檔的完整視圖，請開啟位於 Windows PowerShell 安裝目錄中的其中一個 dll-Help 檔案。 例如，dll-Help 檔案包含數個 Windows PowerShell 指令程式的內容（content）。

### <a name="to-add-a-description"></a>若要加入描述

- 一開始會更詳細地說明 Cmdlet 的基本功能。 在許多情況下，您可以說明 Cmdlet 名稱中使用的詞彙，並以範例說明不熟悉的概念。 例如，如果 Cmdlet 將資料附加至檔案，則會說明它會將資料新增至現有檔案的結尾。

- 若要尋找 Cmdlet 的所有功能，請查看參數清單。 描述 Cmdlet 的主要功能，然後包含其他功能和功能。 例如，如果 Cmdlet 的 main 函式是要變更一個屬性，但 Cmdlet 可以變更所有屬性，在詳細的描述中就是如此。 如果 Cmdlet 參數讓使用者以不同的方式來請求資訊，請加以說明。

- 除了明顯的用法以外，還包括使用者可以使用 Cmdlet 的方式資訊。 例如，您可以使用 `Get-Host` Cmdlet 抓取的物件，在 Windows PowerShell 命令視窗中變更文字的色彩。

  範例：「`Get-Acl` Cmdlet 會取得代表檔案或資源之安全描述項的物件。 安全性描述元包含資源的存取控制清單 (ACL)。 ACL 會指定使用者和使用者群組存取資源所需的許可權。

- 詳細描述應描述 Cmdlet，但不應描述 Cmdlet 所使用的概念。 將概念定義放在其他筆記中。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
