---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "本指南所使用的重要概念"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 178fea44987b0c457b8e5d23fbe851ee12f03b31

---

# 本指南所使用的重要概念
**JEA 到底是什麼？**

JEA 是 PowerShell [限制端點](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx)的延伸模組，其新增了角色定義、虛擬帳戶及其他幾項增強功能，讓您更輕鬆地鎖定管理端點。
JEA 端點是由 PowerShell 工作階段設定檔以及一或多個角色功能檔案所組成。

**什麼是工作階段設定檔和角色功能檔案？**

PowerShell 工作階段設定檔 (.pssc) 定義*誰*可以連線到 PowerShell 端點，以及*如何*進行設定。
您可以在此將使用者和安全性群組對應到特定管理角色，並設定虛擬帳戶和文字記錄原則等全域設定。
工作階段設定檔是每部電腦專屬的檔案，可讓您視需要控制每部電腦的存取權。

PowerShell 角色功能檔案 (.psrc) 定義屬於某個角色的使用者能夠在系統上執行*什麼*工作。
您可以在此限制使用者可在其 JEA 工作階段中使用的 Cmdlet、函式、提供者和外部程式。
角色功能檔案通常沒有特定的服務角色 (DNS 管理、初級技術支援、唯讀清查稽核等)，並屬於 PowerShell 模組，因此可讓您輕鬆地在環境中與其他人共用。

**JEA 如何利用虛擬帳戶？**

在 PowerShell 工作階段設定檔中，您可以將 JEA 工作階段設定為使用虛擬「執行身分」帳戶。
虛擬帳戶是專為特定工作階段中的特定連線使用者所設計的一次性特殊權限帳戶，使用者的命令會在該內容中執行。
虛擬帳戶預設屬於本機 "Administrators" 安全性群組，但可以選擇性地設定為只屬於您指定的安全性群組。

**PowerShell 遠端**：PowerShell 遠端可讓您對遠端電腦執行 PowerShell 命令。
您可以對一或多部電腦執行，並使用暫時或持續連線。
在此示範中，您會使用互動式工作階段從遠端登入本機電腦。
JEA 會限制可透過 PowerShell 遠端使用的功能。
如需 PowerShell 遠端的詳細資訊，請執行 `Get-Help about_Remote`。

**"RunAs" 使用者**︰使用 JEA 時，非系統管理員會以特殊權限「虛擬帳戶」身分執行。
虛擬帳戶只會持續到遠端工作階段期間結束為止。
也就是說，它會在使用者連線到端點時建立，並在使用者結束工作階段時摧毀。
根據預設，虛擬帳戶是本機 Administrator 群組的成員。
在網域控制站上，它是 Domain Admins 的成員。
虛擬帳戶是帳戶建立所在電腦上的本機帳戶，沒有該電腦以外的權限。
這表示它們未登錄在 Active Directory 中 (未指派 RID)。
此外，如果允許的命令/指令碼嘗試存取本機電腦以外的資源，它會使用電腦身分識別 (而不是虛擬帳戶身分識別) 來存取這些資源。

**「已連線」的使用者**︰連線到 JEA 端點且已指派角色的非系統管理員使用者。
這位使用者執行的任何命令，都會在 RunAs 使用者或虛擬帳戶的內容下執行。




<!--HONumber=Jul16_HO1-->


