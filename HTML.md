# HTML

상태: In progress

## HTML ( **H**yper Text Markup Language)

**H**yper**T**ext : 웹 페이지에서 다른 페이지로 이동할 수 있도록 하는 것

**M**arkup **L**anguage : 태그(<>) 등을 이용하여 문서나 데이터의 구조를 기록하는 언어

<aside>
💡 ❓ HTML은 프로그래밍 언어인가요?
     📖 프로그래밍 언어 : 프로그램을 만들기 위해 컴퓨터에게 명령을 내리기 위한 특수 언어
     📖 HTML : 웹사이트의 구조나 의미를 주기 위한 사용되는 마크업 언어

❗ HTML은 프로그래밍 언어가 아니다!

</aside>

## HTML5

- HTML의 5번째 버전
    - 등장 배경
        
        HTML5 이전까지는 같은 웹사이트라도 웹 브라우저의 종류나 버전에 따라 화면에 다르게 보이는 문제 발생!
        
    - HTML5 원칙
        1. 호환성
            1. 콘텐츠의 호환성
                
                이전 버전으로 제작된 콘텐츠를 아무 문제 없이 이용
                
            2. 이전 브라우저와의 호환성
                
                HTML5가 지원되지 않는 이전 브라우저에서도 이용
                
            3. 기능의 재사용
                
                서로 다른 브라우저에서 만든 기능들을 HTML5에서 이용
                
            4. 이용방법의 호환성
                
                HTML태그를 동일한 사용법으로 이용
                
            5. 혁신보다는 발전의 우선
                
                새로운 마크업 언어보다는 기존의 HTML을 발전 시키는 것이 우선
                
        2. 실용성
            
            실무에서 필요로 하는  것이 우선되어야 함
            
        3. 상호운영성
            
            HTML5를 적용한 브라우저라면 동일하게 적용되어야 함
            
        4. 보편적 접관성
            
            콘텐츠에 누구나 접근할 수 있어야 함
            

## HTML 구성 요소

- 구성요소
    - 태그 (tag)
        - 여는 태그
            
            “<” + “태그 이름” (+ “속성”) + “>”
            
        - 닫는 태그
            
            “<” + “/” + “태그 이름” + “>”
            
    - 속성 (attribute)
        
        “속성 이름” + “=” + “속성 값(value)”
        
        - 유의 사항
            1. 요소 이름 또는 이전 속성과는 한칸의 공백이 필요
            2. 속성 이름 뒤 “=”
            3. 속성 값은 “”로 감싸기
    - 내용 (content)
        
        그냥 글자 (text)
        
    - 요소 (element)
        
        여는 태그 + 내용 + 닫는 태그
        
    
    ### 중첩 요소
    
    (nesting elements)
    
    태그 중첩시 여는 태그와 닫는 태그의 순서는 **“선입 후출”**이다
    
    ```c
    /*올바른 예시*/
    <p> 올바른 예시입니다. <strong>이부분은 강조됩니다</strong> </p>
    
    /*잘못된 예시*/
    <p> 잘못된 예시입니다. <strong>이부분은 강조됩니다</p> </strong> 
    ```
    
    ### 비어있는 요소
    
    (empty elements)
    
    content가 없는 태그들도 존재한다
    
    ```c
    <img src="이미지저장경로" alt="이미지가 없으면 나오는 글자">
    ```
    

## HTML document 구성요소

```c
/*
html 파일에서
! 또는 html:5 입력후 enter시 자동으로 생성
*/

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  
</body>
</html>
```

- <!DOCTYPE html>
    
    이 문서는 html로 작성되었다
    
    📖 DOCTYPE : 문서의 유형을 알려주기 위해 사용
    
- < html >…< /html >
    
    (root element)
    
    전체 페이지의 모든 content를 감싸는 element
    
- lang=”en”
    
    해당 html이 어떤 언어로 사용되었는지 알려줌
    
    en : 영어 , ko : 한글
    

---

- < head >…< /head >
    
    해당 문서에 대한 메타데이터(metadata)의 집합을 정의할때 사용
    
- <meta charset="UTF-8">
    
    html 파일의 인코딩을 알려줌
    
    브라우저에 text를 어떻게 쓰는지 알려주는 것
    
    (태그가 없으면 한글, 일본어, 중국어 특수문자가 깨져서 나옴)
    
- <meta http-equiv="X-UA-Compatible" content="IE=edge">
    
    IE브라우저에서, 각 버전 중 가장 최신 표준 모드를 선택한는 문서 모드
    
- <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    최소, 최대 화면 배율 설정해놓기
    
    initial-scale은 초기 배율(0~1 사이의 값
    
    - <meta name="viewport" content="width=device-width">
        
        브라우저 너비를 장치 너비에 맞춰 표시
        
        (모바일과 PC 웹을 고려하기 위해 사용)
        
    - <meta name="viewport" content="user-scalable=no, width=device-width">
        
        사용자가 크기 조절하기를 원치 않을 때 설정
        
    
    <aside>
    💡 📖 veiwpoint : 사용자가  보여지는 화면의 영역
    
    </aside>
    
- <title>Document</title>
    
    웹페이지 본문에는 보이지 않으며, 브라우저의 탭에서 확인 할 수 있음
    
    유저에게 문서를 보이는 용도, 검색 엔진에서 가장 크게 보여지는 텍스트
    
    <aside>
    💡 페이지의 특성을 잘 나타내는 제목을 나타내는 것이 중요
    
    </aside>
    

---

- <body></body>
    
    해당 HTML 문서의 텍스트, 하이퍼링크, 이미지, 리스트 등과 같은 모든 콘텐츠를 포함하는 영역
    
    HTML 문서에는 단 하나의 body만 존재
