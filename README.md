# JAVASCRIPT-Promises

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
      empty_tank.then(function(){
          return enging()
      }).then(function(){
          return travel()
      }).then(function(){
          console.log('Done!')
      })
