---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,設定,安裝
title: 適用於 Linux 的內建預期狀態設定資源
ms.openlocfilehash: 77617b72584f39c46fc4b9eb67235378bbfc19aa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>適用於 Linux 的內建預期狀態設定資源

資源是可讓您撰寫 PowerShell 預期狀態設定 (DSC) 指令碼的建置組塊。 DSC for Linux 隨附一組內建功能，可用於設定資源，例如檔案和資料夾、套件、環境變數，以及服務和處理序。

## <a name="built-in-resources"></a>內建資源

下表提供這些資源和主題詳細資訊的連結清單。

* [nxArchive 資源 ](lnxArchiveResource.md) ─ 提供一個機制，將封存 (.tar、.zip) 檔案解壓縮在特定路徑。
* [nxEnvironment 資源 ](lnxEnvironmentResource.md) ─ 管理目標節點上的環境變數。
* [nxFile 資源 ](lnxFileResource.md) ─ 管理 Linux 檔案和目錄。
* [nxFileLine 資源 ](lnxFileLineResource.md) ─ 管理 Linux 檔案中的個別程式碼行。
* [nxGroup 資源 ](lnxGroupResource.md) ─ 管理本機 Linux 群組。
* [nxPackage 資源](lnxPackageResource.md)--管理 Linux 節點上的套件。
* [nxScript 資源](lnxScriptResource.md)--在目標節點上執行指令碼。
* [nxService 資源 ](lnxServiceResource.md) ─ 管理 Linux 服務 (精靈)。
* [nxSshAuthorizedKeys 資 源](lnxSshAuthorizedKeysResource.md) ─ 管理 Linux 使用者的公用 SSH 金鑰。
* [nxUser 資源 ](lnxUserResource.md) ─ 管理本機 Linux 使用者。