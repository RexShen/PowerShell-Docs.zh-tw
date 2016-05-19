---
title: ISE 物件模型階層
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
---
# ISE 物件模型階層
  本主題說明隸屬於 Windows PowerShell 整合式指令碼環境 (ISE) 一部分的物件階層。 Windows PowerShell ISE 隨附於 Windows PowerShell 3.0 和 Windows PowerShell 4.0。 按一下物件，即會帶領您進入定義物件之類別的參考文件。

##  <a name="psISE"></a> **$psISE 物件**
 **$psISE** 物件是 Windows PowerShell ISE 物件階層的[根物件](The-ObjectModelRoot-Object.md)。 它位於最上層，可提供下列物件來編寫指令碼︰

-   **[$psISE.CurrentFile](#currentfile)**

-   **[$psISE.CurrentPowerShellTab](#currentpowershelltab)**

-   **[$psISE.CurrentVisibleHorizontalTool](#CurrentVisibleHorizontalTool)**

-   **[$psISE.CurrentVisibleVerticalTool](#CurrentVisibleVerticalTool)**

-   **[$psISE.Options](#options)**

-   **[$psISE.PowerShellTabs](#powershelltabs)**

##  <a name="CurrentFile"></a> **[$psISE.CurrentFile](The-ISEFile-Object.md)**
 **$psISE.CurrentFile** 物件是 [ISEFile](The-ISEFile-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰

-   **[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md#Displayname)**

-   **[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)** 這個物件是 [ISEEditor](The-ISEEditor-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰

    -   **[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md#cangotomatch)**

    -   **[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**

    -   **[CaretLine](The-ISEEditor-Object.md#CaretLine)**

    -   **[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**

    -   **[LineCount](The-ISEEditor-Object.md#LineCount)**

    -   **[SelectedText](The-ISEEditor-Object.md#SelectedText)**

    -   **[文字](The-ISEEditor-Object.md#Text)**

-   **[編碼](The-ISEFile-Object.md#Encoding)**

-   **[FullPath](The-ISEFile-Object.md#FullPath)**

-   **[IsSaved](The-ISEFile-Object.md#IsSaved)**

-   **[IsUntitled](The-ISEFile-Object.md#IsUntitled)**

##  <a name="CurrentPowerShellTab"></a> **[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**
 **$psISE.CurrentPowerShellTab** 物件是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰

-   **[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)** 這個物件是 [ISEMenuItem](The-ISEMenuItem-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Action](The-ISEMenuItem-Object.md#Action)**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName](The-ISEMenuItem-Object.md#DisplayName)**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Shortcut](The-ISEMenuItem-Object.md#Shortcut)**

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.CanInvoke](The-PowerShellTab-Object.md#CanExecute)**

-   **[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)** 這個物件是 [ISEEditor](The-ISEEditor-Object.md) 類別的執行個體，可提供下列物件來編寫指令碼︰

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatch](The-ISEEditor-Object.md#cangotomatch)**

    -   **[CaretColumn](The-ISEEditor-Object.md#CaretColumn)**

    -   **[CaretLine](The-ISEEditor-Object.md#CaretLine)**

    -   **[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineText](The-ISEEditor-Object.md#CaretLineText)**

    -   **[LineCount](The-ISEEditor-Object.md#LineCount)**

    -   **[SelectedText](The-ISEEditor-Object.md#SelectedText)**

    -   **[文字](The-ISEEditor-Object.md#Text)**

-   **[$psISE.CurrentPowerShellTab.DisplayName](The-PowerShellTab-Object.md#Displayname)**

-   **[$psISE.CurrentPowerShellTab.ExpandedScript](The-PowerShellTab-Object.md#ExpandedScript)**

-   **[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#HorizontalAddOnToolsPaneOpened)**

-   **[$psISE.CurrentPowerShellTab.Prompt](The-PowerShellTab-Object.md#Prompt)**

-   **[$psISE.CurrentPowerShellTab.ShowCommands](The-PowerShellTab-Object.md#ShowCommands)**

-   **[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.StatusText](The-PowerShellTab-Object.md#StatusText)**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpened](The-PowerShellTab-Object.md#VerticalAddOnToolsPaneOpened)**

-   **[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

##  <a name="CurrentVisibleHorizontalTool"></a> **$psISE.CurrentVisibleHorizontalTool**
 **$psISE.CurrentVisibleHorizontalTool** 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。 它代表目前停駐於 Windows PowerShell ISE 視窗頂端的已安裝附加元件工具。 這個物件可提供下列物件來編寫指令碼︰

-   **[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#control)**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#isvisible)**

-   **[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**

##  <a name="CurrentVisibleVerticalTool"></a> **$psISE.CurrentVisibleVerticalTool**
 **$psISE.CurrentVisibleHorizontalTool** 物件是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 類別的執行個體。 它代表目前停駐於 Windows PowerShell ISE 視窗右邊的已安裝附加元件工具。 這個物件可提供下列物件來編寫指令碼︰

-   **[$psISE.CurrentVisibleHorizontalTool.Control](The-ISEAddOnTool-Object.md#control)**

-   **[$psISE.CurrentVisibleHorizontalTool.IsVisible](The-ISEAddOnTool-Object.md#isvisible)**

-   **[$psISE.CurrentVisibleHorizontalTool.Name](The-ISEAddOnTool-Object.md#name)**

##  <a name="Options"></a> **$psISE.Options**
 **$psISE.Options** 物件可提供下列物件來編寫指令碼︰

-   **[$psISE.Options.AutoSaveMinuteInterval](The-ISEOptions-Object.md#asmi)**

-   **[$psISE.Options.ConsolePaneBackgroundColor](The-ISEOptions-Object.md#cpbc)**

-   **[$psISE.Options.ConsolePaneTextForegroundColor](The-ISEOptions-Object.md#conpfc)**

-   **[$psISE.Options.ConsolePaneTextBackgroundColor](The-ISEOptions-Object.md#conptbc)**

-   **[$psISE.Options.ConsoleTokenColors](The-ISEOptions-Object.md#contc)**

-   **[$psISE.Options.DebugBackgroundColor](The-ISEOptions-Object.md#dbc)**

-   **[$psISE.Options.DebugForegroundColor](The-ISEOptions-Object.md#dfc)**

-   **[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**

-   **[$psISE.Options.ErrorBackgroundColor](The-ISEOptions-Object.md#ebc)**

-   **[$psISE.Options.ErrorForegroundColor](The-ISEOptions-Object.md#efc)**

-   **[$psISE.Options.FontName](The-ISEOptions-Object.md#fn)**

-   **[$psISE.Options.Fontsize](The-ISEOptions-Object.md#fs)**

-   **[$psISE.Options.IntellisenseTimeoutInSeconds](The-ISEOptions-Object.md#itis)**

-   **[$psISE.Options.MRUCount](The-ISEOptions-Object.md#mc)**

-   **[$psISE.Options.ScriptPaneBackgroundColor](The-ISEOptions-Object.md#spbc)**

-   **[$psISE.Options.ScriptPaneForegroundColor](The-ISEOptions-Object.md#spfc)**

-   **[$psISE.Options.SelectedScriptPaneState](The-ISEOptions-Object.md#ssps)**

-   **[$psISE.Options.ShowDefaultSnippets](The-ISEOptions-Object.md#sds)**

-   **[$psISE.Options.ShowIntellisenseInConsolePane](The-ISEOptions-Object.md#siicp)**

-   **[$psISE.Options.ShowIntellisenseInScriptPane](The-ISEOptions-Object.md#siisp)**

-   **[$psISE.Options.ShowLineNumbers](The-ISEOptions-Object.md#sln)**

-   **[$psISE.Options.ShowOutlining](The-ISEOptions-Object.md#so)**

-   **[$psISE.Options.ShowToolBar](The-ISEOptions-Object.md#stb)**

-   **[$psISE.Options.ShowWarningBeforeSavingOnRun](The-ISEOptions-Object.md#swbsor)**

-   **[$psISE.Options.ShowWarningForDuplicateFiles](The-ISEOptions-Object.md#swfdf)**

-   **[$psISE.Options.TokenColors](The-ISEOptions-Object.md#tc)**

-   **[$psISE.Options.UseEnterToSelectConsolePaneIntellisense](The-ISEOptions-Object.md#uetsicpi)**

-   **[$psISE.Options. UseEnterToSelectScriptPaneIntellisense](The-ISEOptions-Object.md#uetsispi)**

-   **[$psISE.Options.UseLocalHelp](The-ISEOptions-Object.md#ulh)**

-   **[$psISE.Options.VerboseBackgroundColor](The-ISEOptions-Object.md#vbc)**

-   **[$psISE.Options.VerboseForegroundColor](The-ISEOptions-Object.md#vfc)**

-   **[$psISE.Options.WarningBackgroundColor](The-ISEOptions-Object.md#wbc)**

-   **[$psISE.Options.WarningForegroundColor](The-ISEOptions-Object.md#wfc)**

-   **[$psISE.Options.XmlTokenColors](The-ISEOptions-Object.md#xtc)**

-   **[$psISE.Options.Zoom](The-ISEOptions-Object.md#z)**

##  <a name="PowerShellTabs"></a> **[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**
 **$psISE.PowerShellTabs** 物件是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 類別的執行個體。 它是所有目前開啟的 PowerShell 索引標籤集合，代表本機電腦上或連線的遠端電腦上可用的 Windows PowerShell 執行環境。 集合中的每個成員都是 [PowerShellTab](The-PowerShellTab-Object.md) 類別的執行個體。

## 另請參閱
 [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
 [Windows PowerShell ISE 物件模型參考](Windows-PowerShell-ISE-Object-Model-Reference.md)


<!--HONumber=May16_HO2-->


