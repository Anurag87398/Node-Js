# Modules
Modules are basically javaScript libraries.  
They are a set of functions that we want to use in our program.

Node has both built-in modules as well as the ones which we can build ourselves.

- We use require() to include a module
    
    ```
    const http= require('http');
    ```
    Now we'll have access to the 'http' module.

# Built-In Modules
`http` is a built in module that allows us to create a http server and implement http protocols.

# Creating Our Own Modules

- Let's create a custom module to return the current date and time info

    ```javascript
    exports.mydate= () => {
        return Date();
    };
    ```

    - Here, `exports` is to make properties and methods availbale outside the module file.
    - Let's save this custom module as `myDateReturn.js`.

- Now we create a server which will include this custom module:
    ```javascript
    const http= require('http');
    const date= require('./myDateReturn');

    const server= http.createServer((req, res)=> {
        res.writeHead(200, {'Content-Type':'text/plain'});
        res.end(`The date and time info is: ${date.mydate()}`);
    });

    server.listen(3000, ()=> {
        console.log("Server is running...");
    });
    ```
    - We save this file as `customModule.js`.
    
    Thus, the desired output is achieved by running `customModule.js`.

### Sources
- https://www.w3schools.com/nodejs/nodejs_get_started.asp
