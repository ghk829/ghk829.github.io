---
layout: post
title:  "react toggle event"
date:   2019-06-30
excerpt: "react toggle event"
tag:
- react
- javascript

comments: false
---

# toggle css 처리

어떤 앱을 이용하다가 UI에서 클릭하면 디테일이 나올 줄 알았는데
나오지 않아서 실망했다.
이미지 등 디테일 항목을 보고 싶을 떄 toggle event로 p tag를 보여주면 좋겠다고 생각했다.

``` javascript 


import React from 'react';
import './arrow.css';
const arrow = require("./down-arrow.svg")


export default class Arrow extends React.Component{

  constructor(props){
    super(props);

    this.state = {
      active: false
    }

    this.toggleClass = this.toggleClass.bind(this); // bind 해줘야 this 활용가능
    
  }

  toggleClass() {
        const currentState = this.state.active;
        this.setState({ active: !currentState });
    };

 render(){
   return(
     
            <div onClick={this.toggleClass} >
            
            <img src={arrow} className={this.state.active ? 'arrow-click': 'arrow-nonclick'}  alt="arrow"/>

            <p className={this.state.active ? 'p-click': 'p-nonclick'}>{this.props.text}</p>
            
            </div>
                
   )


 }
}




```

일단 먼저 해당 기능을 컴퍼넌트화시켰는데, 이유는 arrow 이미지가 toggle 함에 따라 90 정도 회전되어야 하는 것도 있지만, 글자가 안 보이다가 보여야 하는 효과도 있어야 하기 때문이다.

이는 **state**를 활용하면 좋다.

처음에는 **refs**를 활용해야겠다고 생각했는데, 같은 컴퍼넌트에서 똑같은 이벤트로 인해 바뀌면 돼서 **state**로 처리했다.


``` javascript

 // 단순히 toggle 체크하는 state


  toggleClass() {
        const currentState = this.state.active;
        this.setState({ active: !currentState });
    };


```



``` javascript

  // className을 조건식으로 하면 해당 css effect를 쉽게 처리할 수 있다.
  // 물론 p 태그나 arrow 태그처럼 일반화된 태그에 대해 바로 css를 먹이는 건...ㅎㅎ

   <div onClick={this.toggleClass} >
            
    <img src={arrow} className={this.state.active ? 'arrow': 'arrow.click'}  alt="arrow"/>

    <p className={this.state.active ? 'p': 'p.click'}>{this.props.text}</p>

    </div>



```