---
title: Cmdlet 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068601"
---
# <a name="cmdlet-attributes"></a>Cmdlet 屬性

Windows PowerShell 會定義數個屬性，可用來將通用功能加入您的 cmdlet，而不需要實作自己的程式碼中的該功能。 這包括 Cmdlet 屬性，可識別 cmdlet 類別，OutputType 屬性，指定指令程式，識別為 cmdlet 的公用屬性的參數屬性所傳回的.NET Framework 型別為 Microsoft.NET Framework 類別參數等等。

## <a name="in-this-section"></a>在本節中

[Cmdlet 程式碼中的屬性](./attributes-in-cmdlet-code.md)描述 cmdlet 程式碼中使用屬性的好處。

[屬性型別](./attribute-types.md)描述可以裝飾 cmdlet 類別的不同屬性。

[別名屬性宣告](./alias-attribute-declaration.md)描述如何定義 cmdlet 參數名稱的別名。

[Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)描述如何為 cmdlet 定義.NET Framework 類別。

[認證屬性宣告](./credential-attribute-declaration.md)描述如何將轉換成的字串輸入的支援加入[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)物件。

[OutputType 屬性宣告](./outputtype-attribute-declaration.md)描述如何指定 cmdlet 所傳回的.NET Framework 型別。

[參數屬性宣告](./parameter-attribute-declaration.md)描述如何定義 cmdlet 的參數。

[ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)描述如何定義允許參數的引數數目。

[ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)描述如何定義參數引數的長度 （以字元為單位）。

[ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)描述如何定義參數的引數的有效模式。

[ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)描述如何定義參數的引數的有效範圍。

[ValidateSet 屬性宣告](./validateset-attribute-declaration.md)描述如何定義參數的引數的可能值。

## <a name="reference"></a>參考資料

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
