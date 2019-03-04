---
title: 可更新的說明撰寫：Step-by-Step | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860314"
---
# <a name="updatable-help-authoring-step-by-step"></a>可更新的說明撰寫：逐步

此文件列出的程序撰寫可更新說明的步驟。

## <a name="authoring-updatable-help-step-by-step"></a>撰寫可更新的說明：逐步

可更新的說明專為一般使用者，但它也提供重要的優點模組作者和說明的寫入器，包括能夠加入的內容，修正錯誤、 提供多個 UI 文化特性，並回應使用者註解和要求，長時間之後模組已出貨。 本主題說明如何封裝的位置，並上傳的說明檔案，讓使用者可以下載並安裝它們使用[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)並[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet。

下列步驟提供的支援更新說明的程序的概觀。

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>步驟 1：尋找說明檔中的網際網路網站

建立可更新的說明的第一個步驟是尋找模組的說明檔案的網際網路位置。 實際上，您可以使用兩個不同的位置。 您可以在一個網際網路位置和說明內容封包檔在另一個網際網路位置保留模組的說明資訊檔 (HelpInfo XML-如下所述)。 所有說明內容封包檔的模組必須位於相同的位置。 您可以將不同模組的說明內容封包檔放在相同的位置。

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>步驟 2：將 HelpInfoURI 金鑰新增至您的模組資訊清單

新增**HelpInfoURI**到您的模組資訊清單索引鍵。 索引鍵的值是位置的 HelpInfo XML 檔案資訊的模組統一資源識別元 (URI)。 為了安全性，位址必須以"http"或"https"開頭。 URI 應指定網際網路位置，但不是能包含 HelpInfo XML 檔案名稱。

例如：

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>步驟 3：建立 HelpInfo XML 檔案

HelpInfo XML 資訊檔案包含說明檔案，以及您在每個支援的 UI 文化特性中的模組最新說明檔案的版本號碼的網際網路位置的 URI。 每個 Windows PowerShell 模組具有一個 HelpInfo XML 檔案。 當您更新說明檔案時，編輯或取代 HelpInfo XML 檔案;您沒有加入另一個。 如需詳細資訊，請參閱 <<c0> [ 如何建立 HelpInfo XML 檔案](./how-to-create-a-helpinfo-xml-file.md)。

### <a name="step-4-sign-your-help-files"></a>步驟 4：登入您的說明檔

數位簽章是不必要的但它們是最佳做法建議，每當您共用檔案。

### <a name="step-5-create-cab-files"></a>步驟 5：建立 CAB 檔案

使用會建立封包 (.cab) 檔案，例如 MakeCab.exe，若要建立的工具。包含您的模組的說明檔案的封包檔。 在每個支援的 UI 文化特性說明檔案的個別封包檔。 如需詳細資訊，請參閱 <<c0> [ 如何準備可更新的說明封包檔](./how-to-prepare-updatable-help-cab-files.md)。

### <a name="step-6-upload-your-files"></a>步驟 6：將檔案上傳

若要發佈新的或更新的說明檔，將檔案上傳封包到所指定的網際網路位置**HelpContentUri** HelpInfo XML 檔案中的項目。 然後，將 HelpInfo XML 檔案上傳至的值所指定的網際網路位置**HelpInfoUri**模組資訊清單中的索引鍵。
