# Node.js

- Usually in a website, there's frontend(FE) and backend(BE)

- The FE consists mainly of HTML, CSS and JavaScript

- Now, these three languages are executed on the end user's browser.  
    So, the developers thought why restrict Js only to the FE?

- And thus, they extracted the engine from chrome responsible for running Js and put that on the BE (the developer's machine)

- Thus, Node.js is a runtime which allows us to run JavaScript on the backend

## Working

- The end users can only access the FE code, not the BE ones

- And since the JavaScript protion would be running on the BE servers, which is not on the end user's local machine, the browsers need to  
connect with these BE machines.

- In order to establish these connections, protcols such as the HTTP protocols are used. These protocols are implemented by HTTP servers

- Now Express comes into play. Express is a HTML framework written in Node.js that allows us to implement HTTP protocols by creating HTTP servers which the browsers would use to interact with the BE.

## Setup

- Download Node.js
- Install npm on machine if not done already
- Check if both node and npm are installed

    ```
    npm -v
    ```
    ```
    node -v
    ```

## Using Node.js

- We can open the terminal and type 'node'
- This is similiar to the terminal of python, where 1 line commands are executed.
- We can perform JavaScript operations here, but all commands need to be executed in a single line.
- This is why we use an IDE to write node.js files and then use the node terminal to execute it.

## Hello World

```javascript
// requiring the http module
const http= require('http');

// setting the port on which the server would listen
const port= 3000;

// createServer() of http module creates a HTTP server and returns it
const server= http.createServer((req, res) => {

    //indicating successfull response
    res.statusCode= 200;
    
    res.setHeader('Content-Type', 'text/plain');    
    
    //the last command before ending
    //inside the res.end() function, the last chunk of data
    //is sent, which'll be written just before ending
    res.end('Hemlo World');
});
// console.log("a");

// once the server is ready, it listens on the specified port
// and hostname, and calls the callback function
server.listen(port, ()=> {
    console.log(`Listening begins at port: ${port}`);
});
```

### Code Walkthrough

- **require()**  
    - This function is used to 'require' the necessary modules, here in this case: 'http' 
    
        ```javascript
        const http= require('http');
        ```

- **What are Requests?**  
    - Whenever a request is received, it calls the request event.
    - The request event consists of 2 objects:  
        1. Request: 
            - an incomingMessage Object
            - used to access request header/data
        2. Response:  
            - Server Response Object
            - used to return data back to the caller
            
        <br>

        ```javascript
        const server= http.createServer((request, response) => {
            ...
        });
        ```

    - These 2 objects are responsible for handling the http call.

- **listen()**
    - The listen() of the server, indicates that the server is listening on a particular port, hostname
    <br>
        ```javascript
        server.listen(hostname, port, ()=> {
            console.log(`Listening begins at port: ${port}`);
        });
        ```
    
    - And when the server is ready, it'll call the callback function, which in the above code, will print:

        > "Listening begins at port: ${port}"

- **Some important points**
    - if we write any console.log() statements in a node.js file, it'll be displayed in the terminal on the backend.  
    This is because, we are running javaScript on the backend and not on the end user's browser.

    - if we write any statements outside the createServer(), it'll always be executed before the listen() as the listen() executes only when the server is completely ready.

    - Keep the projects organized to be able to refer to them later.

- **writeHead()**
    - This fucntion combines the statusCode and setHeader into one.
    - It initiates the HTML file.

## Improved Code
```javascript
const http= require('http');
const port= 3000;
const server= http.createServer((req, res) => {

    //combining the statusCode and setHeader into one
    res.writeHead(200, {'Content-Type', 'text/plain'});

    res.end('Hemlo World');
});

server.listen(port, ()=> {
    console.log(`Listening begins at port: ${port}`);
});
```

## Running The Code

- Save the file as say Server.js
- Through either the cmd or the terminal in IDE, run:

    ```
    node Server.js
    ```

- We'll get the output in the terminal as:
    ```
    node Server.js
    Listening begins at port: 3000
    ```

- Open the browser and go to: 
    ```
    localhost:3000
    ```
- We'll get the output in the browser as:
  <br><br>
  ![Hemlo World](/Screenshots/HemloWorld.jpg)
