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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067989"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>如何建立 Windows PowerShell 嵌入式管理單元

Windows PowerShell 嵌入式管理單元提供一個機制向 shell 中，因此擴充功能的命令介面中的 cmdlet 和其他 Windows PowerShell 提供者的集合。 Windows PowerShell 嵌入式管理單元可以登錄所有 cmdlet 和提供者中的單一組件，或它可以都註冊特定的 cmdlet 與提供者清單。

就像其他作業系統，其方式是，應該在受保護的目錄中，安裝嵌入式管理單元的組件。 否則，惡意使用者可以使用不安全的程式碼取代組件。

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell 嵌入式管理單元類別

所有 Windows PowerShell 嵌入式管理單元類別都衍生自[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)或是[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)類別。

## <a name="examples"></a>範例

[撰寫 Windows PowerShell 嵌入式管理單元](./writing-a-windows-powershell-snap-in.md):此範例示範如何建立一個嵌入式管理單元，可用來註冊組件中的所有 cmdlet 和提供者。

[撰寫自訂的 Windows PowerShell 嵌入式管理單元](./writing-a-custom-windows-powershell-snap-in.md):此範例示範如何建立自訂嵌入式管理單元用來註冊單一組件中的一組特定的 cmdlet 與提供者可能會或可能不存在。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[註冊 Cmdlet](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
