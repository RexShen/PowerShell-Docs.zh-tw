---
title: Cmdlet 別名 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860504"
---
# <a name="cmdlet-aliases"></a>Cmdlet 別名

您可以使用 cmdlet 別名來改善指令程式使用者經驗。 您可以經常使用的 cmdlet，以減少輸入並讓您更輕鬆地完成工作快速新增別名。 您可以納入您的 cmdlet 中的內建的別名或使用者可以定義自己的自訂別名。

例如， [Get-command](/powershell/module/microsoft.powershell.core/get-command) cmdlet 具有內建`gcm`別名。 您也可以使用別名新增其他語言的命令名稱，以便使用者不需要學習新的命令。

## <a name="alias-guidelines"></a>別名的指導方針

當您建立您的 cmdlet 的內建的別名時，請遵循下列指導方針：

- 指派別名之前，啟動 Windows PowerShell，然後再執行[Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet 來查看已使用的別名。

- 包含參考的指令程式的名稱和名詞的 cmdlet 名稱所參考的別名後置詞的動詞命令的別名前置詞。 比方說，別名`Import-Module`cmdlet 是"ipmo"。 如需所有動詞命令和其別名的清單，請參閱 < [Cmdlet 動詞](./approved-verbs-for-windows-powershell-commands.md)。

- 針對具有相同的指令動詞的 cmdlet，包括相同的別名前置詞。 比方說，其名稱中含有"Get"動詞的所有 Windows PowerShell cmdlet 的別名會使用"g"前置詞。

- 針對具有相同名詞的 cmdlet，包含相同別名後置詞。 例如，具有其名稱中的 「 工作階段 」 名詞的所有 Windows PowerShell cmdlet 的別名會使用"sn"後置詞。

- 針對其他語言中的命令對等的 cmdlet，使用命令的名稱。

- 一般情況下，請盡量縮短的別名。 請確定別名具有至少一個動詞命令的不同字元和一個為名詞的個別字元。 新增更多的字元，視需要使其成為唯一別名。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
