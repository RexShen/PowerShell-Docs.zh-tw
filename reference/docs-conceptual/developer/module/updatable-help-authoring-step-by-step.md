---
title: 可更新的說明撰寫：逐步執行 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366987"
---
# <a name="updatable-help-authoring-step-by-step"></a>可更新的說明撰寫：逐步

本檔列出撰寫可更新的說明程式中的步驟。

## <a name="authoring-updatable-help-step-by-step"></a>撰寫可更新的說明：逐步解說

「可更新的說明」是針對一般使用者所設計，但它也為「課程模組」和「協助」作者提供顯著的優點，包括能夠新增內容、修正錯誤、以多種 UI 文化特性提供，以及回應使用者意見和要求，只要模組已出貨。 本主題說明如何封裝和上傳說明檔，讓使用者可以使用[update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 來下載並安裝這些檔案。

下列步驟提供支援「可更新的說明」之程式的總覽。

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>步驟1：尋找您的說明檔案的網際網路網站

建立「可更新的說明」的第一個步驟是尋找模組的說明檔案的網際網路位置。 實際上，您可以使用兩個不同的位置。 您可以將模組的說明資訊檔案（如下所述的 HelpInfo XML）保留在一個網際網路位置，並將說明內容封包檔保存在另一個網際網路位置。 模組的所有說明內容 CAB 檔案都必須位於相同的位置。 您可以將不同模組的說明內容 CAB 檔案放在相同的位置。

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>步驟2：將 HelpInfoURI 索引鍵新增至您的模組資訊清單

在模組資訊清單中新增**HelpInfoURI**鍵。 索引鍵的值是模組之 HelpInfo XML 資訊檔案位置的統一資源識別元（URI）。 針對安全性，位址必須以 "HTTP" 或 "HTTPs" 開頭。 URI 應該指定網際網路位置，但不能包含 HelpInfo XML 檔案名。

例如：

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>步驟3：建立 HelpInfo XML 檔案

HelpInfo XML 資訊檔案包含您的說明檔的網際網路位置 URI，以及模組中每個支援的 UI 文化特性的最新說明檔案版本號碼。 每個 Windows PowerShell 模組都有一個 HelpInfo XML 檔案。 當您更新說明檔時，可以編輯或取代 HelpInfo XML 檔案;您不會再新增另一個。 如需詳細資訊，請參閱 how [To Create a HELPINFO XML File](./how-to-create-a-helpinfo-xml-file.md)。

### <a name="step-4-sign-your-help-files"></a>步驟4：簽署您的說明檔

數位簽章不是必要的，但在您每次共用檔案時都是最佳作法建議。

### <a name="step-5-create-cab-files"></a>步驟5：建立 CAB 檔案

使用可建立封包（.cab）檔案（例如 Makecab.exe）的工具來建立。CAB 檔案，其中包含模組的說明檔。 針對每個支援的 UI 文化特性中的說明檔，建立個別的 CAB 檔案。 如需詳細資訊，請參閱[如何準備可更新的說明 CAB](./how-to-prepare-updatable-help-cab-files.md)檔案。

### <a name="step-6-upload-your-files"></a>步驟6：上傳您的檔案

若要發佈新的或已更新的說明檔案，請將 CAB 檔案上傳到 HelpInfo XML 檔案中**HelpContentUri**元素所指定的網際網路位置。 然後，將 HelpInfo XML 檔案上傳至模組資訊清單中**HelpInfoUri**機碼的值所指定的網際網路位置。
