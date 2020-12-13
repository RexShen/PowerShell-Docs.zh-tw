---
ms.date: 08/28/2019
ms.topic: reference
title: 如何使用模組來匯入 Cmdlet
description: 如何使用模組來匯入 Cmdlet
ms.openlocfilehash: 485a4be4d2accaf050a6536e7f92a0673f62a30b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657289"
---
# <a name="how-to-import-cmdlets-using-modules"></a>如何使用模組來匯入 Cmdlet

本文說明如何使用二進位模組將 Cmdlet 匯入至 PowerShell 會話。

> [!NOTE]
> 模組的成員可以包含 Cmdlet、提供者、函式、變數、別名等等。 嵌入式管理單元只能包含 Cmdlet 和提供者。

## <a name="how-to-load-cmdlets-using-a-module"></a>如何使用模組載入 Cmdlet

1. 建立模組資料夾，其名稱與用來執行 Cmdlet 的元件檔相同。 在此程式中，模組資料夾會建立在 Windows `system32` 資料夾中。

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. 請確定 `PSModulePath` 環境變數包含新模組資料夾的路徑。 根據預設，系統資料夾已新增至 `PSModulePath` 環境變數。 若要查看 `PSModulePath` ，請輸入： `$env:PSModulePath` 。

1. 將 Cmdlet 元件複製到模組資料夾中。

1. 將模組資訊清單檔 (`.psd1`) 新增至模組的根資料夾。 PowerShell 會使用模組資訊清單來匯入您的模組。 如需詳細資訊，請參閱 [如何撰寫 PowerShell 模組資訊清單](../module/how-to-write-a-powershell-module-manifest.md)。

1. 執行下列命令以將 Cmdlet 新增至會話：

   `Import-Module [Module_Name]`

   此程式可用於測試您的 Cmdlet。 它會將元件中的所有 Cmdlet 新增至會話。 如需模組的詳細資訊，請參閱 [撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

## <a name="see-also"></a>請參閱

[如何撰寫 PowerShell 模組資訊清單](../module/how-to-write-a-powershell-module-manifest.md)

[匯入 PowerShell 模組](../module/importing-a-powershell-module.md)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[安裝模組](../module/installing-a-powershell-module.md)

[修改 PSModulePath 安裝路徑](../module/modifying-the-psmodulepath-installation-path.md)

[撰寫 Windows PowerShell Cmdlet](../cmdlet/cmdlet-overview.md)
