---
ms.date: 09/13/2016
ms.topic: reference
title: 一般參數名稱
description: 一般參數名稱
ms.openlocfilehash: cf39dd3b04660076718336857d79d55c3784ccd1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668213"
---
# <a name="common-parameter-names"></a>一般參數名稱

本主題所描述的參數稱為 *一般參數*。 Windows PowerShell 執行時間會將它們新增至 Cmdlet，且無法由 Cmdlet 宣告。

> [!NOTE]
> 這些參數也會新增至提供者 Cmdlet 和以屬性裝飾的函式 `CmdletBinding` 。

## <a name="general-common-parameters"></a>一般一般參數

系統會將下列參數新增至所有 Cmdlet，並可在執行 Cmdlet 時存取。 這些參數是由 [Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) 類別所定義。

### <a name="debug-alias-db"></a>Debug (alias： db) 

資料類型： SwitchParameter

此參數會指定是否可在命令列中顯示程式設計師層級的偵錯工具訊息。 這些訊息的目的是要針對 Cmdlet 的作業進行疑難排解，並透過呼叫 [WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 方法來產生。 調試訊息不需要當地語系化。

### <a name="erroraction-alias-ea"></a>ErrorAction (別名： ea) 

資料類型：列舉

此參數會指定發生錯誤時應採取的動作。 這個參數的可能值是由 [Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) 列舉所定義。

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias： ev) 

資料類型：字串

此參數會指定發生錯誤時，要在其中放置物件的變數。 若要附加至此變數，請使用 +*varname* ，而不是清除和設定變數。

### <a name="outvariable-alias-ov"></a>OutVariable (alias： ov) 

資料類型：字串

此參數會指定要在其中放置 Cmdlet 所產生之所有輸出物件的變數。 若要附加至此變數，請使用 +*varname* ，而不是清除和設定變數。

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias： ob) 

資料類型： Int32

此參數會定義在將任何物件傳遞至管線之前，要在輸出緩衝區中儲存的物件數目。 依預設，物件會立即沿著管線向下傳遞。

### <a name="verbose-alias-vb"></a>詳細資訊 (別名： vb) 

資料類型： SwitchParameter

此參數會指定此 Cmdlet 是否會寫入可在命令列中顯示的解釋訊息。 這些訊息的目的是要為使用者提供額外的協助，並藉由呼叫 [WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 方法來產生。

### <a name="warningaction-alias-wa"></a>WarningAction (別名： wa) 

資料類型：列舉

此參數會指定 Cmdlet 寫入警告訊息時應採取的動作。 這個參數的可能值是由 [Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) 列舉所定義。

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias： wv) 

資料類型：字串

此參數會指定可儲存警告訊息的變數。 若要附加至此變數，請使用 +*varname* ，而不是清除和設定變數。

## <a name="risk-mitigation-parameters"></a>Risk-Mitigation 參數

下列參數會新增至 Cmdlet，以在執行其動作之前要求確認。 如需確認要求的詳細資訊，請參閱 [要求確認](./requesting-confirmation-from-cmdlets.md)。 這些參數是由 [Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) 類別所定義。

### <a name="confirm-alias-cf"></a>確認 (別名： cf) 

資料類型： SwitchParameter

此參數會指定此 Cmdlet 是否會顯示提示，詢問使用者是否確定要繼續進行。

### <a name="whatif-alias-wi"></a>WhatIf (別名： wi-fi) 

資料類型： SwitchParameter

此參數會指定此 Cmdlet 是否會寫入描述執行 Cmdlet 之效果的訊息，而不會實際執行任何動作。

## <a name="transaction-parameters"></a>交易參數

下列參數會加入至支援交易的 Cmdlet。 這些參數是由 [Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) 類別所定義。

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias： usetx) 

資料類型： SwitchParameter

此參數會指定此 Cmdlet 是否會使用目前的交易來執行其動作。

## <a name="see-also"></a>另請參閱

[Commonparameters 的內部管理](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[Shouldprocessparameters 的內部管理](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[Transactionparameters 的內部管理](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
