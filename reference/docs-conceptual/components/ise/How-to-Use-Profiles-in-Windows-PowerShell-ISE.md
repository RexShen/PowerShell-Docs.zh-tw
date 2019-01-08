---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 如何在 Windows PowerShell ISE 中使用設定檔
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400804"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>如何在 Windows PowerShell ISE 中使用設定檔

本主題說明如何在 Windows PowerShell® 整合式指令碼環境 (ISE) 中使用設定檔。 建議您在執行本節所述的工作之前，先檢閱 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)，或在 [主控台] 窗格中輸入 `Get-Help about_Profiles`，然後按 **ENTER** 鍵。

設定檔是當您啟動新的工作階段時自動執行的 Windows PowerShell ISE 指令碼。  您可以為 Windows PowerShell ISE 建立一或多個 Windows PowerShell 設定檔，然後使用這些設定檔來新增 Windows PowerShell 或 Windows PowerShell ISE 環境的設定、準備環境供您使用，以及提供您所需的變數、別名、函式、色彩和字型喜好設定。 設定檔會影響您啟動的每個 Windows PowerShell ISE 工作階段。

> [!NOTE]
> Windows PowerShell 執行原則會決定您是否可以執行指令碼並載入設定檔。 預設執行原則 “Restricted” 可防止所有指令碼執行，包括設定檔。 如果使用 “Restricted” 原則，則無法載入設定檔。 如需執行原則的詳細資訊，請參閱 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>選取要在 Windows PowerShell ISE 中使用的設定檔

Windows PowerShell ISE 支援目前使用者和所有使用者的設定檔。 它也支援適用於所有主機的 Windows PowerShell 設定檔。

您使用的設定檔取決於您使用 Windows PowerShell 和 Windows PowerShell ISE 的方式。

- 如果只使用 Windows PowerShell ISE 來執行 Windows PowerShell，則要將所有項目儲存到 ISE 特定的其中一個設定檔，例如，適用於 Windows PowerShell ISE 的 CurrentUserCurrentHost 設定檔，或者適用於 Windows PowerShell ISE 的 AllUsersCurrentHost 設定檔。

- 如果使用多個主機程式來執行 Windows PowerShell，請在影響所有主機程式的設定檔 (例如 CurrentUserAllHosts 或 AllUsersAllHosts 設定檔) 中儲存您的函式、別名、變數和命令，並在適用於 Windows PowerShell ISE 設定檔的 CurrentUserCurrentHost 設定檔或適用於 Windows PowerShell ISE 的 AllUsersCurrentHost 設定檔中儲存 ISE 特定的功能 (例如色彩和字型自訂)。

以下是可在 Windows PowerShell ISE 中建立及使用的設定檔。 每個設定檔會儲存到自己的特定路徑。

| 設定檔類型 | 設定檔路徑 |
| --- | --- |
| **目前的使用者，PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost`，或 `$PROFILE` |
| **所有使用者，PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **目前的使用者，所有主機**| `$PROFILE.CurrentUserAllHosts` |
| **所有使用者，所有主機** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>建立新的設定檔

若要建立新的 “Current user, Windows PowerShell ISE” 設定檔，請執行下列命令︰

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

若要建立新的 “All users, Windows PowerShell ISE” 設定檔，請執行下列命令︰

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

若要建立新的 “Current user, All Hosts” 設定檔，請執行下列命令︰

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

若要建立新的 “All users, All Hosts” 設定檔，請輸入︰

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>編輯設定檔

1. 若要開啟設定檔，請執行命令 psedit，並提供指定您要編輯之設定檔的變數。 例如，若要開啟 “Current user, Windows PowerShell ISE” 設定檔，請輸入︰`psEdit $PROFILE`

2. 將一些項目新增至您的設定檔。 以下是一些可協助您開始的範例︰

   - 若要將主控台窗格的預設背景色彩變更為藍色，請在設定檔中輸入︰`$psISE.Options.OutputPaneBackground = 'blue'`。 如需 $psISE 變數的詳細資訊，請參閱 [Windows PowerShell ISE 物件模型參考](object-model/The-ISE-Object-Model-Hierarchy.md)。

   - 若要將字型大小變更為 20，請在設定檔中輸入︰`$psISE.Options.FontSize =20`

3. 若要儲存設定檔，請在 **[檔案]** 功能表上，按一下 **[儲存]**。 下次當您開啟 Windows PowerShell ISE 時，便會套用您的自訂。

## <a name="see-also"></a>另請參閱

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Windows PowerShell ISE 簡介](Introducing-the-Windows-PowerShell-ISE.md)