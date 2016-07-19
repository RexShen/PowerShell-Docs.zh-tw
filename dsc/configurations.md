---
title: "DSC 設定"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 59bf4cff540dabeeb77038ea84177f7c6bac2b4b
ms.openlocfilehash: e5412a3168a18d1dbd117ed8b3eb6dd42a8d8f70

---

# DSC 設定

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

DSC 設定是一種定義特殊類型函式的 PowerShell 指令碼。 若要定義設定，請使用 PowerShell 關鍵字 __Configuration__。

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

將指令碼儲存為 .ps1 檔案。

## 設定語法

設定指令碼包含下列項目：

- **Configuration** 區塊。 這是最外層的指令碼區塊。 定義它的方式，是使用 **Configuration** 關鍵字並提供名稱。 本例中的設定名稱是 "MyDscConfiguration"。
- 一個或多個 **Node** 區塊。 它們會定義您要設定的節點 (電腦或 VM)。 上述設定有一個 **Node** 區塊，以名為 "TEST-PC1" 的電腦為目標。
- 一個或多個資源區塊。 設定就在這裡為它要設定的資源設定屬性。 本例有兩個資源區塊，兩個都呼叫 "WindowsFeature" 資源。

只要可以在 PoweShell 函式中執行的作業，通常在 **Configuration** 區塊內都可以執行。 例如，在前一個範例中，如果設定的目標電腦名稱不想使用硬式編碼，您可以為節點名稱加入參數：

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
```

在本例中，您指定節點名稱的方式，是在您[編譯設定](# Compiling the configuration) 時將其作為 $ComputerName 參數傳遞。 預設名稱為 "localhost"。

## 編譯設定
您必須先將設定編譯成 MOF 文件，才能施行設定。 呼叫設定即可完成此作業，就像您在 PowerShell 函式中做的一樣。
>__注意：__若要呼叫設定，函式必須在全域範圍內 (像任何其他 PowerShell 函式一樣)。 執行此作業的方法有二：「點執行」指令碼，或使用 F5 或按一下 ISE 的 __[執行指令碼]__ 按鈕執行設定指令碼。 若要點執行指令碼，請執行命令 `. .\myConfig.ps1`，其中 `myConfig.ps1` 是包含設定的指令碼檔案名稱。

當您呼叫設定時，它會：

- 解析所有的變數 
- 在目前的目錄中建立和設定同名的資料夾。
- 在新的目錄中建立名為 _NodeName_.mof 的檔案，其中 _NodeName_ 是設定的目標節點名稱。 如果有多個節點，每個節點都會建立一個 MOF 檔案。

>__注意：__MOF 檔案包含目標節點全部的設定資訊。 因為這樣，這個檔案的安全防護很重要。 如需詳細資訊，請參閱[保護 MOF 檔案](secureMOF.md)。

編譯上述第一個設定會導致下列的資料夾結構：

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 TEST-PC1.mof
```  

如果設定使用參數，如同第二個範例，則必須在編譯時提供參數。 它看起來會像這樣：

```powershell
PS C:\users\default\Documents\DSC Configurations> . .\MyDscConfiguration.ps1
PS C:\users\default\Documents\DSC Configurations> MyDscConfiguration -ComputerName 'MyTestNode'
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## 使用 DependsOn
有用的 DSC 關鍵字是 __DependsOn__。 通常 (但不一定永遠)，DSC 會依設定內的資源出現順序套用資源。 不過，__DependsOn__ 會指定哪一個資源依存於其他資源，而 LCM 則確保它們依正確順序套用，不管資源執行個體的定義順序。 例如，設定可能會指定 __User__ 資源的執行個體依存於 __Group__ 執行個體的存在與否：

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}
```

## 在設定中使用新的資源
如果執行了前面的範例，您可能會注意到，系統警告使用了未明確匯入的資源。
現在，DSC 在 PSDesiredStateConfiguration 模組中附有 12 種資源。 外部模組的其他資源必須放置在 `$env:PSModulePath` 中，LCM 才能辨識。 新的 Cmdlet，[Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)，可用來決定哪些資源要安裝在系統上並提供 LCM 使用。 這些模組放置在 `$env:PSModulePath` 並由 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) 正確辨識後，仍需要載入至設定中。 __Import-DscResource__ 是只能在 __Configuration__ 區塊中辨識的動態關鍵字 (亦即它不是 Cmdlet)。 __Import-DscResource__ 支援兩個參數：
* __ModuleName__，使用 __Import-DscResource__ 時建議用它。 它接受包含了要匯入資源 (以及模組名稱字串陣列) 的模組名稱。 
* __Name__ 是要匯入的資源名稱。 [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) 傳回的 "Name" 不是易記的名稱，而是定義資源結構描述時使用的類別名稱 ([Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) 傳回 __ResourceType__)。 

## 另請參閱
* [Windows PowerShell 預期狀態設定概觀](overview.md)
* [DSC 資源](resources.md)
* [設定本機設定管理員](metaConfig.md)




<!--HONumber=Jul16_HO1-->


