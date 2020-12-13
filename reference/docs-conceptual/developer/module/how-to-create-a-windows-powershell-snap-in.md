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
# <a name="how-to-create-a-windows-powershell-snap-in"></a>如何建立 Windows PowerShell 嵌入式管理單元

Windows PowerShell 的嵌入式管理單元提供了一種機制，可讓您利用 shell 來註冊 Cmdlet 組和另一個 Windows PowerShell 提供者，進而擴充 shell 的功能。 Windows PowerShell 嵌入式管理單元可以在單一元件中註冊所有的 Cmdlet 和提供者，也可以註冊特定的 Cmdlet 和提供者清單。

嵌入式管理單元元件應該安裝在受保護的目錄中，就如同其他作業系統一樣。 否則，惡意使用者可以將元件取代為 unsafe 程式碼。

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell 嵌入式管理單元類別

所有 Windows PowerShell 嵌入式管理單元類別都是衍生自 [PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) 或 [Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 類別的類別。

## <a name="examples"></a>範例

[撰寫 Windows PowerShell 嵌入式管理](./writing-a-windows-powershell-snap-in.md)單元：此範例顯示如何建立用來在元件中註冊所有 Cmdlet 和提供者的嵌入式管理單元。

[撰寫自訂 Windows PowerShell 嵌入式管理](./writing-a-custom-windows-powershell-snap-in.md)單元：這個範例示範如何建立自訂嵌入式管理單元，用來註冊一組可能或可能不存在於單一元件中的特定 Cmdlet 和提供者。

## <a name="see-also"></a>另請參閱

[PSSnapIn。](/dotnet/api/System.Management.Automation.PSSnapIn)

[Custompssnapin。](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[註冊 Cmdlet](./registering-cmdlets.md)

[Windows PowerShell 殼層 SDK](../windows-powershell-reference.md)
