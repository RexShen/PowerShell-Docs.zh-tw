---
description: 描述會話設定中使用的會話設定檔， (也稱為「端點」 ) 來定義使用會話設定之會話的環境。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 198a0aeb667c3c947bc7e202bc3c0d9832195b91
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207551"
---
# <a name="about-session-configuration-files"></a>關於會話設定檔

## <a name="short-description"></a>簡短描述

描述會話設定中使用的會話設定檔， (也稱為「端點」 ) 來定義使用會話設定之會話的環境。

## <a name="long-description"></a>詳細描述

「會話設定檔」是副檔名為 .pssc 的文字檔，其中包含會話設定屬性和值的雜湊表。 您可以使用會話設定檔來設定會話設定的屬性。 這麼做會定義使用該會話設定之任何 Windows PowerShell 會話的環境。

會話設定檔可讓您輕鬆地建立自訂會話設定，而不需要使用複雜的 c # 元件或腳本。

「會話設定」或「端點」是本機電腦設定的集合，可決定使用者可在電腦上建立會話的專案;使用者可以在這些會話中執行哪些命令;以及會話是否應以特殊許可權虛擬帳戶的形式執行。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](about_Session_Configurations.md)。

會話設定是在 Windows PowerShell 2.0 中引進，而會話設定檔是在 Windows PowerShell 3.0 引進。 您必須使用 Windows PowerShell 3.0，將會話設定檔包含在會話設定中。 不過，Windows PowerShell 2.0 (和更新版本) 的使用者會受到會話設定中的設定影響。

## <a name="creating-custom-sessions"></a>建立自訂會話

您可以在會話設定中指定會話屬性，以自訂 Windows PowerShell 會話的許多功能。 您可以撰寫可定義自訂執行時間的 c # 程式來自訂會話，也可以使用會話設定檔來定義使用會話設定建立之會話的屬性。 一般來說，使用會話設定檔比撰寫 c # 程式更容易。

您可以使用會話設定檔來建立專案，例如高度信任的使用者的完整運作會話;允許存取基本的已鎖定會話;專為特定而設計的會話，其中只包含這些工作所需的模組;和不具特殊許可權的使用者只能以特殊許可權帳戶執行特定命令的會話。

此外，您可以管理會話的使用者是否可以使用 Windows PowerShell 的語言專案，例如腳本區塊，或是否只能執行命令。 您可以管理可在會話中執行 Windows PowerShell 使用者的版本;管理哪些模組會匯入到會話;以及管理哪些 Cmdlet、函式和別名會話使用者可以執行。 使用 [RoleDefinitions] 欄位時，您可以根據群組成員資格，為使用者的會話提供不同的功能。

如需有關 RoleDefinitions 以及如何定義此值的詳細資訊，請參閱 New-PSRoleCapabilityFile Cmdlet 的說明主題。

## <a name="creating-a-session-configuration-file"></a>建立會話設定檔

若要建立會話設定檔，最簡單的方式是使用 New-PSSessionConfigurationFile Cmdlet。 此 Cmdlet 會產生使用正確語法和格式的檔案，並自動驗證許多配置檔案屬性值。

如需可在會話設定檔中設定之屬性的詳細說明，請參閱 New-PSSessionConfigurationFile Cmdlet 的說明主題。

下列命令會建立使用預設值的會話設定檔。 產生的設定檔案只會使用預設值，因為 Path 參數以外的參數 (指定檔案路徑) 包含：

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

若要在您的預設文字編輯器中查看新的設定檔，請使用下列命令：

```powershell
Invoke-Item -Path .\Defaults.pssc
```

若要建立會話的會話設定，讓使用者可以在其中執行命令，但不使用 Windows PowerShell 語言的其他元素，請輸入：

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

在上述命令中，將 LanguageMode 參數設定為 NoLanguage，可防止使用者進行撰寫或執行腳本，或使用變數等操作。

若要建立會話的會話設定，讓使用者只能使用 Get Cmdlet，請輸入：

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

在上述範例中，將 VisibleCmdlets 參數設定為 Get-help，會將使用者限制為名稱開頭為字串值 "Get-" 的 Cmdlet。

若要針對以特殊許可權虛擬帳戶（而非使用者認證）執行的會話建立會話設定，請輸入：

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

若要針對在角色功能檔案中指定使用者可看見之命令的會話建立會話設定，請輸入：

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a>使用會話設定檔

您可以在建立會話設定時包含會話設定檔，或新增您稍後可以將檔案新增至會話設定。

若要在建立會話設定時包含會話設定檔，請使用 Register-PSSessionConfiguration Cmdlet 的 Path 參數。

例如，下列命令會在建立 NoLanguage 會話設定時，使用 NoLanguage. .pssc 檔案。

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

當新的 NoLanguage 會話啟動時，使用者只能存取 Windows PowerShell 的命令。

若要將會話設定檔新增至現有的會話設定，請使用 Set-PSSessionConfiguration Cmdlet 和 Path 參數。 這會影響使用指定的會話設定所建立的任何新會話。 請注意，Set-PSSessionConfiguration Cmdlet 會變更會話本身，而不會修改會話設定檔。

例如，下列命令會將 NoLanguage. .pssc 檔案新增至 LockedDown 會話設定。

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

當使用者使用 LockedDown 會話設定來建立會話時，他們將能夠執行 Cmdlet，但他們將無法建立或使用變數、指派值，或使用其他 Windows PowerShell 語言元素。

下列命令使用 New-PSSession Cmdlet 在使用 LockedDown 會話設定的電腦 Srv01 上建立會話，並在 $s 變數中儲存會話的物件參考。 會話設定的 ACL (存取控制清單) 會決定誰可以使用它來建立會話。

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

因為 NoLanguage 條件約束已新增至 LockedDown 會話設定，所以 LockedDown 會話中的使用者將只能執行 Windows PowerShell 命令和 Cmdlet。 例如，下列兩個命令會使用 Invoke-Command Cmdlet，在 $s 變數中所參考的會話中執行命令。 第一個命令會執行 Get-UICulture Cmdlet，且不會使用任何變數，而是會成功。 第二個命令會取得 $PSUICulture 變數的值失敗。

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a>編輯工作階段設定檔

除了將 runasvirtualaccount 設和 RunAsVirtualAccountGroups，會話設定中的所有設定都可以藉由編輯會話設定所使用的會話設定檔來進行修改。 若要這樣做，請先找出會話設定檔的使用中複本。

當您在會話設定中使用會話設定檔時，Windows PowerShell 會建立會話設定檔的使用中複本，並將它儲存 \$ 在 \\ 本機電腦上的 pshome SessionConfig 目錄中。

會話設定檔的使用中複本位置會儲存在會話設定物件的 ConfigFilePath 屬性中。

下列命令會取得 NoLanguage 會話設定之會話設定檔的位置。

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

該命令會傳回類似下列的檔案路徑：

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

您可以在任何文字編輯器中編輯 .pssc 檔案。 儲存檔案之後，任何使用會話設定的新會話都會採用此檔案。

如果您需要修改將 runasvirtualaccount 設或 RunAsVirtualAccountGroups 設定，您必須取消註冊會話設定，並重新註冊包含已編輯值的會話設定檔。

## <a name="testing-a-session-configuration-file"></a>測試會話設定檔

使用 Test-PSSessionConfigurationFile Cmdlet 測試手動編輯的會話設定檔。 這一點很重要：如果檔案語法和值不是有效的，使用者將無法使用會話設定來建立會話。

例如，下列命令會測試 NoLanguage 會話設定的作用中會話設定檔。

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

如果設定檔中的語法和值有效 Test-PSSessionConfigurationFile 會傳回 True。 如果語法和值無效，則 Cmdlet 會傳回 False。

您可以使用 Test-PSSessionConfigurationFile 來測試任何會話設定檔，包括 New-PSSessionConfiguration Cmdlet 所建立的檔案。 如需詳細資訊，請參閱 Test-PSSessionConfigurationFile Cmdlet 的說明主題。

## <a name="removing-a-session-configuration-file"></a>移除會話設定檔

您無法從會話設定中移除會話設定檔。
不過，您可以將檔案取代為使用預設設定的新檔案。 這可有效地取消原始設定檔案所使用的設定。

若要取代會話設定檔，請建立新的會話設定檔，以使用預設設定，然後使用 Set-PSSessionConfiguration Cmdlet 將自訂會話設定檔取代為新的檔案。

例如，下列命令會建立預設會話設定檔，然後取代 NoLanguage 會話設定中的使用中會話設定檔。

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

當這些命令完成時，NoLanguage 會話設定實際上會提供完整的語言支援 (使用該會話設定建立之所有會話的預設設定) 。

使用會話設定檔來查看會話設定的內容：代表會話設定的會話設定物件具有額外的屬性，可讓您輕鬆地探索及分析會話設定。  (請注意，以下所示的類型名稱包含格式化的視圖定義。 ) 您可以執行 Get-PSSessionConfiguration Cmdlet 來查看屬性，並將傳回的資料輸送到 Get-Member Cmdlet：

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

這些屬性可讓您輕鬆地搜尋特定的會話設定。
例如，您可以使用 ExecutionPolicy 屬性來尋找支援會話與 RemoteSigned 執行原則的會話設定。
請注意，因為 ExecutionPolicy 屬性只存在於使用會話設定檔的會話中，所以此命令可能不會傳回所有合格的會話設定。

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

下列命令會取得 RunAsUser 為 Exchange 系統管理員的會話設定。

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

若要查看與設定相關聯之角色定義的相關資訊，請使用 Get-PSSessionCapability Cmdlet。 這個 Cmdlet 可讓您判斷特定端點中特定使用者可用的命令和環境。

## <a name="notes"></a>注意

會話設定也支援稱為「空白」會話的會話類型。 空白的會話類型可讓您使用選取的命令來建立自訂會話。 如果您沒有將模組、函式或腳本新增至空的會話，會話會限制為運算式，而且可能不會有任何實用的用途。 SessionType 屬性會告知您是否正在使用空白會話。

## <a name="see-also"></a>另請參閱

[about_Session_Configurations](about_Session_Configurations.md)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Disable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[Enable-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[Get-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[New-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[Register-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[Set-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[Test-PSSessionConfigurationFile](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[Unregister-PSSessionConfiguration](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[Get-PSSessionCapability](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[New-PSRoleCapabilityFile](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)
