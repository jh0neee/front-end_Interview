# 빅오(Big-O) 표기법

#### 알고리즘 성능을 수학적으로 표기해주는 표기법.

<br/>

## 빅오(Big-O)

#### 빅오(Big-O)는 함수의 입력값이 늘어날 때 함수 실행시간이 어떻게 변하는지 설명하는 방법이다.

> 사과 1개를 들고 걸어가는 것과 사과 n개를 들고 걸어갈 때의 속도 차이를 생각하면 쉽다.

<br/>

- **시간복잡도**

We say that an algorithm is O(f(n)) if the number of simple operations the computer has to do is eventually less than a constant times f(n), as n increases

> n이 증가함에 따라, 컴퓨터가 수행해야하는 간단한 연산의 수가 결과적으로 상수 곱하기 f(n)보다 작으면 O(f(n)) 이라고 한다.

선형 O(n) : f(n) = n => n의 값이 커질 수록 실행시간도 같이 늘어나는 형태. 비례
이차형 O(n^2) : f(n) = n^2 => n의 값이 커질 수록 실행 시간이 n의 제곱
일정 O(1) : f(n) = 1 => n의 값이 커질 수록 실행 시간이 상수.(아무 영향도 받지 않음)

<br/>

1. **시간 비교** -> 내장된 타이밍 함수(`performance.now()`) 사용

- `정확도` 측면에서 문제가 있음
- 기기마다 다른 방식으로 시간 기록됨
- 같은 기기에서도 실행 마다 각각 다른 시간 기록됨
- 빠른 알고리즘에서는 짧은 시간 안에 처리되기 때문에 정확히 측정 불가

<br/>

2. **컴퓨터가 처리해야하는 연산 개수** -> 어떤 기기든 `연산 개수는 변하지 않는다.`

- 루프 X

  ```js
  function addUpToFirst(n) {
    return (n * (n + 1)) / 2;
  }
  ```

  - 연산 횟수는 총 **3번** (곱셈, 덧셈, 나눗셈)
  - n의 값이 커질 수록 아무 변화가 없음(항상 연산은 3번). 실행시간 변하지 않음.
  - O(1)

- 루프 O

  ```js
  function addUpToSecond(n) {
    let total = 0;
    for (let i = 1; i <= n; i++) {
      total += i;
    }
    return total;
  }
  ```

  |     코드      |   연산 횟수   |
  | :-----------: | :-----------: |
  | let total = 0 |      1회      |
  |   let i = 1   |      1회      |
  |    i <= n     |   n회 비교    |
  |      i++      | n회 덧셈 연산 |
  |      i++      |   n회 할당    |
  |  total += i   | n회 덧셈 연산 |
  |  total += i   |   n회 할당    |

  - n이 10이라면, 연산 50개의 루프 밖의 2개의 할당을 더한 52
  - n이 커질수록 **연산의 갯수도 비례적으로 증가**함.
  - O(n)

<br />


- **공간복잡도**

boolean, number, undefined, null : O(1) 공간
string, object, array : O(n) 공간

- O(1)

  ```js
  function sum(n) {
    let total = 0; // 1개의 숫자
    for (let i = 0; i < arr.length; i++) {
      // 1개 숫자 할당
      total += arr[i];
    }
    return total;
  }
  ```

  - total 변수에 숫자를 더하는 것 뿐. 입력의 크기와는 상관없이 항상 같다.

- O(n)

  ```js
  function double(arr) {
    let newArr = [];
    for (let i = 0; i < arr.length; i++) {
      newArr.push(2 * arr[i]);
    }
    return newArr;
  }
  ```

  - 입력된 arr 크기와 비례해서 공간이 커진다.
