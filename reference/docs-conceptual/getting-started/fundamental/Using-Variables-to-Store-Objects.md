---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用變數儲存物件"
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 067948d7c234fb70c7cf9966c9ae3e8df1f99757
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="8386a-103">使用變數儲存物件</span><span class="sxs-lookup"><span data-stu-id="8386a-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="8386a-104">Windows PowerShell 使用物件。</span><span class="sxs-lookup"><span data-stu-id="8386a-104">Windows PowerShell works with objects.</span></span> <span data-ttu-id="8386a-105">Windows PowerShell 可讓您建立基本上為具名物件的變數，以保留輸出供之後使用。</span><span class="sxs-lookup"><span data-stu-id="8386a-105">Windows PowerShell lets you create variables - essentially named objects - to preserve output to use later.</span></span> <span data-ttu-id="8386a-106">如果您是用來使用其他殼層中的變數，請記得 Windows PowerShell 變數是物件，而非文字。</span><span class="sxs-lookup"><span data-stu-id="8386a-106">If you are used to working with variables in other shells, remember that Windows PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="8386a-107">變數一律會指定起始字元 $，而且可以在其名稱中包括任何英數字元或底線。</span><span class="sxs-lookup"><span data-stu-id="8386a-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="8386a-108">建立變數</span><span class="sxs-lookup"><span data-stu-id="8386a-108">Creating a Variable</span></span>
<span data-ttu-id="8386a-109">您可以輸入有效的變數名稱來建立變數︰</span><span class="sxs-lookup"><span data-stu-id="8386a-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="8386a-110">這不會傳回任何結果，因為 **$loc** 沒有值。</span><span class="sxs-lookup"><span data-stu-id="8386a-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="8386a-111">您可以在相同的步驟中建立變數並指派其值。</span><span class="sxs-lookup"><span data-stu-id="8386a-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="8386a-112">Windows PowerShell 只會建立不存在的變數；否則，它會將指定的值指派給現有變數。</span><span class="sxs-lookup"><span data-stu-id="8386a-112">Windows PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="8386a-113">若要將您的目前位置儲存在變數 **$loc** 中，請輸入：</span><span class="sxs-lookup"><span data-stu-id="8386a-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="8386a-114">輸入這個命令時未顯示任何輸出，因為輸出會傳送至 $loc。</span><span class="sxs-lookup"><span data-stu-id="8386a-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="8386a-115">在 Windows PowerShell 中，顯示的輸出是下列事實的副作用：未指示的資料一律會傳送至螢幕。</span><span class="sxs-lookup"><span data-stu-id="8386a-115">In Windows PowerShell, displayed output is a side effect of the fact that data which is not otherwise directed always gets sent to the screen.</span></span> <span data-ttu-id="8386a-116">輸入 $loc 將顯示目前的位置：</span><span class="sxs-lookup"><span data-stu-id="8386a-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="8386a-117">您可以使用 **Get-Member** 顯示變數內容的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8386a-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="8386a-118">將 $loc 傳送到 Get-Member 將顯示它是 **PathInfo** 物件，就像 Get-Location 的輸出一樣：</span><span class="sxs-lookup"><span data-stu-id="8386a-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="8386a-119">操作變數</span><span class="sxs-lookup"><span data-stu-id="8386a-119">Manipulating Variables</span></span>
<span data-ttu-id="8386a-120">Windows PowerShell 提供數個命令來操作變數。</span><span class="sxs-lookup"><span data-stu-id="8386a-120">Windows PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="8386a-121">您可以查看可讀取形式的完整清單，方法是輸入︰</span><span class="sxs-lookup"><span data-stu-id="8386a-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="8386a-122">除了您在目前 Windows PowerShell 工作階段中建立的變數之外，還有數個系統定義的變數。</span><span class="sxs-lookup"><span data-stu-id="8386a-122">In addition to the variables you create in your current Windows PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="8386a-123">您可以使用 **Remove-Variable** Cmdlet 來清除所有不受 Windows PowerShell 控制的變數。</span><span class="sxs-lookup"><span data-stu-id="8386a-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by Windows PowerShell.</span></span> <span data-ttu-id="8386a-124">輸入下列命令以清除所有變數：</span><span class="sxs-lookup"><span data-stu-id="8386a-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="8386a-125">這將產生您在下面看到的確認提示。</span><span class="sxs-lookup"><span data-stu-id="8386a-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="8386a-126">如果您之後執行 **Get-Variable** Cmdlet，則會看到其餘的 Windows PowerShell 變數。</span><span class="sxs-lookup"><span data-stu-id="8386a-126">If you then run the **Get-Variable** cmdlet, you will see the remaining Windows PowerShell variables.</span></span> <span data-ttu-id="8386a-127">因為也有變數 Windows PowerShell 磁碟機，所以您也可以顯示所有 Windows PowerShell 變數，方法是輸入︰</span><span class="sxs-lookup"><span data-stu-id="8386a-127">Since there is also a variable Windows PowerShell drive, you can also display all Windows PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="8386a-128">使用 Cmd.exe 變數</span><span class="sxs-lookup"><span data-stu-id="8386a-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="8386a-129">雖然 Windows PowerShell 不是 Cmd.exe，但是會在命令殼層環境中執行，而且可以在 Windows 的任何環境中使用相同的變數。</span><span class="sxs-lookup"><span data-stu-id="8386a-129">Although Windows PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="8386a-130">這些變數是透過名為 **env** 的磁碟機公開：</span><span class="sxs-lookup"><span data-stu-id="8386a-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="8386a-131">您可以檢視這些變數，方法是輸入︰</span><span class="sxs-lookup"><span data-stu-id="8386a-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="8386a-132">雖然標準變數 Cmdlet 未設計成使用 **env:** 變數，但是您仍然可以指定 **env:** 前置詞來使用它們。</span><span class="sxs-lookup"><span data-stu-id="8386a-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="8386a-133">例如，若要查看作業系統根目錄，您可以從 Windows PowerShell 使用命令殼層 **%SystemRoot%** 變數，方法是輸入︰</span><span class="sxs-lookup"><span data-stu-id="8386a-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within Windows PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="8386a-134">您也可以從 Windows PowerShell 建立和修改環境變數。</span><span class="sxs-lookup"><span data-stu-id="8386a-134">You can also create and modify environment variables from within Windows PowerShell.</span></span> <span data-ttu-id="8386a-135">從 Windows PowerShell 存取的環境變數符合 Windows 中其他位置之環境變數的一般規則。</span><span class="sxs-lookup"><span data-stu-id="8386a-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>
