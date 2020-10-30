---
title: PowerShell Core 中的 WS-Management (WSMan) 遠端處理
description: 使用 WSMan 在 PowerShell Core 中遠端
ms.date: 08/06/2018
ms.openlocfilehash: fdc4159279db28b8ee60bc0853e19512a1f9ec14
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501298"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="6ff98-103">PowerShell Core 中的 WS-Management (WSMan) 遠端處理</span><span class="sxs-lookup"><span data-stu-id="6ff98-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="6ff98-104">建立遠端端點的指示</span><span class="sxs-lookup"><span data-stu-id="6ff98-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="6ff98-105">PowerShell Core for Windows 套件包含 `$PSHome` 中的 WinRM 外掛程式 (`pwrshplugin.dll`) 和安裝指令碼 (`Install-PowerShellRemoting.ps1`)。</span><span class="sxs-lookup"><span data-stu-id="6ff98-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span> <span data-ttu-id="6ff98-106">這些檔案讓 PowerShell 在指定其端點時接受連入的 PowerShell 遠端連線。</span><span class="sxs-lookup"><span data-stu-id="6ff98-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="6ff98-107">動機</span><span class="sxs-lookup"><span data-stu-id="6ff98-107">Motivation</span></span>

<span data-ttu-id="6ff98-108">PowerShell 安裝可以使用 `New-PSSession` 和 `Enter-PSSession` 建立遠端電腦的 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="6ff98-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="6ff98-109">若要啟用它來接受連入的 PowerShell 遠端連線，使用者必須建立 WinRM 遠端端點。</span><span class="sxs-lookup"><span data-stu-id="6ff98-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span> <span data-ttu-id="6ff98-110">這是使用者執行 Install-PowerShellRemoting.ps1 建立 WinRM 端點的明確加入案例。</span><span class="sxs-lookup"><span data-stu-id="6ff98-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span> <span data-ttu-id="6ff98-111">將額外功能新增至 `Enable-PSRemoting` 以執行相同動作之前，安裝指令碼是短期解決方案。</span><span class="sxs-lookup"><span data-stu-id="6ff98-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span> <span data-ttu-id="6ff98-112">如需詳細資料，請參閱問題 [#1193](https://github.com/PowerShell/PowerShell/issues/1193)。</span><span class="sxs-lookup"><span data-stu-id="6ff98-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="6ff98-113">指令碼動作</span><span class="sxs-lookup"><span data-stu-id="6ff98-113">Script Actions</span></span>

<span data-ttu-id="6ff98-114">指令碼</span><span class="sxs-lookup"><span data-stu-id="6ff98-114">The script</span></span>

1. <span data-ttu-id="6ff98-115">在 `$env:windir\System32\PowerShell` 內建立外掛程式的目錄</span><span class="sxs-lookup"><span data-stu-id="6ff98-115">Creates a directory for the plug-in within `$env:windir\System32\PowerShell`</span></span>
1. <span data-ttu-id="6ff98-116">將 pwrshplugin.dll 複製至該位置</span><span class="sxs-lookup"><span data-stu-id="6ff98-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="6ff98-117">產生設定檔</span><span class="sxs-lookup"><span data-stu-id="6ff98-117">Generates a configuration file</span></span>
1. <span data-ttu-id="6ff98-118">使用 WinRM 註冊該外掛程式</span><span class="sxs-lookup"><span data-stu-id="6ff98-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="6ff98-119">註冊</span><span class="sxs-lookup"><span data-stu-id="6ff98-119">Registration</span></span>

<span data-ttu-id="6ff98-120">指令碼必須在系統管理員層級 PowerShell 工作階段內執行，並以兩種模式執行。</span><span class="sxs-lookup"><span data-stu-id="6ff98-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="6ff98-121">透過其將註冊的 PowerShell 執行個體來執行</span><span class="sxs-lookup"><span data-stu-id="6ff98-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="6ff98-122">另一個 PowerShell 執行個體代表其將註冊的執行個體來執行</span><span class="sxs-lookup"><span data-stu-id="6ff98-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="6ff98-123">例如：</span><span class="sxs-lookup"><span data-stu-id="6ff98-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

> [!NOTE]
> <span data-ttu-id="6ff98-124">遠端註冊指令碼會重新啟動 WinRM。</span><span class="sxs-lookup"><span data-stu-id="6ff98-124">The remoting registration script restarts WinRM.</span></span> <span data-ttu-id="6ff98-125">所有現有的 PSRP 工作階段都會在執行指令碼之後立即終止。</span><span class="sxs-lookup"><span data-stu-id="6ff98-125">All existing PSRP sessions are terminate immediately after the script is run.</span></span> <span data-ttu-id="6ff98-126">若在遠端工作階段期間執行，指令碼會終止連線。</span><span class="sxs-lookup"><span data-stu-id="6ff98-126">If run during a remote session, the script terminates the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="6ff98-127">如何連線至新端點</span><span class="sxs-lookup"><span data-stu-id="6ff98-127">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="6ff98-128">指定 `-ConfigurationName "some endpoint name"`，以建立與新 PowerShell 端點的新 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="6ff98-128">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="6ff98-129">若要連線至上述範例中的 PowerShell 執行個體，請使用：</span><span class="sxs-lookup"><span data-stu-id="6ff98-129">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="6ff98-130">請注意，未指定 `-ConfigurationName` 的 `New-PSSession` 和 `Enter-PSSession` 引動過程將會以預設 PowerShell 端點 `microsoft.powershell` 為目標。</span><span class="sxs-lookup"><span data-stu-id="6ff98-130">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>
