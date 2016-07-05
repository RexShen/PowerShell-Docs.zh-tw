---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "讀我檔案"
ms.technology: powershell
ms.sourcegitcommit: 47593773fb0f34e0b52d35617522d7b1db7f48e6
ms.openlocfilehash: 1cecf1b6bf5a55ed785c8ff43bdd4a0a41e96cd0

---

# Just Enough Administration
Just Enough Administration (JEA) 是安全性技術，允許將可透過 PowerShell 管理的任何項目委派管理。
使用 JEA，您可以︰
- 利用虛擬帳戶，代表一般使用者執行特殊權限動作，以**減少電腦上的系統管理員數目**。
- 指定使用者可以執行的 Cmdlet、函式和外部命令，以**限制使用者可以執行的工作**。
- 透過 "Over The Shoulder" 文字記錄，顯示使用者在工作階段期間實際執行的命令，以**深入了解使用者正在執行的工作**。

**為何重要？**  
假設在一般情況下，您的 DNS 伺服器會與 Active Directory 網域控制站共置。
您的 DNS 系統管理員必須具有本機系統管理員權限，才能修正 DNS 伺服器的問題，但若要這樣做，您必須將其設為具有高度權限之 "Domain Admins" 安全性群組的成員。
這個方法能有效地讓 DNS 系統管理員控制您的整個網域，並存取該電腦上的所有資源。

有了 JEA，您就可以設定 DNS 系統管理員的角色，並讓他們只存取完成其工作所需的所有命令。
這表示您可以提供適當的存取權以修復有害的 DNS 快取，卻不會無意中給予他們使用 Active Directory、瀏覽檔案、或執行有潛在危險指令碼的權限。
更棒的是，當 JEA 工作階段設定為使用一次性特殊權限虛擬帳戶時，您的 DNS 系統管理員就可以在使用*非特殊權限*認證連線到伺服器的情況下，仍然能夠執行特殊權限命令。

## 可用性
JEA 是與 Windows Server 2016 同期開發的功能，舊版 Windows 可透過 Windows Management Framework 更新來使用這項功能。
目前的 JEA 版本適用於下列平台︰

**Windows Server**
- Windows Server 2016 Technical Preview 4 及更新版本
- 安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows Server 2012 R2、2012 和 2008 R2\*

**Windows 用戶端**
- 安裝的 11 月更新 (1511) 的 Windows 10
- 安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows 8.1、8 和 7\*

\* Windows Server 2008 R2 或 Windows 7 目前不提供 JEA 工作階段中的虛擬帳戶支援。


## 探索體驗指南
準備好了解如何撰寫、部署及使用您專屬的 JEA 端點了嗎？

本指南可讓您快速開始使用預先建置的 JEA 端點，以了解使用者體驗，然後逐步引導您從頭開始重新建立端點，以利示範工作階段設定和角色功能等概念。

1.  [簡介](introduction.md)   
簡短回顧您應該重視 JEA 的原因

2.  [必要條件](prerequisites.md)  
說明如何設定環境

3.  [使用 JEA](using-jea.md)  
協助您從了解使用 JEA 的操作員體驗開始

4.  [重現示範](remake-the-demo-endpoint.md)  
從頭開始建立 JEA 工作階段設定

5.  [角色功能](role-capabilities.md)  
了解如何使用角色功能檔案來自訂 JEA 功能

6.  [端對端 - Active Directory](end-to-end---active-directory.md)  
建立全新的端點以管理 Active Directory

7.  [多電腦部署和維護](multi-machine-deployment-and-maintenance.md)  
探索部署和編寫如何隨著規模調整而變更

8.  [JEA 上的報告](reporting-on-jea.md)  
探索如何對所有 JEA 動作和基礎結構進行稽核與報告

9.  附錄
  - [本指南所使用的重要概念](key-concepts-used-throughout-this-guide.md)  
  -  [建立網域控制站](creating-a-domain-controller.md)  
  -  [列入黑名單](on-blacklisting.md)  
  -  [限制命令時的考量](considerations-when-limiting-commands.md)  
  -  [常見的角色功能問題](common-role-capability-pitfalls.md)

## 開始撰寫您自己的 JEA 端點
撰寫 JEA 端點很容易，您只需要啟用 JEA 的系統和文字編輯器 (例如 PowerShell ISE)。
一個實用的入門秘訣是使用 `New-PSRoleCapabilityFile -Path <path>` 和 `New-PSSessionCapabilityFile -Path <Path>`但不提供任何其他引數來建立基本架構檔案。
這些基本架構檔案包含所有適用的設定欄位，以及說明每個欄位可能用途的實用註解。

若要更輕鬆地撰寫 JEA 端點，請參閱 [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx)，其提供可用來撰寫工作階段設定檔和角色功能檔案的 GUI。
甚至支援根據 PowerShell 記錄檔產生角色功能，讓您一開始就有使用者為完成工作所經常執行的命令。




<!--HONumber=Jun16_HO4-->


