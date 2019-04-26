---
title: 撰寫 Windows PowerShell 模組的說明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082021"
---
# <a name="writing-help-for-windows-powershell-modules"></a>撰寫 Windows PowerShell 模組的說明

Windows PowerShell 模組可以包含有關模組和模組成員，例如 cmdlet、 提供者、 函式和指令碼的說明主題。 `Get-Help` Cmdlet 會顯示模組的 [說明] 主題相同的格式，它會顯示其他 Windows PowerShell 項目，說明，以及使用者使用標準`Get-Help`命令來取得 [說明] 主題。

本文件說明的格式和模組說明主題，正確位置，並建議讓模組的說明內容的指導方針。

## <a name="types-of-module-help"></a>類型的模組說明

模組可以包含下列類型的說明。

- **指令程式說明**。 描述模組中的 cmdlet 的說明主題會使用命令的 XML 檔可幫助的結構描述

- **提供者說明**。 描述在模組中的提供者的說明主題會使用提供者的 XML 檔可幫助的結構描述。

- **函式說明**。 說明 主題描述在模組中的函式可以是結構描述或函式，或在指令碼或指令碼模組的 註解式說明主題，協助使用命令的 XML 檔案

- **指令碼說明**。 描述指令碼模組中的 [說明] 主題可以是結構描述或指令碼或指令碼模組中的註解式說明主題，協助使用命令的 XML 檔案。

- **概念性 （「 關於 」） 說明**。 描述模組和其成員，並說明如何成員可同時執行工作時，您可以使用概念性 （「 關於 」） 說明主題。 概念性說明主題是以 Unicode (utf-8) 編碼的文字檔。 檔案名稱必須使用`about_<name>.help.txt`格式，例如 about_MyModule.help.txt。 根據預設，Windows PowerShell 包含超過 100 個概念的相關說明主題，而它們的格式如下列範例所示。

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>位置的模組說明

`Get-Help` Cmdlet 會尋找模組的模組目錄中的特定語言子目錄中的 [說明] 主題檔案。

例如，下列目錄結構圖表會顯示 SampleModule 模組的 [說明] 主題的位置。

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> 在範例中，  *\<ModulePath >* 預留位置，代表其中一個路徑中`PSModulePath`環境變數，例如 $home\Documents\Modules、 $pshome\Modules 或使用者指定的自訂路徑。

## <a name="getting-module-help"></a>取得模組的說明

當使用者將模組匯入到工作階段時，該模組的 [說明] 主題會匯入到隨著該模組的工作階段。 您可以列出說明主題中的檔案的模組資訊清單中的 FileList 索引鍵的值，但不是會影響 [說明] 主題`Export-ModuleMember`cmdlet。

您可以提供以不同語言的模組說明主題。 `Get-Help`指令程式會自動顯示模組的說明主題中針對目前的使用者，在 [地區及語言選項] 控制台項目中指定的語言。 在 Windows Vista 和更新版本的 Windows，`Get-Help`搜尋的模組目錄中建立 Windows 的語言後援標準符合的特定語言子目錄中的 [說明] 主題。

在 Windows PowerShell 3.0 中，執行從`Get-Help`cmdlet 或函式的命令就會觸發自動匯入模組。 `Get-Help` Cmdlet 模組中立即顯示 [說明] 主題的內容。

如果模組沒有包含 [說明] 主題，而且不有任何使用者的電腦上的模組中命令的說明主題`Get-Help`顯示自動產生的說明。 自動產生的說明包含命令語法、 參數以及輸入和輸出類型，但不包含任何描述。 自動產生的說明包含文字，以指示使用者先嘗試使用`Update-Help`cmdlet 來從網際網路或檔案共用下載命令的說明。 它也會建議使用**線上**參數`Get-Help`cmdlet 來取得 [說明] 主題的線上版本。

## <a name="supporting-updatable-help"></a>支援可更新的說明

使用者的 Windows PowerShell 3.0 和更新版本的 Windows PowerShell 可以下載並安裝模組的已更新的說明檔從網際網路或從本機檔案共用。 `Update-Help`和`Save-Help`cmdlet 會隱藏使用者管理詳細資料。 使用者執行`Update-Help`cmdlet，然後使用`Get-Help`cmdlet 來讀取該模組在 Windows PowerShell 命令提示字元的最新說明檔案。 使用者不需要重新啟動 Windows 或 Windows PowerShell。

背後的防火牆以及沒有網際網路存取的使用者也可以使用可更新的說明。 與網際網路的系統管理員存取使用`Save-Help`cmdlet 來下載並安裝最新說明檔案至檔案共用。 接著，使用者使用**路徑**參數`Update-Help`cmdlet 來取得最新說明檔案從檔案共用。

模組作者可以在模組中包含說明檔並使用可更新的說明更新說明檔，或省略從模組的說明檔，並使用可更新的說明來安裝並加以更新。

如需有關可更新說明的詳細資訊，請參閱 <<c0> [ 支援可更新說明](./supporting-updatable-help.md)。

## <a name="supporting-online-help"></a>支援線上說明

使用者無法或不安裝更新其電腦上的檔案通常會依賴模組說明主題的線上版本的說明。 **線上**參數`Get-Help`指令程式會在其預設網際網路瀏覽器中開啟指令程式或使用者的進階函式說明主題的線上版本。

`Get-Help` Cmdlet 會使用值**HelpUri** cmdlet 或函式來尋找說明主題的線上版本的屬性。

從 Windows PowerShell 3.0 開始，您可以協助使用者尋找 cmdlet 與函式的 [說明] 主題的線上版本，透過在 cmdlet 類別上定義的 HelpUri 屬性或**HelpUri**屬性**CmdletBinding**屬性。 屬性的值是值**HelpUri** cmdlet 或函式的屬性。

如需詳細資訊，請參閱 <<c0> [ 支援線上說明](./supporting-online-help.md)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)

[支援可更新的說明](./supporting-updatable-help.md)

[支援線上說明](./supporting-online-help.md)