---
title:  管理服務
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  7a410e4d-514b-4813-ba0c-0d8cef88df31
---

# 管理服務
有八個針對各種服務工作設計的核心服務 Cmdlet。 我們將只探討列出及變更服務執行中狀態的 Cmdlet，但您可以使用 **Get-Help &#42;-Service** 取得服務 Cmdlet 清單，並使用 **Get-Help<Cmdlet 名稱>** (例如 **Get-Help New-Service**) 尋找每個服務 Cmdlet 的相關資訊。

## 取得服務
您可以使用 **Get-Service** Cmdlet 取得本機或遠端電腦上的服務。 如同 **Get-Process**，在不使用參數的情況下使用 **Get-Service** 命令會傳回所有服務。 您可以依名稱篩選，甚至可以使用星號作為萬用字元︰

```
PS> Get-Service -Name se*
Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

因為服務的實際名稱不一定很明顯，所以您有時可能需要依顯示名稱尋找服務。 您可以依特定名稱、使用萬用字元或使用顯示名稱清單來執行這項操作︰

```
PS> Get-Service -DisplayName se*
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center
PS> Get-Service -DisplayName ServiceLayer,Server
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

您可以使用 Get-Service Cmdlet 的 ComputerName 參數取得遠端電腦上的服務。 ComputerName 參數接受多個值和萬用字元，因此您可以使用單一命令取得多部電腦上的服務。 例如，下列命令會取得 Server01 遠端電腦上的服務。

```
Get-Service -ComputerName Server01
```

## 取得必要和相依的服務
Get-Service Cmdlet 有兩個對服務管理很有用的參數。 DependentServices 參數可取得依存於此服務的服務。 RequiredServices 參數可取得此服務依存的服務。

這些參數只會顯示 Get-Service 所傳回之 System.ServiceProcess.ServiceController 物件的 DependentServices 和 ServicesDependedOn (別名=RequiredServices) 屬性值，但它們簡化了命令，讓您更容易取得這項資訊。

下列命令會取得 LanmanWorkstation 服務所需的服務。

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices
Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

下列命令會取得需要 LanmanWorkstation 服務的服務。

```
PS> Get-Service -Name LanmanWorkstation -DependentServices
Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

您甚至可以取得具有相依性的所有服務。 下列命令會執行這項操作，然後使用 Format-Table Cmdlet 顯示電腦上服務的 Status、Name、RequiredServices 和 DependentServices 屬性。

```
Get-Service -Name * | where {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## 停止、啟動、暫停及重新啟動服務
所有服務 Cmdlet 都有相同的一般形式。 服務可以使用一般名稱或顯示名稱來指定，並接受清單和萬用字元作為值。 若要停止列印多工緩衝處理器，請使用：

```
Stop-Service -Name spooler
```

若要啟動已停止的列印多工緩衝處理器，請使用：

```
Start-Service -Name spooler
```

若要暫停列印多工緩衝處理器，請使用：

```
Suspend-Service -Name spooler
```

**Restart-Service** Cmdlet 與其他服務 Cmdlet 的運作方式相同，不過我們將示範一些更複雜的範例。 最簡單的使用方式是指定服務的名稱︰

```
PS> Restart-Service -Name spooler
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

您會發現自己一再重複收到有關列印多工緩衝處理器正在啟動的警告訊息。 當您執行需要一些時間的服務操作時，Windows PowerShell 會通知您，它仍在嘗試執行工作。

如果您想要重新啟動多項服務，您可以取得服務清單、加以篩選，然後執行重新啟動︰

```
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

這些服務 Cmdlet 沒有 ComputerName 參數，但您可以使用 Invoke-Command Cmdlet 在遠端電腦上執行。 例如，下列命令會重新啟動 Server01 遠端電腦上的多工緩衝處理器服務。

```
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## 設定服務屬性
Set-Service Cmdlet 會變更本機或遠端電腦上的服務屬性。 因為服務狀態是屬性，所以您可以使用這個 Cmdlet 來啟動、停止及暫停服務。 Set-Service Cmdlet 也有 StartupType 參數，可讓您變更服務啟動類型。

若要在 Windows Vista 和更新的 Windows 版本上使用 Set-Service，請使用 [以系統管理員身分執行] 選項開啟 Windows PowerShell。

如需詳細資訊，請參閱 [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)。

## 另請參閱
[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
[Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)



<!--HONumber=May16_HO2-->


