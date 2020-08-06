---
title: 'GetProc03 (c # ) 範例程式碼 |Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 278c3f36bb975f9ea195978853e6539c0bd15084
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787116"
---
# <a name="getproc03-c-sample-code"></a>GetProc03 (C#) 範例程式碼

下列程式碼顯示 `Get-Process` 可接受管線輸入的 Cmdlet 的執行方式。 這個實作為定義 `Name` 參數，它會接受管線輸入、根據提供的名稱從本機電腦抓取進程資訊，然後使用[WriteObject (system.object，system.string) ](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法做為將物件傳送至管線的輸出機制。

> [!NOTE]
> 您可以使用適用于 Windows Vista 和 .NET Framework 3.0 執行時間元件的 Microsoft Windows 軟體發展工具組，為這個 getprov03.cs) 下載 c # 原始程式檔 (。 如需下載指示，請參閱[如何安裝 Windows powershell 和下載 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下載的來源檔案可在目錄中取得 **\<PowerShell Samples>** 。

## <a name="code-sample"></a>程式碼範例

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a>另請參閱

[Windows PowerShell 程式設計人員手冊](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
