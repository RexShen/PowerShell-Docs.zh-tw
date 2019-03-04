---
title: 如何建立 HelpInfo XML 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853264"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>如何建立 HelpInfo XML 檔案

在本節中的此主題說明如何建立並填入說明資訊檔案，通常稱為 「 HelpInfo XML 檔案 」 的 Windows PowerShell 可更新說明的功能。

## <a name="helpinfo-xml-file-overview"></a>HelpInfo XML 檔案的概觀

HelpInfo XML 檔案是主要資訊來源可更新的說明模組。 它包含模組、 支援的 UI 文化特性和版本號碼可更新的說明用來判斷使用者是否有最新說明檔案的說明檔案的位置。

每個模組會有一個 HelpInfo XML 檔案，即使模組包含多重 UI 文化特性的多個說明檔。 模組作者建立 HelpInfo XML 檔案，並將它放在所指定的網際網路位置**HelpInfoUri**模組資訊清單中的索引鍵。 當模組的說明檔會更新，並上傳時，模組作者更新 HelpInfo XML 檔案，並以新版本取代原始的 HelpInfo XML 檔案。

請務必仔細維護的 HelpInfo XML 檔案。 如果您上傳新的檔案，但忘記要遞增版本號碼，可更新的說明不會下載新的檔案至使用者的電腦。 如果您加入新的 UI 文化特性的說明檔案，但不更新 HelpInfo XML 檔案或將它放在正確的位置，可更新的說明將不會下載新的檔案。

## <a name="in-this-section"></a>本節內容

本節包含下列主題。

- [HelpInfo XML 結構描述](./helpinfo-xml-schema.md)

- [HelpInfo XML 範例檔案](./helpinfo-xml-sample-file.md)

- [如何命名 HelpInfo XML 檔案](./how-to-name-a-helpinfo-xml-file.md)

- [如何設定 HelpInfo XML 版本號碼](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>另請參閱

[支援可更新的說明](./supporting-updatable-help.md)