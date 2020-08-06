---
title: Cmdlet 別名 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fed4055f09e01c5f3fa87584d48551918606f4eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784532"
---
# <a name="cmdlet-aliases"></a>Cmdlet 別名

您可以使用 Cmdlet 別名來改善 Cmdlet 的使用者體驗。 您可以將別名新增至常用的 Cmdlet 以減少輸入，並可讓您更輕鬆地快速完成工作。 您可以在 Cmdlet 中包含內建別名，或使用者可以定義自己的自訂別名。

例如， [Get-Command](/powershell/module/microsoft.powershell.core/get-command) Cmdlet 具有內建的 `gcm` 別名。 您也可以使用別名來新增其他語言的命令名稱，讓使用者不必學習新的命令。

## <a name="alias-guidelines"></a>別名指導方針

當您建立 Cmdlet 的內建別名時，請遵循下列指導方針：

- 指派別名之前，請先啟動 Windows PowerShell，然後執行[取得別名](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias)Cmdlet，以查看已經使用的別名。

- 包含別名前置詞，此首碼會參考 Cmdlet 名稱的動詞，以及參考 Cmdlet 名稱名詞的別名尾碼。 例如，Cmdlet 的別名是「 `Import-Module` ipmo」。 如需所有動詞和其別名的清單，請參閱[Cmdlet 動詞](./approved-verbs-for-windows-powershell-commands.md)。

- 對於具有相同動詞的 Cmdlet，請包含相同的別名前置詞。 例如，名稱中含有 "Get" 動詞的所有 Windows PowerShell Cmdlet 的別名都會使用 "g" 前置詞。

- 對於具有相同名詞的 Cmdlet，請包含相同的別名尾碼。 例如，名稱中包含 "Session" 名詞的所有 Windows PowerShell Cmdlet 的別名都會使用 "sn.exe" 尾碼。

- 對於相當於其他語言之命令的 Cmdlet，請使用命令的名稱。

- 一般來說，請儘量縮短別名。 請確定別名至少有一個用於動詞的相異字元，以及一個代表名詞的相異字元。 視需要新增更多字元，讓別名成為唯一的。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
