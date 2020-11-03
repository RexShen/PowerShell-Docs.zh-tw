---
description: PackageManagement 是軟體套件管理員的匯總工具。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 22f0bd5a114866e9785fdaeafd91d9470fef38c8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206687"
---
# <a name="about-packagemanagement"></a>關於 PackageManagement

## <a name="short-description"></a>簡短描述
PackageManagement 是軟體套件管理員的匯總工具。

## <a name="long-description"></a>詳細描述

PackageManagement 功能已在 Windows PowerShell 5.0 中引進。

PackageManagement 是軟體套件管理系統的整合介面;您可以執行 PackageManagement Cmdlet 來執行軟體探索、安裝和清查 (SDII) 工作。 無論基礎安裝技術為何，您都可以在 PackageManagement 模組中執行通用 Cmdlet 來搜尋、安裝或卸載套件。新增、移除和查詢套件存放庫;並在電腦上執行查詢，以判斷安裝了哪些軟體套件。

PackageManagement 支援彈性的外掛程式模型，可支援其他軟體套件管理系統。

PackageManagement 模組隨附于 Windows PowerShell 5.0 和更新版本的 PowerShell，並可在封裝管理結構的三個層級上運作：套件提供者、套件來源和套件本身。 讓我們定義一些詞彙：

- 封裝管理員：軟體套件管理系統。 在 PackageManagement 方面，這是封裝提供者。
- 封裝提供者：適用于封裝管理員的 PackageManagement 詞彙。 範例可以包括 Windows Installer、Chocolatey 和其他專案。
- 套件來源：您設定套件提供者作為存放庫使用的 URL、本機資料夾或網路共用資料夾。
- 封裝：套件提供者所管理的軟體，並儲存在特定套件來源中。

PackageManagement 模組包含下列 Cmdlet。 如需詳細資訊，請參閱 [PackageManagement](/powershell/module/packagemanagement) 說明。

- `Get-PackageProvider`：傳回連接至 PackageManagement 的封裝提供者清單。
- `Get-PackageSource`：取得為封裝提供者註冊的封裝來源清單。
- `Register-PackageSource`：加入指定封裝提供者的封裝來源。
- `Set-PackageSource`：設定現有封裝來源的屬性。
- `Unregister-PackageSource`：移除已註冊的套件來源。
- `Get-Package`：傳回已安裝之軟體套件的清單。
- `Find-Package`：尋找可用套件來源中的軟體套件。
- `Install-Package`：安裝一或多個軟體套件。
- `Save-Package`：將封裝儲存至本機電腦，而不進行安裝。
- `Uninstall-Package`：卸載一或多個軟體套件。

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a>套件提供者啟動載入和動態 Cmdlet 參數

根據預設，PackageManagement 會隨附核心啟動提供者。 您可以藉由啟動提供者，以依需要安裝其他套件提供者;也就是，回應從 web 服務自動安裝提供者的提示。 您可以使用任何 PackageManagement Cmdlet 指定封裝提供者;如果指定的提供者無法使用，PackageManagement 會提示您啟動 (，或自動安裝) 提供者。 在下列範例中，如果尚未安裝 Chocolatey 提供者，PackageManagement 啟動程式會安裝提供者。

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

如果尚未安裝 Chocolatey 提供者，當您執行上述命令時，系統會提示您安裝它。

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

如果尚未安裝 Chocolatey 提供者，則當您執行上述命令時，會安裝提供者;但因為 ForceBootstrap 參數已新增至命令，所以系統不會提示您安裝它。提供者和套件都會自動安裝。

當您嘗試安裝套件時，如果尚未安裝支援提供者，而且您沒有將 ForceBootstrap 參數新增至命令，PackageManagement 會提示您安裝該提供者。

在 PackageManagement 命令中指定封裝提供者可以讓特定的動態參數提供給該封裝提供者使用。 當您針對特定 PackageManagement Cmdlet 執行 Get-Help 時，會傳回參數集清單，並將可用封裝提供者的動態參數群組在不同的參數集中。

PackageManagement 專案的詳細資訊

如需 PackageManagement open 開發專案的詳細資訊，包括如何建立 PackageManagement 套件提供者，請參閱 GitHub 上的 PackageManagement 專案 https://oneget.org 。

## <a name="see-also"></a>另請參閱

[Get-PackageProvider](xref:PackageManagement.Get-PackageProvider)

[Get-PackageSource](xref:PackageManagement.Get-PackageSource)

[Register-PackageSource](xref:PackageManagement.Register-PackageSource)

[Set-PackageSource](xref:PackageManagement.Set-PackageSource)

[Unregister-PackageSource](xref:PackageManagement.Unregister-PackageSource)

[Get-Package](xref:PackageManagement.Get-Package)

[Find-Package](xref:PackageManagement.Find-Package)

[Install-Package](xref:PackageManagement.Install-Package)

[Save-Package](xref:PackageManagement.Save-Package)

[Uninstall-Package](xref:PackageManagement.Uninstall-Package)
