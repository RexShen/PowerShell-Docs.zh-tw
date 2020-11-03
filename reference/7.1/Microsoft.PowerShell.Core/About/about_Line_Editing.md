---
description: 描述如何在 PowerShell 命令提示字元中編輯命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_line_editing?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Line_Editing
ms.openlocfilehash: 31659994e5b99cddd7374badff10e3286b1a4916
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206508"
---
# <a name="about-line-editing"></a>關於行編輯

## <a name="short-description"></a>簡短描述

描述如何在 PowerShell 命令提示字元中編輯命令。

## <a name="long-description"></a>完整描述

PowerShell 主控台有一些實用的鍵盤快速鍵，可協助您在 PowerShell 命令提示字元中編輯命令。

### <a name="add-a-line"></a>新增線條

若要加入一行，請按<kbd>Shift</kbd> + <kbd>enter</kbd>鍵。

您可以新增多行。 每個額外一行開頭為 `>>` 接續提示。 按 <kbd>enter</kbd> 鍵以執行命令。

### <a name="move-left-and-right"></a>向左和向右移動

若要將游標向左移動一個字元，請按 <kbd>向左箭</kbd>號。

若要將游標向左移動一個單字，請按下<kbd>Ctrl</kbd> + <kbd>向左箭</kbd>號。

若要將游標向右移動一個字元，請按 <kbd>向右箭</kbd>號。

若要將游標向右移動一個單字，請按下<kbd>Ctrl</kbd> + <kbd>向右箭</kbd>號。

### <a name="move-to-a-lines-beginning-or-end"></a>移至行的開頭或結尾

若要移至行的開頭，請按 [ <kbd>首頁</kbd>]。

若要移至行的結尾，請按 <kbd>end</kbd>。

如果已加入行，請按 <kbd>Home</kbd> 或 <kbd>end</kbd> 兩次，以移至行的開頭或結尾。

### <a name="delete-characters"></a>刪除字元

若要刪除游標位置後方的字元，請按 <kbd>倒退鍵</kbd>。

若要刪除游標位置的字元，請按 <kbd>delete</kbd>鍵。

### <a name="delete-characters-from-a-line"></a>從一行刪除字元

若要將游標位置的所有字元刪除到行尾，請按下<kbd>Ctrl</kbd> + <kbd>end</kbd>。

若要將游標位置的所有字元刪除到行首，請按<kbd>Ctrl</kbd> + <kbd>Home</kbd>。

如果加入了行，則會從目前的行和已加入的行中刪除字元。

### <a name="insert-and-overstrike-mode"></a>插入和覆寫模式

若要變更為覆寫模式，請按 [ <kbd>插入</kbd>]。 若要返回插入模式，請再次按下 <kbd>insert</kbd> 。

### <a name="tab-completion"></a>Tab 鍵自動完成

若要完成 Cmdlet 名稱、參數或路徑，請按下 <kbd>tab</kbd> 鍵。 若要流覽值清單，請再次按下 <kbd>tab</kbd> 鍵。

## <a name="see-also"></a>另請參閱

[about_Command_Syntax](about_Command_Syntax.md)

[about_Path_Syntax](about_Path_Syntax.md)

[about_PSReadline](../../PSReadline/About/about_PSReadline.md)

