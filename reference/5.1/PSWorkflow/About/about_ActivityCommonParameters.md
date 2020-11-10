---
description: 描述 Windows PowerShell 工作流程新增至活動的參數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: 93fdcdb9c5afe0b73e843baf2474ec7d3f96a6cf
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387799"
---
# <a name="about-activitycommonparameters"></a>關於 ActivityCommonParameters

## <a name="short-description"></a>簡短描述

描述 Windows PowerShell 工作流程新增至活動的參數。

## <a name="long-description"></a>詳細描述

Windows PowerShell 工作流程會將活動一般參數加入至衍生自 PSActivity 基類的活動。 此類別包括 InlineScript 活動，以及實作為活動的 Windows PowerShell Cmdlet，例如 Get-Process 和 New-winevent。

活動一般參數在 Suspend-Workflow 和 Checkpoint-Workflow 活動上無效，並且不會加入至 Windows PowerShell 工作流程在 InlineScript 腳本區塊或類似活動中自動執行的 Cmdlet 或運算式。 活動一般參數在 InlineScript 活動中可以使用，但在 InlineScript 指令碼區塊中的命令中無法使用。

數個活動一般參數也是工作流程一般參數或 Windows PowerShell 一般參數。 其他活動一般參數對活動是唯一的。

如需工作流程一般參數的詳細資訊，請參閱 about_WorkflowCommonParameters。 如需 Windows PowerShell 一般參數的詳細資訊，請參閱 about_CommonParameters。

### <a name="list-of-activity-common-parameters"></a>活動一般參數的清單

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a>參數描述

本章節描述活動一般參數。

#### <a name="appendoutput-boolean"></a>AppendOutput \<Boolean\>

的值會 `$True` 將活動的輸出加入變數的值。
的值 `$False` 沒有任何作用。 根據預設，會將值指派給變數來取代變數值。

例如，下列命令會將處理常式物件新增至變數中的服務物件 `$x` 。

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

此參數是針對以 XAML 為基礎的工作流程所設計。 在腳本工作流程中，您也可以使用 + = 指派運算子將輸出新增至變數的值，如下列範例所示。

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a>調試 \<SwitchParameter\>

顯示命令所執行之作業的程式設計人員層級詳細資料。
Debug 參數會覆寫目前命令之 $DebugPreference 變數的值。 只有當命令產生調試訊息時，此參數才有效。 此參數也是 Windows PowerShell 一般參數。

#### <a name="displayname-string"></a>DisplayName \<String\>

指定活動的好記名稱。 當工作流程執行時，以及在工作流程工作的進度屬性值中，DisplayName 值會出現在進度列中。 當命令中也包含 PSProgressMessage 參數時，進度列內容會顯示為 \<DisplayName\> ： \<PSProgressMessage\> format。

#### <a name="erroraction-actionpreference"></a>ErrorAction \<ActionPreference\>

決定活動如何回應來自命令的非終止錯誤。 它不會影響終止錯誤。 此參數只適用于命令產生非終止錯誤，例如來自 Write-Error Cmdlet 的錯誤。 ErrorAction 參數會覆寫目前命令之 $ErrorActionPreference 變數的值。 此參數也是 Windows PowerShell 一般參數。

有效值：

- 繼續。 顯示錯誤訊息，並繼續執行命令。 [繼續] 是預設值。

- 忽略。 隱藏錯誤訊息，並繼續執行命令。
  不同于 SilentlyContinue，Ignore 不會將錯誤訊息加入 $Error 的自動變數中。 忽略值是在 Windows PowerShell 3.0 中引進。

- 詢問。 顯示錯誤訊息，並在繼續執行之前提示您確認。 此值很少使用。

- 擱置： 自動暫停工作流程工作，以允許進一步調查。 經過調查之後，即可繼續工作流程。

- SilentlyContinue. 隱藏錯誤訊息，並繼續執行命令。

- 停止。 顯示錯誤訊息，並停止執行命令。

#### <a name="input-object"></a>輸入 \<Object[]\>

將物件集合提交給活動。 這是使用管線，一次將物件傳給一個活動的替代方案。

#### <a name="mergeerrortooutput-boolean"></a>MergeErrorToOutput \<Boolean\>

的值會 `$True` 將錯誤加入至輸出資料流程。 的值 `$False` 沒有作用。 使用此參數搭配 Parallel 和 `ForEach -Parallel` 關鍵字，從單一集合的多個平行命令收集錯誤和輸出。

#### <a name="psactionretrycount-int32"></a>PSActionRetryCount \<Int32\>

若第一次嘗試失敗，則重複試著執行活動。 預設值 0 不會重試。

#### <a name="psactionretryintervalsec-int32"></a>PSActionRetryIntervalSec \<Int32\>

判斷動作的重試間隔，以秒為單位。 預設值為 0，立即重試動作。 只有當命令中也使用 PSActionRetryCount 參數時，此參數才有效。

#### <a name="psactionrunningtimeoutsec-int32"></a>PSActionRunningTimeoutSec \<Int32\>

決定每部目標電腦上活動的執行時間。 如果活動未在超時時間過期之前完成，Windows PowerShell 工作流程會產生終止錯誤，並停止處理受影響之目的電腦上的工作流程。

#### <a name="psallowredirection-boolean"></a>PSAllowRedirection \<Boolean\>

值為 $True 允許將連接重新導向至目的電腦。
$False 的值沒有任何作用。 此活動一般參數也是工作流程一般參數。

當您使用 PSConnectionURI 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。 根據預設，Windows PowerShell 不會重新導向連線，但是您可以使用 PSAllowRedirection 參數搭配 $True 值，以允許將連接重新導向至目的電腦。

您也可以藉由設定喜好設定變數的 MaximumConnectionRedirectionCount 屬性 `$PSSessionOption` ，或建立會話之 Cmdlet 的 SSessionOption 參數值的 MaximumConnectionRedirectionCount 屬性，來限制連接重新導向的次數。 預設值為 5。

#### <a name="psapplicationname-string"></a>PSApplicationName \<String\>

指定連接 URI 用來連接目的電腦的應用程式名稱區段。 當您沒有在命令中使用 ConnectionURI 參數時，請使用這個參數來指定應用程式名稱。 此活動一般參數也是工作流程一般參數。

預設值是 `$PSSessionApplicationName` 目的電腦上的喜好設定變數值。 若未定義此喜好設定變數，則預設值是 WSMAN。 這個值適用於大部分用途。 如需詳細資訊，請參閱 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。 此參數的值應該符合遠端電腦上接聽程式之 URLPrefix 屬性的值。

#### <a name="psauthentication-authenticationmechanism"></a>PSAuthentication \<AuthenticationMechanism\>

指定在連接到目的電腦時，用來驗證使用者認證的機制。 有效值為 Default、Basic、Credssp、Digest、Kerberos、Negotiate 與 NegotiateWithImplicitCredential。 預設值為 Default。 此活動一般參數也是工作流程一般參數。

如需此參數值的詳細資訊，請參閱 PowerShell SDK 中 **AuthenticationMechanism** 列舉的說明。

> [!WARNING]
> 使用者認證會傳遞至要驗證之遠端電腦的「認證安全性服務提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

#### <a name="pscertificatethumbprint-string"></a>PSCertificateThumbprint \<String\>

對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。 請輸入憑證的憑證指紋。 此活動一般參數也是工作流程一般參數。

憑證將用於用戶端憑證式驗證。 這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證，請使用 Windows PowerShell Cert：磁片磁碟機中的 [get-Item](xref:Microsoft.PowerShell.Management.Get-Item) 或 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) Cmdlet。

#### <a name="pscomputername-string"></a>PSComputerName \<String[]\>

指定活動執行所在的目的電腦。 預設是本機電腦。 此活動一般參數也是工作流程一般參數。

請輸入 NETBIOS 名稱、IP 位址或是一部或多部電腦的完整網域名稱 (以逗號分隔的清單方式)。 若要指定本機電腦，請輸入電腦名稱、"localhost" 或句點 (.)。

若要在 PSComputerName 參數的值中包含本機電腦，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。

如果從命令省略此參數，或它的值為 $null 或空字串，則工作流程目標是本機電腦，而且不會使用 Windows PowerShell 遠端執行命令。

若要在 ComputerName 參數的值中使用 IP 位址，命令必須包含 PSCredential 參數。 此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。 如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)中的「如何將電腦新增到信任的主機清單」。

#### <a name="psconfigurationname-string"></a>PSConfigurationName \<String\>

指定用來在目的電腦上建立會話的會話設定。 請在目的電腦上輸入會話設定的名稱， (不在執行工作流程的電腦上。 預設值為 [Microsoft. PowerShell]。 此活動一般參數也是工作流程一般參數。

#### <a name="psconnectionretrycount-uint"></a>PSConnectionRetryCount \<UInt\>

指定第一次連線嘗試失敗時，嘗試連接至每部目的電腦的次數上限。 輸入介於1和 4294967295 (UInt) 之間的數位。 預設值為零 (0) 表示無重試嘗試。
此活動一般參數也是工作流程一般參數。

#### <a name="psconnectionretryintervalsec-uint"></a>PSConnectionRetryIntervalSec \<UInt\>

指定連接重試嘗試之間的延遲（以秒為單位）。 預設值為零 (0)。 只有當 PSConnectionRetryCount 的值至少為1時，此參數才有效。 此活動一般參數也是工作流程一般參數。

#### <a name="psconnectionuri-systemuri"></a>PSConnectionURI \<System.Uri\>

指定 (URI) 的統一資源識別項，以定義目的電腦上活動的連接端點。 此 URI 必須是完整的 URI。 此活動一般參數也是工作流程一般參數。

這個字串的格式如下所示：

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

預設值是 `http://localhost:5985/WSMAN`。

如果您未指定 PSConnectionURI，您可以使用 PSUseSSL、PSComputerName、PSPort 和 PSApplicationName 參數來指定 PSConnectionURI 值。

URI 的 Transport 區段有效值為 HTTP 與 HTTPS。 若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。 若要使用預設連接埠於 Windows PowerShell 遠端功能，請為 HTTP 指定連接埠 5985，或是為 HTTPS 指定連接埠 5986。

#### <a name="pscredential-pscredential"></a>PSCredential \<PSCredential\>

指定具有在目的電腦上執行活動之許可權的使用者帳戶。 預設為目前使用者。 只有當命令中包含 PSComputerName 參數時，此參數才有效。 此活動一般參數也是工作流程一般參數。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入包含 PSCredential 物件的變數，例如 Get-Credential Cmdlet 所傳回的物件。 若您只輸入使用者名稱，將會提示您輸入密碼。

#### <a name="psdebug-psdatacollectiondebugrecord"></a>Set-psdebug \<PSDataCollection[DebugRecord]\>

將偵錯工具訊息從活動加入至指定的 debug 記錄集合，而不是將偵錯工具訊息寫入主控台，或工作流程作業的 Debug 屬性值。 您可以將多個活動的偵錯訊息，新增至相同的偵錯記錄集合物件。

若要使用此活動一般參數，請使用 New-Object Cmdlet 來建立 DebugRecord 類型的 C o n 物件，並將物件儲存在變數中。 然後，將變數做為一或多個活動的 Set-psdebug 參數值，如下列範例所示。

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a>PSDisableSerialization \<Boolean\>

指示活動將「即時」(未序列化) 物件傳回至工作流程。
產生的物件具有方法與屬性，但它們無法在取得檢查點時儲存。

#### <a name="psdisableserializationpreference-boolean"></a>PSDisableSerializationPreference \<Boolean\>

將 PSDisableSerialization 參數的對等項套用至整個工作流程，而不只是活動。 通常不建議加入這個參數，因為無法繼續或保存未序列化其物件的工作流程。

有效值：

-  (預設) 如果省略，而且您尚未將 PSDisableSerialization 參數加入至活動，則會序列化物件。

- `$True`. 指示工作流程中的所有活動傳回「即時」(未序列化) 物件。 產生的物件具有方法與屬性，但它們無法在取得檢查點時儲存。
- `$False`. 工作流程物件會序列化。

#### <a name="pserror-psdatacollectionerrorrecord"></a>PSError \<PSDataCollection[ErrorRecord]\>

將錯誤訊息從活動加入至指定的錯誤記錄集合，而不是將錯誤訊息寫入主控台，或工作流程工作的錯誤屬性值。 您可以將多個活動的錯誤訊息，新增至相同的錯誤記錄集合物件。

若要使用此活動一般參數，請使用 `New-Object` Cmdlet 來建立 c o n 物件，其類型為 ErrorRecord，並將物件儲存在變數中。 然後，將變數做為一或多個活動的 PSError 參數值，如下列範例所示。

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a>PSPersist \<Boolean\>

接受活動之後的檢查點。 除了在工作流程中指定的檢查點之外，此檢查點也是。 此活動一般參數也是工作流程一般參數。

「檢查點」或「持續點」是工作流程狀態的快照，以及工作流程執行時所捕捉到的資料，並儲存到磁片上的持續性存放區。 Windows PowerShell 工作流程使用儲存的資料，從上一個持續點繼續暫停或中斷的工作流程，而不是重新開機工作流程。

有效值：

-  (預設) 如果您省略此參數，則不會新增任何檢查點。 檢查點會根據工作流程的設定取得。

- `$True`. 在活動完成後採取檢查點。
  除了在工作流程中指定的檢查點之外，此檢查點也是。

- `$False`. 未新增任何檢查點。 只有在工作流程中指定時，才會採取檢查點。

#### <a name="psport-int32"></a>PSPort \<Int32\>

指定目的電腦上的網路埠。 預設連接埠是 5985 (用於 HTTP 的 WinRM 連接埠) 和 5986 (用於 HTTPS 的 WinRM 連接埠)。 此活動一般參數也是工作流程一般參數。

除非您必須這樣做，否則請勿使用 PSPort 參數。 命令中設定的埠會套用到命令執行所在的所有電腦或會話。 替代的連接埠設定可能使得命令無法在全部電腦上執行。 使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。

#### <a name="psprogress-psdatacollectionprogressrecord"></a>PSProgress \<PSDataCollection[ProgressRecord]\>

將進度訊息從活動加入至指定的進度記錄集合，而不是將進度訊息寫入主控台，或工作流程作業的進度屬性值。 您可以將多個活動的進度訊息，新增至相同的進度記錄集合物件。

#### <a name="psprogressmessage-string"></a>PSProgressMessage \<String\>

指定活動的易記描述。 當工作流程執行時，PSProgressMessage 值會出現在進度列中。 當命令中也包含 DisplayName 時，進度列內容會顯示為 \<DisplayName\> ： \<PSProgressMessage\> format。

這個參數特別適合用來識別 ForEach 平行腳本區塊中的活動。 若缺欠此訊息，會以相同的名稱識別所有平行分支中的活動。

#### <a name="psremotingbehavior-remotingbehavior"></a>PSRemotingBehavior \<RemotingBehavior\>

指定在目標電腦上執行活動時要如何管理遠端處理。
PowerShell 是預設值。

有效值為：

- 無：活動不會在遠端電腦上執行。

- PowerShell： Windows PowerShell 遠端處理是用來在目的電腦上執行活動。

- Custom：活動支援它自己的遠端處理類型。 當實作為活動的 Cmdlet 將 RemotingCapability 屬性的值設定為 SupportedByCommand，且命令包含 ComputerName 參數時，這個值就有效。

#### <a name="psrequiredmodules-string"></a>PSRequiredModules \<String[]\>

執行命令前匯入指定的模組。 輸入模組名稱。 這些模組必須安裝在目的電腦上。

在模組中第一次使用任何命令時，會自動匯入 PSModulePath 環境變數所指定的路徑中所安裝的模組。
使用這個參數來匯入不在 PSModulePath 位置中的模組。

因為工作流程中的每個活動是在其自己的工作階段中執行，所以 Import-Module 命令只會將模組匯入到執行它的工作階段中。 它不會將模組匯入到執行其他活動的工作階段。

#### <a name="pssessionoption-pssessionoption"></a>PSSessionOption \<PSSessionOption\>

將會話的 advanced 選項設定為目的電腦。 輸入 PSSessionOption 物件，例如您使用 New-PSSessionOption Cmdlet 建立的物件。 此活動一般參數也是工作流程一般參數。

會話選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。 否則，會話會使用會話設定中指定的值。

如需會話選項的描述（包括預設值），請參閱 New-PSSessionOption Cmdlet [PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)的說明主題。

如需 $PSSessionOption 喜好設定變數的詳細資訊，請參閱 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

#### <a name="psusessl-boolean"></a>PSUseSSL \<Boolean\>

$True 的值會使用安全通訊端層 (SSL) 通訊協定來建立與目的電腦的連線。 預設不會使用 SSL。 $False 的值沒有任何作用。 此活動一般參數也是工作流程一般參數。

WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。 UseSSL 是額外的保護，可透過 HTTPS (而非 HTTP) 傳送資料。 若您使用此參數，但是命令所用的連接埠上無法使用 SSL，則命令會失敗。

#### <a name="psverbose-psdatacollectionverboserecord"></a>PSVerbose \<PSDataCollection[VerboseRecord]\>

將詳細資訊訊息從活動加入至指定的詳細資訊記錄集合，而不是將詳細資訊訊息寫入主控台，或工作流程工作的詳細資訊屬性值。 您可以將多個活動的詳細資訊訊息，新增至相同的詳細資訊記錄集合物件。

#### <a name="pswarning-psdatacollectionwarningrecord"></a>PSWarning \<PSDataCollection[WarningRecord]\>

將警告訊息從活動加入至指定的警告記錄集合，而不是將警告訊息寫入主控台，或工作流程工作的 Warning 屬性值。 您可以將多個活動的警告訊息，新增至相同的警告記錄集合物件。

#### <a name="result"></a>結果

這個參數只在 XAML 工作流程中有效。

#### <a name="usedefaultinput-boolean"></a>UseDefaultInput \<Boolean\>

接受所有的工作流程輸入做為活動的輸入值。

例如，下列範例工作流程中的 Get-Process 活動會使用 UseDefaultInput 活動一般參數來取得傳遞至工作流程的輸入。 使用輸入執行工作流程時，該輸入由活動使用。

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a>詳細 \<SwitchParameter\>

顯示命令所執行之作業的詳細資訊。
這項資訊與追蹤或交易記錄檔中的資訊類似。
Verbose 參數會覆寫目前命令之 $VerbosePreference 變數的值。 此參數只適用于命令產生詳細訊息時。 此參數也是 Windows PowerShell 一般參數。

#### <a name="warningaction-actionpreference"></a>WarningAction \<ActionPreference\>

決定活動回應警告的方式。 [繼續] 是預設值。 WarningAction 參數會覆寫目前命令之 $WarningPreference 變數的值。 只有當命令產生警告訊息時，此參數才有效。 此參數也是 Windows PowerShell 一般參數。

有效值：

- SilentlyContinue. 隱藏警告訊息，並繼續執行命令。

- 繼續。 顯示警告訊息，並繼續執行命令。
  [繼續] 是預設值。

- 詢問。 顯示警告訊息，並在繼續執行之前提示您確認。 此值很少使用。

- 停止。 顯示警告訊息，並停止執行命令。

> [!NOTE]
> 當命令中使用參數來執行腳本或函式時，WarningAction 參數不會覆寫 $WarningAction 喜好設定變數的值。

### <a name="examples"></a>範例

活動一般參數非常有用。 例如，您可以使用 PSComputerName 參數，只在目的電腦的子集上執行特定的活動。

或者，您可以使用 PSConnectionRetryCount 和 PSConnectionRetryIntervalSec 參數來調整特定活動的重試值。

下列範例示範如何使用 PSComputerName 活動一般參數，只在特定網域的電腦上執行 Get-EventLog 活動。

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a>另請參閱

[about_Workflows](about_workflows.md) 
[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)
