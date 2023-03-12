---
title: "Đẩy code Create React App lên Internet miễn phí"
date: 2019-12-17
draft: false
tags: ["ReactJS"]
---

Sau khi code xong 1 ứng dụng bằng {{< link link="https://github.com/facebook/create-react-app" text="Create React App" >}}, chúng ta có thể đẩy sản phẩm lên Internet theo 1 trong 3 cách miễn phí sau chỉ với 3 bước (còn nhiều cách khác nhưng tác giả lười viết 😅):

## 1. Github Pages

Giả sử bạn đã có tài khoản trên {{< link link="https://github.com/" text="github" >}} là _robinhuy_, và có 1 repository chứa source code ứng dụng tạo bởi {{< link link="https://github.com/facebook/create-react-app" text="Create React App" >}} là _react-app_.

**Bước 1**: Cài thêm thư viện {{< link link="https://github.com/tschaub/gh-pages" text="gh-pages" >}} (devDependencies)

```bash
npm i gh-pages --save-dev
```

**Bước 2**: Sửa lại file **package.json**, bổ sung thêm thuộc tính **homepage**, và **scripts**

![Đẩy code React lên Github](/images/config-package.json-to-deploy-github.png)

**Bước 3**: Deploy lên Github Pages bằng lệnh

```bash
npm run deploy
```

Sau đó truy cập ứng dụng tại địa chỉ: _http://robinhuy.github.io/react-app_

## 2. ZEIT Now

**Bước 1**: Cài đặt Now CLI

```bash
npm i -g now
```

**Bước 2**: Tạo tài khoản trên {{< link link="https://zeit.co/" text="https://zeit.co" >}} và đăng nhập bằng Now CLI (gõ email rồi truy cập email để xác thực)

```bash
now login
```

**Bước 3**: Đẩy code lên bằng lệnh

```bash
now
```

Chú ý nếu đẩy code lên ZEIT Now thì không cấu hình homepage như Github Pages vì mỗi project sẽ có subdomain riêng. Có thể kết nối với Github để mỗi lần push code lên Github sẽ tự động deploy lên Now.

### 3. Heroku

**Bước 1**: Tạo tài khoản trên {{< link link="https://www.heroku.com/" text="https://heroku.com" >}}, sau đó tạo 1 App (tương tự tạo repository trên Github). Truy cập mục Settings của App vừa tạo để add thêm buildpack với địa chỉ {{< link link="https://github.com/mars/create-react-app-buildpack" text="https://github.com/mars/create-react-app-buildpack" >}}

![Deploy react app lên heroku](/images/heroku-react-app-buildpack.png)

**Bước 2**: Cài {{< link link="https://devcenter.heroku.com/articles/heroku-cli#download-and-install" text="Heroku CLI" >}}, sau đó đăng nhập tương tự ZEIT Now

```bash
heroku login
```

**Bước 3**: Đẩy code lên tương tự như đẩy code lên Github

```bash
heroku git:remote -a react-app
git push heroku master
heroku open
```

Chú ý nếu đẩy code lên Heroku thì không cấu hình homepage như Github Pages vì mỗi project sẽ có subdomain riêng. Có thể kết nối với Github để mỗi lần push code lên Github sẽ tự động deploy lên Heroku.
