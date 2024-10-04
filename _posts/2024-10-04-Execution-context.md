---
layout: single
title: "실행 컨텍스트(Execution context)?"
categories: 기술면접
tag: [javascript]
toc: true
author_profile: false
# sidebar:
#     nav: "counts"
# search: true
---

## 실행 컨텍스트(Execution context)

정의 : 실행 컨텍스트는 자바스크립트 코드가 실행되는 환경을 나타내는 객체입니다. 각 실행 컨텍스트는 코드 실행에 필요한 정보를 포함하고 있으며, 자바스크립트가 변수, 함수, 객체 등에 접근하는 방법을 정의합니다.

## 실행 컨텍스트의 주요 구성 요소

### 1. 변수 객체(Variable Object)

- 현재 실행 컨텍스트에 있는 모든 변수, 함수 선언, 매개변수를 포함합니다.
- 예를 들어, 함수 내에서 선언된 변수와 매개변수는 이 변수 객체에 저장됩니다.

### 2. 스코프 체인(Scope Chain)

- 변수를 찾기 위해 사용하는 구조입니다. 실행 컨텍스트는 자신의 변수 객체뿐만 아니라 외부 함수의 변수 객체에도 접근할 수 있습니다.
- 즉, 내부 함수는 외부 함수의 변수를 참조할 수 있습니다.
- 스코프 체인은 클로저(Closure)와 밀접하게 관련되어 있습니다.

### 3. this 값:

- 현재 실행 컨텍스트에서의 this 키워드의 값을 정의합니다. this는 실행되는 함수의 호출 방식에 따라 다르게 결정됩니다.

## 실행 컨텍스트의 유형

### 1. 글로벌 실행 컨텍스트:

- 자바스크립트 파일이 처음 실행될 때 생성됩니다. 이 컨텍스트는 전역 객체(브라우저에서는 window 객체)에 대한 참조를 포함합니다.

### 2. 함수 실행 컨텍스트:

- 함수가 호출될 때마다 새로운 실행 컨텍스트가 생성됩니다. 각 함수 호출은 독립적인 실행 컨텍스트를 가집니다.

## 실행 컨텍스트의 생성 과정

### 1. 컨텍스트 생성

- 코드가 실행되면, 해당 코드의 실행 컨텍스트가 생성됩니다.

### 2. 변수 객체 설정

- 변수 객체가 생성되고, 함수의 매개변수와 변수들이 할당됩니다.

### 3. 스코프 체인 설정

- 현재 컨텍스트의 스코프 체인이 설정됩니다.

### 4. this 값 설정

- 현재 실행 컨텍스트에서의 this 값을 설정합니다.

### 5. 코드 실행

- 해당 컨텍스트의 코드를 실행합니다.

## 예시

```javascript
let globalVar = "안녕하세요!"; // 글로벌 변수

function outerFunction() {
  let outerVar = "외부 변수"; // 외부 함수의 지역 변수

  function innerFunction(innerParam) {
    let innerVar = "내부 변수"; // 내부 함수의 지역 변수
    console.log(globalVar); // 글로벌 변수에 접근
    console.log(outerVar); // 외부 함수의 변수에 접근
    console.log(innerParam); // 매개변수에 접근
    console.log(innerVar); // 내부 변수에 접근
  }

  innerFunction("내부 매개변수");
}

outerFunction();
```

## 실행 과정

### 1. 글로벌 실행 컨텍스트 생성

- globalVar가 포함됩니다.

### 2. outerFunction 호출

- outerFunction이 호출되면 새로운 함수 실행 컨텍스트가 생성됩니다.
- outerVar가 포함된 변수 객체가 생성되고, innerFunction에 대한 스코프 체인이 설정됩니다.

### 3. innerFunction 호출

- innerFunction이 호출되면 또 다른 실행 컨텍스트가 생성됩니다.
- innerParam와 innerVar가 포함된 변수 객체가 생성됩니다.

### 4. 변수 접근

- innerFunction 내부에서 globalVar, outerVar, innerParam, innerVar에 접근할 수 있습니다.
- 이를 통해 스코프 체인이 작동하는 모습을 확인할 수 있습니다.
