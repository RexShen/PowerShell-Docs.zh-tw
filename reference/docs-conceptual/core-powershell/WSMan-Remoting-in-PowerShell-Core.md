# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="0c733-101">PowerShell Core 中的 WS-Management (WSMan) 遠端處理</span><span class="sxs-lookup"><span data-stu-id="0c733-101">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="0c733-102">建立遠端端點的指示</span><span class="sxs-lookup"><span data-stu-id="0c733-102">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="0c733-103">PowerShell Core for Windows 套件包含 `$PSHome` 中的 WinRM 外掛程式 (`pwrshplugin.dll`) 和安裝指令碼 (`Install-PowerShellRemoting.ps1`)。</span><span class="sxs-lookup"><span data-stu-id="0c733-103">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="0c733-104">這些檔案讓 PowerShell 在指定其端點時接受連入的 PowerShell 遠端連線。</span><span class="sxs-lookup"><span data-stu-id="0c733-104">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="0c733-105">動機</span><span class="sxs-lookup"><span data-stu-id="0c733-105">Motivation</span></span>

<span data-ttu-id="0c733-106">PowerShell 安裝可以使用 `New-PSSession` 和 `Enter-PSSession` 建立遠端電腦的 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="0c733-106">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="0c733-107">若要啟用它來接受連入的 PowerShell 遠端連線，使用者必須建立 WinRM 遠端端點。</span><span class="sxs-lookup"><span data-stu-id="0c733-107">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="0c733-108">這是使用者執行 Install-PowerShellRemoting.ps1 建立 WinRM 端點的明確加入案例。</span><span class="sxs-lookup"><span data-stu-id="0c733-108">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="0c733-109">將額外功能新增至 `Enable-PSRemoting` 以執行相同動作之前，安裝指令碼是短期解決方案。</span><span class="sxs-lookup"><span data-stu-id="0c733-109">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="0c733-110">如需詳細資料，請參閱問題 [#1193](https://github.com/PowerShell/PowerShell/issues/1193)。</span><span class="sxs-lookup"><span data-stu-id="0c733-110">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="0c733-111">指令碼動作</span><span class="sxs-lookup"><span data-stu-id="0c733-111">Script Actions</span></span>

<span data-ttu-id="0c733-112">指令碼</span><span class="sxs-lookup"><span data-stu-id="0c733-112">The script</span></span>

1. <span data-ttu-id="0c733-113">在 %windir%\System32\PowerShell 內建立外掛程式的目錄</span><span class="sxs-lookup"><span data-stu-id="0c733-113">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="0c733-114">將 pwrshplugin.dll 複製至該位置</span><span class="sxs-lookup"><span data-stu-id="0c733-114">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="0c733-115">產生設定檔</span><span class="sxs-lookup"><span data-stu-id="0c733-115">Generates a configuration file</span></span>
1. <span data-ttu-id="0c733-116">使用 WinRM 註冊該外掛程式</span><span class="sxs-lookup"><span data-stu-id="0c733-116">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="0c733-117">註冊</span><span class="sxs-lookup"><span data-stu-id="0c733-117">Registration</span></span>

<span data-ttu-id="0c733-118">指令碼必須在系統管理員層級 PowerShell 工作階段內執行，並以兩種模式執行。</span><span class="sxs-lookup"><span data-stu-id="0c733-118">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="0c733-119">透過其將註冊的 PowerShell 執行個體來執行</span><span class="sxs-lookup"><span data-stu-id="0c733-119">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="0c733-120">另一個 PowerShell 執行個體代表其將註冊的執行個體來執行</span><span class="sxs-lookup"><span data-stu-id="0c733-120">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="0c733-121">例如：</span><span class="sxs-lookup"><span data-stu-id="0c733-121">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="0c733-122">**注意：** 遠端註冊指令碼將重新啟動 WinRM，因此所有現有 PSRP 工作階段會在指令碼執行之後立即終止。</span><span class="sxs-lookup"><span data-stu-id="0c733-122">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="0c733-123">如果在遠端工作階段期間執行，這會終止連線。</span><span class="sxs-lookup"><span data-stu-id="0c733-123">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="0c733-124">如何連線至新端點</span><span class="sxs-lookup"><span data-stu-id="0c733-124">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="0c733-125">指定 `-ConfigurationName "some endpoint name"`，以建立與新 PowerShell 端點的新 PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="0c733-125">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="0c733-126">若要連線至上述範例中的 PowerShell 執行個體，請使用：</span><span class="sxs-lookup"><span data-stu-id="0c733-126">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="0c733-127">請注意，未指定 `-ConfigurationName` 的 `New-PSSession` 和 `Enter-PSSession` 引動過程將會以預設 PowerShell 端點 `microsoft.powershell` 為目標。</span><span class="sxs-lookup"><span data-stu-id="0c733-127">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>