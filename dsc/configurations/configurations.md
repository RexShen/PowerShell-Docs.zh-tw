---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: DSC 設定
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080165"
---
# <a name="dsc-configurations"></a>DSC 設定

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

DSC 設定是一種定義特殊類型函式的 PowerShell 指令碼。
若要定義設定，請使用 PowerShell 關鍵字 **Configuration**。

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

將指令碼儲存為 `.ps1` 檔案。

## <a name="configuration-syntax"></a>設定語法

設定指令碼包含下列項目：

- **Configuration** 區塊。 這是最外層的指令碼區塊。 定義它的方式，是使用 **Configuration** 關鍵字並提供名稱。 本例中的設定名稱是 "MyDscConfiguration"。
- 一個或多個 **Node** 區塊。 它們會定義您要設定的節點 (電腦或 VM)。 上述設定有一個 **Node** 區塊，以名為 "TEST-PC1" 的電腦為目標。 節點區塊可以接受多個電腦名稱。
- 一個或多個資源區塊。 設定就在這裡為它要設定的資源設定屬性。 本例有兩個資源區塊，兩個都呼叫 "WindowsFeature" 資源。

只要可以在 PowerShell 函式中執行的作業，通常在 **[設定]** 區塊內都可以執行。 例如，在前一個範例中，如果設定的目標電腦名稱不想使用硬式編碼，您可以為節點名稱加入參數：

在本範例中，您在編譯設定時將節點名稱當作 **ComputerName** 參數來傳遞，藉以指定節點名稱。 預設名稱為 "localhost"。

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

**節點**區塊也可以接受多個電腦名稱。 在上述範例中，您可以使用 `-ComputerName` 參數，也可以將逗號分隔的電腦清單直接傳遞給**節點**區塊。

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

在**節點**區塊中指定電腦清單時，從設定中，您需要使用陣列標記法。

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>編譯設定

您必須先將設定編譯成 MOF 文件，才能施行設定。
呼叫設定即可完成此作業，就像您呼叫 PowerShell 函式一樣。
範例的最後一行僅包含設定名稱，並會呼叫設定。

> [!NOTE]
> 若要呼叫設定，函式必須在全域範圍內 (像任何其他 PowerShell 函式一樣)。
> 執行此作業的方法有二：「點執行」指令碼，或使用 F5 或按一下 ISE 的 **[執行指令碼]** 按鈕執行設定指令碼。
> 若要點執行指令碼，請執行命令 `. .\myConfig.ps1`，其中 `myConfig.ps1` 是包含設定的指令碼檔案名稱。

當您呼叫設定時，它會：

- 解析所有的變數
- 在目前的目錄中建立和設定同名的資料夾。
- 在新的目錄中建立名為 _NodeName_.mof 的檔案，其中 _NodeName_ 是設定的目標節點名稱。
  如果有多個節點，每個節點都會建立一個 MOF 檔案。

> [!NOTE]
> MOF 檔案包含目標節點的所有設定資訊。 因為這樣，這個檔案的安全防護很重要。
> 如需詳細資訊，請參閱[保護 MOF 檔案](../pull-server/secureMOF.md)。

編譯上述第一個設定會導致下列的資料夾結構：

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

如果設定使用參數，如同第二個範例，則必須在編譯時提供參數。 它看起來會像這樣：

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>在設定中使用新的資源

如果執行了前面的範例，您可能會注意到，系統警告使用了未明確匯入的資源。
現在，DSC 在 PSDesiredStateConfiguration 模組中附有 12 種資源。

Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 可用於決定在系統上安裝並供 LCM 使用的資源。
這些模組放置在 `$env:PSModulePath` 並由 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 正確辨識後，仍需要載入至設定中。

**Import-DscResource** 是只能在**設定**區塊中辨識的動態關鍵字，它不是 Cmdlet。
**Import-DscResource** 支援兩個參數：

- **ModuleName**，使用 **Import-DscResource** 時建議用它。 它接受包含了要匯入資源 (以及模組名稱字串陣列) 的模組名稱。
- **Name** 是要匯入的資源名稱。 [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 傳回的 "Name" 不是易記的名稱，而是定義資源結構描述時使用的類別名稱 ([Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 傳回 **ResourceType**)。

如需使用 `Import-DSCResource` 的詳細資訊，請參閱[使用 Import-DSCResource](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 和 v5 的差異

在 PowerShell 4.0 中需要儲存 DSC 資源的位置存在差異。 如需詳細資訊，請參閱[資源位置](import-dscresource.md#resource-location)。

## <a name="see-also"></a>另請參閱

- [Windows PowerShell 預期狀態設定概觀](../overview/overview.md)
- [DSC 資源](../resources/resources.md)
- [設定本機設定管理員](../managing-nodes/metaConfig.md)
