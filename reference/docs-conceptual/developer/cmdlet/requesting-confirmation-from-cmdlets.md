---
title: 正在從 Cmdlet 要求確認 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369527"
---
# <a name="requesting-confirmation-from-cmdlets"></a>從 Cmdlet 要求確認

當 Cmdlet 即將對 Windows PowerShell 環境以外的系統進行變更時，應要求確認。 例如，如果 Cmdlet 即將新增使用者帳戶或停止進程，此 Cmdlet 應該會在繼續進行之前要求使用者確認。 相反地，如果 Cmdlet 即將變更 Windows PowerShell 變數，Cmdlet 就不需要確認。

若要提出確認要求，此 Cmdlet 必須指出它支援確認要求，而且必須呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 中的，才能進行這項功能。 （選擇性）用來顯示確認要求訊息的方法。

## <a name="supporting-confirmation-requests"></a>支援確認要求

若要支援確認要求，Cmdlet 必須將 Cmdlet 屬性的 `SupportsShouldProcess` 參數設定為 `true`。 這會啟用 Windows PowerShell 所提供的 `Confirm` 和 `WhatIf` Cmdlet 參數。 `Confirm` 參數可讓使用者控制是否顯示確認要求。 `WhatIf` 參數可讓使用者判斷 Cmdlet 是否應該顯示訊息或執行其動作。 請勿手動將 `Confirm` 和 `WhatIf` 參數新增至 Cmdlet。

下列範例顯示支援確認要求的 Cmdlet 屬性宣告。

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>呼叫確認要求方法

在 Cmdlet 程式碼中，在執行變更系統的作業之前，呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 設計 Cmdlet，以便在呼叫傳回 `false`的值時，不會執行此作業，而 Cmdlet 會處理下一個作業。

## <a name="calling-the-shouldcontinue-method"></a>呼叫 ShouldContinue 方法

大部分的 Cmdlet 只會使用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法來要求確認。 不過，某些情況下可能需要額外的確認。 在這些情況下，請使用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的呼叫，來補充 ShouldProcess 呼叫的相關[功能](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)，以進行。 這可讓 Cmdlet 或提供者更精確地控制「是」對確認提示的**所有**回應範圍。

如果 Cmdlet 呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，則此 Cmdlet 也必須提供 `Force` 交換器參數（switch）。 如果使用者在叫用 Cmdlet 時指定 `Force`，此 Cmdlet 仍應呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)，但它應該會略過[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的呼叫，而不應使用。

[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)將會擲回例外狀況，因為它是從非互動式環境呼叫，而無法提示使用者。 新增 `Force` 參數可確保在非互動式環境中叫用命令時，仍然可以執行此命令。

下列範例會示範如何呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)，以供您執行此動作的說明。

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫的行為可能會因叫用 Cmdlet 的環境而異，而有所不同。 使用先前的指導方針可協助確保 Cmdlet 與其他 Cmdlet 一致地運作，而不論主機環境為何。

如需呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的範例，請參閱[如何要求確認](./how-to-request-confirmations.md)。

## <a name="specify-the-impact-level"></a>指定影響層級

當您建立 Cmdlet 時，請指定變更的影響層級（嚴重性）。 若要這麼做，請將 Cmdlet 屬性的 `ConfirmImpact` 參數值設定為 [高]、[中] 或 [低]。 只有當您同時指定 Cmdlet 的 `SupportsShouldProcess` 參數時，才可以指定 `ConfirmImpact` 的值。

對於大部分的 Cmdlet，您不需要明確指定 `ConfirmImpact`。  相反地，請使用參數的預設設定，也就是 Medium。 如果您將 `ConfirmImpact` 設定為 [高]，預設會確認此作業。 保留此設定以進行高度干擾性的動作，例如重新格式化硬碟磁片區。

## <a name="calling-non-confirmation-methods"></a>呼叫非確認方法

如果 Cmdlet 或提供者必須傳送訊息但不要求確認，它可以呼叫下列三種方法。 請避免使用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法來傳送這些類型的訊息，因為[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)輸出與 Cmdlet 或提供者的一般輸出混合在一起，使得腳本撰寫變得很棘手。

- 為謹慎起見，此 Cmdlet 或提供者可以呼叫[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法，並繼續操作。

- 若要提供使用者可使用 `Verbose` 參數抓取的其他資訊，Cmdlet 或提供者可以呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。

- 為了提供其他開發人員或產品支援的調試層級詳細資料，Cmdlet 或提供者可以呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。 使用者可以使用 `Debug` 參數來抓取此資訊。

Cmdlet 和提供者會先呼叫下列方法來要求確認，然後才嘗試執行會變更 Windows PowerShell 外部系統的作業：

- [Shouldprocess 的管理元件](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [提供者： Cmdletprovider. Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

他們會藉由呼叫[Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法來執行此動作，它會提示使用者根據使用者叫用命令的方式來確認操作。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
