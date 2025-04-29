# General

 - Node.js is a run time environment that used browser engine to run the server in V8 JavaScript engine , the core of chrome browser outside the browser to provide high performance
 - Express is a node js framework




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


