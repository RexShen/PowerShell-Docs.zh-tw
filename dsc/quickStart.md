---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 預期狀態設定快速入門
ms.openlocfilehash: eb7572f39f7a2710c82f132f42c3502b15c48d0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219040"
---
> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

# <a name="desired-state-configuration-quick-start"></a>預期狀態設定快速入門

這個練習會從頭開始完整地逐步建立並套用預期狀態設定 (DSC)。
我們將使用的範例會確保伺服器已啟用 `Web-Server` (IIS) 功能，且在該伺服器的 `intepub\wwwroot` 目錄中有簡單 "Hello World" 網站的內容。

如需 DSC 及其運作方式的概觀，請參閱[適合決策者的預期狀態設定概觀](decisionMaker.md)。

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

[DSC 設定](configurations.md)是特殊的 PowerShell 函式，可定義您想要設定一或多部目標電腦 (節點) 的方式。

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

**Node** 區塊會指定要設定的目標節點，在本範例中為 `localhost`。

設定會呼叫兩個[資源](resources.md)，[WindowsFeature](windowsFeatureResource.md) 和 [File](fileResource.md)。
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
此檔案即為可套用至目標節點的檔案。

## <a name="apply-the-configuration"></a>套用設定

現在您已經有已編譯的 MOF，您接著可呼叫 [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) Cmdlet 來將設定套用至目標節點 (在本範例中為本機電腦)。

`Start-DscConfiguration` Cmdlet 會要求[本機設定管理員 (LCM)](metaConfig.md) (也就是 DSC 的引擎) 套用設定。
LCM 會呼叫 DSC 資源以套用設定。

在 PowerShell 主控台中，瀏覽至您儲存設定的同一個資料夾，並執行下列命令：

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>測試組態

您可以呼叫 [Get DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) Cmdlet 來查看設定是否成功。

您也可以直接測試結果，在本範例中是透過網頁瀏覽器瀏覽至 `http://localhost/`。
您應該會看到您做為本範例的第一個步驟所建立的 "Hello World" HTML 頁面。

## <a name="next-steps"></a>接下來的步驟

- 在 [DSC 設定](configurations.md)中深入了解 DSC 設定。
- 在 [DSC 資源](resources.md)中查看可用的 DSC 資源，以及如何建立自訂 DSC 資源。
- 在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。