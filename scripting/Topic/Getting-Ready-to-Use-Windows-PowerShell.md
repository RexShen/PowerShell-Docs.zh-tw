---
title: 準備好使用 Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
---
# 準備好使用 Windows PowerShell
安裝並啟動 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 之後，請考慮下列安裝程式選項。 您可以隨時執行這些工作。

-   **安裝說明檔。** [!INCLUDE[psversion3](../Token/psversion3_md.md)] 中包含的 Cmdlet 沒有說明檔。 不過，您可以使用 [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) Cmdlet 將最新的說明檔下載並安裝到您的電腦 安裝檔案之後，您可以使用 [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) Cmdlet 直接在命令列顯示。 如需詳細資訊，請參閱 [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe)。

    如果您決定不要安裝說明檔，您仍然可以閱讀線上說明主題。 若要尋找任何線上版本的 Cmdlet 說明主題，請輸入：`Get-Help <CmdletName> -Online`。 若要瀏覽 TechNet Library 中的 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 說明主題，請從 [http://go.microsoft.com/fwlink/?LinkID=107116](http://go.microsoft.com/fwlink/?LinkID=107116) 開始。

-   **執行指令碼。** 為保護 [!INCLUDE[mshshort](../Token/mshshort_md.md)] 的安全，[!INCLUDE[mshshort](../Token/mshshort_md.md)] 上的預設執行原則為 **Restricted**。 這項原則可讓您執行 Cmdlet，但不能執行指令碼。 若要執行指令碼，請使用 [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) Cmdlet，將執行原則變更為 **AllSigned** 或 **RemoteSigned**。 只有電腦上的 Administrators 群組成員才能執行此 Cmdlet。 如需詳細資訊，請參閱 [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6)。

-   **啟用遠端功能。** 系統已為您設定成在其他電腦上執行遠端命令。 在 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 上，系統還會設定成接收遠端命令，也就是允許其他電腦在本機電腦上執行遠端命令。 若要讓執行其他 Windows 版本的電腦接收遠端命令，請在您要遠端管理的電腦上執行 [Enable-PSRemoting](https://technet.microsoft.com/en-us/library/19437c28-33b8-4ac1-9113-8439cc8beffb) Cmdlet。 只有電腦上的 Administrators 群組成員才能執行此 Cmdlet。 如需詳細資訊，請參閱 [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)。

    注意︰如果在執行 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 的電腦上啟用了遠端功能，安裝 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 之後會維持啟用遠端功能。 不過，在 [!INCLUDE[lserver](../Token/lserver_md.md)] 上 (而不是 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)])，您必須在安裝 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 之後重新啟用遠端功能。

## 另請參閱
[安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[啟動 Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->


