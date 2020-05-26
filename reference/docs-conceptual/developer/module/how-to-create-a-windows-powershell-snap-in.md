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
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811327"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>如何建立 Windows PowerShell 嵌入式管理單元

Windows PowerShell 嵌入式管理單元提供一種機制，用來向 shell 註冊一組 Cmdlet 和另一個 Windows PowerShell 提供者，因此擴充了命令介面的功能。 Windows PowerShell 嵌入式管理單元可以在單一元件中註冊所有 Cmdlet 和提供者，也可以註冊特定的 Cmdlet 和提供者清單。

嵌入式管理單元元件應該安裝在受保護的目錄中，就像其他作業系統一樣。 否則，惡意使用者可以用不安全的程式碼取代元件。

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell 嵌入式管理單元類別

所有的 Windows PowerShell 嵌入式管理單元類別都是衍生自[PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)或[Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)類別的。

## <a name="examples"></a>範例

[撰寫 Windows PowerShell 嵌入式管理單元](./writing-a-windows-powershell-snap-in.md)：這個範例示範如何建立一個嵌入式管理單元，用來在元件中註冊所有的 Cmdlet 和提供者。

[撰寫自訂的 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md)：這個範例示範如何建立自訂嵌入式管理單元，用來註冊一組不一定存在於單一元件中的特定 Cmdlet 和提供者。

## <a name="see-also"></a>另請參閱

[PSSnapIn。](/dotnet/api/System.Management.Automation.PSSnapIn)

[Custompssnapin。](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[註冊 Cmdlet](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
