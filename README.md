# JAVASCRIPT-Promises

A new Promise is created with the new keyword and the promise provides resolve and reject functions to the provided callback:<br>

      var p = new Promise(function(resolve, reject) {
      	
      	// Do an async task async task and then...
      
      	if(/* good condition */) {
      		resolve('Success!'); //resolved called based on true condition
      	}
      	else {
      		reject('Failure!');  //reject called based on false condition
      	}
      });
      
      p.then(function(result) { 
      	/* do something with the result */
      }).catch(function() {
      	/* error :( */
      }).finally(function() {
         /* executes regardless or success for failure */ 
      });
<br>
The developer must call resolve or reject within the body of the callback based on the result of their given task.<br>
Since a promise is always returned, you can always use the then and catch methods on its return value!<br>
### then
All promise instances get a .then method which allows you to react to the promise.  The 1st then method callback receives the result given to it by the resolve() call<br>

            new Promise(function(resolve, reject) {
            	// A mock async action using setTimeout
            	setTimeout(function() { resolve(10); }, 3000);
            })
            .then(function(result) {
            	console.log(result);
            });
            
            // From the console:
            // 10
The then callback is triggered when the promise is resolved.

Chaining .then method callbacks:<br>

            new Promise(function(resolve, reject) { 
            	// A mock async action using setTimeout
            	setTimeout(function() { resolve(10); }, 3000);
            })
            .then(function(num) { console.log('first then: ', num); return num * 2; })
            .then(function(num) { console.log('second then: ', num); return num * 2; })
            .then(function(num) { console.log('last then: ', num);});
            
            // From the console:
            // first then:  10
            // second then:  20
            // last then:  40  
Each .then receives the result of the previous then's return value.<br>
If a promise has already resolved but then is called again, the callback immediately fires.<br>
If the promise is rejected and you call then after rejection, the callback is never called. <br>

### catch
The catch callback is executed when the promise is rejected:<br>

            new Promise(function(resolve, reject) {
            	// A mock async action using setTimeout
            	setTimeout(function() { reject('Done!'); }, 3000);
            })
            .then(function(e) { console.log('done', e); })
            .catch(function(e) { console.log('catch: ', e); });
            
            // From the console:
            // 'catch: Done!'
What you provide to the reject method is up to you. A frequent pattern is sending an Error to the catch:<br>

            reject(Error('Data could not be found'));

### Promise.all
Takes an array of promises and fires one callback once they are all resolved:

            Promise.all([promise1, promise2])
            .then(function(results) {
            	// Both promises resolved
            })
            .catch(function(error) {
            	// One or more promises was rejected
            });

##### EXAMPLE #1

  var promiseCount = 0;

    function testPromise() { 
      var thisPromiseCount = ++promiseCount;
      console.log(thisPromiseCount + ': Started =Sync code started');
      
      var p1 = new Promise(function(resolve, reject){
        console.log(thisPromiseCount + ': Promise started = Ascync code started');
        // This is only and example to create asynchronism
        setTimeout(function() {
          resolve(thisPromiseCount); 
        }, Math.random() * 2000 + 1000);
      });
      
      p1.then(function(val){
        console.log(val + ': Promise fullfilled = Async code terminated"');
      }).catch(function(reason){
        console.log('Handle rejected promise ('+ reason+') here.');
      })
      console.log(thisPromiseCount + ' : Promise made = Sync code terminated');
    }

`testPromise();` <br>
`testPromise();` <br>
`testPromise(); <br>

#### EXAMPLE #2

      let empty_tank = function(){
          return new Promise(function(resolve,reject){
              resolve('The car doesn't have enough fuel.')
          })
      }
      let engine = function(){
          return new Promise(function(resolve,reject){
              resolve('The engine is over heating.')
          })
      }
      let travel = function(){
          return new Promise(function(resolve,reject){
              resolve('The car is not safe for travelling.')
          })
      }
      empty_tank().then(function(){
          return enging()
      }).then(function(){
          return travel()
      }).then(function(){
          console.log('Done!')
      })
