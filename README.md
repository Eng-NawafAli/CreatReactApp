# CreatReactApp
The command to creat a react app
1-Install React and React DOM
    Create a root folder with the name reactApp 
    Now, you need to create a package.json file. To create any module, it is required to generate a package.json file in the project folder
                javatpoint@root:~/Desktop/reactApp> npm init -y 
    After creating a package.json file, you need to install react and its DOM packages using the following npm command in the terminal
                javatpoint@root:~/Desktop/reactApp>npm install react react-dom --save  
     




2-Install Webpack
        Webpack is used for module packaging, development, and production pipeline automation. We will use webpack-dev-server during development, webpack to create             production builds, and webpack CLI provides a set of commands. Webpack compiles these into a single file(bundle).
        
            javatpoint@root:~/Desktop/reactApp>npm install webpack --save  
            javatpoint@root:~/Desktop/reactApp>npm install webpack-dev-server --save  
            javatpoint@root:~/Desktop/reactApp>npm install webpack-cli --save  




3-Install Babel

    Babel is a JavaScript compiler and transpiler used to convert one source code to others. It compiles React JSX and ES6 to ES5 JavaScript which can be run on all         browsers. We need babel-loader for JSX file types, babel-preset-react makes your browser update automatically when any changes occur to your code without losing the     current state of the app. ES6 support requires babel-preset-env Babel preset.
    
          javatpoint@root:~/Desktop/reactApp>npm install babel-core --save-dev  
          javatpoint@root:~/Desktop/reactApp>npm install babel-loader --save-dev  
          javatpoint@root:~/Desktop/reactApp>npm install babel-preset-env --save-dev  
          javatpoint@root:~/Desktop/reactApp>npm install babel-preset-react --save-dev  
          javatpoint@root:~/Desktop/reactApp>npm install babel-webpack-plugin --save-dev  
          
          
          
 4-create Files
      To complete the installation process, you need to add the following files in your project folder. These files are index.html, App.js, main.js,                       webpack.config.js and, .babelrc. You can create these files by manually
      
      
      
      
      
5-Configure webpack

      ou can configure webpack in the webpack.config.js file by adding the following code. It defines your app entry point, build output and the extension which will resolve automatically. It also set the development server to 8080 port. It defines the loaders for processing various file types used within your app and wrap up by adding plugins needed during our development.
      
      
          const path = require('path');  
    const HtmlWebpackPlugin = require('html-webpack-plugin');  
      
    module.exports = {  
       entry: './main.js',  
       output: {  
          path: path.join(__dirname, '/bundle'),  
          filename: 'index_bundle.js'  
       },  
       devServer: {  
          inline: true,  
          port: 8080  
       },  
       module: {  
          rules: [  
             {  
                test: /\.jsx?$/,  
                exclude: /node_modules/,  
            use: {  
                  loader: "babel-loader",  
                }  
             }  
          ]  
       },  
       plugins:[  
          new HtmlWebpackPlugin({  
             template: './index.html'  
          })  
       ]  
    }  
    
    
    Now, open the package.json file and delete "test" "echo \" Error: no test specified\" && exit 1" inside "scripts" object, then add the start and build commands instead. It is because we will not perform any testing in this app.
    
    
    
        {  
      "name": "reactApp",  
      "version": "1.0.0",  
      "description": "",  
      "main": "index.js",  
      "scripts": {  
        "start": "webpack-dev-server --mode development --open --hot",  
        "build": "webpack --mode production"  
      },  
      "keywords": [],  
      "author": "",  
      "license": "ISC",  
      "dependencies": {  
        "react": "^16.8.6",  
        "react-dom": "^16.8.6",  
        "webpack-cli": "^3.3.1",  
        "webpack-dev-server": "^3.3.1"  
      },  
      "devDependencies": {  
        "@babel/core": "^7.4.3",  
        "@babel/preset-env": "^7.4.3",  
        "@babel/preset-react": "^7.0.0",  
        "babel-core": "^6.26.3",  
        "babel-loader": "^8.0.5",  
        "babel-preset-env": "^1.7.0",  
        "babel-preset-react": "^6.24.1",  
        "html-webpack-plugin": "^3.2.0",  
        "webpack": "^4.30.0"  
      }  
    }  
    
    
    
    
    
    
6-HTML webpack template for index.html

We can add a custom template to generate index.html using the HtmlWeb-packPlugin plugin. This enables us to add a viewport tag to support mobile responsive scaling of our app. It also set the div id = "app" as a root element for your app and adding the index_bundle.js script, which is our bundled app file.
      
      
          <!DOCTYPE html>  
    <html lang = "en">  
       <head>  
          <meta charset = "UTF-8">  
          <title>React App</title>  
       </head>  
       <body>  
          <div id = "app"></div>  
          <script src = 'index_bundle.js'></script>  
       </body>  
    </html>  
    
    
    
    
    
    App.jsx and main.js

This is the first React component, i.e. app entry point. It will render Hello World.

App.js

    import React, { Component } from 'react';  
    class App extends Component{  
       render(){  
          return(  
             <div>  
                <h1>Hello World</h1>  
             </div>  
          );  
       }  
    }  
    export default App;  

Now, import this component and render it to your root App element so that you can see it in the browser.

Main.js

    import React from 'react';  
    import ReactDOM from 'react-dom';  
    import App from './App.js';  
      
    ReactDOM.render(<App />, document.getElementById('app'));  

Note: If you want to use something, you need to import it first. To make the component usable in other parts of the app, you need to export it after creation and import it in the file where you want to use it.

Create .babelrc file

Create a file with name .babelrc and copy the following code to it.

.babelrc

    {  
       "presets":[  
      "@babel/preset-env", "@babel/preset-react"]  
    }  

Running the Server

After completing the installation process and setting up the app, you can start the server by running the following command.

    javatpoint@root:~/Desktop/reactApp>npm start  

It will show the port number which we need to open in the browser. After we open it, you will see the following output.
React Environment Setup

Generate the Bundle

Now, generate the bundle for your app. Bundling is the process of following imported files and merging them into a single file: a "bundle." This bundle can then be included on a webpage to load an entire app at once. To generate this, you need to run the build command in command prompt which can be shown below.

    javatpoint@root:~/Desktop/reactApp> npm run build  

This command will generate the bundle in the current folder(in which your app belongs) and will be shown as like below image.
React Environment Setup
2. Using the create-react-app command

If you do not want to install react by using webpack and babel, then you can choose create-react-app to install react. The 'create-react-app' is a tool maintained by Facebook itself. This is suitable for beginners without manually having to deal with transpiling tools like webpack and babel. In this section, I will be showing you how to install React using CRA tool.

Install NodeJS and NPM

NodeJS and NPM are the platforms need to develop any ReactJS application. You can install NodeJS and NPM package manager by the link given below.
https://www.javatpoint.com/install-nodejs-on-linux-ubuntu-centos

Install React

You can install React using npm package manager by using the below command. There is no need to worry about the complexity of React installation. The create-react-app npm package will take care of it.

    javatpoint@root:~/>npm install -g create-react-app  

Create a new React project

After the installation of React, you can create a new react project using create-react-app command. Here, I choose jtp-reactapp name for my project.

    javatpoint@root:~/>create-react-app jtp-reactapp  

NOTE: You can combine the above two steps in a single command using npx. The npx is a package runner tool that comes with npm 5.2 and above version.

    javatpoint@root:~/>npx create-react-app jtp-reactapp  

The above command will install the react and create a new project with the name jtp-reactapp. This app contains the following sub-folders and files by default which can be shown in the below image.
React Environment Setup

Now, to get started, open the src folder and make changes in your desired file. By default, the src folder contain the following files shown in below image.
React Environment Setup

For example, I will open App.js and make changes in its code which are shown below.

App.js

    import React from 'react';  
    import logo from './logo.svg';  
    import './App.css';  
      
    function App() {  
      return (  
        <div className="App">  
          <header className="App-header">  
            <img src={logo} className="App-logo" alt="logo" />  
            <p>  
              Welcome To JavaTpoint.  
      
          <p>To get started, edit src/App.js and save to reload.</p>  
            </p>  
            <a  
              className="App-link"  
              href="https://reactjs.org"  
              target="_blank"  
              rel="noopener noreferrer"  
            >  
              Learn React  
            </a>  
          </header>  
        </div>  
      );  
    }  
      
    export default App;  

NOTE: You can also choose your own favorite code editor for editing your project. But in my case, I choose Eclipse. Using the below link, you can download Eclipse for Ubuntu and install.
click Here to download Eclipse for Ubuntu and install

Running the Server

After completing the installation process, you can start the server by running the following command.

    javatpoint@root:~/Desktop>cd jtp-reactapp  
    javatpoint@root:~/Desktop/jtp-reactapp>npm start  

It will show the port number which we need to open in the browser. After we open it, you will see the following output.

      
      
      
      
