---
ms.date: 09/13/2016
ms.topic: reference
title: 支援線上說明
description: 支援線上說明
ms.openlocfilehash: 0164b5e6c6c8d66a6ab2467a8adfb7efffe0fe17
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645422"
---
# <a name="supporting-online-help"></a>支援線上說明

從 PowerShell 3.0 開始，有兩種方式可以支援 `Get-Help` PowerShell 命令的線上功能。 本主題說明如何針對不同的命令類型來執行這項功能。

## <a name="about-online-help"></a>關於線上說明

線上說明一直是 PowerShell 的重要部分。 雖然指令程式會 `Get-Help` 在命令提示字元中顯示說明主題，但是許多使用者都偏好線上閱讀的體驗，包括色彩編碼、超連結，以及在社區內容和以 wiki 為基礎的檔中共用想法。 最重要的是，在有可更新的說明之前，線上說明提供最新版本的說明檔。

隨著 PowerShell 3.0 中的可更新說明，線上說明仍扮演重要的角色。 除了有彈性的使用者體驗之外，線上說明也可提供協助，讓沒有或無法使用「可更新的說明」的使用者下載說明主題。

## <a name="how-get-help--online-works"></a>Get-Help-Online 的運作方式

為了協助使用者找到命令的線上說明主題， `Get-Help` 命令具有線上參數，可在使用者的預設網際網路瀏覽器中開啟命令的線上版說明主題。

例如，下列命令會開啟 Cmdlet 的線上說明主題 `Invoke-Command` 。

```powershell
Get-Help Invoke-Command -Online
```

為了執行 `Get-Help -Online` ，此 `Get-Help` Cmdlet 會在下列位置中尋找線上版本說明主題的統一資源識別項 (URI) 。

- 命令之說明主題的 [ **相關連結** ] 區段中的第一個連結。 您必須在使用者的電腦上安裝說明主題。 這項功能是在 PowerShell 2.0 中引進。

- 任何命令的 **HelpUri** 屬性。 即使使用者的電腦上未安裝命令的說明主題，也可以存取 **HelpUri** 屬性。 這項功能是在 PowerShell 3.0 中引進。

  `Get-Help`取得 **HelpUri** 屬性值之前，請在 [**相關連結**] 區段的第一個專案中尋找 URI。 如果屬性值不正確或已變更，您可以在第一個相關連結中輸入不同的值來覆寫它。 不過，第一個相關的連結只適用于在使用者電腦上安裝說明主題時。

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>將 URI 新增至命令說明主題的第一個相關連結

您可以針對 `Get-Help -Online` 命令的 XML 型說明主題之 [ **相關連結** ] 區段中的第一個專案新增有效的 URI，以支援任何命令。 此選項只適用于以 XML 為基礎的說明主題，而且只有在說明主題安裝在使用者的電腦上時才適用。 安裝說明主題並填入 URI 之後，這個值的優先順序會高於命令的 **HelpUri** 屬性。

若要支援這項功能，URI 必須出現在元素中第一個元素底下的專案中 `maml:uri` `maml:relatedLinks/maml:navigationLink` `maml:relatedLinks` 。

下列 XML 會顯示 URI 的正確位置。 專案 `Online version:` 中的文字 `maml:linkText` 是最佳做法，但不是必要的。

```xml
<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>將 HelpUri 屬性新增至命令

本節說明如何將 HelpUri 屬性新增至不同類型的命令。

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>將 HelpUri 屬性新增至 Cmdlet

針對以 c # 撰寫的 Cmdlet，請將 **HelpUri** 屬性新增至 **Cmdlet** 類別。 屬性的值必須是以或開頭的 URI `http` `https` 。

下列程式碼顯示 Cmdlet 類別的 **HelpUri** 屬性 `Get-History` 。

```csharp
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>將 HelpUri 屬性加入至 Advanced 函數

若為 advanced 函數，請將 **HelpUri** 屬性加入至 **CmdletBinding** 屬性。 屬性的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。

下列程式碼顯示函數的 **HelpUri** 屬性。 `New-Calendar`

```powershell
function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>將 HelpUri 屬性新增至 CIM 命令

若為 CIM 命令，請將 **HelpUri** 屬性加入至 CDXML 檔案中的 **CmdletMetadata** 元素。
屬性的值必須是以或開頭的 URI `http` `https` 。

下列程式碼顯示 CIM 命令的 HelpUri 屬性 `Start-Debug`

```xml
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>將 HelpUri 屬性加入至工作流程

針對以 PowerShell 語言撰寫的工作流程，請新增 **。** 將批註指示詞 .externalhelp 至工作流程程式碼。 指示詞的值必須是以或開頭的 URI `http` `https` 。

> [!NOTE]
> PowerShell 中以 XAML 為基礎的工作流程不支援 HelpUri 屬性。

下列程式碼顯示。工作流程檔案中的 .Externalhelp 指示詞。

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
