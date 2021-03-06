# DOM ์กฐ์ ๋ฐฉ๋ฒ

## ๐ย DOM ๋ค๋ฃจ๊ธฐ - CRUD

### ๐งฉย CREATE

- **document.createElement(โdivโ)**
    
    : ์๋ฆฌ๋จผํธ๋ฅผ ๋ง๋ ๋ค. ๋ค๋ง ์์ฑ๋ง ํ๋ฉด ๋ธ๋๊ฐ ์๋ฌด๋ฐ๋ ์ฐ๊ฒฐ๋์ง ์์, HTML์ ๋ํ๋์ง ์๋๋ค.
    
    โ ์์ฑ ํ ๋ณ์์ ํ ๋นํด์ฃผ๊ณ , .append() ๋ฅผ ์ด์ฉํด ๋ถ๋ชจ ๋ธ๋์ ์์์ผ๋ก ์ถ๊ฐํด์ฃผ์ด์ผํ๋ค.
    
    ```javascript
    const container = document.querySelector('#container');
    const tweetDiv = document.createElement('div');
    
    container.append(tweetDiv); //-> ์ด๋์ผ HTML ๋ฌธ์์ ์ div ๊ฐ ์๊ธด๋ค.
    ```
    

- **document.importNode(externalNode, deep)**
    
    : ํ์ฌ ๋ฌธ์๊ฐ ์๋ ์ธ๋ถ ๋ฌธ์์ ๋ธ๋๋ฅผ ๋ณต์ฌํ์ฌ ํ์ฌ ๋ฌธ์์ ๋ฃ์ ์ ์๋๋ก ํด์ค๋ค.
    
    > โ ๏ธย IE 9 ์ด์๋ถํฐ ์ง์!
    > 
    > - externalNode - ๋ค๋ฅธ ๋ฌธ์์์ ๊ฐ์ ธ์ฌ ๋ธ๋
    > - deep - ๋ถ๋ฆฌ์ธ ํ์. ๋ธ๋๋ฅผ ๊ฐ์ ธ์ฌ ๋ ๋ธ๋์ ์์ ์์๋ค์ ํฌํจํ์ฌ ๊ฐ์ ธ์ฌ ๊ฒ์ธ์ง ์ฌ๋ถ. `๊ผญ ์จ์ฃผ์`
    
    โ ์ค๋ฆฌ์ง๋ ๋ธ๋๋ ์ค๋ฆฌ์ง๋ ๋ฌธ์์์ ์ญ์ ๋์ง ์๋๋ค. ์ถ๊ฐ๋ ๋ธ๋๋ ์ค๋ฆฌ์ง๋ ๋ธ๋์ ๋ณต์ฌ๋ณธ!
    
    โ deep ์์ฑ์ ์๋ตํ๋ฉด ๋ธ๋ผ์ฐ์ ์ ๋ฐ๋ผ ๊ธฐ๋ณธ๊ฐ์ด ๋ฌ๋ผ์ง๊ฑฐ๋ ์๋ฌ๋ฅผ ๋ฐ์์ํฌ์ ์๋ค. ***๊ผญ ์จ์ฃผ์!***
    
    ```javascript
    //๊ธฐ๋ณธ ๋ฌธ๋ฒ
    let node = document.importNode(externalNode, deep);
    
    //์ฌ์ฉ ์์ (mdn ์์)
    let iframe = document.getElementsByTagName("iframe")[0];
    let oldNode = iframe.contentDocument.getElementById("myNode");
    
    let newNode = document.importNode(oldNode, true); //true - ์์ ์์๊น์ง ๊ฐ์ ธ์
    document.getElementById("container").appendChild(newNode);
    ```
    

- **node.cloneNode(deep)**
    
    : ์ด ๋ฉ์๋๋ฅผ ํธ์ถํ Node ์ ๋ณต์ ๋ Node๋ฅผ ๋ฐํํ๋ค.
    
    - deep - ๋ถ๋ฆฌ์ธ ํ์. ๋ธ๋๋ฅผ ๊ฐ์ ธ์ฌ ๋ ๋ธ๋์ ์์ ์์๋ค์ ํฌํจํ์ฌ ๊ฐ์ ธ์ฌ ๊ฒ์ธ์ง ์ฌ๋ถ. `๊ผญ ์จ์ฃผ์`
    
    โ deep ์์ฑ์ ์๋ตํ๋ฉด ๋ธ๋ผ์ฐ์ ์ ๋ฐ๋ผ ๊ธฐ๋ณธ๊ฐ์ด ๋ฌ๋ผ์ง๊ฑฐ๋ ์๋ฌ๋ฅผ ๋ฐ์์ํฌ์ ์๋ค. ***๊ผญ ์จ์ฃผ์!***
    
    โ ํ๊ทธ ์์ ํ์คํธ ์์๋ ์์ ์์๊ธฐ ๋๋ฌธ์, deep ์ต์์ false ๋ก ํ๋ฉด ํ์คํธ๋ ์ ๊ฐ์ ธ์จ๋ค.
    
    โ ํด๋ก ํ ๋ธ๋๋ฅผ ๋ณ์์ ์ ์ฅํด ๋ถ๋ชจ์์์ append ์์ผ์ฃผ์ง ์์ผ๋ฉด ๋ฌธ์์ ๋ํ๋์ง ์๋๋ค.
    
    โ ํด๋ก ํ ๋ธ๋๋ฅผ ๋ฐํํ๋ค.
    
    ```javascript
    let dupNode = node.cloneNode(true);
    //node - ์๋ณธ ๋ธ๋
    //dupNode - ํด๋ก  ๋ธ๋
    //true -> ์์ ๋ธ๋๊น์ง ๋ณต์ ํ๋ผ.
    
    //MDN ์์
    let p = document.getElementById("para1");
    let cloneP = p.cloneNode(true);
    ```
    

### ๐งฉย APPEND


> โ ๏ธ **์ถ๊ฐ(append, ๋ธ๋ ์ฐ๊ฒฐ) ์, ์ฃผ์ํ  ์ !**   
> ๐ย ๋ง์ฝ ์ฃผ์ด์ง ๋ธ๋๊ฐ ์ด๋ฏธ ๋ฌธ์์ ์กด์ฌํ๋ ๋ธ๋๋ฅผ ์ฐธ์กฐํ๊ณ  ์๋ค๋ฉด `insertBefore()`, `append()` ์ย `appendChild()`ย ๋ฉ์๋๋ ๋ธ๋๋ฅผ ํ์ฌ ์์น์์ ์๋ก์ด ์์น๋ก ์ด๋์ํจ๋ค!ย    
> (๋ฌธ์์ ์กด์ฌํ๋ ๋ธ๋๋ฅผ ๋ค๋ฅธ ๊ณณ์ผ๋ก ๋ถ์ด๊ธฐ ์ ์ ๋ถ๋ชจ ๋ธ๋๋ก ๋ถํฐ ์ง์๋ฒ๋ฆด ํ์๋ ์๋ค.   
> โ ํ ๋ธ๋๊ฐ ๋ฌธ์์์ ๋ ์ง์ ์ ๋์์ ์กด์ฌํ  ์ ์๊ธฐ ๋๋ฌธโฆ!


- **node.insertBefore(์ฝ์ํ  ๋ธ๋, ๊ธฐ์ค์  ๋ธ๋)**
    
    : ๋ถ๋ชจ ๋ธ๋ ์์ ๊ธฐ์ค์ ์ด ๋๋ ์์ ๋ธ๋ ์์ ์์ ๋ธ๋๋ฅผ ์ฝ์
    
    โ ์ฝ์ํ  ๋ธ๋์, ๊ธฐ์ค์  ๋ธ๋๋ ํ์  ์ฌ์ด๊ฐ ๋๋ค.
    
    โ ์ถ๊ฐ๋ ์์ ๋ธ๋๋ฅผ ๋ฐํ.
    
    ```javascript
    //๋ฌธ๋ฒ
    ๋ถ๋ชจ๋ธ๋.insertBefore(์ฝ์ํ  ๋ธ๋, (๋ถ๋ชจ ๋ธ๋์ ์์ ์ค) ๊ธฐ์ค์  ๋ธ๋);
    
    //์ด๋ฐ ํํ๋ผ๊ณ  ๋ณผ ์ ์๋ค.
    parentDiv.insertBefore(sp1, sp2.nextSibling);
    ```
    
    ```html
    <๋ถ๋ชจ๋ธ๋>
    	<์์๋ธ๋1></์์๋ธ๋1>
    	<์์๋ธ๋2></์์๋ธ๋2>
    	<์ฝ์ํ ๋ธ๋></์ฝ์ํ ๋ธ๋>   <!-- ์ฌ๊ธฐ์ ์ฝ์๋์๋ค --> 
    	<๊ธฐ์ค์ ๋ธ๋></๊ธฐ์ค์ ๋ธ๋>
    </๋ถ๋ชจ๋ธ๋>
    ```
    

- **element.append(๋ธ๋)**
    
    : element์ ๋ง์ง๋ง ์์ ์์๋ก ๋ธ๋๋ฅผ ์ถ๊ฐํ๋ค.
    
    โ IE ๋ ์ง์ ์๋๋ค. IE ์ง์์ด ํ์ํ  ๋ ๋์  `.appendChild()` ์ฌ์ฉ
    
    โ ๋ฌธ์์ด(text node)๋ ๋ฃ์ด์ค ์ ์๋ค. `body.append(โjust text')`
    
    โ ์ฌ๋ฌ๊ฐ์ ์์ ์์๋ฅผ ํ๋ฒ์ ๋ฃ์ด ์ค ์ ์๋ค. `body.append(div, โhelloโ, p)`
    
    โ `undefined` ๋ง ๋ฐํํ๋ค. ๋ฐํํ๋ ๊ฐ ์์.
    

- **node.appendChild(๋ธ๋)**
    
    : node์ ๋ง์ง๋ง ์์ ์์๋ก ๋ธ๋๋ฅผ ์ถ๊ฐํ๋ค.
    
    โ `.append()`๋ณด๋ค ํธํ์ฑ์ด ์ข๋ค. IE5 ๋ถํฐ ์ง์
    
    โ ๋ฌธ์์ด(text node)์ ๋ฃ์ด ์ค ์ ์๋ค. ์ค์ง **Node Object** ๋ง ๋ฃ์ ์ ์๋ค.
    
    โ ํ ๋ฒ์ ์ค์ง ํ๋์ ๋ธ๋๋ง ์ถ๊ฐํ  ์ ์๋ค.
    
    โ ์ถ๊ฐ๋ ์์ ๋ธ๋๋ฅผ ๋ฐํํ๋ค. (๋ฆฌํด๊ฐ ์๋ค.)
    
    ```javascript
    document.body.appendChild(div);  //์์ ์์๊ฐ ์ถ๊ฐ๋์๋ค.
    //๋ฐํ๊ฐ : <div id="box"><p class="para"></p></div>
    ```
    

> ๐ค **append() ์ appendChild() ๋น๊ต**
> 
> - ๊ณตํต์  : ๋๋ค `parent.append(child)` ํํ๋ก parent ์ ๋ง์ง๋ง ์์ ์์๋ก child ๋ฅผ ์ถ๊ฐํจ.
> - ๋น๊ต ํ
>    
>    
>    |  | append() | appendChild() |
>    |---|:---:|:---:|
>    | ๋ธ๋ ๊ฐ์ฒด(Node Object) | O | O |
>    | ๋ฌธ์์ด(text Node) | O | X |
>    | ๋ฐํ๊ฐ(return) | X | O |
>    | ๋ค์ค ๊ฐ ํ์ฉ | O | X |
>    | ์ง์ ๋ธ๋ผ์ฐ์  | IE ์ง์ ์ํจ | IE 5๋ถํฐ ์ง์ |
>
> > ์ฐธ๊ณ ์๋ฃ
> >
> > [MDN append()](https://developer.mozilla.org/en-US/docs/Web/API/Element/append)  /  [MDN appendChild()](https://developer.mozilla.org/ko/docs/Web/API/Node/appendChild)   
> > [๋จ์์ฃผ๊ฐ๋ฐ์๋ ํฐ์คํ ๋ฆฌ](https://webruden.tistory.com/634)
> 
<br/>

### ๐งฉย READ

โ ๏ธย querySelector๋ IE 9์ด์ ์ฌ์ฉ๊ฐ๋ฅ

- **document.querySelector('.className li');**
    
    : ์ ํ์์ ์ผ์นํ๋ ๋ฌธ์ ๋ด ์ฒซ ๋ฒ์งธย element๋ฅผ ๋ฐํ
    
    โ ์ผ์นํ๋ ์์๊ฐ ์์ผ๋ฉดย `null`์ ๋ฐํ
    
    โ ๋ณ์์ ํ ๋นํ๋ฉด ํด๋น element๋ฅผ ์กฐ์ํ  ์ ์๋ค.
    
    โ querySelector ๋ ์ ํ์์ ํด๋นํ๋ ์์๊ฐ ์ฌ๋ฌ๊ฐ์ฌ๋ ์ฒซ๋ฒ์งธ ์๋ฆฌ๋จผํธ๋ง ๊ฐ์ ธ์จ๋ค.
    
    โป ์ฟผ๋ฆฌ๋ฅผ ๋ ๋ฆฌ๋ค = ์กฐํํ๋ค
    
    ```javascript
    let oneTweet = document.querySelector('.tweet')
    ```
    

- **document.querySelectorAll('li');**
    
    : ์ ํ์์ ์ผ์นํ๋ ๋ชจ๋ ย element๋ฅผ NodeList ๋ก ๋ฐํ 
    
    โ NodeList ๋ผ๋ ์ ์ฌ ๋ฐฐ์ด ๊ฐ์ฒด(Array-like Object)๋ก ๋ฐ์์จ๋ค. (for๋ฌธ ์ฌ์ฉ ๊ฐ๋ฅ)
    

- **document.getElementById('idName')**
    
    : id ๊ฐ์ผ๋ก HTML ์๋ ๋จผํธ๋ฅผ ๊ฐ์ ธ์จ๋ค.
    

- **document.getElementsByClassName('className')**
    
    : class ๋ค์์ผ๋ก ์๋ ๋จผํธ๋ค์ ๊ฐ์ ธ์จ๋ค. (๊ทธ๋์ Elements)
    
    โ NodeList ๋ผ๋ ์ ์ฌ ๋ฐฐ์ด ๊ฐ์ฒด(Array-like Object)๋ก ๋ฐ์์จ๋ค. (for๋ฌธ ์ฌ์ฉ ๊ฐ๋ฅ)
    

    ```javascript
    const idElement = document.getElementById('idName');
    const classElement = document.getElementsByClassName('className');
    //ํด๋์ค ๋ค์์ผ๋ก ๊ฐ์ ธ์ค๋ฉด html ์ฝ๋ ์์ผ๋ก ๊ฐ์ ธ์จ๋ค. ๊ทธ๋์ element's' ์.
    //์ด๋ ๊ฒ ๊ฐ์ ธ์จ ๊ฒ์ ๋ฐฐ์ด์ด ์๋. NodeList = ์ ์ฌ ๋ฐฐ์ด ๊ฐ์ฒด
    //Array.from() ์ผ๋ก ๋ฐฐ์ด๋ก ๋ฐ๊ฟ ์ ์์.

    //๋น๊ต์  ์ต์  querySelector, querySelectorAll
    //๊ฐ์ฅ ํธ๋ฆฌ! ์ ์ฉ! IE 9์ด์ ์ฌ์ฉ๊ฐ๋ฅ
    //CSS ์ ํ์๋ฅผ ์กฐํฉํ์ฌ ํธํ๊ฒ ๊ฐ์ ธ์ฌ ์ ์์.
    //querySelector -> ์ ํจํ ๊ฒ ํ๋๋ง ๊ฐ์ ธ์ด(์ฒซ๋ฒ์งธ๋ง)
    //querySelectorAll -> ํด๋นํ๋ ๊ฒ ๋ค. NodeList ๋ก ๊ฐ์ ธ์ด
    const query = document.querySelector('.className li');
    const queryAll = document.querySelectorAll('li');
    ```

<br/>

### ๐งฉย UPDATE

**๋ด์ฉ ๋ฐ๊พธ๊ธฐ**

- **node.textContent**
    
    : ์์ ์์ ์๋ ๋ด์ฉ ๋ฐํ
    
    โ textContent, innerText, innerHTML ์ค์์ **๊ฐ์ฅ ๊ถ์ฅ** ๋๋ค.
    
    - .textContent;  โ ๋ด๋ถ ํ์คํธ ๋ฆฌํด
    - ๋ธ๋.textContent = 'ํ์คํธ';  โ ๋ด๋ถ ํ์คํธ ๋์ฒด
    
    ```javascript
    const oneDiv = document.creatElement('div');
    oneDiv.textContent = 'happy';
    ```
    

> ๐ค **textContent vs innerHTML**
>
> nnerHTML ์ฌ์ฉ์ ๊ผญ ํ์ํ์ง ์์ผ๋ฉด ์ง์ํ์.   
> HTML tag๋ฅผ ์ง์  ์ฝ์ํ์ฌ ์คํํ๋ ํํ์ ๋ฉ์๋๋ ๋ณด์ ๋ฌธ์ ๊ฐ ์๋ค.  
> ์๋ฅผ ๋ค๋ฉด, `<script>`๋ฅผ ํ์ฉํ์ฌ ๊ฐ์ ๋ก ํด์ปค๊ฐ ์ํ๋ ์คํฌ๋ฆฝํธ๋ฅผ ์คํ์ํค๋ XSS Attack ๊ฐ์ ํดํน์ ์ทจ์ฝํ๋ค. 
>
> โ ๊ณต๊ฒฉ์ ์ฌ์ง๋ฅผ ์ฃผ์ง ์๊ฒ ๊ฐ๋ฅํ ํ **textContent** ๋ฅผ ์ฌ์ฉํ์.

<br/>

**ํด๋์ค ์ถ๊ฐ์ ๊ฑฐ**

- **element.classList**
    
    : ์์์ ํด๋์ค ์ ๋ณด๊ฐ ๋ด๊ฒจ์๋ค.
    
    โ ๋ฃ์ด์ค์ผ๋  class ๊ฐ ํ๋์ด๋ฉด `el.classList = 'class-name'` ์ด๋ ๊ฒ ๋ฃ์ด์ค๋ ๋๋ค.
    

- **.classList.add('ํด๋์ค๋ช')**
    
    : ์์์ ํด๋์ค ์ถ๊ฐํ๊ธฐ
    

- **.classList.remove('ํด๋์ค๋ช')**
    
    : ์์์ ํด๋์ค ์ ๊ฑฐํ๊ธฐ
    

**๋ค๋ฅธ ์์ฑ ์ถ๊ฐ์ ๊ฑฐ**

- **element.setAttribute(โnameโ, โsubmit-btnโ)**
    
    : ํน์  ์์ฑ์ ๊ฐ์ ์์์ ๋ฃ์ด์ค ์ ์๋ค.
    
    โ ์ ๋ฌ์ธ์ (โ์์ฑ๋ชโ, โ์์ฑ๊ฐโ)
    
    โ ๋ง์ฝ ์์ฑ์ด boolean ๊ฐ์ด๋ผ๋ฉด (โ์์ฑ๋ชโ, โโ) or (โ์์ฑ๋ชโ, true)
    
    ```javascript
    const btn = document.querySelector("button");
    
    btn.setAttribute("name", "submit-btn");
    btn.setAttribute("disabled", "")
    ```
    
- **element.removeAttribute(โ์์ฑ๋ชโ)**
    
    : ํน์  ์์ฑ์ ์ ๊ฑฐํ  ์ ์๋ค.
    
<br/>    

### ๐งฉย DELETE

- **element.remove()**
    
    : ํด๋น ์์๊ฐ ์ญ์ ๋๋ค.
    
    ```javascript
    //class ๊ฐ tweet ์ธ ๊ฒ๋ง ์ง์ฐ๊ธฐ(์์๊ฐ ์ฌ๋ฌ ๊ฐ์ผ ๋)
    const tweets = document.querySelectorAll('.tweet');
    
    tweets.forEach(function(tweet){
    	tweet.remove();
    })
    
    //or
    
    for(let tweet of tweets){
    	tweet.remove();
    }
    
    ```
    
- **node.removeChild(childNode)**
    
    : ์์ ๋ธ๋๋ฅผ ์์ค๋ค. 
    
    โ ๋ถ๋ชจ ๋ธ๋์์ ๋ถ๋ชจ-์์๊ด๊ณ๋ฅผ ๋์ด DOM ํธ๋ฆฌ์์ ํด์ ํ๋ค. 
    
    โ ๊ด๊ณ๋ฅผ ๋์ ํด๋น ๋ธ๋์ ์ฐธ์กฐ๋ฅผ ๋ฐํํ๋ค.
    
    ```javascript
    //์์ ๋ธ๋ ์ ๋ถ ์ ๊ฑฐํ๊ธฐ
    const container = document.querySelector('#container');
    
    while (container.firstChild) {
      container.removeChild(container.firstChild);
    }
    ```
    
<br/>

### ๐งฉย ์์

```javascript
const searchButton = document.querySelector('.gN089b');

//ํด๋์ค ์ด๋ฆ ๋ฃ๊ณ  ๋นผ๊ธฐ
searchButton.classList.remove('gN089b');
searchButton.classList.contains('gN089b'); //ํด๋น ํด๋์ค๋ค์์ด ์๋์ง

//์์ ํ์คํธ ๋ฝ์์ค๊ธฐ, ๋์ฒดํ๊ธฐ
searchButton.textContent; //๋ด๋ถ ํ์คํธ ๋ฆฌํด
searchButton.textContent = 'zero'; //๋ด๋ถ ํ์คํธ ๋์ฒด

//์์ ์ง์ฐ๊ธฐ
const el = document.querySelector('.link_partner')
searchButton.removeChild(el);

//์๋ ๋จผํธ ๋ง๋ค๊ธฐ createElement('div')
const el2 = document.createElement('div');
el2.textContent = "new";
//์์ ์ถ๊ฐํ๊ธฐ
searchButton.appendChild(el2); //๋์ ์์ ์์ฑ
//or
searchButton.innerHTML = '<div>new</div>';
```