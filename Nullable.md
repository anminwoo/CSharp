```c#
Nullable<T>: true, false, null
bool: true, false;

줄임 표현은 bool?, int? 형식으로 null 가능 형식을 만들 수 있다.
```

| 주요 멤버         | 뜻                                       |
| ----------------- | ---------------------------------------- |
| HasValue 속성     | 값이 있으면 true, null 값이면 false 반환 |
| Value 속성        | 값 반환                                  |
| GetValueOrDefault | 값 또는 기본 값 반환                     |



```c#
using System;
using System.Linq;
class HelloWorld {
  static void Main() {
      string nullValue = null;
      string message = "";

      nullValue = null;
      if(nullValue == null)
      {
          message = "nullValue is null";
      }
      Console.WriteLine(message);

      message = nullValue ?? "nullValue is null"; // 피연산자가 null일 때 오른쪽 피연산자 반환, 아닐 때 왼쪽 피연산자 반환
      Console.WriteLine(message);
  }
}
```



```c#
using System;
using System.Linq;
class HelloWorld {
  static void Main() {
      string value = null;
      string message = "";
      message = value ?? "값이 없어 기본값으로 대체하였습니다.";
      Console.WriteLine(message);
      value = "값이 있다";
      message = value ?? "값이 없습니다.";
      Console.WriteLine(message);
  }
}
```

특정 변수 값이 null이라면 오른쪽 값으로 초기화 되고, 이미 값을 가지고 있다면 해당 값을 사용한다.



```c#
using System;
using System.Linq;
class HelloWorld {
  static void Main() {
      int? len;
      string message;

      message = null;
      len = message?.Length;
      Console.WriteLine(len);

      message = "Hello";
      len = message ?.Length;
      Console.WriteLine(len);
  }
}
```

문자열 변수 message의 값이 null 이라면 **?.** 을 실행했을 때 null을 반환하고, 값이 있다면 **?.** 뒤에 있는 속성 또는 메서드를 실행한다. **?[]** 형태로 배열 또는 인덱서에도 사용할 수 있다.

---

#### null 조건부 연산자와 null 병합 연산자 함께 사용

```c#
using System;
using System.Collections.Generic;
using System.Linq;
class HelloWorld {
  static void Main() {
      int num;
      List<string> list;

      list = null;
      num = list?.Count ?? 0; // null 이면 0 반환, 오른쪽 값을 사용함.
      Console.WriteLine(num); // 0

      list = new List<string>();
      list.Add("Added"); // 값 추가
      num = list?.Count ?? 0; // null 이 아님. 왼쪽 값 list.Count 사용함.
      Console.WriteLine(num); // 1
  }
}
```

