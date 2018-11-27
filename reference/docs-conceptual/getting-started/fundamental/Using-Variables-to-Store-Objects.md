---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 使用變數儲存物件
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: d166ec58dc658c1b134030c9a9592249ee40d4f5
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320953"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="1c967-103">使用變數儲存物件</span><span class="sxs-lookup"><span data-stu-id="1c967-103">Using variables to store objects</span></span>

<span data-ttu-id="1c967-104">PowerShell 可以搭配物件來使用。</span><span class="sxs-lookup"><span data-stu-id="1c967-104">PowerShell works with objects.</span></span> <span data-ttu-id="1c967-105">PowerShell 可讓您建立稱為變數的具名物件。</span><span class="sxs-lookup"><span data-stu-id="1c967-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="1c967-106">變數名稱可以包含底線字元和任何英數字元。</span><span class="sxs-lookup"><span data-stu-id="1c967-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="1c967-107">在 PowerShell 中使用時，變數一律使用 \$ 字元後面接著變數名稱來指定。</span><span class="sxs-lookup"><span data-stu-id="1c967-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="1c967-108">建立變數</span><span class="sxs-lookup"><span data-stu-id="1c967-108">Creating a variable</span></span>

<span data-ttu-id="1c967-109">您可以輸入有效的變數名稱來建立變數︰</span><span class="sxs-lookup"><span data-stu-id="1c967-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="1c967-110">此範例不會傳回任何結果，因為 `$loc` 沒有值。</span><span class="sxs-lookup"><span data-stu-id="1c967-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="1c967-111">您可以在相同的步驟中建立變數並指派其值。</span><span class="sxs-lookup"><span data-stu-id="1c967-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="1c967-112">PowerShell 只有在變數不存在時才會加以建立。</span><span class="sxs-lookup"><span data-stu-id="1c967-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="1c967-113">否則，它會將指定的值指派給現有變數。</span><span class="sxs-lookup"><span data-stu-id="1c967-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="1c967-114">下列範例會將目前的位置儲存在變數 `$loc` 中：</span><span class="sxs-lookup"><span data-stu-id="1c967-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="1c967-115">當您輸入此命令時，PowerShell 不會顯示任何輸出。</span><span class="sxs-lookup"><span data-stu-id="1c967-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="1c967-116">PowerShell 會將 'Get-location' 的輸出傳送到 `$loc`。</span><span class="sxs-lookup"><span data-stu-id="1c967-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="1c967-117">在 PowerShell 中，會將未指派或重新導向的資料傳送到畫面。</span><span class="sxs-lookup"><span data-stu-id="1c967-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="1c967-118">輸入 `$loc` 會顯示您的目前位置：</span><span class="sxs-lookup"><span data-stu-id="1c967-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="1c967-119">您可以使用 `Get-Member` 來顯示變數內容的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1c967-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="1c967-120">`Get-Member` 會顯示 `$loc` 為 **PathInfo** 物件，就像來自 `Get-Location` 的輸出：</span><span class="sxs-lookup"><span data-stu-id="1c967-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="1c967-121">操作變數</span><span class="sxs-lookup"><span data-stu-id="1c967-121">Manipulating variables</span></span>

<span data-ttu-id="1c967-122">PowerShell 提供數個命令來操作變數。</span><span class="sxs-lookup"><span data-stu-id="1c967-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="1c967-123">您可以查看可讀取形式的完整清單，方法是輸入︰</span><span class="sxs-lookup"><span data-stu-id="1c967-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="1c967-124">PowerShell 也會建立數個系統定義的變數。</span><span class="sxs-lookup"><span data-stu-id="1c967-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="1c967-125">您可以使用 `Remove-Variable` Cmdlet，從目前的工作階段移除所有不受 PowerShell 控制的變數。</span><span class="sxs-lookup"><span data-stu-id="1c967-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="1c967-126">輸入下列命令以清除所有變數：</span><span class="sxs-lookup"><span data-stu-id="1c967-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="1c967-127">執行上一個命令之後，`Get-Variable` Cmdlet 會顯示 PowerShell 系統變數。</span><span class="sxs-lookup"><span data-stu-id="1c967-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="1c967-128">PowerShell 也會建立變數磁碟機。</span><span class="sxs-lookup"><span data-stu-id="1c967-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="1c967-129">使用下列範例，利用變數磁碟機來顯示所有 PowerShell 變數：</span><span class="sxs-lookup"><span data-stu-id="1c967-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="1c967-130">使用 Cmd.exe 變數</span><span class="sxs-lookup"><span data-stu-id="1c967-130">Using cmd.exe variables</span></span>

<span data-ttu-id="1c967-131">PowerShell 可以使用可供任何 Windows 處理序 (包括 **cmd.exe**) 使用的相同環境變數。</span><span class="sxs-lookup"><span data-stu-id="1c967-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="1c967-132">這些變數會透過名為 `env:` 的磁碟機來公開。</span><span class="sxs-lookup"><span data-stu-id="1c967-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="1c967-133">您可以輸入下列命令來檢視這些變數：</span><span class="sxs-lookup"><span data-stu-id="1c967-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="1c967-134">標準的 `*-Variable` Cmdlet 不是設計來使用環境變數。</span><span class="sxs-lookup"><span data-stu-id="1c967-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="1c967-135">環境變數可以使用 `env:` 磁碟機前置詞來存取。</span><span class="sxs-lookup"><span data-stu-id="1c967-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="1c967-136">例如，**cmd.exe** 中的 **%SystemRoot%** 變數包含作業系統的根目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="1c967-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="1c967-137">在 PowerShell 中，您會使用 `$env:SystemRoot` 來存取相同的值。</span><span class="sxs-lookup"><span data-stu-id="1c967-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="1c967-138">您也可以從 PowerShell 建立和修改環境變數。</span><span class="sxs-lookup"><span data-stu-id="1c967-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="1c967-139">PowerShell 中的環境變數會遵循在作業系統中其他地方所使用之環境變數的相同規則。</span><span class="sxs-lookup"><span data-stu-id="1c967-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="1c967-140">下列範例會建立新的環境變數：</span><span class="sxs-lookup"><span data-stu-id="1c967-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="1c967-141">雖然並非必要，但通常會針對環境變數名稱全部使用大寫字母。</span><span class="sxs-lookup"><span data-stu-id="1c967-141">Though not required, is it common for environment variable names to use all uppercase letters.</span></span>
