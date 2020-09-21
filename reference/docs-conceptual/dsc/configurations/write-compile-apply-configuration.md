---
ms.date: 06/22/2020
keywords: dsc,powershell,設定,服務,安裝
title: 撰寫、編譯及套用設定
ms.openlocfilehash: 9acb2db882795d7150326fadb2964deb1105b2cc
ms.sourcegitcommit: 7eea0885dd7ac90ab36e5664501438a292217f7f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85295670"
---
# <a name="write-compile-and-apply-a-configuration"></a>撰寫、編譯及套用設定

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

這個練習會從頭開始完整地逐步建立並套用預期狀態設定 (DSC)。 在下列範例中，您會了解如何撰寫及套用非常簡單的設定。 此設定會確保本機電腦上有 "HelloWorld.txt" 檔案。
如果您刪除此檔案，DSC 會在下次更新時重新建立它。

如需了解 DSC 及其運作方式的概觀，請參閱[開發人員適用的預期狀態設定概觀](../overview/overview.md)。

## <a name="requirements"></a>需求

若要執行此範例，您需要執行 PowerShell 4.0 或更新版本的電腦。

## <a name="write-the-configuration"></a>撰寫設定

DSC [設定](configurations.md)是特殊的 PowerShell 函式，可定義您想設定一或多個目標電腦 (節點) 的方式。

在 PowerShell ISE 或其他 PowerShell 編輯器中，鍵入下列命令：

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when
    # this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a
        # source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> [!IMPORTANT]
> 在更進階案例中，若需要匯入多個模組，以供可在相同組態中使用許多 DSC 資源，請務必使用 `Import-DscResource` 來將每個模組放在個別的一行。 在原始程式碼控制中，此作法較容易維護，且當您在 Azure 狀態設定中使用 DSC 時，它是必要的。
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

將檔案另存為 "HelloWorld.ps1"。

定義設定如同定義函式。 **Node** 區塊會指定要設定的目標節點，在本範例中為 `localhost`。

此設定會呼叫一項[資源](../resources/resources.md)，即 `File` 資源。 資源會確保目標節點處於設定所定義的狀態。

## <a name="compile-the-configuration"></a>編譯設定

DSC 設定若要套用至節點，便必須先編譯成 MOF 檔案。 執行組態 (例如函式)，會針對 `Node` 區塊定義的每個節點編譯一個 `.mof` 檔案。 若要執行執行此組態，您需要將`HelloWorld.ps1` 指令碼「點執行」到目前的範圍。 如需詳細資訊，請參閱 [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)。

<!-- markdownlint-disable MD038 -->
藉由鍵入儲存 `HelloWorld.ps1` 指令碼的路徑 (於 `. ` (點、空格) 之後)，「點執行」該指令碼。 然後，您即可像呼叫函式一樣呼叫該項目來執行組態。 您也可以在指令碼底部叫用組態函式，如此即無須進行「點執行」。
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

這會產生下列輸出：

```Output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>套用設定

現在您已經有已編譯的 MOF，您接著可呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來將設定套用至目標節點 (在本範例中為本機電腦)。

`Start-DscConfiguration` Cmdlet 會要求[本機設定管理員 (LCM)](../managing-nodes/metaConfig.md) (即 DSC 的引擎) 套用設定。 LCM 會呼叫 DSC 資源以套用設定。

使用下列程式碼執行 `Start-DSCConfiguration` Cmdlet。 將儲存 `localhost.mof` 的目錄路徑指定給 **Path** 參數。 `Start-DSCConfiguration` Cmdlet 會查看是否有針對任何 `<computername>.mof` 檔案指定的路徑。 `Start-DSCConfiguration` Cmdlet 會嘗試將其找到的每個 `.mof` 檔案套用到檔案名稱 ("localhost"、"server01"、"dc-02" 等等) 所指定 `computername`。

> [!NOTE]
> 如未指定 `-Wait` 參數，`Start-DSCConfiguration` 就會建立背景作業來執行作業。 指定 `-Verbose` 參數可讓您監看作業的**詳細資訊**輸出。 `-Wait` 和 `-Verbose` 都是選用參數。

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>測試組態

`Start-DSCConfiguration` Cmdlet 完成後，您應該會在指定的位置看到 `HelloWorld.txt` 檔案。 您可以使用 [Get-Content](/powershell/module/microsoft.powershell.management/get-content) Cmdlet 驗證內容。

您也可以使用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)「測試」目前的狀態。

如果節點目前與套用的組態相容，則輸出應為 `True`。

```powershell
Test-DSCConfiguration
```

```Output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```Output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>重新套用設定

若要查看再次套用設定，您可以移除由設定建立的文字檔。 使用 `Start-DSCConfiguration` Cmdlet 搭配 `-UseExisting` 參數。 `-UseExisting` 參數會指示 `Start-DSCConfiguration` 重新套用 "current.mof" 檔案，它代表最近成功套用的設定。

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>後續步驟

- 在 [DSC 設定](configurations.md)中深入了解 DSC 設定。
- 在 [DSC 資源](../resources/resources.md)中查看可用的 DSC 資源，以及如何建立自訂 DSC 資源。
- 在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。
