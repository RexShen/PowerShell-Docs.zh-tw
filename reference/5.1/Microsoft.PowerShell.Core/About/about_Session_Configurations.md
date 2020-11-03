---
description: 描述工作階段設定，這會決定可以從遠端連線到電腦的使用者，以及他們可以執行的命令。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configurations
ms.openlocfilehash: 5dd13107396aa7d908fe8224e3de35571b73fae7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207912"
---
# <a name="about-session-configurations"></a>關於會話設定

## <a name="short-description"></a>簡短描述
描述工作階段設定，這會決定可以從遠端連線到電腦的使用者，以及他們可以執行的命令。

## <a name="long-description"></a>詳細描述

會話設定（也稱為「端點」）是本機電腦上的一組設定，可定義當遠端或本機使用者連接到本機電腦上的 PowerShell 時所建立的 PowerShell 會話環境。

電腦的系統管理員可以使用會話設定來保護電腦，以及為連接到電腦的使用者定義自訂環境。

系統管理員也可以使用會話設定，判斷從遠端連線到電腦所需的許可權。 依預設，只有 Administrators 群組的成員才有許可權可以使用會話設定從遠端連線，但您可以變更預設設定以允許所有使用者或選取的使用者從遠端連線到您的電腦。

從 PowerShell 3.0 開始，您可以使用會話設定檔來定義會話設定的元素。 這項功能可讓您輕鬆自訂會話，而不需要撰寫程式碼及探索會話設定的屬性。 若要建立會話設定檔，請使用 New-PSSessionConfiguration Cmdlet。 如需有關工作階段設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](about_Session_Configuration_Files.md)。

會話設定是 Web 服務的管理功能 (WS-MANAGEMENT) 架構的 PowerShell 遠端處理。 只有當您使用新的-PSSession、Invoke 命令或 Enter-PSSession Cmdlet 來連接到遠端電腦時，才會使用它們。

注意：若要管理會話設定，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。

關於會話設定

每個 PowerShell 會話都會使用會話設定。 這包括您使用 New-PSSession 或 Enter-PSSession Cmdlet 建立的持續性會話，以及當您使用使用以 WS-MANAGEMENT 為基礎的遠端處理技術（例如 Invoke 命令）之 Cmdlet 的 ComputerName 參數時，PowerShell 所建立的暫時會話。

系統管理員可以使用會話設定來保護電腦的資源，以及為連接到電腦的使用者建立自訂環境。 例如，您可以使用會話設定來限制電腦在會話中收到的物件大小、定義會話的語言模式，以及指定可在會話中使用的 Cmdlet、提供者和功能。

您可以藉由設定會話設定的安全描述項，判斷誰可以使用會話設定連接到電腦。
使用者必須擁有會話設定的 Execute 許可權，才能在會話中使用它。 如果使用者沒有在電腦上使用任何會話設定的必要許可權，則使用者將無法從遠端連線到電腦。

依預設，只有電腦的系統管理員具有使用預設會話設定的許可權。 但是，您可以變更安全描述項，讓所有人、沒有人或只有選取的使用者使用您電腦上的會話設定。

內建會話設定

PowerShell 3.0 包含內建的會話設定，名稱為 Microsoft PowerShell 和 Microsoft。 在執行 Windows 64 位版本的電腦上，PowerShell 也會提供 Microsoft.powershell32，也就是32位的會話設定。

依預設，會話會使用 Microsoft PowerShell 會話設定，也就是建立會話的命令不包含新的-PSSession、輸入-PSSession 或 Invoke-Command Cmdlet 的 ConfigurationName 參數。

預設會話設定的安全描述項只允許本機電腦上的 Administrators 群組成員使用這些設定。 因此，除非您變更預設設定，否則只有 Administrators 群組的成員可以從遠端連線到電腦。

您可以使用 $PSSessionConfigurationName 喜好設定變數來變更預設的會話設定。 如需詳細資訊，請參閱 about_Preference_Variables。

在本機電腦上查看會話設定

若要取得本機電腦上的會話設定，請使用 Get-PSSessionConfiguration Cmdlet。

例如，輸入：

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property Name, Permission

Name       : microsoft.powershell
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell.workflow
Permission : BUILTIN\Administrators AccessAllowed

Name       : microsoft.powershell32
Permission : BUILTIN\Administrators AccessAllowed
```

會話設定物件會在 PowerShell 3.0 中展開，以顯示使用會話設定檔所設定的會話設定屬性。

例如，若要查看會話設定物件的所有屬性，請輸入：

```powershell
PS C:> Get-PSSessionConfiguration | Format-List -Property *
```

您也可以使用 PowerShell 中的 WSMan 提供者來查看會話設定。 WSMan 提供者會在您的會話中建立 WSMAN：磁片磁碟機。

在 WSMAN：磁片磁碟機中，會話設定位於外掛程式節點中。  (所有會話設定都位於外掛程式節點中，但外掛程式節點中有不是會話設定的專案。 ) 

例如，若要查看本機電腦上的會話設定，請輸入：

```powershell
PS C:> dir wsman:\localhost\plugin\microsoft*

WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

在遠端電腦上查看會話設定

若要查看遠端電腦上的會話設定，請使用 Connect-WSMan Cmdlet 將遠端電腦的附注新增至本機電腦上的 WSMAN：磁片磁碟機，然後使用 WSMAN：磁片磁碟機來查看會話設定。

例如，下列命令會將 Server01 遠端電腦的節點新增到本機電腦上的 WSMAN：磁片磁碟機。

```powershell
PS C:> Connect-WSMan server01.corp.fabrikam.com
```

當命令完成時，您可以流覽至 Server01 電腦的節點，以查看會話設定。

例如：

```powershell
PS C:> cd wsman:

PS WSMan:> dir

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01.corp.fabrikam.com                    Container

PS WSMan:> dir server01\plugin\

WSManConfig: Microsoft.WSMan.Management\WSMan::server01.corp.fabrikam.com\Pl
ugin

Type       Keys                              Name
----       ----                              ----
Container  {Name=microsoft.powershell}       microsoft.powershell
Container  {Name=microsoft.powershell.wor... microsoft.powershell.workflow
Container  {Name=microsoft.powershell32}     microsoft.powershell32
```

變更會話設定的安全描述項

在 Windows Server 2012 和更新版本的 Windows Server 中，預設會為遠端使用者啟用內建的會話設定。 在其他支援的 Windows 版本中，您必須變更會話設定的安全描述項，以允許遠端存取。

若要啟用電腦上會話設定的遠端存取，請使用 Enable-PSRemoting Cmdlet。

此外，根據預設，只有電腦上 Administrators 群組的成員具有預設會話設定的 [執行] 許可權，但您可以變更預設會話設定的安全描述項，以及您所建立之任何會話設定的安全性描述項。

若要授與其他使用者從遠端連線到電腦的許可權，請使用 Set-PSSessionConfiguration Cmdlet 將這些使用者的「執行」許可權新增至 Microsoft.powershell32 會話設定的安全描述項。

例如，下列命令會開啟屬性頁，讓您變更 Microsoft PowerShell 預設會話設定的安全描述項。

```powershell
Set-PSSessionConfiguration -name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

若要拒絕所有使用者對電腦上所有會話設定的許可權，請使用 Disable-PSSessionConfiguration Cmdlet。 例如，下列命令會停用電腦上的預設會話設定。

```powershell
PS C:> Disable-PSSessionConfiguration -Name Microsoft.PowerShell
```

若要防止遠端使用者連線到電腦，但允許本機使用者連接，請使用 Disable-PSRemoting Cmdlet。 Disable-PSRemoting 將 "Network_Deny_All" 專案新增到電腦上的所有會話設定。

```powershell
PS C:> Disable-PSRemoting
```

若要允許遠端使用者使用電腦上的所有會話設定，請使用 Enable-PSRemoting 或 Enable-PSSessionConfiguration Cmdlet。 例如，下列命令會啟用內建會話設定的遠端存取。

```powershell
PS C:> Enable-PSSessionConfiguration -name Microsoft.Power*
```

若要對會話設定的安全描述項進行其他變更，請使用 Set-PSSessionConfiguration Cmdlet。 使用 SecurityDescriptorSDDL 參數來提交 SDDL 字串值。 使用 ShowSecurityDescriptorUI 參數來顯示使用者介面屬性工作表，以協助您建立新的 SDDL。

例如：

```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell `
  -ShowSecurityDescriptorUI
```

建立新的會話設定

若要在本機電腦上建立新的會話設定，請使用 Register-PSSessionConfiguration Cmdlet。 若要定義新的會話設定，您可以使用 c # 元件、PowerShell 腳本，以及 Register-PSSessionConfiguration Cmdlet 的參數。

例如，下列命令會建立與 Microsoft PowerShell 會話設定相同的會話設定，不同之處在于它會將從遠端命令接收的資料限制為 20 mb 的 (MB) 。  (預設值為 50 MB) 。

```powershell
Register-PSSessionConfiguration -Name NewConfig `
  -MaximumReceivedDataSizePerCommandMB 20
```

當您建立會話設定時，您可以使用其他會話設定 Cmdlet 來管理它，它會出現在 WSMAN：磁片磁碟機中。

如需詳細資訊，請參閱 PSSessionConfiguration。

移除會話設定

若要從本機電腦移除會話設定，請使用 Unregister-PSSessionConfiguration Cmdlet。 例如，下列命令會從電腦移除 >newconfig.json 會話設定。

```powershell
PS C:> Unregister-PSSessionConfiguration -Name NewConfig
```

如需詳細資訊，請參閱取消登錄-PSSessionConfiguration。

還原會話設定

若要還原已刪除的預設會話設定 (未) 意外註冊，請使用 Enable-PSRemoting Cmdlet。

Enable-PSRemoting Cmdlet 會重新建立所有不存在於電腦上的預設會話設定。 它不會覆寫或變更現有會話設定的屬性值。

若要還原預設會話設定的原始屬性值，請使用 Unregister-PSSessionConfiguration 刪除會話設定，然後使用 Enable-PSRemoting Cmdlet 來重新建立它。

選取會話設定

若要選取會話的特定會話設定，請使用新的-PSSession、輸入-PSSession 或 Invoke 命令的 ConfigurationName 參數。

例如，此命令會使用 New-PSSession Cmdlet 來啟動 Server01 電腦上的 PSSession。 此命令會使用 ConfigurationName 參數來選取 Server01 電腦上的 WithProfile 設定。

```powershell
PS C:> New-PSSession -ComputerName Server01 -ConfigurationName WithProfile
```

只有當目前的使用者具有使用 WithProfile 會話設定的許可權，或可提供擁有必要許可權之使用者的認證時，此命令才會成功。

您也可以使用 $PSSessionConfigurationName 喜好設定變數來變更電腦上的預設會話設定。 如需 $PSSessionConfigurationName 喜好設定變數的詳細資訊，請參閱 about_Preference_Variables。

## <a name="keywords"></a>關鍵 字

about_Endpoints about_SessionConfigurations

## <a name="see-also"></a>另請參閱

[about_Preference_Variables](about_Preference_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Session_Configuration_Files](about_Session_Configuration_Files.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Unregister-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)
