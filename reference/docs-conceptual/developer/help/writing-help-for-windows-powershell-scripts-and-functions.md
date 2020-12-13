---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫 PowerShell 腳本和函式的說明
description: 撰寫 PowerShell 腳本和函式的說明
ms.openlocfilehash: f72742e2a131f41ba8ffdcec4901c7c3ea1da1ad
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654633"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>撰寫 PowerShell 腳本和函式的說明

只要與其他人共用 PowerShell 腳本和函式，就應該完整記載。
此 `Get-Help` Cmdlet 會以顯示 Cmdlet 說明的相同格式顯示腳本和函式說明主題，而且所有參數都可 `Get-Help` 在腳本和函式說明主題中運作。

PowerShell 腳本可包含有關腳本的說明主題，以及腳本中每個函式的說明主題。 與腳本分開共用的函式可以包含自己的說明主題。

本檔說明說明主題的格式和正確位置，並建議內容的指導方針。

## <a name="types-of-script-and-function-help"></a>腳本和函式說明的類型

### <a name="comment-based-help"></a>註解型說明

描述腳本或函式的說明主題可以實作為腳本或函數內的一組批註。 撰寫腳本的批註式說明和腳本中的函式時，請特別注意放置以批註為基礎的說明的規則。 放置會決定 Cmdlet 是否將 `Get-Help` 說明主題與腳本或函式產生關聯。 如需撰寫以批註為基礎的說明主題的詳細資訊，請參閱 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。

### <a name="xml-based-command-help"></a>XML-Based 命令說明

描述腳本或函式的說明主題可以在使用命令說明架構的 XML 檔案中執行。 若要將腳本或函式與 XML 檔案產生關聯，請使用 `ExternalHelp` comment 關鍵字，後面接著 xml 檔案的路徑和名稱。

當 `ExternalHelp` comment 關鍵字存在時，其優先于批註式說明，即使 `Get-Help` 找不到符合關鍵字值的說明檔 `ExternalHelp` 。

### <a name="online-help"></a>線上說明

您可以在網際網路上張貼說明主題，然後直接 `Get-Help` 開啟主題。 如需撰寫以批註為基礎的說明主題的詳細資訊，請參閱 [支援線上說明](../module/supporting-online-help.md)。

沒有針對腳本和函式撰寫概念 ( "About" ) 主題的已建立方法。
不過，您可以在網際網路上張貼概念性主題，在命令說明主題的 [相關連結] 區段中，列出主題及其 Url。

## <a name="content-considerations-for-script-and-function-help"></a>腳本和函數說明的內容考慮

- 如果您要撰寫一個非常簡短的說明主題，其中只包含幾個可用的命令説明區段，請務必包含腳本或函式參數的清楚描述。 也請在 [範例] 區段中包含一或兩個範例命令，即使您決定省略範例描述。

- 在 [所有描述] 中，以腳本或函式的形式來參考命令。 此資訊可協助使用者瞭解和管理命令。

  例如，下列詳細描述指出 New-Topic 命令是腳本。
  這會提醒使用者他們在執行時必須指定路徑和完整名稱。

  > 「New-Topic 腳本會為輸入檔中的每個主題名稱建立空白的概念主題 ...」

  以下是函式的詳細說明 `Disable-PSRemoting` 。 當會話包含多個具有相同名稱的命令時，這項資訊特別有用，其中有些命令可能會由優先順序較高的命令隱藏。

  > 此 `Disable-PSRemoting` 函數會停用本機電腦上的所有會話設定 .。。

- 在腳本說明主題中，說明如何使用整個腳本。 如果您也要撰寫腳本中函式的說明主題，請提及腳本說明主題中的函式，並在腳本說明主題的 [相關連結] 區段中包含函數說明主題的參考。
  相反地，當函式是腳本的一部分時，會在函式說明主題中說明函式在腳本中扮演的角色，以及如何獨立使用它。 然後，列出函數說明主題之 [相關連結] 區段中的腳本說明主題。

- 撰寫腳本說明主題的範例時，請務必在範例命令中包含指令檔的路徑。 這會提醒使用者必須明確指定路徑，即使腳本是在目前的目錄中也一樣。

- 在函式說明主題中，提醒使用者函式只存在於目前的會話中，若要在其他會話中使用它，他們需要新增它，或將它新增至 PowerShell 設定檔。

- `Get-Help` 只有當腳本檔案和說明主題檔案儲存在正確的位置時，才會顯示腳本或函式的說明主題。 因此，在腳本或函式說明主題中包含安裝 PowerShell 或儲存或安裝腳本或函式的指示並不實用。 相反地，請在您用來散發腳本或功能的檔中包含任何安裝指示。

## <a name="see-also"></a>另請參閱

[撰寫註解型說明主題](./writing-comment-based-help-topics.md)
