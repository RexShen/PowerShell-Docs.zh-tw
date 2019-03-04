---
title: 使用者要求確認 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856234"
---
# <a name="users-requesting-confirmation"></a>使用者要求確認

當您指定的值`true`for `SupportsShouldProcess` Cmdlet 屬性宣告的參數，使用者可以指定`Confirm`參數在命令提示字元。

在預設環境中，使用者可以指定`Confirm`參數或`"-Confirm:$true`，因此會要求確認時[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫方法。 這會略過[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)確認要求，甚至是具有強烈影響的作業。

如果`Confirm`未指定，則[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫要求您確認如果`$ConfirmPreference`喜好設定變數是等於或大於`ConfirmImpact`設定cmdlet 或提供者。 預設設定`$ConfirmPreference`是 「 高 」。 因此，在預設環境中，唯一的 cmdlet 和提供者，指定具有強烈影響動作要求確認。

如果`Confirm`為 false 或如果`"-Confirm:$false`指定，則[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫，不讓使用者要求確認和`$ConfirmPreference`殼層變數會被忽略。

## <a name="remarks"></a>備註

- Cmdlet 和指定的提供者`SupportsShouldProcess`，而非`ConfirmImpact`，做為 「 中度影響 」 動作，處理這些動作，而且預設不會提示他們。 其影響層級小於預設值`$ConfirmPreference`喜好設定變數。

- 如果使用者指定`Verbose`參數，系統會通知的作業即使它們不會提示進行確認。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
