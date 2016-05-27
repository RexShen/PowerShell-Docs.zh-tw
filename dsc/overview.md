---
title:   Windows PowerShell 預期狀態設定概觀 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Windows PowerShell 預期狀態設定概觀 

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

本主題說明在 Windows PowerShell 中的 Windows PowerShell 預期狀態設定 (DSC) 功能。 您可以使用本主題，以取得 DSC 的概觀，並尋找您需要了解和使用 DSC 的文件資源。

## 功能說明
DSC 是 Windows PowerShell 中的新管理平台，可讓您部署和管理軟體服務的設定資料及管理這些服務執行的環境。

DSC 提供一組 Windows PowerShell 語言擴充功能、新的 Windows PowerShell Cmdlet，與您可以用來以宣告方式指定如何設定軟體環境的資源。 它也提供方法來維護和管理現有的設定。

## 實際應用
以下是一些範例案例，其中您可以用自動化方式，使用內建 DSC 資源來設定及管理一組電腦 (也稱為目標節點)：

* 啟用或停用伺服器角色與功能
* 管理登錄設定
* 管理檔案和目錄
* 啟動、停止和管理程序與服務
* 管理群組和使用者帳戶
* 部署新的軟體
* 管理環境變數
* 執行 Windows PowerShell 指令碼
* 修正偏離預期狀態的設定
* 探索指定節點上的實際設定狀態

## 重要概念
DSC 是用於設定、部署和管理系統的宣告式平台。 它包含三個主要元件：

* [設定](configurations.md) 是宣告式 PowerShell 指令碼，會定義和設定資源的執行個體。 在執行設定時，DSC (及設定所呼叫的資源) 將只會「保持原狀」，確保系統存在於設定所配置的狀態。 DSC 設定也是等冪：本機設定管理員 (LCM) 仍可確定電腦依據設定中宣告的任何狀態所設定。
* 資源是被寫入的 DSC 命令式建置組塊，用以建立子系統的各種元件模型，並實作其變更狀態的控制流程。 它們位於 PowerShell 模組，且可以被寫入，將如同檔案或 Windows 處理序一樣普遍的某些項目建立模型，或將如同 IIS 伺服器或 Azure 中執行的 VM 一樣特定的項目建立模型。
* 本機設定管理員 (LCM) 是 DSC 用於協助資源和設定之間互動的引擎。 LCM 使用資源所實作的控制流程，定期輪詢系統，以確保設定所配置的狀態能保留。 如果系統未符合狀態，LCM 會使用資源內的更多邏輯，根據設定宣告來「保持原狀」。 

DSC 也包含一些新的語言關鍵字、Cmdlet 和工具，允許建立設定、協助建置 DSC 資源、叫用設定並管理 LCM。 許多這些 Cmdlet 位在屬於 Windows 8.1 的 PSDesiredStateConfiguration 模組中 (包括 `Start-DscConfiguration`、`Set-DscLocalConfigurationManager`和 `Get-DscResource`)。 xDscResourceDesigner (位於 [PowerShell 組件庫](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)) 是一組簡化 DSC 資源開發的 Cmdlet。

## 另請參閱
* [DSC 設定](configurations.md)
* [DSC 資源](resources.md)
* [設定本機設定管理員](metaConfig.md)



<!--HONumber=May16_HO3-->


