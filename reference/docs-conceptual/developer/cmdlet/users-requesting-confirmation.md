---
title: 要求確認的使用者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369247"
---
# <a name="users-requesting-confirmation"></a>使用者要求確認

當您為 Cmdlet 屬性宣告的 `SupportsShouldProcess` 參數指定 `true` 的值時，使用者可以在命令提示字元中指定 `Confirm` 參數。

在預設環境中，使用者可以指定 `Confirm` 參數或 `"-Confirm:$true`，以便在呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法時要求確認。 這會略過[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)確認要求，即使是對高影響力的作業也一樣。

如果未指定 `Confirm`，則[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫會在 `$ConfirmPreference` 喜好設定變數等於或大於 Cmdlet 或提供者的 `ConfirmImpact` 設定時要求確認。 @No__t-0 的預設設定為 [高]。 因此，在預設環境中，只有指定高影響動作要求確認的 Cmdlet 和提供者。

如果 `Confirm` 為 false，或指定了 `"-Confirm:$false`，則[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫會向使用者要求確認，而 @no__t 3 shell 變數會被忽略。

## <a name="remarks"></a>備註

- 對於指定 `SupportsShouldProcess` 但不 `ConfirmImpact` 的 Cmdlet 和提供者，這些動作會當做「中度影響」動作來處理，而且預設不會提示。 其影響層級小於 `$ConfirmPreference` 喜好設定變數的預設值。

- 如果使用者指定了 `Verbose` 參數，則即使系統不會提示您進行確認，也會收到操作的通知。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
