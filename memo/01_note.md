```ts
// VSCode 내부에서 tsconfig가 없을 경우 에러가 생깁니다.
// 이때 터미널에 tsc --init을 실행하면 tsconfig파일이 생성되면서 해결이 됩니다.
// 또한 ts파일이 실시간으로 변경 되었을 때 자동적으로 컴파일 하는 방법은 터미널에 tsc-w를 실행하면 됩니다. (w = Watch)
function logName(name: string) {
  console.log(name);
}

logName("FREEKO");
```
