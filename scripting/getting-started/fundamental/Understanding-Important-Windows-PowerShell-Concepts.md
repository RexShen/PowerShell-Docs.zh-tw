---
title:  了解 Windows PowerShell 重要概念
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  3e601e38-4520-4578-a48d-b6779f1d35ee
---

# 了解 Windows PowerShell 重要概念
Windows PowerShell 設計整合許多不同環境的概念。 具有特定殼層或程式設計環境經驗的人員會熟悉其中一些概念，但只有極少數的人員才知道所有這些概念。 查看其中一些概念，可提供有用的殼層概觀。

### 命令不是以文字為基礎
與傳統命令列介面命令不同，Windows PowerShell Cmdlet 設計成處理不只是畫面上所出現字串的物件結構化資訊。 命令輸出一律會攜帶您在需要時可使用的額外資訊。 我們將在本文件中深入討論此主題。

如果您過去已經使用文字處理工具來處理命令列資料，則嘗試在 Windows PowerShell 中使用它們時會發現它們的行為不同。 在大部分情況下，您不需要文字處理工具擷取特定資訊。 您可以使用標準 Windows PowerShell 物件操作命令來直接存取資料的各部分。

### 命令系列可進行擴充
Cmd.exe 這類介面未提供可讓您直接擴充內建命令集的方法。 您可以建立在 Cmd.exe 中執行的外部命令列工具，但這些外部工具沒有服務 (例如說明整合)，而且 Cmd.exe 不會自動得知它們是否為有效命令。

您所建立的 Cmdlet 以及使用嵌入式管理單元新增至 Windows PowerShell 的 Cmdlet，可以增強 Windows PowerShell 中的原生二進位命令 (稱為 *Cmdlet*，唸成 command-let)。 Windows PowerShell *嵌入式管理單元*會進行編譯，就像任何其他介面中的二進位工具一樣。 您可以使用它們將 Windows PowerShell 提供者新增至殼層，以及新的 Cmdlet。

基於 Windows PowerShell 內部命令的特殊本質，我們將其稱為 *Cmdlet*。

> [!NOTE]
> Windows PowerShell 可以執行 Cmdlet 以外的命令。 我們將不會在《Windows PowerShell 使用者手冊》中詳細討論它們，但它們對於了解命令類型類別十分有用。 Windows PowerShell 支援與 UNIX 殼層指令碼和 Cmd.exe 批次檔類似的指令碼，但副檔名是 .ps1。 Windows PowerShell 也可讓您建立可直接在介面或指令碼中使用的內部函式。

### Windows PowerShell 處理主控台輸入和顯示
當您輸入命令時，Windows PowerShell 一律會直接處理命令列輸入。 Windows PowerShell 也會格式化您在畫面上看到的輸出。 這十分重要，因為它會減少每個 Cmdlet 所需的工作，並確保您一律可以使用相同的方式來執行動作，而不管使用的 Cmdlet 為何。 如何簡化工具開發人員和使用者作業的其中一個範例是命令列說明。

傳統命令列工具有其專屬方法來要求和顯示說明。 部分命令列工具使用 **\/?** 來觸發說明顯示；其他則使用 **\-?**、**\/H** 甚至 **\/\/**。 有一部分會在 GUI 視窗中顯示說明，而不是在主控台顯示中。 有些複雜工具 (例如應用程式更新程式) 會先解壓縮內部檔案，再顯示其說明。 如果您使用錯誤的參數，則工具可能會忽略您輸入的內容，並開始自動執行工作。

當您在 Windows PowerShell 中輸入命令時，Windows PowerShell 會自動剖析並預先處理輸入的所有內容。 如果您使用 **-?** 參數與 Windows PowerShell Cmdlet，則一律表示「顯示此命令的說明」。 Cmdlet 開發人員不需要剖析命令，只需要提供說明文字。

請務必了解，即使在 Windows PowerShell 中執行傳統命令列工具，還是會提供 Windows PowerShell 的說明功能。 Windows PowerShell 會處理參數，並將結果傳遞給外部工具。

> [!NOTE]
> 如果您在 Windows PowerShell 中執行圖形應用程式，則會開啟應用程式的視窗。 只有在處理您提供的命令列輸入或傳回給主控台視窗的應用程式輸出時，Windows PowerShell 才會干擾，否則不會影響應用程式的內部運作方式。

### Windows PowerShell 使用某個 C# 語法
Windows PowerShell 的語法功能和關鍵字與 C# 程式設計語言中所使用的語法功能和關鍵字十分類似，因為 Windows PowerShell 是以 .NET Framework 為基礎。 如果您對 C# 語言感興趣，則學習 Windows PowerShell 更容易了解該語言。

如果您不是 C# 程式設計人員，則這項相似性不重要。 不過，如果您已經熟悉 C#，則相似性可讓學習 Windows PowerShell 更為簡單。



<!--HONumber=May16_HO2-->


