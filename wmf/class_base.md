# 宣告基底類別
您可以將 Windows PowerShell 類別宣告為另一個 Windows PowerShell 類別的基底類型。

```PowerShell
class bar
{
   [int]foo() 
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

現有的 .NET Framework 類型也可以用作為基底類別︰

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```<!--HONumber=Mar16_HO2-->
