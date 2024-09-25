---
layout: single
title:  "구조 분해 Destructuring"
categories: javascript
tag: [javascript, 구조분해]
toc: true
author_profile: false
# sidebar: 
#     nav: "counts"
# search: true
---

## 구조 분해 (Destructuring)
구조 분해(Destructuring)는 자바스크립트의 ES6(ECMAScript 2015)에서 도입된 기능으로,
<br>배열이나 객체에서 값을 쉽게 추출하여 변수에 할당할 수 있는 문법이다.

## 기본적으로 배열을 선언 하는 방법
```javascript
const aespa = ['카리나', '윈터', '지젤', '닝닝']

const leader = aespa[0];
const mainVocal = aespa[1];
const subVocal = aespa[2];
const dancer = aespa[3];

console.log(leader); // 카리나
console.log(mainVocal); // 윈터
console.log(subVocal); // 지젤
console.log(dancer); // 닝닝
```
각 변수의 할당하는 객체의[]을 사용하여 출력을한다.

하지만!!

## 배열을 구조분해를 사용하면

```javascript
const aespa = ['카리나', '윈터', '지젤', '닝닝']

const [leader, mainVocal, subVocal, dancer] = aespa

console.log(leader); // 카리나
console.log(mainVocal); // 윈터
console.log(subVocal); // 지젤
console.log(dancer); // 닝닝
```
4줄이였던 코드를 1줄로 나타내며 간결하고 가독성을 높일수 있다.

또한
```javascript
// Destructuring 문법을 활용해서 카리나는 aesapLeader, 나머지 요소들(배열)은 rest 변수에 할당해 주세요
const aespa = ['카리나', '윈터', '지젤', '닝닝']
const [aesapLeader, ...rest] = aespa
console.log(aesapLeader) // 카리나
console.log(...rest) // 윈터 지젤 닝닝

// Destructuring 문법을 활용해서 두 변수의 값을 서로 바꿔주세요
let firstName = 'KHN';
let lastName = 'KDH';

[firstName, lastName] = [lastName, firstName]
// 뒤에 있는 값이 앞으로 할당되기때문에 
console.log(firstName) // KDH
console.log(lastName) // KHN
```
설명 : 

1. 나머지 요소를 ...a을 사용하여 나태낼 수도 있으며
2. 변수의 값을 변경할 수도 있다. ex) [a, b] = [b, a]

## 기본적으로 객체를 선언하는 방법

```javascript
const GalaxyFold = {
  title: '갤럭시 폴드',  // key: 'title', value: '갤럭시 폴드'
  price: 200,            // key: 'price', value: 200
  Memory: '12GB',       // key: 'Memory', value: '12GB'
  'serial-unm': 'ABCDEF' // key: 'serial-unm', value: 'ABCDEF'
}

const title = GalaxyFold.title; // 
const price = GalaxyFold.price;

console.log(title) // 갤럭시 폴드 
console.log(price) // 200

```
설명 :

1. GalaxyFold 객채를 선언하고 중괄호{}안에 각 속성의 key:value 값을 가지며<br>
2. key: 속성의 이름 : title, price, Memory, serial-unm<br>
3. value: 속성에 할당된 값 : 갤럭시 폴드, 200, 12GB, ABCDEF<br>
4. GalaxyFold 객체에서 title과 price 속성의 값을 각각 변수 title과 price에 할당합니다.<br>
5. 이때, 객체의 속성에 접근할 때는 점(.) 표기법을 사용합니다.

## 객체을 구조분해를 사용하면

```javascript
const GalaxyFold = {
  title: '갤럭시 폴드',  
  price: 200,            
  Memory: '12GB',       
  'serial-unm': 'ABCDEF'
}

const {title, price, Memory, color="puple", 'serial-unm':serialNnm} = GalaxyFold

console.log(color) // 출력: puple(기본값을 설정할수 있다.)
console.log(serialNnm) // 출력: ABCDEF
```
설명:

1. 객체 구조 분해 할당은 속성에 쉽게 접근할 수 있게 해주며, 
2. 특히 특수 문자(''), (-)를 포함한 속성에 대해서도 새로운 변수 이름을 지정할 수 있는 유연성을 제공합니다. 
3. 이로 인해 코드가 간결해지고 가독성이 향상됩니다.

## 함수에서 객체 구조 분해 사용하기

```javascript
function displayInfo({ title, price, Memory }) {
    // 파라미터안에 객체의 매개변수를 받을때 구조 분해 할당을 사용한것 
    console.log(`제목: ${title}`);
    console.log(`가격: ${price}`);
    console.log(`메모리: ${Memory}`);
}

const GalaxyFold = {
    title: '갤럭시 폴드',  
    price: 200,            
    Memory: '12GB',       
    'serial-unm': 'ABCDEF'
};

displayInfo(GalaxyFold);
// 출력: 
// 제목: 갤럭시 폴드
// 가격: 200
// 메모리: 12GB
```
설명 : 
1. 함수의 매개변수로 객체를 받을 때 구조 분해 할당을 사용하면, 개별 속성에 쉽게 접근할 수 있습니다.<br>
2. 코드가 간결해지고 가독성이 높아지는 장점이 있습니다.

## 중첩 객체의 구조 분해

중첩 객체는 객체 안에 다른 객체가 포함된 구조를 의미합니다.<br>
구조 분해는 이러한 중첩 객체에서 원하는 속성을 쉽게 추출하는 방법입니다.

### 1. 중첩 객체 정의를 정의한다.

```javascript
const user = {
    username: 'john_doe',
    personalInfo: {
        age: 30,
        email: 'john@example.com',
        address: {
            street: '123 Main St',
            city: 'Seoul',
            country: 'South Korea'
        }
    },
    preferences: {
        theme: 'dark',
        language: 'ko'
    }
};
```
### 2. 구조 분해 할당을 정의한다.

```javascript
const {
    username,
    personalInfo: {
        age,
        email,
        address: { street, city, country }
    },
    preferences: { theme, language }
} = user;
```
### 3. 콘솔 출력
```javascript
console.log(username);  // 출력: john_doe
console.log(age);       // 출력: 30
console.log(email);     // 출력: john@example.com
console.log(street);    // 출력: 123 Main St
console.log(city);      // 출력: Seoul
console.log(country);    // 출력: South Korea
console.log(theme);     // 출력: dark
console.log(language);   // 출력: ko
```
### 함수 매개변수로 사용
중첩 객체를 함수의 매개변수로 받아서 구조 분해 할당을 활용할 수 있습니다.
```javascript
function displayUserInfo({ 
    username, 
    personalInfo: { 
        age, 
        email, 
        address: { street, city, country } 
    }, 
    preferences: { theme, language } 
}) {
    console.log(`Username: ${username}`);
    console.log(`Age: ${age}`);
    console.log(`Email: ${email}`);
    console.log(`Address: ${street}, ${city}, ${country}`);
    console.log(`Theme: ${theme}`);
    console.log(`Language: ${language}`);
}

const user = {
    username: 'john_doe',
    personalInfo: {
        age: 30,
        email: 'john@example.com',
        address: {
            street: '123 Main St',
            city: 'Seoul',
            country: 'South Korea'
        }
    },
    preferences: {
        theme: 'dark',
        language: 'ko'
    }
};

displayUserInfo(user);
```
### 변수로 할당하여 재사용하기

구조 분해를 한 번만 하고 필요한 변수들을 재사용할 수 있습니다.

```javascript
const { 
    username, 
    personalInfo: { age, email, address }, 
    preferences 
} = user;

const { street, city, country } = address;

console.log(username); // john_doe
console.log(age);      // 30
console.log(email);    // john@example.com
console.log(street);   // 123 Main St
console.log(city);     // Seoul
console.log(country);   // South Korea
console.log(preferences.theme); // dark
console.log(preferences.language); // ko
```
#### 장점

가독성 향상:

* 중첩된 속성을 쉽게 추출할 수 있어 코드가 간결하고 이해하기 쉬워집니다.

코드 중복 감소:

* 객체의 속성을 여러 번 참조할 필요가 없어 코드의 중복을 줄일 수 있습니다.

명확한 데이터 구조 표현:

* 중첩된 구조를 명확히 나타내므로, 데이터의 계층적 관계를 쉽게 이해할 수 있습니다.

디폴트 값 설정 가능:

* 구조 분해 시 기본값을 설정할 수 있어, 값이 없을 경우에도 안전하게 처리할 수 있습니다.

#### 단점

복잡한 구조:

* 중첩이 깊어질수록 구조가 복잡해져 가독성이 떨어질 수 있습니다. 특히 중첩이 3단계 이상일 경우, 코드가 길어지고 이해하기 어려워질 수 있습니다.

오류 발생 가능성:

* 중첩된 속성이 없거나 잘못된 경로로 접근할 경우 undefined 에러가 발생할 수 있습니다. 예를 들어, user.personalInfo가 없으면 user.personalInfo.age에서 오류가 발생합니다.

성능 문제:

* 많은 중첩과 구조 분해가 있을 경우, 성능에 영향을 줄 수 있습니다. 그러나 일반적인 사용에서는 큰 문제가 되지 않습니다.

디버깅 어려움:

* 중첩 구조를 사용하면 디버깅 시 어떤 속성이 문제가 되는지 파악하기 어려울 수 있습니다.

