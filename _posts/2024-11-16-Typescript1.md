---
layout: single
title: "TypeScript를 사용하는 이유와 동작원리"
categories: 기술면접
tag: [TypeScript]
toc: true
author_profile: false
# sidebar:
#     nav: "counts"
# search: true
---

## TypeScript?.

타입스크립트는 마이크로소프트에서 개발한 자바스크립트의 슈퍼셋(상위 집합) 프로그래밍 언어입니다. 자바스크립트에 정적 타입 시스템을 추가하여 코드의 안정성과 가독성을 높인 언어입니다.

### 타입스크립트가 만들어진 배경

대규모 애플리케이션 개발 지원: 자바스크립트는 원래 작은 규모의 스크립트를 위해 설계되었지만, 점차 복잡하고 큰 애플리케이션에 사용되면서 한계점이 드러났습니다. 타입스크립트는 이러한 대규모 프로젝트에서의 문제점을 해결하기 위해 개발되었습니다.

### 타입스크립트 vs 자바스크립트

자바스크립트는 매우 유연한 언어로, 간단한 스크립트부터 복잡한 애플리케이션까지 다양한 프로그램을 개발할 수 있습니다. 하지만 이러한 유연함은 때로는 안정성을 저해하는 단점으로 작용할 수 있습니다.
예를 들어, 타입에 대한 제약이 없기 때문에 런타임 오류가 발생하기 쉽습니다.

이러한 문제를 해결하기 위해 등장한 것이 TypeScript입니다.
TypeScript는 자바스크립트에 **정적 타입 검사(Static Type Checking)**를 추가하여, 개발 단계에서 오류를 미리 감지할 수 있게 합니다.
즉, 자바스크립트에 안전장치를 더한 언어로 이해할 수 있습니다. 이를 통해 대규모 애플리케이션 개발 시 안정성과 유지보수성을 높이는 데 도움을 줍니다.

### TypeScript의 동작 원리

TypeScript의 동작 원리는 자바스크립트와 마찬가지로 컴파일러를 기반으로 작동하며, 코드를 컴퓨터가 이해할 수 있는 형식으로 변환하는 과정에서 **AST(Abstract Syntax Tree, 추상 문법 트리)**라는 중간 단계가 포함됩니다.

#### 1. 개발자가 TypeScript 코드를 작성합니다.

```ts
function greet(name: string): string {
  return `Hello, ${name}`;
}
```

#### 2. 파싱(Parsing): AST 생성

컴파일러는 작성된 코드를 **파싱(Parsing)**하여 **AST(Abstract Syntax Tree, 추상 문법 트리)**를 생성합니다. AST는 코드의 문법 구조를 트리 형태로 표현한 자료구조입니다.

파싱이란?텍스트 데이터를 분석하여 컴퓨터가 이해할 수 있는 구조(특히 AST)로 변환하는 과정입니다.

예를 들어, 위 코드의 AST는 다음과 같은 형태로 변환됩니다:

```yaml
FunctionDeclaration
├── Identifier: greet
├── Parameters:
│   └── Parameter:
│       ├── Identifier: name
│       └── TypeAnnotation: string
└── Body:
    └── ReturnStatement:
        └── TemplateLiteral:
            ├── Literal: "Hello, "
            └── Identifier: name

```

#### AST의 역할

코드를 이해하기 쉽고 분석 가능한 데이터 구조로 변환.
타입 검사 및 코드 변환의 기반이 됨.

### 3. 타입 검사(Type Checking)

AST가 생성되면 컴파일러는 코드를 읽고 타입 검사를 수행합니다. TypeScript는 컴파일 단계에서 변수, 함수, 객체 등의 타입을 확인하며, 타입이 잘못된 경우 오류를 출력합니다.

```ts
greet(42);
// 오류: 'number' 타입은 'string' 타입 매개변수에 할당할 수 없습니다.
```

### 4. 코드 변환(Transpilation)

타입 검사가 끝나면, TypeScript 코드는 순수 JavaScript 코드로 변환됩니다. 변환된 JavaScript는 AST를 바탕으로 작성되며, TypeScript에서 사용된 타입 정보는 모두 제거됩니다.

예: 위의 TypeScript 코드는 다음과 같이 변환됩니다.

```js
function greet(name) {
  return `Hello, ${name}`;
}
```

이 JavaScript 코드는 브라우저나 Node.js와 같은 런타임 환경에서 실행됩니다.

### 5. 출력된 JavaScript 실행

TypeScript는 자체적으로 실행되지 않습니다. 컴파일 결과로 생성된 JavaScript가 실행됩니다. 따라서 TypeScript는 런타임 단계에서는 아무 영향을 미치지 않습니다.

### TypeScript의 동작원리 요약

1. 코드를 파싱하여 **AST(추상 문법 트리)**로 변환.
2. 타입 검사를 수행하여 오류를 감지.
3. 타입 정보를 제거하고 JavaScript 코드로 변환.
4. 변환된 JavaScript 코드를 실행 환경(브라우저, Node.js 등)에서 실행.
