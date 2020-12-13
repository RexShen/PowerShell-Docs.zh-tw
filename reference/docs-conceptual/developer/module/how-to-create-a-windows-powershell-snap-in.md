---
ms.date: 09/13/2016
ms.topic: reference
title: 如何建立 Windows PowerShell 嵌入式管理單元
description: 如何建立 Windows PowerShell 嵌入式管理單元
ms.openlocfilehash: 29394ebcd2f7c4a547aabcb88685ff494b2c381d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657277"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="1f59a-103">如何建立 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="1f59a-103">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="1f59a-104">Windows PowerShell 的嵌入式管理單元提供了一種機制，可讓您利用 shell 來註冊 Cmdlet 組和另一個 Windows PowerShell 提供者，進而擴充 shell 的功能。</span><span class="sxs-lookup"><span data-stu-id="1f59a-104">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="1f59a-105">Windows PowerShell 嵌入式管理單元可以在單一元件中註冊所有的 Cmdlet 和提供者，也可以註冊特定的 Cmdlet 和提供者清單。</span><span class="sxs-lookup"><span data-stu-id="1f59a-105">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="1f59a-106">嵌入式管理單元元件應該安裝在受保護的目錄中，就如同其他作業系統一樣。</span><span class="sxs-lookup"><span data-stu-id="1f59a-106">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="1f59a-107">否則，惡意使用者可以將元件取代為 unsafe 程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f59a-107">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="1f59a-108">Windows PowerShell 嵌入式管理單元類別</span><span class="sxs-lookup"><span data-stu-id="1f59a-108">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="1f59a-109">所有 Windows PowerShell 嵌入式管理單元類別都是衍生自 [PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) 或 [Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 類別的類別。</span><span class="sxs-lookup"><span data-stu-id="1f59a-109">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="1f59a-110">範例</span><span class="sxs-lookup"><span data-stu-id="1f59a-110">Examples</span></span>

<span data-ttu-id="1f59a-111">[撰寫 Windows PowerShell 嵌入式管理](./writing-a-windows-powershell-snap-in.md)單元：此範例顯示如何建立用來在元件中註冊所有 Cmdlet 和提供者的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="1f59a-111">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="1f59a-112">[撰寫自訂 Windows PowerShell 嵌入式管理](./writing-a-custom-windows-powershell-snap-in.md)單元：這個範例示範如何建立自訂嵌入式管理單元，用來註冊一組可能或可能不存在於單一元件中的特定 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="1f59a-112">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f59a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f59a-113">See Also</span></span>

[<span data-ttu-id="1f59a-114">PSSnapIn。</span><span class="sxs-lookup"><span data-stu-id="1f59a-114">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="1f59a-115">Custompssnapin。</span><span class="sxs-lookup"><span data-stu-id="1f59a-115">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="1f59a-116">註冊 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1f59a-116">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="1f59a-117">Windows PowerShell 殼層 SDK</span><span class="sxs-lookup"><span data-stu-id="1f59a-117">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
