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


# 6. **PropTypes**

`props`구성 요소에는 React에서 호출되는 많은 특정 속성이 있으며 모든 유형이 될 수 있습니다.

때때로 이러한 props를 검증하는 방법이 필요합니다. 사용자가 구성 요소에 아무 것도 입력할 수 있는 자유를 원하지 않습니다.

React에는 이에 대한 솔루션이 있으며 이를 PropTypes라고 합니다.

```jsx
class MyTitle extends React.Component {
  static propTypes = {
    title: PropTypes.string.isRequired,
  }
  render() {
    return <h1> {this.props.title} </h1>;
  }
}
```

위의 구성 요소 `MyTitle`에는  `title`있습니다. PropTypes는 제목이 필수이고 값이 문자열(PropTypes.string.isRequired)이어야 한다고 React에 알려줍니다.

이제 `Title`숫자 값을 지정합니다.

```jsx
var data = 123;

ReactDOM.render(
  <MyTitle title={data} />,
  document.getElementById('example')
);
```

이는 props가 유효성 검사를 통과하지 못했고 콘솔에 오류 메시지가 표시됨을 의미합니다.

`Warning: Failed propType: Invalid prop `title` of type `number` supplied to `MyTitle`, expected `string`.`

실행결과

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2014.png)

PS props에 기본값을 지정하려면 `defaultProps`.

```jsx
class MyTitle extends React.Component {
  constructor(props) {
    super(props)
  }
  static defaultProps = {
    title: 'Hello World',
  }
  render() {
    return <h1> {this.props.title} </h1>;
  }
}

ReactDOM.render(
  <MyTitle />,
  document.getElementById('example')
);
```

# 7. ****DOM 노드 찾기****

때로는 구성 요소에서 DOM 노드를 참조해야 합니다. React는 `ref`에 의해 생성된 인스턴스에 DOM 노드를 연결하는 속성을 제공합니다 `React.createRef()`.

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2015.png)

이 구성 요소가 DOM에 마운트된 후에만 수행할 수 있다는 점에 유의하십시오. 그렇지 않으면 `null`.

# 8. ****this.state****

React는 구성 요소를 상태 기계로 생각하고 구성 `this.state`요소의 상태를 유지하고 구성 요소 `this.setState()`를 업데이트 `this.state`하고 다시 렌더링하는 데 사용합니다.

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2016.png)

`onClick`, `onKeyDown`, `onCopy`등과 같이 구성 요소 속성을 사용하여 이벤트 핸들러를 등록할 수 있습니다 

this.state가 `false` 일때 `var text = haven\'t liked`

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2017.png)

this.state가 `true` 일때 `var text = like`

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2018.png)

# 9. ****this.state****

React의 디자인 철학에 따르면 `this.state`구성 요소의 상태를 설명하고 사용자 상호 작용을 통해 `this.props`변경되며 구성 요소의 속성을 설명하고 안정적이고 변경할 수 없습니다.

이후 `value`, `<input>`, `<textarea>`, `<option>`과 같은 Form 컴포넌트의 속성은 사용자 입력에 영향을 받지 않습니다. 사용자 입력에 대한 응답으로 값에 액세스하거나 업데이트하려면 onChange 이벤트를 사용할 수 있습니다.

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2019.png)

실행결과

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2020.png)

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2021.png)

# 10. ****구성 요소 수명 주기****

[구성 요소에는 수명 주기](https://facebook.github.io/react/docs/working-with-the-browser.html#component-lifecycle) 의 세 가지 주요 부분이 있습니다 . 마운팅(DOM에 삽입됨), 업데이트(재 렌더링 중) 및 마운트 해제(DOM에서 제거됨). React는 이러한 수명 주기 부분에 대한 후크를 제공합니다. `will`메서드는 일이 발생하기 직전에 호출되고 `did`메서드는 일이 발생한 직후에 호출됩니다.

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2022.png)

실행결과

![Animation.gif](https://github.com/skarbgud/Github-User-Content/blob/main/Animation.gif?raw=true)

# 11. ****Ajax****

서버 또는 API 공급자로부터 구성 요소의 데이터를 가져오는 방법은 무엇입니까? 대답은 Ajax를 사용하여 의 이벤트 핸들러에서 데이터를 가져오는 것입니다 `componentDidMount`. 서버 응답이 도착하면 데이터를 저장 `this.setState()`하여 UI를 다시 렌더링하도록 합니다.

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2023.png)

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2024.png)

호출된 url을 통해 얻은 `result` 라는 변수의 값으로 결과 값을 가져와서

해당 값의 [0]번째를 lastGist로 할당해서 해당 값에서 `html_url`값과 `owner.login`값을 가져와서 state 상태값에 세팅하여서 사용합니다.

![Untitled](https://raw.githubusercontent.com/skarbgud/Github-User-Content/main/Untitled%2024.png)