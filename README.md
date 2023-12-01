# E-commerce React App

## To run this app in your local system:

### Clone this repo in vs studio code and open terminal

### step 1- Install node module
```
npm install
```

### step 2- Run code on local system
```
npm start
```
---
## Project description

### To start project

### Step 1- Install node modules

### Step 2- Navigate to `src` folder

#### All the changes made inside the `src` folder will be visible in the App

`Components let you split the UI into independent, reusable pieces, and think about each piece in isolation `

`Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen `

`When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. We call this object “props” `

`For example, this following code inside `index.html` renders App.js on the page: `
```
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```

