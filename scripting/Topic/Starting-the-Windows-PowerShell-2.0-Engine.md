---
title: 啟動 Windows PowerShell 2.0 引擎
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
---
# 啟動 Windows PowerShell 2.0 引擎
本節說明如何在下列系統上啟動 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎：[!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] (包括 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎)，以及已安裝 [!INCLUDE[psversion2](../Token/psversion2_md.md)]、[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 的其他系統。

[!INCLUDE[psversion4](../Token/psversion4_md.md)] 和 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 設計成與 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 舊版相容。 在 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 和 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 中，針對 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 所撰寫的 Cmdlet、提供者、嵌入式管理單元、模組和指令碼會以現狀執行。 不過，因為 Microsoft .NET Framework 4 中執行階段啟用原則的變更，所以在 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 或 [!INCLUDE[psversion4](../Token/psversion4_md.md)] (使用 CLR 4.0 所編譯) 中，必須修改才能執行針對 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 所撰寫以及使用 Common Language Runtime (CLR) 2.0 所編譯的 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 主程式。 只有在現有指令碼或主機程式無法執行時才會使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎，因為它與 [!INCLUDE[psversion4](../Token/psversion4_md.md)]、[!INCLUDE[psversion3](../Token/psversion3_md.md)] 或 Microsoft .NET Framework 4 不相容。 這種情況應該很少見。

許多需要 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的程式都會自動啟動它。 這些指示是針對需要手動啟動引擎的罕見情況。

## 安裝和啟用必要的程式
啟動 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎之前，請啟用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎和 Microsoft .NET Framework 3.5 (含 Service Pack 1)。 如需相關指示，請參閱[安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)。

已安裝 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 或 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 的系統都具有所有必要元件。 不需要進一步設定。 如需安裝 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 或 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 的資訊，請參閱[安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)。

## 如何啟動 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎
啟動 [!INCLUDE[mshshort](../Token/mshshort_md.md)] 時，預設會啟動最新版本。 若要啟動 [!INCLUDE[mshshort](../Token/mshshort_md.md)] (含 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎)，請使用 PowerShell.exe 的 Version 參數。 您可以在任何命令提示字元 (包括 Windows PowerShell 和 Cmd.exe) 執行命令。

```
PowerShell.exe -Version 2
```

## 如何使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎啟動遠端工作階段
若要在遠端工作階段中執行 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎，請在載入 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的遠端電腦上建立工作階段設定 (也稱為「端點」)。 工作階段設定儲存在遠端電腦上，而且任何授權使用者都可以用來建立使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的工作階段。

這是通常由系統管理員所執行的進階工作。

下列程序使用 [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) Cmdlet 的 **PSVersion** 參數，來建立使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的工作階段設定。 您也可以使用 [New-PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866) Cmdlet 的 **PowerShellVersion** 參數來建立可載入 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎之工作階段的工作階段設定檔，以及使用 [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) 參數的 **PSVersion** 參數將工作階段設定變更成使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。

如需工作階段設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](https://technet.microsoft.com/en-us/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8)。如需工作階段設定 (包括設定和安全性) 的資訊，請參閱 [about_Session_Configurations [v4]](https://technet.microsoft.com/en-us/library/a2fbe12a-350c-4d04-be50-24102824e3ab)。

#### 啟動遠端 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 工作階段

1.  若要建立需要 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的工作階段設定，請使用 [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) Cmdlet 的 **PSVersion** 參數 (值為 "2.0")。 在「伺服器端」或連線接收端的電腦上，執行此命令。

    下列範例命令會在 Server01 電腦上建立 PS2 工作階段設定。 若要執行此命令，請使用 **[以系統管理員身分執行]** 選項來啟動 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 或 [!INCLUDE[psversion3](../Token/psversion3_md.md)]。

    ```
    Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
    ```

2.  若要在 Server01 電腦上建立使用 PS2 工作階段設定的工作階段，請使用建立遠端工作階段之 Cmdlet 的 **ConfigurationName** 參數 (例如 [New-PSSession](https://technet.microsoft.com/en-us/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) Cmdlet)。

    使用工作階段設定的工作階段啟動時，會將 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎自動載入到工作階段。

    下列命令會在 Server01 電腦上啟動使用 PS2 工作階段設定的工作階段。 命令會將工作階段儲存於 $s 變數中。

    ```
    $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
    ```

## 如何使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎啟動背景工作
若要使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎啟動背景工作，請使用 [Start-Job](https://technet.microsoft.com/en-us/library/2bc04935-0deb-4ec0-b856-d7290cca6442) Cmdlet 的 **PSVersion** 參數。

下列命令會使用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎啟動背景工作。

```
Start-Job {Get-Process} -PSVersion 2.0
```

如需背景工作的詳細資訊，請參閱 [about_Jobs [v4]](https://technet.microsoft.com/en-us/library/7362512a-8a4e-4575-b2ea-a740e5c4f002)。



<!--HONumber=Apr16_HO2-->


