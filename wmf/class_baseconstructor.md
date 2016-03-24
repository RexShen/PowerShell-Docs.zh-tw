# 呼叫基底類別建構函式

若要從子類別中呼叫基底類別建構函式，請使用關鍵字 **base**：

```PowerShell
class A 
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

如果基底類別有預設的 (無參數) 建構函式，您可以省略明確的建構函式呼叫︰

```PowerShell
class C : B
{
    C([int]$c) {}
}
```<!--HONumber=Mar16_HO2-->
