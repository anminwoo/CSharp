`params`를 사용하여 가변 인자를 받을 수 있다.

단, 일반적인 매개변수와 함께 사용할 때는 마지막에 사용해야한다.

```c#
using System;

class HelloWorld {
  static void Main() {
      Console.WriteLine(SumAll(1, 3, 5));
      Console.WriteLine(SumAll(2, 4, 6));
      Console.WriteLine(SumAll(8, 9, 10));
    }

    static int SumAll(params int[] numbers)
    {
        int sum = 0;
        foreach(int number in numbers)
        {
            sum += number;
        }
        return sum;
    }
}
```

