# css_basic

 CSS 기초적인 개념들 정리

[참고자료](https://developer.mozilla.org/ko/docs/Web/CSS) 

  목차

- [Selector](#selector)

- [Box](#box)

- [Float](#float)

- [Position](#position)

- [Flexbox](#flexbox)

- [Media Query](#media-query)

- [Typography](#typography)

- [Background](#background)

- [Transition](#transition)

- [Animation](#animation)
- [Etc](#Etc)

<hr>

### Selector
- 우선순위 : ID > Class(Pseudo-class도 포함) > Type

<hr>

### Box
- box-sizing 
  - content-box : width,height 설정시, content영역의 크기로 지정됨. 따라서 w,h 지정해도 의도한 크기대로 나오지 않을 가능성이 있음.
  -  border-box : 별도 계산 없이 설정한 width, height로 적용됨

- Box Type (=display)
  #### Block 
    ![image](https://user-images.githubusercontent.com/26318691/124144843-48d1fb00-dac7-11eb-8df3-0ebc76446001.png)
    - 키워드 : 길막, 면
    
     ##### width
     따로 width를 선언하지 않은 경우, width = 부모의 content-box 의 100%
     따로 width를 선언한 경우, 남은 공간은 자동으로 margin으로 채움
    
     ##### height 특성
     따로 부모의 height를 선언하지 않을 경우, 자식 요소의 height의 합 = 부모의 height
    
     width,height,padding,border,margin box model에 있는 속성 모두 적용 가능

  #### Inline
    ![image](https://user-images.githubusercontent.com/26318691/124143917-7bc7bf00-dac6-11eb-9380-ba7ad977594f.png)
    - 키워드 : 흐름, 선
    - width,height,padding-top,padding-bottom, border-top,border-bottom,margin-top,margin-bottom 사용 못함 (Inline의 흐름을 방해하기 때문)

  #### Inline Block
  - Blcok && Inline : Inline과 Block의 특성을 둘 다 가지고 있음 

<hr>

### Float
- inlineBlock,block -> block 으로 바뀜
- block의 특성인 width,height가 적용 되지 않고 자신의 content width,height만큼 자리를 차지하게 됨
- float를 사용할 경우 레이아웃이 틀어지게 된다
- 해결책 2가지 
  ##### overflow:hidden;
    ![image](https://user-images.githubusercontent.com/26318691/124336979-4d87d380-dbdb-11eb-92d2-76dbbc7c7f7c.png)
  ##### Clearfix
    ![image](https://user-images.githubusercontent.com/26318691/124337164-2b428580-dbdc-11eb-9e92-e530d79764b2.png)
    ![image](https://user-images.githubusercontent.com/26318691/124337246-92f8d080-dbdc-11eb-9d9b-13b4e2ba61a8.png) 
    ![image](https://user-images.githubusercontent.com/26318691/124337284-b02d9f00-dbdc-11eb-86e5-ad0001534c24.png)
    ![image](https://user-images.githubusercontent.com/26318691/124337377-3a760300-dbdd-11eb-90ba-13c9cf53b52c.png)

<hr>

### Position 
 : Type에 따른 기준점

- static : 모든 요소의 기본값, 가장 일반적인 상태
- relative : 이동의 기준점은 자기 자신이 본래 있던 자리, 다른 요소들에게 영향을 끼치지 않음 
- absolute : float특성과 비슷, 자신의 조상 요소 중에 position:static이 아닌 요소를 기준으로 잡음
- fixed : viewpoint 사이즈를 기준으로 위치 
- sticky

- z-index : 수직방향/포지션된 요소들의 수직방향 레벨 위치를 알려줌

<hr>

### Flexbox
  : 정렬

- 단계
   1. Flexbox 선언  (display)
   ```
   .flexbox {
     display: flex;
       /* flex | inline-flex */
   }
   ```
   
  
   2. 가로 or 세로 정렬인지 명시 (flex-direction)
      ![image](https://user-images.githubusercontent.com/26318691/126856721-58f0be9c-294b-4fb2-a6e1-bd97c829fa27.png)
      ![image](https://user-images.githubusercontent.com/26318691/126857181-abafb832-df5a-4b90-a2af-f580841f8f18.png)

      - flex-direction이 row 일 때 
        ![image](https://user-images.githubusercontent.com/26318691/126857197-6f408578-59da-4e6e-bfba-9dcf85aada80.png)

      - flex-direction이 column 일 때 
        ![image](https://user-images.githubusercontent.com/26318691/126857313-a0743cb2-5bae-47a9-9ef2-9d5caaf9a764.png)

      - flex-direction이 row-reverse 일 때
        ![image](https://user-images.githubusercontent.com/26318691/126857437-02ed0f81-4da5-44db-9db0-06bbc0aa39c2.png)

      - flex-direction이 column-reverse 일 때 
        ![image](https://user-images.githubusercontent.com/26318691/126857424-53add48a-f68f-4dd5-aa98-69052da6f2d2.png)

   3. 무조건 한줄안에 다 정렬 인지?  (flex-wrap)

      ![image](https://user-images.githubusercontent.com/26318691/126857447-de95b120-635a-4c6a-a271-a080ef8928b7.png)
  
      - no-wrap
        ![image](https://user-images.githubusercontent.com/26318691/126857563-1fc74f8d-e817-4f78-9c9d-a5f49781bbd3.png)

      - wrap
        ![image](https://user-images.githubusercontent.com/26318691/126857521-e7925c49-3887-4a6c-89ab-3371de2fc915.png)

  #### props

  - Main axis 기준으로 정렬 : justify-content 
  - Cross axis 기준으로 정렬 : align-content or align-items 
  - space-between : 요소 사이의 간격 일정하게 띄우기
  - space-around : 앞, 뒤, 그리고 요소들 사이에도 모두 여유 공간을 두고 배치

  - align-content와 align-items 차이
    align-items : 하나의 flex line에 흐르는 Cross axis를 기준으로 정렬함
    align-content : 전체 Cross axis를 기준으로 정렬함

  - order 
  원하는 순서대로 정렬

<hr>

### Media Query
![image](https://user-images.githubusercontent.com/26318691/127504115-3a71c8ca-f66f-4583-a114-a1df7b8fb97d.png)

![image](https://user-images.githubusercontent.com/26318691/127504073-70190864-5e01-4765-a48e-5f339ebd1c30.png)

<hr>

### Typography 
<img width="1393" alt="KakaoTalk_20210804_182602815" src="https://user-images.githubusercontent.com/26318691/128189566-9074f1fa-18c0-4b74-9f37-7bd3df9a048c.png">

<img width="974" alt="KakaoTalk_20210804_182602815_02" src="https://user-images.githubusercontent.com/26318691/128189527-108b479e-92b9-4e82-9d5b-fc7afe410aaa.png">

<img width="858" alt="KakaoTalk_20210804_182602815_01" src="https://user-images.githubusercontent.com/26318691/128189700-9434a850-7490-4b92-a2c6-7628b729af19.png">

- font-size
  단위 : px / em(equal to capital M)  실제로 적용된 사이즈 / rem  (root em) html에 적용된 폰트 사이즈

- line-height
  단위 : px / em(equal to capital M)  실제로 적용된 사이즈, 가장 많이 사용! / rem  (root em) html에 적용된 폰트 사이즈

- letter-spacing : 자간
  단위 : px / em

- font-family 

- font-weight : 폰트 굵기 

-  color : 폰트 색상

-  text-align : 텍스트 정렬 (left | center | right)

-  text-indent : 들여쓰기할 때 사용

- text-transform : 알파벳 대소문자 변형 (none | capitalize | uppercase | lowercase) 

- text-decoration : 텍스트에 줄 긋기 (none | underline | line-through | overline)

- font-style : 문자 기울기 (normal | italic | oblique) 

<hr>

### Background
- background-color 
  단위 : hex / rgb / rgba

- background-image
  url() 사용해서 파일 경로 or 이미지 주소 넣어줌

- background-repeat 
  repeat(default) / no-repeat

- background-size 
  - contain : 이미지가 잘리거나 찌그러지지 않는 한도 내에서 제일 크게 설정
  - cover :  이미지가 잘리거나 찌그러지지 않는 한도 내에서 제일 크게 설정. 이미지의 가로세로비가 요소와 다르다면 이미지를 세로 또는 가로방향으로 잘라내어 빈 공간이 생기지 않도록 설정
 
- background-position 
   x축 y축 위치 명시

<hr>

### Transition
  - property
    css 속성 명시(font-size,..etc)

  - duration
    지속시간(ms/s)

  - [timing-function]
    변화 속도 지정
    ease-in | ease-out | ease-in-out | cubic-bezier()

  - [delay]
    transition 지연 설정 

<hr>

### Animation
  
  - animation-name 
    ![image](https://user-images.githubusercontent.com/26318691/130977378-cc502d4f-c09b-47b2-9b82-cc5c403ea441.png)

   #### @keyframes
   ![image](https://user-images.githubusercontent.com/26318691/130977999-f25cd2e3-39ca-411e-999b-8fca49a8c357.png)

   ![image](https://user-images.githubusercontent.com/26318691/130978127-64be4fe7-c690-4440-8bc4-b7838d701e3e.png)

 - animation-duration : 지속 시간
 - [animation-timing-function]
 - [animation-delay]
 - animation-iteration-count : 반복 횟수
 - animation-direction : 진행 방향 

<hr>

### Etc
 #### Box Shadow 
 - 요소에 그림자를 줄 때 사용
 - h-offset(x축) v-offset(y축) blur(흐린정도) spread(그림자 사이즈) color(색상)

 #### Overflow 
 - 넘쳐흘렸을 때 어떻게 처리할 것인 지 설정
 - *visible | auto | scroll | hidden

 #### Transform 
 - translate() | scale() | rotate()
 - translate : 내가 원하는 방향으로 옮길 때 사용
 - scale : 사이즈를 키우고 줄이고 할 때 사용
 - rotate : 어떤 요소의 각도를 돌려줄 때 사용 (deg로 명시)


 #### Visibility 
 - *visible | hidden 
 - display : none과의 차이점 : display는 아예 존재하지 않는 것처럼 빈 자리를 채움

<hr>

### Grid System
- container : 그리드 시스템이 적용되는 전체 범위
- column : 나눠져 있는 칸
- gutter : 간격조절을 위한 여백 주기
