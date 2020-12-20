# TS의 특징

- Static Typing(정적 타이핑)을 JS에 제공합니다.
- Static Typing이란 타입을 선언 하고 선언된 파일에 맞는 값만 할당 또는 반환 되어야 한다는 뜻입니다.
- 타입 추론(Type Inference), 타입 명시(Type Annotations)가 존재 합니다
- TS는 타입 표기가 없는 경우 코드를 스스로 읽고 분석하여 타입을 유추해 낼 수 있습니다. (타입추론)

<br>

### 타입 추론(Type Inference)

```ts
<app.ts>
let a = 5;

// 이렇게 재 할당 할 경우 에러 메세지가 뜨게 됩니다.
// 이러한 이유는 타입 추론 때문입니다.
// 위에서 변수를 선언 할 때 할당된 값이 숫자 5 이기 때문에
// 밑에 동일한 변수에 무언가를 할당 할 때 타입을 선언하지 않으면 위에서 선언한 타입을 추론하여 a의 타입은 숫자로 결정 됩니다.
// 그런데 추론한 변수 a의 타입이 숫자인데 갑자기 문자열을 할당하면 당연히 에러가 뜨게 됩니다.
a = "hello";

let student = {
    nanme: 'FREE',
    course: 'Getting Started with TypeScript',
    codingIQ: 120,
    code: function() {
        console.log('Brain is working hard');
    }
}

// 밑 경우 타입 추론으로 인해 에러가 뜹니다.
// 이미 객체 안의 Property의 타입을 TS가 읽고 분석하여 추론을 끝냈습니다.
// 그렇기 때문에 Property Name의 타입은 String이기 때문에 밑에 에러가 뜹니다.
student.name = 10;

```
