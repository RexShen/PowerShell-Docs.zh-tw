---
title: 格式、別名、提供者、比較
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: 本章介紹輸出格式、命令別名、提供者和比較作業的概念。
ms.openlocfilehash: efe70d2d220f8451e781603b6000c3553dda910c
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501604"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a><span data-ttu-id="b8ec2-103">第 5 章 - 格式、別名、提供者、比較</span><span class="sxs-lookup"><span data-stu-id="b8ec2-103">Chapter 5 - Formatting, aliases, providers, comparison</span></span>

## <a name="requirements"></a><span data-ttu-id="b8ec2-104">需求</span><span class="sxs-lookup"><span data-stu-id="b8ec2-104">Requirements</span></span>

<span data-ttu-id="b8ec2-105">本章所示的部分範例需要 SQL Server PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-105">The SQL Server PowerShell module is required by some of the examples shown in this chapter.</span></span> <span data-ttu-id="b8ec2-106">模組會安裝為 [SQL Server Management Studio (SMSS)][SMSS] 的一部分。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-106">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="b8ec2-107">後續章節也會用到它。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-107">It's also used in subsequent chapters.</span></span> <span data-ttu-id="b8ec2-108">將它下載並安裝在您的 Windows 10 實驗室環境電腦上。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-108">Download and install it on your Windows 10 lab environment computer.</span></span>

## <a name="format-right"></a><span data-ttu-id="b8ec2-109">右側格式化</span><span class="sxs-lookup"><span data-stu-id="b8ec2-109">Format Right</span></span>

<span data-ttu-id="b8ec2-110">在第 4 章中，您已了解如何盡可能地篩選左側。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-110">In Chapter 4, you learned to filter as far to the left as possible.</span></span> <span data-ttu-id="b8ec2-111">手動格式化命令輸出的規則類似於該規則，但它必須盡可能地出現在最右邊。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-111">The rule for manually formatting a command's output is similar to that rule except it needs to occur as far to the right as possible.</span></span>

<span data-ttu-id="b8ec2-112">最常見的格式化命令是 `Format-Table` 和 `Format-List`。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-112">The most common format commands are `Format-Table` and `Format-List`.</span></span> <span data-ttu-id="b8ec2-113">也可以使用 `Format-Wide` 和 `Format-Custom`，但較不常見。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-113">`Format-Wide` and `Format-Custom` can also be used, but are less common.</span></span>

<span data-ttu-id="b8ec2-114">如第 3 章中所述，除非使用自訂格式，否則傳回四個以上屬性的命令會預設為清單。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-114">As mentioned in Chapter 3, a command that returns more than four properties defaults to a list unless custom formatting is used.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="b8ec2-115">使用 `Format-Table` Cmdlet 來手動覆寫格式，並將輸出以資料表顯示，而不是清單。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-115">Use the `Format-Table` cmdlet to manually override the formatting and show the output in a table instead of a list.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

<span data-ttu-id="b8ec2-116">`Get-Service` 的預設輸出是資料表中的三個屬性。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-116">The default output for `Get-Service` is three properties in a table.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="b8ec2-117">使用 `Format-List` Cmdlet 來覆寫預設格式，並以清單傳回結果。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-117">Use the `Format-List` cmdlet to override the default formatting and return the results in a list.</span></span>

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

<span data-ttu-id="b8ec2-118">請注意，只要將 `Get-Service` 以管線傳送至 `Format-List` 就可讓它傳回其他屬性。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-118">Notice that simply piping `Get-Service` to `Format-List` made it return additional properties.</span></span> <span data-ttu-id="b8ec2-119">由於在幕後對該特定命令的格式設定方式，並非每個命令都可執行此動作。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-119">This doesn't occur with every command because of the way the formatting for that particular command is set up behind the scenes.</span></span>

<span data-ttu-id="b8ec2-120">使用格式化 Cmdlet 必須注意的第一件事便是，它們會產生與 PowerShell 中一般物件不同的格式化物件。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-120">The number one thing to be aware of with the format cmdlets is they produce format objects that are different than normal objects in PowerShell.</span></span>

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

<span data-ttu-id="b8ec2-121">這表示格式化命令無法以管線傳送至大部分的其他命令。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-121">What this means is format commands can't be piped to most other commands.</span></span> <span data-ttu-id="b8ec2-122">它們可以透過管線傳送至一些 `Out-*` 命令，就這些。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-122">They can be piped to some of the `Out-*` commands, but that's about it.</span></span> <span data-ttu-id="b8ec2-123">這就是為什麼您想要在行尾執行任何格式設定 (格式化右側)。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-123">This is why you want to perform any formatting at the very end of the line (format right).</span></span>

## <a name="aliases"></a><span data-ttu-id="b8ec2-124">別名</span><span class="sxs-lookup"><span data-stu-id="b8ec2-124">Aliases</span></span>

<span data-ttu-id="b8ec2-125">PowerShell 中的別名是命令的較短名稱。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-125">An alias in PowerShell is a shorter name for a command.</span></span> <span data-ttu-id="b8ec2-126">PowerShell 包含一組內建的別名，您也可以定義自己的別名。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-126">PowerShell includes a set of built-in aliases and you can also define your own aliases.</span></span>

<span data-ttu-id="b8ec2-127">`Get-Alias` Cmdlet 可用來尋找別名。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-127">The `Get-Alias` cmdlet is used to find aliases.</span></span> <span data-ttu-id="b8ec2-128">如果您已知道命令的別名，則會使用 **Name** 參數來判斷別名所關聯的命令。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-128">If you already know the alias for a command, the **Name** parameter is used to determine what command the alias is associated with.</span></span>

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

<span data-ttu-id="b8ec2-129">可以為 **Name** 參數的值指定多個別名。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-129">Multiple aliases can be specified for the value of the **Name** parameter.</span></span>

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="b8ec2-130">您通常會看到 **Name** 參數已省略，因為它是位置參數。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-130">You'll often see the **Name** parameter omitted since it's a positional parameter.</span></span>

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

<span data-ttu-id="b8ec2-131">如果您想要尋找命令的別名，則必須使用 **Definition** 參數。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-131">If you want to find aliases for a command, you'll need to use the **Definition** parameter.</span></span>

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="b8ec2-132">**Definition** 參數無法依位置使用，因此必須指定它。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-132">The **Definition** parameter can't be used positionally so it must be specified.</span></span>

<span data-ttu-id="b8ec2-133">別名可以讓您省去一些按鍵輸入的時間，而且當您將命令輸入主控台時，其可正常運作。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-133">Aliases can save you a few keystrokes and they're fine when you're typing commands into the console.</span></span>
<span data-ttu-id="b8ec2-134">它們不應該用於指令碼或您要儲存或與其他人共用的任何程式碼中。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-134">They shouldn't be used in scripts or any code that you're saving or sharing with others.</span></span> <span data-ttu-id="b8ec2-135">如本書稍早所述，使用完整的 Cmdlet 和參數名稱是自我說明且易於了解的。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-135">As mentioned earlier in this book, using full cmdlet and parameter names is self-documenting and easier to understand.</span></span>

<span data-ttu-id="b8ec2-136">建立自己的別名時請務必小心，因為它們只會存在於您電腦上目前的 PowerShell 工作階段中。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-136">Use caution when creating your own aliases because they'll only exist in your current PowerShell session on your computer.</span></span>

## <a name="providers"></a><span data-ttu-id="b8ec2-137">提供者</span><span class="sxs-lookup"><span data-stu-id="b8ec2-137">Providers</span></span>

<span data-ttu-id="b8ec2-138">PowerShell 中的提供者是介面，會允許對資料存放區執行類似檔案系統的存取。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-138">A provider in PowerShell is an interface that allows file system like access to a datastore.</span></span> <span data-ttu-id="b8ec2-139">PowerShell 中有許多內建提供者。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-139">There are a number of built-in providers in PowerShell.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

<span data-ttu-id="b8ec2-140">如您在先前的結果中所見，有一些用於登錄、別名、環境變數、檔案系統、函式、變數、憑證和 WSMan 的內建提供者。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-140">As you can see in the previous results, there are built-in providers for the registry, aliases, environment variables, the file system, functions, variables, certificates, and WSMan.</span></span>

<span data-ttu-id="b8ec2-141">這些提供者用來公開其資料存放區的實際磁碟機，可以使用 `Get-PSDrive` Cmdlet 來判斷。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-141">The actual drives that these providers use to expose their datastore can be determined with the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="b8ec2-142">`Get-PSDrive` Cmdlet 不只會顯示提供者所公開的磁碟機，還會顯示 Windows 邏輯磁碟機，包括與網路共用對應的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-142">The `Get-PSDrive` cmdlet not only displays drives exposed by providers, but it also displays Windows logical drives including drives mapped to network shares.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="b8ec2-143">協力廠商模組 (例如 Active Directory PowerShell 模組和 SQLServer PowerShell 模組) 都會新增自己的 PowerShell 提供者和 PSDrive。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-143">Third-party modules such as the Active Directory PowerShell module and the SQLServer PowerShell module both add their own PowerShell provider and PSDrive.</span></span>

<span data-ttu-id="b8ec2-144">匯入 Active Directory 和 SQL Server PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-144">Import the Active Directory and SQL Server PowerShell modules.</span></span>

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

<span data-ttu-id="b8ec2-145">檢查以了解是否已新增任何其他 PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-145">Check to see if any additional PowerShell providers were added.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

<span data-ttu-id="b8ec2-146">請注意，在先前的結果集中，現在存在兩個新的 PowerShell 提供者，一個用於 Active Directory，另一個則用於 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-146">Notice that in the previous set of results, two new PowerShell providers now exist, one for Active Directory and another one for SQL Server.</span></span>

<span data-ttu-id="b8ec2-147">也針對每個模組新增了一個 PSDrive。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-147">A PSDrive for each of those modules was also added.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="b8ec2-148">您可以如傳統檔案系統般存取 PSDrive。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-148">PSDrives can be accessed just like a traditional file system.</span></span>

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a><span data-ttu-id="b8ec2-149">比較運算子</span><span class="sxs-lookup"><span data-stu-id="b8ec2-149">Comparison Operators</span></span>

<span data-ttu-id="b8ec2-150">PowerShell 包含一些比較運算子，用來比較值或尋找符合特定模式的值。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-150">PowerShell contains a number of comparison operators that are used to compare values or find values that match certain patterns.</span></span> <span data-ttu-id="b8ec2-151">資料表 5-1 包含 PowerShell 中比較運算子的清單。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-151">Table 5-1 contains a list of comparison operators in PowerShell.</span></span>

|    <span data-ttu-id="b8ec2-152">運算子</span><span class="sxs-lookup"><span data-stu-id="b8ec2-152">Operator</span></span>    |                          <span data-ttu-id="b8ec2-153">定義</span><span class="sxs-lookup"><span data-stu-id="b8ec2-153">Definition</span></span>                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | <span data-ttu-id="b8ec2-154">等於</span><span class="sxs-lookup"><span data-stu-id="b8ec2-154">Equal to</span></span>                                                     |
| `-ne`          | <span data-ttu-id="b8ec2-155">不等於</span><span class="sxs-lookup"><span data-stu-id="b8ec2-155">Not equal to</span></span>                                                 |
| `-gt`          | <span data-ttu-id="b8ec2-156">大於</span><span class="sxs-lookup"><span data-stu-id="b8ec2-156">Greater than</span></span>                                                 |
| `-ge`          | <span data-ttu-id="b8ec2-157">大於或等於</span><span class="sxs-lookup"><span data-stu-id="b8ec2-157">Greater than or equal to</span></span>                                     |
| `-lt`          | <span data-ttu-id="b8ec2-158">小於</span><span class="sxs-lookup"><span data-stu-id="b8ec2-158">Less than</span></span>                                                    |
| `-le`          | <span data-ttu-id="b8ec2-159">小於或等於</span><span class="sxs-lookup"><span data-stu-id="b8ec2-159">Less than or equal to</span></span>                                        |
| `-Like`        | <span data-ttu-id="b8ec2-160">使用 `*` 萬用字元比對</span><span class="sxs-lookup"><span data-stu-id="b8ec2-160">Match using the `*` wildcard character</span></span>                       |
| `-NotLike`     | <span data-ttu-id="b8ec2-161">不符合使用 `*` 萬用字元</span><span class="sxs-lookup"><span data-stu-id="b8ec2-161">Does not match using the `*` wildcard character</span></span>              |
| `-Match`       | <span data-ttu-id="b8ec2-162">比對指定的規則運算式</span><span class="sxs-lookup"><span data-stu-id="b8ec2-162">Matches the specified regular expression</span></span>                     |
| `-NotMatch`    | <span data-ttu-id="b8ec2-163">不符合指定的規則運算式</span><span class="sxs-lookup"><span data-stu-id="b8ec2-163">Does not match the specified regular expression</span></span>              |
| `-Contains`    | <span data-ttu-id="b8ec2-164">判斷集合是否包含指定的值</span><span class="sxs-lookup"><span data-stu-id="b8ec2-164">Determines if a collection contains a specified value</span></span>        |
| `-NotContains` | <span data-ttu-id="b8ec2-165">判斷集合是否不包含特定值</span><span class="sxs-lookup"><span data-stu-id="b8ec2-165">Determines if a collection does not contain a specific value</span></span> |
| `-In`          | <span data-ttu-id="b8ec2-166">判斷指定的值是否在集合中</span><span class="sxs-lookup"><span data-stu-id="b8ec2-166">Determines if a specified value is in a collection</span></span>           |
| `-NotIn`       | <span data-ttu-id="b8ec2-167">判斷指定的值是否不在集合中</span><span class="sxs-lookup"><span data-stu-id="b8ec2-167">Determines if a specified value is not in a collection</span></span>       |
| `-Replace`     | <span data-ttu-id="b8ec2-168">取代指定的值</span><span class="sxs-lookup"><span data-stu-id="b8ec2-168">Replaces the specified value</span></span>                                 |

<span data-ttu-id="b8ec2-169">資料表 5-1 中列出的所有運算子都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-169">All of the operators listed in Table 5-1 are case-insensitive.</span></span> <span data-ttu-id="b8ec2-170">將 `c` 放在資料表 5-1 所列的運算子前面，可使其區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-170">Place a `c` in front of the operator listed in Table 5-1 to make it case-sensitive.</span></span> <span data-ttu-id="b8ec2-171">例如，`-ceq` 是 `-eq` 比較運算子的區分大小寫版本。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-171">For example, `-ceq` is the case-sensitive version of the `-eq` comparison operator.</span></span>

<span data-ttu-id="b8ec2-172">使用等於比較運算子時，適當大小寫 "PowerShell" 會等於小寫 "powershell"。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-172">Proper case "PowerShell" is equal to lower case "powershell" using the equals comparison operator.</span></span>

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

<span data-ttu-id="b8ec2-173">它不等於使用等於比較運算子的區分大小寫版本。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-173">It's not equal using the case-sensitive version of the equals comparison operator.</span></span>

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

<span data-ttu-id="b8ec2-174">不等於比較運算子會反轉條件。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-174">The not equal comparison operator reverses the condition.</span></span>

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

<span data-ttu-id="b8ec2-175">大於、大於或等於、小於，以及小於或等於均可對字串或數值使用。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-175">Greater than, greater than or equal to, less than, and less than or equal all work with string or numeric values.</span></span>

```powershell
5 -gt 5
```

```Output
False
```

<span data-ttu-id="b8ec2-176">對上一個範例使用大於或等於，而不是大於，會傳回 **布林值** true，因為五等於五。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-176">Using greater than or equal to instead of greater than with the previous example returns the **Boolean** true since five is equal to five.</span></span>

```powershell
5 -ge 5
```

```Output
True
```

<span data-ttu-id="b8ec2-177">根據前兩個範例的結果，您也許能猜測小於和小於或等於的運作方式。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-177">Based on the results from the previous two examples, you can probably guess how both less than and less than or equal to work.</span></span>

```powershell
5 -lt 10
```

```Output
True
```

<span data-ttu-id="b8ec2-178">即使是有經驗的 PowerShell 使用者，`-Like` 和 `-Match` 運算子也可能令人混淆。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-178">The `-Like` and `-Match` operators can be confusing, even for experienced PowerShell users.</span></span> <span data-ttu-id="b8ec2-179">`-Like` 會與萬用字元 `*` 和 `?` 搭配使用，以執行 "like" 比對。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-179">`-Like` is used with wildcard the characters `*` and `?` to perform "like" matches.</span></span>

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

<span data-ttu-id="b8ec2-180">`-Match` 使用規則運算式來執行比對。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-180">`-Match` uses a regular expression to perform the matching.</span></span>

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

<span data-ttu-id="b8ec2-181">使用範圍運算子，將數字 1 到 10 儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-181">Use the range operator to store the numbers 1 through 10 in a variable.</span></span>

```powershell
$Numbers = 1..10
```

```Output
```

<span data-ttu-id="b8ec2-182">判斷 `$Numbers` 變數是否包含 15。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-182">Determine if the `$Numbers` variable includes 15.</span></span>

```powershell
$Numbers -contains 15
```

```Output
False
```

<span data-ttu-id="b8ec2-183">判斷它是否包含數字 10。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-183">Determine if it includes the number 10.</span></span>

```powershell
$Numbers -contains 10
```

```Output
True
```

<span data-ttu-id="b8ec2-184">`-NotContains` 會反轉邏輯，以查看 `$Numbers` 變數是否不包含值。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-184">`-NotContains` reverses the logic to see if the `$Numbers` variable doesn't contain a value.</span></span>

```powershell
$Numbers -notcontains 15
```

```Output
True
```

<span data-ttu-id="b8ec2-185">上一個範例會傳回 **布林值** true，因為 `$Numbers` 變數不會包含 15。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-185">The previous example returns the **Boolean** true because it's true that the `$Numbers` variable doesn't contain 15.</span></span> <span data-ttu-id="b8ec2-186">不過，它確定包含數字 10，因此在測試時為 false。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-186">It does however contain the number 10 so it's false when it's tested.</span></span>

```powershell
$Numbers -notcontains 10
```

```Output
False
```

<span data-ttu-id="b8ec2-187">"in" 比較運算子最初是在 PowerShell 3.0 版中推出。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-187">The "in" comparison operator was first introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="b8ec2-188">它是用來判斷值是否「在」陣列中。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-188">It's used to determine if a value is "in" an array.</span></span> <span data-ttu-id="b8ec2-189">`$Numbers` 變數是陣列，因為它包含多個值。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-189">The `$Numbers` variable is an array since it contains multiple values.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="b8ec2-190">換句話說，`-in` 會執行與包含比較運算子相同的測試，但方向相反。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-190">In other words, `-in` performs the same test as the contains comparison operator except from the opposite direction.</span></span>

```powershell
10 -in $Numbers
```

```Output
True
```

<span data-ttu-id="b8ec2-191">15 不在 `$Numbers` 陣列中，因此在下列範例中會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-191">15 isn't in the `$Numbers` array so false is returned in the following example.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="b8ec2-192">就像 `-contains` 運算子一樣，`not` 會反轉 `-in` 運算子的邏輯。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-192">Just like the `-contains` operator, `not` reverses the logic for the `-in` operator.</span></span>

```powershell
10 -notin $Numbers
```

```Output
False
```

<span data-ttu-id="b8ec2-193">上一個範例會傳回 false，因為 `$Numbers` 陣列確實包含 10，而測試條件是要判斷它是否未包含 10。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-193">The previous example returns false because the `$Numbers` array does include 10 and the condition was testing to determine if it didn't contain 10.</span></span>

<span data-ttu-id="b8ec2-194">15「不在」`$Numbers` 陣列中，因此會傳回 **布林值** true。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-194">15 is "not in" the `$Numbers` array so it returns the **Boolean** true.</span></span>

```powershell
15 -notin $Numbers
```

```Output
True
```

<span data-ttu-id="b8ec2-195">`-replace` 運算子只會執行您想要的動作。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-195">The `-replace` operator does just want you would think.</span></span> <span data-ttu-id="b8ec2-196">其用來取代某個項目。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-196">It's used to replace something.</span></span> <span data-ttu-id="b8ec2-197">指定一個值時，將該值取代為空值。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-197">Specifying one value replaces that value with nothing.</span></span> <span data-ttu-id="b8ec2-198">在下列範例中，我將 "Shell" 取代為空值。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-198">In the following example, I replace "Shell" with nothing.</span></span>

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

<span data-ttu-id="b8ec2-199">如果您想要將某個值取代為不同的值，請在您想要取代的模式之後指定該新值。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-199">If you want to replace a value with a different value, specify the new value after the pattern you want to replace.</span></span> <span data-ttu-id="b8ec2-200">巴頓魯治的 SQL 星期六是我每年都會試著談到的事件。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-200">SQL Saturday in Baton Rouge is an event that I try to speak at every year.</span></span> <span data-ttu-id="b8ec2-201">在下列範例中，我將 "Saturday" 這個字取代為縮寫 "Sat"。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-201">In the following example, I replace the word "Saturday" with the abbreviation "Sat".</span></span>

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="b8ec2-202">還有一些 **Replace ()**  之類的方法，可用來取代項目，類似取代運算子的運作方式。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-202">There are also methods like **Replace()** that can be used to replace things similar to the way the replace operator works.</span></span> <span data-ttu-id="b8ec2-203">不過，`-Replace` 運算子預設為不區分大小寫，而 **Replace ()**  方法則區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-203">However, the `-Replace` operator is case-insensitive by default, and the **Replace()** method is case-sensitive.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

<span data-ttu-id="b8ec2-204">請注意，在上一個範例中，並未取代 "Saturday" 這個字。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-204">Notice that the word "Saturday" wasn't replaced in the previous example.</span></span> <span data-ttu-id="b8ec2-205">這是因為指定了與原始不同的大小寫。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-205">This is because it was specified in a different case than the original.</span></span> <span data-ttu-id="b8ec2-206">以與原始相同的大小寫指定 "Saturday" 這個字時， **Replace ()** 方法會如預期般加以取代。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-206">When the word "Saturday" is specified in the same case as the original, the **Replace()** method does replace it as expected.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="b8ec2-207">使用方法來轉換資料時請小心，因為您可能會遇到未預期的問題，例如使得 _土耳其測試_ 失敗。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-207">Be careful when using methods to transform data because you can run into unforeseen problems, such as failing the _Turkey Test_ .</span></span> <span data-ttu-id="b8ec2-208">如需範例，請參閱標題為[使用 Pester 測試 PowerShell 程式碼與其他文化特性][]的部落格文章。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-208">For an example, see the blog article titled [Using Pester to Test PowerShell Code with Other Cultures][].</span></span> <span data-ttu-id="b8ec2-209">我的建議是盡可能使用運算子，而不是方法來避免這些類型的問題。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-209">My recommendation is to use an operator instead of a method whenever possible to avoid these types of problems.</span></span>

<span data-ttu-id="b8ec2-210">雖然可以如先前範例所示使用比較運算子，但我通常會發現自己是使用 `Where-Object` Cmdlet 來執行某種類型的篩選。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-210">While the comparison operators can be used as shown in the previous examples, I normally find myself using them with the `Where-Object` cmdlet to perform some type of filtering.</span></span>

## <a name="summary"></a><span data-ttu-id="b8ec2-211">摘要</span><span class="sxs-lookup"><span data-stu-id="b8ec2-211">Summary</span></span>

<span data-ttu-id="b8ec2-212">在本章中，您已了解一些不同的主題來包含右側格式化、別名、提供者和比較運算子。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-212">In this chapter, you've learned a number of different topics to include Formatting Right, Aliases, Providers, and Comparison Operators.</span></span>

## <a name="review"></a><span data-ttu-id="b8ec2-213">檢閱</span><span class="sxs-lookup"><span data-stu-id="b8ec2-213">Review</span></span>

1. <span data-ttu-id="b8ec2-214">為什麼有必要盡可能執行右側格式化？</span><span class="sxs-lookup"><span data-stu-id="b8ec2-214">Why is it necessary to perform Formatting as far to the right as possible?</span></span>
1. <span data-ttu-id="b8ec2-215">如何判斷用於 `%` 別名的實際 Cmdlet 為何？</span><span class="sxs-lookup"><span data-stu-id="b8ec2-215">How do you determine what the actual cmdlet is for the `%` alias?</span></span>
1. <span data-ttu-id="b8ec2-216">為什麼不應該在您儲存的指令碼或與其他人共用的程式碼中使用別名？</span><span class="sxs-lookup"><span data-stu-id="b8ec2-216">Why shouldn't you use aliases in scripts you save or code you share with others?</span></span>
1. <span data-ttu-id="b8ec2-217">在與其中一個登錄提供者相關聯的磁碟機上執行目錄列出。</span><span class="sxs-lookup"><span data-stu-id="b8ec2-217">Perform a directory listing on the drives that are associated with one of the registry providers.</span></span>
1. <span data-ttu-id="b8ec2-218">使用取代運算子而非 replace 方法的其中一個主要優點是什麼？</span><span class="sxs-lookup"><span data-stu-id="b8ec2-218">What's one of the main benefits of using the replace operator instead of the replace method?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="b8ec2-219">建議閱讀資料</span><span class="sxs-lookup"><span data-stu-id="b8ec2-219">Recommended Reading</span></span>

- <span data-ttu-id="b8ec2-220">[Format-Table][]</span><span class="sxs-lookup"><span data-stu-id="b8ec2-220">[Format-Table][]</span></span>
- <span data-ttu-id="b8ec2-221">[Format-List][]</span><span class="sxs-lookup"><span data-stu-id="b8ec2-221">[Format-List][]</span></span>
- <span data-ttu-id="b8ec2-222">[Format-Wide][]</span><span class="sxs-lookup"><span data-stu-id="b8ec2-222">[Format-Wide][]</span></span>
- <span data-ttu-id="b8ec2-223">[about_Aliases][]</span><span class="sxs-lookup"><span data-stu-id="b8ec2-223">[about_Aliases][]</span></span>
- <span data-ttu-id="b8ec2-224">[about_Providers][]</span><span class="sxs-lookup"><span data-stu-id="b8ec2-224">[about_Providers][]</span></span>
- <span data-ttu-id="b8ec2-225">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ec2-225">[about_Comparison_Operators][]</span></span>
- <span data-ttu-id="b8ec2-226">[about_Arrays][]</span><span class="sxs-lookup"><span data-stu-id="b8ec2-226">[about_Arrays][]</span></span>

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[使用 Pester 測試 PowerShell 程式碼與其他文化特性]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
[Using Pester to Test PowerShell Code with Other Cultures]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
