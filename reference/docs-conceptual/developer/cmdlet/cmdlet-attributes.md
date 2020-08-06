---
title: Cmdlet 屬性 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.openlocfilehash: f22c2882fbe5b2f51ca5ea218b921192b0a7d41f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784515"
---
# <a name="cmdlet-attributes"></a>Cmdlet 屬性

Windows PowerShell 定義數個屬性，您可以用來將通用功能新增至您的 Cmdlet，而不需要在自己的程式碼中執行該功能。 這包括將 Microsoft .NET Framework 類別識別為 Cmdlet 類別的 Cmdlet 屬性、指定 Cmdlet 所傳回之 .NET Framework 類型的 OutputType 屬性、將公用屬性識別為 Cmdlet 參數的參數屬性等等。

## <a name="in-this-section"></a>本節內容

[Cmdlet 程式碼中的屬性](./attributes-in-cmdlet-code.md)說明在 Cmdlet 程式碼中使用屬性的優點。

[屬性類型](./attribute-types.md)描述可以裝飾 Cmdlet 類別的不同屬性。

[Alias 屬性](./alias-attribute-declaration.md)宣告說明如何定義 Cmdlet 參數名稱的別名。

[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告說明如何將 .NET Framework 類別定義為 Cmdlet。

[Credential 屬性](./credential-attribute-declaration.md)宣告描述如何新增將字串輸入轉換成[system.web](/dotnet/api/System.Management.Automation.PSCredential)物件的支援。

[OutputType 屬性](./outputtype-attribute-declaration.md)宣告說明如何指定 Cmdlet 所傳回的 .NET Framework 類型。

[參數屬性](./parameter-attribute-declaration.md)宣告說明如何定義 Cmdlet 的參數。

[ValidateCount 屬性](./validatecount-attribute-declaration.md)宣告描述如何定義參數允許的引數數目。

[ValidateLength 屬性](./validatelength-attribute-declaration.md)宣告描述如何定義參數引數的字元)  (長度。

[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告描述如何定義參數引數的有效模式。

[ValidateRange 屬性](./validaterange-attribute-declaration.md)宣告描述如何定義參數引數的有效範圍。

[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告描述如何定義參數引數的可能值。

## <a name="reference"></a>參考

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
