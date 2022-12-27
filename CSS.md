# CSS

상태: In progress

## CSS ( Cascading Style Sheet )

**C**ascading : “상속 또는 종속하는” ⇒ 선택자에 적용된 많은 스타일 중에 어떤 스타일로 브라우저에 표시할지 결정해주는 원리

마크업 언어가 실제 표시되는 방법을 기술하는 스타일 언어

## 사용이유

문서 전체의 일관성을 유지할 수 있고 작업 시간도 단축됨

## CSS3

CSS3의 경우 그림자 효과, 그라데이션, 변형 등 그래픽 편집 프로그램으로 제작한 이미지를 대체할 수 있는 기능이 추가

다양한 애니메이션 기능이 추가되어 어도비 플래시를 어느 정도 대체

## Style 꾸미는 법

1. 속성처럼 style 적용
    
    ```html
    <h1 style="color:blue; text-algin:center;"> 속성처럼 style 적용 </h1>
    ```
    
2. style 태그 사용
    
    ```html
    <style>
    	h1{
    		color:blue;
    		text-algin:center;
    	}
    </style>
    
    <h1> 속성처럼 style 적용 </h1>
    ```
    
3. css파일을 만들어 html에 적용
    
    ```css
    /*파일이름 : styletest.css*/
    h1{
    	color:blue;
    	text-algin:center;
    }
    ```
    
    ```html
    <head>
    	<link rel="stylesheet" href="styletest.css" />
    </head>
    <h1> 속성처럼 style 적용 </h1>
    ```