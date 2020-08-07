---
title: PowerShell 脚本性能注意事项
description: 在 PowerShell 中编写性能脚本
ms.topic: article
ms.author: jasonsh
author: lzybkr
ms.date: 10/16/2017
ms.openlocfilehash: f5ab7fbb1c993192f4626935d2adb73fc9401250
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87896258"
---
# <a name="powershell-scripting-performance-considerations"></a>PowerShell 脚本性能注意事项

直接利用 .NET 并避免管道的 PowerShell 脚本的速度要快于惯用 PowerShell。 惯用 PowerShell 通常使用 cmdlet 和 PowerShell 函数，通常利用管道，并且仅在必要时才会将其放入 .NET。

>[!Note]
> 此处所述的许多方法并不惯用 PowerShell，可能降低 PowerShell 脚本的可读性。 建议编写作者使用惯用 PowerShell，除非性能决定。

## <a name="suppressing-output"></a>禁止输出

有多种方法可避免将对象写入管道：

```PowerShell
$null = $arrayList.Add($item)
[void]$arrayList.Add($item)
```

对 `$null` 或强制转换到 `[void]` 的操作大致等效，通常应优先于性能重要。

```PowerShell
$arrayList.Add($item) > $null
```

文件重定向 `$null` 几乎与以前的替代方法一样好，大多数脚本都不会注意到差异。
不过，文件重定向会稍微增加一些开销。

```PowerShell
$arrayList.Add($item) | Out-Null
```

`Out-Null`与替代方法相比，管道与其他方法相比有显著的开销。
它应避免对性能敏感的代码的影响。

```PowerShell
$null = . {
    $arrayList.Add($item)
    $arrayList.Add(42)
}
```

引入脚本块并使用点 (或其他) 将其调用，然后将结果分配给 `$null` 是一种用于取消大型脚本块输出的便利方法。
此方法大致适用于和管道， `Out-Null` 应避免在性能敏感的脚本中。
此示例中的额外开销来自于创建和调用以前内联脚本的脚本块。


## <a name="array-addition"></a>数组加法

通常使用带有加法运算符的数组来生成项列表：

```PowerShell
$results = @()
$results += Do-Something
$results += Do-SomethingElse
$results
```

由于数组是不可变的，因此这可能非常 inefficent。
对于数组的每个加法，实际上会创建一个足以容纳左操作数和右操作数的所有元素的新数组，然后将这两个操作数的元素复制到新数组中。
对于小型集合，这种开销可能并不重要。
对于大型集合，这可能是一个问题。

有一些替代方法。
如果实际上不需要数组，请考虑使用 ArrayList：

```PowerShell
$results = [System.Collections.ArrayList]::new()
$results.AddRange((Do-Something))
$results.AddRange((Do-SomethingElse))
$results
```

如果确实需要数组，则可以使用自己的， `ArrayList` 只需 `ArrayList.ToArray` 在需要数组时调用。
或者，你可以让 PowerShell `ArrayList` `Array` 为你创建和：

```PowerShell
$results = @(
    Do-Something
    Do-SomethingElse
)
```

在此示例中，PowerShell 创建一个 `ArrayList` 来保存写入到数组表达式中的管道的结果。
在将分配到之前 `$results` ，PowerShell 会将转换 `ArrayList` 为 `object[]` 。

## <a name="processing-large-files"></a>处理大型文件

在 PowerShell 中处理文件的惯用方法可能如下所示：

```PowerShell
Get-Content $path | Where-Object { $_.Length -gt 10 }
```

这可能比直接使用 .NET Api 时的数量级慢：

```PowerShell
try
{
    $stream = [System.IO.StreamReader]::new($path)
    while ($line = $stream.ReadLine())
    {
        if ($line.Length -gt 10)
        {
            $line
        }
    }
}
finally
{
    $stream.Dispose()
}
```

## <a name="avoid-write-host"></a>避免写入主机

通常情况下，将输出直接写入控制台通常是一种很好的做法，但当有意义时，很多脚本会使用 `Write-Host` 。

如果必须将多条消息写入控制台，则 `Write-Host` 的阶数可能比低 `[Console]::WriteLine()` 。 但请注意， `[Console]::WriteLine()` 只是特定主机（如 powershell.exe 或 powershell_ise.exe）的一种合适的替代方法，这不能保证在所有主机中都能正常工作。

请不要使用 `Write-Host` ，而应考虑使用[写入输出](/powershell/module/Microsoft.PowerShell.Utility/Write-Output?view=powershell-5.1)。

