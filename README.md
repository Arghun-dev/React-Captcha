# React-Captcha


## React-Captcha Generator

```
$. npm i react-captcha-generator
```

Example:

```
import React, { Component } from 'react';
import './App.css';
import RCG from 'react-captcha-generator';
 
class App extends Component {
 
  constructor(props) {
    super(props)
    this.state = {
      captcha: ''
    }
    this.check = this.check.bind(this)
    this.result = this.result.bind(this)
    this.handleClick = this.handleClick.bind(this)
  }
 
  render() {
    return (
      <div className="App">
        <form onSubmit={this.handleClick}>
          <input type='text' className={'xxx'} ref={ref => this.captchaEnter = ref} />
          <input type='submit' />
        </form>
        <RCG result={this.result} />
      </div>
    );
  }
 
  handleClick(e) {
    e.preventDefault();
    this.check()
  }
 
  result(text) {
    this.setState({
      captcha: text
    })
  }
  
  check() {
    console.log(this.state.captcha, this.captchaEnter.value, this.state.captcha === this.captchaEnter.value)
  }
 
}
 
export default App;
```


## Implementing reCAPTCHA in ReactJS

```
$. npm i react-recaptcha
```

Then add this script tag in the head section of your app:

`<script src="https://www.google.com/recaptcha/api.js" async defer></script>`
