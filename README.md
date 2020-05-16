# React-Captcha


## React-Captcha Generator

```
$. npm i react-google-recaptcha
```

قبل از اینکه بتونید از این ماژول استفاده کنید  باید در سایت گوگل کلید جدیدی تعریف کنید و آدرس سایت خودتون رو جهت استفاده از این کلید در سایت گوگل ثبت کنید . توجه کنید اگر در سیستم محلی یا لوکال در حال تست هستید باید آدرس localhost یا پورت 127.0.0.1 رو نیز به کلید ایجاد شده معرفی کنید . تصایر صفحه وب سایت گوگل برای معرفی کلید در ادامه آموزش آورده شده است .

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
