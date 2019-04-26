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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068601"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="8dc45-102">Cmdlet 屬性</span><span class="sxs-lookup"><span data-stu-id="8dc45-102">Cmdlet Attributes</span></span>

<span data-ttu-id="8dc45-103">Windows PowerShell 會定義數個屬性，可用來將通用功能加入您的 cmdlet，而不需要實作自己的程式碼中的該功能。</span><span class="sxs-lookup"><span data-stu-id="8dc45-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="8dc45-104">這包括 Cmdlet 屬性，可識別 cmdlet 類別，OutputType 屬性，指定指令程式，識別為 cmdlet 的公用屬性的參數屬性所傳回的.NET Framework 型別為 Microsoft.NET Framework 類別參數等等。</span><span class="sxs-lookup"><span data-stu-id="8dc45-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8dc45-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="8dc45-105">In This Section</span></span>

<span data-ttu-id="8dc45-106">[Cmdlet 程式碼中的屬性](./attributes-in-cmdlet-code.md)描述 cmdlet 程式碼中使用屬性的好處。</span><span class="sxs-lookup"><span data-stu-id="8dc45-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="8dc45-107">[屬性型別](./attribute-types.md)描述可以裝飾 cmdlet 類別的不同屬性。</span><span class="sxs-lookup"><span data-stu-id="8dc45-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="8dc45-108">[別名屬性宣告](./alias-attribute-declaration.md)描述如何定義 cmdlet 參數名稱的別名。</span><span class="sxs-lookup"><span data-stu-id="8dc45-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="8dc45-109">[Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)描述如何為 cmdlet 定義.NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="8dc45-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="8dc45-110">[認證屬性宣告](./credential-attribute-declaration.md)描述如何將轉換成的字串輸入的支援加入[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)物件。</span><span class="sxs-lookup"><span data-stu-id="8dc45-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="8dc45-111">[OutputType 屬性宣告](./outputtype-attribute-declaration.md)描述如何指定 cmdlet 所傳回的.NET Framework 型別。</span><span class="sxs-lookup"><span data-stu-id="8dc45-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="8dc45-112">[參數屬性宣告](./parameter-attribute-declaration.md)描述如何定義 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="8dc45-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="8dc45-113">[ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)描述如何定義允許參數的引數數目。</span><span class="sxs-lookup"><span data-stu-id="8dc45-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="8dc45-114">[ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)描述如何定義參數引數的長度 （以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="8dc45-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="8dc45-115">[ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)描述如何定義參數的引數的有效模式。</span><span class="sxs-lookup"><span data-stu-id="8dc45-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="8dc45-116">[ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)描述如何定義參數的引數的有效範圍。</span><span class="sxs-lookup"><span data-stu-id="8dc45-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="8dc45-117">[ValidateSet 屬性宣告](./validateset-attribute-declaration.md)描述如何定義參數的引數的可能值。</span><span class="sxs-lookup"><span data-stu-id="8dc45-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="8dc45-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="8dc45-118">Reference</span></span>

[<span data-ttu-id="8dc45-119">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8dc45-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
