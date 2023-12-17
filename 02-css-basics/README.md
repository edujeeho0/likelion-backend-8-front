# CSS Basics

CSS는 Cascading Style Sheet의 약자이다. HTML이 인터넷 브라우저에 표시될때 스타일과 배치를 정의하기 위해 사용하는 코드의 일종이다. HTML이 데이터와 구조라면, CSS는 데이터의 표현을 담당한다.

일반적인 HTML 요소의 모습도 결국 W3C에서 정의한 표준에 맞게 브라우저 내부 CSS가 적용된 모습이라 생각할 수 있다.

## CSS 문법

```css
p {
  color: red;
  text-align: center;
}
```

- 선택자(Selector) - 어떤 요소에 적용할지 결정한다. 위의 예시의 `p`는 `<p>` 요소를 지정하는 선택자.
- 선언(Declaration) - 속성과 값을 정의한다.
- 속성(Property) - 어떤 표현 요소를 변경할지 결정한다.
- 값(Value) - 해당 속성을 어떻게 변경할지 결정한다.

## CSS 적용하기

### 개별 요소에 적용 (Inline)

- 장점: 빠르고 정확하게 하나의 요소에 적용 가능
- 단점: 똑같이 생긴 요소를 만든다면 코드가 반복해서 등장

```html
<!-- 1. 요소에 style 속성 사용  -->
<h1 style="color: red;">CSS inline</h1>
```

### HTML `<style>` 태그 (Embedded, Internal)

- 장점: 한 HTML 문서 전체에 적용되어, Inline보다 중복이 줄어듬
- 단점: 여러 HTML 문서를 사용하는 큰 프로젝트라면 마찬가지로 CSS를 반복해서 작성하게 됨

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <style>
    h2 {
      color: yellowgreen;
    }
  </style>
  <title>Title Element</title>
</head>
<body>
  <!-- 2. head의 style 요소 사용 -->
  <h2>CSS Embedded</h2>
</body>
</html>
```

### 외부 CSS 파일 불러오기 (External)

- 장점: 여러 문서에 걸쳐 같은 디자인을 적용하기 좋음
- 단점: CSS를 가져오는 요청 한번이 추가되어 아주아주아주 조금 느림

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Title Element</title>
  <link rel="stylesheet" href="01-styles.css">
</head>
<body>
  <!-- 3. link로 불러온 css 파일 사용 -->
  <h3>CSS External</h3>
</body>
</html>
```

## CSS Selector

기본적으로 CSS를 정의할때는 어떤 요소에 적용할지를 결정해야 한다. 이때 사용하는게 CSS 선택자이다. 특정 규칙을 바탕으로 CSS 요소를 정하는 방법

### 요소 선택자

모든 요소에 일괄적으로 CSS를 적용

```css
/* 모든 h1에 적용 */
h1 {
  color: blue;
}

/* 모든 p에 적용 */
p {
  color: cadetblue;
}
```

### `id` 선택자

주어진 값과 동일한 `id`를 속성으로 가진 요소에 적용.
`id`는 중복해서 만들지 않기 때문에, 하나의 요소에 적용한다고 볼 수 있다.

- `#{선택할 id}`

```css
/* id가 "id-selector-h1"인 요소에 적용 */
#id-selector-h1 {
  color: dodgerblue;
}

/* id가 "id-selector-p"인 요소에 적용 */
#id-selector-p {
  color: darkgreen;
}
```

```html
<!-- id 선택자 -->
<h1 id="id-selector-h1">ID Selector</h1>
<p id="id-selector-p"><!-- 생략 --></p>
```

### `class` 선택자

주어진 값과 동일한 값을 `class`에 포함한 요소에 적용.
같은 역할을 하는 요소들에 일괄적으로 스타일을 적용할 수 있다.

- `.{선택할 class}`

```css
/* class에 "message-sender"가 포함된 요소에 적용 */
.message-sender {
  color: darkslateblue;
}

/* class에 "message-body"가 포함된 요소에 적용 */
.message-body {
  color: brown;
}
```

```html
<!-- class 선택자 -->
<h3 class="message-sender">Alex</h3>
<p class="message-body">Hi, I'm Alex!</p>

<h3 class="message-sender">Brad</h3>
<p class="message-body">Hi, I'm Brad.</p>

<h3 class="message-sender">Chad</h3>
<p class="message-body">Hey, nice to meet you!</p>
```

---

그 외 전체 선택자, 속성 선택자, 결합자는 직접 찾아서 연습해볼것.

### CSS 우선순위

CSS의 선택자가 지정하는 요소가 겹칠 수 있다.

```html
<!-- 어떤 선택자가 우선 적용될까? -->
<p id="red" class="blue">simple element</p>
```

```css
p {
  color: purple;
}

#red {
  color: red;
}

.blue {
  color: blue;
}
```

이때 CSS는 우선순위에 따라 어떤 선언을 적용할지 결정한다(Cascading).

1. `!important` 가 명시된 규칙 (권장되지 않음)
2. 인라인으로 작성된 규칙
3. `id`, `class`, 요소의 우선순위

자세한건 Wikipedia, MDN 등을 참고할것


