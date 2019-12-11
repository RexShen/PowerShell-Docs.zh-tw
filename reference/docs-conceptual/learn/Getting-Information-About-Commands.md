---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 取得命令的相關資訊
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030953"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="38b08-103">取得命令的相關資訊</span><span class="sxs-lookup"><span data-stu-id="38b08-103">Getting information about commands</span></span>

<span data-ttu-id="38b08-104">PowerShell `Get-Command` 會顯示您目前工作階段中的所有可用命令。</span><span class="sxs-lookup"><span data-stu-id="38b08-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="38b08-105">當您執行 `Get-Command` Cmdlet 時，您會看到如下輸出：</span><span class="sxs-lookup"><span data-stu-id="38b08-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="38b08-106">此輸出與 **cmd.exe** 的 Help 輸出十分相似：內部命令的表格式摘要。</span><span class="sxs-lookup"><span data-stu-id="38b08-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="38b08-107">如上面 `Get-Command` 命令輸出的摘要所示，每個顯示的命令都有一個屬於 Cmdlet 的 CommandType。</span><span class="sxs-lookup"><span data-stu-id="38b08-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="38b08-108">Cmdlet 是 PowerShell 的內建命令類型。</span><span class="sxs-lookup"><span data-stu-id="38b08-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="38b08-109">此類型大致上對應至 **cmd.exe** 中 `dir` 與 `cd` 之類的命令，或是 Unix 殼層 (例如 Bash) 的內建命令。</span><span class="sxs-lookup"><span data-stu-id="38b08-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="38b08-110">`Get-Command` Cmdlet 有一個 **Syntax** 參數，可傳回每個 Cmdlet 的語法。</span><span class="sxs-lookup"><span data-stu-id="38b08-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="38b08-111">下列範例示範如何取得 `Get-Help` Cmdlet 的語法：</span><span class="sxs-lookup"><span data-stu-id="38b08-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="38b08-112">依類型顯示可用的命令</span><span class="sxs-lookup"><span data-stu-id="38b08-112">Displaying available command by type</span></span>

<span data-ttu-id="38b08-113">`Get-Command` 命令只會列出目前工作階段中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="38b08-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="38b08-114">PowerShell 實際上支援數個其他類型的命令：</span><span class="sxs-lookup"><span data-stu-id="38b08-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="38b08-115">別名</span><span class="sxs-lookup"><span data-stu-id="38b08-115">Aliases</span></span>
- <span data-ttu-id="38b08-116">函式</span><span class="sxs-lookup"><span data-stu-id="38b08-116">Functions</span></span>
- <span data-ttu-id="38b08-117">指令碼</span><span class="sxs-lookup"><span data-stu-id="38b08-117">Scripts</span></span>

<span data-ttu-id="38b08-118">外部可執行檔案或具有已登錄之檔案類型處理常式的檔案，也會分類為命令。</span><span class="sxs-lookup"><span data-stu-id="38b08-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="38b08-119">若要取得工作階段中的所有命令，請輸入：</span><span class="sxs-lookup"><span data-stu-id="38b08-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="38b08-120">此清單包含您搜尋路徑中的外部命令，因此會包含數千個項目。</span><span class="sxs-lookup"><span data-stu-id="38b08-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="38b08-121">所以查看一組精簡過的命令會更實用。</span><span class="sxs-lookup"><span data-stu-id="38b08-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="38b08-122">星號 (\*) 會用於 PowerShell 命令引數中的萬用字元比對。</span><span class="sxs-lookup"><span data-stu-id="38b08-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="38b08-123">\* 表示「符合一或多個任意字元」。</span><span class="sxs-lookup"><span data-stu-id="38b08-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="38b08-124">您可以鍵入 `Get-Command a*` 來尋找開頭為字母 "a" 的所有命令。</span><span class="sxs-lookup"><span data-stu-id="38b08-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="38b08-125">不同於 **cmd.exe** 中的萬用字元比對，PowerShell 的萬用字元也會比對句點。</span><span class="sxs-lookup"><span data-stu-id="38b08-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="38b08-126">使用 `Get-Command` 的 **CommandType** 參數來取得其他類型的原生命令。</span><span class="sxs-lookup"><span data-stu-id="38b08-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="38b08-127">Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="38b08-127">cmdlet.</span></span>

<span data-ttu-id="38b08-128">若要取得命令別名 (指派給命令的暱稱)，請輸入：</span><span class="sxs-lookup"><span data-stu-id="38b08-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="38b08-129">若要取得目前工作階段中的函式，請輸入：</span><span class="sxs-lookup"><span data-stu-id="38b08-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="38b08-130">若要顯示 PowerShell 搜尋路徑中的指令碼，請輸入：</span><span class="sxs-lookup"><span data-stu-id="38b08-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
