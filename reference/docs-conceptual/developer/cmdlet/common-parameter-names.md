---
title: 一般參數名稱 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365737"
---
# <a name="common-parameter-names"></a>一般參數名稱

本主題中所述的參數稱為*一般參數*。 Windows PowerShell 執行時間會將它們新增至 Cmdlet，而且不能由 Cmdlet 宣告。

> [!NOTE]
> 這些參數也會新增至提供者 Cmdlet 和以 `CmdletBinding` 屬性裝飾的函式。

## <a name="general-common-parameters"></a>一般通用參數

下列參數會新增至所有 Cmdlet，並可在每次執行 Cmdlet 時存取。 這些參數是由[Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)類別所定義。

### <a name="debug-alias-db"></a>Debug （別名： db）

資料類型： SwitchParameter

這個參數會指定程式設計人員層級的偵錯工具訊息是否可以在命令列中顯示。 這些訊息的目的是要針對 Cmdlet 的作業進行疑難排解，並透過呼叫[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法來產生。 不需要當地語系化的 Debug 訊息。

### <a name="erroraction-alias-ea"></a>ErrorAction （別名： ea）

資料類型：列舉

這個參數會指定發生錯誤時應採取的動作。 這個參數的可能值是由[Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference)列舉所定義。

### <a name="errorvariable-alias-ev"></a>ErrorVariable （別名： ev）

資料類型：字串

這個參數會指定發生錯誤時，要在其中放置物件的變數。 若要附加至此變數，請使用 +*varname* ，而不是清除和設定變數。

### <a name="outvariable-alias-ov"></a>OutVariable （別名： ov）

資料類型：字串

此參數會指定要在其中放置 Cmdlet 所產生之所有輸出物件的變數。 若要附加至此變數，請使用 +*varname* ，而不是清除和設定變數。

### <a name="outbuffer-alias-ob"></a>OutBuffer （別名： ob）

資料類型： Int32

這個參數會定義在將任何物件向下傳遞至管線之前，要在輸出緩衝區中儲存的物件數目。 根據預設，物件會立即傳遞給管線。

### <a name="verbose-alias-vb"></a>Verbose （別名： vb）

資料類型： SwitchParameter

此參數會指定此 Cmdlet 是否會寫入可在命令列中顯示的說明訊息。 這些訊息的目的是要為使用者提供額外的協助，並藉由呼叫[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法來產生。

### <a name="warningaction-alias-wa"></a>WarningAction （別名： wa）

資料類型：列舉

此參數會指定當 Cmdlet 寫入警告訊息時，應採取什麼動作。 這個參數的可能值是由[Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference)列舉所定義。

### <a name="warningvariable-alias-wv"></a>WarningVariable （別名： wv）

資料類型：字串

這個參數會指定可儲存警告訊息的變數。 若要附加至此變數，請使用 +*varname* ，而不是清除和設定變數。

## <a name="risk-mitigation-parameters"></a>風險-緩和參數

下列參數會新增至 Cmdlet，這些指令程式會在執行其動作之前要求確認。 如需有關確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。 這些參數是由[Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)類別所定義。

### <a name="confirm-alias-cf"></a>確認（別名： cf）

資料類型： SwitchParameter

此參數會指定此 Cmdlet 是否會顯示提示，詢問使用者是否確定要繼續。

### <a name="whatif-alias-wi"></a>WhatIf （別名： wi-fi）

資料類型： SwitchParameter

此參數會指定 Cmdlet 是否會寫入訊息，以描述執行 Cmdlet 的效果，而不需實際執行任何動作。

## <a name="transaction-parameters"></a>交易參數

下列參數會加入至支援交易的 Cmdlet 中。 這些參數是由[Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)類別所定義。

### <a name="usetransaction-alias-usetx"></a>UseTransaction （別名： usetx）

資料類型： SwitchParameter

這個參數會指定此 Cmdlet 是否將使用目前的交易來執行其動作。

## <a name="see-also"></a>另請參閱

[Commonparameters （內部）](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[Shouldprocessparameters （內部）](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[Transactionparameters （內部）](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
