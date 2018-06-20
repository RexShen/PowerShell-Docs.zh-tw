---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 準備好使用 Windows PowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: 5e095984286ff89958dc0a4e3d27e40eae5b2c5e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950962"
---
# <a name="getting-ready-to-use-windows-powershell"></a>準備好使用 Windows PowerShell
安裝並啟動 Windows PowerShell 之後，請考慮下列安裝選項。 您可以隨時執行這些工作。

- **安裝說明檔。** Windows PowerShell 3.0 中包含的 Cmdlet 沒有說明檔。 不過，您可以使用 [Update-Help](/powershell/module/microsoft.powershell.core/update-help) Cmdlet 將最新的說明檔下載並安裝到您的電腦 安裝檔案之後，您可以使用 [Get-Help](/powershell/module/microsoft.powershell.core/get-help) Cmdlet 直接在命令列顯示。 如需詳細資訊，請參閱 [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_updatable_help)。

    如果您決定不要安裝說明檔，您仍然可以閱讀線上說明主題。 若要尋找任何線上版本的 Cmdlet 說明主題，請輸入：`Get-Help <CmdletName> -Online`。 若要瀏覽 Windows PowerShell 說明主題，請參閱 [PowerShell 文件](/powershell/scripting)。

- **執行指令碼。** 為了保護 Windows PowerShell 的安全，Windows PowerShell 上預設的執行原則是**受限制**的。 這項原則可讓您執行 Cmdlet，但不能執行指令碼。 若要執行指令碼，請使用 [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) Cmdlet，將執行原則變更為 **AllSigned** 或 **RemoteSigned**。 只有電腦上的 Administrators 群組成員才能執行此 Cmdlet。 如需詳細資訊，請參閱 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。

- **啟用遠端功能。** 系統已為您設定成在其他電腦上執行遠端命令。 在 Windows Server 2012 R2 和 Windows Server 2012 上，系統還會設定為接收遠端命令，也就是允許其他電腦在本機電腦上執行遠端命令。 若要讓執行其他 Windows 版本的電腦接收遠端命令，請在您要遠端管理的電腦上執行 [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) Cmdlet。 只有電腦上的 Administrators 群組成員才能執行此 Cmdlet。 如需詳細資訊，請參閱 [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote)。

    注意︰如果在執行 Windows PowerShell 2.0 的電腦上啟用了遠端功能，當您安裝 Windows Management Framework 3.0 之後仍會啟用遠端功能。 不過，在 Windows Server 2008 (不是 Windows Server 2008 R2) 上，您必須在安裝 Windows Management Framework 3.0 之後重新啟用遠端功能。

## <a name="see-also"></a>另請參閱
- [安裝 Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [啟動 Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)