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
