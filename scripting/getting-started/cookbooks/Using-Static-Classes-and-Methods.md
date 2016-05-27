---
title:  使用靜態類別和方法
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  418ad766-afa6-4b8c-9a44-471889af7fd9
---

# 使用靜態類別和方法
使用 **New-Object** 並無法建立所有 .NET Framework 類別。 例如，如果您嘗試使用 **New-Object** 來建立 **System.Environment** 或 **System.Math** 物件，則會收到下列錯誤訊息︰

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment
PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

這些錯誤的發生原因是沒有方法可透過這些類別建立新的物件。 這些類別是未變更狀態之方法和屬性的參考程式庫。 您不需要建立它們，而只需要使用它們。 這類類別和方法稱為*靜態類別*，因為不會建立、破壞或變更它們。 為了讓這個概念更為清楚，我們將提供使用靜態類別的範例。

### 使用 System.Environment 取得環境資料
通常，在 Windows PowerShell 中使用物件的第一個步驟是使用 Get-Member 來找出它包含的成員。 運用靜態類別時，處理方式會有些不同，因為實際類別不是物件。

#### 參考靜態 System.Environment 類別
使用方括弧括住類別名稱，即可參考靜態類別。 例如，在方括弧內輸入名稱，即可參考 **System.Environment**。 這麼做會顯示一些泛型類型資訊︰

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> 如前所述，Windows PowerShell 會自動將 '**System.**' 加到類型名稱的前面 (使用 **New-Object** 時)。 使用以方括弧括住的類型名稱時會發生相同的作業，因此您可以將 **[System.Environment]** 指定為 **[Environment]**。

**System.Environment** 類別包含目前處理處序之運作環境的一般資訊 (在 Windows PowerShell 內運作時為 powershell.exe)。

如果您輸入 **[System.Environment] | Get-Member** 來嘗試檢視這個類別的詳細資訊，則物件類型會回報為 **System.RuntimeType**，而非 **System.Environment**：

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

若要使用 Get-Member 來檢視靜態成員，請指定 **Static** 參數︰

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

我們現在可以從 System.Environment 中選取要檢視的屬性。

#### 顯示 System.Environment 的靜態屬性
System.Environment 的屬性也是靜態的，而且指定的方式必須與一般屬性不同。 我們使用 **::** 向 Windows PowerShell 表示我們想要使用靜態方法或屬性。 若要查看已用來啟動 Windows PowerShell 的命令，我們會檢查 **CommandLine** 屬性，方法是輸入︰

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

若要檢查作業系統版本，請顯示 OSVersion 屬性，方法是輸入︰

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

顯示 **HasShutdownStarted** 屬性，即可檢查電腦是否正在進行關機：

```
PS> [System.Environment]::HasShutdownStarted
False
```

### 使用 System.Math 執行數學運算
System.Math 靜態類別適用於執行一些數學運算。 **System.Math** 的重要成員主要是方法，而使用 **Get-Member** 即可顯示這些方法。

> [!NOTE] System.Math 有數種同名的方法，但透過其參數的類型予以區分。

輸入下列命令來列出 **System.Math** 類別的方法。

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

這會顯示數個數學方法。 以下是示範一些常見方法之運作方式的命令清單 ︰

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```



<!--HONumber=May16_HO2-->


