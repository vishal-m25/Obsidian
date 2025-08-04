
--- plugin-prettier: true ---

# General

 - Node.js is a run time environment that used browser engine to run the server in V8 JavaScript engine , the core of chrome browser outside the browser to provide high performance
 - Express is a node js framework

- arrow function will not be declared in the time of hoisting, but while the execution begins it is declared.
- **fragments** in react is used to group html elements with the use of `<div></div>`  instead 

## Requests
- ### options 
| **Method**  | **Purpose**                                  |
| ----------- | -------------------------------------------- |
| **GET**     | Retrieve data (no modification).             |
| **POST**    | Create a new resource (send data to server). |
| **PUT**     | Update/replace an existing resource.         |
| **PATCH**   | Partially update a resource.                 |
| **DELETE**  | Remove a resource.                           |
| **OPTIONS** | Check supported HTTP methods for a resource. |
| **HEAD**    | Like GET but returns only headers (no body). |
- ### structure 
| **Component** | **Description**                               |
| ------------- | --------------------------------------------- |
| **Method**    | The action to perform (GET, POST, etc.)       |
| **URL**       | The resource address (endpoint).              |
| **Headers**   | Meta-information (content type, auth, etc.).  |
| **Body**      | Data sent with the request (for POST/PUT).    |
| **Params**    | Data in URL (query params or path variables). |
## Status code 
| **Code** | **Meaning**                    | **Description**                                  |
| -------- | ------------------------------ | ------------------------------------------------ |
| **200**  | **OK**                         | Request succeeded, response contains the result. |
| **201**  | **Created**                    | Resource successfully created (e.g., POST).      |
| **204**  | **No Content**                 | Request succeeded, but no response body.         |
| **301**  | **Moved Permanently**          | Resource has been permanently moved.             |
| **302**  | **Found** (Temporary Redirect) | Resource temporarily moved to another URL.       |
| **400**  | **Bad Request**                | Invalid request from the client.                 |
| **401**  | **Unauthorized**               | Authentication required or failed.               |
| **403**  | **Forbidden**                  | Request is understood but refused by the server. |
| **404**  | **Not Found**                  | Resource not found.                              |
| **405**  | **Method Not Allowed**         | HTTP method not supported for this endpoint.     |
| **409**  | **Conflict**                   | Conflict with the current state of the resource. |
| **500**  | **Internal Server Error**      | Generic server-side error.                       |
| **502**  | **Bad Gateway**                | Invalid response from upstream server.           |
| **503**  | **Service Unavailable**        | Server is currently unavailable or overloaded.   |
| **504**  | **Gateway Timeout**            | Server did not receive a timely response.        |

## JS
- types of function
	- normal function
	- function expression
	- arrow function (declared with a help of arrow `=>`), has implicit return for the function
- `fist class function`
- `higher order function` 
	 - Takes another function as an argument.
	 -  Returns another function as its result.
		 ```javascript
		// call function form another
		const action = (x,y)=> x+y;
		const add = (x,y,fn) => fn(x,y);
		console.log(add(10,02,action));
```
	 OR
	 ```javascript
		// return function to the variable
	    const action = (a,b)=> a+b;
		const add=(c)=>c;
		const addition=(c,d)=> c(d);
		var aa=addition(add,action);
		console.log(aa(10,20))
```
- ### setTimeout()
	- this function executes the function in it only after the time given expires
	- syntax
	`setTimeout(function(),time(in milliseconds))`
- ### Promises
	- do deal with asynchronous operations 
```javascript
var p=new Promise((resolve,reject)=>{
    setTimeout(()=>{
        console.log("asdf");
    var pp=new Promise((resolve,reject)=>{
    setTimeout(()=>{
        resolve(50);
    },10000);
    });
    pp.then(
        function(a){resolve(a);}
    );
    pp.catch(
        function(err){console.error(err);}
        );
    pp.finally(
        function(){console.log("inner promise");}
        );
},5000);
});
p.then(
    function(a){console.log(a);}
);
p.catch(
    function(err){console.error(err);}
    );
p.finally(
        function(){console.log("outer promise");}
    );


```

- ### async and await
	- we go with this method when code readability and maintainability comes into consideration. It simplifies error handling with try/catch blocks, providing a cleaner approach compared to promise chaining's `.catch()`
```javascript

async function fn(){
try{
const data1=await delay(1000);
console.log("1",data1);
const data2=await delay(2000);
console.log("2",data2);
const data3=await delay(3000);
console.log("3",data3);

}
catch(err){
console.log(err);
}
}
```

- ### closure
	- A closure in JavaScript is a function's ability to remember and access its lexical scope even when it's executed outside that scope. This "remembrance" allows the function to work with variables that were available at its creation time, regardless of where it's called later.
```javascript
function race(){
	let distance=0;
	function acc(){
		distance++;
	}
	fucntion getd(){
		return distance;
	}
	return [acc,getd];
}

const [acc,getd]=race();
console.log(getd());
acc()
acc()
console.log(getd())
```

- ### function currying

```javascript
function multiply(a){
	function fn(b){
		return a*b;
	}
}
const mul3=multiply(3); // returns fn to the variable
const mul2=multiply(2);
const mul5=multiply(5);

console.log(mul2(10)); //20
console.log(mul5(23)); //115


//volum of cuboid
function l(x){
	return function b(y){
		return function c(z){
			return x*y*z;
		}
	}
}

let ll=l(1)
let bb=ll(2)
console.log(bb(3)) 
console.log(l(1)(2)(3));

//(or)
let l=x=>y=>z=> x*y*z;
console.log(l(1)(2)(3));
```


```javascript
const userContoller={
	createUser:async {req,res}=> {},
	getAllUser:async {req,res}=> {}
}
```

### classes
```javascript
//class based 2
class UsersController{
	static async createUser(req,res){},
	static async getAllUser(req,res){}
}
module.exports=new UsersController();
```

### objects in js
```javascript
const obj={
	name:"john",
	age:23,
	speak: function(){
	console.log(`hello${this.name}, of ${this.age}`);
	}
}
obj.speak();
```


### Object based used when you want to group and export multiple handlers






### login page
```javascript
async register(email,pass){
const 
}
```


### To get apps password in gmail




### node mailer
```js
const nodemailer=require('nodemailer');
const transort =nodemailer.createTransport({
service:'gmail
,
auth{
user:'mail',
pass:'pass'
},
});

const otp=123;
const mailOptions={
from:"mail@gmail.com",
tp:'mail2@g,ail.com',
subject:'aasdf',
html:`
	<h1>yout otp is : ${otp}</h1>
	`
	};
transport.sendMail(mailOptions);
```


### .env files

```md
make sure to add this in the .gitignore file
for accessing use `process.env.EMAIL`

```


### password hasing
```js
const jwt=require('jsonwebtoken');
constzn
```



### ways to use middlewares

- a common middlewares for each routes
- use router.use() method to include common middleware.
- for many middleware
	- use multiple render.use()
	- using array of middlewares


### handle errors in nodejs express
```js
app.use((err,req,res,next)=>{
console.error(err.stack);
res.statuc(500).send('something breoke');
})
```

### passing data between middlewares
```js
const cm1=(req,res,next)=>{
const data="asdf";
console.log("cm1:"+data);
req.value=234;
next(data);
}
const cm2=(data,req,res)=>{
const data="asdf";
console.log("cm2:"+data+req.value);
}
```