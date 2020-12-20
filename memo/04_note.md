# 타입으로 사용되는 인터페이스

- 지난 시간에 함수의 반한되는 객체의 타입을 지정해 보았습니다.
- 그런데 인터페이스를 적용해 조금 더 깔끔하게 할 수 있습니다.
- TS의 인터페이스는 JS에서 아무런 영향력이 없기 때문에 JS로 컴파일 되는 과정에서 삭제 되어집니다.
- 즉 인터페이스는 작성중인 코드에 대한 더 많은 정보를 TS에 제공하기 위해 존재합니다.
- 이렇게 타입에 대한 정보가 많이 제공될 수록 실수를 찾는데 도움이 됩니다.
- 인터페이스를 사용 함으로써 객체에 포함된 내용과 객체의 동작 방식에 대해서 정확하게 묘사 할 수 있습니다.

```ts
let x: sting = "나는 영원한 문자열";

let studentID: number = 12345;
let studentName: string = "freeko";
let age: number = 29;
let gender: string = "male";
let subject: string = "JS";
let courseCompleted: boolean = false;

// 인터페이스를 타입으로 만들어 주기 위해 인터페이스를 만들어 줍니다.
// 완성된 인터페이스는 타입으로 사용 가능합니다.
interface Student {
  studentID: number;
  studentName: string;
  age: number; // age?: number 이렇게 작성하게 되면 밑에 함수의 반환된 값에 age가 있어도 되고 없어도 됩니다.(선택적 Property)
  gender: string;
  subject: string;
  courseCompleted: boolean;
}

// 함수의 반환되는 타입을 인터페이스로 적용해 줍니다.
// 인터페이스를 타입으로 가지는 값은 인터페이스의 구조를 그 값으로 가지도록 강제 됩니다.
// 즉 함수의 결과로 반환되는 값은 인터페이스 정의로 된 값으로 반환되어야 하는 뜻 입니다.
// 예를 들어 return 값에 'hello'라고 하면 에러가 생깁니다.
function getStudentDetails(studentID: number): Student {
  return {
    studentID: 123456,
    studentName: "freeko",
    age: 29, // 만약에 age를 미포함 시키면 TS에서 반환되는 값에 age가 없다고 이야기 해줍니다.(위에서 age 옆에 '?'없는 경우)
    gender: "male",
    subject: "NodeJS",
    courseCompleted: true,
  };
}

// Student 인터페이스를 재사용했습니다. 즉 코드의 재사용이 가능합니다.
function saveStudentDetails(student: Student): void {}

// 직접 오브젝트를 함수의 인자로 집어 넣으는 것도 가능하지만
saveStudentDetails({
  studentID: 12121212,
  studentName: "Ju",
  age: 22,
  gender: "female",
  subject: "JS",
  courseCompleted: false,
});

// 따로 학생의 오브젝트를 선언해 그 선언한 변수만 함수의 인자로 넣는 것도 가능 합니다.
let student1 = {
  studentID: 12121212,
  studentName: "Ju",
  age: 22,
  gender: "female",
  subject: "JS",
  courseCompleted: false,
};

saveStudentDetails(student1);

// 지금까지 Property에 만 인터페이스를 적용하였습니다.
// 그러나 인터페이스 안에 Method를 정의 할 수 있습니다.
// 메소드(Method)는 객체 내에서 선언된 함수 입니다.
// 메소드를 인터페이스 안에 정의하는 방법은 2가지가 있습니다.
// 첫 번째는 직접적으로 기입하는 방법과
// 두 번째는 에로우 함수를 사용 하는 것 입니다.
// 표현만 다를 뿐 기능은 같습니다.
interface Student {
    ...
    addComment (comment: string): string;
    addComment: (comment: string) => string;
    addComment?: (comment: string) => string;  // '?'를 붙이게 되면 선택적인 메소드가 됩니다.
}

// Readonly Property는 읽기 전용 프로퍼티로 객체 생성시 할당된 프로터티의 값을 바꿀 수 없습니다.
// 밑에 처럼 작성한 뒤에
let student1 = {
    readonly studentID: 12121212,
    ...
};

function saveStudentDetails(student: Student): void {
    // 이렇게 속성 값을 변경하는 코드를 작성하게 되면 에러가 발생합니다.
    // 그 이유는 인터페이스 내에서 studentID 를 readonly 라고 지정했기 때문입니다.
    // 즉 readonly로 지정하게 되면 새로운 값을 할당 할 수 없습니다.
    student.studentID = 111113;
}

```
