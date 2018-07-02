---
ms.date: 10/13/2017
keywords: dsc,powershell,設定,安裝
title: 適合工程師的預期狀態設定概觀
ms.openlocfilehash: 30ce8bbb8bd3ea69dbf8ca509ecf523eb8fd915f
ms.sourcegitcommit: bad40d59598ae5597051fa381986316a2d9bf6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271070"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>適合工程師的預期狀態設定概觀

本文件適合開發人員及作業小組了解 PowerShell 預期狀態設定 (DSC) 的優勢。
如需 DSC 所提供價值的較高層級檢視，請參閱[適合決策者的預期狀態設定概觀](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>預期狀態設定的優勢

DSC 是用來：

- 減少 Windows 中的指令碼複雜度
- 提升反覆運算的速度

「持續部署」的概念越來越重要。
「持續部署」是指頻繁部署的能力，可以在一天內部署多次。
這些部署的目的並非修正某些項目，而是能快速發行某些項目。
透過盡可能以順暢且可靠的方式讓新功能從開發進入作業，將可以減少新商務邏輯創造價值所需的時間。

移至雲端運算，代表需要能運用「宣告式」範本模型的部署解決方案，其中的結束狀態環境會宣告為文字，並發佈至部署引擎。
此部署技術能大規模地做出快速變更，並具備針對失敗風險的恢復力，因為部署可隨時一致地重複以保證結束狀態。
透過自動化建立支援此作業模式的工具和服務，便是針對這些變更的回應。

DSC 是一個可提供宣告式且等冪 (可重複) 部署、設定和一致性的平台。
DSC 平台可讓您確保資料中心的元件具有正確的設定，以避免錯誤並防止耗費成本的部署失敗。
藉由將 DSC 設定當作應用程式程式碼的一部分，DSC 便能提供持續部署的可能性。
DSC 設定應該當作應用程式的一部分更新，以確保部署應用程式所需的知識永遠保持在最新狀態且隨時可用。

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>「我有 PowerShell，為什麼需要預期狀態設定？」

DSC 設定可將意圖 (或「我要做什麼」) 從執行 (或「我要如何做」) 中分隔出來。
這表示執行邏輯是包含在資源之內。
當功能的 DSC 資源可用時，使用者並不需要了解實作或部署該功能的方式。
這可讓使用者專注於他們的部署結構。

例如，PowerShell 指令碼看起來應該如下：
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
這個指令碼簡單、易懂又直接。
但是，如果您嘗試將該指令碼放入生產環境，您將會遇到幾個問題。
如果該指令碼連續執行兩次，會發生什麼事？
如果 Bob 之前擁有該共用的完整存取權，會發生什麼事？

為了彌補這些問題，指令碼的「實際」版本看起來會更像這樣：
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

這個指令碼更複雜，含有大量的邏輯及錯誤處理。
因為您已不再是指出要完成的動作，而是「要如何這麼做」，使得這個指令碼變得更加複雜。

DSC 可讓您指定要完成的動作，並將基礎邏輯抽象化。

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

此指令碼的格式簡潔且容易閱讀。
邏輯路徑和錯誤處理仍然存在於[資源](resources.md)的實作中，但指令碼作者看不到。

## <a name="separating-environment-from-structure"></a>從結構分隔環境

DevOps 中其中一個常見的模式，是針對部署有多個環境。
例如，可能會有一個可用來快速開發新程式碼原型的「開發」環境。
「開發」環境的程式碼接著會進入「測試」環境，讓其他人員可以確認新的功能。
最後，該程式碼會進入「生產」，也就是即時網站生產環境。

DSC 設定透過使用[設定資料](configData.md)來容納這個開發-測試-生產的管線。
這會進一步將設定結構與受管理節點之間的差異抽象化。
例如，您可以定義一個需要 SQL 伺服器、IIS 伺服器以及中介層伺服器的設定。
無論何種節點接收此設定的何種部分，這三個元素將總是會存在。
您可以使用設定資料將所有三個元素指向開發環境的同一部電腦，然後將三個元素分別指向測試環境的三台不同的電腦，並於最後將三個元素指向生產環境的所有生產伺服器。
若要部署至不同環境，您可以搭配目標環境的正確設定資料來叫用 **Start-DscConfiguration**。

## <a name="see-also"></a>另請參閱

[設定](configurations.md)

[設定資料](configData.md)

[資源](resources.md)
