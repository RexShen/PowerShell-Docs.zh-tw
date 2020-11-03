---
description: 描述隱藏的關鍵字，它會從預設的 Get-Member 結果中隱藏類別成員。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hidden?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hidden
ms.openlocfilehash: 7a8646f1b88da9b42ef26ccdf1d27eaa7042abd7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206732"
---
# <a name="about_hidden"></a><span data-ttu-id="adcb3-104">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="adcb3-104">about_Hidden</span></span>

## <a name="short-description"></a><span data-ttu-id="adcb3-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="adcb3-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="adcb3-106">描述隱藏的關鍵字，它會從預設的 Get-Member 結果中隱藏類別成員。</span><span class="sxs-lookup"><span data-stu-id="adcb3-106">Describes the Hidden keyword, which hides class members from default Get-Member results.</span></span>

## <a name="long-description"></a><span data-ttu-id="adcb3-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="adcb3-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="adcb3-108">當您在腳本中使用 Hidden 關鍵字時，預設會隱藏類別的成員。</span><span class="sxs-lookup"><span data-stu-id="adcb3-108">When you use the Hidden keyword in a script, you hide the members of a class by default.</span></span> <span data-ttu-id="adcb3-109">Hidden 關鍵字可以隱藏屬性、方法 (包括函式、事件、別名屬性和其他成員類型，包括靜態成員、Get-Member Cmdlet 的預設結果，以及從 IntelliSense 和 tab 鍵自動完成結果。</span><span class="sxs-lookup"><span data-stu-id="adcb3-109">The Hidden keyword can hide properties, methods (including constructors, events, alias properties, and other member types, including static members, from the default results of the Get-Member cmdlet, and from IntelliSense and tab completion results.</span></span> <span data-ttu-id="adcb3-110">若要顯示您以 Hidden 關鍵字隱藏的成員，請將-Force 參數新增至 Get-Member 命令。</span><span class="sxs-lookup"><span data-stu-id="adcb3-110">To display members that you have hidden with the Hidden keyword, add the -Force parameter to a Get-Member command.</span></span>

<span data-ttu-id="adcb3-111">除非在定義隱藏成員的類別中發生完成，否則不會使用 tab 鍵自動完成或 IntelliSense 來顯示隱藏的成員。</span><span class="sxs-lookup"><span data-stu-id="adcb3-111">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="adcb3-112">已新增新的屬性 >system.management.automation.hiddenattribute，因此 C 程式 \# 代碼在 PowerShell 內可以有相同的語法。</span><span class="sxs-lookup"><span data-stu-id="adcb3-112">A new attribute, System.Management.Automation.HiddenAttribute, has been added, so that C\# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="adcb3-113">Hidden 關鍵字適合用來建立類別中的屬性和方法，而您不一定希望類別的其他使用者能夠看到或立即能夠編輯。</span><span class="sxs-lookup"><span data-stu-id="adcb3-113">The Hidden keyword is useful for creating properties and methods within a class that you do not necessarily want other users of the class to see, or readily be able to edit.</span></span>

<span data-ttu-id="adcb3-114">Hidden 關鍵字並不會影響您如何查看或變更類別的成員。</span><span class="sxs-lookup"><span data-stu-id="adcb3-114">The Hidden keyword has no effect on how you can view or make changes to members of a class.</span></span> <span data-ttu-id="adcb3-115">如同 PowerShell 中的所有語言關鍵字，隱藏並不區分大小寫，而且隱藏成員仍然是公用的。</span><span class="sxs-lookup"><span data-stu-id="adcb3-115">Like all language keywords in PowerShell, Hidden is not case-sensitive, and hidden members are still public.</span></span>

<span data-ttu-id="adcb3-116">PowerShell 5.0 中引進了隱藏的和自訂類別。</span><span class="sxs-lookup"><span data-stu-id="adcb3-116">Hidden, along with custom classes, was introduced in PowerShell 5.0.</span></span>

## <a name="example"></a><span data-ttu-id="adcb3-117">範例</span><span class="sxs-lookup"><span data-stu-id="adcb3-117">EXAMPLE</span></span>

<span data-ttu-id="adcb3-118">下列範例顯示如何在類別定義中使用 Hidden 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="adcb3-118">The following example shows how to use the Hidden keyword in a class definition.</span></span> <span data-ttu-id="adcb3-119">Car 類別方法（磁片磁碟機）具有不需要觀看或變更的屬性乘車點， (只會計算在 Car 類別上呼叫該磁片磁碟機的次數，而對類別使用者而言不重要的計量，例如，假設您在購買汽車時，不會向賣方要求車輛有多少磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="adcb3-119">The Car class method, Drive, has a property, rides, that does not need to be viewed or changed (it merely tallies the number of times that Drive is called on the Car class, a metric that is not important to users of the class; consider, for example, that when you are buying a car, you do not ask the seller on how many drives the car has been taken.</span></span>

<span data-ttu-id="adcb3-120">由於類別的使用者不需要變更這個屬性，因此我們可以使用 Hidden 關鍵字來隱藏 Get-Member 的屬性和自動完成結果。</span><span class="sxs-lookup"><span data-stu-id="adcb3-120">Because there is little need for users of the class to change this property, we can hide the property from Get-Member and automatic completion results by using the Hidden keyword.</span></span>

<span data-ttu-id="adcb3-121">在與屬性和其資料類型相同的語句行上輸入 Hidden 關鍵字，以加入該關鍵字。</span><span class="sxs-lookup"><span data-stu-id="adcb3-121">Add the Hidden keyword by entering it on the same statement line as the property and its data type.</span></span> <span data-ttu-id="adcb3-122">雖然關鍵字可以依照任何順序來執行，但使用 Hidden 關鍵字啟動語句可讓您更輕鬆地識別所有已隱藏的成員。</span><span class="sxs-lookup"><span data-stu-id="adcb3-122">Although the keyword can be in any order on this line, starting the statement with the Hidden keyword makes it easier for you later to identify all members that you have hidden.</span></span>

```powershell
class Car
{
   # Properties
   [String] $Color
   [String] $ModelYear
   [int] $Distance

   # Method
   [int] Drive ([int]$miles)
   {
      $this.Distance += $miles
      $this.rides++
      return $this.Distance
   }

   # Hidden property of the Drive method
    hidden [int] $rides = 0
}
```

<span data-ttu-id="adcb3-123">現在，建立汽車類別的新實例，並將它儲存在變數 \$ TestCar 中。</span><span class="sxs-lookup"><span data-stu-id="adcb3-123">Now, create a new instance of the Car class, and save it in a variable, \$TestCar.</span></span>

```powershell
$TestCar = [Car]::new()
```

<span data-ttu-id="adcb3-124">在您建立新的實例之後，請將 $TestCar 變數的內容輸送到取得成員。</span><span class="sxs-lookup"><span data-stu-id="adcb3-124">After you create the new instance, pipe the contents of the $TestCar variable to Get-Member.</span></span> <span data-ttu-id="adcb3-125">請注意，乘車點屬性不在 Get-Member 命令結果中所列出的成員內。</span><span class="sxs-lookup"><span data-stu-id="adcb3-125">Observe that the rides property is not among the members listed in the Get-Member command results.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member

   TypeName: Car

Name        MemberType Definition
----        ---------- ----------
Drive       Method     int Drive(int miles)
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
ToString    Method     string ToString()
Color       Property   string Color {get;set;}
Distance    Property   int Distance {get;set;}
ModelYear   Property   string ModelYear {get;set;}

```

<span data-ttu-id="adcb3-126">現在，請試著再次執行 Get-Member，但這次請新增-Force 參數。</span><span class="sxs-lookup"><span data-stu-id="adcb3-126">Now, try running Get-Member again, but this time, add the -Force parameter.</span></span>
<span data-ttu-id="adcb3-127">請注意，結果會包含隱藏的乘車點屬性，以及其他預設隱藏的成員。</span><span class="sxs-lookup"><span data-stu-id="adcb3-127">Note that the results contain the hidden rides property, among other members that are hidden by default.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member -Force

   TypeName: Car

Name          MemberType   Definition
----          ----------   ----------
pstypenames   CodeProperty System.Collections.ObjectModel.Collection`1
psadapted     MemberSet    psadapted {Color, ModelYear, Distance,
psbase        MemberSet    psbase {Color, ModelYear, Distance,...
psextended    MemberSet    psextended {}
psobject      MemberSet    psobject {BaseObject, Members,...
Drive         Method       int Drive(int miles)
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
get_Color     Method       string get_Color()
get_Distance  Method       int get_Distance()
get_ModelYear Method       string get_ModelYear()
get_rides     Method       int get_rides()
set_Color     Method       void set_Color(string )
set_Distance  Method       void set_Distance(int )
set_ModelYear Method       void set_ModelYear(string )
set_rides     Method       void set_rides(int )
ToString      Method       string ToString()
Color         Property     string Color {get;set;}
Distance      Property     int Distance {get;set;}
ModelYear     Property     string ModelYear {get;set;}
rides         Property     int rides {get;set;}

```

## <a name="see-also"></a><span data-ttu-id="adcb3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adcb3-128">SEE ALSO</span></span>

[<span data-ttu-id="adcb3-129">about_Classes</span><span class="sxs-lookup"><span data-stu-id="adcb3-129">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="adcb3-130">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="adcb3-130">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="adcb3-131">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="adcb3-131">about_Wildcards</span></span>](about_Wildcards.md)

[<span data-ttu-id="adcb3-132">Get-Member</span><span class="sxs-lookup"><span data-stu-id="adcb3-132">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

