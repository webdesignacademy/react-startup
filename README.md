# react-startup
A brief overview of React - Startup notes, components etc.
STARTING A NEW PROJECT

React can be (and should be) installed via CLI (command line interface). You can use windows command promt or vsc to run the below commands.

create folder on hd  c:/reactapp
go into folder  cd  c:/reactapp
npm create-react-app projectname
npm install   =   npm i
npm start

This will create your file structure with a start template with all the files required including node, webpack and all dependencies.

The main file will be the App.js. You can then create multiple components / pages in separate JS files. The main thinking in react is to break every section of your app or website into different components. Each component will be a seperate js file which will contain the code and functionality of that section inside each file. You can even break smaller sections/components into separate files.  -  See:
 
Docs - https://reactjs.org/docs/getting-started.html#learn-react
Thinking in react   - https://reactjs.org/docs/thinking-in-react.html

The below is a basic example of a component called MovieList (can also be About) 

Each component must also be exported right at the bottom of the file by using 
export default filename


A BASIC COMPONENT

import React from 'react'

const MovieList = () => {
	return(
		<div 
		  className="container"
 		  style={{marginTop:'80px',color:'red'}}
			<h1 className="heading">My App</h1>
		</div>
	);
}

export default MovieList

When we have HTML in our return function (also known as JSX) we use className instead off class. We can also add inline styles inside double curly brackets and look at the style names with a - in it. We will remove the dash and camel case it like marginTop. Look at JSX below.                


This file then needs to be imported in the App.js file at the top below the import React from.

App.js

import React from 'react'
import MovieList from './MovieList'  or  './Components/MovieList'

Then we need to "call" the movielist item in the returen function of the app.

function App(){

	return(
		<div>
		  <MovieList/>
		</div>
	);
}


REACT ROUTER
The react router is basically creating a route / path / link to different components / pages in our app

You might have to install react-router-dom via npm like you do when installing react. In your project folder in CLI you just run      npm install react-router-dom   then   
npm start  again

As mentioned in the beginning each page will be a separate js file or component. In each component you will import React.

In order to use react router you also need to import BrowserRouter, Switch and Route from React Router Dom. In the below example Im importing BrowserRouter as Router (optional but shorter) then im using <Router/> to wrap my code. 

Also be sure to import all your pages/components into the main app file where you want to display them. Se below full example of all imports.

import React from 'react'
import {BrowserRouter as Router, Switch, Route} from 'react-router-dom';
import Nav from './Nav';
import Nav from './Home';
import Nav from './About';
import Nav from './Shop';


You then wrap your app code includeing the nav and different components inside a <Router>

App.js

return(
	<Router>
		<div className="App">
			<Nav/>
			<Switch>
			  <Route exact path="/" component={Home} />
			  <Route path="/about" component={About} />
			  <Route path="/shop" component={Shop} />
			  <Route path="/contact" component={Contact} />
			<Switch/>
		</div>
	</Router/>
)

Check the exact path on the home page. This is to ensure the route does not load multiple pages for using just the / in the URL (for home). This is where the Switch comes into play.

Inside your nav.js file is where you will create the actual links to the different "pages/components"

Nav.js

import React from 'react'
import {Link} from 'react-router-dom';
 
return(
	<Router>
		<nav className="nav">
		  <ul>
			<Link to="/">
			   <li>Home</li>
			</Link>
			<Link to="/about">
			   <li>About</li>
			</Link>
			<Link to="/shop">
			   <li>Shop</li>
			</Link>
		  </ul>
		</nav>
	</Router/>
)
export default Nav;

We are using the Link above and importing it as well. Be sure to also check out NavLink. The NavLink will add a active class to the menu item.                                                                   

We are using the Link instead of an <a> tag. React default behaviour will then load the         pages/components asyncrously. With an a tag it will do a new request and reload the page. 
AND THIS IS WHAT MAKES IT SO POPULAR AS AN SPA (SINGLE PAGE APP) 


REACT STATE
The react state is basically the data beign used at a specific time. Like when someone click on a button and we want to update data in the file (text, numbers, arrays etc). React does not 'react to changes in a document, like when clicked on). 

We use the HOOK called STATE in order to achieve this. Update data. The hook is called useState()

You need to import the useState hook when you use it in your components.

import {useState} from 'react'


const [name, setName = useState('brian');

const btnClick = () {
	setName('Gordon);
}
return(
	<p>{name}</p>
)
<button onClick={btnClick}>UPDATE NAME</p>

In the example above the initial value for name is Brian. When we click the button the value will be updated to Gordon


OUTPUTTING DATA WITH JS MAP FUNCTION
In order to output a list of data (json, array) you can use the JS map() function. 

Each item must have a unique identifier like an id. We can use the key{} keyword to do that.

asd

