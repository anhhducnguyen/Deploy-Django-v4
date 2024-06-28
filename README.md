# How to deploy app Django use Heroku

### Cách này đẩy cả file `db.sqlite3` lên `Heroku`


#### Điều kiện tiên quyết

1. Đảm bảo `requirements.txt` chứa các thư viện sau

    ```python
    Django==5.0.6
    django-heroku==0.3.1
    gunicorn==22.0.0
    ```

2. Đảm bảo `Procfile` có chứa đoạn mã sau, trong đó `myproject` là tên dự án lúc bạn tạo `django`

    ```python
    web: gunicorn myproject.wsgi --log-file -
    ```

3. Đảm bảo `settings.py` có chứa

- Giúp không bị mất `css`

  ```python
  import django_heroku
  django_heroku.settings(locals())
  ```

- Đảm bảo có chứa tên miền
  
  ```python
  ALLOWED_HOSTS = [
      'chat-123-b5f27fe98cab.herokuapp.com',
  ]
  ```


**Setep 1.** Tạo app trên `Heroku` tại [Heroku](https://dashboard.heroku.com/)

**Setep 2.** Sử dụng `powershell` di chuyển đến thư mục bạn đang làm việc
  
  ```
   cd E:\2ndSemester3rdYear\applicationAnalysis\Myproject
  ```

**Setep 3.** Đăng nhập `Heroku` bằng cách sử dụng câu lệnh sau trên `powershell`

  ```
  heroku login
  ```

**Setep 4.** Tạo kho lưu trữ

```
git init
```

**Setep 5.** Kết nối với `chat-123` tên app mà bạn đã đặt trên `Heroku`

```
heroku git:remote -a chat-123
```


```
git add .
```

```
git commit -m "commit"
```

```
git push heroku master
```

**Setep 6.** Nếu có lỗi hãy sử dụng sau đó `push` lại

```
heroku config:set DISABLE_COLLECTSTATIC=1
```
