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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853784"
---
# <a name="attributes-in-cmdlet-code"></a>Cmdlet 程式碼中的屬性

若要使用 Windows PowerShell 所提供的一般功能，類別和 cmdlet 程式碼中定義的公用屬性裝飾屬性。 例如，下列類別定義使用 Cmdlet 屬性來識別在其中的 Microsoft.NET Framework 類別**Get-proc** cmdlet 實作。 (這個指令程式使用本文件的範例，類似於`Get-Process`Windows PowerShell 所提供的指令程式。)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

這些屬性會被視為中繼資料，因為它們的實作是不同於 cmdlet 程式碼實作。 時，Windows PowerShell 執行階段中執行該 cmdlet，它會辨識的屬性，並針對每個屬性，然後執行適當動作。

雖然您可能想要實作您自己的版本，這些屬性所提供的功能，是很好的 cmdlet 的設計會使用這些常見的功能。

如需有關可以在您的 cmdlet 中宣告的不同屬性的詳細資訊，請參閱[屬性類型](./attribute-types.md)。

## <a name="see-also"></a>另請參閱

[屬性類型](./attribute-types.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
