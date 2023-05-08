# 프론트엔드 컨벤션

HTML, CSS, JAVASCRIPT에 관련된 규칙을 정리한 문서입니다.

1. [HTML](#HTML)
1. [CSS](#CSS)
1. [Javascript](#Javascript)

## HTML

## CSS

## Javascript

1. [상수](#상수)
1. [function](#function)

### 상수

모든 상수는 대문자로 표기한다. 다른 개발자가 객체 구조 할당으로 사용하더라도 상수라는 것을 명확히 알 수 있기 때문이다.

```js
// bad

const TAB_INDEX = {
  first: 1,
  second: 2,
  third: 3,
};

const { first, second, third } = TAB_INDEX;

// good

const TAB_INDEX = {
  FIRST: 1,
  SECOND: 2,
  THIRD: 3,
};

const { FIRST, SECOND, THIRD } = TAB_INDEX;
```

### function 함수와 arrow 함수를 사용하는 기준

아래와 같은 이유로 함수라면 arrow 함수를 사용합니다.

1. this를 신경 쓰지 않아도 되기에 순수 함수로 사용할 수 있다.
1. function은 일반 함수, 생성자 함수, 메서드 함수의 다양한 역할을 하지만 화살표 함수를 사용하면 '이 코드는 함수다'라는 정보를 다른 개발자에게 명확히 전달할 수 있다.
1. function과 달리 프로토타입이 없기에 더 가볍다

```js
// bad

function add(a, b) {
  return a + b;
}

// good

const add = (a, b) => {
  return a + b;
};
```
