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
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="7769f-102">Cmdlet 程式碼中的屬性</span><span class="sxs-lookup"><span data-stu-id="7769f-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="7769f-103">若要使用 Windows PowerShell 所提供的一般功能，在 Cmdlet 程式碼中定義的類別和公用屬性會以屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="7769f-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="7769f-104">例如，下列類別定義會使用 Cmdlet 屬性，來識別用來實作為**Get-Proc** Cmdlet 的 Microsoft .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="7769f-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="7769f-105"> (此 Cmdlet 是用來做為本檔中的範例，類似于 `Get-Process` Windows PowerShell 所提供的 Cmdlet。 ) </span><span class="sxs-lookup"><span data-stu-id="7769f-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="7769f-106">這些屬性會被視為中繼資料，因為它們的實作為獨立于 Cmdlet 程式碼的執行。</span><span class="sxs-lookup"><span data-stu-id="7769f-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="7769f-107">當 Windows PowerShell 執行時間執行 Cmdlet 時，它會辨識屬性，然後針對每個屬性執行適當的動作。</span><span class="sxs-lookup"><span data-stu-id="7769f-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="7769f-108">雖然您可能會想要執行這些屬性所提供的專屬功能版本，但良好的 Cmdlet 設計會使用這些常見功能。</span><span class="sxs-lookup"><span data-stu-id="7769f-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="7769f-109">如需可在 Cmdlet 中宣告之不同屬性的詳細資訊，請參閱[屬性類型](./attribute-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7769f-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7769f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7769f-110">See Also</span></span>

[<span data-ttu-id="7769f-111">屬性類型</span><span class="sxs-lookup"><span data-stu-id="7769f-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="7769f-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7769f-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
