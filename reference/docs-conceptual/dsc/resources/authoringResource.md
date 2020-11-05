---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: 建置自訂的 Windows PowerShell 預期狀態設定資源
description: 此文章提供開發資源的概觀，以及具有特定資訊與範例之文章的連結。
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656400"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>建置自訂的 Windows PowerShell 預期狀態設定資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 有內建資源，可用以設定您的環境。 此文章提供開發資源的概觀，以及具有特定資訊與範例之文章的連結。

## <a name="dsc-resource-components"></a>DSC 資源元件

DSC 資源是 Windows PowerShell 模組。 模組包含資源的結構描述 (可設定的屬性定義) 和實作 (真正執行設定所指定工作的程式碼)。 DSC 資源結構描述可以在 MOF 檔案中定義，並由指令碼模組執行實作。 從第 5 版的 PowerShell 類別支援開始，結構描述和實作都可以在類別中定義。 下列文章詳細說明如何建立 DSC 資源。

- [撰寫自訂的 DSC 資源與 MOF](authoringResourceMOF.md)
- [在 C# 中實作 DSC 資源](authoringResourceMofCS.md)
- [使用 PowerShell 類別撰寫自訂的 DSC 資源](authoringResourceClass.md)
- [複合資源：把 DSC 設定當做資源使用](authoringResourceComposite.md)
- [使用 [資源設計工具] 工具](authoringResourceMofDesigner.md)
