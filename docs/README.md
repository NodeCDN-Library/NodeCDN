## About NodeCDN
A simple library that transforms JavaScript into a better platform.

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


