---
description: 說明語言模式及其對 PowerShell 會話的影響。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 2cf232fd170ee9175f40693579cca60f69ccbcdd
ms.sourcegitcommit: fb1a4bc4b249afd3513663de2e1ba3025d63467e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2020
ms.locfileid: "94625732"
---
# <a name="about-language-modes"></a>關於語言模式

## <a name="short-description"></a>簡短描述
說明語言模式及其對 PowerShell 會話的影響。

## <a name="long-description"></a>詳細描述

PowerShell 會話的語言模式會決定可以在會話中使用 PowerShell 語言的哪些元素。

PowerShell 支援下列語言模式：

- FullLanguage
- PowerShell 3.0 中引進的 ConstrainedLanguage () 
- RestrictedLanguage
- NoLanguage

### <a name="what-is-a-language-mode"></a>什麼是語言模式？

語言模式會決定會話中允許的語言元素。

語言模式實際上是會話設定的屬性 (或用來建立會話的「端點」 ) 。 使用特定會話設定的所有會話都具有會話設定的語言模式。

所有的 PowerShell 會話都有語言模式，包括您使用 Cmdlet 建立的 Pssession `New-PSSession` 、使用 ComputerName 參數的暫時會話，以及啟動 PowerShell 時出現的預設會話。

遠端會話是使用遠端電腦上的會話設定所建立。 會話設定中設定的語言模式會決定會話的語言模式。 若要指定 PSSession 的會話設定，請使用建立會話之 Cmdlet 的 ConfigurationName 參數。

### <a name="language-modes"></a>語言模式

本節說明 PowerShell 會話中的語言模式。

#### <a name="full-language-fulllanguage"></a>完整語言 (>fulllanguage) 

>fulllanguage 模式允許會話中的所有語言元素。
>fulllanguage 是所有 Windows 版本上預設會話的預設語言模式，但 Windows RT 除外。

#### <a name="restricted-language-restrictedlanguage"></a>受限制的語言 (RestrictedLanguage) 

在 RestrictedLanguage 模式中，使用者可 (Cmdlet、函式、CIM 命令和工作流程執行命令) 但不允許使用腳本區塊。

根據預設，RestrictedLanguage 模式中只允許下列變數：

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

使用 RestrictedLanguage 模式的模組資訊清單也會允許下列其他變數：

- `$PSScriptRoot`
- `$PSEdition` PowerShell Core) 中的 (
- `$EnabledExperimentalFeatures` PowerShell Core) 中的 (

只允許下列比較運算子：

- `-eq` (等於) 
- `-gt` (大於) 
- `-lt` (小於) 

不允許指派陳述式、屬性參照及方法呼叫。

#### <a name="no-language-nolanguage"></a>沒有語言 (NoLanguage) 

NoLanguage 模式只能透過 API 使用。 NoLanguage 模式表示不允許任何表單的腳本文字。 這樣就不會使用 **AddScript ( # B1** 方法來傳送要剖析和執行的 PowerShell 腳本片段。 您只能使用 **AddCommand ( # B1** 和 **AddParameter ( # B3** ，而不會經過剖析器。

#### <a name="constrained-language-constrained-language"></a>受限語言 (受限語言) 

ConstrainedLanguage 模式允許所有 Cmdlet 和所有 PowerShell 語言元素，但它會限制允許的類型。

ConstrainedLanguage 模式是設計用來支援 Windows RT 上的使用者模式程式碼完整性 (UMCI) 。 它是 Windows RT 上唯一支援的語言模式，但可在所有支援的系統上使用。

UMCI 藉由只允許在 Windows RT 型裝置上安裝 Microsoft 簽署和經 Microsoft 認證的應用程式，來保護 ARM 裝置。
ConstrainedLanguage 模式會防止使用者使用 PowerShell 規避或違反 UMCI。

ConstrainedLanguage 模式的功能如下所示：

- Windows 模組中的所有 Cmdlet，以及其他 UMCI 核准的 Cmdlet 皆可完全正常運作，並可完整存取系統資源（如所述除外）。

- 允許 PowerShell 指令碼語言的所有元素。

- 您可以匯入 Windows 中包含的所有模組，以及模組匯出在會話中執行的所有命令。

- 在 PowerShell 工作流程中，您可以撰寫和執行以 PowerShell 語言) 撰寫 (工作流程的腳本工作流程。 不支援以 XAML 為基礎的工作流程，而且您無法在腳本工作流程（例如使用）中執行 XAML `Invoke-Expression -Language XAML` 。 此外，工作流程無法呼叫其他工作流程，雖然允許嵌套工作流程。

- `Add-Type`Cmdlet 可以載入已簽署的元件，但無法載入任意的 c # 程式碼或 Win32 api。

- 此 `New-Object` Cmdlet 只能用在以下) 所列的允許類型 (：

- 只有下面所列的允許類型 (可在 PowerShell 中使用) 。 不允許其他類型。

- 允許類型轉換，但只有在結果是允許的類型時。

- 只有當產生的型別是允許的型別時，才會將字串輸入轉換成類型的 Cmdlet 參數。

- 您可以叫用 **ToString ( # B1** 方法和允許類型 (的 .net 方法，如下所示) 。 無法叫用其他方法。

- 使用者可以取得允許類型的所有屬性。 使用者只能在核心類型上設定屬性的值。 只允許下列 COM 物件：

  - **腳本字典**
  - **Scripting.FileSystemObject**
  - **VBScript. RegExp**

以下是在 ConstrainedLanguage 模式中允許的類型。 使用者可以取得屬性、叫用方法，以及將物件轉換為這些類型。

允許的類型：

- AliasAttribute
- AllowEmptyCollectionAttribute
- AllowEmptyStringAttribute
- AllowNullAttribute
- Array
- Bool
- byte
- char
- CmdletBindingAttribute
- Datetime
- decimal
- DirectoryEntry
- DirectorySearcher
- double
- FLOAT
- Guid
- 雜湊表
- int
- Int16
- long
- ManagementClass
- System.management.managementobject
- ManagementObjectSearcher
- NullString
- OutputTypeAttribute
- ParameterAttribute
- PSCredential
- PSDefaultValueAttribute
- PSListModifier
- PSObject
- PSPrimitiveDictionary
- PSReference
- PSTypeNameAttribute
- Regex
- SByte
- 字串
- SupportsWildcardsAttribute
- SwitchParameter
- System.Globalization.CultureInfo
- 系統 .Net IPAddress
- 系統 .Net MailAddress
- BigInteger
- System.Security.SecureString
- TimeSpan
- UInt16
- UInt32
- UInt64

### <a name="finding-the-language-mode-of-a-session-configuration"></a>尋找會話設定的語言模式

使用會話設定檔建立會話設定時，會話設定具有 LanguageMode 屬性。 您可以藉由取得 LanguageMode 屬性的值來尋找語言模式。

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

在其他會話設定中，您可以藉由尋找使用會話設定建立之會話的語言模式，來間接找到語言模式。

### <a name="finding-the-language-mode-of-a-session"></a>尋找會話的語言模式

您可以取得會話狀態的 LanguageMode 屬性值，以尋找 >fulllanguage 或 ConstrainedLanguage 會話的語言模式。

例如：

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

不過，在具有 RestrictedLanguage 和 NoLanguage 模式的會話中，您無法使用點方法來取得屬性值。 相反地，錯誤訊息會顯示語言模式。

當您 `$ExecutionContext.SessionState.LanguageMode` 在 RestrictedLanguage 會話中執行命令時，PowerShell 會傳回 PropertyReferenceNotSupportedInDataSection 和 VariableReferenceNotSupportedInDataSection 錯誤訊息。

- PropertyReferenceNotSupportedInDataSection：不允許在受限制的語言模式或資料區段中使用屬性參考。
- VariableReferenceNotSupportedInDataSection 無法在受限制的語言模式下參考的變數，或參考的資料區段。

當您 `$ExecutionContext.SessionState.LanguageMode` 在 NoLanguage 會話中執行命令時，PowerShell 會傳回 ScriptsNotAllowed 錯誤訊息。

- ScriptsNotAllowed：此執行空間不支援語法。 這可能是因為它在無語言模式中。

## <a name="see-also"></a>另請參閱

- [about_Session_Configuration_Files](about_Session_Configuration_Files.md)
- [about_Session_Configurations](about_Session_Configurations.md)
