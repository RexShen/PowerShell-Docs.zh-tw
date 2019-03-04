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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855524"
---
# <a name="how-to-update-help-files"></a>如何更新說明檔

本主題說明如何更新為支援 Updatable Help 的模組的說明檔。

## <a name="updating-help-files"></a>更新說明檔

有許多原因可更新說明檔，例如更正錯誤、 釐清概念、 回答常見問題集、 加入新的檔案，或加入新的和更好的範例。

若要更新的說明檔：

1. 變更的檔案。

2. 檔案轉譯為其他的 UI 文化特性。

3. 收集所有說明檔 （新增、 變更和未變更） 的每個 UI 文化特性中的模組。

4. 驗證 XML 結構描述檔案。

5. 重新建置各 UI 文化特性的封包檔。

6. 在 HelpInfo XML 檔案中，遞增版本號碼的每個 UI 文化特性的 CAB 檔案。

7. 新的 CAB 檔案上傳至的值所指定的位置**HelpContentUri** HelpInfo XML 檔案中的項目。 較舊的 CAB 檔案取代成新的封包檔。

8. 已更新的 HelpInfo XML 檔案上傳至所指定的位置**HelpInfoUri**模組資訊清單中的索引鍵。 使用新的檔案取代較舊的 HelpInfo XML 檔案。