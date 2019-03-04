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
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="9eb89-102">Cmdlet 程式碼中的屬性</span><span class="sxs-lookup"><span data-stu-id="9eb89-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="9eb89-103">若要使用 Windows PowerShell 所提供的一般功能，類別和 cmdlet 程式碼中定義的公用屬性裝飾屬性。</span><span class="sxs-lookup"><span data-stu-id="9eb89-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="9eb89-104">例如，下列類別定義使用 Cmdlet 屬性來識別在其中的 Microsoft.NET Framework 類別**Get-proc** cmdlet 實作。</span><span class="sxs-lookup"><span data-stu-id="9eb89-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="9eb89-105">(這個指令程式使用本文件的範例，類似於`Get-Process`Windows PowerShell 所提供的指令程式。)</span><span class="sxs-lookup"><span data-stu-id="9eb89-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="9eb89-106">這些屬性會被視為中繼資料，因為它們的實作是不同於 cmdlet 程式碼實作。</span><span class="sxs-lookup"><span data-stu-id="9eb89-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="9eb89-107">時，Windows PowerShell 執行階段中執行該 cmdlet，它會辨識的屬性，並針對每個屬性，然後執行適當動作。</span><span class="sxs-lookup"><span data-stu-id="9eb89-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="9eb89-108">雖然您可能想要實作您自己的版本，這些屬性所提供的功能，是很好的 cmdlet 的設計會使用這些常見的功能。</span><span class="sxs-lookup"><span data-stu-id="9eb89-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="9eb89-109">如需有關可以在您的 cmdlet 中宣告的不同屬性的詳細資訊，請參閱[屬性類型](./attribute-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9eb89-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9eb89-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9eb89-110">See Also</span></span>

[<span data-ttu-id="9eb89-111">屬性類型</span><span class="sxs-lookup"><span data-stu-id="9eb89-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="9eb89-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9eb89-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
