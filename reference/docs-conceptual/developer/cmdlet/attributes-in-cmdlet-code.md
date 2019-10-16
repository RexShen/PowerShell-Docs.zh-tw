---
title: Cmdlet 程式碼中的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369997"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet 程式碼中的屬性

若要使用 Windows PowerShell 所提供的一般功能，在 Cmdlet 程式碼中定義的類別和公用屬性會以屬性裝飾。 例如，下列類別定義會使用 Cmdlet 屬性，來識別用來實作為**Get-Proc** Cmdlet 的 Microsoft .NET Framework 類別。 （此 Cmdlet 是本檔中的範例，類似于 Windows PowerShell 所提供的 `Get-Process` Cmdlet）。

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
