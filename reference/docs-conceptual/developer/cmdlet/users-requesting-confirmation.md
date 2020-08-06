---
title: 要求確認的使用者 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f0effb35a110f33248a582fab874e3ab95c7df4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786334"
---
# <a name="users-requesting-confirmation"></a>使用者要求確認

當您 `true` 針對 Cmdlet 屬性宣告的參數指定的值時 `SupportsShouldProcess` ，使用者可以 `Confirm` 在命令提示字元指定參數。

在預設的環境中，使用者可以指定 `Confirm` 參數，或在 `"-Confirm:$true` 呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法時要求該確認。 這會略過[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)確認要求，即使是對高影響力的作業也一樣。

如果 `Confirm` 未指定，則[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫 `$ConfirmPreference` 會在喜好設定變數等於或大於 `ConfirmImpact` Cmdlet 或提供者的設定時要求確認。 的預設設定 `$ConfirmPreference` 為 [高]。 因此，在預設環境中，只有指定高影響動作要求確認的 Cmdlet 和提供者。

如果 `Confirm` 為 false，或 `"-Confirm:$false` 指定了，則[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫會向使用者要求確認，並 `$ConfirmPreference` 忽略 shell 變數。

## <a name="remarks"></a>備註

- 對於指定（但不是）的 Cmdlet 和提供者， `SupportsShouldProcess` `ConfirmImpact` 這些動作會當做「中度影響」動作來處理，而且預設不會提示。 其影響層級小於喜好設定變數的預設值 `$ConfirmPreference` 。

- 如果使用者指定參數，則會收到作業的 `Verbose` 通知，即使系統不會提示您進行確認。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
