This Project was made with care by JustAnEric. Copying the code for your reputation is not permitted.

## About NodeCDN
A simple library that transforms JavaScript into a better platform. We make it easy for beginners to learn the basics of our code to actual JavaScript code!

## Installation
- For client sides: `<script class="nodecdn-init" src="https://hostereric.herokuapp.com/NodeCDN/index.min.js">config = {"method": "web"}</script>`
- For backend: Go down to the [backend](#initialising-on-the-backend) section.

## Initialising on the backend
- Python (Flask): `pip install nodecdn` or use your Package Manager to search for `nodecdn`.

## For standalone installs:
1. Download the latest ZIP file from [Releases](https://github.com/WWEMGamer2/NodeCDN/releases/tag/StandaloneInstalls)
2. UnZIP, then move to your website's asset directory
3. Initialise it like in this example here (change the src to your corresponding path): `<script class="nodecdn-init standalone" src="assets/NodeCDN/init/index.min.js">config = {"method": "standalone"}</script>`

## Start coding
- To initialise in JavaScript, copy and paste this code into your script file:

```js
nd = new Node(); //initialise the NodeCDN minimal js script
nd.Client('key'); //initialise the client

Init();
```

- To initalise in Python, copy and paste this code into your script files:

```py
# This is the file where your Flask server will be

from flask import Flask
from nodecdn import backend, frontend

app = Flask('app')

@app.route('/')
def index(): return "home"

backend.init(app);
app.run()
```
```html
<!--Put before closing body tag -->
<script src="nodecdn/dist">
    config = {
        "method": "standalone"
    }
</script>
```

### node.Client(key)
Used to specify the client of the browser.
`node.Client('yourKeyHere')`

### node.PingServer(times)
Used to ping the server as many times as you like.
`node.PingServer(1)`

### node.makeFunction(code, executorOptions={})
Used to make a function easily!

```js
node.makeFunction(function() {
    alert("Hello there!")
}, {exec:true})
```

You can also execute it using this method: (still in development)

```js
func = node.makeFunction(function() {
    alert("Hello there!")
}, {})
func()()
```

### node.safeExec(func) / node.safeExecute(func)
Used to execute a function made by NodeCDN.
`node.safeExec(func) && node.safeExecute(func)`

### node.request(method="GET", url, callback, headers={}, body="") (asynchronous)
Used to send a request to the backend or an api call of your choice.

```js 
function func(resp) {
    alert(`response is ${resp}`)
}

node.request(
    "POST", 
    "https://emmalovescooking.com/recipes/api", 
    func, 
    {"token": "authToken"}, 
    "Meat pie and roasted beans"
)
```

### node.match(x, y)
Used to match two objects to see if they're the same.

```js
node.match("string", "another")
>>> false
```

### node.str(input)
Used to transform an object into a string.

```js
node.str({"baked-beans": "yum"})
>>> '{"baked-beans": "yum"}'
```

### node.json(input)
Used to transform a string with an object inside it to an object.

```js
node.json('{"am I a vaild JSON": "yes"}')
>>> {"am I a vaild JSON": "yes"}
```
However an invalid json will return errors:

```js
node.json('{"am I a vaild JSON": "no""}')
>>> 'The JSON you provided could not be parsed: Incorrect JSON'
```

### node.calc(a, b, method)
Used to calculate "a" and "b" values with the "method" value.

```js
node.calc(
    9,
    10,
    "+"
)
>>> 19
```

### node.findElement(tag)
Used to find an element in HTML by tag name

```js
return node.findElement('title').innerHTML
>>> 'tagged ya'
```
You can also use it with class names and identifications by doing this:

```js
return node.findElement('.title').innerHTML
>>> 'tagged ya'

return node.findElement('#title').innerHTML
>>> 'wow epic!'
```

### node.appendChildToParent(parent, child)
Used to append a child to a parent element.

```js
node.appendChildToParent(node.doc().body, node.doc().head)
```

```html
<!--Before:-->
<html>
    <head>
        <title>Some stuff</title>
    </head>
    <body>
        Head tag right here:

    </body>
</html>

<!--After:-->
<html>
    <body>
        Head tag right here:

        <head>
            <title>Some stuff</title>
        </head>
    </body>
</html>
```

### node.doc()
Used to return the document variable.

```js
docu = node.doc()
body = node.body()

e = node.findElementInElement(body, '.class');
e.innerHTML = 'suuuuuu!'
```

### node.win()
Used to return the window variable.

```js
docu = node.win.document()
body = node.body()

e = node.findElementInElement(body, '.class');
e.innerHTML = 'suuuuuu!'
```

### node.navig()
Used to return the navigator variable.

```js
node.navig()
>>> window.navigator
```

### node.whichDevice()
Used to return which device the user is on

```js
node.whichDevice()
>>> 'Mozilla 5.0 (like Gecko) Apple Macintosh'
```

### node.isMobile()
Used to return a bool depending on if the user is on a mobile device

```js
node.isMobile()
>>> false
```

### node.createHTML(tag)
Used to create a HTML element which you can append by putting it in our [appendChildToParent()](#nodeappendchildtoparentparent-child) function provided by NodeCDN.

```js
element = node.createHTML('a')
element.innerHTML = "a link"
element.href = "#"
node.appendChildToParent(node.doc().body, element)
```

### node.editStyle(element, styles="")
Used to set an element's styling and CSS properties.

```js
element = node.createHTML('a')
element.innerHTML = "a link"
element.href = "#"
node.editStyle(element, "text-decoration: none;")
node.appendChildToParent(node.doc().body, element)
```