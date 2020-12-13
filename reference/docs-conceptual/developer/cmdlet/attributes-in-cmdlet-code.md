---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 程式碼中的屬性
description: Cmdlet 程式碼中的屬性
ms.openlocfilehash: 296bb8bcb06ef660e97dc792d1ecf596cc7c2930
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653649"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet 程式碼中的屬性

若要使用 Windows PowerShell 所提供的一般功能，Cmdlet 程式碼中定義的類別和公用屬性會以屬性裝飾。 例如，下列類別定義會使用 Cmdlet 屬性來識別要在其中執行 **Proc** Cmdlet 的 Microsoft .NET Framework 類別。  (使用此 Cmdlet 作為本檔中的範例，類似于 Windows PowerShell 所提供的 `Get-Process` Cmdlet。 ) 

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

這些屬性會視為中繼資料，因為它們的執行與 Cmdlet 程式碼的執行不同。 當 Windows PowerShell 執行時間執行 Cmdlet 時，它會辨識屬性，然後針對每個屬性執行適當的動作。

雖然您可能會想要執行這些屬性所提供的自有功能版本，但良好的 Cmdlet 設計會使用這些常用功能。

如需可在 Cmdlet 中宣告之不同屬性的詳細資訊，請參閱 [屬性類型](./attribute-types.md)。

## <a name="see-also"></a>另請參閱

[屬性類型](./attribute-types.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
