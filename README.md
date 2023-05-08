# 프론트엔드 컨벤션

HTML, CSS, JAVASCRIPT에 관련된 규칙을 정리한 문서입니다.

1. [HTML](#HTML)
1. [CSS](#CSS)
1. [Javascript](#Javascript)

## HTML

## CSS

## Javascript

1. [상수](##상수)

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
