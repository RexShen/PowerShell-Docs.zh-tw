---
ms.date: 12/12/2018
keywords: dsc，powershell，設定、 服務、 安裝程式
title: 撰寫、編譯及套用設定
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676627"
---
> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>撰寫、編譯及套用設定

這個練習會從頭開始完整地逐步建立並套用預期狀態設定 (DSC)。
在下列範例中，您將學習如何撰寫及套用非常簡單的組態。 組態可確保 「 HelloWorld.txt"檔案存在本機電腦上。 如果您刪除檔案時，DSC 會重新建立它便會更新下一次。

如需 DSC 的功能及其運作方式的概觀，請參閱 <<c0> [ 適用於開發人員 Desired State Configuration 概觀](../overview/overview.md)。

## <a name="requirements"></a>需求

若要執行此範例中，您必須執行 PowerShell 4.0 或更新版本的電腦。

## <a name="write-the-configuration"></a>撰寫設定

DSC [設定](configurations.md)是特殊的 PowerShell 函式，可定義您想設定一或多個目標電腦 (節點) 的方式。

在 PowerShell ISE 中或其他 PowerShell 編輯器中，輸入下列命令：

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

將檔案儲存為"HelloWorld.ps1 」 中。

定義組態，就像定義的函式。 **Node** 區塊會指定要設定的目標節點，在本範例中為 `localhost`。

此設定會呼叫其中一個[資源](../resources/resources.md)，則`File`資源。 資源會確保目標節點處於設定所定義的狀態。

## <a name="compile-the-configuration"></a>編譯設定

DSC 設定若要套用至節點，便必須先編譯成 MOF 檔案。
執行設定，例如函式，將會編譯一個 「.mof"檔案所定義的每個節點的`Node`區塊。
若要執行設定時，您必須*點溯源*"HelloWorld.ps1 」 指令碼到目前的範圍。
如需詳細資訊，請參閱 < [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)。

*點溯源*"HelloWorld.ps1 」 指令碼中您儲存的路徑之後, 輸入`. `（點、 空格）。 然後，您可能會藉由呼叫例如函式中執行您的設定。

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
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

`Start-DscConfiguration` Cmdlet 會告知[本機設定管理員 (LCM)](../managing-nodes/metaConfig.md)，DSC，以套用組態的引擎。
LCM 會呼叫 DSC 資源以套用設定。

使用下列程式碼來執行`Start-DSCConfiguration`cmdlet。 指定的目錄路徑來儲存您 「 localhost.mof"`-Path`參數。 `Start-DSCConfiguration`指令程式會透過任何指定的目錄"\<computername\>.mof 」 檔案。 `Start-DSCConfiguration`指令程式會嘗試將每個找到的".mof"檔案套用到檔案名稱 （"localhost"、"server01"、"dc-02"等等） 所指定電腦名稱。

> [!NOTE]
> 如果`-Wait`未指定參數，`Start-DSCConfiguration`建立背景工作來執行作業。 指定`-Verbose`參數可讓您監看**Verbose**作業的輸出。 `-Wait`與`-Verbose`是這兩個選擇性參數。

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>測試組態

一次`Start-DSCConfiguration`cmdlet 完成時，您應該會看到您所指定的位置中的 「 HelloWorld.txt"檔案。 您可以確認與內容[Get-content](/powershell/module/microsoft.powershell.management/get-content) cmdlet。

您也可以*測試*目前的狀態使用[Test-dscconfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)。

如果節點是目前符合套用的設定，輸出應該是"True"。

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

## <a name="re-applying-the-configuration"></a>重新套用組態

若要查看您一次套用的設定，您可以移除您組態所建立的文字檔。 使用`Start-DSCConfiguration`cmdlet 搭配`-UseExisting`參數。 `-UseExisting`參數會指示`Start-DSCConfiguration`來重新套用 「 current.mof"檔案，表示最近成功套用設定。

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>接下來的步驟

- 在 [DSC 設定](configurations.md)中深入了解 DSC 設定。
- 在 [DSC 資源](../resources/resources.md)中查看可用的 DSC 資源，以及如何建立自訂 DSC 資源。
- 在 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/) 中尋找 DSC 設定和資源。
