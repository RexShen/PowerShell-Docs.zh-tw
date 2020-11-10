---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: a21c2974fd66a9b02929752ae487c8995579b8a7
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388819"
---
# Add-PSSnapin

## 概要
新增一或多個 Windows PowerShell 嵌入式管理單元至目前的工作階段。

## SYNTAX

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

`Add-PSSnapin`Cmdlet 會將已註冊 Windows PowerShell 嵌入式管理單元新增至目前的會話。 新增嵌入式管理單元之後，您就可以在目前的工作階段中使用嵌入式管理單元支援的 Cmdlet 與提供者。

若要將嵌入式管理單元新增至所有未來的 Windows PowerShell 會話，請將 `Add-PSSnapin` 命令新增至您的 Windows PowerShell 設定檔。 如需詳細資訊，請參閱 [about_Profiles](about/about_Profiles.md)。

從 Windows PowerShell 3.0 開始，Windows PowerShell 中包含的核心命令已經封裝成模組。 **Microsoft.PowerShell.Core** 是一個例外，它是一個嵌入式管理單元 (PSSnapin)。
依照預設，只會新增 **Microsoft.PowerShell.Core** 嵌入式管理單元至工作階段。 模組會在第一次使用時自動匯入，而您可以使用 Import-Module Cmdlet 來匯入它們。

## 範例

### 範例1：新增嵌入式管理單元

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

此命令會將 Microsoft Exchange 與 Active Directory 嵌入式管理單元新增至目前的工作階段。

### 範例2：新增所有已註冊的嵌入式管理單元

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

此命令會將所有已註冊的 Windows PowerShell 嵌入式管理單元新增至工作階段。 它會使用 Get-PSSnapin Cmdlet 搭配 **已註冊** 的參數，以取得代表每個已註冊嵌入式管理單元的物件。管線運算子 (|) 將結果傳遞給 `Add-PSSnapin` ，以將其新增至會話。 **PassThru** 參數會傳回代表每個新增之嵌入式管理單元的物件。

### 範例3：註冊嵌入式管理單元並加以新增

第一個命令會取得已新增至目前會話的嵌入式管理單元，其中包含隨 Windows PowerShell 安裝的嵌入式管理單元。 在這個範例中，並沒有傳回 ManagementFeatures。 這表示它尚未新增至工作階段。

第二個命令會取得已在系統上註冊的嵌入式管理單元，其中包括已新增至會話的嵌入式管理單元。 它不包含隨 Windows PowerShell 安裝的嵌入式管理單元。 在此情況下，此命令不會傳回任何嵌入式管理單元。這表示 ManagementFeatures 嵌入式管理單元未在系統上註冊。

第三個命令會在 .NET Framework 中建立 Installutil.exe 工具路徑的別名 installutil.exe。

第四個命令會使用 Installutil.exe 工具來註冊嵌入式管理單元。 此命令會指定 ManagementCmdlets.dll 的路徑，也就是嵌入式管理單元的檔案名或模組名稱。

第五個命令與第二個命令相同。 這一次您是使用此命令來確認 ManagementCmdlets 嵌入式管理單元已經註冊。

第六個命令會使用 `Add-PSSnapin` Cmdlet 將 ManagementFeatures 嵌入式管理單元新增至會話。 它會指定 ManagementFeatures 嵌入式管理單元的名稱，而不是檔案名稱。

為了確認此嵌入式管理單元是否已新增至會話，第七個命令使用 Get-Command Cmdlet 的 **Module** 參數。 它會顯示由嵌入式管理單元或模組新增至工作階段的項目。

您也可以使用 Cmdlet 所傳回之物件的 **PSSnapin** 屬性， `Get-Command` 來尋找 Cmdlet 所產生的嵌入式管理單元或模組。 第八個命令會使用點標記法來尋找 Set-Alias Cmdlet 的 PSSnapin 屬性值。

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

此範例示範在您的系統上註冊嵌入式管理單元，然後將它們新增至您的工作階段的處理程序。 它會使用 ManagementFeatures，這是在名為 ManagementCmdlets.dll 的檔案中執行的虛構嵌入式管理單元。

## PARAMETERS

### -Name

指定嵌入式管理單元的名稱。 這是名稱，而不是 AssemblyName 或 ModuleName。 允許使用萬用字元。

若要尋找您系統上已註冊之嵌入式管理單元的名稱，請輸入 `Get-PSSnapin -Registered` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

指出此 Cmdlet 會傳回代表每個新增之嵌入式管理單元的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### 無或 System.Management.Automation.PSSnapInInfo

如果您指定 **PassThru** 參數，此 Cmdlet 會傳回代表嵌入式管理單元的 PSSnapInInfo 物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

- 從 Windows PowerShell 3.0 開始，與 Windows PowerShell 一起安裝的核心命令已經封裝成模組。 在 Windows PowerShell 2.0，以及在較新版本的 Windows PowerShell 中建立舊版會話的主機程式中，核心命令會封裝在嵌入式管理單元 (PSSnapins) 中。 **Microsoft.PowerShell.Core** 是一個例外，它一律是一個嵌入式管理單元。 此外，遠端工作階段 (例如由 New-PSSession cmdlet 所啟動的遠端工作階段) 都是包含核心嵌入式管理單元的舊式工作階段。

  如需使用核心模組建立較新樣式會話之 **CreateDefault2** 方法的詳細資訊，請參閱 [CreateDefault2 方法](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2)。

- 如需嵌入式管理單元的詳細資訊，請參閱 [about_PSSnapins](About/about_PSSnapins.md) 以及 [如何建立 Windows PowerShell 嵌入式管理](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in)單元。
- `Add-PSSnapin` 僅將嵌入式管理單元新增至目前的會話。 若要將嵌入式管理單元新增至所有 Windows PowerShell 工作階段，請將它新增至您的 Windows PowerShell 設定檔。 如需詳細資訊，請參閱 about_Profiles。
- 您可以新增任何已使用 Microsoft .NET Framework 安裝公用程式註冊的嵌入式管理單元。 如需詳細資訊，請參閱 [如何註冊 Cmdlet、提供者和主機應用程式](/previous-versions//ms714644(v=vs.85))。
- 若要取得已在電腦上註冊的嵌入式管理單元清單，請輸入 `Get-PSSnapin -Registered` 。
- 在新增嵌入式管理單元之前，請先檢查嵌入式管理單元的 `Add-PSSnapin` 版本，以確認它是否與 Windows PowerShell 的目前版本相容。 如果嵌入式管理單元版本檢查失敗，Windows PowerShell 會回報錯誤。

## 相關連結

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
