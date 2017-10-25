---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "取得命令的相關資訊"
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="b56b2-103">取得命令的相關資訊</span><span class="sxs-lookup"><span data-stu-id="b56b2-103">Getting Information About Commands</span></span>
<span data-ttu-id="b56b2-104">Windows PowerShell **Get-Command** Cmdlet 能取得您目前工作階段中所有可用的命令。</span><span class="sxs-lookup"><span data-stu-id="b56b2-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="b56b2-105">當您在 Windows PowerShell 命令提示字元輸入 **Get-Command** 時，您會看到如下輸出：</span><span class="sxs-lookup"><span data-stu-id="b56b2-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="b56b2-106">此輸出與 Cmd.exe 的「說明」輸出 (內部命令的表格式摘要) 十分相似。</span><span class="sxs-lookup"><span data-stu-id="b56b2-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="b56b2-107">如上面 **Get-Command** 命令輸出的摘要所示，每個顯示的命令都有一個屬於 Cmdlet 的 CommandType。</span><span class="sxs-lookup"><span data-stu-id="b56b2-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="b56b2-108">Cmdlet 是 Windows PowerShell 的內建命令類型，大致上是對應到 Cmd.exe 的 **dir** 和 **cd** 命令，以及 UNIX 殼層的內建項 (例如 BASH)。</span><span class="sxs-lookup"><span data-stu-id="b56b2-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="b56b2-109">在 **Get-Command** 命令的輸出中，所有定義的結尾都是省略符號 (...)，表示 PowerShell 無法在可用空間內顯示所有內容。</span><span class="sxs-lookup"><span data-stu-id="b56b2-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="b56b2-110">當 Windows PowerShell 顯示輸出時，它會將輸出格式化為文字，並將其排列以在視窗中整齊地顯示。</span><span class="sxs-lookup"><span data-stu-id="b56b2-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="b56b2-111">我們將稍後在格式化相關的章節中討論此內容。</span><span class="sxs-lookup"><span data-stu-id="b56b2-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="b56b2-112">**Get-Command** Cmdlet 具有一個可取得各 Cmdlet 語法的 **Syntax** 參數。</span><span class="sxs-lookup"><span data-stu-id="b56b2-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="b56b2-113">若要取得 Get-Help Cmdlet 的語法，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="b56b2-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="b56b2-114">**Get-Command Get-Help -Syntax**</span><span class="sxs-lookup"><span data-stu-id="b56b2-114">**Get-Command Get-Help -Syntax**</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="b56b2-115">顯示可用的命令類型</span><span class="sxs-lookup"><span data-stu-id="b56b2-115">Displaying Available Command Types</span></span>
<span data-ttu-id="b56b2-116">**Get-Command** 命令不會列出 Windows PowerShell 中所有可用的命令。</span><span class="sxs-lookup"><span data-stu-id="b56b2-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="b56b2-117">反之，**Get-Command** 命令只會列出目前工作階段中的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b56b2-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="b56b2-118">Windows PowerShell 實際上支援一些其他類型的命令。</span><span class="sxs-lookup"><span data-stu-id="b56b2-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="b56b2-119">雖然 Windows PowerShell 使用者手冊中沒有詳細討論別名、函式與指令碼，但它們也是 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="b56b2-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="b56b2-120">可執行或具有已登錄檔案類型處理常式的外部檔案，也分類為命令。</span><span class="sxs-lookup"><span data-stu-id="b56b2-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="b56b2-121">若要取得工作階段中的所有命令，請輸入：</span><span class="sxs-lookup"><span data-stu-id="b56b2-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="b56b2-122">因為此清單包含您搜尋路徑中的外部檔案，其中可能會有數千個項目。</span><span class="sxs-lookup"><span data-stu-id="b56b2-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="b56b2-123">所以查看一組精簡過的命令會更實用。</span><span class="sxs-lookup"><span data-stu-id="b56b2-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="b56b2-124">若要取得其他類型的原生命令，請使用 **Get-Command** Cmdlet 的 **CommandType** 參數。</span><span class="sxs-lookup"><span data-stu-id="b56b2-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="b56b2-125">星號 (\*) 在 Windows PowerShell 命令引數中用於萬用字元比對。</span><span class="sxs-lookup"><span data-stu-id="b56b2-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="b56b2-126">\* 表示「符合一或多個任意字元」。</span><span class="sxs-lookup"><span data-stu-id="b56b2-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="b56b2-127">您可以輸入 **Get-Command a\&#42;** 來尋找開頭為字母 "a" 的所有命令。</span><span class="sxs-lookup"><span data-stu-id="b56b2-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="b56b2-128">與 Cmd.exe 中萬用字元比對不同的是，Windows PowerShell 的萬用字元也會比對句號。</span><span class="sxs-lookup"><span data-stu-id="b56b2-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="b56b2-129">若要取得命令別名 (指派給命令的暱稱)，請輸入：</span><span class="sxs-lookup"><span data-stu-id="b56b2-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="b56b2-130">若要取得目前工作階段中的函式，請輸入：</span><span class="sxs-lookup"><span data-stu-id="b56b2-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="b56b2-131">若要顯示 Windows PowerShell 搜尋路徑中的指令碼，請輸入：</span><span class="sxs-lookup"><span data-stu-id="b56b2-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```

