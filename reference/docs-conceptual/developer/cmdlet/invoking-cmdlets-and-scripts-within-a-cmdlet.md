---
title: 在 Cmdlet 內叫用 Cmdlet 和腳本 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 3d5f76242c02763c41b81215bbb031e19869066a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786572"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>在 Cmdlet 內叫用 Cmdlet 與指令碼

Cmdlet 可以從 Cmdlet 的輸入處理方法中叫用其他 Cmdlet 和腳本。 這可讓您將現有 Cmdlet 和腳本的功能新增至您的 Cmdlet，而不需要重寫程式碼。

## <a name="the-invoke-method"></a>Invoke 方法

所有 Cmdlet 都可以叫用現有的 Cmdlet，方法是從輸入處理方法（例如[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)）中的指令程式所覆寫的方法中，呼叫[。](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 不過，您只能叫用直接衍生自[system.object](/dotnet/api/System.Management.Automation.Cmdlet)類別的 Cmdlet。 您不能叫用衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別的 Cmdlet。

[[調用] *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法具有下列變體。

[。叫用此變](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)體會叫用 Cmdlet 物件，並傳回 "T" 類型物件的集合。

[。叫用此變](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)體會叫用 Cmdlet 物件，並傳回強型別 emumerator。 這個變異數可讓使用者使用集合中的物件來執行自訂作業。

## <a name="examples"></a>範例

|範例|描述|
|-------------|-----------------|
|[叫用 Cmdlet 中的 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|這個範例示範如何從另一個 Cmdlet 中叫用 Cmdlet。|
|[在 Cmdlet 內叫用腳本](./how-to-invoke-scripts-within-a-cmdlet.md)|這個範例示範如何從另一個 Cmdlet 叫用提供給 Cmdlet 的腳本。|

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
