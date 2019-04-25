---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057498"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>宣告版本範圍 (1.* 等等) 的模組支援
結合 **-MinimumVersion** 之後，**-MaximumVersion** 現在可讓使用者在特定範圍內取得/匯入模組。 參數也支援 **.**\*。 下列範例會顯示其運作方式︰

現在，您可以結合 **-MinimumVersion** 和 **-MaximumVersion** 來匯入特定範圍內的模組：

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
