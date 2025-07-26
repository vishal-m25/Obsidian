

@HostLinstener -- is similar to eventListerner in react
## string interpolation
- user do print the the value of a variable in the component with the help of `{{}}`
- It can also have function calls of any type(including void)
- attribute binding can also be done
	- ex: src='{{imageURL}}'
## Data binding
- sharing a value(variable) between component and view
- types
	- one way 
	- two way
		- with help of ngModel this is achieved ( `[(ngModel)]`  )

## Property binding
- Assigning values to DOM elements
	- ex:  
		-  `[innerHTML]=hello`
		-  `[disabled]= islogin()`
- using safe navigation to avoid accessing unavailable variables or properties and raising errors `user?.name`
- in here if the name property is available the value is being accessed else it is left aside

## Event binding
- is done with the help of signals (similar to useEffect in react)

## Signals
```ts
count= signal(0); // makes it a writable function when passes with value
double:Signal<number>=computed(()=>this.count()*2);

increment(){

this.count.set(this.count()+1);

}
```


## Directives
- Types
	- components
	- structural
	- attribute

- ### Structural directive
	-  `ngFor` acts like map in react (import commonModule for its access)
	```html
	<ol>
	<li *ngFor="let i of movies">{{i}}</li>
	</ol>
	```
	- similarly in ngFor (sets true/false as value to the variables accordingly)
		- let i=index
		- let f=first
		- let l=last
		- let od=odd
		- let ev=even
		- trackBy=function()
- ### attribute directive
	- #### ngClass
```html
<p [ngClass]="class_name">hi</p>
<p [ngClass]="{'class_name':true/false">hi</p> %% instead of true or false a variable can be asigned and dnamically controlled %%
```
- ### custom directive
	- `ng g directive <name>`
## Pipe
	- to modify original data to some other while showing in  the component or template we use pipe.


## sharing data between componets
-  using input and output decorator

- #### using service
	-  `ng g s <service_name>`

## component life cycle hooks
- ngOnInit
	- runs when the component is about to be shown
- ngDoCheck
	- run everytime a variable or anything inside a component changes
- ngAfterContentInit
	- runs when the component is loaded completely
- ngAfterViewInit
	- runs after the view is completely loaded
- ngAfterViewChecked
- ngOnDestory
	- called when the component is removed from the view
- ngOnChange
	- can be used only when input property is used

## Reactive forms
- forms are created based in model