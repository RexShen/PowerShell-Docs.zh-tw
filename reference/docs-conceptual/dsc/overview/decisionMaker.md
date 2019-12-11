---
ms.date: 10/11/2019
keywords: dsc,powershell,設定,安裝
title: 適合決策者的預期狀態設定概觀
ms.openlocfilehash: 271ec04035feb17e932acd0ac80f32213a4e018b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352126"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>適用於決策者的預期狀態設定概觀

此文件說明使用 PowerShell 預期狀態設定 (DSC) 的商業優勢，它不是技術指南。

## <a name="what-is-dsc"></a>什麼是 DSC？

PowerShell DSC 是 Windows 內建的開放式標準組態管理平台。 DSC 的彈性足以因應部署生命週期 (開發、測試、生產階段前、生產環境) 各階段穩定且一致的運作，相應放大時亦然。

DSC 的中心概念是[設定](../configurations/configurations.md)。 設定是 PowerShell 指令碼，描述由特定特性的電腦 (或稱「節點」) 組成的環境。 這些特性可以簡單到像是確保已啟用特定的 Windows 功能，也可以複雜到像是部署 SharePoint。

DSC 內建監視和報告功能。 如果系統不再相容，DSC 會引發警示，採取動作更正系統。

## <a name="benefits-of-using-dsc"></a>使用 DSC 的優點

設定的設計可簡化讀取、儲存及更新設定的方式。 設定會宣告目標裝置的狀態，不需要撰寫如何讓裝置進入該狀態的指示。 這些因素可降低透過 DSC 學習、採用及維護設定的成本。

建立設定即表示，已在單一位置將複雜的部署步驟擷取為**單一事實來源**。 設定讓特定電腦集合的重複部署更不容易出錯。 此外，部署更快速且更可靠，藉此縮短複雜部署的完成時間。

設定也可以透過 [PowerShell 資源庫](https://powershellgallery.com)共用。 您需要完成的工作可能已有常見案例和最佳做法。

## <a name="dsc-and-devops"></a>DSC 與 DevOps

DSC 在設計時即已考慮到 [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) \(英文\)。 它是人員、程序與工具的組合，可允許快速部署與反覆開發週期，為內部或外部的終端使用者創造價值。 定義環境的單一設定表示開發人員可以將其需求編碼到設定中，並將該設定簽入原始檔控制。 作業小組接著可以部署程式碼，而不需要執行容易出錯的人工處理。

設定是[資料驅動](../configurations/configData.md)的。 已定義的資料可讓作業小組更容易識別及變更環境，而不必開發人員介入。

## <a name="dsc-on-premises-and-off-premises"></a>DSC 內部部署與外部部署

DSC 可管理內部部署及外部部署的部署。 針對內部部署解決方案，DSC 具有[提取伺服器](../pull-server/pullServer.md)，可用來集中管理電腦並回報其狀態。 針對外部部署雲端解決方案，DSC 可在 Windows 可用的地方使用。
Azure 提供以 DSC 為基礎建置的特定供應項目，例如 [Azure 自動化](https://azure.microsoft.com/en-us/documentation/services/automation/)，這可讓您集中管理 DSC 回報功能。

## <a name="dsc-and-compatibility"></a>DSC 和相容性

DSC 是在 Windows Server 2012 R2 引進，卻是透過 Windows Management Framework (WMF) 供較低的作業系統使用。 如需有關 WMF 的詳細資訊，請參閱 [Windows Management Framework](/powershell/scripting/wmf/overview) 套件。

DSC 也可以用來管理 Linux。 如需詳細資訊，請參閱[開始使用 DSC for Linux](../getting-started/lnxGettingStarted.md)。
