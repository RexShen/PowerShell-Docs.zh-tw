---
title: 支援線上說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360657"
---
# <a name="supporting-online-help"></a>支援線上說明

從 Windows PowerShell 3.0 開始，有兩種方式可支援 Windows PowerShell 命令的 @no__t 0 線上功能。 本主題說明如何針對不同的命令類型來執行這項功能。

## <a name="about-online-help"></a>關於線上說明

線上說明一直是 Windows PowerShell 的重要部分。 雖然 `Get-Help` Cmdlet 會在命令提示字元中顯示說明主題，但許多使用者偏好閱讀線上的經驗，包括色彩編碼、超連結，以及在社區內容和 wiki 架構檔中分享想法。 最重要的是，在「可更新的說明」出現之前，線上說明已提供最新版本的說明檔。

隨著 Windows PowerShell 3.0 中的「可更新的說明」的出現，線上說明仍然扮演重要的角色。 除了彈性的使用者體驗之外，線上說明也能協助不使用「可更新的說明」下載說明主題的使用者。

## <a name="how-get-help--online-works"></a>Get-help-Online 的運作方式

為了協助使用者尋找命令的線上說明主題，`Get-Help` 命令具有線上參數，可開啟使用者預設網際網路瀏覽器中命令的線上版本說明主題。

例如，下列命令會開啟 `Invoke-Command` Cmdlet 的線上說明主題。

```powershell
Get-Help Invoke-Command -Online
```

若要執行 `Get-Help`-Online，@no__t 1 Cmdlet 會在下列位置尋找線上版本說明主題的統一資源識別元（URI）。

- 命令之說明主題的 [相關連結] 區段中的第一個連結。 您必須在使用者的電腦上安裝說明主題。 這項功能是在 Windows PowerShell 2.0 中引進。

- 任何命令的 HelpUri 屬性。 即使未在使用者的電腦上安裝命令的說明主題，仍可存取 HelpUri 屬性。 這項功能是在 Windows PowerShell 3.0 中引進。

  `Get-Help` 會在 [相關連結] 區段的第一個專案中尋找 URI，然後才取得 HelpUri 屬性值。 如果屬性值不正確或已變更，您可以在第一個相關連結中輸入不同的值來覆寫它。 不過，第一個相關的連結僅適用于在使用者的電腦上安裝說明主題時。

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>將 URI 新增至命令說明主題的第一個相關連結

您可以在命令的 XML 型說明主題的 [相關連結] 區段中，將有效的 URI 新增至第一個專案，以支援任何命令的 `Get-Help`-Online。 這個選項只有在以 XML 為基礎的說明主題中才有效，而且只有在說明主題安裝在使用者的電腦上時才適用。 安裝說明主題並填入 URI 後，此值會優先于命令的**HelpUri**屬性。

若要支援這項功能，URI 必須出現在 `maml:relatedLinks` 元素中第一個 `maml:relatedLinks/maml:navigationLink` 元素下的 `maml:uri` 元素中。

下列 XML 會顯示正確的 URI 位置。 @No__t-0 元素中的「線上版本：」文字是最佳做法，但並非必要。

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
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

針對以C#撰寫的 Cmdlet，將**HelpUri**屬性新增至 Cmdlet 類別。 屬性的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。

下列程式碼顯示 `Get-History` Cmdlet 類別的 HelpUri 屬性。

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>將 HelpUri 屬性加入至 Advanced 函數

針對 advanced 函式，將**HelpUri**屬性新增至**CmdletBinding**屬性。 屬性的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。

下列程式碼顯示新行事曆函數的 HelpUri 屬性

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>將 HelpUri 屬性新增至 CIM 命令

針對 CIM 命令，請將**HelpUri**屬性新增至 CDXML 檔案中的**CmdletMetadata**元素。 屬性的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。

下列程式碼顯示啟動-Debug CIM 命令的 HelpUri 屬性

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>將 HelpUri 屬性新增至工作流程

針對以 Windows PowerShell 語言撰寫的工作流程，請新增 **.Externalhelp**批註指示詞至工作流程程式碼。 指示詞的值必須是以 "HTTP" 或 "HTTPs" 開頭的 URI。

> [!NOTE]
> Windows PowerShell 中以 XAML 為基礎的工作流程不支援 HelpUri 屬性。

下列程式碼會顯示。工作流程檔案中的 .Externalhelp 指示詞。

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```