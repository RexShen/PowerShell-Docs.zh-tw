---
ms.date: 09/13/2016
ms.topic: reference
title: 在 Cmdlet 內叫用 Cmdlet 與指令碼
description: 在 Cmdlet 內叫用 Cmdlet 與指令碼
ms.openlocfilehash: 246c61661f2d290e7e7ac62a8ad303b05bdc7582
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652639"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>在 Cmdlet 內叫用 Cmdlet 與指令碼

Cmdlet 可以從 Cmdlet 的輸入處理方法中叫用其他 Cmdlet 和腳本。 這可讓您將現有 Cmdlet 和腳本的功能新增至您的 Cmdlet，而不需要重寫程式碼。

## <a name="the-invoke-method"></a>Invoke 方法

所有 Cmdlet 都可以呼叫 BeginProcessing 來叫用現有的 Cmdlet，方法是從 Cmdlet 所覆寫的輸入處理方法（例如， [ ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)）中叫[用方法。](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 不過，您只能叫用直接衍生自 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 類別的 Cmdlet。 您無法叫用衍生自 [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 類別的 Cmdlet。

System.servicemodel. [Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 方法具有下列變體。

（ [Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant）會叫用 Cmdlet 物件，並傳回 "T" 類型物件的集合。

Emumerator 叫[用此變異](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)會叫用 Cmdlet 物件，並傳回強型別的。 此變數可讓使用者使用集合中的物件來執行自訂作業。

## <a name="examples"></a>範例

|範例|描述|
|-------------|-----------------|
|[在 Cmdlet 中叫用 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|此範例顯示如何從另一個 Cmdlet 中叫用 Cmdlet。|
|[在 Cmdlet 中叫用腳本](./how-to-invoke-scripts-within-a-cmdlet.md)|此範例示範如何從另一個 Cmdlet 中叫用提供給 Cmdlet 的腳本。|

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
