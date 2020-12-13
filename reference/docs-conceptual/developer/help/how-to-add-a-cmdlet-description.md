---
ms.date: 09/13/2016
ms.topic: reference
title: 如何新增 Cmdlet 描述
description: 如何新增 Cmdlet 描述
ms.openlocfilehash: 08d21a281881678423bbe3c382279875ed2868db
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651218"
---
# <a name="how-to-add-a-cmdlet-description"></a>如何新增 Cmdlet 描述

本節說明如何新增在 Cmdlet 說明的 [ **描述** ] 部分中顯示的內容。 在說明檔中，此內容會新增至每個 Cmdlet 的 **命令** 節點。

> [!NOTE]
> 如需說明檔的完整觀點，請開啟 `dll-Help.xml` 位於 PowerShell 安裝目錄中的其中一個檔案。 例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。

### <a name="to-add-a-description"></a>若要加入描述

- 一開始會更詳細地說明 Cmdlet 的基本功能。 在許多情況下，您可以說明 Cmdlet 名稱中所使用的詞彙，並使用範例來說明不熟悉的概念。 例如，如果 Cmdlet 將資料附加至檔案，則說明它會將資料新增至現有檔案的結尾。

- 若要尋找 Cmdlet 的所有功能，請檢查參數清單。 描述 Cmdlet 的主要功能，然後包含其他功能和功能。 例如，如果 Cmdlet 的 main 函式是變更一個屬性，則 Cmdlet 可以變更所有屬性，例如在詳細的描述中。 如果 Cmdlet 參數讓使用者以不同的方式來請求資訊，請加以說明。

- 除了明顯的用途之外，還包含使用者可以使用 Cmdlet 的方法資訊。 例如，您可以使用 Cmdlet 抓取的物件 `Get-Host` 來變更 Windows PowerShell 命令視窗中的文字色彩。

  範例：「 `Get-Acl` Cmdlet 會取得物件，以代表檔案或資源的安全描述項。 安全性描述元包含資源的存取控制清單 (ACL)。 ACL 會指定使用者和使用者群組存取資源所需的許可權。

- 詳細描述應該描述 Cmdlet，但不應該描述 Cmdlet 所使用的概念。 將概念定義放在其他附注中。

## <a name="see-also"></a>另請參閱

[Windows PowerShell SDK](../windows-powershell-reference.md)
