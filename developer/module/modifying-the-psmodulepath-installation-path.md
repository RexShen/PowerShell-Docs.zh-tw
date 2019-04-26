---
title: 修改 PSModulePath 安裝路徑 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082204"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>修改 PSModulePath 安裝路徑

`PSModulePath`環境變數會儲存在磁碟上已安裝的模組位置的路徑。 Windows PowerShell 會在使用者未指定模組的完整路徑，請找出模組使用此變數。 此變數中的路徑會以其出現的順序進行搜尋。

Windows PowerShell 啟動時，`PSModulePath`會建立系統環境變數包含下列的預設值為： `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`。

## <a name="to-view-the-psmodulepath-variable"></a>若要檢視 PSModulePath 變數

若要檢視中所指定的路徑`PSModulePath`變數中，輸入下列命令：

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>若要將位置加入至 PSModulePath 變數

若要將路徑新增至這個變數，使用下列方法之一：

- 若要新增暫存值，可僅針對目前的工作階段，請在命令列執行下列命令：

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- 若要新增為可用，每當開啟工作階段時的永續性值，請在 Windows PowerShell 設定檔中新增下列命令：

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  如需有關設定檔的詳細資訊，請參閱 < [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) Microsoft TechNet library 中。

- 若要登錄中新增永續性的變數，建立新的使用者環境變數，呼叫`PSModulePath`使用中的環境變數編輯器**系統屬性**對話方塊。

- 若要使用指令碼中新增永續性的變數，請使用**SetEnvironmentVariable**環境類別上的方法。 例如，下列指令碼"C:\Program Files\Fabrikam\Module 將路徑加入至電腦的 PSModulePath 環境變數的值。 若要將路徑新增至使用者 PSModulePath 環境變數，將目標設定為 「 使用者 」。

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>若要移除 PSModulePath 位置

您可以移除變數使用類似的方法中的路徑： 例如，`$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"`將會移除**c:\ModulePath**目前工作階段的路徑。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
