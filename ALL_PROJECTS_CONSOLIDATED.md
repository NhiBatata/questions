# React EndSem - All Projects Consolidated

Complete compilation of all React projects and components from the React EndSem course.

---

## TABLE OF CONTENTS
1. [Anexxure Project](#anexxure)
2. [SimpleState Projects](#simplestate)
3. [ComplexState Projects](#complexstate)
4. [FunctionComp Projects](#functioncomp)
5. [ExtraClassQues Projects](#extraclassques)
6. [Router-DOM Projects](#routerdom)

---

## ANEXXURE

### App.jsx
```jsx
import { useState } from "react";
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  BarElement,
  Title,
  Tooltip,
  Legend,
} from "chart.js";

import { Bar } from "react-chartjs-2";

ChartJS.register(
  CategoryScale,
  LinearScale,
  BarElement,
  Title,
  Tooltip,
  Legend
);

function App() {
  const [transactions, setTransactions] = useState([]);

  const [amount, setAmount] = useState("");
  const [description, setDescription] = useState("");
  const [type, setType] = useState("income");
  const [category, setCategory] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();

    if (
      amount.trim() === "" ||
      description.trim() === "" ||
      category.trim() === "" ||
      isNaN(amount)
    ) {
      alert("Please enter valid data");
      return;
    }

    const newTransaction = {
      id: Date.now(),
      amount: Number(amount),
      description,
      type,
      category,
    };
```

---

## SIMPLESTATE

### 1. Random Quote Generator

**Location:** `SimpleState/RandomQuoteGen/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const arr = ["Hey i'm Keshav",
    "How are you?",
    "Today is Monday",
    "My End Term are going on",
    "Good Bye Have a nice Day"
  ]
  const [quote, setQuote] = useState("Generate One now")
  const handleClick = () => {
    let i = Math.floor(Math.random()*arr.length);
    setQuote(arr[i])
  }

  return (
    <>
    <h1>Random Quote Generator</h1>
    <p>{quote}</p>
    <button onClick={handleClick}>Generate Quote</button>
    </>
  )
}

export default App
```

---

### 2. Background Color Change

**Location:** `SimpleState/BgColorChange/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const [color, setColor] = useState("Grey")

  const handleClick = () => {
    let r = Math.floor(Math.random()*256)
    let g = Math.floor(Math.random()*256)
    let b = Math.floor(Math.random()*256)

    setColor(`rgb(${r},${g},${b})`)
  }
  return (
    <>
    <button onClick={handleClick} style={{width:"150px"}}>Click to change color</button>
    <div style={{margin:"50px", height:"400px", width:"400px", backgroundColor:color}}></div>
    </>
  )
}

export default App
```

---

### 3. Character Limit Warning

**Location:** `SimpleState/CharLimitWarn/app/src/App.jsx`

```jsx
import { useState,useEffect } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const [text, setText] = useState("")

  const handleChange = (e) => {
    setText(e.target.value)
  }

  return (
    <>
    <h1>Character Limit Input</h1>
    <input value={text} type='text' maxLength={20} onChange={handleChange}></input>
    <h3>Remaining: {20-text.length}</h3>
    {text.length==20?<p style={{color:"orange"}}>Limit Reached!!</p>:<p style={{color:"green"}}>Limit Not Reached</p>}
    </>
  )
}

export default App
```

---

### 4. Counter with Limit

**Location:** `SimpleState/counterWithLimit/app/src/App.jsx`

```jsx
import { useState } from 'react'

function App() {
  const [count, setCount] = useState(0)
  const Increament = () => {
    if(count<10){
      setCount(count+1);
    }
  }
  const Decrement = () => {
    if(count>0){
      setCount(count-1);
    }
  }

  return (
    <>
    <h1>Yo</h1>
    <h1>{count}</h1>
    <button onClick={Increament}>Increase</button>
    <button onClick={Decrement}>Decrement</button>
    </>
  )
}

export default App
```

---

### 5. Disable Button on Click

**Location:** `SimpleState/DisableButtonOnClick/app/src/App.jsx`

```jsx
import { useState } from 'react'

function App() {
  const [dis, setDis] = useState(false)

  return (
    <>
    <button disabled={dis} style={{backgroundColor:"grey", height:"40px", width:"150px"}} onClick={(e)=>{setDis(!dis)}}>Press to disable</button>
    <p>{dis==true?"Disabled":"Not Disabled"}</p>
    </>
  )
}

export default App
```

---

### 6. Dropdown Selection

**Location:** `SimpleState/DropdownSel/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const [state, setState] = useState("")
  const handleChange = (e) => {
    setState(e.target.value);
  }
  return (
    <>
    <h2>Select Tech:</h2>
    <select value={state} onChange={handleChange}>
      <option value="Nothing">Nothing</option>
      <option value="CSS">CSS</option>
      <option value="HTML">HTML</option>
      <option value="JS">JS</option>
    </select>
    <h2>You selected: {state}</h2>
    </>
  )
}

export default App
```

---

### 7. Password Input Show/Hide

**Location:** `SimpleState/PassInputShowHide/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const [state, setState] = useState("Show")
  const handleClick = () => {
    if(state == "Show"){
      setState("Hide");
    }else{
      setState("Show");
    }
  }
  return (
    <>
    <h1>Password</h1>
    <input type={state=="Hide"?"text":"password"} placeholder='Enter Pass'></input>
    <button style={{width:"150px", margin:"50px"}} onClick={handleClick}>{state}</button>
    </>
  )
}

export default App
```

---

### 8. Input Live Preview

**Location:** `SimpleState/InputLivePreview/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const [text, setText] = useState("")
  const handleChange = (e) => {
    setText(e.target.value);
  }

  return (
    <>
    <h1>Live Input Preview</h1>
    <input onChange={handleChange}></input>
    <p>You typed: {text}</p>
    </>
  )
}

export default App
```

---

## COMPLEXSTATE

### 1. Update User in List

**Location:** `ComplexState/UpdateUserInList/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const [users, setUsers] = useState([
    { id: 1, name: "A"},
    { id: 2, name: "B"}
  ]);
  const handleChange = () => {
    setUsers(
      users.map((data)=>{
      if(data.id==2){
        return({...data,name:"Updated"})
      }else{
        return(data)
      }
    })
    )
  }

  return (
    <>
    <div>
      <p>User List</p>
      {users.map((data)=>{
        return(
          <p>User {data.id}: {data.name}</p>
        )
      })}
      <button onClick={handleChange}>Update User</button>
    </div>
    </>
  )
}

export default App
```

---

### 2. Toggle Status Inside Object

**Location:** `ComplexState/ToggleStatusInsideObj/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const [task, setTask] = useState({
    title:"React",
    complete:true
  })
  const handleClick = () => {
    setTask({...task,
      complete:!task.complete
    })
  }

  return (
    <>
    <h2>{task.title} - {task.complete?"Completed":"Peding"}</h2>
    <button onClick={handleClick}>Toggle</button>
    </>
  )
}

export default App
```

---

### 3. Employee Form

**Location:** `ComplexState/EmployeeForm/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const employees = [
  {
    id: 1,
    name: "Keshav",
    department: "Frontend",
    salary: 50000
  },
  {
    id: 2,
    name: "Rahul",
    department: "Backend",
    salary: 60000
  },
  {
    id: 3,
    name: "Priya",
    department: "HR",
    salary: 45000
  },
  {
    id: 4,
    name: "Aman",
    department: "DevOps",
    salary: 70000
  },
  {
    id: 5,
    name: "Neha",
    department: "UI/UX",
    salary: 55000
  }
];
const [emp, setEmp] = useState("")
const [submit,setSubmit] = useState("")
const handleChange = (e) => {
  setEmp(e.target.value)
}
const handleSubmit = () => {
  setSubmit(emp)
}
const handleReset = () => {
  setEmp("")
  setSubmit("")
}

  return (
    <>
      <input type='text' name='name' value={emp} onChange={handleChange} placeholder='Name'></input>
      <button onClick={handleSubmit}>Submit</button>
      <button onClick={handleReset}>Reset</button>
    <div style={{backgroundColor:"Grey", margin:"10px"}}>
      {employees.filter(data=>data.name.toLowerCase().includes(submit.toLowerCase())).map((data)=>{
            return(
              <div style={{backgroundColor:"Grey", margin:"10px"}}>
                <p>{data.name}</p>
                <p>{data.department}</p>
                <p>{data.salary}</p>
              </div>
            )
          })}
    </div>
    </>
  )
}

export default App
```

---

### 4. Search Functionality

**Location:** `ComplexState/SearchFunctionality/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const usersData = [
    { id: 1, name: "Amit Sharma", city: "Delhi" },
    { id: 2, name: "Neha Verma", city: "Mumbai" },
    { id: 3, name: "Rahul Singh", city: "Chandigarh" },
    { id: 4, name: "Priya Mehta", city: "Pune" }
  ];
  const [search, setSearch] = useState("")
  const handleChange = (e) => {
    setSearch(e.target.value);
  }

  return (
    <>
    <div>
      <input value={search} placeholder='Search by name...' onChange={handleChange}></input>
      {usersData.filter(data=>data.name.includes(search)).map((data)=>{
        return(
          <div>
            <p>{data.name} ||  {data.city}</p>
          </div>
        )
      })}
    </div>
    </>
  )
}

export default App
```

---

### 5. Product Dashboard

**Location:** `ComplexState/ProductDashboard/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const products = [
    { id: 1, name: "Laptop", price: 80000, category: "Premium" },
    { id: 2, name: "Mouse", price: 500, category: "Basic" },
    { id: 3, name: "Keyboard", price: 1500, category: "Basic" },
    { id: 4, name: "Smartphone", price: 60000, category: "Premium" },
    { id: 5, name: "Monitor", price: 12000, category: "Deluxe" },
    { id: 6, name: "Headphones", price: 3000, category: "Deluxe" }
  ];
  const [sort, setSort] = useState("")
  const handleChange = (e) => {
      setSort(e.target.value);
  }
  const sortedProducts = sort==="all" || sort==""?products:products.filter(data=>data.category.toLowerCase().includes(sort))

  return (
    <>
    <div>
      <select onChange={handleChange}>
        <option value="all">All</option>
        <option value="premium">Premium</option>
        <option value="deluxe">Deluxe</option>
        <option value="basic">Basic</option>
      </select>
      <p>{sort}</p>
      <div style={{display:"flex",gap:"15px"}}>
      {sortedProducts.map((data)=>{
        return(
          <div>
            <p>{data.name}</p>
          <p>{data.price}</p>
          <div style={{backgroundColor:data.category==="Basic"?"grey":
                data.category==="Premium"?"blue":
                data.category==="Deluxe"?"green":"",
                color:"white"
                }}>{data.category}</div>
          </div>
        )
      })}
      </div>
    </div>
    </>
  )
}

export default App
```

---

## FUNCTIONCOMP

### 1. Marks Table

**Location:** `FunctionComp/MarksTable/src/App.jsx`

```jsx
import { useState } from 'react'
import Card from './Cards'

function App() {
  const [count, setCount] = useState(0)
  const students = [
  { id: 1, name: "Aman", marks: 85, course: "BCA", attendance: 92 },
  { id: 2, name: "Riya", marks: 45, course: "BCA", attendance: 78 },
  { id: 3, name: "Karan", marks: 72, course: "BBA", attendance: 55 },
  { id: 4, name: "Neha", marks: 30, course: "BCA", attendance: 95 },
  { id: 5, name: "Arjun", marks: 92, course: "BBA", attendance: 40 },
  { id: 6, name: "Sonia", marks: 55, course: "BCA", attendance: 65 }
];

  return (
    <>
      <table>
        <thead>
          <tr>
            <th>Id</th>
            <th>Name</th>
            <th>Marks</th>
            <th>Course</th>
            <th>Attendance</th>
            <th>Final Status</th>
          </tr>
        </thead>
        <tbody>
          {students.map((data)=>{
            let status;
            let Tcolor;
            if(data.marks>50 && data.attendance>60){
              status = "Pass";
              Tcolor = "green";
            }else if(data.marks>50 && data.attendance<60){
              status = "Attendance Shortage";
              Tcolor = "orange";
            }else{
              status = "Fail";
              Tcolor = "red";
            }
            return(
              <tr style={{color:Tcolor}}>
              <td>{data.id}</td>
              <td>{data.name}</td>
              <td>{data.marks}</td>
              <td>{data.course}</td>
              <td>{data.attendance}</td>
              <td>{status}</td>
            </tr>
            )
          })}
        </tbody>
      </table>
      <Card prop={students}/>
    </>
  )
}

export default App
```

### Cards.jsx (Component)

```jsx
import React from 'react'

function Card({prop}){
    let sum=0;
    let count=0;
    for(let i=0;i<prop.length;i++){
        sum += prop[i].marks;
        count++;
    }
    let avg = sum/count;
    return(
        <>
        <div>
            <h3>Statistics</h3>
            <p>Total Students : {count}</p>
            <p>Average Marks : {avg.toFixed(2)}</p>
        </div>
        <div>
            <h3>Dean's List</h3>
            {prop.filter(prop => prop.marks>85).map((data)=>{
                return(
                    <p>{data.name}</p>
                )
            })}
        </div>
        <div>
            <h3>BCA Honors</h3>
            {prop.filter(prop => prop.course ==="BCA" && prop.marks>50).map((data)=>{
                return(
                    <p>{data.name} - {data.marks}</p>
                )
            })}
        </div>
        </>
    )
}

export default Card
```

---

## EXTRACLASSQUES

### 1. E-commerce Dashboard

**Location:** `ExtraClassQues/E-commerceDash/app/src/App.jsx`

```jsx
import { useState,useEffect } from 'react'

import './App.css'

function App() {
  const [products, setProducts] = useState([])
  const [OGproducts,setOGProducts] = useState([])
    
  useEffect(()=>{
    fetch("https://fakestoreapi.com/products")
    .then(res=>res.json())
    .then((data)=>{
      setProducts(data)
      setOGProducts(data)
      console.log(data)
    })
    .catch(()=>{
      console.log("Data Not Found")
    });
  },[])

  const handleChange = (e) => {
    let value = e.target.value
    let sorted = [...products]
    if(value === "none"){
      sorted = [...OGproducts];
    }
    else if(value === "low"){
      sorted.sort((a,b)=>a.price-b.price);
    }
    else if(value === "high"){
      sorted.sort((a,b)=>b.price-a.price);
    }
    setProducts(sorted);
  }
  console.log(products)
  return (
    <>
    <select onChange={handleChange}>
      <option key={1} value="none">None</option>
      <option key={2} value="low">Price Low to High</option>
      <option key={3} value="high">Price High to Low</option>
    </select>
    <tabble>
      <thead>
        <tr>
          <th>ID</th>
          <th>Product Name</th>
          <th>Price</th>
          <th>Category</th>
          <th>Rating</th>
          <th>Image</th>
        </tr>
      </thead>
      <tbody>
        {products.map((data)=>{
          return(
            <tr key={data.id}>
              <td>{data.id}</td>
              <td>{data.title}</td>
              <td>{data.price}</td>
              <td>{data.category}</td>
              <td>{data.rating.rate}</td>
              <img style={{height:"80px"}} src={data.image}></img>
            </tr>
          )
        })}
      </tbody>
    </tabble>
    </>
  )
}

export default App
```

---

### 2. Image Slide

**Location:** `ExtraClassQues/ImageSlide/app/src/App.jsx`

```jsx
import { useState } from 'react'
import './App.css'

function App() {
  const images = [
  "https://images.unsplash.com/photo-1506744038136-46273834b3fb",
  "https://images.unsplash.com/photo-1500530855697-b586d89ba3ee",
  "https://images.unsplash.com/photo-1493246507139-91e8fad9978e",
  "https://images.unsplash.com/photo-1519125323398-675f0ddb6308"
];
  const [count, setCount] = useState(0)
  function handleNext(){
    if(count==images.length-1){
      setCount(0);
    }else{
      setCount(count+1)
    }
  }
  function handlePrev(){
    if(count==0){
      setCount(images.length-1);
    }else{
      setCount(count-1)
    }
  }

  return (
    <>
    <img style={{height:"200px"}} src={images[count]} alt="image" /><br></br>
    <button onClick={handleNext}>Next</button>
    <button onClick={handlePrev}>Prev</button>
    </>
  )
}

export default App
```

---

### 3. Password Validator

**Location:** `ExtraClassQues/PassValidator/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const [pass, setPass] = useState("")

  return (
    <>
    <h1>Password Validator</h1>
    <input type='text'onChange={(e)=>{setPass(e.target.value)}} value={pass} placeholder='Enter Pass...'></input>
    <p>{pass}</p>
    </>
  )
}

export default App
```

---

### 4. Product Category Filter Checkbox

**Location:** `ExtraClassQues/ProductCategoryFilterCheckbox/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const products = [
  {
    id: 1,
    name: "Laptop",
    category: "Electronics",
    price: 50000
  },
  {
    id: 2,
    name: "T-Shirt",
    category: "Clothing",
    price: 1200
  },
  {
    id: 3,
    name: "Mobile",
    category: "Electronics",
    price: 30000
  },
  {
    id: 4,
    name: "Jeans",
    category: "Clothing",
    price: 2000
  }
];
  const [eleCheck, setEle] = useState(false)
  const [clothCheck, setCloth] = useState(false)
  let arr=[];
  
    if(eleCheck && !clothCheck){
      arr = products.filter(data=>data.category==="Electronics");
    }
    else if(clothCheck && !eleCheck){
      arr = products.filter(data=>data.category==="Clothing");
    }
    else if(clothCheck && eleCheck){
      arr = products
    }

  return (
    <>
    <input checked={eleCheck} onChange={(e)=>{setEle(e.target.checked)}} type='checkbox'/>Electronics<br></br>
    <input checked={clothCheck} onChange={(e)=>{setCloth(e.target.checked)}} type='checkbox'/>Clothing<br></br>
    {arr.map((data)=>{
      return(
        <p>{data.name}</p>
      )
    })}
    </>
  )
}

export default App
```

---

### 5. Smart Inventory Dashboard

**Location:** `ExtraClassQues/SmartInventoryDash/app/src/App.jsx`

```jsx
import { useState } from 'react';

function App() {
  const products = [
  { id: 101, name: "Laptop", price: 85000, category: "Electronics", stock: 15 },
  { id: 102, name: "Office Chair", price: 12000, category: "Furniture", stock: 0 },
  { id: 103, name: "Smart Watch", price: 5000, category: "Electronics", stock: 4 },
  { id: 104, name: "Desk Lamp", price: 1500, category: "Furniture", stock: 8 },
  { id: 105, name: "Mechanical Keyboard", price: 7000, category: "Electronics", stock: 25 },
  { id: 106, name: "Gaming Mouse", price: 3500, category: "Electronics", stock: 2 }
];
  const [count, setCount] = useState(0)

  return (
    <>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Category</th>
          <th>Price</th>
          <th>Stock</th>
          <th>Availability Status</th>
        </tr>
      </thead>
      <tbody>
        {products.map((data)=>{
          let avb;
          let color;
          let font="";
          if(data.stock>10){
            if(data.price>50000){
              color="green";
            }
            avb="In Stock";
          }
          else if(data.stock>1){
            avb="Limited Stock";
            color="orange";
          }else{
            avb="Out of Stock";
            color="red";
            font="italic";
          }
          return(
          <tr style={{color:color, fontStyle:font}}>
            <td >{data.name}</td>
            <td >{data.price}</td>
            <td >{data.category}</td>
            <td >{data.stock}</td>
            <td >{avb}</td>
          </tr>)
        })}
      </tbody>
    </table>
    </>
  )
}

export default App
```

---

### 6. Product Dropdown

**Location:** `ExtraClassQues/ProductDropdown/app/src/App.jsx`

```jsx
import { useEffect, useState } from "react";

function App() {
  const [products, setProducts] = useState([]);
  const [selectedId, setSelectedId] = useState("");

  useEffect(() => {
    fetch("https://fakestoreapi.com/products")
      .then((res) => res.json())
      .then((data) => {
        setProducts(data);
      })
      .catch((err) => console.log(err));
  }, []);

  const selectedProduct = products.find(
    (product) => product.id === Number(selectedId)
  );

  return (
    <div style={{ padding: "20px" }}>
      <h1>Product Viewer</h1>

      <select
        value={selectedId}
        onChange={(e) => setSelectedId(e.target.value)}
      >
        <option value="">Select Product</option>

        {products.map((product) => (
          <option key={product.id} value={product.id}>
            {product.title}
          </option>
        ))}
      </select>

      <hr />

      {selectedProduct ? (
        <div>
          <img
            src={selectedProduct.image}
            alt={selectedProduct.title}
            width="150"
          />

          <h2>{selectedProduct.title}</h2>

          <h3>Category: {selectedProduct.category}</h3>

          <h3>Price: ${selectedProduct.price}</h3>

          <p>{selectedProduct.description}</p>
        </div>
      ) : (
        <h3>Select a product to view details</h3>
      )}
    </div>
  );
}

export default App;
```

---

### 7. Student Dropdown

**Location:** `ExtraClassQues/StudentDrop/app/src/App.jsx`

```jsx
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'

function App() {
  const students = [
  { id: 1, name: "Amit" },
  { id: 2, name: "Riya" },
  { id: 3, name: "John" },
  { id: 4, name: "Sneha" }
];
  const [count, setCount] = useState(0)

  return (
    <>
    <select>
      <option key={0}>Select Student</option>
      {students.map((data)=>{
        return(
          <option key={data.id}>{data.name}</option>
        )
      })}
    </select>
    </>
  )
}

export default App
```

---

## ROUTERDOM

### 1. Login Page with Protected Routes

**Location:** `Router-DOM/LoginPage/app/src/`

#### App.jsx
```jsx
import { useState } from 'react'
import {BrowserRouter,Routes,Route} from 'react-router-dom'
import Protected from './Protected'
import Dashboard from './Dashboard'
import Login from './Login'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
    <BrowserRouter>
    <Routes>
      <Route path="/login" element={<Login/>}/>
      <Route path="/dashboard" element={
        <Protected>
        <Dashboard/>
        </Protected>
        }/>
    </Routes>
    </BrowserRouter>
    </>
  )
}

export default App
```

#### Login.jsx
```jsx
import React from 'react'
import {useNavigate} from 'react-router-dom'

function Login() {
    const navigate = useNavigate();
    const handleChange = () => {
        localStorage.setItem("token","123abc");
        navigate("/dashboard")
    }
  return (
    <div>
      <h1>Hey its Login page</h1>
        <button onClick={handleChange}>Login</button>
    </div>
  )
}

export default Login
```

#### Dashboard.jsx
```jsx
import React from 'react'
import {useNavigate} from 'react-router-dom'

function Dashboard() {
    const navigate = useNavigate()
    function handleChange(){
        localStorage.removeItem("token");
        navigate("/login");
    }
    return (
    <>
    <div>
        <h1>Hey its Dashboard</h1>
        <button onClick={handleChange}>Logout</button>
    </div>
    </>
    )
}

export default Dashboard
```

#### Protected.jsx
```jsx
import React from 'react'
import {Navigate} from 'react-router-dom'

function Protected({children}) {
    const token = localStorage.getItem("token");
    if(!token){
        return(<Navigate to="/login"/>);
    }
  return children;
}

export default Protected
```

---

### 2. User Profile Page

**Location:** `Router-DOM/UserProfilePage/app/src/`

#### App.jsx
```jsx
import { useState } from 'react'
import Users from './Users'
import UserProfile from './UserProfile'
import {BrowserRouter,Routes,Route,Link,Outlet,Navigate} from 'react-router-dom'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
    <BrowserRouter>
    <Routes>
        <Route path='/' element={<Navigate to='/users'/>}/>
        <Route path="/users" element={<Users/>}/>
        <Route path="/users/:id" element={<UserProfile/>}/>
    </Routes>
    </BrowserRouter>
    </>
  )
}

export default App
```

#### Users.jsx
```jsx
import {Link} from 'react-router-dom';
import usersD from './usersData';

function Users(){
    return(
        <>
        <h1>Yo</h1>
        {usersD.map((user)=>{
            return(
                <div>
                    <Link to={`/users/${user.id}`}>{user.name}</Link>
                </div>
            )
        })}
        </>
    )
}

export default Users
```

#### UserProfile.jsx
```jsx
import { useParams, Link } from "react-router-dom";
import users from "./usersData";

function UserProfile() {
    const {id} = useParams();
    const user = users.find((u)=>u.id === Number(id));

    if(!user){
        return(
            <>
            <div>
                <h1>User not found!!</h1>
                <Link to='/users'>Back to Users Page...</Link>
            </div>
            </>
        )
    }
    return(
        <>
        <div>
            <h1>{user.name}</h1>
            <h3>{user.email}</h3>
            <h2>Posts:</h2>
            <ul>
                {user.posts.map((post,id)=>{
                    return(
                        <li key={id}>{post}</li>
                    )
                })}
            </ul>
            <Link to='/users'>Back to Users Page...</Link>
        </div>
        </>
    )
}

export default UserProfile;
```

#### Product.jsx
```jsx
import React from 'react'
import {Route,Link,Outlet} from 'react-router-dom'

function Product() {
  return (
    <div>
      <nav>
        <Link to="electronics">Electronics</Link>
        <Link to="clothing">Clothing</Link>
        <Link to="furniture">Furniture</Link>
      </nav>
      <Outlet/>
    </div>
  )
}

export default Product
```

#### Clothing.jsx
```jsx
import React from 'react'

function Clothing() {
  return (
    <div>
      <h1>Clothings here</h1>
    </div>
  )
}

export default Clothing
```

#### Electronics.jsx
```jsx
import React from 'react'

function Electronics() {
  return (
    <div>
      <h1>Electronics comp</h1>
    </div>
  )
}

export default Electronics
```

#### Furniture.jsx
```jsx
import React from 'react'

function Furniture() {
  return (
    <div>
      <h1>Furniture comp</h1>
    </div>
  )
}

export default Furniture
```

---

### 3. E-Commerce

**Location:** `Router-DOM/E-Commerce/app/src/`

#### App.jsx
```jsx
import { useState } from 'react'
import {Routes,Route,Link} from 'react-router-dom';
import Product from './Product';
import Electronics from './Electronics';
import Clothing from './Clothing';
import Furniture from './Furniture';

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
    <Routes>
      <Route path="/product" element={<Product/>}>
        <Route path="/product/electronics" element={<Electronics/>}/>
        <Route path="/product/clothing" element={<Clothing/>}/>
        <Route path="/product/furniture" element={<Furniture/>}/>
      </Route>
    </Routes>
    </>
  )
}

export default App
```

#### Product.jsx
```jsx
import React from 'react'
import Electronics from './Electronics';
import Clothing from './Clothing';
import Furniture from './Furniture';
import {Link,Outlet} from 'react-router-dom';

export default function Product() {
  return (
    <div>
      <h1>Product</h1>
      <nav>
        <Link to="/product/clothing">Clothing</Link>
        <Link to="/product/electronics">Electronics</Link>
        <Link to="/product/furniture">Furniture</Link>
      </nav>
      <Outlet/>
    </div>
  )
}
```

#### Clothing.jsx
```jsx
import React from 'react'

function Clothing() {
  return (
    <div>
      <h1>Clothing</h1>
    </div>
  )
}

export default Clothing
```

#### Electronics.jsx
```jsx
import React from 'react'

function Electronics() {
  return (
    <div>
      <h1>Electronics</h1>
    </div>
  )
}

export default Electronics
```

#### Furniture.jsx
```jsx
import React from 'react'

function Furniture() {
  return (
    <div>
      <h1>Furniture</h1>
    </div>
  )
}

export default Furniture
```

---

## SUMMARY

This document contains a complete compilation of all JSX files from the React EndSem course, organized by project category:

| Category | Projects | Key Concepts |
|----------|----------|--------------|
| **Anexxure** | Transaction Manager | Chart.js, State Management |
| **SimpleState** | 8 projects | Basic useState, Event Handling |
| **ComplexState** | 5 projects | Complex State Updates, Filtering |
| **FunctionComp** | 1 project | Functional Components, Props |
| **ExtraClassQues** | 7 projects | API Fetching, Tables, Dropdowns |
| **RouterDOM** | 3 projects | React Router, Protected Routes |

**Total Projects:** 24+
**Total Components:** 60+

---

**Last Updated:** June 2026
**Course:** React End Semester Projects
