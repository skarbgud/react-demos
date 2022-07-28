# 1. ****Render JSX****

React의 템플릿 구문을 JSX라고 합니다. JSX에서는 HTML 태그를 JavaScript 코드에 직접 넣을 수 있습니다. 

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled.png)

ReactDOM.render()는 JSX를 HTML로 변환하고 지정된 DOM 노드로 렌더링하는 메소드입니다.

실행결과

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%201.png)

# 2. JSX에서 자바스크립트 사용하기(**Use JavaScript in JSX)**

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%202.png)

JSX에서 JavaScript를 사용할 수도 있습니다. HTML 구문의 시작으로 꺾쇠 괄호( < )를 사용하고

JavaScript 구문의 시작으로 중괄호( { )를 사용합니다.

Tips. [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

**`map()`**
 메서드는 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환합니다.

실행결과

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%203.png)

# 3. JSX에서 배열 사용하기 (****Use array in JSX)****

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%204.png)

JavaScript 변수가 배열인 경우 JSX는 암시적으로 배열의 모든 구성원을 연결합니다.

실행결과

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%205.png)

# 4. 컴포넌트 정의 (****Define a component)****

**컴포넌트란?** **component : 재활용 가능한 UI 구성 단위**

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%206.png)

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

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%207.png)

# 5. ****this.props.children****

React는 `this.props.children`**을 사용하여 구성 요소의 하위 노드에 액세스합니다.**

## props란?

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%208.png)

<리액트 공식문서>

그럼 props.children이란?

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%209.png)

<리액트 공식문서>

Welcome 이라는 컴포넌트를 정의했으면 해당 태그 사이에 내용을 담으면 Welcom 컴포넌트에서는 해당 값을 props.children으로 접근해서 해당 값을 사용할 수 있다.

좀 더 쉽게 아래의 예시를 보자

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2010.png)

기차가 있습니다. 기차의 이름이 `ktx 산천` 일 수도 있고 `무궁화` 일수도 있습니다.

클래스의 이름은 그대로 두면서 props.children의 값을 다르게 전달 받아서 똑같은 컴포넌트에서 다른 열차의 이름을 출력하고 싶다면 아래와 같이 됩니다.

[ktx 산천] 일 경우

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2011.png)

[무궁화] 일 경우

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2012.png)

여러개의 요소를 사용한 넣은 경우

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2013.png)

`this.props.children`에는 세 가지 유의점이 있습니다. 

1. 구성 요소에 자식 노드가 없으면 값은 `undefined`입니다. 
2. 단일 자식 노드인 경우 개체입니다.
3. 자식 노드가 여러 개인 경우 배열입니다.
