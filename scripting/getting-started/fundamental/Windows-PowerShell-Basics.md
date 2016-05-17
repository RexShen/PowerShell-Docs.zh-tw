---
title:  Windows PowerShell 基本概念
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  6b3cbbc8-060c-4877-b00b-7300dbbe4e28
---

# Windows PowerShell 基本概念
圖形化使用者介面使用大部分電腦使用者熟知的一些基本概念。 使用者會依賴對這些介面的熟悉度來完成工作。 作業系統會向使用者呈現可瀏覽項目的圖形化呈現，通常是使用下拉式功能表來存取特定功能，以及使用操作功能表來存取內容特定功能。

命令列介面 (CLI) (例如 Windows PowerShell) 必須使用不同的方式來公開資訊，因為它沒有可協助使用者的功能表或圖形化系統。 您需要先知道命令名稱，才能使用它們。 雖然您可以輸入相當於 GUI 環境中功能的複雜命令，但是您必須熟悉常用命令和命令參數。

大部分 CLI 沒有可協助使用者了解介面的模式。 因為 CLI 是第一個作業系統殼層，所以會任意選取多個命令名稱和參數名稱。 一般會選擇簡短命令名稱，而非完整命令名稱。 雖然說明系統和命令設計標準已整合為大部分 CLI，但是它們通常是設計成與最早的命令相容，因此數十年以前所做的決定仍然會形成命令集。

Windows PowerShell 是設計成利用使用者過往對 CLI 的了解。 在本章中，我們會討論一些可用來快速了解 Windows PowerShell 的基本工具和概念。 其中包括：

-   使用 Get-Command

-   使用 Cmd.exe 和 UNIX 命令

-   使用外部命令

-   使用 TAB 鍵自動完成

-   使用 Get-Help



<!--HONumber=May16_HO2-->


