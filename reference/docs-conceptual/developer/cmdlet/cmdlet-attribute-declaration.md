---
title: Cmdlet 屬性宣告 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.openlocfilehash: 672609f1f50e4600aebcbb7e6e79bb7353ec867d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774825"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet 屬性宣告

Cmdlet 屬性會將 Microsoft .NET Framework 類別識別為 Cmdlet，並指定用來叫用 Cmdlet 的動詞和名詞。

## <a name="syntax"></a>語法

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>參數

`VerbName`需要 ([system.string](/dotnet/api/System.String)) 。 指定 Cmdlet 動詞。 這個動詞命令會指定 Cmdlet 所採取的動作。 如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)和[必要的開發指導方針](./required-development-guidelines.md)。

`NounName`需要 ([system.string](/dotnet/api/System.String)) 。 指定 Cmdlet 名詞。 此名詞會指定 Cmdlet 作用的資源。 如需 Cmdlet 名詞的詳細資訊，請參閱[Cmdlet](./cmdlet-class-declaration.md)宣告和[強烈建議的開發指導方針](./strongly-encouraged-development-guidelines.md)。

`SupportsShouldProcess` ([的布林值](/dotnet/api/System.Boolean)) 選擇性的具名引數。 `True`指出此 Cmdlet 支援[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的呼叫，它會提供 Cmdlet，讓您在執行變更系統的動作之前，先提示使用者。 `False`（預設值）表示此 Cmdlet 不支援呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的程式，而是。 如需有關確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

`ConfirmImpact` ([Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) 選擇性的具名引數。 指定在呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法時，應如何確認 Cmdlet 的動作。（& i） [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)只會在 Cmdlet 的 ConfirmImpact 值 (時呼叫，而 Medium) 等於或大於變數的值時才會呼叫。 `$ConfirmPreference` 只有在指定參數時，才應該指定這個參數 `SupportsShouldProcess` 。

`DefaultParameterSetName` ([system.string](/dotnet/api/System.String)) 選擇性的具名引數。 指定 Windows PowerShell 執行時間在無法判斷要使用哪個參數集時，所嘗試使用的預設參數集。 請注意，您可以將每個參數的 unique 參數設定為強制參數，以消除這種情況。

有一種情況下，即使指定了預設參數集名稱，Windows PowerShell 也無法使用預設參數集。 Windows PowerShell 執行時間無法根據物件類型來區分參數集。 例如，如果您有一個參數集採用字串做為檔案路徑，而另一個是直接接受**FileInfo**物件的集合，Windows PowerShell 就無法根據傳遞給 Cmdlet 的值來判斷要使用的參數集，也不會使用預設參數集。 在此情況下，即使您指定預設參數集名稱，Windows PowerShell 還是會擲回不明確的參數集錯誤訊息。

`SupportsTransactions` ([的布林值](/dotnet/api/System.Boolean)) 選擇性的具名引數。 `True`指出可以在交易內使用此 Cmdlet。 當 `True` 指定時，Windows PowerShell 執行時間會將 `UseTransaction` 參數新增至 Cmdlet 的參數清單。 `False`（預設值）表示無法在交易內使用此 Cmdlet。

## <a name="remarks"></a>備註

- 動詞和名詞一起用來識別您已註冊的 Cmdlet，並在腳本中叫用您的 Cmdlet。

- 從 Windows PowerShell 主控台叫用 Cmdlet 時，命令會類似下列命令：

**VerbName-NounName**

- 在 Windows PowerShell 外部變更資源的所有 Cmdlet 應該在宣告 `SupportsShouldProcess` Cmdlet 屬性時包含關鍵字，這可讓 Cmdlet 在執行其動作之前呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 如果[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫傳回 `false` ，就不應該採取此動作了。 如需[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫所產生之確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

`Confirm`和 `WhatIf` Cmdlet 參數僅適用于支援[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫的指令程式。

## <a name="example"></a>範例

下列類別定義會使用 Cmdlet 屬性來識別用來取得在本機電腦上執行之處理常式相關資訊的**Proc** Cmdlet 的 .NET Framework 類別。

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

如需有關**Proc** Cmdlet 的詳細資訊，請參閱[GetProc 教學](./getproc-tutorial.md)課程。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
