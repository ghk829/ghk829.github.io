---
layout: post
title:  "expo study"
date:   2019-06-28
excerpt: "react expo"
tag:
- react
- react-native
- expo

comments: false
---

<iframe height="400px" width="100%" src="https://repl.it/@ghk829/reacttutorial?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

# react image click bind

[study repl](https://repl.it/@ghk829/reacttutorial)

이미지 클릭을 위해서 onclick 이벤트를 직접적으로 image에 event에 달면
클릭시 이벤트처리가 발생하지 않을 수 있다.

따라서 다음과 같이 <code>div tag</code>로 감싼다.

``` javascript

<div onClick={this.changeLogo}>
<img src={this.state.image} className="App-logo" alt="logo" />
</div>

```

그리고 this.changeLogo를 Component에서 정의해도, this를 다루기 위해선

constructure에서 bind this를 해줘야 한다.


``` javascript

constructor(props){
    super(props);

    this.state = {
      clicked: true,
      firefox : firefox,
      logo : logo,
      image : logo
    }

    this.changeLogo = this.changeLogo.bind(this); // bind 해줘야 this 활용가능

  }

  changeLogo(){

    if (this.state.clicked){
      this.setState({image:this.state.firefox})
   } else{
     this.setState({image:this.state.logo})
   }

   this.setState({clicked:!this.state.clicked})
  }



```

위와 같이 하면 image 클릭 이벤트마다 이미지가 바뀔 수 있다.
