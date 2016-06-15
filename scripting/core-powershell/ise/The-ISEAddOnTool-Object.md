---
title:  ISEAddOnTool 物件
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
---

# ISEAddOnTool 物件
  **ISEAddonTool** 物件代表一個已安裝的附加元件工具，可為 Windows PowerShell ISE 提供額外的功能。 **命令**工具即為一例，您可以依序按一下 [檢視] 和 [顯示命令附加元件] 來顯示此工具。 您接著可以藉由操作各種可用的 **ISEAddOnTool** 物件來存取此工具。

 每個附加元件工具都可以與垂直窗格或水平窗格產生關聯。 垂直窗格會停駐於 Windows PowerShell ISE 的右邊。 水平窗格則會停駐於底部。

 Windows PowerShell ISE 中的每個 PowerShell 索引標籤都可以安裝一組自己的附加元件工具。 請參閱 [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md) 和 [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)，來存取可供目前所選取索引標籤使用的工具集合，或者 [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) 集合物件中任何 **PowerShellTab** 物件上的相同屬性。

## 方法
 沒有任何 Windows PowerShell ISE 特定的方法適用於這個類別的物件。

## [內容]

###  <a name="Control"></a> 控制
  在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

 **Control** 屬性可提供許多命令附加元件詳細資料的讀取權。

```
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher

```

###  <a name="IsVisible"></a> IsVisible
  在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

 布林值屬性，指出附加元件工具目前是否會顯示於它的指派窗格中。 如果顯示，您可以將 **IsVisible** 屬性設定為 **$false** 來隱藏工具，或者將 **IsVisible** 屬性設定為 **$true**，讓附加元件工具可顯示於 PowerShell 索引標籤上。 請注意，隱藏附加元件工具之後，就無法再透過 **CurrentVisibleHorizontalTool** 或 **CurrentVisibleVerticalTool** 物件來存取，因此無法透過在該物件上使用這個屬性來顯示。

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

###  <a name="name"></a> 名稱
  在 Windows PowerShell ISE 3.0 與更新的版本中支援，而且不存在於之前的版本。

 可取得附加元件工具名稱的唯讀屬性。

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## 另請參閱
 [ISEAddOnToolCollection 物件](The-ISEAddOnToolCollection-Object.md)
 [Windows PowerShell ISE 指令碼物件模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
 [Windows PowerShell ISE 物件模型參考](Windows-PowerShell-ISE-Object-Model-Reference.md)
 [ISE 物件模型階層](The-ISE-Object-Model-Hierarchy.md)



<!--HONumber=May16_HO2-->


