---
title: 如何在 Windows PowerShell ISE 中建立 PowerShell 索引標籤
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
---
# 如何在 Windows PowerShell ISE 中建立 PowerShell 索引標籤
Windows PowerShell® 整合式指令碼環境 (ISE) 中的索引標籤可讓您在同一個應用程式內，同時建立並使用數種執行環境。 每個 PowerShell 索引標籤會對應到不同的執行環境或工作階段。

> [!NOTE]
> 您在一個索引標籤中建立的變數、函式和別名不會延續到另一個索引標籤。 它們是不同的 Windows PowerShell 工作階段。

使用下列步驟，在 Windows PowerShell 中開啟或關閉索引標籤。 若要重新命名索引標籤，可在 Windows PowerShell 索引標籤指令碼物件上設定 [DisplayName](https://technet.microsoft.com/en-us/library/a9b58556-951b-4f48-b3ae-b351b7564360#Displayname) 屬性。

## 建立及使用新的 PowerShell 索引標籤
在 **[檔案]** 功能表上，按一下 **[新增 PowerShell 索引標籤]**。 新的 PowerShell 索引標籤一律會以使用中視窗開啟。 PowerShell 索引標籤是依其開啟順序以累加方式編號。 每個索引標籤會與自己的 Windows PowerShell 主控台視窗建立關聯。 您一次最多可以開啟 32 個 PowerShell 索引標籤 (在 Windows PowerShell ISE 2.0 中僅限 8 個)，每個索引標籤會有自己的工作階段。

請注意，按一下工具列中的**新增**或**開啟**圖示，並不會建立新的索引標籤和個別工作階段。  相反地，這些按鈕會在目前使用中的索引標籤和工作階段中，開啟新的或現有的指令碼檔案。 每個索引標籤和工作階段可以有多個開啟的指令碼檔案。 當相關聯的工作階段為使用中時，工作階段的指令碼索引標籤只會出現在工作階段索引標籤下方。

若要將 PowerShell 索引標籤設為使用中，請按一下該索引標籤。 若要從所有開啟的 PowerShell 索引標籤中進行選取，請在 **[檢視]** 功能表上，按一下您要使用的 PowerShell 索引標籤。

## 建立及使用新的遠端 PowerShell 索引標籤
在 **[檔案]** 功能表上，按一下 **[新增遠端 PowerShell 索引標籤]** 在遠端電腦上建立工作階段。 對話方塊隨即出現，並提示您輸入建立遠端連線所需的詳細資料。 遠端索引標籤的運作方式就像是本機 PowerShell 索引標籤，但命令和指令碼會在遠端電腦上執行。

## 關閉 PowerShell 索引標籤
若要關閉索引標籤，您可以使用下列任一項技術：

-   按一下您要關閉的索引標籤。

-   在 **[檔案]** 功能表上，按一下 **[關閉 PowerShell 索引標籤]**，或在使用中的索引標籤上，按一下 [關閉] 按鈕 (**X**) 以關閉索引標籤。

如果您在要關閉的 PowerShell 索引標籤中，有已開啟且未儲存的檔案，系統會提示您儲存或捨棄檔案。 如需如何儲存指令碼的詳細資訊，請參閱[如何儲存指令碼](https://technet.microsoft.com/en-us/library/162f594d-efd3-4234-9960-45e56e6eadc8).

## 另請參閱
[使用 Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)
[如何在 Windows PowerShell ISE 中使用主控台窗格](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


