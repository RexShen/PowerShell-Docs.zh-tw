---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 屬性
description: Cmdlet 屬性
ms.openlocfilehash: 6a106f33cb34c6c33b88a981815543bc9af4e4ba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653517"
---
# <a name="cmdlet-attributes"></a>Cmdlet 屬性

Windows PowerShell 定義數個屬性，可讓您用來將通用功能新增至 Cmdlet，而不需要在自己的程式碼中執行該功能。 這包括 Cmdlet 屬性，該屬性會將 Microsoft .NET Framework 類別識別為 Cmdlet 類別、指定 Cmdlet 所傳回之 .NET Framework 類型的 OutputType 屬性、將公用屬性識別為 Cmdlet 參數的參數屬性等等。

## <a name="in-this-section"></a>本節內容

[Cmdlet 程式碼中的屬性](./attributes-in-cmdlet-code.md) 描述在 Cmdlet 程式碼中使用屬性的優點。

[屬性類型](./attribute-types.md) 描述可裝飾 Cmdlet 類別的不同屬性。

[Alias 屬性聲明](./alias-attribute-declaration.md) 說明如何定義 Cmdlet 參數名稱的別名。

[Cmdlet 屬性聲明](./cmdlet-attribute-declaration.md) 說明如何將 .NET Framework 類別定義為 Cmdlet。

[Credential 屬性聲明](./credential-attribute-declaration.md)說明如何將將字串輸入轉換為[system.string 物件的支援。](/dotnet/api/System.Management.Automation.PSCredential)

[OutputType 屬性](./outputtype-attribute-declaration.md) 宣告說明如何指定 Cmdlet 所傳回的 .NET Framework 類型。

[Parameter 屬性聲明](./parameter-attribute-declaration.md) 說明如何定義 Cmdlet 的參數。

[ValidateCount 屬性](./validatecount-attribute-declaration.md) 宣告描述如何定義參數允許的引數數目。

[ValidateLength 屬性](./validatelength-attribute-declaration.md) 宣告描述如何定義參數引數) 的字元 (長度。

[ValidatePattern 屬性](./validatepattern-attribute-declaration.md) 宣告描述如何定義參數引數的有效模式。

[ValidateRange 屬性](./validaterange-attribute-declaration.md) 宣告描述如何定義參數引數的有效範圍。

[ValidateSet 屬性](./validateset-attribute-declaration.md) 宣告描述如何定義參數引數的可能值。

## <a name="reference"></a>參考

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
