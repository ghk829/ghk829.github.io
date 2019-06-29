---
layout: post
title:  "react chatbot UI"
date:   2019-06-29
excerpt: "react chatbot UI"
tag:
- react
- javascript

comments: false
---

# React Chatbot UI

요즘 어떤 웹사이트를 접속하든 chatbot UI가 많이 보인다.

그래서 react 공부하면서 어떻게 적용하는 지 알아보았다.

yarn 및 npm 에서 react-chat-widget를 설치하면 해당 컴퍼넌트를 쉽게 다운받을 수 있다.


``` json
{
  "name": "runner",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "react": "^16.8.2",
    "react-dom": "^16.8.2",
    "react-scripts": "2.1.5",
    "react-chat-widget":"latest"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": "react-app"
  },
  "browserslist": [
    ">0.2%",
    "not dead",
    "not ie <= 11",
    "not op_mini all"
  ]
}

```

단순히 컴퍼넌트만 JSX로 호출하면 흔히 웹사이트에서 볼 수 있는 UI를 적용할 수 있다.

``` javascript
import { Widget } from 'react-chat-widget';

class component extends React.Component{
  render(){
    return (<Widget/>)
  }
}

```


# Sample

<iframe height="400px" width="100%" src="https://repl.it/@ghk829/chatComponent?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>