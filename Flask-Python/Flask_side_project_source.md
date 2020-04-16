### 로직

1. id, pw 로그인 페이지  O
2. 회원가입 페이지 O
3. 관리자 로그인 : 데이터베이스를 이용하여 등록 회원 조회 - 미완
4. 등록된 id, pw 확인 후  successfully  O

- 참고링크 
  - [Flask Post request example](https://m.blog.naver.com/PostView.nhn?blogId=cosmosjs&logNo=221031798823&proxyReferer=https:%2F%2Fwww.google.com%2F)
  - [메세지 출력](https://growingsaja.tistory.com/272)
  - 

app.py

```python
from flask import Flask, render_template, request, flash, redirect, url_for
import sqlite3 as sql


app = Flask(__name__)
# app.secret_key = "random string"

# 데이터 베이스 등록, 조회

@app.route('/')
def home():
    return render_template("login.html")

@app.route('/login', methods=['GET', 'POST'])
def login():
    error = None

    if request.method == 'POST':
        user = request.form['userid']
        password = request.form['password']

        if user == 'admin' and password == 'admin':
            return render_template('list.html')        # render_template   : HTML 페이지 이동 === POST
            # return redirect(url_for('member_list'))  # redirect(url_for) : 해당 함수 이동   === GET
        elif user == "" or password == "":
            error = 'Invalid username or password. Please try again!'
        else:
            return redirect(url_for('success', name=user))

    return render_template('login.html', error=error)


@app.route('/new')
def new():
    return render_template('new.html')


@app.route('/addrec', methods=['GET', 'POST'])
def addrec():
    error = None

    if request.method == "POST":
        try:
            # userid = request.args.get('id')
            # name = request.args.get('name')
            # birth = request.args.get('birth')
            # area = request.args.get('area')
            # phone = request.args.get('phone')
            userid = request.form['id']
            name = request.form['name']
            birth = request.form['birth']
            area = request.form['area']
            phone = request.form['phone']

            with sql.connect("database.db") as con:
                cur = con.cursor()
                cur.execute('INSERT INTO members (id,name,birth,area,phone)'
                            'VALUES (?,?,?,?,?)', (userid,name,birth,area,phone))
                con.commit()
                error = "New Membership Successfully Added!"
        except:
            con.rollback()
            error = "Error In Insert Operation"
        finally:
            return render_template('login.html', error=error)
            con.close()
    # else:
    #     return render_template('login.html', error=error)


@app.route('/list', methods=["POST", "GET"])
def member_list():
    con = sql.connect("database.db")
    con.row_factory = sql.Row

    cur = con.cursor()
    cur.execute("SELECT * FROM members")
    #cur.execute("DELETE FROM members")
    # cur.execute('select name from sqlite_master where type="table"') # 테이블 생성 확인
    # cur.execute('DROP TABLE students')
    rows = cur.fetchall()
    return render_template('list.html', rows=rows)


@app.route('/success/<name>')
def success(name):
    return render_template("success.html", name=name)


if __name__ == '__main__':
    app.run()

```

login.html

```html
<!doctype html>
<html>
   <body>
      <h1>Login</h1>

      {% if error %}
         <p><strong>msg : </strong> {{ error }}
      {% endif %}
{#      {% if msg %}#}
{#         <p><strong>msg : </strong> {{ msg }}#}
{#      {% endif %}#}

      <form action = "/login" method = post>
         <dl>
            <dt>ID : </dt>
            <dd>
            <input type = text name = id placeholder="UserID" value = "{{request.form.userid }}">
            </dd>
            <dt>PW : </dt>
            <dd><input type = password placeholder="Password"  name = password></dd>
         </dl>
{#          <p><a href={{ url_for('new') }}><b>Sign up </b></a></p>#}
         <button type = button style="WIDTH: 60pt" onclick="location.href='/new'">New</button>
         <p><input type = submit style="WIDTH: 60pt" value = Login></p>
      </form>
   </body>
</html>
```

success.html

```html
<!DOCTYPE html>
<html>
<head>
</head>
<body>
    <h1>{{ name }} Successfully!</h1>
    <a href={{ url_for('home') }}><b>Go to Logout</b></a></p>
</body>
</html>
```

new.html

```html
<!DOCTYPE html>
<html>
   <body>
      <form action = "{{ url_for('addrec') }}" method = "POST">
         <p>ID <input type = "text" name = "id" /></p>
         <p>Password <input type = "password" name = pw /></p>
         <p>Name <input type = "text" name = "name" /></p>
         <p>Birth <input type = "text" name = "birth" /></p>
         <p>Area <input type ="text" name = "area" /></p>
         <p>Phone <input type = "text" name = "phone" /></p>

         <button type = button style="WIDTH: 60pt" onclick="location.href='/'">back</button>
{#         <button type = button style="WIDTH: 60pt" onclick="location.href='/new'">SignUp</button>#}
          <p><input type = submit style="WIDTH: 60pt" value = "Sign UP"></p>
      </form>
   </body>
</html>


```

list.html

```html
<!doctype html>
<html>
   <body>
      <table border = 1>
         <thead>
            <td>Id</td>
            <td>Name</td>
            <td>Birth</td>
            <td>Area</td>
            <td>Phone</td>
         </thead>

         {% for row in rows %}
            <tr>
               <td>{{row["id"]}}</td>
               <td>{{row["name"]}}</td>
               <td>{{row["birth"]}}</td>
               <td>{{row['area']}}</td>
               <td>{{row['phone']}}</td>
            </tr>
         {% endfor %}
      </table>
        <button type = button style="WIDTH: 60pt" onclick="location.href='/'">back</button>
{#      <a href = "/">Go back to home page</a>#}
   </body>
</html>
```

