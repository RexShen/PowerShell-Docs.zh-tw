---
ms.date: 09/13/2016
ms.topic: reference
title: 使用者要求確認
description: 使用者要求確認
ms.openlocfilehash: 58dbe27635ca38886b728f585fec063645b3597e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646313"
---
# <a name="users-requesting-confirmation"></a>使用者要求確認

當您針對 Cmdlet 屬性宣告的參數指定值時 `true` `SupportsShouldProcess` ，使用者可以 `Confirm` 在命令提示字元指定參數。

在預設環境中，使用者可以指定 `Confirm` 參數，或在 `"-Confirm:$true` 呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法時，要求您確認。 這會略過 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 確認要求，即使是對高影響的作業也是如此。

如果 `Confirm` 未指定，則 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 呼叫會在 `$ConfirmPreference` 喜好設定變數等於或大於 `ConfirmImpact` Cmdlet 或提供者的設定時，要求確認。 的預設設定 `$ConfirmPreference` 為 High。 因此，在預設環境中，只有指定高影響動作要求確認的 Cmdlet 和提供者。

如果 `Confirm` 為 false 或 `"-Confirm:$false` 已指定，則 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 呼叫會要求使用者確認，而且 `$ConfirmPreference` 會忽略 shell 變數的功能。

## <a name="remarks"></a>備註

- 針對指定的 Cmdlet 和提供者（ `SupportsShouldProcess` 但不 `ConfirmImpact` 是），這些動作會被視為「影響」的動作，而且預設不會提示。 其影響層級小於喜好設定變數的預設設定 `$ConfirmPreference` 。

- 如果使用者指定 `Verbose` 參數，即使系統未提示您進行確認，這些參數也會收到操作的通知。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
