---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "使用 JEA"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 88ce340c09efdbb3d81a72fe6113c1187a9152f2
ms.openlocfilehash: 9db7a5a91d25d459313117da34af63016f03c241

---

# 使用 JEA
本節主要在於了解*使用 JEA* 的使用者體驗。
在＜必要條件＞一節中，您已建立一個 JEA 端點示範。
我們將使用此示範來說明 JEA 的操作方式。
在稍後的章節中，本指南會回頭介紹讓該使用者體驗變成可能的動作和檔案。

## 以非系統管理員身分使用 JEA
為了示範 JEA 的操作方式，您必須以非系統管理員使用者身分使用 PowerShell 遠端。
在新的 PowerShell 視窗中執行下列命令：   

```PowerShell
$NonAdminCred = Get-Credential
```

當出現提示時，輸入非系統管理員帳戶的認證。
如果您遵循[設定使用者和群組](creating-a-domain-controller.md#set-up-users-and-groups)一節進行，則會是︰
-   使用者名稱 = "OperatorUser"
-   密碼 = "pa$$w0rd"

接下來，執行下列命令，使用您提供的認證連線到示範端點︰

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

您現在已輸入本機電腦上的互動式遠端 PowerShell 工作階段。
藉由使用 "Credential" 參數，即可*像是* OperatorUser (或您使用的任何帳戶) 進行連線。
提示 `[localhost]: PS>` 的變更表示您正在對遠端工作階段執行。  

在遠端命令提示字元中執行下列命令，以顯示您可以使用的命令︰

```PowerShell
Get-Command
```

如您所見，這是一般 PowerShell 視窗 (通常可包含數千個命令) 中非常有限的一小組可用命令。
具體來說，它只會顯示 8 個預設 JEA 命令 (Clear-Host、Exit-PSSession、Get-Command、Get-FormatData、Get-Help、Measure-Object、Out-Default、Select-Object)，以及兩個明確包含在維護角色功能檔案中的命令。

接下來，讓我們看看此工作階段執行所在的使用者內容，方法是叫用包含在維護角色功能檔案中的自訂函式︰

```PowerShell
Get-UserInfo
```

此函式的輸出顯示 "ConnectedUser" 及 "RunAsUser"。
已連線的使用者是連線到遠端工作階段的帳戶 (例如您的帳戶)。
已連線的使用者不需要具有系統管理員權限。
「執行身分」帳戶是實際執行特殊權限動作的帳戶。
以一位使用者的身分連線，並以特殊權限使用者身分執行，我們可以允許非特殊權限使用者執行特定的管理工作，而不需要授與系統管理權限。

若要示範其操作方式，請執行下列命令︰

```PowerShell
Restart-Service -Name Spooler -Verbose
```

一般而言，Restart-Service 需要系統管理員權限才能執行。
不過，透過 JEA 虛擬帳戶，我們就可以使用非特殊權限認證來執行。

因此，JEA 可讓您使用已在使用的命令來完成工作。
但您*不應該*使用的命令又如何？
請嘗試在 JEA 工作階段中執行不同的命令，例如 `Restart-Computer`，並注意 JEA 如何防止這類命令被執行。

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

最後，若要離開 JEA 限制端點，請執行下列命令︰

```PowerShell
Exit-PSSession
```

這會中斷您與遠端 PowerShell 工作階段的連線。




<!--HONumber=Jul16_HO1-->


