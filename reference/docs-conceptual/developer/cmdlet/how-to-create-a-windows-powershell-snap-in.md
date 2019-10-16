---
title: 如何建立 Windows PowerShell 嵌入式管理單元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364427"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="e9c04-102">如何建立 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="e9c04-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="e9c04-103">Windows PowerShell 嵌入式管理單元提供一種機制，用來向 shell 註冊一組 Cmdlet 和另一個 Windows PowerShell 提供者，因此擴充了命令介面的功能。</span><span class="sxs-lookup"><span data-stu-id="e9c04-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="e9c04-104">Windows PowerShell 嵌入式管理單元可以在單一元件中註冊所有 Cmdlet 和提供者，也可以註冊特定的 Cmdlet 和提供者清單。</span><span class="sxs-lookup"><span data-stu-id="e9c04-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="e9c04-105">嵌入式管理單元元件應該安裝在受保護的目錄中，就像其他作業系統一樣。</span><span class="sxs-lookup"><span data-stu-id="e9c04-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="e9c04-106">否則，惡意使用者可以用不安全的程式碼取代元件。</span><span class="sxs-lookup"><span data-stu-id="e9c04-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="e9c04-107">Windows PowerShell 嵌入式管理單元類別</span><span class="sxs-lookup"><span data-stu-id="e9c04-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="e9c04-108">所有的 Windows PowerShell 嵌入式管理單元類別都是衍生自[PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)或[Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)類別的。</span><span class="sxs-lookup"><span data-stu-id="e9c04-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="e9c04-109">範例</span><span class="sxs-lookup"><span data-stu-id="e9c04-109">Examples</span></span>

<span data-ttu-id="e9c04-110">[撰寫 Windows PowerShell 嵌入式管理單元](./writing-a-windows-powershell-snap-in.md)：這個範例示範如何建立一個嵌入式管理單元，用來在元件中註冊所有的 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="e9c04-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="e9c04-111">[撰寫自訂的 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md)：這個範例示範如何建立自訂嵌入式管理單元，用來註冊一組不一定存在於單一元件中的特定 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="e9c04-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9c04-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9c04-112">See Also</span></span>

[<span data-ttu-id="e9c04-113">PSSnapIn。</span><span class="sxs-lookup"><span data-stu-id="e9c04-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="e9c04-114">Custompssnapin。</span><span class="sxs-lookup"><span data-stu-id="e9c04-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="e9c04-115">註冊 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e9c04-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="e9c04-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="e9c04-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
