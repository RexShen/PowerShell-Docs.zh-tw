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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363537"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet 屬性宣告

Cmdlet 屬性會將 Microsoft .NET Framework 類別識別為 Cmdlet，並指定用來叫用 Cmdlet 的動詞和名詞。

## <a name="syntax"></a>語法

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>參數

需要 `VerbName` （[system.string](/dotnet/api/System.String)）。 指定 Cmdlet 動詞。 這個動詞命令會指定 Cmdlet 所採取的動作。 如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)和[必要的開發指導方針](./required-development-guidelines.md)。

需要 `NounName` （[system.string](/dotnet/api/System.String)）。 指定 Cmdlet 名詞。 此名詞會指定 Cmdlet 作用的資源。 如需 Cmdlet 名詞的詳細資訊，請參閱[Cmdlet](./cmdlet-class-declaration.md)宣告和[強烈建議的開發指導方針](./strongly-encouraged-development-guidelines.md)。

`SupportsShouldProcess` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。 `True` 指出此 Cmdlet 支援[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的呼叫，它會提供 Cmdlet，讓您在執行變更系統的動作之前，先提示使用者。 `False`（預設值）表示此 Cmdlet 不支援[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的呼叫，而是。 如需有關確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

`ConfirmImpact` （[Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)）選擇性的具名引數。 指定在呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法時，應如何確認 Cmdlet 的動作。（& i） [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)只會在 Cmdlet 的 ConfirmImpact 值（依預設為 Medium）等於或大於 `$ConfirmPreference` 變數的值時才會呼叫此功能。 只有在指定了 `SupportsShouldProcess` 參數時，才應該指定這個參數。

`DefaultParameterSetName` （[system.string](/dotnet/api/System.String)）選擇性的具名引數。 指定 Windows PowerShell 執行時間在無法判斷要使用哪個參數集時，所嘗試使用的預設參數集。 請注意，您可以將每個參數的 unique 參數設定為強制參數，以消除這種情況。

有一種情況下，即使指定了預設參數集名稱，Windows PowerShell 也無法使用預設參數集。 Windows PowerShell 執行時間無法根據物件類型來區分參數集。 例如，如果您有一個參數集採用字串做為檔案路徑，而另一個是直接接受**FileInfo**物件的集合，Windows PowerShell 就無法根據傳遞給 Cmdlet 的值來判斷要使用的參數集，也不會使用預設參數集。 在此情況下，即使您指定預設參數集名稱，Windows PowerShell 還是會擲回不明確的參數集錯誤訊息。

`SupportsTransactions` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。 `True` 表示可在交易內使用此 Cmdlet。 當指定 `True` 時，Windows PowerShell 執行時間會將 `UseTransaction` 參數新增至 Cmdlet 的參數清單。 `False`，預設值表示無法在交易內使用此 Cmdlet。

## <a name="remarks"></a>備註

- 動詞和名詞一起用來識別您已註冊的 Cmdlet，並在腳本中叫用您的 Cmdlet。

- 從 Windows PowerShell 主控台叫用 Cmdlet 時，命令會類似下列命令：

**VerbName-NounName**

- 在 Windows PowerShell 外部變更資源的所有 Cmdlet 應該在宣告 Cmdlet 屬性時包含 `SupportsShouldProcess` 關鍵字，這可讓 Cmdlet 在執行其動作之前呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 如果[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫傳回 `false`，則不應採取此動作。 如需[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫所產生之確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

`Confirm` 和 `WhatIf` Cmdlet 參數僅適用于支援[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫的指令程式。

## <a name="example"></a>範例

下列類別定義會使用 Cmdlet 屬性來識別用來取得在本機電腦上執行之處理常式相關資訊的**Proc** Cmdlet 的 .NET Framework 類別。

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

如需有關**Proc** Cmdlet 的詳細資訊，請參閱[GetProc 教學](./getproc-tutorial.md)課程。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
