---
title: 在 Cmdlet 參數支援萬用字元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862514"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>在 Cmdlet 參數中支援萬用字元

通常，您必須設計可執行的資源群組中，而不是針對單一資源的 cmdlet。 比方說，cmdlet 可能需要在有相同的名稱或延伸模組的資料存放區中找出所有檔案。 當您設計的 cmdlet，將會針對資源群組中的執行時，您便必須提供萬用字元的支援。

> [!NOTE]
> 使用萬用字元有時稱為*萬用字元*。

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>使用萬用字元的 Windows PowerShell Cmdlet

 許多 Windows PowerShell cmdlet 的參數值支援萬用字元。 例如，幾乎每個 cmdlet 可`Name`或`Path`參數支援萬用字元為這些參數。 (雖然大多數的 cmdlet 具有`Path`參數也有`LiteralPath`不支援萬用字元的參數。)下列命令會顯示如何將萬用字元使用返回其名稱中包含 Get 動詞命令的目前工作階段中的所有 cmdlet。

 **PS > get 命令 get-\***

## <a name="supported-wildcard-characters"></a>支援的萬用字元

Windows PowerShell 支援下列的萬用字元。

|萬用字元|描述|範例|相符項目|不符合|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|比對零或多個字元，從指定的位置開始|a*|，ag Apple||
|?|位於指定位置的相符項目 anycharacter|？ n|中，在|執行|
|[ ]|比對字元的範圍|[a-l]ook|書籍、 cook、 外觀|花了|
|[ ]|符合指定的字元|[bc]ook|書籍、 cook|尋找|

當您設計支援萬用字元的 cmdlet 時，允許的萬用字元的組合。 例如，下列命令會使用`Get-ChildItem`cmdlet 來擷取的所有.txt 檔案 c:\Techdocs 資料夾中，開頭為字母"a"到"l。"

**get-childitem c:\techdocs\\[a-l]\*.txt**

前一個命令會使用範圍萬用字元 **[a-l]** 來指定，檔案名稱應該是以開頭的字元"a"到"l。" 此命令接著會使用 * 萬用字元以.txt 為副檔名的檔案名稱的第一個字母之間的任何字元預留位置。

下列範例會使用範圍的萬用字元模式排除字母"d"，但包含從"a"到"f。 」 的所有其他字母

**get-childitem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>處理中萬用字元模式比對常值字元

如果您指定的萬用字元模式包含常值字元，做為逸出字元倒引號字元 （'）。 當您以程式設計方式指定常值字元時，使用單一的倒引號。 當您指定的命令提示字元的常值字元時，使用兩個反引號。 例如，下列模式包含必須純粹的兩個括號。

"John Smith \`[*']"（以程式設計方式指定）

"John Smith \` \`[*\`']"（在命令提示字元中指定）

此模式會比對"John Smith [行銷]"或"John Smith [開發]"。

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet 輸出和萬用字元

當 cmdlet 參數支援萬用字元時，則 cmdlet 作業通常會產生的陣列輸出。 有時候，它沒有意義支援輸出，因為使用者可能會一次使用單一項目陣列。 比方說，`Set-Location`指令程式支援的輸出，因為使用者設定的單一位置的陣列。 在此情況下，cmdlet 仍然支援萬用字元，但它會強制解析至單一位置。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern 類別](/dotnet/api/system.management.automation.wildcardpattern)
