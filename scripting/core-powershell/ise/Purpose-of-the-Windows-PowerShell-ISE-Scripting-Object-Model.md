---
title: Windows PowerShell ISE 指令碼物件模型的用途
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
---
# Windows PowerShell ISE 指令碼物件模型的用途
  物件會關聯至 Windows PowerShell 整合式指令碼環境 (ISE) 的表單和函式。 物件模型參考提供有關成員屬性的詳細資料以及這些物件公開的方法。 我們將提供範例來示範您如何使用指令碼直接存取這些方法與屬性。 指令碼物件模型讓您更容易進行下列範圍內的工作。

## 自訂 Windows PowerShell ISE 的外觀
 您可以使用物件模型來修改應用程式設定和選項。 例如，您可以使用如下方式來修改它們︰

-   您可以變更錯誤、警告、詳細資訊輸出及偵錯輸出的色彩。

-   您可以取得或設定命令窗格、輸出窗格及指令碼窗格的背景色彩。

-   您可以設定輸出窗格的前景色彩。

-   您可以設定 Windows PowerShell ISE 的字型名稱和大小。

-   您可以設定警告。 此設定包含在多個 PowerShell 索引標籤中開啟檔案時，或者在儲存檔案之前執行該檔案中的指令碼時所發出的警告。

-   您可以在指令碼窗格和輸出窗格並排顯示的檢視，以及指令碼窗格位於輸出窗格上方的檢視之間進行切換。 您可以將命令窗格停駐於輸出窗格的下方或上方。

## 增強 Windows PowerShell ISE 功能
 您可以使用物件模型來增強 Windows PowerShell ISE 功能。 例如，您可以：

-   新增和修改 Windows PowerShell ISE 本身的執行個體。 例如，若要變更功能表，您可以新增功能表項目，並將新的功能表項目對應至指令碼。

-   建立指令碼，來執行一些您可以在 Windows PowerShell ISE 中使用功能表命令和按鈕來執行的工作。 例如，您可以新增、移除或選取 PowerShell 索引標籤。

-   可使用功能表命令和按鈕執行的補充工作。 例如，您可以重新命名 PowerShell 索引標籤。

-   管理與檔案相關聯之命令窗格、輸出窗格和指令碼窗格的文字緩衝區。 例如，您可以：

    -   取得或設定所有文字。

    -   取得或設定文字選取範圍。

    -   執行指令碼或執行所選取的指令碼部分。

    -   捲動一行來檢視。

    -   在插入號位置插入文字。

    -   選取文字區塊。

    -   取得最後一個行號。

-   執行檔案作業。 例如，您可以：

    -   開啟檔案、儲存檔案，或使用不同名稱儲存檔案。

    -   判斷檔案在上次儲存之後是否已變更。

    -   取得檔案名稱。

    -   選取檔案。

## 自動化工作
 您可以使用指令碼物件模型，針對經常執行的作業建立鍵盤快速鍵。

## 另請參閱
 [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md) 
 [Windows PowerShell ISE 物件模型參考](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  


<!--HONumber=May16_HO2-->


