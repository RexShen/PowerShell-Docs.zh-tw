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
# <a name="cmdlet-attributes"></a><span data-ttu-id="a7eab-103">Cmdlet 屬性</span><span class="sxs-lookup"><span data-stu-id="a7eab-103">Cmdlet Attributes</span></span>

<span data-ttu-id="a7eab-104">Windows PowerShell 定義數個屬性，可讓您用來將通用功能新增至 Cmdlet，而不需要在自己的程式碼中執行該功能。</span><span class="sxs-lookup"><span data-stu-id="a7eab-104">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="a7eab-105">這包括 Cmdlet 屬性，該屬性會將 Microsoft .NET Framework 類別識別為 Cmdlet 類別、指定 Cmdlet 所傳回之 .NET Framework 類型的 OutputType 屬性、將公用屬性識別為 Cmdlet 參數的參數屬性等等。</span><span class="sxs-lookup"><span data-stu-id="a7eab-105">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a7eab-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="a7eab-106">In This Section</span></span>

<span data-ttu-id="a7eab-107">[Cmdlet 程式碼中的屬性](./attributes-in-cmdlet-code.md) 描述在 Cmdlet 程式碼中使用屬性的優點。</span><span class="sxs-lookup"><span data-stu-id="a7eab-107">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="a7eab-108">[屬性類型](./attribute-types.md) 描述可裝飾 Cmdlet 類別的不同屬性。</span><span class="sxs-lookup"><span data-stu-id="a7eab-108">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="a7eab-109">[Alias 屬性聲明](./alias-attribute-declaration.md) 說明如何定義 Cmdlet 參數名稱的別名。</span><span class="sxs-lookup"><span data-stu-id="a7eab-109">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="a7eab-110">[Cmdlet 屬性聲明](./cmdlet-attribute-declaration.md) 說明如何將 .NET Framework 類別定義為 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a7eab-110">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="a7eab-111">[Credential 屬性聲明](./credential-attribute-declaration.md)說明如何將將字串輸入轉換為[system.string 物件的支援。](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="a7eab-111">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="a7eab-112">[OutputType 屬性](./outputtype-attribute-declaration.md) 宣告說明如何指定 Cmdlet 所傳回的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="a7eab-112">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="a7eab-113">[Parameter 屬性聲明](./parameter-attribute-declaration.md) 說明如何定義 Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="a7eab-113">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="a7eab-114">[ValidateCount 屬性](./validatecount-attribute-declaration.md) 宣告描述如何定義參數允許的引數數目。</span><span class="sxs-lookup"><span data-stu-id="a7eab-114">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="a7eab-115">[ValidateLength 屬性](./validatelength-attribute-declaration.md) 宣告描述如何定義參數引數) 的字元 (長度。</span><span class="sxs-lookup"><span data-stu-id="a7eab-115">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="a7eab-116">[ValidatePattern 屬性](./validatepattern-attribute-declaration.md) 宣告描述如何定義參數引數的有效模式。</span><span class="sxs-lookup"><span data-stu-id="a7eab-116">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="a7eab-117">[ValidateRange 屬性](./validaterange-attribute-declaration.md) 宣告描述如何定義參數引數的有效範圍。</span><span class="sxs-lookup"><span data-stu-id="a7eab-117">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="a7eab-118">[ValidateSet 屬性](./validateset-attribute-declaration.md) 宣告描述如何定義參數引數的可能值。</span><span class="sxs-lookup"><span data-stu-id="a7eab-118">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="a7eab-119">參考</span><span class="sxs-lookup"><span data-stu-id="a7eab-119">Reference</span></span>

[<span data-ttu-id="a7eab-120">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a7eab-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
