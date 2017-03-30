---
title: "Windows PowerShell 預期狀態設定概觀"
ms.date: 2016-05-16
keywords: "PowerShell，DSC"
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: d215289675ee9c2b7121fa3d785549c48733d2e8
ms.sourcegitcommit: 910f090edd401870fe137553c3db00d562024a4c
translationtype: HT
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell 預期狀態設定概觀 

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

DSC 是 PowerShell 中的管理平台，可讓您以程式碼形式的設定來管理 IT 和開發基礎結構。

- 如需使用 DSC 的商務優點概觀，請參閱[適合決策者的預期狀態設定概觀](decisionMaker.md)。
- 如需使用 DSC 的工程優點概觀，請參閱[適合工程師的預期狀態設定概觀]DscForEngineers.md)。
- 若要快速開始使用 DSC，請參閱 [DSC 快速入門]quickStart.md。

## <a name="key-concepts"></a>重要概念

DSC 是用於設定、部署和管理系統的宣告式平台。 它包含三個主要元件：

- [設定](configurations.md) 是宣告式 PowerShell 指令碼，會定義和設定資源的執行個體。
    在執行設定時，DSC (及設定所呼叫的資源) 將只會「保持原狀」，確保系統存在於設定所配置的狀態。 
    DSC 設定也是等冪：本機設定管理員 (LCM) 仍可確定電腦依據設定中宣告的任何狀態所設定。
- 資源是 DSC「實現目標狀態」的方式。 它們包含的程式碼可使設定的目標進入並保持在指定狀態。 
    資源位於 PowerShell 模組，且可以被撰寫以針對檔案或 Windows 處理序等一般項目建立模型，或是針對 IIS 伺服器或 Azure 中執行的 VM 等特定項目建立模型。
- 本機設定管理員 (LCM) 是 DSC 用於協助資源和設定之間互動的引擎。 
    LCM 使用資源所實作的控制流程，定期輪詢系統，以確保能維持設定所定義的狀態。 
    如果系統未符合狀態，LCM 會呼叫資源內的程式碼，以根據設定來「實現目標狀態」。 

## <a name="see-also"></a>另請參閱

- [DSC 設定](configurations.md)
- [DSC 資源](resources.md)
- [設定本機設定管理員](metaConfig.md)

