# DOM

## 📌 DOM 이란?

- DOM = Document Object Model = 문서 객체 모델
- HTML 요소를 Object(JavaScript Object)처럼 조작(Manipulation)할 수 있는 Model이다.
- JavaScript를 사용할 수 있으면, DOM으로 HTML을 조작할 수 있다.
- JavaScript에서 DOM은 document 객체에 구현되어 있다.
- 브라우저에서 작동되는 JS 코드에서는 어디에서나 document 객체를 조회할 수 있다.
- DOM 구조 조회하기
    
    `console.dir(document.body)` = DOM 을 객체의 모습으로 출력해준다. (앞으로 자주 사용)
    
- DOM에는 HTML 엘리먼트에 저장할 수 있는 다양한 속성들이 이미 객체 내에 존재한다.
    
    ```javascript
    const list = document.querySelector('li');//이렇게 DOM을 가져오면
    
    //내부에 여러 프로퍼티들을 가지고 있다.
    const list = {
        ariaAutoComplete: null,
        ariaBusy: null,
        ariaChecked: null,
        ariaColCount: null,
        innerHTML: '<a id="link" href="#"></a>',
        appendChild: function() {
            //...Some Code
        }
        // ...
    }
    ```
    
- DOM은 **트리구조**
    
    → 부모가 자식을 여러 개 가지고, 자식에게는 부모가 하나인 구조가 반복된다.
    
    ![image](https://user-images.githubusercontent.com/89282099/171015863-134966bb-6db0-4f31-84f2-992cdd5915c4.png)
    

<br/>

## 📌 DOM 의 특징

1. 항상 유효한 HTML 형식이다. 

    → HTML 문서가 유효하지 않으면 DOM 트리는 교정되어 나타난다.
    
2. 자바스크립트에 수정될 수 있는 동적 모델이어야 한다.
    
    → 자바스트립트로 DOM을 업데이트할 수 있다. HTML 문서가 변경되는 건 아니다.
    
3. 가상 요소를 포함하지 않는다. (Ex. `::after`)
    
    → 화면에 랜더링되는 랜더 트리는 DOM & CSSOM 의 조합이다. 가상요소 등은 CSSOM 을 통해 표현된 것이기 때문에 DOM 에 포함되지 않는다.
    
4. 보이지 않는 요소를 포함한다. (Ex. `display: none`)
    
    → 보이지 않는 요소라도 DOM 에 포함되어있다. 다만 DOM 과 CSSOM 가 조합되면서 랜더 트리에서 제외가 되기 때문에 보이지 않는 것이다.
    


## 📌 DOM, CSSOM, 랜더 트리

- 랜더 트리 :  DOM 과 CSSOM 의 조합. 오직 스크린에 그려지는 것으로 구성되어 있다.
- DOM(Document Object Model) : HTML 요소들의 구조화된 표현
- CSSOM(Cascading Style Sheets Object Model) : 요소들과 연관된 스타일 정보의 구조화된 표현   



> **참고 자료**    
> [DOM은 정확히 무엇일까?](https://wit.nts-corp.com/2019/02/14/5522)
