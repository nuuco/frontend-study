# DOM 조작 방법

## 📌 DOM 다루기 - CRUD

### 🧩 CREATE

- document.createElement(’div’)
    
    : 엘리먼트를 만든다. 다만 생성만 하면 노드가 아무데도 연결되지 않아, HTML에 나타나지 않는다.
    
    → 생성 후 변수에 할당해주고, .append() 를 이용해 부모 노드에 자식으로 추가해주어야한다.
    
    ```javascript
    const container = document.querySelector('#container');
    const tweetDiv = document.createElement('div');
    
    container.append(tweetDiv); //-> 이래야 HTML 문서에 새 div 가 생긴다.
    ```
    

- document.importNode(externalNode, deep)
    
    : 현재 문서가 아닌 외부 문서의 노드를 복사하여 현재 문서에 넣을 수 있도록 해준다.
    
    > ⚠️ IE 9 이상부터 지원!
    > 
    > - externalNode - 다른 문서에서 가져올 노드
    > - deep - 불리언 타입. 노드를 가져올 때 노드의 자식 요소들을 포함하여 가져올 것인지 여부. `꼭 써주자`
    
    → 오리지널 노드는 오리지널 문서에서 삭제되지 않는다. 추가된 노드는 오리지널 노드의 복사본!
    
    → deep 속성은 생략하면 브라우저에 따라 기본값이 달라지거나 에러를 발생시킬수 있다. ***꼭 써주자!***
    
    ```javascript
    //기본 문법
    let node = document.importNode(externalNode, deep);
    
    //사용 예시 (mdn 예시)
    let iframe = document.getElementsByTagName("iframe")[0];
    let oldNode = iframe.contentDocument.getElementById("myNode");
    
    let newNode = document.importNode(oldNode, true); //true - 자식 요소까지 가져와
    document.getElementById("container").appendChild(newNode);
    ```
    

- node.cloneNode(deep)
    
    : 이 메서드를 호출한 Node 의 복제된 Node를 반환한다.
    
    - deep - 불리언 타입. 노드를 가져올 때 노드의 자식 요소들을 포함하여 가져올 것인지 여부. `꼭 써주자`
    
    → deep 속성은 생략하면 브라우저에 따라 기본값이 달라지거나 에러를 발생시킬수 있다. ***꼭 써주자!***
    
    → 태그 안의 텍스트 요소도 자식 요소기 때문에, deep 옵션을 false 로 하면 텍스트는 안 가져온다.
    
    → 클론한 노드를 변수에 저장해 부모요소에 append 시켜주지 않으면 문서에 나타나지 않는다.
    
    → 클론한 노드를 반환한다.
    
    ```javascript
    let dupNode = node.cloneNode(true);
    //node - 원본 노드
    //dupNode - 클론 노드
    //true -> 자식 노드까지 복제하라.
    
    //MDN 예시
    let p = document.getElementById("para1");
    let cloneP = p.cloneNode(true);
    ```
    

### 🧩 APPEND


> ⚠️ **추가(append, 노드 연결) 시, 주의할 점!**   
> 👉 만약 주어진 노드가 이미 문서에 존재하는 노드를 참조하고 있다면 `insertBefore()`, `append()` 와 `appendChild()` 메소드는 노드를 현재 위치에서 새로운 위치로 이동시킨다!    
> (문서에 존재하는 노드를 다른 곳으로 붙이기 전에 부모 노드로 부터 지워버릴 필요는 없다.   
> ⇒ 한 노드가 문서상의 두 지점에 동시에 존재할 수 없기 때문…!

</aside>

- node.insertBefore(삽입할 노드, 기준점 노드)
    
    : 부모 노드 안의 기준점이 되는 자식 노드 앞에 자식 노드를 삽입
    
    → 삽입할 노드와, 기준점 노드는 형제 사이가 된다.
    
    → 추가된 자식 노드를 반환.
    
    ```javascript
    //문법
    부모노드.insertBefore(삽입할 노드, (부모 노드의 자식 중) 기준점 노드);
    
    //이런 형태라고 볼 수 있다.
    parentDiv.insertBefore(sp1, sp2.nextSibling);
    ```
    
    ```html
    <부모노드>
    	<자식노드1></자식노드1>
    	<자식노드2></자식노드2>
    	<삽입할노드></삽입할노드>   <!-- 여기에 삽입되었다 --> 
    	<기준점노드></기준점노드>
    </부모노드>
    ```
    

- element.append(노드)
    
    : element에 마지막 자식 요소로 노드를 추가한다.
    
    → IE 는 지원 안된다. IE 지원이 필요할 땐 대신 `.appendChild()` 사용
    
    → 문자열(text node)도 넣어줄 수 있다. `body.append(’just text')`
    
    → 여러개의 자식 요소를 한번에 넣어 줄 수 있다. `body.append(div, ‘hello’, p)`
    
    → `undefined` 만 반환한다. 반환하는 값 없음.
    

- node.appendChild(노드)
    
    : node의 마지막 자식 요소로 노드를 추가한다.
    
    → `.append()`보다 호환성이 좋다. IE5 부터 지원
    
    → 문자열(text node)은 넣어 줄 수 없다. 오직 **Node Object** 만 넣을 수 있다.
    
    → 한 번에 오직 하나의 노드만 추가할 수 있다.
    
    → 추가된 자식 노드를 반환한다. (리턴값 있다.)
    
    ```javascript
    document.body.appendChild(div);  //자식 요소가 추가되었다.
    //반환값 : <div id="box"><p class="para"></p></div>
    ```
    

> 🤔 **append() 와 appendChild() 비교**
> 
> - 공통점 : 둘다 `parent.append(child)` 형태로 parent 에 마지막 자식 요소로 child 를 추가함.
> - 비교 표
>    
>    
>    |  | append() | appendChild() |
>    |---|:---:|:---:|
>    | 노드 객체(Node Object) | O | O |
>    | 문자열(text Node) | O | X |
>    | 반환값(return) | X | O |
>    | 다중 값 허용 | O | X |
>    | 지원 브라우저 | IE 지원 안함 | IE 5부터 지원 |
>
> > 참고자료
> >
> > [MDN append()](https://developer.mozilla.org/en-US/docs/Web/API/Element/append)  /  [MDN appendChild()](https://developer.mozilla.org/ko/docs/Web/API/Node/appendChild)   
> > [남양주개발자님 티스토리](https://webruden.tistory.com/634)
> 
<br/>

### 🧩 READ

⚠️ querySelector는 IE 9이상 사용가능

- document.querySelector('.className li');
    
    : 선택자와 일치하는 문서 내 첫 번째 element를 반환
    
    → 일치하는 요소가 없으면 `null`을 반환
    
    → 변수에 할당하면 해당 element를 조작할 수 있다.
    
    → querySelector 는 선택자에 해당하는 요소가 여러개여도 첫번째 엘리먼트만 가져온다.
    
    ※ 쿼리를 날리다 = 조회하다
    
    ```javascript
    let oneTweet = document.querySelector('.tweet')
    ```
    

- document.querySelectorAll('li');
    
    : 선택자와 일치하는 모든 element를 NodeList 로 반환 
    
    → NodeList 라는 유사 배열 객체(Array-like Object)로 받아온다. (for문 사용 가능)
    

- document.getElementById('idName')
    
    : id 값으로 HTML 엘레먼트를 가져온다.
    

- document.getElementsByClassName('className');
    
    : class 네임으로 엘레먼트들을 가져온다. (그래서 Elements)
    
    → NodeList 라는 유사 배열 객체(Array-like Object)로 받아온다. (for문 사용 가능)
    

```javascript
const idElement = document.getElementById('idName');
const classElement = document.getElementsByClassName('className');
****//클래스 네임으로 가져오면 html 콜렉션으로 가져온다. 그래서 element's' 임.
//이렇게 가져온 것은 배열이 아님. NodeList = 유사 배열 객체
//Array.from() 으로 배열로 바꿀 수 있음.

//비교적 최신 querySelector, querySelectorAll
//가장 편리! 유용! IE 9이상 사용가능
//CSS 선택자를 조합하여 편하게 가져올 수 있음.
//querySelector -> 유효한 것 하나만 가져옴(첫번째만)
//querySelectorAll -> 해당하는 것 다. NodeList 로 가져옴
const query = document.querySelector('.className li');
const queryAll = document.querySelectorAll('li');
```

<br/>

### 🧩 UPDATE

**내용 바꾸기**

- node.textContent
    
    : 요소 안에 있는 내용 반환
    
    → textContent, innerText, innerHTML 중에서 **가장 권장** 된다.
    
    - .textContent;  → 내부 텍스트 리턴
    - 노드.textContent = '텍스트';  → 내부 텍스트 대체
    
    ```javascript
    const oneDiv = document.creatElement('div');
    oneDiv.textContent = 'happy';
    ```
    

> 🤔 **textContent vs innerHTML**
>
> nnerHTML 사용은 꼭 필요하지 않으면 지양하자.   
> HTML tag를 직접 삽입하여 실행하는 형태의 메서드는 보안 문제가 있다.  
> 예를 들면, `<script>`를 활용하여 강제로 해커가 원하는 스크립트를 실행시키는 XSS Attack 같은 해킹에 취약하다. 
>
> ⇒ 공격의 여지를 주지 않게 가능한 한 **textContent** 를 사용하자.

<br/>

**클래스 추가제거**

- element.classList
    
    : 요소의 클래스 정보가 담겨있다.
    
    → 넣어줘야될 class 가 하나이면 `el.classList = 'class-name'` 이렇게 넣어줘도 된다.
    

- .classList.add('클래스명')
    
    : 요소에 클래스 추가하기
    

- .classList.remove('클래스명')
    
    : 요소에 클래스 제거하기
    

**다른 속성 추가제거**

- element.setAttribute(’name’, ‘submit-btn’)
    
    : 특정 속성의 값을 요소에 넣어줄 수 있다.
    
    → 전달인자 (’속성명’, ‘속성값’)
    
    → 만약 속성이 boolean 값이라면 (’속성명’, ‘’) or (’속성명’, true)
    
    ```javascript
    const btn = document.querySelector("button");
    
    btn.setAttribute("name", "submit-btn");
    btn.setAttribute("disabled", "")
    ```
    
- element.removeAttribute(’속성명’)
    
    : 특정 속성을 제거할 수 있다.
    
<br/>    

### 🧩 DELETE

- element.remove()
    
    : 해당 요소가 삭제된다.
    
    ```javascript
    //class 가 tweet 인 것만 지우기(요소가 여러 개일 때)
    const tweets = document.querySelectorAll('.tweet');
    
    tweets.forEach(function(tweet){
    	tweet.remove();
    })
    
    //or
    
    for(let tweet of tweets){
    	tweet.remove();
    }
    
    ```
    
- node.removeChild(childNode)
    
    : 자식 노드를 없앤다. 
    
    → 부모 노드와의 부모-자식관계를 끊어 DOM 트리에서 해제한다. 
    
    → 관계를 끊은 해당 노드의 참조를 반환한다.
    
    ```javascript
    //자식 노드 전부 제거하기
    const container = document.querySelector('#container');
    
    while (container.firstChild) {
      container.removeChild(container.firstChild);
    }
    ```
    
<br/>

### 🧩 예시

```javascript
const searchButton = document.querySelector('.gN089b');

//클래스 이름 넣고 빼기
searchButton.classList.remove('gN089b');
searchButton.classList.contains('gN089b'); //해당 클래스네임이 있는지

//안에 텍스트 뽑아오기, 대체하기
searchButton.textContent; //내부 텍스트 리턴
searchButton.textContent = 'zero'; //내부 텍스트 대체

//자식 지우기
const el = document.querySelector('.link_partner')
searchButton.removeChild(el);

//엘레먼트 만들기 createElement('div')
const el2 = document.createElement('div');
el2.textContent = "new";
//자식 추가하기
searchButton.appendChild(el2); //끝에 자식 생성
//or
searchButton.innerHTML = '<div>new</div>';
```