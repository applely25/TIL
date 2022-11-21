# DOM

DOM (Document Object Model) : 웹 페이지에 대한 인터페이스(인터페이스 : 사용자가 기기를 쉽게 동작시키는데 도움을 주는 시스템)

## 웹 페이지는 어떻게 만들어짐?

웹 브라우저가 원본 html문서 읽음 → 스타일을 입히고 대화형 페이지로 만들어 뷰 포트에 표시 ⇒ “Critical Rendering Path”

<aside>
💡 정리 : 대략 두 단계로 나눔
1. 브라우저는 읽어드린 문서를 파싱하여 최종적으로 어떤 내용을 렌더링할지 결정
2. 브라우저는 해당 렌더링을 수행

</aside>

첫번째 과정 ⇒ “렌더 트리” 생성

### 렌더트리를 생성하기 위해 필요한 것

- DOM ( Document Object Model ) - HTML로 구조홛된 표현
- CSSOM ( Cascading Style Sheets Object Model ) - 요소들과 연관된 스타일 정보의 구조화된 표현

## DOM 생성 / 보여지는 방법

DOM → 원본 HTML 문서의 객체 기반 표현 방식

HTML → 단순 텍스트

DOM → HTML이 객체 모델로 변환되어 다양한 프로그램에서 사용될 수 있음

### DOM 개체 구조

DOM 개체구조 → 노드 트리 ( 하나의 부모 줄기가 여러개의 나뭇가지를 가지고있고, 각각의 나뭇가지가 잎은 가질 수 있는 나무와 같은 구조)

⇒ 루트 요소 <html> : 부모줄기 ,  루트요소 안 태그 : 자식 나뭇가지, 요소안의 컨텐츠 : 잎

```html
<!doctype html>
<html lang="en">
	<head>
		<title>My first web page</title>
	</head>
	<body>
		<h1>Hello, world!</h1>
		<p>How are you?</p>
	</body>
</html>
```

![-3.png](DOM%202b6f4c0f2b0842ada7889e5525fa77bb/-3.png)

## DOM이 아닌 것

### HTML

DOM ≠ HTML (DOM은 HTML문서로부터 생성되지만 항상 동일하지 않음)

DOM이 원본 HTML 소스와 다른 경우 두가지

1. **작성된 HTML이 유료하지 않은 경우**
    
    DOM이 생성되는 동안, 브라우저는 유효하지 않은 HTML 코드를 교정
    

```html
<!doctype html>
<html>
Hello, world!
</html>
```

![-5.png](DOM%202b6f4c0f2b0842ada7889e5525fa77bb/-5.png)

1. **********************************************************************************************자바스크립트에 의해 DOM이 수정될 경우**********************************************************************************************
    
    DOM은 HTML 문서의 내용을 볼 수 있는 인터페이스 역할 + 동적 자원이 되어 수정 할 수 있음
    
    ```jsx
    const newParagraph = document.createElemnt("p");
    const paragraphContent = document.createTextNode("I'm new!");
    newParagraph.appendChild(paragraphContent);
    document.body.appendChild(newParagraph)l
    ```
    
    DOM을 업데이트, HTML 내용을 변경 X
    

### 브라우저에서 보이는 것

브라우저 뷰 포트에 보이는 것은 렌더 트리(DOM, CSSOM) → 렌더트리는 오직 스크린에 그려지는 것으로 구성되어 있어 DOM과 다름

⇒ 렌더링 되는 요소만 관련 있기 때문에 시각적으로 보이지 않는 요소는 제외됨 (ex - display:none)

```html
<!doctype html>
<html lang="en">
	<head></head>
	<body>
		<h1>Hello, world!</h1>
		<p style="display: none;">How are you?</p>
	</body>
</html>렌더트리
```

![DOM](DOM%202b6f4c0f2b0842ada7889e5525fa77bb/-9.png)

DOM

![렌더 트리](DOM%202b6f4c0f2b0842ada7889e5525fa77bb/-8.png)

렌더 트리

DOM은 <p> 포함

렌더 트리 <p> 포함 X

### 개발도구

개발도구의 요소 검사기는 DOM과 가장 유사

개방도구의 요소 검사기 → DOM+ 추가 정보

ex) CSS의 가상 요소 → ::before과 ::after 선택자를 사용하여 생성된 가상요소는 CSSOM과 렌더트리의 일부를 구성함

but, 기술적으로 DOM의 일부는 아님

DOM은 원본 HTML문서로부터 빌드 되고, 요소에 적용되는 스타일을 포함하지 않기 때문임

![Untitled](DOM%202b6f4c0f2b0842ada7889e5525fa77bb/Untitled.png)

가성요소는 DOM의 일부가 아니기때문에 자바스크립트에 의해 수정 X

---

<aside>
💡 요약
📖 DOM : HTML 문서에 대한 인터페이스
1. 뷰 포트에 무엇을 렌더링 할지 결정하기 위해 사용
2. 페이지의 콘텐츠 및 구조, 스타일이 자바스크립트 프로그램에 의해 수정되기 위해사용

</aside>