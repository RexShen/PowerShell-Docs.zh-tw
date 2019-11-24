---
title: 撰寫 PowerShell 腳本和函式的說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367717"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>撰寫 PowerShell 腳本和功能的說明

當 PowerShell 腳本和函式與其他人共用時，應該完整記載。
`Get-Help` Cmdlet 會顯示腳本和函式說明主題，其格式與顯示 Cmdlet 的說明相同，而且所有 `Get-Help` 參數都適用于腳本和函式說明主題。

PowerShell 腳本可以包含有關腳本中每個函式之腳本和說明主題的說明主題。
獨立于腳本共用的函式可以包含自己的說明主題。

本檔說明說明主題的格式和正確位置，並建議內容的指導方針。

## <a name="types-of-script-and-function-help"></a>腳本和函數說明的類型

### <a name="comment-based-help"></a>以批註為基礎的說明
描述腳本或函式的說明主題，可以實作為腳本或函式中的一組批註。
針對腳本撰寫以批註為基礎的說明，並針對腳本中的函式，請特別注意放置以批註為基礎之說明的規則。
此位置會決定 `Get-Help` Cmdlet 是否要將說明主題與腳本或函式產生關聯。
如需撰寫以批註為基礎之說明主題的詳細資訊，請參閱[about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。

### <a name="xml-based-command-help"></a>以 XML 為基礎的命令說明
描述腳本或函數的說明主題，可以在使用命令說明架構的 XML 檔案中執行。
若要將腳本或函數與 XML 檔案產生關聯，請使用 `ExternalHelp` comment 關鍵字，後面接著 XML 檔案的路徑和名稱。

當 `ExternalHelp` comment 關鍵字存在時，它的優先順序高於以批註為基礎的說明，即使 `Get-Help` 找不到符合 `ExternalHelp` 關鍵字值的說明檔案也一樣。

### <a name="online-help"></a>線上說明
您可以在網際網路上張貼說明主題，然後直接 `Get-Help` 開啟主題。
如需撰寫以批註為基礎之說明主題的詳細資訊，請參閱[支援線上說明](../module/supporting-online-help.md)。

沒有已建立的方法可撰寫腳本和函式的概念性（「關於」）主題。
不過，您可以在網際網路清單上張貼概念性主題的主題，以及命令說明主題的 [相關連結] 區段中的 Url。

## <a name="content-considerations-for-script-and-function-help"></a>腳本和函數說明的內容考慮

- 如果您要撰寫一個非常簡短的說明主題，其中只有幾個可用的命令說明區段，請務必包含腳本或函數參數的清楚描述。 也請在 [範例] 區段中包含一或兩個範例命令，即使您決定省略範例描述也一樣。

- 在所有描述中，請將命令稱為腳本或函式。 此資訊可協助使用者瞭解和管理命令。

  例如，下列詳細描述說明新主題的命令是腳本。 這會提醒使用者他們在執行時必須指定路徑和完整名稱。

  > 「新主題腳本會針對輸入檔中的每個主題名稱建立空白的概念主題 ...」

  下列詳細描述指出 `Disable-PSRemoting` 為函式。 當會話包含多個具有相同名稱的命令時，這項資訊特別有用，其中某些命令可能會被較高優先順序的命令隱藏。

  > `Disable-PSRemoting` 函式會停用本機電腦上的所有會話設定 。

- 在腳本說明主題中，說明如何使用整個腳本。 如果您也在腳本中撰寫函式的說明主題，請在腳本說明主題中提及函數，並在腳本說明主題的 [相關連結] 區段中包含函數說明主題的參考。 相反地，當函式是腳本的一部分時，請在函式說明主題中說明函式在腳本中所扮演的角色，以及如何獨立使用該功能。 然後在函式說明主題的 [相關連結] 區段中列出腳本說明主題。

- 撰寫腳本說明主題的範例時，請務必在範例命令中包含腳本檔案的路徑。 這會提醒使用者必須明確指定路徑，即使腳本位於目前目錄中也一樣。

- 在函式說明主題中，提醒使用者該函式只存在於目前的會話中，若要在其他會話中使用，他們必須加以新增，或將它新增至 PowerShell 設定檔。

- `Get-Help` 只有在腳本檔案和說明主題檔案儲存在正確的位置時，才會顯示腳本或函數的說明主題。 因此，包含安裝 PowerShell 的指示，或儲存或安裝腳本或函式說明主題中的腳本或函式，並不會很有用。 相反地，請在您用來散發腳本或函式的檔中包含任何安裝指示。

## <a name="see-also"></a>另請參閱

[撰寫以批註為基礎的說明主題](./writing-comment-based-help-topics.md)
