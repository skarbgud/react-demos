# 1. ****Render JSX****

React의 템플릿 구문을 JSX라고 합니다. JSX에서는 HTML 태그를 JavaScript 코드에 직접 넣을 수 있습니다. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8eb50ca-573f-47b1-8fbc-7d007e3f58de/Untitled.png)

ReactDOM.render()는 JSX를 HTML로 변환하고 지정된 DOM 노드로 렌더링하는 메소드입니다.

실행결과

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/94b53cdb-d653-4256-bfb7-fc99315efc36/Untitled.png)

# 2. JSX에서 자바스크립트 사용하기(**Use JavaScript in JSX)**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/afd0959d-0492-4bdd-8acb-5f3c26cad758/Untitled.png)

JSX에서 JavaScript를 사용할 수도 있습니다. HTML 구문의 시작으로 꺾쇠 괄호( < )를 사용하고

JavaScript 구문의 시작으로 중괄호( { )를 사용합니다.

Tips. [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

**`map()`**
 메서드는 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환합니다.

실행결과

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93a04ab5-1465-43ca-a590-25d3736b7a72/Untitled.png)

# 3. JSX에서 배열 사용하기 (****Use array in JSX)****

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/43d9ef36-296a-498c-b63e-bb1a460399af/Untitled.png)

JavaScript 변수가 배열인 경우 JSX는 암시적으로 배열의 모든 구성원을 연결합니다.

실행결과

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0012a902-aa02-420e-8c78-d51ec9548cc2/Untitled.png)

# 4. 컴포넌트 정의 (****Define a component)****

**컴포넌트란?** **component : 재활용 가능한 UI 구성 단위**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6c905e6a-b0e9-4b8f-b3a2-8fc146abdd6b/Untitled.png)

React를 사용할 때는 컴포넌트를 class 또는 함수로 정의할 수 있습니다. React 컴포넌트 class를 정의하려면 `React.Component`를 상속받아야 합니다.

여기서 `[render()](https://ko.reactjs.org/docs/react-component.html#render)`는 `React.Component`의 하위 class에서 *반드시*  정의해야 하는 메서드입니다. 

Class에는 속성이 있으며 `this.props.[속성]`을 사용하여 `HelloMessage name='John'`의 this.props.name이 John인 것처럼 구성 요소에 액세스할 수 있습니다.

Class 이름의 첫 글자는 대문자이여야 합니다. 그렇지 않으면 React에서 오류가 발생합니다. 

예를 들어 컴포넌트의 이름으로 HelloMessage는 괜찮지만 helloMessage는 허용되지 않습니다. 

그리고 React 컴포넌트에는 최상위 자식 노드가 하나만 있어야 합니다.

```jsx
// No!
class HelloMessage extends React.Component {
  render() {
    return
			<h1> Hello {this.props.name}</h1>
			<p>some text</p>;
  }
}

// OK!
class HelloMessage extends React.Component {
  render() {
    return 
		<div> 
      <h1> Hello {this.props.name}</h1>
			<p>some text</p>;
		</div>
  }
}
```

실행결과

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bd9f0779-d935-4689-9ed5-6606865fefe4/Untitled.png)

# 5. ****this.props.children****

React는 `this.props.children`**을 사용하여 구성 요소의 하위 노드에 액세스합니다.**

## props란?

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/716bc683-9425-4b1f-8699-717a787d43c1/Untitled.png)

<리액트 공식문서>

그럼 props.children이란?

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/24f929a1-bd13-45b9-b0dc-4c2c7b7100f6/Untitled.png)

<리액트 공식문서>

Welcome 이라는 컴포넌트를 정의했으면 해당 태그 사이에 내용을 담으면 Welcom 컴포넌트에서는 해당 값을 props.children으로 접근해서 해당 값을 사용할 수 있다.

좀 더 쉽게 아래의 예시를 보자

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c56cd4d-7c23-4cc6-b2c9-ca5a9586a2ab/Untitled.png)

기차가 있습니다. 기차의 이름이 `ktx 산천` 일 수도 있고 `무궁화` 일수도 있습니다.

클래스의 이름은 그대로 두면서 props.children의 값을 다르게 전달 받아서 똑같은 컴포넌트에서 다른 열차의 이름을 출력하고 싶다면 아래와 같이 됩니다.

[ktx 산천] 일 경우

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d7928c56-cd2f-4cff-965c-0949d2d670dd/Untitled.png)

[무궁화] 일 경우

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/70988db4-7912-468b-b4c9-744ef732716b/Untitled.png)

여러개의 요소를 사용한 넣은 경우

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/87c5df39-75b9-4a52-9b88-0794e013f277/Untitled.png)

`this.props.children`에는 세 가지 유의점이 있습니다. 

1. 구성 요소에 자식 노드가 없으면 값은 `undefined`입니다. 
2. 단일 자식 노드인 경우 개체입니다.
3. 자식 노드가 여러 개인 경우 배열입니다.
