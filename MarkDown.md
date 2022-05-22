# 마크다운 정리

README.md 파일 작성할 때 사용하는 마크다운 문법!

헷갈릴 때 찾아보기위해 다른 분들 블로그를 참고하여 따로 정리해보았다.

주로 사용할 만한 것 위주로 요약했기 때문에 몇 문법은 생략했다.

## 📌 마크다운?

2004년 존그루버에 의해 만들어진 텍스트 기반 마크업 언어.

읽고 쓰기가 쉽고 HTML로 변환이 가능하다.

README.md 에서 확장자 .md 가 바로 마크다운 문서를 뜻한다. 

### 🧩 장점?

1. 문법이 쉽다.
2. 별도 도구 없이 작성이 가능하다.
3. 텍스트 파일이기 때문에 가볍고, 보관과 변경이력 관리가 쉽다.

### 🧩 단점?

1. 표준이 없다.
2. 따라서 사용자마다 문법이 상이하고, 도구에 따라 결과물에 차이가 있다.
3. 모든 HTML 마크업을 대신하지 못한다.

### 🧩 VScode 에서 마크 다운 사용하기 & 미리보기

md 문서를 만든 뒤, 오른쪽 상단의 ‘미리보기 열기' 버튼 클릭하면 결과물을 미리볼 수 있다.

![image](https://user-images.githubusercontent.com/89282099/169690791-50959d46-0a12-47aa-bfab-91ea02f05613.png)

## 📌 제목(Header)

순서대로 `<h1>` ~ `<h6>` 로 변환된다.

```markdown
# 제목 1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6
```

## 📌 강조(Emphasis)

✅ 문장 중간에 사용할 경우, 앞 뒤에 띄어쓰기 해주자!

→ 이렇게 `**앞뒤로**` 띄어쓰기 해줘야한다.

1. 이텔릭체
    
    *별표(asterisks)*  or   _언더바(underscore)_
    
    →  `<em>`으로 변환 됨.
    
2. 볼드체
    
    **별표(asterisks)**  or   __언더바(underscore)__
    
    → `<strong>`으로 변환 됨.
    
    ※ **_이텔릭체_와 두껍게**를 같이 사용할 수 있다.
    

1. 취소선
    
     ~~물결표시(tilde)~~
    

1. 밑줄
    
    <u>밑줄</u>
    

```markdown
<em> 으로 변환
*single asterisks*    //이탤릭체
_single underscores_    //이탤릭체

<strong> 으로 변환
**double asterisks**    //강조
__double underscores__   //강조

<del> 으로 변환
~~cancelline~~      //취소선

<u>는 밑줄
<u>underline</u>     //밑줄
```

- *single asterisks*
- *single underscores*
- **double asterisks**
- **double underscores**
- ~~cancelline~~
- underline

## 📌 들여쓰기

4개의 공백 or 탭으로 들여쓰기 가능.

```markdown
안녕하세요.

    안녕하세요.
    만나서 반값습니다.
    오늘은 어떠셨나요.

안녕하세요.
```

- 들여쓰지 않은 행을 만날때까지 변환이 계속된다.
- 반드시 들여쓰기할 문단 위 아래로 한줄씩 띄워줘야 잘 작동한다.

## 📌 목록(List)

`<ol>`, `<ul>` 목록 태그로 변환

```markdown
1. 순서 목록
1. 순서 목록
  1. 순서 목록(서브)
  1. 순서 목록(서브)
1. 순서 목록
  - 비순서 목록(서브) 
  - 비순서 목록(서브)

- 비순서 목록 기호
  - 대쉬(hyphen)
  * 별표(asterisks)
  + 더하기(plus sign)
```

- 순서 목록을 1. 로만 써도 알아서 번호가 매겨진다.
- 무조건 내림차순. 1 - 2 - 3 ... 순서를 바꿀 순 없다.

## 📌 인용문(BlockQuote)

`<blockquote>`로 변환 됨.

- `>` 블럭인용문자 이용

```markdown
> 인용문입니다.
>> 중첩된 인용문(nested blockquote)
>>> 중중첩된 인용문 1
>>> 중중첩된 인용문 2
```

> 인용문입니다.
> > 중첩된 인용문(nested blockquote)
> > > 중중첩된 인용문 1
> > > 중중첩된 인용문 2

## 📌 링크(Links)

`<a>`로 변환 됨.

상대적 주소도 가능. 이메일도 링크 가능.

- [링크 키워드](실제 주소) 이런 형식

1. 그냥 주소만 올릴 때
    - 그냥 주소 쓰기
    - <> 안에 주소 쓰기
    
    ```markdown
    그냥 주소만 작성해도 링크가 생긴다. <>로 감싸도 된다.
    
    구글 : https://google.com
    네이버 : <https://naver.com>
    ```
    
2. 링크 키워드 필요할 때
    - [link keyword](실제 주소)
    - [link keyword](실제 주소 “링크 설명(title)”)
    - 상대 주소도 가능
    
    ```markdown
    [GOOGLE](https://google.com)
    
    [NAVER](https://naver.com "링크 설명(title)")
    
    [상대 주소](../users/login)
    ```
    
3. 참조 링크로 표시
    - [link keyword] [id]
        
        [id] : 실제 주소 “링크 설명(title)”
        
        → 보통 하단에 id를 모아서 작성 
        
    - [id]
        
        → 링크 키워드 없이 참조 링크 그대로 표시 가능.
        
    
    ```markdown
    [MDN][MDN link]  //링크 주소 대신 id로 주고 아래에서 정의
    
    [GitHub][1]
    
    문서 안에서 [참조 링크]를 그대로 사용 가능하다.
    -> 참조 링크 부분이 링크 표시됨.
    
    [MDN link]: https://developer.mozilla.org/ko/
    [1]: https://github.com
    [참조 링크]: https://naver.com "네이버로 이동"
    ```
    

## 📌 이미지(Images)

`<img>` 로 변환 됨.

링크랑 비슷하나, `!` 가 붙는다!

- ![대체 텍스트](이미지 주소)
- 대체 텍스트를 [] 이렇게 비워둬도 되지만, 가능하면 써주자.

```makefile
![대체 텍스트(alternative text)](http://www.gstatic.com/webp/gallery/5.jpg "링크 설명(title)")

![랜덤 이미지][dummy]

[dummy]: [https://picsum.photos/200/300](https://picsum.photos/200/300) "더미 이미지 사이트 링크"
```

### 🧩 이미지에 링크 걸기

- 이미지 마크다운을 [ ]로 감싸고 뒤에 (주소) 쓰기

```markdown
[![Vue](https://kr.vuejs.org/images/logo.png)](https://kr.vuejs.org/)
```

## 📌 코드(code) 강조

`<pre>`, `<code>`로 변환 됨.

### 🧩 인라인(inline) 코드 강조

`(백틱) 으로 감싸 준다.

### 🧩 블록(block) 코드 강조

1. `<pre><code> {코드 내용} </code></pre>`
2. 코드블럭코드(```) 을 이용 - 백틱 3개 찍기
    
    → 코드 종류까지 적어주면 좋다.
    
    ```markdown
    ```javascript
    function func() {
      var a = 'AAA';
      return a;
    }
    ```
    ```
    

## 📌 표(Table)

`<table>` 로 변환 됨.

- 헤더 셀을 구분할 때 3개 이상의 -(hyphen/dash) 기호 필요
- 헤더 셀을 구분하면서 : (Colons) 기호로 셀(열/칸) 안에 내용을 정렬 가능
    
    |:---|   좌측 정렬
    
    |:---:|  가운데 정렬
    
    |---:|  우측 정렬
    
- 가장 좌측과 가장 우측에 있는 | (vertical bar) 기호는 생략 가능

```markdown
| 학생 | 등급 | 점수 |
|---|:---:|---:|
| Andy | B+ | 85 |
| July | A | 92 |
| Chris | C | 70 |
| Helen | C+ | 75 |

학생 | 등급 | 점수
---|:---:|---:
Andy | B+ | 85
July | A | 92
Chris | C | 70
Helen | C+ | 75
```

## 📌 수평선(Horizontal Rule)

`<hr/>` 로 변환 됨

-, *, _ 등을 3개 이상 쓰면 된다.

```markdown
---
Hyphens <- 요걸 가장 많이 쓰게 되는 듯...?

***
Asterisks

___
Underscores
```

## 📌 줄바꿈(Line Breaks)

- 그냥 엔터만 치면 줄바꿈이 되지 않는다.
    - 문장 마지막에 공백 2개를 친 뒤에 엔터를 치거나
    - 엔터를 한 번 더 쳐서 한줄을 통으로 비워주거나
- `<br/>` 태그를 써도 줄바꿈 된다.

## 📌 체크박스(Checkbox)
- 대괄호 `[]`를 써주면 된다.
- 안을 체크하고 싶을 땐 `[x]` 이렇게 x를 넣어준다.

```markdown
[ ] 체크박스
[x] 표시된 체크박스
```
[ ] 체크박스   
[x] 표시된 체크박스

<br/>

> 참고자료   
> heropy님 블로그 [https://heropy.blog/2017/09/30/markdown/](https://heropy.blog/2017/09/30/markdown/)
> ihoneymon님 깃헙 [https://gist.github.com/ihoneymon/652be052a0727ad59601](https://gist.github.com/ihoneymon/652be052a0727ad59601)