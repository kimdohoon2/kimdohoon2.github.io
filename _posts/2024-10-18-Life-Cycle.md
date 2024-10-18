---
layout: single
title: "React 생명주기(Life Cycle) 무엇일까요?"
categories: 기술면접
tag: [React, Life Cycle]
toc: true
author_profile: false
# sidebar:
#     nav: "counts"
# search: true
---

## React 컴포넌트는 여러 상태에서 생명주기를 겪으며, 크게 3단계로 나눌 수 있습니다.

### 1단계 : Mounting (생성)

컴포넌트가 처음 DOM에 추가되는 단계입니다. 이때 초기화 작업이나 데이터를 가져오는 작업을 수행할 수 있습니다.

주로 사용되는 메서드:

- constructor(): 컴포넌트 초기 상태를 설정할 때 사용합니다.
- componentDidMount(): 컴포넌트가 화면에 처음 렌더링된 후 실행되며, 보통 API 호출 등 외부 데이터를 가져올 때 많이 사용됩니다.

### 2단계 : Updating (업데이트)

컴포넌트의 상태(state)나 props가 변경되어 리렌더링이 발생하는 단계입니다.

주로 사용되는 메서드:

- shouldComponentUpdate(): 성능 최적화를 위해 컴포넌트가 업데이트될 필요가 있는지 결정할 수 있습니다.
- componentDidUpdate(): 컴포넌트가 업데이트된 후 실행되며, 변경된 값에 대한 후처리가 필요할 때 사용합니다.

### 3단계 : Unmounting (제거)

컴포넌트가 DOM에서 제거되는 단계입니다.

주로 사용되는 메서드:

- componentWillUnmount(): 컴포넌트가 DOM에서 제거되기 전에 실행되며, 타이머나 구독 해제 같은 정리 작업을 할 수 있습니다.

## 최근 React

함수형 컴포넌트와 Hooks를 많이 사용하는데,
useEffect()가 생명주기 메서드를 대체하여 여러 시점에 필요한 로직을 처리할 수 있습니다.
