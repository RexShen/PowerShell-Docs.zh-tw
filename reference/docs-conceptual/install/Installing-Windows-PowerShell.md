---
ms.date: 08/09/2017
keywords: powershell,cmdlet,下載,安裝,安裝程式,windows 10, windows 8.1, windows 8.0,windows 7
title: 安裝 Windows PowerShell
ms.openlocfilehash: 345cde8012bece730e7217ed16be6175ad26bb28
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "62086471"
---
# <a name="installing-windows-powershell"></a>安裝 Windows PowerShell

從 Windows 7 SP1 和 Windows Server 2008 R2 SP1 開始，根據預設，每個 Windows 中都已預先安裝 Windows PowerShell。

如果您感興趣的是 PowerShell 6 和更新版本，則需要安裝 PowerShell Core，而不是 Windows PowerShell。 如需相關資訊，請參閱[在 Windows 上安裝 PowerShell Core](Installing-PowerShell-Core-on-Windows.md)。

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>在 Windows 10、8.1、8.0 和 7 中尋找 PowerShell

由於 PowerShell 主控台或 ISE (整合式指令碼環境) 的位置會從某個 Windows 版本移到另一版，因此要在 Windows 中找到並不容易。

下表有助於在您的 Windows 版本中找到 PowerShell。
此處列出的所有版本都是發行之後未經更新的原始版本。

### <a name="for-console"></a>主控台

版本 | Location
-- | --
Windows 10 | 按一下左下角 Windows 圖示，開始鍵入 PowerShell
Windows 8.1、8.0 | 在開始畫面中，開始鍵入 PowerShell。<br/>如果在桌面上，則按一下左下角 Windows 圖示，開始鍵入 PowerShell
Windows 7 SP1 | 按一下左下角 Windows 圖示，在搜尋方塊開始鍵入 PowerShell

### <a name="for-ise"></a>ISE

版本 | Location
-- | --
Windows 10 | 按一下左下角 Windows 圖示，開始鍵入 ISE
Windows 8.1、8.0 | 在開始畫面上，鍵入 **PowerShell ISE**。<br/>如果在桌面上，則按一下左下角 Windows 圖示，鍵入 **PowerShell ISE**
Windows 7 SP1 | 按一下左下角 Windows 圖示，在搜尋方塊開始鍵入 PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>在 Windows Server 版本中尋找 PowerShell

從 Windows Server 2008 R2 開始，可以不使用圖形化使用者介面 (GUI) 安裝 Windows 作業系統。
不含 GUI 的 Windows Server 版本會命名為 **Core** 版本，而含 GUI 的版本會命名為 **Desktop**。

### <a name="windows-server-core-editions"></a>Windows Server Core 版本

在所有 Core 版本中，當您登入伺服器時，會看到 Windows 命令提示字元視窗。

鍵入 `powershell` 並按 **ENTER**，以在命令提示字元工作階段內啟動 PowerShell。
鍵入 `exit` 以終止 PowerShell 工作階段，並返回命令提示字元。

### <a name="windows-server-desktop-editions"></a>Windows Server Desktop 版本

在所有 Desktop 版本中，按一下左下角 Windows 圖示，開始鍵入 PowerShell。
您會同時取得主控台和 ISE 選項。

上述規則中唯一例外的是 Windows Server 2008 R2 SP1 的 ISE。在此情況下，按一下左下角 Windows 圖示，鍵入 PowerShell ISE。

## <a name="how-to-check-the-version-of-powershell"></a>如何檢查 PowerShell 版本

若要知道您安裝的 PowerShell 是哪個版本，請開啟 PowerShell 主控台 (或 ISE)，鍵入 `$PSVersionTable` 並按 **ENTER**。 尋找 `PSVersion` 值。

## <a name="upgrading-existing-windows-powershell"></a>升級現有的 Windows PowerShell

PowerShell 的安裝套件隨附於 WMF 安裝程式。
WMF 安裝程式的版本會與 PowerShell 版本相符；Windows PowerShell 沒有獨立安裝程式。

如果您需要在 Windows 中更新現有的 PowerShell 版本，請使用下表找出您想要更新的目標 PowerShell 版本安裝程式。

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (請參閱備註 1)<br/>Windows Server 2016 | - | - | - | 已安裝
Windows 8.1<br/>Windows Server 2012 R2 | - | 已安裝 | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | 已安裝 | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> 在已啟用自動更新的 Windows 10 初始版本上，PowerShell 會從 5.0 版更新為 5.1 版。
>
> 若 Windows 10 的原始版本未透過 Windows Updtaes 更新，PowerShell 的版本會是 5.0。

## <a name="need-azure-powershell"></a>Microsoft Azure PowerShell

如果您要尋找 **Azure PowerShell**，可以從 [Azure PowerShell 概觀](/powershell/azure/overview)著手。

否則，您可能需要[安裝與設定 Azure PowerShell](/powershell/azure/install-az-ps)

## <a name="see-also"></a>另請參閱

[Windows PowerShell 系統需求](Windows-PowerShell-System-Requirements.md)

[啟動 Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)
