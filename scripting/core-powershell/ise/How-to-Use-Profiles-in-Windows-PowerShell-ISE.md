---
title: 如何在 Windows PowerShell ISE 中使用設定檔
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
---
# 如何在 Windows PowerShell ISE 中使用設定檔
本主題說明如何在 Windows PowerShell® 整合式指令碼環境 (ISE) 中使用設定檔。 建議您在執行本節中的工作之前，先檢閱 [about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054)，或者在主控台窗格中輸入 “get-help about_profiles”，然後按 **ENTER** 鍵.

設定檔是當您啟動新的工作階段時自動執行的 Windows PowerShell ISE 指令碼。  您可以為 Windows PowerShell ISE 建立一或多個 Windows PowerShell 設定檔，然後使用這些設定檔來新增 Windows PowerShell 或 Windows PowerShell ISE 環境的設定、準備環境供您使用，以及提供您所需的變數、別名、函式、色彩和字型喜好設定。 設定檔會影響您啟動的每個 Windows PowerShell ISE 工作階段。

> [!NOTE]
> Windows PowerShell 執行原則會決定您是否可以執行指令碼並載入設定檔。 預設執行原則 “Restricted” 可防止所有指令碼執行，包括設定檔。 如果使用 “Restricted” 原則，則無法載入設定檔。 如需執行原則的詳細資訊，請參閱 [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6).

## 選取要在 Windows PowerShell ISE 中使用的設定檔
Windows PowerShell ISE 支援目前使用者和所有使用者的設定檔。 它也支援適用於所有主機的 Windows PowerShell 設定檔。

您使用的設定檔取決於您使用 Windows PowerShell 和 Windows PowerShell ISE 的方式。

-   如果只使用 Windows PowerShell ISE 來執行 Windows PowerShell，則要將所有項目儲存到 ISE 特定的其中一個設定檔，例如，適用於 Windows PowerShell ISE 的 CurrentUserCurrentHost 設定檔，或者適用於 Windows PowerShell ISE 的 AllUsersCurrentHost 設定檔。

-   如果使用多個主機程式來執行 Windows PowerShell，請在影響所有主機程式的設定檔 (例如 CurrentUserAllHosts 或 AllUsersAllHosts 設定檔) 中儲存您的函式、別名、變數和命令，並在適用於 Windows PowerShell ISE 設定檔的 CurrentUserCurrentHost 設定檔或適用於 Windows PowerShell ISE 的 AllUsersCurrentHost 設定檔中儲存 ISE 特定的功能 (例如色彩和字型自訂)。

以下是可在 Windows PowerShell ISE 中建立及使用的設定檔。 每個設定檔會儲存到自己的特定路徑。

|設定檔類型|設定檔路徑|
|----------------|----------------|
|“Current user, PowerShell ISE”|$profile.CurrentUserCurrentHost (或 $profile)|
|“All users, PowerShell ISE”|$profile.AllUsersCurrentHost|
|“Current user, All hosts”|$profile.CurrentUserAllHosts|
|“All users, All hosts”|$profile.AllUsersAllHosts|

## 建立新的設定檔
若要建立新的 “Current user, Windows PowerShell ISE” 設定檔，請執行下列命令︰

```
if (!(test-path $profile )) 
{new-item -type file -path $profile -force}
```

若要建立新的 “All users, Windows PowerShell ISE” 設定檔，請執行下列命令︰

```
if (!(test-path $profile.AllUsersCurrentHost)) 
{new-item -type file -path $profile.AllUsersCurrentHost -force}
```

若要建立新的 “Current user, All Hosts” 設定檔，請執行下列命令︰

```
if (!(test-path $profile.CurrentUserAllHosts)) 
{new-item -type file -path $profile.CurrentUserAllHosts -force}
```

若要建立新的 “All users, All Hosts” 設定檔，請輸入︰

```
if (!(test-path $profile.AllUsersAllHosts)) 
{new-item -type file -path $profile.AllUsersAllHosts-force}
```

## 編輯設定檔

1.  若要開啟設定檔，請執行命令 psedit，並提供指定您要編輯之設定檔的變數。 例如，若要開啟 “Current user, Windows PowerShell ISE” 設定檔，請輸入︰ `psEdit $profile`

2.  將一些項目新增至您的設定檔。 以下是一些可協助您開始的範例︰

    -   若要將主控台窗格的預設背景色彩變更為藍色，請在設定檔中輸入︰`$psISE.Options.OutputPaneBackground = 'blue'`。 如需 $psISE 變數的詳細資訊，請參閱 [Windows PowerShell ISE 物件模型參考](https://technet.microsoft.com/en-us/library/e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c).

    -   若要將字型大小變更為 20，在設定檔中輸入︰ `$psISE.Options.FontSize =20`

3.  若要儲存設定檔，請在 **[檔案]** 功能表上，按一下 **[儲存]**。 下次當您開啟 Windows PowerShell ISE 時，便會套用您的自訂。

## 另請參閱
[about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[使用 Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=May16_HO2-->


