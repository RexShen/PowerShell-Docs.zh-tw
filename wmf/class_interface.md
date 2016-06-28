# 宣告實作的介面

如未指定基底類型，您可以在基底類型之後或緊跟在冒號 (:) 之後宣告實作的介面。 使用逗號分隔所有類型名稱。 非常類似 C# 語法。

```PowerShell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

<!--HONumber=Jun16_HO4-->


