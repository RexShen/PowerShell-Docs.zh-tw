---
title: 如何將 Cmdlet 說明主題中的 Cmdlet 名稱和概要 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083327"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題

本節說明如何新增顯示名稱和概要區段中的 cmdlet 說明的內容。 在說明檔案中，此內容會新增至每個 cmdlet 的命令節點。

> [!NOTE]
> 說明檔案，開啟其中一個 dll Help.xml 檔案位於 Windows PowerShell 安裝目錄的完整檢視。 比方說，Microsoft.PowerShell.Commands.Management.dll Help.xml 檔案會包含內容的數個 Windows PowerShell cmdlet。

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>將指令程式的名稱和概要

- Cmdlet 說明可以顯示兩個 cmdlet 的說明。 第一個描述是稱為 「 概要的簡短描述。 第二項描述會更詳細的描述中所討論[Cmdlet 說明主題將詳細說明](./how-to-add-a-cmdlet-description.md)。 這兩個這些描述應寫成單一的段落。

- 在概要中不重複的 cmdlet 名稱。 通知使用者 Get-server cmdlet 會取得伺服器是簡短，但不是具有資訊價值。 相反地，使用同義字，並新增至描述的詳細資料。

  範例：「 取得物件，表示在本機或遠端電腦。 」

- 使用簡單的動詞，例如 「 get 」、 「 建立 」 和 「 變更 」 中的概要。 請避免使用 「 設定 」 因為它是含糊不清，而且美觀的字這類 「 修改。 」

  範例：「 檔案中取得 Authenticode 簽章的相關資訊。 」

- 主動語氣來撰寫。 例如，[使用 TimeSpan 物件...]要清楚得多比 「 TimeSpan 物件可用來...」

- 描述取得物件的 cmdlet 時，請避免動詞"display"。 雖然 Windows PowerShell 會顯示 cmdlet 的資料，務必為使用者介紹的概念，此 cmdlet 會傳回.NET Framework 物件可能不會顯示其資料。 如果強調顯示時，使用者可能不知道此 cmdlet 可能會傳回許多其他有用的屬性和方法，不會顯示。

## <a name="see-also"></a>另請參閱

 [Windows PowerShell SDK](../windows-powershell-reference.md)