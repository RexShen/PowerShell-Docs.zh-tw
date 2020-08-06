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
# <a name="cmdlet-attributes"></a><span data-ttu-id="c8bdd-102">Cmdlet 屬性</span><span class="sxs-lookup"><span data-stu-id="c8bdd-102">Cmdlet Attributes</span></span>

<span data-ttu-id="c8bdd-103">Windows PowerShell 定義數個屬性，您可以用來將通用功能新增至您的 Cmdlet，而不需要在自己的程式碼中執行該功能。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="c8bdd-104">這包括將 Microsoft .NET Framework 類別識別為 Cmdlet 類別的 Cmdlet 屬性、指定 Cmdlet 所傳回之 .NET Framework 類型的 OutputType 屬性、將公用屬性識別為 Cmdlet 參數的參數屬性等等。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c8bdd-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="c8bdd-105">In This Section</span></span>

<span data-ttu-id="c8bdd-106">[Cmdlet 程式碼中的屬性](./attributes-in-cmdlet-code.md)說明在 Cmdlet 程式碼中使用屬性的優點。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="c8bdd-107">[屬性類型](./attribute-types.md)描述可以裝飾 Cmdlet 類別的不同屬性。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="c8bdd-108">[Alias 屬性](./alias-attribute-declaration.md)宣告說明如何定義 Cmdlet 參數名稱的別名。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="c8bdd-109">[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告說明如何將 .NET Framework 類別定義為 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="c8bdd-110">[Credential 屬性](./credential-attribute-declaration.md)宣告描述如何新增將字串輸入轉換成[system.web](/dotnet/api/System.Management.Automation.PSCredential)物件的支援。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="c8bdd-111">[OutputType 屬性](./outputtype-attribute-declaration.md)宣告說明如何指定 Cmdlet 所傳回的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="c8bdd-112">[參數屬性](./parameter-attribute-declaration.md)宣告說明如何定義 Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="c8bdd-113">[ValidateCount 屬性](./validatecount-attribute-declaration.md)宣告描述如何定義參數允許的引數數目。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="c8bdd-114">[ValidateLength 屬性](./validatelength-attribute-declaration.md)宣告描述如何定義參數引數的字元)  (長度。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="c8bdd-115">[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告描述如何定義參數引數的有效模式。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="c8bdd-116">[ValidateRange 屬性](./validaterange-attribute-declaration.md)宣告描述如何定義參數引數的有效範圍。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="c8bdd-117">[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告描述如何定義參數引數的可能值。</span><span class="sxs-lookup"><span data-stu-id="c8bdd-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="c8bdd-118">參考</span><span class="sxs-lookup"><span data-stu-id="c8bdd-118">Reference</span></span>

[<span data-ttu-id="c8bdd-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c8bdd-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
