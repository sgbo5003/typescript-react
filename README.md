# Start TypeScript

# 11/25일 공부내용

## 8-0 Bound TypeScript + React Introduction

TypeScript와 리액트를 어떻게 같이 쓸 수 있을지 소개

## 8-1 Introduction to Typescript

Typescript
: 자바스크립트의 superset ( = 다른 언어 위에서 동작하는언어라는 뜻)

Typescript가 하는 것
개발자들이 하는 실수들을 줄여주고 더 좋은 코드를 짤 수 있게 도와준다.
(엄격한 문법)

## 8-2 Introduction to Typescript part Two

Typescript 는 인터페이스를 가지고있다.

```
const sangjun = {
  name: "sangjun",
  age: 23,
  hungry: false
}
const lynn = {
  name: "lynn",
  hungry: true
}
interface Ihuman{
  name: string;
  age?: number; // ? -> number | undefined
  hungry: boolean;
}
const helloToHuman = (human: Ihuman) => {
  console.log(`Hello ${human.name} you are ${human.age} old`)
}
helloToHuman(sangjun);
helloToHuman(lynn);
```

## 8-3 Typescript and React Introduction

Typescript를 포함한 react app 설치
npx create-react-app typescript-react-demo --typescript
or
npx create-react-app typescript-react-demo --template typescript

typescript의 설정을 바꾸고 싶으면 tsconfig.json에서 고치고, library들을 가져와 쓴다. (https://github.com/DefinitelyTyped 에 엄청 많음 )

## 8-4 React State and Typescript

Typescript 로 React app 을 좀 더 좋게 만들기 위한 방법

#12/11일 공부내용

## 8-4 React State and Typescript

typescript는 component에게 state를 줘야한다.

## 8-5 React Props and Typescript

props 와 state 를 같이 쓰는 방법
Functional Component를 어떻게 쓰는지

**Number.tsx**

```
import React from "react";
import styled from "styled-components";
const Container = styled.span``;
interface IProps {
  count: number;
}
const Number: React.FunctionComponent<IProps> = ({ count }) => (
  <Container>{count}</Container>
);
export default Number;
```

**App.tsx**

```
import React, { Component } from "react";
import Number from "./Number";
interface IState {
  counter: number;
}
class App extends Component<{}, IState> {
  state = {
    counter: 0,
  };
  render() {
    const { counter } = this.state;
    return (
      <div>
        <Number count={counter} />
        <button onClick={this.add}>Add</button>
      </div>
    );
  }
  add = () => {
    this.setState((prev) => {
      return {
        counter: prev.counter + 1,
      };
    });
  };
}
export default App;
```

## 8-6 React Events and Typescript

**Input.tsx**

```
import React from "react";
interface IInputProps {
  value: string;
  onChange: (event: React.SyntheticEvent<HTMLInputElement>) => void;
}
export const Input: React.FunctionComponent<IInputProps> = ({
  value,
  onChange,
}) => (
  <input type="text" placeholder="Name" value={value} onChange={onChange} />
);
interface IFormProps {
  onFormSubmit: (event: React.FormEvent) => void;
}
export const Form: React.FunctionComponent<IFormProps> = ({
  children,
  onFormSubmit,
}) => <form onSubmit={onFormSubmit}>{children}</form>;
```

**App.tsx**

```
import React, { Component } from "react";
import { Input } from "./Input";
import { Form } from "./Input";
import Number from "./Number";
interface IState {
  counter: number;
  name: string;
}
class App extends Component<{}, IState> {
  state = {
    counter: 0,
    name: "",
  };
  render() {
    const { counter, name } = this.state;
    return (
      <div>
        <Form onFormSubmit={this.onFormSubmit}>
          <Input value={name} onChange={this.onChange} />
        </Form>
        <Number count={counter} />
        <button onClick={this.add}>Add</button>
      </div>
    );
  }
  onChange = (event: React.SyntheticEvent<HTMLInputElement>) => {
    console.log(event.target);
  };
  onFormSubmit = (event: React.FormEvent) => {
    event.preventDefault();
  };
  add = () => {
    this.setState((prev) => {
      return {
        counter: prev.counter + 1,
      };
    });
  };
}
export default App;
```

+내껀 왜 그런지 모르겠지만
tsconfig.json에서

```
"jsx": "react"
```

이걸 변경해줘야 컴파일이 제대로 된다.
