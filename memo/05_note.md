# TS Enum & Literal type

- Enum은 연관된 아이템들을 함께 묶어서 표현 할 수 있는 수단 입니다.
- Enum은 JS로 컴파일 하게 되면 코드가 구현되어 JS에 나타납니다.
- 즉 Enum은 런타임에 존재하는 실제 객체라는 것을 보여 줍니다.

```ts
// Enum을 타입으로 사용하기 위해 먼저 선언합니다.
enum GenderType {
  Male,
  Female,
}

// Enum이 JS로 컴파일 될 경우
// 밑에처럼 변환이 됩니다.
GenderType[GenderType["Male"] = 0] = "Male";
GenderType[GenderType["Female"] = 1] = "Female";

// 위의 JS로 컴파일 되었을 때 나타나는 코드를 통하여
// Enum으로 정의 하였을 때
// Male = 0, Female = 1의 값을 가지는 것을 알 수 있습니다.
// 이 부분이 숫자 열거형(Numeric Enum)입니다.
// 그러나 만약에 Male이 숫자 값이 아닌 String의 값을 가지도록 하기 위해서는
// Enum 속의 멤버들에게 각각의 값을 할당해 주면 됩니다.
// 이것이 String Enum 입니다.
// String Enum은 Numeric Enum 처럼 자동 증가하는 기능은 없지만 코드를 실행 할 때 조금 더 읽기 쉬운 값을 주는 장점이 있습니다.
enum GenderType {
  Male = "male",
  Female = "female",
}

interface Student {
  studentID: number;
  studentName: string;
  age: number;
  gender: GenderType; // Enum을 사용하기 위해 인터페이스의 프로퍼티의 타입을 GenderType으로 바꿉니다.
  subject: string;
  courseCompleted: boolean;
}

function getStudentDetails(studentID: number): Student {
    return {
        ...
        gender: GenderType.Male  // 이렇게 사용합니다.
    }
}

// 이번엔 Enum 말고 다른 방식으로 GenderType의 Property 값을 제한하는 방법을 알아 보겠습니다.
// 바로 Literal type입니다.
// Enum 보다 심플한 방법입니다.
interface Student {
  studentID: number;
  studentName: string;
  age: number;
  gender: 'male' | 'female'
  subject: string;
  courseCompleted: boolean;
}

function getStudentDetails(studentID: number): Student {
    return {
        ...
        gender: 'male'  // 이렇게 사용합니다.
    }
}
```
