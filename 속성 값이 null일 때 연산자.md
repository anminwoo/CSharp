```c#
using static System.Console;
using System;
using static System.Math;
using System.Collections.Generic;
using System.Linq;

namespace NullWithObject
{
    class Person
    {
        public string Name {get; set;}
        public Address Address {get; set;}
    }

    class Address
    {
        public string Street {get; set;} = "unkwown";
    }

    class NullWithObject
    {
        static void Main()
        {
            var people = new Person[] {new Person {Name = "안민우"}, null};

            ProcessPeople(people);

            void ProcessPeople(IEnumerable<Person> peopleArray)
            {
                foreach (var person in peopleArray)
                {
                    WriteLine($"{person?.Name ?? "아무개"}은(는) {person?.Address?.Street ?? "아무곳"}에 삽니다.");
                }
            }

            var otherPeople = null as Person[];

            WriteLine($"첫 번째 사람: {otherPeople?[0]?.Name ?? "없음"}");

        }
    }
}
```

person?.Name 형태로 null이 아니라면 person.Name 속성을 사용, 아니라면 ?? 뒤에 있는 "아무개"를 반환함.

?[0] 이런식으로 인덱서가 null인지 아닌지 확인 할 수 있다.