---
title: Cmdlet 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058023"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet 屬性宣告

Cmdlet 屬性識別為 cmdlet 的 Microsoft.NET Framework 類別，並指定用來叫用 cmdlet 的名詞與動詞命令。

## <a name="syntax"></a>語法

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>參數

`VerbName` ([System.String](/dotnet/api/System.String)) 所需。 指定 cmdlet 動詞命令。 此動詞命令會指定此 cmdlet 所採取的動作。 如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)並[所需的開發指導方針](./required-development-guidelines.md)。

`NounName` ([System.String](/dotnet/api/System.String)) 所需。 指定 cmdlet 名詞。 這個名詞會指定此 cmdlet 作用的資源。 如需有關 cmdlet 名詞的詳細資訊，請參閱[Cmdlet 宣告](./cmdlet-class-declaration.md)並[強烈鼓勵開發指導方針](./strongly-encouraged-development-guidelines.md)。

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。 `True` 指出此 cmdlet 支援對[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，可提供此 cmdlet 以變更系統的動作執行之前，提示使用者的方式。 `False`預設值，指出此 cmdlet 不支援呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 如需確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) 選擇性具名參數。 指定 cmdlet 的動作時應該呼叫確認[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)將只在等於或大於的值 （根據預設，媒體） cmdlet 的 ConfirmImpact 值時才呼叫`$ConfirmPreference`變數。 應該指定這個參數時，才`SupportsShouldProcess`指定參數。

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) 選擇性具名參數。 指定預設參數可讓您設定 Windows PowerShell 執行階段嘗試時無法判斷哪一個參數設定為使用所要使用的。 請注意，這種情況下要消除，可以藉由每個參數的唯一參數，設定必要的參數。

沒有 Windows PowerShell 不能使用的預設參數集，即使未指定預設參數集名稱的其中一種情況。 Windows PowerShell 執行階段無法區分僅根據物件類型的參數集。 例如，如果您有另一組檔案路徑，以及採用字串的一個參數集花**FileInfo**物件直接，Windows PowerShell 無法判斷哪一個參數設定為使用根據傳遞給的值指令程式，也不會使用預設參數集。 在此情況下，即使您指定預設參數集名稱，Windows PowerShell 會擲回模稜兩可的參數設定錯誤訊息。

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。 `True` 指出此 cmdlet，可以使用在交易內。 當`True`未指定，Windows PowerShell 執行階段加入`UseTransaction`cmdlet 的參數清單的參數。 `False`預設值，指出此 cmdlet 不可用於交易。

## <a name="remarks"></a>備註

- 在一起，動詞和名詞用來識別您已註冊的 cmdlet，並叫用您在指令碼內的 cmdlet。

- 從 Windows PowerShell 主控台中，叫用 cmdlet 時，命令就會類似下列的命令：

**VerbName-NounName**

- 變更 Windows PowerShell 以外之資源的所有 cmdlet 應該都包含`SupportsShouldProcess`關鍵字宣告 Cmdlet 屬性時，它可讓 cmdlet 呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之前，此 cmdlet 會執行其動作。 如果[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫傳回`false`，不應採取的動作。 如需詳細資訊，所產生之確認要求的相關[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

`Confirm`並`WhatIf`只會針對支援的 cmdlet 的 cmdlet 參數可[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫。

## <a name="example"></a>範例

下列類別定義使用 Cmdlet 屬性來識別的.NET Framework 類別**Get-proc** cmdlet，擷取本機電腦上執行的處理程序的相關資訊。

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

如需詳細資訊**Get-proc** cmdlet，請參閱[GetProc 教學課程](./getproc-tutorial.md)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
