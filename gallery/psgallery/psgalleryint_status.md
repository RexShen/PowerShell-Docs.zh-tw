---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a>PowerShell 資源庫狀態
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>2017 年 3 月 27 日 - 已解決：無法看到個別模組和指令碼頁面

__影響摘要__：https://www.powershellgallery.com 上個別模組和指令碼頁面的直接連結已中斷。 所有區域均回報此問題。 這並未影響任何 PowerShellGet Cmdlet，亦即 Install-Module、Install-Script、Update-Module、Update-Script、Publish-Module、Publish-Script 仍繼續運作。

__根本原因__：工程師確認原因出自將社交媒體按鈕 (例如 Facebook) 引入到頁面上。  

__解決方法__：工程師停用了 Facebook 計數資訊，以修正此問題。

__後續步驟__：我們開啟了內部追蹤問題，以修正我們的 Facebook API 使用方式。

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>12/15/2016 - 無法透過 PowerShellGallery 網站傳送電子郵件

__影響的摘要__：在 12/13/2016 和 12/15/2016 之間，PowerShell 資源庫系統管理員未收到透過「連絡擁有者」、「管理擁有者」、「連絡支援人員」或「檢舉不當使用」傳送的任何訊息。  
__根本原因__︰工程師找出其肇因為 SMTP 伺服器的驗證問題。  
__解決方法__︰工程師能夠解決驗證問題並還原 SMTP 伺服器連線。  
__後續步驟__︰如果您在這段期間使用連絡「擁有者」、「管理擁有者」、「連絡支援人員」或「檢舉不當使用」連結來傳送郵件給 cgadmin@microsoft.com，而我們沒有回應，請再試一次。 造成您的不便，我們深感抱歉。   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>2016/8/10 - 已解決︰無法傳送電子郵件給 cgadmin@microsoft.com
__影響摘要__：2016 年 8 月5 日到 2016 年 8 月 10 日之間，客戶無法傳送電子郵件給 cgadmin@microsoft.com，也無法使用「與我們連絡」功能。  
__根本原因__︰工程師確認原因出自電子郵件帳戶的設定變更。  
__解決方法__︰工程師已找出解決此設定問題的方法。  
__後續步驟__︰若您曾在這段期間使用 [與我們連絡] 連結，或傳送郵件給 cgadmin@microsoft.com，但我們未回應，請再試一次。 感謝您的耐心配合。


