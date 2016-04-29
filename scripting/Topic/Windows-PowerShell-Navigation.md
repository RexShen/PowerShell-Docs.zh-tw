---
title: Windows PowerShell 瀏覽
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 846f5233-43be-496a-9ca1-e3e34207cb49
---
# Windows PowerShell 瀏覽
資料夾是「檔案總管 」介面、Cmd.exe 與 UNIX 工具 (例如 BASH) 中常見的組合管理功能。 資料夾 (或其更常見的名稱「目錄」) 是用來針對檔案與其他目錄進行組合管理的實用概念。 UNIX 系列作業系統延伸了此概念，這些作業系統將每樣東西都視為檔案；特定硬體與網路連線會顯示為特定資料夾中的檔案。 此方法不會確保內容可由特定應用程式讀取或使用，但會使得尋找特定項目的程序更簡單。 可列舉或搜尋檔案與資料夾的工具也可以搭配這些裝置使用。 您也可以使用代表項目的檔案路徑來找到該特定項目。

類似地，Windows PowerShell 基礎結構支援以 Windows PowerShell 磁碟機方式公開可瀏覽的所有項目，就像標準 Microsoft Windows 磁碟機或 UNIX 檔案系統一樣。 Windows PowerShell 磁碟機不一定代表實際磁碟機，不論是本機或網路磁碟機。 本章主要討論檔案系統的瀏覽，但概念適用於與檔案系統無關聯的 Windows PowerShell 磁碟機。



<!--HONumber=Apr16_HO1-->


