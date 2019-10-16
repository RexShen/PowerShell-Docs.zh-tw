---
title: Cmdlet 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369957"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="38db7-102">Cmdlet 屬性</span><span class="sxs-lookup"><span data-stu-id="38db7-102">Cmdlet Attributes</span></span>

<span data-ttu-id="38db7-103">Windows PowerShell 定義數個屬性，您可以用來將通用功能新增至您的 Cmdlet，而不需要在自己的程式碼中執行該功能。</span><span class="sxs-lookup"><span data-stu-id="38db7-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="38db7-104">這包括將 Microsoft .NET Framework 類別識別為 Cmdlet 類別的 Cmdlet 屬性、指定 Cmdlet 所傳回之 .NET Framework 類型的 OutputType 屬性，以及將公用屬性識別為 Cmdlet 的參數屬性參數等等。</span><span class="sxs-lookup"><span data-stu-id="38db7-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="38db7-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="38db7-105">In This Section</span></span>

<span data-ttu-id="38db7-106">[Cmdlet 程式碼中的屬性](./attributes-in-cmdlet-code.md)說明在 Cmdlet 程式碼中使用屬性的優點。</span><span class="sxs-lookup"><span data-stu-id="38db7-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="38db7-107">[屬性類型](./attribute-types.md)描述可以裝飾 Cmdlet 類別的不同屬性。</span><span class="sxs-lookup"><span data-stu-id="38db7-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="38db7-108">[Alias 屬性](./alias-attribute-declaration.md)宣告說明如何定義 Cmdlet 參數名稱的別名。</span><span class="sxs-lookup"><span data-stu-id="38db7-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="38db7-109">[Cmdlet 屬性](./cmdlet-attribute-declaration.md)宣告說明如何將 .NET Framework 類別定義為 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="38db7-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="38db7-110">[Credential 屬性](./credential-attribute-declaration.md)宣告描述如何新增將字串輸入轉換成[system.web](/dotnet/api/System.Management.Automation.PSCredential)物件的支援。</span><span class="sxs-lookup"><span data-stu-id="38db7-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="38db7-111">[OutputType 屬性](./outputtype-attribute-declaration.md)宣告說明如何指定 Cmdlet 所傳回的 .NET Framework 類型。</span><span class="sxs-lookup"><span data-stu-id="38db7-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="38db7-112">[參數屬性](./parameter-attribute-declaration.md)宣告說明如何定義 Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="38db7-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="38db7-113">[ValidateCount 屬性](./validatecount-attribute-declaration.md)宣告描述如何定義參數允許的引數數目。</span><span class="sxs-lookup"><span data-stu-id="38db7-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="38db7-114">[ValidateLength 屬性](./validatelength-attribute-declaration.md)宣告描述如何定義參數引數的長度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="38db7-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="38db7-115">[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告描述如何定義參數引數的有效模式。</span><span class="sxs-lookup"><span data-stu-id="38db7-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="38db7-116">[ValidateRange 屬性](./validaterange-attribute-declaration.md)宣告描述如何定義參數引數的有效範圍。</span><span class="sxs-lookup"><span data-stu-id="38db7-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="38db7-117">[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告描述如何定義參數引數的可能值。</span><span class="sxs-lookup"><span data-stu-id="38db7-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="38db7-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="38db7-118">Reference</span></span>

[<span data-ttu-id="38db7-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="38db7-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
