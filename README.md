# Activity 1
Web Dev't Boilerplate Setup using Express

## 1. Setup Tools
* Verify nodeJS version. ```$ node --version```
* Verify npm version. ```$ npm --version```
* Verify git version. ```$ git --version```
* Verify sublime version. ```$ subl --version```

## 2. Setup Web App Framework (Express JS)
* Create a local repository. ```$ cd desktop && mkdir lastname-022317 && cd lastname-022317```
* Launch sublime text editor. ```$ subl .```
* Create ```package.json```. ```$ npm init -y```
* Install express as dependency. ```$ npm install express --save```
* Create simple express directory tree. ```$ mkdir public && mkdir views```
```
+-- lastname-022317
| +-- node_modules
| +-- public
| | +-- css
| | | `-- app.css
| | +-- img
| | | `-- winteriscomming.jpg
| | +-- js
| | | `-- app.js
| +-- views
| | `-- 404.html
| | `-- app.html
| `-- .gitignore
| `-- package.json
| `-- Procfile
| `-- README.md
| `-- server.js

```

```javascript
//server.js
//require modules
var express = require('express');
var path = require('path');
//instantiate express
var app = express();
//set port
app.set('port', (process.env.PORT || 5000));
//use static files
app.use(express.static(path.join(__dirname, 'public')));
//express routes
app.get('/', function(req, res){
  res.sendFile(path.join(__dirname, 'views/app.html'));
});
app.get('/about', function(req, res){
  res.sendFile(path.join(__dirname, 'views/about.html'));
});
app.get('*', function(req, res){
  res.status(404).sendFile(path.join(__dirname, 'views/404.html'));
});
//express server listen
var server = app.listen(app.get('port'), function(){
  console.log('Server listening on port ',app.get('port'));
});
```

```html
<!--index.html-->
<!DOCTYPE html>
<html>
<head>
	<title>My Web App</title>
</head>
<body>
	<h1>Welcome to my web app!</h1>
	<img src="img/winteriscoming.jpg" />

	<br>
	<a href="/">Home</a> |
	<a href="/about">About</a>
</body>
</html>
```

```html
<!--404.html-->
<!DOCTYPE html>
<html>
<head>
	<title>404 Page</title>
</head>
<body>
	<h1>Error 404: Page cannot be found!</h1>
	<p>Click <a href="/">here</a> to return to main page</p>
</body>
</html>
```

* Download images [here](https://drive.google.com/drive/folders/0By-aduulSKAMU3RxUm16Vm04cU0?usp=sharing)

## 3. Upload files to remote repository (Github)
* Create new github remote repository
* Open ```.gitignore``` file and write ```node_modules``` inside.
* ```$ git init```
* ```$ git config user.email "youremailusedingithub@domain.com"```
* ```$ git config user.name "yourgithubname"```
* ```$ git status```
* ```$ git add .```
* ```$ git commit -m "my first commit"```
* ```$ git remote add origin https://github.com/yourgithubusername/yourgithubrepo.git```
* ```$ git push -u origin master```
* Open your web app at http://localhost:5000 ```$ node server.js```

## 4. Deploy to heroku
* ```$ heroku login```
* ```$ heroku create lastname-022217```
* ```$ git status```
* ```$ git add .```
* ```$ git commit -m "deploy to heroku"```
* ```$ git push -u heroku master```
* ```$ heroku open```