---
title: 常見的參數名稱 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068417"
---
# <a name="common-parameter-names"></a>一般參數名稱

本主題中所述的參數指*一般參數*。 它們會新增至 cmdlet，Windows PowerShell 執行階段，並不可以宣告為 cmdlet。

> [!NOTE]
> 提供者 cmdlet，並以裝飾的函式，也會加入這些參數`CmdletBinding`屬性。

## <a name="general-common-parameters"></a>一般常見參數

下列參數新增至所有 cmdlet，而且每次執行 cmdlet 時可以存取。 這些參數會由[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)類別。

### <a name="debug-alias-db"></a>偵錯 (別名： db)

資料類型：SwitchParameter

此參數會指定是否程式設計人員層級偵錯訊息，可以在命令列中顯示。 這些訊息是針對疑難排解 cmdlet，作業，藉由呼叫會產生[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。 偵錯訊息不需要當地語系化。

### <a name="erroraction-alias-ea"></a>ErrorAction (別名： ea)

資料類型：列舉型別

此參數會指定何種動作發生錯誤時，應該會發生。 可能的值，這個參數會定義所[System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference)列舉型別。

### <a name="errorvariable-alias-ev"></a>ErrorVariable (別名： 環境變數)

資料類型：String

這個參數會指定要放置物件發生錯誤時的變數。 若要將附加至這個變數，請使用 +*varname*而不會清除和設定變數。

### <a name="outvariable-alias-ov"></a>OutVariable (別名： 關於)

資料類型：String

此參數會指定要放置所有輸出 cmdlet 所產生的物件的變數。 若要將附加至這個變數，請使用 +*varname*而不會清除和設定變數。

### <a name="outbuffer-alias-ob"></a>OutBuffer (別名： ob)

資料類型：Int32

此參數會定義要沿著管線向下傳遞任何物件之前，在輸出緩衝區中儲存物件的數目。 根據預設，物件會立即沿著管線向下傳遞。

### <a name="verbose-alias-vb"></a>詳細資訊 (別名： vb)

資料類型：SwitchParameter

此參數會指定此 cmdlet 是否會寫入說明可以在命令列中顯示的訊息。 這些訊息要提供給使用者時，其他說明，而且會產生藉由呼叫[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。

### <a name="warningaction-alias-wa"></a>WarningAction (別名： wa)

資料類型：列舉型別

此參數會指定此 cmdlet 會寫入一則警告訊息時，動作應該會發生。 可能的值，這個參數會定義所[System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference)列舉型別。

### <a name="warningvariable-alias-wv"></a>WarningVariable (別名： wv)

資料類型：String

此參數會指定可以在其中儲存的警告訊息的變數。 若要將附加至這個變數，請使用 +*varname*而不會清除和設定變數。

## <a name="risk-mitigation-parameters"></a>風險降低參數

要求您確認之後執行其動作的 cmdlet 會新增下列參數。 如需確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。 這些參數會由[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)類別。

### <a name="confirm-alias-cf"></a>確認 (別名： cf)

資料類型：SwitchParameter

此參數會指定此 cmdlet 是否會顯示一個提示，詢問使用者是否確定要繼續。

### <a name="whatif-alias-wi"></a>WhatIf (別名： wi-fi)

資料類型：SwitchParameter

此參數會指定此 cmdlet 是否會寫入訊息，說明執行此指令程式而不實際執行任何動作的效果。

## <a name="transaction-parameters"></a>交易參數

支援交易的 cmdlet 已新增下列參數。 這些參數會由[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)類別。

### <a name="usetransaction-alias-usetx"></a>UseTransaction (別名： usetx)

資料類型：SwitchParameter

此參數會指定是否 cmdlet 會使用目前的交易來執行其動作。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
