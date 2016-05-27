---
title:   在 Nano Server 上使用 DSC
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 在 Nano Server 上使用 DSC

> 適用於：Windows PowerShell 5.0

您可以選用 Windows Server 2016 媒體上 `NanoServer\Packages` 資料夾中的 **Nano Server 上的 DSC** 封裝。 當您建立 Nano Server 的 VHD 時，可以安裝此套件，方法是指定 **Microsoft-NanoServer-DSC-Package** 作為 **New-NanoServerImage** 函數中 **Packages** 參數的值。 例如，如果要建立虛擬機器的 VHD，命令會如下所示︰

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

如需安裝及使用 Nano Server 以及如何透過 PowerShell 遠端來管理 Nano Server 的相關資訊，請參閱 [Getting Started with Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx) (開始使用 Nano Server)。


## Nano Server 提供的 DSC 功能

 相較於完整版的 Windows Server，Nano Server 僅支援一組有限的 API，所以目前 Nano Server 上的 DSC 和執行於完整 SKU 上的 DSC 相較，並不具備完整的同位功能。 Nano Server 上的 DSC 正在開發中，功能還不夠完備。
 
 目前於 Nano Server 上提供的 DSC 功能如下︰ 


* 推入與提取模式

* 完整版 Windows Server 的所有現有 DSC Cmdlet 包括︰ 
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)   
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* 編譯設定 (請參閱 [DSC 設定](configurations.md))。

  **問題︰** 密碼加密 (請參閱[保護 MOF 檔案](securemof.md)) 在設定編譯期間無法運作。

* 編譯中繼設定 (請參閱[設定本機設定管理員](metaConfig.md))

* 執行使用者內容下的資源 (請參閱[以使用者認證執行 DSC (RunAs)](runAsUser.md))

* 類別型資源 (請參閱[使用 PowerShell 類別撰寫自訂 DSC 資源](authoringResourceClass.md))

* 為 DSC 資源偵錯 (請參閱[為 DSC 資源偵錯](debugresource.md))
  
  **問題︰** 如果資源使用 PsDscRunAsCredential 則無法運作 (請參閱[以使用者認證執行 DSC](runAsUser.md))

* [指定跨節點相依性](crossNodeDependencies.md) 

* [資源的版本管理](sxsResource.md)

* 提取用戶端 (設定與資源) (請參閱[使用設定名稱設定提取用戶端](pullClientConfigNames.md))

* [部分設定 (提取與推入)](partialConfigs.md)

* [回報至提取伺服器](reportServer.md) 

* MOF 加密

* 事件記錄

* Azure 自動化 DSC 報告

* 可完全正常運作的資源
  * [Archive](archiveResource.md)
  * [環境](environmentResource.md)
  * [檔案](fileResource.md)
  * [記錄檔](logResource.md)
  * ProcessSet
  * [登錄](registryResource.md)
  * [指令碼](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll (請參閱[指定跨節點相依性](crossNodeDependencies.md))
  * WaitForAny (請參閱[指定跨節點相依性](crossNodeDependencies.md))
  * WaitForSome (請參閱[指定跨節點相依性](crossNodeDependencies.md))

* 部分運作的資源
  * [群組](groupResource.md)
  * GroupSet
  
  **問題︰** 若呼叫特定執行個體兩次 (執行兩次相同的設定)，則上述資源會失敗
  
  * [Service](serviceResource.md)
  * ServiceSet
  
  **問題︰** 只適用於開始/停止 (狀態) 服務。 如果嘗試變更啟動類型、認證、描述等其他服務屬性，則會失敗。 擲回的錯誤類似如下︰
  
  *找不到類型 [management.managementobject]：請驗證已載入包含此類型的組件。*
  
* 無法正常運作的資源
  * [使用者](userResource.md)
  

## Nano Server 上不提供的 DSC 功能

目前於 Nano Server 上沒有提供下列 DSC 功能︰

* 使用加密密碼將 MOF 文件解密 
* 提取伺服器 -- 目前無法在 Nano Server 上設定提取伺服器
* 任何不在功能清單中的項目皆可使用

## 在 Nano Server 上使用自訂 DSC 資源
 
因為 Nano Server 上僅提供有限的 Windows API 與 CLR 程式庫，所以在 Windows 完整 CLR 版能執行的 DSC 資源，在 Nano Server 上不一定有效。 
請先完成端對端測試，再將任何 DSC 自訂資源部署至生產環境。

## 另請參閱
- [開始使用 Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx)



<!--HONumber=May16_HO3-->


