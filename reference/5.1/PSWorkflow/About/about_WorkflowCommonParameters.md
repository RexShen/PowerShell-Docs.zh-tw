---
description: 本主題說明所有 Windows PowerShell 工作流程命令都有效的參數。 由於 Windows PowerShell 引擎會將它們新增至工作流程，因此您可以在任何工作流程上使用這些參數，而且這些參數會在您撰寫的工作流程上自動啟用。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflowcommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WorkflowCommonParameters
ms.openlocfilehash: 386200475c1dab9735921edd60abbde20ee354c4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207215"
---
# <a name="about-workflowcommonparameters"></a>關於 WorkflowCommonParameters

## <a name="short-description"></a>簡短描述

本主題說明所有 Windows PowerShell 工作流程命令都有效的參數。 由於 Windows PowerShell 引擎會將它們新增至工作流程，因此您可以在任何工作流程上使用這些參數，而且這些參數會在您撰寫的工作流程上自動啟用。

## <a name="long-description"></a>詳細描述

Windows PowerShell 工作流程一般參數是一組 Cmdlet 參數，可搭配所有 Windows PowerShell 工作流程和活動使用。 它們是由 Windows PowerShell 工作流程引擎新增，而不是由工作流程作者加入，而且會自動提供給工作流程和活動使用。 不過，嵌套三層級深度的工作流程不支援任何一般參數，包括工作流程一般參數。

所有工作流程參數都是選擇性的，且命名 (不是位置) 。 它們不會從管線取得輸入。

大部分的工作流程一般參數都有 PS 前置詞，例如 `PSComputerName` 和 `PSCredential` 。 以 PS 為首碼的參數會設定目的電腦的連接和執行環境，也稱為「遠端節點」。

許多工作流程一般參數（例如 `PSAllowRedirection` 和 `AsJob` ）都有類似于 Windows PowerShell 遠端處理和背景工作中使用之參數的名稱。 這些參數的運作方式與類似命名的遠端和作業參數相同，因此您可以使用在遠端處理和作業中所開發的知識來管理工作流程。

工作流程會在 Windows PowerShell 3.0 中引進。

### <a name="parameter-descriptions"></a>參數描述

本節說明工作流程一般參數。

#### <a name="-asjob-switchparameter"></a>-AsJob \<SwitchParameter\>

以工作流程工作的形式執行工作流程。 Workflow 命令會立即傳回代表父作業的物件。 父工作包含在每部目的電腦上執行的子工作。 若要管理工作，請使用各項 Job Cmdlet。 若要取得工作結果，請使用 [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)。

#### <a name="-jobname-string"></a>-JobName \<String\>

指定工作流程工作的易記名稱。 工作預設會命名為 "Job\<n\>"，其中 \<n\> 是序號。

如果您在工作流程命令中使用 JobName 參數，則工作流程會以工作的形式執行，而且即使您未在命令中包含參數，工作流程命令也會傳回工作物件 `AsJob` 。

如需 Windows PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)。

#### <a name="-psallowredirection-switchparameter"></a>-PSAllowRedirection \<SwitchParameter\>

允許將連接重新導向至目的電腦。

當您使用 `PSConnectionURI` 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。 根據預設，Windows PowerShell 不會重新導向連線，但是您可以使用 `PSAllowRedirection` 參數來允許將連接重新導向至目的電腦。

您也可以藉由設定 `MaximumConnectionRedirectionCount` 喜好設定變數的屬性 `$PSSessionOption` ，或的值的屬性，限制連接重新導向的次數 `MaximumConnectionRedirectionCount` `PSSessionOption parameter` 。 預設值為 5。 如需詳細資訊，請參閱 `PSSessionOption` 參數和 [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)的說明。

#### <a name="-psapplicationname-string"></a>-PSApplicationName \<String\>

指定連接 URI 用來連接目的電腦的應用程式名稱區段。 當您未在命令中使用參數時，請使用這個參數來指定應用程式名稱 `ConnectionURI` 。

預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。 若未定義此喜好設定變數，則預設值是 WSMAN。 這個值適用於大部分用途。 如需詳細資訊，請參閱 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。 此參數的值應該符合 `URLPrefix` 遠端電腦上接聽程式的屬性值。

#### <a name="-psauthentication-authenticationmechanism"></a>-PSAuthentication \<AuthenticationMechanism\>

指定在連接到目的電腦時，用來驗證使用者認證的機制。

有效值為：

- **預設值**
- **基本**
- **Credssp**
- **Digest**
- **Kerberos**
- **洽談**
- **NegotiateWithImplicitCredential**

預設值為 **Default** 。

如需此參數值的詳細資訊，請參閱 `System.Management.Automation.Runspaces.AuthenticationMechanism` MSDN 中的列舉描述。

> [!WARNING]
> 使用者認證會傳遞至要驗證之遠端電腦的「認證安全性服務提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

#### <a name="-psauthenticationlevel-authenticationlevel"></a>-PSAuthenticationLevel \<AuthenticationLevel\>

指定與目的電腦之連接的驗證層級。
預設值為 **Default** 。

有效值為：

|Name |描述 |
|---------|---------|
|**未變更** | 驗證等級與前一個命令相同。 |
|**預設值** | Windows 驗證。 |
|**無** | 沒有 COM 驗證。   |
|**[連接]** | 連接層級 COM 驗證。|
|**呼叫** | 呼叫層級 COM 驗證。   |
|**包** | 封包層級 COM 驗證。|
|**PacketIntegrity** | 封包完整性層級 COM 驗證。  |
|**PacketPrivacy** | 封包隱私權層級 COM 驗證。 |

#### <a name="-pscertificatethumbprint-string"></a>-PSCertificateThumbprint \<String\>

對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。 請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。 這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證，請使用 [Get 專案](xref:Microsoft.PowerShell.Management.Get-Item) 或 [get-childitem] (。/../Microsoft.PowerShell.Management/Get-Childitem.md Windows PowerShell Cert：磁片磁碟機中的) Cmdlet。

#### <a name="-pscomputername-string"></a>-PSComputerName \<String[]\>

指定屬於工作流程目標節點的電腦清單。
工作流程中的命令或活動會在使用此參數指定的電腦上執行。 預設是本機電腦。

請輸入 NETBIOS 名稱、IP 位址或是一部或多部電腦的完整網域名稱 (以逗號分隔的清單方式)。 若要指定本機電腦，請輸入電腦名稱、"localhost" 或句點 (.)。

若要在參數值中包含本機電腦 `PSComputerName` ，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。

如果從命令省略此參數，或它的值為 `$null` 或空字串，則工作流程目標是本機電腦，而且不會使用 Windows PowerShell 遠端處理來執行命令。

若要在參數的值中使用 IP 位址 `ComputerName` ，命令必須包含 `PSCredential` 參數。 此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。 如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)中的「 *如何將電腦新增到信任的主機清單* 」。

#### <a name="-psconfigurationname-string"></a>-PSConfigurationName \<String\>

指定用來在目的電腦上設定會話的會話設定。 請在目的電腦上輸入會話設定， (不是工作流程伺服器電腦) 。 預設為 `Microsoft.PowerShell.Workflow`。

#### <a name="-psconnectionretrycount-uint"></a>-PSConnectionRetryCount \<UInt\>

指定第一次連線嘗試失敗時，嘗試連接至每部目的電腦的次數上限。 輸入介於1和 4294967295 (UInt) 之間的數位。 預設值為零 (0) 表示無重試嘗試。

#### <a name="-psconnectionretryintervalsec-uint"></a>-PSConnectionRetryIntervalSec \<UInt\>

指定連接重試嘗試之間的延遲（以秒為單位）。 預設值為零 (0)。 只有當 PSConnectionRetryCount 的值至少為1時，此參數才有效。

#### <a name="-psconnectionuri-systemuri"></a>-PSConnectionURI \<System.Uri\>

指定 (URI) 的統一資源識別項，以定義目的電腦上工作流程的連接端點。 此 URI 必須是完整的 URI。

這個字串的格式如下所示：

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

預設值是 `http://localhost:5985/WSMAN`。

如果您未指定 `PSConnectionURI` ，則可以使用 `PSUseSSL` 、 `PSComputerName` 、 `PSPort` 和 `PSApplicationName` 參數來指定 `PSConnectionURI` 值。

URI 的傳輸區段有效值為 **HTTP** 和 **HTTPS** 。
若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。 若要使用預設連接埠於 Windows PowerShell 遠端功能，請為 HTTP 指定連接埠 5985，或是為 HTTPS 指定連接埠 5986。

#### <a name="-pscredential-pscredential"></a>-PSCredential \<PSCredential\>

指定具有在目的電腦上執行工作流程之許可權的使用者帳戶。 預設為目前使用者。 只有當命令中包含 PSComputerName 參數時，此參數才有效。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入包含物件的變數 `PSCredential` ，例如 Cmdlet 所傳回的物件 `Get-Credential` 。 若您只輸入使用者名稱，將會提示您輸入密碼。

#### <a name="-pselapsedtimeoutsec-uint32"></a>-PSElapsedTimeoutSec \<UInt32\>

決定在系統中維護工作流程和所有相關資源的時間長度。 當超時時間過期時，即使工作流程仍在處理中，也會將其刪除。 請輸入介於10到4294967295之間的值。 預設值 0 (零) 表示沒有經過的超時時間。

#### <a name="-psparametercollection-hashtable"></a>-PSParameterCollection \<Hashtable[]\>

針對不同的目的電腦指定不同的工作流程一般參數值。

輸入以逗號分隔的雜湊表清單，其中每一部目的電腦各有一個雜湊表。 在每個雜湊表中，第一個索引鍵是， `PSComputerName` 而它的值是目的電腦的名稱。 電腦名稱稱中允許使用萬用字元。 針對雜湊表中其餘的索引鍵，索引鍵是參數名稱，而值是參數值。

例如：

```powershell
-PSParameterCollection @{PSComputerName="*"; PSElapsedTimeoutSec=20},
@{PSComputerName="Server02"},
@{PSComputerName="Server03"},
@{PSComputerName="Server01"; PSElapsedTimeoutSec=10}
```

在上述範例中，所有的連接都會有20秒的預設 PSElapsedTimeoutSec，但是 Server01 會指定自己的10秒超時，來覆寫預設值。

#### <a name="-pspersist-boolean"></a>-PSPersist \<Boolean\>

除了工作流程中指定的檢查點之外，還會將檢查點加入至工作流程。

此參數無法隱藏工作流程中的檢查點，例如使用 `PSPersist` 活動一般參數、 `Checkpoint-Workflow` 活動或變數所指定的檢查點 `$PSPersistPreference` 。

「檢查點」或「持續點」是工作流程執行時所捕捉的工作流程狀態和資料的快照集，而且會儲存到磁片或 SQL 資料庫中的持續性存放區。 Windows PowerShell 工作流程使用儲存的資料，從上一個持續點繼續暫停或中斷的工作流程，而不是重新開機工作流程。

有效值：

-  ( *預設* ) 如果您省略此參數，則除了工作流程中指定的任何檢查點之外，還會將檢查點加入至工作流程的開頭和結尾。

- `$True`. 將檢查點加入至工作流程的開頭和結尾，以及在每個活動之後的檢查點，以及工作流程中指定的任何檢查點。

- `$False`. 未新增任何檢查點。 只有在工作流程中指定時，才會採取檢查點。

#### <a name="-psport-int32"></a>-PSPort \<Int32\>

指定目的電腦上的網路埠。 預設連接埠是 5985 (用於 HTTP 的 WinRM 連接埠) 和 5986 (用於 HTTPS 的 WinRM 連接埠)。

除非您必須這樣做，否則請勿使用 PSPort 參數。 命令中設定的埠會套用到命令執行所在的所有電腦或會話。 替代的連接埠設定可能使得命令無法在全部電腦上執行。 使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。

#### <a name="-psprivatemetadata-hashtable"></a>-PSPrivateMetadata \<Hashtable\>

提供自訂的資訊給工作流程工作。 輸入雜湊表。 每個工作流程都會自訂索引鍵和值。 如需工作流程私用中繼資料的詳細資訊，請參閱工作流程的說明主題。

Windows PowerShell 工作流程引擎不會處理這個參數。
相反地，引擎會直接將雜湊表傳遞給工作流程。

#### <a name="-psrunningtimeoutsec-uint32"></a>-PSRunningTimeoutSec \<UInt32\>

指定工作流程的執行時間（以秒為單位），不包括工作流程暫止的任何時間。 如果工作流程執行在時間過期時未完成，Windows PowerShell 工作流程引擎會強制停止工作流程的執行。

#### <a name="-pssessionoption-pssessionoption"></a>-PSSessionOption \<PSSessionOption\>

將會話的 advanced 選項設定為目的電腦。 輸入 `PSSessionOption` 您使用 Cmdlet 建立的物件，例如您所建立的物件 `New-PSSessionOption` 。

會話選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。 否則，會話會使用會話設定中指定的值。

如需會話選項的描述（包括預設值），請參閱 Cmdlet ( 的說明主題 `New-PSSessionOption` 。/../Microsoft.PowerShell.Core/New-PSSessionOption.md) 。 如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

#### <a name="-psusessl-switchparameter"></a>-PSUseSSL \<SwitchParameter\>

使用安全通訊端層 (SSL) 通訊協定來建立與目的電腦的連線。 預設不會使用 SSL。

WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。 UseSSL 是額外的保護，可透過 HTTPS (而非 HTTP) 傳送資料。 若您使用此參數，但是命令所用的連接埠上無法使用 SSL，則命令會失敗。

## <a name="see-also"></a>另請參閱

- [about_ActivityCommonParameters](about_ActivityCommonParameters.md)
- [about_Workflows](about_Workflows.md)
- [Invoke-AsWorkflow](xref:PSWorkflowUtility.Invoke-AsWorkflow)
- [New-PSWorkflowExecutionOption](xref:PSWorkflow.New-PSWorkflowExecutionOption)
- [New-PSWorkflowSession](xref:PSWorkflow.New-PSWorkflowSession)
