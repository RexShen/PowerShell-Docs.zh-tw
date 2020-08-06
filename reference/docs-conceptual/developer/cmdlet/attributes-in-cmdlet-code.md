---
title: Cmdlet 程式碼中的屬性 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1f92e329d304754d5596cef0c95dc597aca3a538
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774910"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet 程式碼中的屬性

若要使用 Windows PowerShell 所提供的一般功能，在 Cmdlet 程式碼中定義的類別和公用屬性會以屬性裝飾。 例如，下列類別定義會使用 Cmdlet 屬性，來識別用來實作為**Get-Proc** Cmdlet 的 Microsoft .NET Framework 類別。  (此 Cmdlet 是用來做為本檔中的範例，類似于 `Get-Process` Windows PowerShell 所提供的 Cmdlet。 ) 

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

這些屬性會被視為中繼資料，因為它們的實作為獨立于 Cmdlet 程式碼的執行。 當 Windows PowerShell 執行時間執行 Cmdlet 時，它會辨識屬性，然後針對每個屬性執行適當的動作。

雖然您可能會想要執行這些屬性所提供的專屬功能版本，但良好的 Cmdlet 設計會使用這些常見功能。

如需可在 Cmdlet 中宣告之不同屬性的詳細資訊，請參閱[屬性類型](./attribute-types.md)。

## <a name="see-also"></a>另請參閱

[屬性類型](./attribute-types.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
