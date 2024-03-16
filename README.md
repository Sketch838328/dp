PRACTICAL 1
AIM: Install create react app and create a new create project
THEORY:
import React from 'react';
function Studentlist(props){
  return(
    <>
      <h1> Name: {props.name}</h1>
      <h1>Rollno :{props.rollno}</h1>
      <h1>Class : {props.class}</h1>
    </>
  );
}
function Student(){
  return(
    <>
    <Studentlist name= "Aman" rollno="322" class="HMAD II"/>
    </>

    );
}
export default Student;

PRACTICal 2
AIM: create todolist with different expression ,apply css via class name
JSX DEF…
JS EXPRESSION 
CODE:
import React,{ useState } from 'react';
const TodoList =() => {
  const [todos, setTodos] = useState([
  { id: 1, text: 'Learn React', completed: false },
  { id: 2,text: 'Build a todo App', completed: false },
  { id: 3, text: 'Style with CSS', completed: false },
  ]);
  const handleToggle = (id) =>{
    setTodos((prevTodos) => 
      prevTodos.map((todo) =>
        todo.id === id ? { ...todo, completed: !todo.completed } : todo
        )
      );
  };
  return (
    <div className="todo-list">
      <h2>Todo List </h2>
      <ul>
        {todos.map((todo) =>(
          <li
            key={todo.id}
            className={todo.completed ? 'completed' : ''}
            onClick={() => handleToggle(todo.id)}
          >
            {todo.completed ? <s>{todo.text}</s> : todo.text}
          </li>
        ))}
      </ul>
      <style>
        {`  
          .todo-list {
            font-family: 'Arial', sans-serif;
          }
          ul {
            list-style-type: none;
            padding: 0;
          }
          li {
            cursor: pointer;
            margin-bottom:8px;
          }
          .completed{
            text-decoration: line through;
            color: #888;
          }
          }
        `}
      </style>
    </div>
  );
};
export default TodoList;
OUTPUT:





Practical 3
AIM:
CODE:
App.js:-

import React,{ useState } from 'react';
const MultiStepForm =() => {
  const [step, setStep] = useState(1);
  const [ formData , setFormData ] = useState ({
    firstName : ' ' ,
    lastName: ' ' ,
    email : ' ',
    password :' ',
  });
  const handleChange = (e) =>{
    const {name , value} = e.target ;
    setFormData((prevData) => ({...prevData,[name]: value }))

  };
   const nextStep = ( ) =>{
    setStep ((prevStep) => prevStep + 1 );
   };

   const prevStep = ()=>{
    setStep((prevStep) => prevStep - 1 );
   };

   const handleSubmit = (e) => {
    e.preventDefault();
    console.log ('Form submitted :' ,formData);
   };

   const renderStep = ( ) =>{
    switch (step){
      case 1:
        return (
        <div>
          <label> First Name :</label>
            <input
              type ="text"
              name ="firstName"
              value ={formData.firstName}
              onChange = {handleChange}
          />
        </div>
        );
    case 2:
      return (
        <div>
        <label> Last Name :</label>
        <input 
          type = "text"
          name = "lastName"
          value ={formData.lastName}
          onChange = {handleChange}
        />
      </div>
      );
    case 3:
      return(
      <div>
      <label> Email:</label>
      <input 
        type = "email"
        name ="email"
        value ={formData.email }
        onChange = {handleChange}
      />
      <label> Password :</label>
      <input
        type = "password"
        name = "password"
        value ={formData.password}
        onChange = {handleChange}
      />
      </div>
      );
    default:
      return null;
    }
   };
   return(
   <form onSubmit ={handleSubmit}>
   <h2>Step{step}</h2>
   {renderStep()}
   <div>
   {step >1&&<button type="button" onClick={prevStep}>Previous</button>}
  {step <3 ? <button type ="button" onClick ={nextStep} > Next </button>:<button type="submit">Submit</button>}
  </div>
  </form>
   );
  };
  export default MultiStepForm;


OUTPUT:






















Practical 4
code
App.js
import React from 'react';
import './FlexboxFragment.css';
 const FlexboxFragment = () => {
  return(
      <div className="flexbox-container">
      <div className="flexbox-item python">Python</div>
      <div className="flexbox-item java">Java</div>
      <div className="flexbox-item javascript">JavaScript</div>
      </div>

    );
 };

 export default FlexboxFragment;
CODe
Flexboxfragment.css
.flexbox-container{
  display: flex;
  justify-content: space-between;
  align-items: center;

}
.flexbox-item{
  flex:1;
  padding:20px;
  border:1px solid #ccc;
  margin:10px;
  text-align: center;
  font-size: 1.5em;
}
.python{
  background-color: #3572A5;
  color: #ffffff;

}

.java{
  background-color: #5382a1;
  color: #ffffff;
  flex:2;/*make the java fragment twice as wide*/

}
.javascript{
  background-color: #f1e05a;
  color: #000000;
}
output:

Practical 5
Aim:
CODE:
App.js
import React from'react';
import AuthorCard from './AuthorCard';

const App = () =>{
  const authorData1= {
    name:'Aman Kanojiya',
    biography:'A prolific authoe with a passion for storytelling.',
    books:['Its happen yesterday','Atomics Habits','Zestech'],

  };

  const authorData2 = {
    name:'Salman Khan',
    biography:'Award-winning Indian author exploring diverse themes.',
    books:['The silent Hills','Echoes of tradition','Whispers of Tomorrow'],
  };
  const authorData3= {
    name:'Shivom Kanojiya',
    biography:'Bestselling author from India known for gripping thrillers.',
    books:['Shadowa in the Mist','The Crimson Conspiracy','Fatal Deception'],
  };

  return(
      <div className="app">
      <AuthorCard author={authorData1}/>
      <AuthorCard author={authorData2}/>
      <AuthorCard author={authorData3}/>
      </div>
    );  
};

export default App;

Index.css
.app{
  display:flex;
  justify-content: space-around;
  align-items: flex-start;
  flex-wrap: wrap;
  padding: 20px;
  background-color: #f0f0f0;
  min-height: 100vh;
}

/*ensure each card has some space around it*/

.author-card{
  margin: 10px;
}

AuthorCard.js
import React from 'react';
import './AuthorCard.css';

const AuthorCard =({author}) => {
	const {name,biography,books}=author;
	return(
		<div className="author-card">
		<h2>{name}</h2>
		<p>{biography}</p>
		<h3>Books by {name}:</h3>
		<ul>
		{books.map((book,index) => (
		<li key={index}>{book}</li>
		))}
		</ul>
		</div>
	);
};
export default AuthorCard;

AuthorCard.css
.author-card{
	background-color: #f8f8f8;
	border: 2px solid #4CAF50;
	border-radius: 10px;
	padding: 20px;
	margin: 20px;
	width: 400px;

}
h2{
	color: #4CAF50;
	font-size: 24px;
	margin-bottom: 10px;

}
p{
	color: #333;
	font-size: 20px;
	margin-bottom: 10px;

}
ul{
	padding: 0;
	list-style: none;

}
li{
	color: #555;
	font-size: 14px;
	margin-bottom: 8px;

}
/*Add some animation for more attractive appearance*/
.author-card:hover{
	transform:scale(1.05);
	transition: transform 0.3e ease-in-out;
}

Output:




















Practical 8
CODE
App.js
import React from 'react';
import Counter from './Counter';

const App =()=>{
  return(
    <div>
    <Counter/>
    </div>
    );
};
export default App;

Counter.js
import React,{useState, useEffect } from 'react';
const Counter=()=>{
  //State for the counter value
  const [count,setCount] = useState(0);

  //effect to update the document title with the current count
  useEffect(()=>{
    document.title = 'Count:${count}';

  },[count]);
  //funtion to handle increment 
  const increment =()=>{
    setCount(count+1);
  };

  //function to handle decrement
  const decrement =()=>{
    setCount(count-1);
  };
  return(
    <div>
    <h1>Counter</h1>
    <p>Count:{count}</p>
    <button onClick={increment}>Increment</button>
    <button onClick={decrement}>Decrement</button>
    </div>
    );
};
export default Counter;
OUTPUT:








pract10
code:
app.js
import React, { useState, useEffect } from 'react';
const FootballGame =()=>{
  const[points,setPoints] = useState(0);
  const[chatMessages,setChatMessages]=useState([]);
  const[newMessage,setNewMessage]=useState('');

  useEffect(()=>{
    const intervalId=
     setInterval(()=>setPoints(prev=>prev+Math.floor(Math.random()*5)+1),5000);
    return () => clearInterval(intervalId);
  },[]);

  return(
    <div>
      <h1>Football Game</h1>
      <p>Points:{points}</p>
      <div>
        <h2>Chat</h2>
        <div style={{border:'1px solid #ccc',padding:'10px',height:'150px',overflowY:'auto'}}>
          {chatMessages.map(({ text, time },index) => (
            <div key={index}><strong>{time.toLocaleTimeString()}:</strong>{text}</div>
          ))}
          </div>
          <input type="text" value={newMessage} onChange={e=>setNewMessage(e.target.value)} placeholder="Type your message..."/>
          <button onClick={()=>setChatMessages([...chatMessages,{text:newMessage,time:new Date()}])}>Send</button>
          </div>
          </div>

  );
};

export default FootballGame;

OUTPUT:


App.js
import React from 'react';
import ShoeStore from './ShoeStore';


const App = () => {
  return (
    <div>
      <ShoeStore />
    </div>
  );
};
export default App;


ShoeStore.js
import React, { useState } from 'react';


const ShoeStore = () => {
  //state for user login status
  const [isLoggedIn, setLoggedIn] = useState(false);


  //State for email subscription
  const [isSubscribed, setSubscribed] = useState(false);


  //Map function for generating discount based on the shoe type
  const getDiscount = (shoeType) => {
    const discountMap = {
      running: 10,
      casual: 5,
      formal: 15,
    };
    return discountMap[shoeType] || 0;
  };
  return (
    <div>
      <h1>Shoe Store </h1>
      {/*Conditional rendering based on login status*/}
      {isLoggedIn ? (
        <p>Welcome back! Explore our latest collection.</p>
      ) : (
        <p>Please log in to access exclusive deals.</p>
      )}
      {/*Email subscription form.*/}
      {!isSubscribed && (
        <div>
          <p>Subscribe to our newsletter and get additional discounts:</p>
          <form>
            <label>
              Email:
              <input type="email" />
            </label>
            <button
              type="submit"
              onClick={() => setSubscribed(true) || setLoggedIn(true)}
              required
            >
              subscribe
            </button>
          </form>
        </div>
      )}
      {/*Discount mapping example */}
      <p>Discounts for different shoe types:</p>
      <ul>
        <li>Running Shoes: {getDiscount('running')}%off</li>
        <li>Casual Shoes:{getDiscount('casual')}%off</li>
        <li>Formal Shoes:{getDiscount('formal')}%off</li>
      </ul>
    </div>
  );
};
export default ShoeStore;




WEBPACK
what is webpack in react
with the help of the well-liked module bundler webpack,react apps may create optimized bundler from a variety of files, including javascript,css and pictures. It offers a cionveninet build process for deploying React

why web pack is used
*Build process streamlined : webpack can automatically combine all of the javascript files in your react application into single file, which can greatly streamline the build procedure.
*code splitting: by just loading the code required for the current page , webpack can enhance efficiency by dividing your javascript code into small bundles.
*improved performance : webpack can optimize your javascript code for 
*Better developer experience
Support for ES6:by transpiling ES6 code with webpack ,we can use the most resent javascript capabilities in the reACT APPS.
Hot reloading:we may make changes to the code and see them take effect right away without having to restart the server by using webpack to hot reload your react application.this is can speed development 
Source map: source map allows to map the transform file back to the original source file the main purpose of the source map is to add debugging and help investigating issues

entry:
The entry point is the starting point for webpack to build the dependency graph . It could be a single file or multiple files.
//webpack.config.js
module.exports={
entry:’./src/index.js’,
};

Output:
The output specifies where webpack should emit the bundled files and what to name them
//webpack.config.js
const path = require (‘path’);
module.exports={
output:{
filename:’bundle.js’,
path:path.resolve(__dirname,’dist’),
},
};
Loaders:
Loader enable webpack to process different file types beyond Javascript by transforming them into valid modules.
//webpack.config.js
{module.exports={
module:{
rules:[


test:/\.css$/,
use:[‘style-loader’,css-loader’],
},
],
},
};

Plugins:
Plugins are powerful tools to perform tasks that go beyond the capabilities of loaders. They can optimize bundles, add assets, or perform other build tasks.
//webpack.config.js
const HtmlWebpackPlugin = require(‘html-webpack-plugin’);
module.exports={
plugins:[new HtmlWebpackPlugin()],
};
Mode:
set the mode to ‘development’,’production’, or ‘none’ to enable built-in optimizations accordingly.
//webpack.config.js
module.exports={
mode:’developer’,
};
the modes setting 


DevServer:
webpack Dev Server is a development server that provides live reloading , allowing you to see changes in real-time without manual refresh
//webpack.config.js
module.exports={


Installation:
we can install webpack and its command-line interface(CLI) globally or locally within your project:
npm install webpack webpack-cli -- save-dev













PRACTICAL 6: 
CORRECT ONE:
CODE:
App.js
import React, { useState } from 'react';
import Product from './Product';
import Cart from './Cart';

const App = () => {
  const [cartItems, setCartItems] = useState([]);

  const addToCart = (item) => {
    setCartItems((prevItems) => [...prevItems, { ...item, quantity: 1 }]);
  };

  const removeFromCart = (itemId) => {
    setCartItems((prevItems) => prevItems.filter((item) => item.id !== itemId));
  };
  const products = [
    { id: 1, name: 'Product1', price: 19.99 },
    { id: 2, name: 'Product2', price: 29.99 },
    { id: 3, name: 'Product3', price: 9.99 },
  ];
  return (
    <div className="app">
      <div className="product-list">
        <h2>Product List </h2>
        {products.map((product) => (
          <Product key={product.id} {...product} addToCart={addToCart} />
        ))}
      </div>
      <Cart items={cartItems} removeFromCart={removeFromCart} />
    </div>
  );
};
export default App;

Cart.js
import React from 'react';
import PropTypes from 'prop-types';
import CartItem from './CartItem';

const Cart = ({ items, removeFromCart }) => {
  return (
    <div className="cart">
      <h2> Shopping Cart </h2>
      {items.map((item) => (
        <CartItem key={item.id} {...item} removeFromCart={removeFromCart} />
      ))}
    </div>
  );
};

Cart.propTypes = {
  items: PropTypes.array.isRequired,
  removeFromCart: PropTypes.func.isRequired,
};

export default Cart;

CartItem.js
import React from 'react';
import PropTypes from 'prop-types';

const CartItem = ({ id, name, price, quantity, removeFromCart }) => {
  return (
    <div className="cart-item">
      <span>{name}</span>
      <span> ${price.toFixed(2)}</span>
      <span> Quantity: {quantity}</span>
      <button onClick={() => removeFromCart(id)}>Remove</button>
    </div>
  );
};

CartItem.propTypes = {
  id: PropTypes.number.isRequired,
  name: PropTypes.string.isRequired,
  price: PropTypes.number.isRequired,
  quantity: PropTypes.number.isRequired,
  removeFromCart: PropTypes.func.isRequired,
};

export default CartItem;

Product.js
import React from 'react';
import PropTypes from 'prop-types';

const Product = ({ id, name, price, addToCart }) => {
  return (
    <div className="product">
      <h3>{name}</h3>
      <p>${price.toFixed(2)}</p>
      <button onClick={() => addToCart({ id, name, price })}>
        {' '}
        Add to Cart{' '}
      </button>
    </div>
  );
};

Product.propTypes = {
  id: PropTypes.number.isRequired,
  name: PropTypes.string.isRequired,
  price: PropTypes.number.isRequired,
  addToCart: PropTypes.func.isRequired,
};
export default Product;

Prac7
App.js
import React from 'react';
import Dropdown from 'react-bootstrap/Dropdown';

function SubjectDropdown({year,subjects}){
  return(
    <Dropdown>
    <Dropdown.Toggle variant= "primary" 
   id={'dropdown-${year}'} className="dropdown-toggle">
    {year}Subjects
    </Dropdown.Toggle>

    <Dropdown.Menu className="dropdown-menu">
    {subjects.map((subject,index)=>(
    <Dropdown.Item key={index} className="dropdown-item">
    {subject}</Dropdown.Item>
    ))}
    </Dropdown.Menu>
    </Dropdown>


    );
}

function App(){
  const FYSubjects=['Mathematics','Physics','Chemistry','Biology'];
  const SYSubjects=['History','Geography','English','Economics'];
  const TYSubjects=['Computer Science','Accounting','Business Studies','Psychology'];

  return(
  <div className="container">
  <div className="row">
  <div className="col">
  <SubjectDropdown year="FY" subjects={FYSubjects}/>
  </div>
  <div className="col">
  <SubjectDropdown year="SY" subjects={SYSubjects}/>
  </div>
  <div className="col">
  <SubjectDropdown year="TY" subjects={TYSubjects}/>
  </div>
  </div>
  </div>
  );
}
export default App;
index.css
.dropdown-toggle{
  padding: 10px 20px;
margin: 20px
}

.dropdown-menu{
  padding: 5px;
}
.dropdown-item{
  padding:5px 20px;
}
practical 12/11
CODE:
App.js
import React from 'react';
import SyntheticEventsDemo from './SyntheticEventsDemo';

function App(){
  return(
    <div className="App">
    <SyntheticEventsDemo/>
    </div>
    );
}
export default App;

SyntheticEventsDemo.js
import React from 'react';

class SyntheticEventsDemo extends React.Component{
  handleClick=(event)=>{
    alert('Button clicked!');
  };

  render(){
    return(
      <div>
      <h1>Synthetic Events Demo</h1>
      <button onClick={this.handleClick}>Click me</button>
      </div>
      );
  }
}
export default SyntheticEventsDemo;









