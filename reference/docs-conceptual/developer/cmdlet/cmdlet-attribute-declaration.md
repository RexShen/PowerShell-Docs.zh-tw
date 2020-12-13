---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 屬性宣告
description: Cmdlet 屬性宣告
ms.openlocfilehash: 6bdfe39a4ab9ef4d4cc98daa592f69f7fab95e84
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653550"
---
# <a name="cmdlet-attribute-declaration"></a>Cmdlet 屬性宣告

Cmdlet 屬性會將 Microsoft .NET Framework 類別識別為 Cmdlet，並指定用來叫用 Cmdlet 的動詞和名詞。

## <a name="syntax"></a>語法

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>參數

`VerbName` 需要 ([system.string](/dotnet/api/System.String)) 。 指定 Cmdlet 動詞。 此動詞命令會指定 Cmdlet 所採取的動作。 如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱 [Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md) 和 [必要的開發指導方針](./required-development-guidelines.md)。

`NounName` 需要 ([system.string](/dotnet/api/System.String)) 。 指定 Cmdlet 名詞。 此名詞指定 Cmdlet 作用的資源。 如需 Cmdlet 名詞的詳細資訊，請參閱 [Cmdlet](./cmdlet-class-declaration.md) 宣告和 [強烈建議的開發指導方針](./strongly-encouraged-development-guidelines.md)。

`SupportsShouldProcess` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。 `True` 指出此 Cmdlet 支援 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法的呼叫，這個方法會提供 Cmdlet 提示使用者的方法，在執行變更系統的動作之前提示使用者。 `False`（預設值）表示此 Cmdlet 不支援對 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法的呼叫的呼叫。 如需確認要求的詳細資訊，請參閱 [要求確認](./requesting-confirmation-from-cmdlets.md)。

`ConfirmImpact` ([Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) 選擇性的具名引數。 指定 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法的呼叫時，應如何確認 Cmdlet 的動作，以確認。 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)只會在 Cmdlet 的 ConfirmImpact 值 (預設情況下呼叫，而中) 等於或大於變數的值時才會呼叫。 `$ConfirmPreference` 只有在指定參數時，才應指定這個參數 `SupportsShouldProcess` 。

`DefaultParameterSetName` ([system.string](/dotnet/api/System.String)) 選擇性的具名引數。 指定當 Windows PowerShell 執行時間無法判斷要使用哪個參數集時，所嘗試使用的預設參數集。 請注意，您可以將每個參數的 unique 參數設定為強制參數，以消除這種情況。

有一種情況是，即使指定了預設參數集名稱，Windows PowerShell 也無法使用預設參數集。 Windows PowerShell 執行時間無法區分只以物件類型為基礎的參數集。 例如，如果您有一個參數集接受字串做為檔案路徑，另一個則是直接接受 **FileInfo** 物件的集合，Windows PowerShell 無法根據傳遞給 Cmdlet 的值判斷要使用的參數集，也不會使用預設參數集。 在此情況下，即使您指定預設參數集名稱，Windows PowerShell 也會擲回不明確的參數集錯誤訊息。

`SupportsTransactions` ([system.string) 選擇性的命名](/dotnet/api/System.Boolean) 參數。 `True` 表示可以在交易內使用此 Cmdlet。 當 `True` 指定時，Windows PowerShell 執行時間會將 `UseTransaction` 參數新增至 Cmdlet 的參數清單。 `False`（預設值）表示無法在交易內使用此 Cmdlet。

## <a name="remarks"></a>備註

- 指令動詞和名詞會一起用來識別您的已註冊 Cmdlet，並在腳本中叫用您的 Cmdlet。

- 從 Windows PowerShell 主控台叫用 Cmdlet 時，命令會類似下列命令：

**VerbName-NounName**

- 在宣告 Windows PowerShell 之外變更資源的所有 Cmdlet 都應該在宣告 `SupportsShouldProcess` Cmdlet 屬性時包含關鍵字，如此可讓 Cmdlet 在 Cmdlet 執行其動作之前呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 方法。 如果 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 呼叫傳回 `false` ，就不應採取此動作，。 如需 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 呼叫所產生之確認要求的詳細資訊，請參閱 [要求確認](./requesting-confirmation-from-cmdlets.md)。

`Confirm`和 `WhatIf` Cmdlet 參數僅適用于支援[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫的指令程式。

## <a name="example"></a>範例

下列類別定義會使用 Cmdlet 屬性來識別 **get-help** Cmdlet 的 .NET Framework 類別，以抓取在本機電腦上執行之處理常式的相關資訊。

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

如需有關 **Proc** Cmdlet 的詳細資訊，請參閱 [GetProc 教學](./getproc-tutorial.md)課程。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
