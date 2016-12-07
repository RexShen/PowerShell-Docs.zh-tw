---
title: "DSC 資源"
ms.date: 2016-05-16
keywords: "PowerShell，DSC"
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 0a27a40b995393c41f0496a5f7fa3f56fbd865dd
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-resources"></a>DSC 資源

>適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

預期狀態設定 (DSC) 資源提供 DSC 設定的建置組塊。 資源會公開可以設定的屬性 (結構描述)，而且這些屬性包含本機設定管理員 (LCM) 稱之為「make it so (讓它變成這樣)」的 PowerShell 指令碼函式。

資源可以建立某些物件的模型，像檔案一樣平常或如 IIS 伺服器設定一樣專用。  類似資源的群組會併入 DSC 模組，將所有必要的檔案組織到可攜式結構中，而且包含中繼資料以識別資源的原訂用法。  

下列主題會說明 DSC 資源：

- [內建 DSC 資源](builtInResource.md)
- [建置自訂的 DSC 資源](authoringResource.md)
- [Linux 的內建 DSC 資源](lnxBuiltInResources.md)

