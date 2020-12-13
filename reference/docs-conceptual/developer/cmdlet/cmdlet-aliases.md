---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 別名
description: Cmdlet 別名
ms.openlocfilehash: 734553a9911aef256df563afa6abcdb23d7a62e6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660796"
---
# <a name="cmdlet-aliases"></a>Cmdlet 別名

您可以使用 Cmdlet 別名來改善 Cmdlet 使用者體驗。 您可以將別名新增到常用的 Cmdlet 來減少輸入，並讓您更輕鬆地快速完成工作。 您可以在 Cmdlet 中包含內建的別名，或是使用者可以定義自己的自訂別名。

例如， [Get 命令](/powershell/module/microsoft.powershell.core/get-command) Cmdlet 有內建的 `gcm` 別名。 您也可以使用別名來新增其他語言的命令名稱，讓使用者不需要學習新的命令。

## <a name="alias-guidelines"></a>別名指導方針

當您建立 Cmdlet 的內建別名時，請遵循下列指導方針：

- 指派別名之前，請先開始 Windows PowerShell，然後執行「 [取得別名](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) 」 Cmdlet 以查看已使用的別名。

- 包含別名前置詞，其參考 Cmdlet 名稱的動詞，以及參考 Cmdlet 名稱名詞的別名尾碼。 例如，Cmdlet 的別名是「 `Import-Module` ipmo」。 如需所有動詞及其別名的清單，請參閱 [Cmdlet 動詞](./approved-verbs-for-windows-powershell-commands.md)命令。

- 針對具有相同動詞的 Cmdlet，請包含相同的別名前置詞。 例如，在其名稱中有 "Get" 動詞的所有 Windows PowerShell Cmdlet 的別名會使用 "g" 前置詞。

- 若為具有相同名詞的 Cmdlet，請包含相同的別名尾碼。 例如，其名稱中有 "Session" 名詞的所有 Windows PowerShell Cmdlet 的別名會使用 "sn" 尾碼。

- 針對相當於其他語言命令的 Cmdlet，請使用命令的名稱。

- 一般情況下，請盡可能縮短別名。 請確定別名至少有一個用於動詞的相異字元和一個不同的名詞字元。 視需要新增更多字元，使別名成為唯一的。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
