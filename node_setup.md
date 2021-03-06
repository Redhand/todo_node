# Setup Node.JS app

* Installation

  * Among multiple way to install Node.js, to make is simple lets install using Ubuntu's inbuilt **apt**:
 
    ```
    sudo apt-get update
    sudo apt-get install nodejs
    ```
    Verify version with:
    ```
    node -v
    ```
    
  * Install the Node package manager, npm:

    ```
    sudo apt-get install npm
    ```
    Checkout version with:
    ```
    npm -v
    ```
* Create a file with name **app.js**
  
  let's write very basic code to output **Hello World!**. Write down below code in the app.js file.
  
  `
  console.log('Hello World!')
  `
* Run the file:
  
  ```script
  node app.js
  ```
  It will output text **Hello World!**
  
* Let's show **Hello World!** in browser by sending response through node server
  
  Modify **app.js** with the code for the following purpose
  * define a port through which node server get request and send response, say communicate with client
    
    `const port = 3000;`
  * use http module to create a server which sends text upon the request from client
  
     ```
     const http = require('http');
     const server = http.createServer((req, res) => {
        res.end("Hello World!");
      });
      ```
  * serve should be run on the defined port
    
    ```
      server.listen(port, () => {
        console.log(`Server running at http://localhost:${port}/`);
      });
    ```
  Together, **app.js** file should be:
  
  ```
  const port = 3000;
  const http = require('http');
  const server = http.createServer((req, res) => {
    res.end("Hello World!");
  });
  server.listen(port, () => {
    console.log(`Server running at http://localhost:${port}/`);
  });
  ```
* Start the node server with
  ```
  node app.js
  ```
* Open [http://localhost:3000](http://localhost:3000)

  Should see **Hello World!** text output in the browser

* Let's use **express** server instead of node inbuilt **http** module
  
  * Need to install **express** with **npm**
  
    So first, initialize **npm** in current node project with the command:
    
    ```
    npm init
    ```
    Follow the instruction, But if confused just press key **Enter**
    
    File named *package.json* is created.
    
    Explore [package.json going to this link](https://docs.npmjs.com/files/package.json).
    
    Install express with command:
    
    ```
    npm install express --save
    ```
    Explore [npm install command going to this link](https://docs.npmjs.com/cli/install).
    
    Add `node_module` directory to `.gitignore`.
   
  * Create express serve
    ```
    const port = 3000;
    const express = require('express');
    const app = express();
    app.get('/', (req, res) => {
      res.end("Hello World!");
    });
    app.listen(port, () => {
      console.log(`Server running at http://localhost:${port}/`);
    });

    ```
* Restart the Server
   * Stop server with keypress `Ctrl c`
   * Start again with command `node app.js`
   
     OR
   * Use [nodemon](https://nodemon.io/) or [forever](https://github.com/foreverjs/forever) to restart automatically when code change.
   
* Open [http://localhost:3000](http://localhost:3000)

  Should see **Hello World!** text output in the browser