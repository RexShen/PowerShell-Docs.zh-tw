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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055932"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="5d7de-102">如何建立 Windows PowerShell 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="5d7de-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="5d7de-103">Windows PowerShell 嵌入式管理單元提供一個機制向 shell 中，因此擴充功能的命令介面中的 cmdlet 和其他 Windows PowerShell 提供者的集合。</span><span class="sxs-lookup"><span data-stu-id="5d7de-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="5d7de-104">Windows PowerShell 嵌入式管理單元可以登錄所有 cmdlet 和提供者中的單一組件，或它可以都註冊特定的 cmdlet 與提供者清單。</span><span class="sxs-lookup"><span data-stu-id="5d7de-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="5d7de-105">就像其他作業系統，其方式是，應該在受保護的目錄中，安裝嵌入式管理單元的組件。</span><span class="sxs-lookup"><span data-stu-id="5d7de-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="5d7de-106">否則，惡意使用者可以使用不安全的程式碼取代組件。</span><span class="sxs-lookup"><span data-stu-id="5d7de-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="5d7de-107">Windows PowerShell 嵌入式管理單元類別</span><span class="sxs-lookup"><span data-stu-id="5d7de-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="5d7de-108">所有 Windows PowerShell 嵌入式管理單元類別都衍生自[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)或是[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)類別。</span><span class="sxs-lookup"><span data-stu-id="5d7de-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="5d7de-109">範例</span><span class="sxs-lookup"><span data-stu-id="5d7de-109">Examples</span></span>

<span data-ttu-id="5d7de-110">[撰寫 Windows PowerShell 嵌入式管理單元](./writing-a-windows-powershell-snap-in.md):此範例示範如何建立一個嵌入式管理單元，可用來註冊組件中的所有 cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="5d7de-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="5d7de-111">[撰寫自訂的 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md):此範例示範如何建立自訂嵌入式管理單元用來註冊單一組件中的一組特定的 cmdlet 與提供者可能會或可能不存在。</span><span class="sxs-lookup"><span data-stu-id="5d7de-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d7de-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d7de-112">See Also</span></span>

[<span data-ttu-id="5d7de-113">System.Management.Automation.PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="5d7de-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="5d7de-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="5d7de-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="5d7de-115">註冊 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d7de-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="5d7de-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="5d7de-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
