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
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="a71a3-103">Cmdlet 程式碼中的屬性</span><span class="sxs-lookup"><span data-stu-id="a71a3-103">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="a71a3-104">若要使用 Windows PowerShell 所提供的一般功能，Cmdlet 程式碼中定義的類別和公用屬性會以屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="a71a3-104">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="a71a3-105">例如，下列類別定義會使用 Cmdlet 屬性來識別要在其中執行 **Proc** Cmdlet 的 Microsoft .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="a71a3-105">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="a71a3-106"> (使用此 Cmdlet 作為本檔中的範例，類似于 Windows PowerShell 所提供的 `Get-Process` Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="a71a3-106">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="a71a3-107">這些屬性會視為中繼資料，因為它們的執行與 Cmdlet 程式碼的執行不同。</span><span class="sxs-lookup"><span data-stu-id="a71a3-107">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="a71a3-108">當 Windows PowerShell 執行時間執行 Cmdlet 時，它會辨識屬性，然後針對每個屬性執行適當的動作。</span><span class="sxs-lookup"><span data-stu-id="a71a3-108">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="a71a3-109">雖然您可能會想要執行這些屬性所提供的自有功能版本，但良好的 Cmdlet 設計會使用這些常用功能。</span><span class="sxs-lookup"><span data-stu-id="a71a3-109">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="a71a3-110">如需可在 Cmdlet 中宣告之不同屬性的詳細資訊，請參閱 [屬性類型](./attribute-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a71a3-110">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a71a3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a71a3-111">See Also</span></span>

[<span data-ttu-id="a71a3-112">屬性類型</span><span class="sxs-lookup"><span data-stu-id="a71a3-112">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="a71a3-113">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a71a3-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
