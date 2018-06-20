---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 建置自訂的 Windows PowerShell 預期狀態設定資源
ms.openlocfilehash: f1ac626c5ef18b7ed14f3754ab39139db2a2a2d7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222365"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>建置自訂的 Windows PowerShell 預期狀態設定資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 有內建資源，可用以設定您的環境。 (如需詳細資訊，請參閱[內建的 Windows PowerShell 預期狀態設定資源](builtInResource.md)。)本主題提供開發資源概述以及特定資訊和範例的主題連結。

## <a name="dsc-resource-components"></a>DSC 資源元件

DSC 資源是 Windows PowerShell 模組。 模組包含資源的結構描述 (可設定的屬性定義) 和實作 (真正執行設定所指定工作的程式碼)。 DSC 資源結構描述可以在 MOF 檔案中定義，並由指令碼模組執行實作。 從第 5 版的 PowerShell 類別支援開始，結構描述和實作都可以在類別中定義。 下列主題會詳細說明如何建立 DSC 資源。

* [撰寫自訂的 DSC 資源與 MOF](authoringResourceMOF.md)
* [在 C# 中實作 DSC 資源](authoringResourceMofCS.md)
* [使用 PowerShell 類別撰寫自訂的 DSC 資源](authoringResourceClass.md)
* [複合資源：把 DSC 設定當做資源使用](authoringResourceComposite.md)
* [使用 [資源設計工具] 工具](authoringResourceMofDesigner.md)