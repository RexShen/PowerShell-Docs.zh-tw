---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 DSC 來建置持續整合和持續部署管線
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954235"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>使用 DSC 來建置持續整合和持續部署管線

此範例示範如何使用 PowerShell、DSC、Pester 及 Visual Studio Team Foundation Server (TFS) 來建置「持續整合/持續部署」(CI/CD) 管線。

建置並設定管線之後，您便可以使用它來完整部署、設定及測試 DNS 伺服器和相關的主機記錄。
此程序會模擬將在開發環境中使用之管線的第一個部分。

自動化的 CI/CD 管線可協助您以更快且更可靠的方式更新軟體，確保所有程式碼都經過測試，並且您程式碼的最新組建隨時可供使用。

## <a name="prerequisites"></a>必要條件

若要使用此範例，您應該熟悉下列各項知識：

- CI-CD 概念。 如需詳細的參考資料，請參閱[發行管線模型](https://aka.ms/thereleasepipelinemodelpdf) \(英文\)。
- [Git](https://git-scm.com/) 原始檔控制
- [Pester](https://github.com/pester/Pester) 測試架構
- [Team Foundation Server](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a>您將需要

若要建置和執行此範例，您將需要一個有數台電腦和/或虛擬機器的環境。

### <a name="client"></a>Client

這是您將進行所有設定和執行範例之工作的電腦。

用戶端電腦必須是已安裝下列各項的 Windows 電腦：

- [Git](https://git-scm.com/)
- 從 https://github.com/PowerShell/Demo_CI 複製的本機 Git 儲存機制
- 文字編輯器，例如 [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

裝載 TFS 伺服器且您將定義組建和版本的電腦。
此電腦上必須安裝 [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/)。

### <a name="buildagent"></a>BuildAgent

執行建置專案之 Windows 組建代理程式的電腦。
此電腦上必須安裝及執行 Windows 組建代理程式。
如需有關如何安裝及執行 Windows 組建代理程式的指示，請參閱[在 Windows 上部署代理程式](/azure/devops/pipelines/agents/v2-windows) \(英文\)。

您還必須在此電腦上安裝 `xDnsServer` 和 `xNetworking` DSC 模組。

### <a name="testagent1"></a>TestAgent1

這是此範例中的 DSC 設定所設定為 DNS 伺服器的電腦。
此電腦必須執行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。

### <a name="testagent2"></a>TestAgent2

這是裝載此範例所設定之網站的電腦。
此電腦必須執行 [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)。

## <a name="add-the-code-to-tfs"></a>將程式碼新增至 TFS

我們一開始會在 TFS 中建立 Git 儲存機制，並從您在用戶端電腦上的本機儲存機制匯入程式碼。
如果您尚未將 Demo_CI 儲存機制複製到您的用戶端電腦上，請立即執行下列 Git 命令來執行此操作：

`git clone https://github.com/PowerShell/Demo_CI`

1. 在您的用戶端電腦上，於網頁瀏覽器中瀏覽至您的 TFS 伺服器。
1. 在 TFS 中，[建立一個新的小組專案](/azure/devops/organizations/projects/create-project)並命名為 Demo_CI。

   請確定將 [版本控制]  設定為 [Git]  。
1. 在您的用戶端電腦上，使用下列命令為您剛在 TFS 中建立的儲存機制新增遠端：

   `git remote add tfs <YourTFSRepoURL>`

   其中 `<YourTFSRepoURL>` 是您在上一個步驟中所建立之 TFS 儲存機制的複製 URL。

   如果您不知道哪裡可以找到此 URL，請參閱[複製現有的 Git 儲存機制](/azure/devops/repos/git/clone) \(英文\)。
1. 使用下列命令將程式碼從您的本機儲存機制推送到 TFS 儲存機制：

   `git push tfs --all`
1. 將會在 TFS 儲存機制中填入 Demo_CI 程式碼。

> [!NOTE]
> 本範例使用 Git 存放庫之 `ci-cd-example` 分支中的程式碼。
> 請務必指定此分支作為您 TFS 專案中及您所建立之 CI/CD 觸發程序的預設分支。

## <a name="understanding-the-code"></a>了解程式碼

在建立這些組建與部署管線之前，讓我們先來看看部分程式碼以了解情況。
在您的用戶端電腦上，開啟您慣用的文字編輯器，然後瀏覽至 Demo_CI Git 儲存機制的根目錄。

### <a name="the-dsc-configuration"></a>DSC 設定

開啟檔案 `DNSServer.ps1` (從本機 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Configs/DNSServer.ps1`)。

此檔案包含設定 DNS 伺服器的 DSC 設定。 以下是其全部：

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

請注意 `Node` 陳述式：

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

這會尋找[設定資料](../configurations/configData.md) (由 `DevEnv.ps1` 指令碼所建立) 中所有已定義為具備 `DNSServer` 角色的節點。

您可以在 [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays) 中深入閱讀 `Where` 方法

進行 CI 時，使用設定資料來定義節點相當重要，因為節點資訊在環境之間可能會有所變更，而使用設定資料則可讓您不須變更設定程式碼，即可輕鬆對節點資訊進行變更。

在第一個資源區塊中，此設定會呼叫 **WindowsFeature** 以確保啟用 DNS 功能。
接下來的資源區塊會從 [xDnsServer](https://github.com/PowerShell/xDnsServer) 模組呼叫資源，以設定主要區域和 DNS 記錄。

請注意，兩個 `xDnsRecord` 區塊皆包裝在 `foreach` 迴圈中，這些迴圈會逐一查看設定資料中的陣列。
此設定資料同樣也是 `DevEnv.ps1` 指令碼所建立的，接下來將會探討此設定資料。

### <a name="configuration-data"></a>設定資料

`DevEnv.ps1` 檔案 (從本機 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/DevEnv.ps1`) 會在雜湊表中指定環境特定設定資料，然後將該雜湊表傳遞給對 `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`) 中定義之 `New-DscConfigurationDataDocument` 函式的呼叫。

`DevEnv.ps1` 檔案：

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

`New-DscConfigurationDataDocument` 函式 (定義於 `\Assets\DscPipelineTools\DscPipelineTools.psm1`) 會以程式設計方式，從以 `RawEnvData` 和 `OtherEnvData` 參數的形式傳遞的雜湊表 (節點資料) 和陣列 (非節點資料) 建立設定資料文件。

在我們的案例中，只使用 `RawEnvData` 參數。

### <a name="the-psake-build-script"></a>psake 建置指令碼

`Build.ps1` (從 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Build.ps1`) 中定義的 [psake](https://github.com/psake/psake) 建置指令碼會定義組建所含的工作。
它也定義每個工作所依存的其他工作。
當叫用 psake 指令碼時，它會確保指定的工作 (如果未指定任何工作，則是名為 `Default` 的工作) 執行，並且所有相依項目也一併執行 (這是遞迴的，因此相依項目的相依項目也會執行，依此類推)。

在此範例中，`Default` 是定義為：

```powershell
Task Default -depends UnitTests
```

`Default` 工作本身沒有任何實作，但依存於 `CompileConfigs` 工作。
產生的工作相依性鏈結會確保執行建置指令碼中的所有工作。

在此範例中，是透過呼叫 `Initiate.ps1` 檔案 (位於 Demo_CI 儲存機制的根目錄) 中的 `Invoke-PSake` 來叫用 psake 指令碼：

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

當我們在 TFS 中為範例建立組建定義時，將會提供 psake 指令碼檔作為此指令碼的 `fileName` 參數。

建置指令碼會定義下列工作：

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

會執行 `DevEnv.ps1` 以產生設定資料檔。

#### <a name="installmodules"></a>InstallModules

會安裝設定 `DNSServer.ps1` 所需的模組。

#### <a name="scriptanalysis"></a>ScriptAnalysis

會呼叫 [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)。

#### <a name="unittests"></a>UnitTests

會執行 [Pester](https://github.com/pester/Pester/wiki) 單元測試。

#### <a name="compileconfigs"></a>CompileConfigs

會使用 `GenerateEnvironmentFiles` 工作所產生的設定資料，將設定 (`DNSServer.ps1`) 編譯成 MOF 檔案。

#### <a name="clean"></a>Clean

會建立用於範例的資料夾，並移除來自先前回合的所有測試結果、設定資料檔及模組。

### <a name="the-psake-deploy-script"></a>psake 部署指令碼

`Deploy.ps1` (從 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Deploy.ps1`) 中定義的 [psake](https://github.com/psake/psake) 部署指令碼會定義部署和執行設定的工作。

`Deploy.ps1` 會定義下列工作：

#### <a name="deploymodules"></a>DeployModules

會在 `TestAgent1` 上啟動 PowerShell 工作階段，並安裝包含設定所需 DSC 資源的模組。

#### <a name="deployconfigs"></a>DeployConfigs

會呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 以在 `TestAgent1` 上執行設定。

#### <a name="integrationtests"></a>IntegrationTests

會執行 [Pester](https://github.com/pester/Pester/wiki) 整合測試。

#### <a name="acceptancetests"></a>AcceptanceTests

會執行 [Pester](https://github.com/pester/Pester/wiki) 接受度測試。

#### <a name="clean"></a>Clean

會移除在先前回合中安裝的所有模組，並確保測試結果資料夾存在。

### <a name="test-scripts"></a>測試指令碼

接受度、整合及單元測試是在 `Tests` 資料夾 (從 Demo_CI 儲存機制的根目錄路徑為 `./InfraDNS/Tests`) 內的指令碼中定義的，各分別在其個別資料夾內名為 `DNSServer.tests.ps1` 的檔案中。

測試指令碼會使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 語法。

#### <a name="unit-tests"></a>單元測試

單元測試會測試 DSC 設定本身，以確保設定在執行時會執行預期執行的工作。
單元測試指令碼會使用 [Pester](https://github.com/pester/Pester/wiki)。

#### <a name="integration-tests"></a>整合測試

整合測試會測試系統的設定，以確保當與其他元件整合時，會依照預期的方式設定系統。 使用 DSC 來設定這些測試之後，這些測試就會在目標節點上執行。
整合測試指令碼會混合使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 語法。

#### <a name="acceptance-tests"></a>接受度測試

接受度測試會測試系統，以確保系統依照預期的方式運作。
例如，它會測試來確保在查詢時，網頁會傳回正確的資訊。
這些測試會從目標節點的遠端執行，以測試真實世界案例。
整合測試指令碼會混合使用 [Pester](https://github.com/pester/Pester/wiki) 和 [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) 語法。

## <a name="define-the-build"></a>定義組建

既然我們已將程式碼上傳到 TFS 並查看其功能，現在即可開始定義組建。

在這裡，我們將只涵蓋您將新增到組建中的建置步驟。 如需有關如何在 TFS 中建立組建定義的指示，請參閱[建立組建定義並將其排入佇列](/azure/devops/pipelines/create-first-pipeline) \(英文\)。

請建立一個名為 "InfraDNS" 的新組建定義 (選取 [空白]  範本)。
將下列步驟新增到您的組建定義中：

- PowerShell 指令碼
- 發行測試結果
- 複製檔案
- 發行成品

新增這些建置步驟之後，請依下列方式編輯每個步驟的屬性：

### <a name="powershell-script"></a>PowerShell 指令碼

1. 將 [類型]  屬性設定為 `File Path`。
1. 將 [指令碼路徑]  屬性設定為 `initiate.ps1`。
1. 將 `-fileName build` 新增到 [引數]  屬性。

此建置步驟會執行 `initiate.ps1` 檔案以呼叫 psake 建置指令碼。

### <a name="publish-test-results"></a>發行測試結果

1. 將 [測試結果格式]  設定為 `NUnit`
1. 將 [測試結果檔案]  設定為 `InfraDNS/Tests/Results/*.xml`
1. 將 [測試回合標題]  設定為 `Unit`。
1. 確定已選取 [啟用]  和 [永遠執行]  這兩個 [控制選項]  。

此建置步驟會執行我們先前查看之 Pester 指令碼中的單元測試，然後將結果儲存在 `InfraDNS/Tests/Results/*.xml` 資料夾中。

### <a name="copy-files"></a>複製檔案

1. 將下列每一行新增到 [內容]  中：

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. 將 [目標資料夾]  設定為 `$(Build.ArtifactStagingDirectory)\`

此步驟會將建置和測試指令碼複製到暫存目錄中，以便供下一個步驟發行成組建成品。

### <a name="publish-artifact"></a>發行成品

1. 將 [要發行的路徑]  設定為 `$(Build.ArtifactStagingDirectory)\`
1. 將 [成品名稱]  設定為 `Deploy`
1. 將 [成品類型]  設定為 `Server`
1. 在 [控制選項]  中選取 [`Enabled`]

## <a name="enable-continuous-integration"></a>啟用持續整合

現在我們將設定一個觸發程序，此觸發程序會在每當有任何變更簽入 Git 儲存機制的 `ci-cd-example` 分支中時，便促使專案進行建置。

1. 在 TFS 中，按一下 [建置及發行]  索引標籤
1. 選取 `DNS Infra` 組建定義，然後按一下 [編輯] 
1. 按一下 [觸發程序]  索引標籤
1. 選取 [持續整合 (CI)]  ，然後從分支下拉式清單中選取 `refs/heads/ci-cd-example`
1. 按一下 [儲存]  ，然後按一下 [確定] 

現在 TFS Git 儲存機制中的任何變更都會觸發自動化建置。

## <a name="create-the-release-definition"></a>建立發行定義

讓我們來建立一個發行定義，以便在每次簽入程式碼時，都將專案部署到開發環境。

若要這樣做，請新增一個與您先前建立之 `InfraDNS` 組建定義關聯的新發行定義。
請務必選取 [持續部署]  ，以便在每次完成新組建時便觸發新的發行。
([什麼是發行管線？](/azure/devops/pipelines/release/))，並設定它，如下所示：

將下列步驟新增到發行定義中：

- PowerShell 指令碼
- 發行測試結果
- 發行測試結果

依下列方式編輯步驟：

### <a name="powershell-script"></a>PowerShell 指令碼

1. 將 [指令碼路徑]  欄位設定為 `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. 將 [引數]  欄位設定為 `-fileName Deploy`

### <a name="first-publish-test-results"></a>第一個發行測試結果

1. 為 [測試結果格式]  欄位選取 [`NUnit`]
1. 將 [測試結果檔案]  欄位設定為 `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. 將 [測試回合標題]  設定為 `Integration`
1. 在 [控制選項]  底下，選取 [永遠執行] 

### <a name="second-publish-test-results"></a>第二個發行測試結果

1. 為 [測試結果格式]  欄位選取 [`NUnit`]
1. 將 [測試結果檔案]  欄位設定為 `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. 將 [測試回合標題]  設定為 `Acceptance`
1. 在 [控制選項]  底下，選取 [永遠執行] 

## <a name="verify-your-results"></a>驗證您的結果

現在，每當您將 `ci-cd-example` 分支中的變更推送到 TFS 時，就會開始一個新的組建。
如果組建順利完成，就會觸發新的部署。

您可以在用戶端電腦上開啟瀏覽器並瀏覽至 `www.contoso.com`，來檢查部署結果。

## <a name="next-steps"></a>接下來的步驟

此範例會設定 DNS 伺服器 `TestAgent1`，讓 URL `www.contoso.com` 解析成 `TestAgent2`，但它並不會實際部署網站。
儲存機制的 `WebApp` 資料夾底下有提供此做法的基本架構。
您可以使用提供的 Stub 來建立 psake 指令碼、Pester 測試及 DSC 設定，以部署您自己的網站。
