---
title: 如何可更新說明運作方式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082252"
---
# <a name="how-updatable-help-works"></a>可更新的說明如何運作

本主題說明可更新的說明處理序 HelpInfo XML 檔案，並在封包檔的每個模組，並安裝更新的使用者說明的方式。

## <a name="the-update-help-process"></a>Update-help 程序

下列清單描述的動作[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet，當使用者執行更新特定的 UI 文化特性中的模組的說明檔案的命令。

1. `Update-Help` 取得遠端 HelpInfo XML 檔案中的值所指定的位置**HelpInfoURI**模組資訊清單中索引鍵，並驗證針對結構描述檔案。 (若要檢視結構描述，請參閱[HelpInfo XML 結構描述](./helpinfo-xml-schema.md)。)然後`Update-Help`會尋找在模組目錄中模組的本機 HelpInfo XML 檔案在使用者電腦上。

2. `Update-Help` 比較指定模組的遠端和本機 HelpInfo XML 檔案中的 UI 文化特性的說明檔案的版本號碼。 如果對遠端檔案的版本號碼大於版本號碼，在本機檔案，或如果有任何本機的 HelpInfo XML 檔案，對於模組，`Update-Help`準備要下載新的說明檔。

3. `Update-Help` 選取模組的 CAB 檔案從所指定的位置**HelpContentUri**遠端 HelpInfo XML 檔案中的項目。 它會使用模組名稱、 GUID、 模組和 UI 文化特性，來識別封包檔。

4. `Update-Help` 下載的 CAB 檔案、 將它解壓縮、 驗證的說明內容檔案，並說明內容會將檔案儲存在模組目錄的特定語言子目錄中使用者的電腦上。

5. `Update-Help` 建立本機 HelpInfo XML 檔案，複製 遠端 HelpInfo XML 檔案。 它會編輯本機 HelpInfo XML 檔案，使其包含所安裝的 CAB 檔案的元素。 然後它會將本機 HelpInfo XML 檔案儲存在模組目錄，並結束更新。

## <a name="the-save-help-process"></a>Save-help 程序

下列清單描述的動作[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help)並[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet，當使用者執行命令來更新說明檔中的檔案共用，然後使用這些檔案上更新說明檔使用者的電腦。

`Save-Help` Cmdlet 會執行下列動作以回應至命令，以將模組的說明檔案儲存在所指定的檔案共用**DestinationPath**參數。

1. `Save-Help` 取得遠端 HelpInfo XML 檔案中的值所指定的位置**HelpInfoURI**模組資訊清單中索引鍵，並驗證針對結構描述檔案。 (若要檢視結構描述，請參閱[HelpInfo XML 結構描述](./helpinfo-xml-schema.md)。)然後`Save-Help`本機 HelpInfo XML 檔案所指定的目錄中尋找**DestinationPath**中的參數`Save-Help`命令。

2. `Save-Help` 比較指定模組的遠端和本機 HelpInfo XML 檔案中的 UI 文化特性的說明檔案的版本號碼。 如果對遠端檔案的版本號碼大於版本號碼，在本機檔案，或如果已在模組沒有本機 HelpInfo XML 檔案**DestinationPath**目錄中，`Save-Help`準備要下載新的說明檔。

3. `Save-Help` 選取模組的 CAB 檔案從所指定的位置**HelpContentUri**遠端 HelpInfo XML 檔案中的項目。 它會使用模組名稱、 GUID、 模組和 UI 文化特性，來識別封包檔。

4. `Save-Help` 下載封包檔，並儲存在**DestinationPath**目錄。 （它不會建立任何語言特定子目錄。）

5. `Save-Help` 建立本機 HelpInfo XML 檔案，複製 遠端 HelpInfo XML 檔案。 它會編輯本機 HelpInfo XML 檔案，使其包含它所儲存的 CAB 檔案的元素。 然後它會將儲存在本機的 HelpInfo XML 檔案**DestinationPath**目錄，並於結尾的更新。

   `Update-Help` Cmdlet 會執行下列動作以回應更新說明檔中所指定的檔案共用的檔案從使用者的電腦上的命令**SourcePath**參數。

1. `Update-Help` 取得遠端 HelpInfo XML 檔案從**SourcePath**目錄。 然後它會尋找本機 HelpInfo XML 檔案，在模組目錄中使用者的電腦上。

2. `Update-Help` 比較指定模組的遠端和本機 HelpInfo XML 檔案中的 UI 文化特性的說明檔案的版本號碼。 如果對遠端檔案的版本號碼大於版本號碼，在本機檔案，或如果有任何本機 HelpInfo XML 檔案，`Update-Help`準備要安裝新的說明檔。

3. `Update-Help` 選取 從模組的 CAB 檔案**SourcePath**目錄。 它會使用模組名稱、 GUID、 模組和 UI 文化特性，來識別封包檔。

4. `Update-Help` 解壓縮 CAB 檔案、 驗證的說明內容檔案，並說明內容會將檔案儲存在模組目錄的特定語言子目錄中使用者的電腦上。

5. `Update-Help` 建立本機 HelpInfo XML 檔案，複製 遠端 HelpInfo XML 檔案。 它會編輯本機 HelpInfo XML 檔案，使其包含所安裝的 CAB 檔案的元素。 然後它會將本機 HelpInfo XML 檔案儲存在模組目錄，並結束更新。