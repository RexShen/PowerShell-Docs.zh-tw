---
title: 如何更新說明檔 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367137"
---
# <a name="how-to-update-help-files"></a>如何更新說明檔

本主題說明如何更新支援「可更新的說明」之模組的說明檔。

## <a name="updating-help-files"></a>更新說明檔

更新說明檔的原因有很多，例如更正錯誤、闡明概念、回答常見問題、新增檔案，或加入新的更好的範例。

若要更新說明檔：

1. 變更檔案。

2. 將檔案轉譯為其他 UI 文化特性。

3. 針對每個 UI 文化特性中的模組，收集所有說明檔（新的、已變更和不變）。

4. 針對 XML 架構驗證檔案。

5. 重建每個 UI 文化特性的 CAB 檔案。

6. 在 HelpInfo XML 檔案中，將每個 UI 文化特性的 CAB 檔案版本號碼遞增。

7. 將新的 CAB 檔案上傳到 HelpInfo XML 檔案中**HelpContentUri**元素的值所指定的位置。 以新的 CAB 檔案取代舊版的封包檔。

8. 將更新的 HelpInfo XML 檔案上傳至模組資訊清單中的**HelpInfoUri**索引鍵所指定的位置。 以新的檔案取代舊版的 HelpInfo XML 檔案。