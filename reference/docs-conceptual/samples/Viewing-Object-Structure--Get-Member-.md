---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 檢視物件結構 Get Member
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058840"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="29e3f-103">檢視物件結構 (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="29e3f-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="29e3f-104">因為物件在 Windows PowerShell 中播放這類重要角色，所以有數個設計成使用任意物件類型的原生命令。</span><span class="sxs-lookup"><span data-stu-id="29e3f-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="29e3f-105">最重要的是 **Get-Member** 命令。</span><span class="sxs-lookup"><span data-stu-id="29e3f-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="29e3f-106">分析命令所傳回物件的最簡單技巧是將該命令的輸出傳送到 **Get-Member** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="29e3f-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="29e3f-107">**Get-Member** Cmdlet 顯示物件類型的正式名稱以及其成員的完整清單。</span><span class="sxs-lookup"><span data-stu-id="29e3f-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="29e3f-108">所傳回元素的數目有時可能非常龐大。</span><span class="sxs-lookup"><span data-stu-id="29e3f-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="29e3f-109">例如，Process 物件可以有 100 位以上的成員。</span><span class="sxs-lookup"><span data-stu-id="29e3f-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="29e3f-110">若要查看 Process 物件的所有成員，並將輸出分頁，以檢視其所有內容，請輸入︰</span><span class="sxs-lookup"><span data-stu-id="29e3f-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="29e3f-111">此命令的輸出看起來如下︰</span><span class="sxs-lookup"><span data-stu-id="29e3f-111">The output from this command will look something like this:</span></span>

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

<span data-ttu-id="29e3f-112">我們可以篩選想要查看的元素，以讓這份長資訊清單更為有用。</span><span class="sxs-lookup"><span data-stu-id="29e3f-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="29e3f-113">**Get-Member** 命令可讓您只列出為屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="29e3f-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="29e3f-114">有數種形式的屬性。</span><span class="sxs-lookup"><span data-stu-id="29e3f-114">There are several forms of properties.</span></span> <span data-ttu-id="29e3f-115">如果我們將 **Get-Member MemberType** 參數設為值 **Properties**，則這個 Cmdlet 會顯示任何類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="29e3f-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="29e3f-116">產生的清單仍然很長，但更容易管理︰</span><span class="sxs-lookup"><span data-stu-id="29e3f-116">The resulting list is still very long, but a bit more manageable:</span></span>

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> <span data-ttu-id="29e3f-117">MemberType 的允許值是 AliasProperty、CodeProperty、Property、NoteProperty、ScriptProperty、Properties、PropertySet、Method、CodeMethod、ScriptMethod、Methods、ParameterizedProperty、MemberSet 和 All。</span><span class="sxs-lookup"><span data-stu-id="29e3f-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="29e3f-118">處理序有 60 個以上的屬性。</span><span class="sxs-lookup"><span data-stu-id="29e3f-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="29e3f-119">Windows PowerShell 通常僅顯示任何已知物件之少數屬性的原因，在於顯示其所有項目將會產生無法管理的資訊量。</span><span class="sxs-lookup"><span data-stu-id="29e3f-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="29e3f-120">Windows PowerShell 使用名稱結尾為 .format.ps1xml 的 XML 檔案中所儲存的資訊，來決定如何顯示物件類型。</span><span class="sxs-lookup"><span data-stu-id="29e3f-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="29e3f-121">Process 物件 (即 .NET System.Diagnostics.Process 物件) 的格式資料儲存在 DotNetTypes.format.ps1xml 中。</span><span class="sxs-lookup"><span data-stu-id="29e3f-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="29e3f-122">如果您需要查看 Windows PowerShell 預設所顯示屬性以外的屬性，則需要自行格式化輸出資料。</span><span class="sxs-lookup"><span data-stu-id="29e3f-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="29e3f-123">使用格式 Cmdlet 來完成這個動作。</span><span class="sxs-lookup"><span data-stu-id="29e3f-123">This can be done by using the format cmdlets.</span></span>