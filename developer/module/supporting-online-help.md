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
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857914"
---
# <a name="supporting-online-help"></a>支援線上說明

從 Windows PowerShell 3.0 開始，有兩種方式，以支援`Get-Help`Windows PowerShell 命令的線上功能。 本主題說明如何實作此功能，針對不同的命令類型。

## <a name="about-online-help"></a>關於線上說明

線上說明一直是 Windows PowerShell 中不可或缺的一部分。 雖然`Get-Help`cmdlet 會顯示 [說明] 主題，在命令提示字元中，許多使用者偏好的線上閱讀，包含色彩編碼、 超連結及社群內容和 wiki 文件中的共用想法的體驗。 最重要的是，可更新的說明問世之前, 的線上說明所提供說明檔案的最新的版本。

隨著可更新的說明，在 Windows PowerShell 3.0 中，線上說明，仍扮演重要角色。 除了彈性的使用者體驗，線上說明會提供給使用者，對於沒有或無法使用可更新的說明下載說明主題的說明。

## <a name="how-get-help--online-works"></a>如何取得說明-線上的運作方式

若要協助使用者尋找線上 [說明] 主題的命令，`Get-Help`命令有線上的參數，在使用者的預設網際網路瀏覽器中開啟命令的說明主題的線上版本。

例如，下列命令會開啟線上說明主題的`Invoke-Command`cmdlet。

```powershell
Get-Help Invoke-Command -Online
```

若要實作`Get-Help`-線上`Get-Help`cmdlet 看起來的統一資源識別元 (URI) 的線上版本說明主題，在下列位置。

- 命令的說明主題的相關連結 區段中的第一個連結。 在使用者電腦上必須安裝 [說明] 主題。 在 Windows PowerShell 2.0 引進這項功能。

- 任何命令的 HelpUri 屬性。 即使命令的 [說明] 主題未安裝在使用者電腦上存取的 HelpUri 屬性。 這項功能是在 Windows PowerShell 3.0 引進。

  `Get-Help` 取得 HelpUri 屬性值之前尋找相關連結 區段中的第一個項目中的 URI。 如果屬性值不正確，或已變更，您可以在第一個相關連結中輸入不同的值來覆寫它。 不過，第一個相關連結僅適用於使用者的電腦上已安裝的說明主題。

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>將 URI 新增至命令的說明主題的第一個相關連結

您可以在支援`Get-Help`-線上的任何命令，以 XML 為基礎的說明主題之命令的相關連結 區段中的第一個項目中加入有效的 URI。 此選項僅適用於以 XML 為基礎的說明主題，且只有在使用者的電腦上已安裝的說明主題時，才會運作。 安裝 [說明] 主題，並會填入 URI，這個值會優先**HelpUri**命令的屬性。 以 XML 為基礎命令的說明主題的相關資訊，請參閱[Writing XML-Based 命令的說明主題](../help/writing-xml-based-help-topics-for-commands.md)。

若要支援這項功能，URI 必須出現在`maml:uri`置於第一個項目`maml:relatedLinks/maml:navigationLink`中的項目`maml:relatedLinks`項目。

下列 XML 顯示正確的 URI 位置。 「 線上版本:"中的文字`maml:linkText`項目是最佳作法，但並非必要。

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

## <a name="adding-the-helpuri-property-to-a-command"></a>將 HelpUri 屬性加入至命令

本節說明如何將 HelpUri 屬性加入至不同類型的命令。

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>將 HelpUri 屬性加入至指令程式

以撰寫的 cmdlet C#，新增**HelpUri**屬性設定為在 Cmdlet 類別。 屬性的值必須是以"http"或"https"開頭的 URI。

下列程式碼顯示的 HelpUri 屬性`Get-History`cmdlet 類別。

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>新增進階的函式的 HelpUri 屬性

進階的函式中，新增**HelpUri**屬性設**CmdletBinding**屬性。 屬性的值必須是以"http"或"https"開頭的 URI。

下列程式碼會顯示新行事曆函式的 HelpUri 屬性

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>將 HelpUri 屬性加入至 CIM 命令

如需 CIM 命令，新增**HelpUri**屬性設定為**CmdletMetadata** CDXML 檔案中的項目。 屬性的值必須是以"http"或"https"開頭的 URI。

下列程式碼會顯示 開始偵錯 CIM 命令的 HelpUri 屬性

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>加入至工作流程的 HelpUri 屬性

以 Windows PowerShell 語言撰寫的工作流程，新增 **。ExternalHelp**註解指示詞，以便在工作流程程式碼。 指示詞的值必須是以"http"或"https"開頭的 URI。

> [!NOTE]
> 在 Windows PowerShell 中的 XAML 型工作流程不支援的 HelpUri 屬性。

下列程式碼所示。在工作流程檔案 ExternalHelp 指示詞。

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```