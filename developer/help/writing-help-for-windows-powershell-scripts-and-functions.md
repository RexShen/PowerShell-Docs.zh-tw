---
title: 撰寫 PowerShell 指令碼和函式的說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083105"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>撰寫 PowerShell 指令碼和函式的說明

PowerShell 指令碼和函式都應該詳細記錄時它們會與其他人共用。
`Get-Help` Cmdlet 會顯示指令碼和函式的 [說明] 主題相同的格式與顯示的 cmdlet 和所有說明`Get-Help`參數作用於指令碼和函式的 [說明] 主題。

PowerShell 指令碼可以包括有關指令碼的說明主題以及有關每個函式的說明主題，指令碼中。
共用獨立指令碼的函式可以包含它們自己的 [說明] 主題。

本文件說明的格式和的 [說明] 主題的正確位置，並建議讓內容的指導方針。

## <a name="types-of-script-and-function-help"></a>類型的指令碼和函式的說明

### <a name="comment-based-help"></a>註解型說明
「 說明 」 主題所描述的指令碼或函式可以實作為一組內的指令碼或函式的註解。
在指令碼中撰寫註解型說明的指令碼和函式，請特別注意規則放置註解型說明。
位置會決定是否`Get-Help`cmdlet 說明主題將與相關聯的指令碼或函式。
如需有關如何撰寫註解式說明主題的詳細資訊，請參閱[about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。

### <a name="xml-based-command-help"></a>以 XML 為基礎的命令說明
描述指令碼或函式的 [說明] 主題可以實作中使用的命令說明結構描述的 XML 檔案。
若要關聯的 XML 檔案中的指令碼或函式，使用`ExternalHelp`註解關鍵字後面的路徑和名稱的 XML 檔案。

當`ExternalHelp`關鍵字，則其優先順序高於註解型說明註解，即使`Get-Help`找不到符合的值的說明檔`ExternalHelp`關鍵字。

### <a name="online-help"></a>線上說明
您可以在網際網路上張貼您的說明主題，並再直接`Get-Help`開啟主題。
如需有關如何撰寫註解式說明主題的詳細資訊，請參閱[支援線上說明](../module/supporting-online-help.md)。

沒有概念性 （「 關於 」） 主題中的指令碼和函式的建立的方法進行寫入。
不過，您可以張貼網際網路清單上的概念性主題的主題，以及其 Url 命令的說明主題的相關連結 區段中。

## <a name="content-considerations-for-script-and-function-help"></a>說明內容的指令碼和函式的考量

- 如果您正在撰寫非常簡短的 [說明] 主題，使用只有幾個可用的命令說明部分，請務必包含指令碼或函式參數的清楚描述。 也包含一或兩個範例命令範例 > 一節中，即使您決定省略範例的描述。

- 在所有的描述，請參閱命令的指令碼或函式。 這項資訊可協助使用者了解並管理命令。

  比方說，下列的詳細的描述狀態的新主題的命令是指令碼。 這會提醒使用者他們需要執行它時指定的路徑和完整名稱。

  > 「 新增主題指令碼會建立在輸入檔...空白的觀念性主題，每個主題名稱 」

  下列的詳細的描述指出`Disable-PSRemoting`是函式。 當工作階段包含多個具有相同的名稱，其中有些可能會被隱藏命令具有較高優先順序的命令，這項資訊是使用者特別有用。

  > `Disable-PSRemoting`函式會停用本機電腦上的所有工作階段設定...

- 在指令碼說明主題，說明如何使用指令碼整體。 如果您也在指令碼中撰寫函式的說明主題，提及您的指令碼說明主題中的函式，並包含在指令碼的 說明 主題的相關連結 區段中的函式的 說明 主題的參考。 相反地，在指令碼函式時，說明函式的 [說明] 主題中的函式中的指令碼，並可能會用它獨立所扮演的角色。 然後列出指令碼說明主題中的函式的 說明 主題的相關連結 區段。

- 在撰寫指令碼說明主題的範例，請務必範例命令中包含的指令碼檔案的路徑。 這會提醒使用者，他們必須指定路徑明確，即使指令碼是在目前的目錄。

- 在函式說明主題中，提醒函式只存在於目前工作階段的使用者，而若要使用它在其他工作階段，它們需要加入它，或將它加入 PowerShell 設定檔。

- `Get-Help` 顯示說明主題的指令碼或函式的指令碼檔案和說明主題檔會儲存在正確的位置時，才。 因此，最好不包含安裝 PowerShell，或儲存安裝指令碼或函式的說明主題中的指令碼或函式的相關指示。 相反地，您使用發佈的指令碼或函式的文件中包含的任何安裝指示。

## <a name="see-also"></a>另請參閱

 [指令碼和函式撰寫 XML 為基礎的說明主題](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [撰寫 XML 為基礎的說明主題的命令](./writing-xml-based-help-topics-for-commands.md)

 [撰寫註解式說明主題](./writing-comment-based-help-topics.md)
