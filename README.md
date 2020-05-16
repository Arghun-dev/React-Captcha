# React-Captcha


## React-Captcha Generator

```
$. npm i react-google-recaptcha
```

قبل از اینکه بتونید از این ماژول استفاده کنید  باید در سایت گوگل کلید جدیدی تعریف کنید و آدرس سایت خودتون رو جهت استفاده از این کلید در سایت گوگل ثبت کنید . توجه کنید اگر در سیستم محلی یا لوکال در حال تست هستید باید آدرس localhost یا پورت 127.0.0.1 رو نیز به کلید ایجاد شده معرفی کنید . تصایر صفحه وب سایت گوگل برای معرفی کلید در ادامه آموزش آورده شده است .

Label: 127.0.0.1
Domain: localhost


و نمونه کدهای زیر رو در برنامتون پیاده کنید . توضیح خاصی نداره و کاری که انجام میشه اینه که خود ابزار بررسی هویت انسان بودن کاربر رو بررسی میکنه در غیر اینصورت recaptcha رو که در state قرار دادیم ، خالی میکنه و شما با چک کردن این state متوجه میشید که آیا امنیت بر قرار هست یا خیر . دو رویداد تعریف شده که یکی ربات نبودن و دیگری مدت زمان انقضا رو کنترل میکنند .

Example:

```
import React, { Component } from "react";
import ReCAPTCHA from "react-google-recaptcha";

class Login extends Component {
  state = { username: "", password: "", recaptcha: "", error: "" };

  onreCaptchaExpire = () => {
    this.setState({
      recaptcha: ""
    });
  };

  onreCaptchaChange = e => {
    this.setState({
      recaptcha: e
    });
  };

  handleSubmit = e => {
    e.preventDefault();
    if (this.state.recaptcha === "" || this.state.recaptcha === undefined) {
      this.setState({
        error: "لطفا من ربات نیستم را انتخاب نمائید"
      });
      return;
    } else {
      this.setState({
        error: ""
      });
    }
    //continue your code
  };
  render() {
    return (
      <div style={{ padding: "50px" }}>
        <form onSubmit={this.handleSubmit}>
          <input
            style={{ display: "block", padding: "5px" }}
            type="text"
            value={this.state.username}
            onChange={e => {
              this.setState({
                username: e.target.value
              });
            }}
            placeholder="نام کاربری"
          />
          <input
            style={{ display: "block", padding: "5px" }}
            type="password"
            value={this.state.password}
            onChange={e => {
              this.setState({
                password: e.target.value
              });
            }}
            placeholder="رمز عبور"
          />
          <label style={{ color: "red", display: "block" }}>
            {this.state.error}
          </label>
          <ReCAPTCHA
            sitekey="کلید دریافت شده از گوگل"
            onChange={this.onreCaptchaChange}
            onExpired={this.onreCaptchaExpire}
          />
          <button>ورود</button>
        </form>
      </div>
    );
  }
}

export default Login;
```
