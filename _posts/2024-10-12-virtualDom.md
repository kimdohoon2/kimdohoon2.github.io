---
layout: single
title: "리엑트에서 Virtual DOM 무엇일까요?"
categories: 기술면접
tag: [React, DOM]
toc: true
author_profile: false
# sidebar:
#     nav: "counts"
# search: true
---

## Virtual DOM(가상 DOM)

정의 : 리액트에서 Virtual DOM이란 실제 DOM을 수정하기전에 가상의 복제판에서 DOM을 먼저 반영해볼수 있는 장소라고 생각하면 됩니다.
아주 쉽게 말하면 실제 DOM을 복제한 DOM이라고 생각하면 이해하기 편하실겁니다.

## Virtual DOM의 동작 원리

### 1. 상태 변화 발생

리액트에서 상태(state)나 props가 변경되면 UI가 갱신되어야 하는데, 이때 실제 DOM을 바로 수정하지 않고, Virtual DOM에서 먼저 변화가 반영됩니다.

### 2. Virtual DOM 비교

변화가 반영된 새로운 Virtual DOM과 이전 Virtual DOM을 비교(diffing)하여 어떤 부분이 실제로 변화했는지 파악합니다. 이 비교는 매우 효율적인 알고리즘을 사용하여 빠르게 수행됩니다.

### 3. 실제 DOM 업데이트

비교 결과, 변경된 부분만 실제 DOM에 반영하는 과정이 일어납니다. 이때 필요한 최소한의 조작만 DOM에 수행되므로 성능이 최적화됩니다.

## Virtual DOM을 사용하는 이유

### 1. 성능 최적화

실제 DOM은 매우 느린 편입니다. DOM 요소를 직접 추가, 수정, 삭제하는 작업은 브라우저가 화면을 다시 렌더링하는 과정을 수반하므로 비용이 큽니다.

### 2. 효율적인 업데이트

상태 변화로 인해 전체 UI를 다시 렌더링하지 않고, Virtual DOM에서 바뀐 부분만 선택적으로 갱신하여 더 효율적인 업데이트가 가능합니다.

### 3. 코드의 단순화

개발자는 상태 변화에 따른 UI 갱신 로직을 직접 관리하지 않고, Virtual DOM이 알아서 변경된 부분을 찾아 처리해 주기 때문에 코드를 더 간결하게 작성할 수 있습니다.
