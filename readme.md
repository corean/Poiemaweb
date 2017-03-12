# [poemaweb](http://poiemaweb.com) 정리

## html5

### symantic-web  

#### tag

* strong = b
* em = i
* small
* mark
* del
* ins
* sub / sup
* pre
* q / blockquote

#### link

* target
  * _blank
  * _self
  * _parent
  * _top

#### list

* ul
  ```html
  <ol type="I" start="3" reverse>
      <li value="2">coffee</li>
      <li value="4">tea
      	<ol>
      		<li>Black tea</li>
      		<li>Green tea</li>
      	</ol>
      </li>
      <li>Milk</li>
  </ol> 
  ```


#### table

#### media

* audio

  `<audio src="assets/audo/kalimba.mp3" controls></audio>`

  attribute : src, preload, autoplay, loop, controls

  ```html
  <audio controls>
    <source src="assets/audio/Kalimba.mp3" type="audio/mpeg">
    <source src="assets/audio/Kalimba.ogg" type="audio/ogg">
  </audio>
  <!--웹브라우저별로 지원하는 음악파일이 다르지만,  type속성을 이용해 해결가능-->
  ```

* video

  attribute : poster, preload, autoplay, loop, controls, width, heigh

  ```html
  <video width="640" height="360" controls>
     <source src="assets/video/Wildlife.mp4" type="video/mp4">
     <source src="assets/video/Wildlife.webm" type="video/webm">
  </video>
  ```


#### form

* select group

  ```html
  <select name="cars3">
    <optgroup label="Swedish Cars">
      <option value="volvo">Volvo</option>
      <option value="saab">Saab</option>
    </optgroup>
    <optgroup label="German Cars" disabled>
      <option value="mercedes">Mercedes</option>
      <option value="audi">Audi</option>
    </optgroup>
  </select>
  ```

* button

  `<input type="button">` 는 빈 태그인 반면,  button 태그는 채워진 태그이므로 텍스트나 이미지 같은 컨텐츠를 사용할 수 있다.

  `<form>`안에서는 `<input>`태그를 사용하는 것이 바람직.

#### 레이아웃

* header

* nav

* aside

* section

* article

* footer

  div = block level, span = inline level

## CSS

### Rule set = Style Sheet

### CSS Selecter { Property : Property Value; }

* Reset CSS

  * Eric Meyer's Reset
  * normalize.css

* Attribute Selector 속성 선택자

  ```html
  <style>
    a[target="_blank"]
    h1[title~="first"] /* h1 요소 중에 title 속성값에 "first"를 단어로 포함하는 요소 */
    [lang|="en"] /* lang 속성값이 "en"과 일치하거나 "en-"로 시작하는 요소 */
    a[href^="https://"] /* a 요소 중에 href 속성값이 "https://"로 시작하는 요소 */
    a[href$=".html"] /* a 요소 중에 href 속성값이 ".html"로 끝나는 요소 */
    
    /* div 요소 중에서 class 속성값에 "test"를 포함하는 요소 */
    div[class*="test"] { color: red; }
    /* div 요소 중에서 class 속성값에 "test"를 단어로 포함하는 요소 */
    div[class~="test"] { background-color: yellow; }
  </style>
  ```

* Combinator  복합선택자

  * `>` Child Combinator
  * Sibling Combinator
    * `+` Adjacent Sibling Combinator
    * `~` General Sibling Combinator

* Pseudo-Class Selector

  * Link Pseudo-classes

    * :link
    * :visited
    * :hover
    * :active
    * :focus

  * UI Element states Pseudo-classes

    * :checked
    * :enabled
    * :diabled

  * Structural Pseudo-classes

    * :first-child - 해당 엘리먼트가 부모 엘리먼트를 기준으로 첫번째 있어야

    * :last-child

    * :nth-child(n) : 1번째부터 시작 

      `ol > li:nth-child(2n+1) /* 홀수번째 요소 */` 

    * :nth-last-child(n)

    * :first-of-type - 해당 엘리먼트 기준으로 첫번째

    * :last-of-type

    * :nth-of-type(n)

    * :nth-last-of-type(n)

      `p:nth-last-of-type(2) /* p 요소의 부모의 자식 중 뒤에서 2번째 등장하는 p 요소 */`

    * :not()

    ```css
    div {
      width: 32vw;
      height: 200px;
      background-color: red;
      margin-bottom: 2vw;
      float: left;
    }
    div:not(:nth-of-type(3n-2)) {
      margin-left: 2vw;
    }
    /* 2번째, 3번째 div만 margin-left: 2vx; */
    ```

* Pseudo-Element Selector  가상요소 선택자

  * ::first-letter
  * ::first-line
  * ::after - 일반적으로 content 속성과 함께 사용 
  * ::before
  * ::selection 

## CSS Units

* px
* % - 부모요소의 의해 상속된 사이즈의 %
* em - 부모요소에 의해 상속된 font size의 상대적인 사이즈 100% = 1em
* rem - 최상위(root)의 font size를 기준
* Viewport 
  * vw - viewport width %
  * vh - viewport height %
  * vmin - smaller than width min or height min %
  * vmax - bigger than width max or height max %

## CSS Box Model

* width / height - 기본적 box-sizing : content box. border-box = content + border + padding

* margin, padding, border, box-sizing 은 상속되지 않는다.

* `margin: auto /* 해당 요소를 중앙에 정렬 */`

* max-width / min-width - width 속성보다 우선 적용

* border : border-width border-style border-color;

  * border-style: (horizntal|vertical) (top|horizontal|bottom) (top|right|bottom|left)
  * border-width, border-color - border-style과 함께 사용되지 않으면 적용되지 않는다
  * border-radius - px, em, % 단위. 반지름 기준. 타원도 가능
    * `border-top-left-radius : 50px 25px;`
    * `border-radius: 50px50px 0 0 / 25px 25px 0 0 `

* box-sizing

  * border-box = content + padding + border

  * content-box = content

  * box-sizing은 상속되지 않으므로 초기화하려면

    ```css
    html {
      box-sizing: border-box;
    }
    *, *:before, *:after {
      box-sizing: inherit;
    }
    ```

## CSS Display

### display

* block
  * 항상 새로운 라인에서 시작
  * width: 100%
* inline
  * content의 너비만큼
  * 상하여백은 line-height로 지정. width, height, margin-top, margin-bottom을 사용할수 없다.
  * inline 속성요소내에 block 속성요소를 포함할수 없음.
  * 연속해서 사용하는 경우, 좌우에 정의되지 않은 space(4px)가 자동 지정.
* inline-block
  * inline 과 block 속성을 모두 갖는다. = 한 줄에 표현하면서 width, height, margin 속성을 사용할수 있다.
  * 상하여백은 margin(block)과 line-height(inline) 모두 사용가능
  * 연속해서 사용하는 경우, 좌우에 정의되지 않은 space(4px)가 지정된다. [회피방벙](https://css-tricks.com/almanac/properties/d/display/)
* none

### Visibility

* visible (default)
* hidden : 보이지 않게. 공간차지
* collapse : table요소에서 사용하며 행이나 열을 보이지 않게 한다.
* none : 보이지 않게. 공간차지 X (ie,ff에서만 동작. chrome에서는 hidden과 같이 동작)

### Opacity

* 0.0 ~ 1.0 

## CSS Background

### background-image

여러개 지정가능. 먼저 설정한 이미지가 전면에 출력.

```css
body {
  background-image: url("img/bg/dot.png"), url("img/bg/paper.gif");
  background-repeat: no-repeat, repeat;
}
```

### background-repeat

기본 속성 : repeat

* repeat-x 
* repeat-y
* no-repeat

### background-size

* px : `background-size: 700px 500px;`
* %
* cover : 이미지의 크기 비율을 유지한 상태로 부모요소의 width, height 요소중 큰 값에 맞춘다. (일부가 안보일수 있다)ㅇㅂ
* contain : : 이미지의 크기 비율을 유지한 상태로 부모요소의 width, height 요소중 작은 값에 맞춘다. (꽉 채워지지 않는다)

width, hegith는 공백으로 구분. 쉼표는 다른 이미지를 지정함.

```css
body {
  background-image: url("front.png"), url("back.png");
  background-repeat: no-repeat, no-repeat;
  background-size: 100%, 500px;
}
```

### background-attachment

`background-attachment: fixed  /* 배경이미지는 스크롤 되지 않게 함. */`

### background-position

* top, bottom, center, left, right, 25%, 10px 0 px

### background-color

* rgb(0,0,0)
* transparent

### background

```css
/* background: color || image || repeat || attachment || position */
background: #FFEE99 url("img/bg/dot.png") no-repeat center;
width: 50vw;
height: 300px;
```

## CSS Font & Text

### font-size

