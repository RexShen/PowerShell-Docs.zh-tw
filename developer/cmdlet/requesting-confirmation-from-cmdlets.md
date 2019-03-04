---
title: Cmdlet 從要求確認 |Microsoft Docs
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
ms.openlocfilehash: ec441831f5e3231a44c9875d1b6d2bf6280a6965
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853394"
---
# <a name="requesting-confirmation-from-cmdlets"></a>從 Cmdlet 要求確認

他們即將進行之系統的 Windows PowerShell 環境以外變更時，Cmdlet 就應該要求確認。 比方說，cmdlet 是否新增使用者帳戶，或停止的處理序，此 cmdlet 應該要求使用者確認之前它會繼續。 相較之下，如果 cmdlet 是將要變更的 Windows PowerShell 變數，此 cmdlet 不需要要求確認。

若要確認要求，它支援確認要求，且必須呼叫，必須指出此 cmdlet [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) （選擇性） 的方法，以顯示一則確認要求訊息。

## <a name="supporting-confirmation-requests"></a>確認要求的支援

若要支援確認要求，必須設定 cmdlet`SupportsShouldProcess`參數到 Cmdlet 屬性`true`。 這可讓`Confirm`和`WhatIf`所提供的 Windows PowerShell 的 cmdlet 參數。 `Confirm`參數可讓使用者控制是否顯示確認要求。 `WhatIf`參數可讓使用者判斷 cmdlet 是否應該顯示一則訊息，或執行其動作。 不要以手動方式新增`Confirm`和`WhatIf`cmdlet 的參數。

下列範例會示範支援確認要求 Cmdlet 屬性宣告。

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>呼叫確認要求方法

Cmdlet 程式碼中呼叫[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之前執行變更系統的作業。 因此，如果在呼叫傳回的值，設計 cmdlet `false`、 未執行此作業，和 cmdlet 所處理的下一個作業。

## <a name="calling-the-shouldcontinue-method"></a>呼叫 ShouldContinue 方法

大多數的 cmdlet 會要求確認只會使用[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。 不過，某些情況下可能需要再次確認。 在這些情況下，補充[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫透過呼叫[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法。 這可讓 cmdlet 或提供者，以更細微控制的領域**全部皆是**回應的確認提示。

如果指令程式會呼叫[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，此 cmdlet 也必須提供`Force`切換參數。 如果使用者指定`Force`當使用者叫用此指令程式，仍應該呼叫此 cmdlet [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)，但它應該略過呼叫[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。

[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)呼叫不會提示使用者從非互動式環境時將會擲回例外狀況。 新增`Force`參數可確保在非互動式環境中叫用時，仍然可以執行命令。

下列範例示範如何呼叫[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

行為[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫而異的指令程式會叫用的環境。 使用先前的指導方針，可協助確保 cmdlet 與其他 cmdlet，不論主機環境以一致的方式運作。

如需呼叫的範例[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，請參閱[如何要求確認](./how-to-request-confirmations.md)。

## <a name="specify-the-impact-level"></a>指定影響層級

當您建立 cmdlet 時，指定變更的影響等級 （嚴重性）。 若要這樣做，請將設定的值`ConfirmImpact`高、 中或低 Cmdlet 屬性的參數。 您可以指定的值`ConfirmImpact`只有當您也指定`SupportsShouldProcess`cmdlet 的參數。

對於大多數的 cmdlet，您不必明確指定`ConfirmImpact`。  相反地，使用預設設定的參數，這也是媒介。 如果您將設定`ConfirmImpact`為 [高]，作業將會確認預設。 保留這項設定高度干擾性的動作，例如重新格式化硬碟磁碟區。

## <a name="calling-non-confirmation-methods"></a>呼叫非確認方法

如果 cmdlet 或提供者必須將訊息傳送，但不是要求確認，它可以呼叫下列三種方法。 請避免使用[System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法來傳送這些類型的訊息，因為[System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)輸出會互相混合您的 cmdlet 或提供者的一般輸出，這會使得指令碼撰寫困難。

- 若要想要提醒使用者，並繼續進行此作業，cmdlet 或提供者可以呼叫[System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法。

- 若要提供使用者可以使用擷取的其他資訊`Verbose`參數，cmdlet 或提供者可以呼叫[System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。

- 若要讓其他開發人員，或取得產品支援，請提供偵錯層級詳細資料，該 cmdlet 或提供者可以呼叫[System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。 使用者可以使用此資訊來擷取`Debug`參數。

Cmdlet 與提供者先呼叫下列方法來要求確認，以免他們發動執行作業，以變更在 Windows PowerShell 之外的系統：

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

藉由呼叫會進行[System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，它會提示使用者確認是否要根據使用者如何叫用命令的作業。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
