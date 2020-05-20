---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,服務,安裝
title: 撰寫、編譯及套用設定
ms.openlocfilehash: eb61e518762b9f13e617ecd4711bfef7a86814ec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "76818153"
---
> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>撰寫、編譯及套用設定

這個練習會從頭開始完整地逐步建立並套用預期狀態設定 (DSC)。
在下列範例中，您會了解如何撰寫及套用非常簡單的設定。 此設定會確保本機電腦上有 "HelloWorld.txt" 檔案。 如果您刪除此檔案，DSC 會在下次更新時重新建立它。

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

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> !重要 在更進階案例中，若需要匯入多個模組，以便您可以在相同設定中使用許多 DSC 資源，請務必使用 `Import-DscResource`，將每個模組放在個別的一行。
> 在原始程式碼控制中，此作法較容易維護，且當您在 Azure 狀態設定中使用 DSC 時，它是必要的。
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

DSC 設定若要套用至節點，便必須先編譯成 MOF 檔案。
執行設定 (例如函式)，會針對 `Node` 區塊定義的每個節點編譯一個 ".mof" 檔案。
為執行此設定，您需要「點溯源」  "HelloWorld.ps1" 指令碼到目前的範圍。
如需詳細資訊，請參閱 [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)。

<!-- markdownlint-disable MD038 -->
在 `. ` (點、空格) 後輸入儲存路徑，即可「點溯源」您的 "HelloWorld.ps1" 指令碼。 然後，您就可以像呼叫函式一樣呼叫它來執行您的設定。
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

這會產生下列輸出：

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>套用設定

現在您已經有已編譯的 MOF，您接著可呼叫 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 來將設定套用至目標節點 (在本範例中為本機電腦)。

`Start-DscConfiguration` Cmdlet 會要求[本機設定管理員 (LCM)](../managing-nodes/metaConfig.md) (即 DSC 的引擎) 套用設定。
LCM 會呼叫 DSC 資源以套用設定。

使用下列程式碼執行 `Start-DSCConfiguration` Cmdlet。 將您儲存 "localhost.mof" 的目錄路徑指定給 `-Path` 參數。 `Start-DSCConfiguration` Cmdlet 會查看是否有針對任何 "\<電腦名稱\>.mof" 檔案指定的路徑。 `Start-DSCConfiguration` Cmdlet 會嘗試將它所找到每個 ".mof" 檔案套用到檔案名稱 ("localhost"、"server01"、"dc-02" 等等) 指定的電腦名稱。

> [!NOTE]
> 如未指定 `-Wait` 參數，`Start-DSCConfiguration` 就會建立背景作業來執行作業。 指定 `-Verbose` 參數可讓您監看作業的**詳細資訊**輸出。 `-Wait` 和 `-Verbose` 都是選用參數。

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>測試組態

`Start-DSCConfiguration` Cmdlet 完成後，您應該會在指定的位置看到 "HelloWorld.txt" 檔案。 您可以使用 [Get-Content](/powershell/module/microsoft.powershell.management/get-content) Cmdlet 驗證內容。

您也可以使用 [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)「測試」目前的狀態。

如果節點目前與套用的設定相容，則輸出應為 "True"。

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
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
