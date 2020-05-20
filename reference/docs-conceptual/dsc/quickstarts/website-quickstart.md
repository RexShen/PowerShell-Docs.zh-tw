---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 快速入門 - 使用 DSC 建立網站
ms.openlocfilehash: 08ca25604998ce8c913ef8112b5342f2e0216b6e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "75416123"
---
# <a name="quickstart---create-a-website-with-desired-state-configuration-dsc"></a>快速入門 - 使用 Desired State Configuration (DSC) 來建立網站

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

這個練習會從頭開始完整地逐步建立並套用預期狀態設定 (DSC)。
我們將使用的範例會確保伺服器已啟用 `Web-Server` (IIS) 功能，且在該伺服器的 `inetpub\wwwroot` 目錄中有簡單 "Hello World" 網站的內容。

如需 DSC 及其運作方式的概觀，請參閱[適合決策者的預期狀態設定概觀](../overview/decisionMaker.md)。

## <a name="requirements"></a>需求

若要執行此範例，您將需要執行 Windows Server 2012 或更新版本的電腦，以及 PowerShell 4.0 或更新版本。

## <a name="write-and-place-the-indexhtm-file"></a>撰寫並放置 index.htm 檔案

首先，我們會建立 HTML 檔案，將它用來做為網站內容。

在您的根資料夾中，建立名為 `test` 的資料夾。

在文字編輯器中，輸入下列文字：

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

將此內容在您稍早建立的 `test` 資料夾中另存為 `index.htm`。

## <a name="write-the-configuration"></a>撰寫設定

[DSC 設定](../configurations/configurations.md)是特殊的 PowerShell 函式，可定義您想要設定一或多部目標電腦 (節點) 的方式。

在 PowerShell ISE 中，輸入下列命令：

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

將檔案儲存為 `WebsiteTest.ps1`。

您可以看到它看起來像是 PowerShell 函式，並在函式名稱前使用額外的關鍵字 **Configuration**。

**Node** 區塊會指定要設定的目標節點。 在此案例中為 `localhost`。

設定會呼叫兩個[資源](../resources/resources.md)，**WindowsFeature** 和 **File**。
資源會確保目標節點處於設定所定義的狀態。

## <a name="compile-the-configuration"></a>編譯設定

DSC 設定若要套用至節點，便必須先編譯成 MOF 檔案。
若要這麼做，您要如函式一般執行設定。
在 PowerShell 主控台中，瀏覽至您儲存設定的同一個資料夾，並執行下列命令以將設定編譯成 MOF 檔案：

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

這會產生下列輸出：

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

第一行會使設定函式可在主控台中使用。
第二行會執行設定。
結果會在目前資料夾中，建立名為 `WebsiteTest` 的新子資料夾。
`WebsiteTest` 資料夾包含名稱為 `localhost.mof` 的檔案。
這是可接著套用至目標節點的檔案。

## <a name="apply-the-configuration"></a>套用設定

現在您已經有已編譯的 MOF，您接著可呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來將設定套用至目標節點 (在本範例中為本機電腦)。

`Start-DscConfiguration` Cmdlet 會要求[本機設定管理員 (LCM)](../managing-nodes/metaConfig.md) (也就是 DSC 的引擎) 套用設定。
LCM 會呼叫 DSC 資源以套用設定。

> [!NOTE]
> 若要允許 DSC 執行，就必須將 Windows 設定成即使在您執行 `localhost` 設定時，也接收 PowerShell 遠端命令。 若要輕鬆正確地設定您的環境，只要在已提高權限的 PowerShell 終端機中執行 `Set-WsManQuickConfig -Force` 即可。

在 PowerShell 主控台中，瀏覽至您儲存設定的同一個資料夾，並執行下列命令：

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>測試組態

您可以呼叫 [Get DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) Cmdlet 來查看設定是否成功。

您也可以直接測試結果，在本範例中是透過網頁瀏覽器瀏覽至 `http://localhost/`。
您應該會看到您做為本範例的第一個步驟所建立的 "Hello World" HTML 頁面。

## <a name="next-steps"></a>後續步驟

- 在 [DSC 設定](../configurations/configurations.md)中深入了解 DSC 設定。
- 在 [DSC 資源](../resources/resources.md)中查看可用的 DSC 資源，以及如何建立自訂 DSC 資源。
- 在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。
