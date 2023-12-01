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

```
`Components let you split the UI into independent, reusable pieces, and think about each piece in isolation `

`Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen `

`When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. We call this object “props” `

`For example, this following code inside `index.html` renders App.js on the page: `
```

```javascript
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />);
```
### Step 3- Import all desired components and give functionalities

```javascript
import { useState } from "react";

import Navigation from "./Navigation/Nav";
import Products from "./Products/Products";
import products from "./db/data";
import Recommended from "./Recommended/Recommended";
import Sidebar from "./Sidebar/Sidebar";
import Card from "./components/Card";
import "./index.css";

function App() {
  const [selectedCategory, setSelectedCategory] = useState(null);

  // ----------- Input Filter -----------
  const [query, setQuery] = useState("");

  const handleInputChange = (event) => {
    setQuery(event.target.value);
  };

  const filteredItems = products.filter(
    (product) => product.title.toLowerCase().indexOf(query.toLowerCase()) !== -1
  );

  // ----------- Radio Filtering -----------
  const handleChange = (event) => {
    setSelectedCategory(event.target.value);
  };

  // ------------ Button Filtering -----------
  const handleClick = (event) => {
    setSelectedCategory(event.target.value);
  };

  function filteredData(products, selected, query) {
    let filteredProducts = products;

    // Filtering Input Items
    if (query) {
      filteredProducts = filteredItems;
    }

    // Applying selected filter
    if (selected) {
      filteredProducts = filteredProducts.filter(
        ({ category, color, company, newPrice, title }) =>
          category === selected ||
          color === selected ||
          company === selected ||
          newPrice === selected ||
          title === selected
      );
    }

    return filteredProducts.map(
      ({ img, title, star, reviews, prevPrice, newPrice }) => (
        <Card
          key={Math.random()}
          img={img}
          title={title}
          star={star}
          reviews={reviews}
          prevPrice={prevPrice}
          newPrice={newPrice}
        />
      )
    );
  }

  const result = filteredData(products, selectedCategory, query);

  return (
    <>
      <Sidebar handleChange={handleChange} />
      <Navigation query={query} handleInputChange={handleInputChange} />
      <Recommended handleClick={handleClick} />
      <Products result={result} />
    </>
  );
}

export default App;
```

### Step 4- Add `index.css` file and write css code

```css
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: sans-serif;
}

a {
  text-decoration: none;
  color: rgb(97, 97, 97);
}

li {
  list-style: none;
}

.btns {
  padding: 10px 20px;
  margin-right: 6px;
  background: transparent;
  border: none;
  border: 0.6px solid #ccc;
  border-radius: 5px;
  color: #323232;
  cursor: pointer;
}
```
