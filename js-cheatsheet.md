# JS Lambda (Arrow Functions)

***anonymous function***
```JavaScript
var anon = function (a, b) { return a + b };
```

***In ES6 we have arrow functions***:
```JavaScript
// we could write the above example as:
var anon = (a, b) => a + b;
// or
var anon = (a, b) => { return a + b };
// if we only have one parameter we can loose the parentheses
var anon = a => a;
// and without parameters
var () => {} // noop

// this looks pretty nice when you change something like:
[1,2,3,4].filter(function (value) {return value % 2 === 0});
// to:
[1,2,3,4].filter(value => value % 2 === 0);
```

***Be careful when returning objects in arrow functions***:
```JavaScript
(() => {foo: 1})() // this will return undefined.
                   // 'foo: 1' is interpreted as a statement composed of a label and the literal 1

// the correct way should be wrapping it with parenthesis
(() => ({foo: 1}))() // returns Object {foo: 1}
```

#### !One of the major advantages of arrow functions is that it does not have it's own `this` value!

# JS Promise
***basic***
```JavaScript
const p = new Promise((r, j) => {
	r(123);
});

p.then(data => console.log(data))
 .catch(error => console.log(error.message));
```

***Promise.resolve()***
```JavaScript
// The Promise.resolve() method returns a Promise object that is resolved with a given value.
const p = Promise.resolve(123);
const t = Promise.resolve((() => 12 + 34)());
p.then(data => console.log(data));
```

```JavaScript
 var firstMethod = function() {
   var promise = new Promise(function(resolve, reject){
      setTimeout(function() {
         console.log('first method completed');
         resolve({data: '123'});
      }, 2000);
   });
   return promise;
};


var secondMethod = function(someStuff) {
   var promise = new Promise(function(resolve, reject){
      setTimeout(function() {
         console.log('second method completed');
         resolve({newData: someStuff.data + ' some more data'});
      }, 2000);
   });
   return promise;
};

var thirdMethod = function(someStuff) {
   var promise = new Promise(function(resolve, reject){
      setTimeout(function() {
         console.log('third method completed');
         resolve({result: someStuff.newData});
      }, 3000);
   });
   return promise;
};

firstMethod()
   .then(secondMethod)
   .then(thirdMethod);

Promise.resolve(123)
.then(data => {data*data}) // implicity chaining
.then(data => {console.log(data)})
```



