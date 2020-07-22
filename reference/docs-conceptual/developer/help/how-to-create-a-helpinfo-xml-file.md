---
title: 如何建立 HelpInfo XML 檔案
ms.date: 09/13/2016
ms.openlocfilehash: e395746e51309477bbcbff51b4591de3f73ce0db
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893300"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>如何建立 HelpInfo XML 檔案

本節中的主題說明如何建立和填入說明資訊檔案（通常稱為「HelpInfo XML 檔案」），以取得 PowerShell 可更新的說明功能。

## <a name="helpinfo-xml-file-overview"></a>HelpInfo XML 檔案總覽

HelpInfo XML 檔案是模組之可更新說明的主要資訊來源。 其中包含模組的說明檔位置、支援的 UI 文化特性，以及可更新的說明用來判斷使用者是否有最新說明檔案的版本號碼。

每個模組只有一個 HelpInfo XML 檔案，即使模組包含多個 UI 文化特性的多個說明檔案也一樣。 模組作者會建立 HelpInfo XML 檔案，並將它放在模組資訊清單中**HelpInfoUri**機碼所指定的網際網路位置。 當模組說明檔案更新並上傳時，模組作者會更新 HelpInfo XML 檔案，並以新版本取代原始 HelpInfo XML 檔案。

請務必小心維護 HelpInfo XML 檔案。 如果您上傳新檔案，但忘了遞增版本號碼，可更新的說明將不會將新的檔案下載到使用者的電腦。 如果您加入新 UI 文化特性的說明檔，但未更新 HelpInfo XML 檔案，或將它放在正確的位置，可更新的說明將不會下載新的檔案。

## <a name="in-this-section"></a>本節內容

本節包含下列主題。

- [HelpInfo XML 結構描述](./helpinfo-xml-schema.md)

- [HelpInfo XML 範例檔案](./helpinfo-xml-sample-file.md)

- [如何為 HelpInfo XML 檔案命名](./how-to-name-a-helpinfo-xml-file.md)

- [如何設定 HelpInfo XML 版本號碼](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>另請參閱

[支援可更新的說明](./supporting-updatable-help.md)
