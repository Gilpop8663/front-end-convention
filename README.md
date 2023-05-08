# 프론트엔드 컨벤션

HTML, CSS, JAVASCRIPT에 관련된 규칙을 정리한 문서입니다.

1. [HTML](#HTML)
1. [CSS](#CSS)
1. [Javascript](#Javascript)

## HTML

## CSS

## Javascript

1. [상수](#상수)
1. [함수](#함수)
1. [메서드](#메서드)

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

### 함수

#### function 함수와 arrow 함수를 사용하는 기준

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

#### class, object에서 함수 선언식 메서드와 화살표 메서드

1. 클래스에서는 선언식을 사용하도록 합시다. 이유는 덮어씌우는 것을 따로 생각해야 해서 개발자가 의도한 것과 다른 동작이 일어날 수 있습니다.
1. 클래스에서는 속도 또한 일반 함수 선언식이 화살표 함수보다 더 빠르다고 합니다.
1. 저의 경우는 객체(오브젝트) 메서드 형식으로는 this가 필요한 상황이 아니라면 객체로 만들지 않고 화살표 함수로 만들어 각각 사용하려고 합니다. 그리고 this가 필요하다면 클래스로 만들어 일반 함수 선언식을 사용하도록 하겠습니다.

```js
// bad

class A {
  static color = "red";
  counter = 0;

  handleClick = () => {
    this.counter++;
    console.log("A.handleClick");
  };

  handleLongClick = () => {
    this.counter++;
  };
}

// good

class A {
  static color = "red";
  counter = 0;

  handleClick() {
    this.counter++;
    console.log("A.handleClick");
  }

  handleLongClick() {
    this.counter++;
  }
}

// bad 2

class A {
  handleClick = () => {
    alert(this.getName());
  };

  addEventClick() {
    $("card").addEventListener("click", handleClick);
  }
}

// good 2

class A {
  handleClick() {
    alert(this.getName());
  }

  addEventClick() {
    $("card").addEventListener("click", handleClick.bind(this));
  }
}
```
