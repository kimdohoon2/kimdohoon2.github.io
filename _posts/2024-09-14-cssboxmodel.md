---
layout: single
title:  "CSS의 박스 모델(Box Model)이란?"
categories: CSS
tag: [CSS, Margin, Padding]
toc: true
author_profile: false
# sidebar: 
#     nav: "counts"
# search: true
---
## CSS의 박스 모델

CSS의 박스 모델(Box Model)은 웹 페이지의 요소가 차지하는 공간을 설명하는 모델로,<br>
각 요소는 네 개의 주요 부분으로 구성됩니다.

1. 내용 (Content): 실제 텍스트나 이미지와 같은 요소의 내용이 위치하는 부분입니다. 이 영역의 크기는 width와 height 속성으로 설정합니다.

2. 패딩 (Padding): 내용과 테두리 사이의 공간입니다. 패딩은 요소의 내부 여백을 의미하며, padding 속성으로 조절할 수 있습니다. 패딩은 요소의 배경색과 함께 표시됩니다.

3. 테두리 (Border): 요소의 가장자리를 감싸는 선입니다. 테두리는 border 속성으로 설정할 수 있으며, 두께, 스타일, 색상을 지정할 수 있습니다.

4. 마진 (Margin): 요소의 외부 공간으로, 다른 요소와의 간격을 조절합니다. 마진은 margin 속성으로 설정하며, 요소의 바깥쪽에 위치합니다.

차이점 : 마진은 요소와 다른 요소 간의 간격을 조절하고, 패딩은 요소 내부의 내용과 테두리 간의 간격을 조절합니다.

## 박스 모델의 구조
![css box model](https://miro.medium.com/v2/resize:fit:2560/1*nmdxvJbL2GI5NQSXCLOskA.png){: width="50%" height="100%"}



* 가장 안쪽: 내용
* 그 다음: 패딩
* 그 다음: 테두리
* 가장 바깥쪽: 마진


<span style="font-size:15px;">이미지 출처: Pyram, Joseph. "The CSS Box Model." Medium, 2 Sep. 2020, https://medium.com/swlh/the-css-box-model-b73c8a771ddb.</span>







