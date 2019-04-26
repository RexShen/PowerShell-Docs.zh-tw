---
title: 叫用 Cmdlet 與 Cmdlet 中的指令碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067666"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>在 Cmdlet 內叫用 Cmdlet 與指令碼

其他的 cmdlet 和指令碼的位置內的輸入處理方法的 cmdlet，可以叫用 cmdlet。 這可讓您將現有的 cmdlet 與指令碼的功能新增至 cmdlet，而不必重寫程式碼。

## <a name="the-invoke-method"></a>叫用方法

所有的指令程式可以藉由呼叫項目叫用現有的 cmdlet [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法內的輸入處理方法，例如[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)，也就是覆寫 cmdlet。 不過，您可以叫用直接衍生自這些指令程式[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別。 您無法叫用的 cmdlet，衍生自[System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別。

[System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法有下列的變化。

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此變異會叫用 cmdlet 物件，並傳回"T"type 物件的集合。

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此變異會叫用 cmdlet 物件，並傳回強型別的 emumerator。 此變數可讓使用者使用集合中的物件，來執行自訂的作業。

## <a name="examples"></a>範例

|範例|描述|
|-------------|-----------------|
|[叫用 Cmdlet 中的 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|此範例示範如何叫用另一個 cmdlet 中的 cmdlet。|
|[叫用的指令碼中的 Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|此範例示範如何叫用的指令碼，提供給從中另一個 cmdlet 的 cmdlet。|

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
