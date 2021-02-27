# Flask 
Flask is a  web framework written in python that can:
- develop RESTful api's that can rescieve requests
- create webpages
- create interactive GUI apps on the web

### Basic structure
```python
# import Flask
from flask import Flask

# create the app
app = Flask(__name__) # app is the name of the object here

# create routes for the apps webpage
@app.route('/')
def home():
    return "<h1> Hello World </h1>"

# run the app
if __name__ == "__main__":
    app.run(debug=True, port=8080)
```
### Basic RESTful api
```python
# import Flask and jsonify
from flask import Flask, jsonify, request
# import Resource, Api and reqparser
from flask_restful import Resource, Api, reqparse

# create aoo
app = Flask(__name__)
# create api for the app
api = Api(app)

# create class and define type of requests it takes(podt here)
class add(Resource):
    def post(self):
        json_data = request.get_json()
        num1 = json_data['num1'] 
        num2 = json_data['num2']
        return num1 + num2

# assign endpoint, where to send api request to
api.add_resource(add, '/add')

# run api
if __name__ == '__main__':
    app.run(debug=True)
```
### Basic request to api in python, can also use postman
```python 
import requests

# define data to send, and url to send to
json_data = {'num1': 100, 'num2': 25}
URL = "http://127.0.0.1:5000/add"

# make request
r = requests.post(url = URL, json = json_data) 

#print request
print(r.json())
```
# Advanced flask
- create a folder named `templates` in working directory 
    - populate this directory with html page codes you want to render
- create forms with html, and use `request.form.get()` to use form inputs in python script
- import models with `pickle` to use predictions 
---
#### use `jinja2` syntax `{% %}` for html inheritance 
