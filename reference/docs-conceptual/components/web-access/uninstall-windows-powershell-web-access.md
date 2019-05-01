---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: 解除安裝 Windows PowerShell Web 存取
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058128"
---
# <a name="uninstall-windows-powershell-web-access"></a>解除安裝 Windows PowerShell Web 存取

更新日期：2013 年 6 月 24 日

適用於：Windows Server 2012 R2、Windows Server 2012

本主題中的步驟會將 Windows PowerShell Web 存取網站及對應的應用程式，從安裝所在的閘道伺服器移除。

## <a name="notify-users"></a>通知使用者

在開始之前，請通知網頁型主控台的使用者，您正在移除網站。

解除安裝 Windows PowerShell Web 存取不會解除安裝 IIS 或自動安裝的任何其他功能，因為 Windows PowerShell Web 存取需要這些功能才能執行。
解除安裝程序會保留與 Windows PowerShell Web 存取相依的功能；您可以視需要個別解除安裝這些功能。

## <a name="recommended-quick-uninstallation"></a>建議 (快速) 解除安裝

本節中的程序可協助您解除安裝：

- Windows PowerShell Web 存取 Web 應用程式，以及
- Windows PowerShell Web 存取功能

其藉由使用 Windows PowerShell Cmdlet 來完成。

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>步驟 1：使用 Cmdlet 刪除 Web 應用程式

1. 執行下列其中一個動作來開啟 Windows PowerShell 工作階段。

    -   在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 [Windows PowerShell]。

    -   在 Windows **[開始]** 畫面上，按一下 **[Windows PowerShell]**。

2. 輸入 `Uninstall-PswaWebApplication`，然後按 **Enter** 鍵。
   1. 如果您已經指定您自訂的網站名稱，請將 `-WebsiteName` 參數新增至您的命令並指定網站名稱。

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. 如果您已經使用自訂的 Web 應用程式 (不是預設應用程式 **pswa**)，請將 `-WebApplicationName` 參數新增至您的命令，並指定 Web 應用程式的名稱。

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. 如果您使用測試憑證，請新增 `DeleteTestCertificate` 參數到此 Cmdlet，如下列範例所示。

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>步驟 2：使用 Cmdlet 解除安裝 Windows PowerShell Web 存取

1. 執行下列其中一個動作，使用提高的使用者權限開啟 Windows PowerShell 工作階段。 如果已經開啟工作階段，請移至下一個步驟。

    -   在 Windows 桌面上，以滑鼠右鍵按一下工作列上的 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

    -   在 Windows **[開始]** 畫面上，以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

1. 輸入下列命令，然後按 **Enter**，其中 *computer_name* 代表要移除 Windows PowerShell Web 存取的遠端伺服器。 如果移除時需要， `-Restart` 參數會自動重新啟動目的地伺服器。

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    若要從離線 VHD 移除角色及功能，您必須新增 `-ComputerName` 參數及 `-VHD` 參數。 `-ComputerName` 參數包含要掛接 VHD 的伺服器名稱， `-VHD` 參數則包含指定伺服器上的 VHD 檔案路徑。

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. 完成移除後，請確認是否已移除 Windows PowerShell Web 存取，方法是在 [伺服器管理員] 中開啟 [所有伺服器] 頁面，選取移除功能的伺服器，並檢視所選伺服器頁面上的 [角色和功能] 磚。

    您也可以針對所選伺服器執行 `Get-WindowsFeature` Cmdlet (Get-WindowsFeature -ComputerName &lt;電腦名稱&gt;)，檢視伺服器上安裝的角色和功能清單。

## <a name="custom-uninstallation"></a>自訂解除安裝

本節中的程序可協助您使用伺服器管理員中的「移除角色及功能精靈」和 IIS 管理員主控台，解除安裝 Windows PowerShell Web 存取 Web 應用程式和 Windows PowerShell Web 存取功能。

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>步驟 1：使用 IIS 管理員刪除 Web 應用程式


1. 執行下列其中一個動作以開啟 IIS 管理員主控台。 如果已經開啟，請移至下一個步驟。

    -   在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。 在 [伺服器管理員] 的 **[工具]** 功能表上，按一下 **[Internet Information Services (IIS) 管理員]**。

    -   在 Windows [開始] 畫面中，輸入 **Internet Information Services (IIS) 管理員**名稱的任何部分。 當捷徑出現在 [應用程式] 結果時，按一下該捷徑。

1. 在 [IIS 管理員] 樹狀目錄窗格中，選取正在執行 Windows PowerShell Web 存取 Web 應用程式的網站。

1. 在 **[動作]** 窗格的 **[管理網站]** 下，按一下 **[停止]**。

1. 在樹狀目錄窗格中，以滑鼠右鍵按一下正在執行 Windows PowerShell Web 存取 Web 應用程式之網站中的 Web 應用程式，然後按一下 **[移除]**。

1. 在樹狀目錄窗格中，選取 [應用程式集區]，選取 Windows PowerShell Web 存取應用程式集區資料夾，按一下 [動作] 窗格中的 [停止]，然後按一下內容窗格中的 [移除]。

1. 關閉 [IIS 管理員]。

> ![警告注意](images/SecurityNote.jpeg)**注意**：
>
> 解除安裝期間不會刪除憑證。
>
> 如果您建立自我簽署憑證，或使用測試憑證並想要將它移除，請在 IIS 管理員中刪除憑證。

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>步驟 2：使用移除角色及功能精靈解除安裝 Windows PowerShell Web 存取

1. 如果已經開啟伺服器管理員，請移至下一個步驟。 如果尚未開啟伺服器管理員，請執行下列其中一個動作來將它開啟。

    -   在 Windows 桌面上，按一下 Windows 工作列中的 [伺服器管理員] 來啟動 [伺服器管理員]。

    -   在 Windows **[開始]** 畫面上，按一下 **[伺服器管理員]**。

1. 在 **[管理]** 功能表上，按一下 **[移除角色及功能]**。

1. 在 [選取目的地伺服器] 頁面上，選取您想要從中移除功能的伺服器或離線 VHD。 若要選取離線 VHD，請先選取要掛接 VHD 的伺服器，然後選取 VHD 檔案。 選取目的地伺服器之後，按一下 **[下一步]**。

1. 再按一下 [下一步]，跳至 [移除功能] 頁面。

1. 取消選取 **[Windows PowerShell Web 存取]** 核取方塊，然後按一下 **[下一步]**。

1. 在 **[確認移除選項]** 頁面上，按一下 **[移除]**。

## <a name="see-also"></a>另請參閱

- [安裝和使用 Windows PowerShell Web 存取](install-and-use-windows-powershell-web-access.md)
- [IIS 管理員 7.0 說明](https://technet.microsoft.com/library/cc732664.aspx)