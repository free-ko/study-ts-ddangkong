# 타입 명시

- 변수를 선언 할 때 선언 할 때, 변수 값의 타입을 명시함으로써 변수 값의 데이터 타입을 지정합니다.

```ts
let x: sting = "나는 영원한 문자열";

let studentID: number = 12345;
let studentName: string = "freeko";
let age: number = 29;
let gender: string = "male";
let subject: string = "JS";
let courseCompleted: boolean = false;

// void는 반환된 값이 없다는 의미 입니다.
// 함수에 반환된 값의 타입이 object라 해놓고 함수 안에 아무것도 작성하지 않으면 에러가 뜨게 됩니다.
// 대신 return null 이라고 함수 안에 작성하면 에러는 사라집니다.
// TS에서 타입을 많이 적용시켜 주면 유지 보수 하기가 쉬워집니다.
// 밑에 함수에서 예를 들어 Object를 반환 할 때에 Object 안에 Property의 타입까지 명시해 주면 좋습니다.
function getStudentDetails(
  studentID: number
): {
  // 이렇게 반환되는 객체의 구조를 타입으로 지정 할 수 있습니다.
  studentID: number;
  studentName: string;
  age: number;
  gender: string;
  subject: string;
  courseCompleted: boolean;
} {
  return null;
}
```
