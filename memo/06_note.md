# Any, Union Type, Type Aliases & Type Guards

<br>

```ts
// 타입에 Any를 작성 할 경우 어떠한 타입이든 모두 OK이라는 뜻 입니다. (타입 체크 안 하겠다는 의미 입니다.)
// 예를 들어 어떤 타입든 상관없이 추가적으로 변수에 새로운 값들을 할당 할 수 있습니다.
// 그러나 많은 타입의 정보를 지정해야 나중에 유지 보수 하기가 편합니다.
// 그러기 때문에 any 타입의 사용을 지양하면 좋습니다.
// 그러나 작업 중인 코드의 타입 명시가 어려운 경우
// 예를 들어 서드 파티 라이브러리에서 동적 콘텐츠를 가지고와 프로그램 작성시 변수에 타입을 알 수 없어서 타입을 지정할 수 없는 경우
// 이러한 경우에만 제한적으로 any 타입을 사용하면 좋습니다.
let someValue: any;
someValue = "hello";
someValue = true;

// 변수 타입이 무조건 숫자 아니면 문자열로 동시에 지정하고 싶을 때
// 이 때에 Uion Type이라고 불리우는 테크닉을 사용 할 수 있습니다.
// 예를 들어
let price: number | string = 5;
price = "free";
price = false; // 이렇게 하게 되면 오류가 뜨게 됩니다.

// 같은 조합이 계속 반복될 경우 어떻게 코드를 향상 시킬 수 있을까요?
// 즉 숫자 or 문자열 타입을 동시에 가지는 변수가 여러군데 있다고 하면 어떻게 하면 좋을까요?
// 이럴 때에는 코드를 타입으로 지정하고 재활용 하는것이 좋습니다.
// 이 때 Type Aliases를 사용 합니다.
// 예를 들어밑에 처럼 키워드를 사용하여 새로운 타입을 정의 하는 것이 Type Aliasses입니다.
type StrOrNum = string | number;

let totalCost: number;
let orderID: StrOrNum;

const calculateTotalCost = (price:StrOrNum, qty: number): void => {

};

const findOrderID = (customer: {costomerId: StrOrNum, name: string}, productId: StrOrNum): StrOrNum => {
    return orderID;
})

// Type Guards

// 밑에 타입은 Uion Type입니다.
type StringOrNum = string | number;
let itemPrice: number;

const setItemPrice = (price: StringOrNum): void => {
    // itemPrice에 에러 메세지가 뜹니다.
    // 그 이유는 price의 매개변수의 타입이 문자열 혹은 숫자열이 될 수 있기 때문입니다.
    // 혹여 price에 문자열이 할당되는 경우 itemPrice는 숫자 타입으로 지정되어 있기 때문에 에러가 뜨는 것 입니다. (즉 만약의 상황을 염두해서 에러 메세지가 뜬다고 볼 수 있습니다.)
    // 만약에 price에 문자열이 할당되는 경우 어떻게 문제를 해결 할 수 있을까요?
    // 바로 JS에 내장되어 있는 typeof Operator를 사용합니다.
    // Typeof 연산자와 조건문을 함께 사용 함으로써 이러한 문제가 되는 코드를 고칠 수 있습니다.
    itemPrice = price;
};

// 해결해 보겠습니다.
// 이렇게 Uion Type을 사용 할 때 typeof를 사용 하여 코드 검증을 수행하는 것을 TS에서 Type Guard라고 합니다.
// 타입 가드의 방식은 여러게 있으니 검색해 보세요
const setItemPrice = (price: StringOrNum): void => {
    // typeof 연산자는 변수의 데이터 타입을 반환하는 연산자 입니다.
    if(typeof price === 'string') {
        itemPrice = 0;
    } else if {
        itemPrice = price;
    }
};

setItemPrice(50);

```

<br>

참고 블로그  
https://velog.io/@zeros0623/TypeScript-%EA%B3%A0%EA%B8%89-%ED%83%80%EC%9E%85
