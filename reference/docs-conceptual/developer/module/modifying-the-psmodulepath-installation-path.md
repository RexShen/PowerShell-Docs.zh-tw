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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360667"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>修改 PSModulePath 安裝路徑

@No__t-0 環境變數會儲存安裝在磁片上之模組位置的路徑。 當使用者未指定模組的完整路徑時，Windows PowerShell 會使用此變數來尋找模組。 此變數中的路徑會依照其出現的順序進行搜尋。

當 Windows PowerShell 啟動時，`PSModulePath` 會建立為具有下列預設值的系統內容變數： `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`。

## <a name="to-view-the-psmodulepath-variable"></a>若要查看 PSModulePath 變數

若要查看在 `PSModulePath` 變數中指定的路徑，請輸入下列命令：

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>若要將位置新增至 PSModulePath 變數

若要將路徑新增至此變數，請使用下列其中一種方法：

- 若要新增僅適用于目前會話的暫時值，請在命令列中執行下列命令：

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- 若要新增每次開啟會話時可用的持續性值，請將下列命令新增至 Windows PowerShell 設定檔：

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  如需設定檔的詳細資訊，請參閱 Microsoft TechNet library 中的[about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) 。

- 若要將持續變數新增至登錄，請使用 [**系統屬性**] 對話方塊中的 [環境變數編輯器]，建立名為 `PSModulePath` 的新使用者環境變數。

- 若要使用腳本新增持續性變數，請在環境類別上使用**SetEnvironmentVariable**方法。 例如，下列腳本會將 "C:\Program Files\Fabrikam\Module path 新增至電腦的 PSModulePath 環境變數值。 若要將路徑新增至使用者 PSModulePath 環境變數，請將目標設定為 "User"。

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>若要從 PSModulePath 中移除位置

您可以使用類似的方法來移除變數中的路徑：例如，`$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` 會從目前的會話移除**c:\ModulePath**路徑。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
