# JAVASCRIPT-Promises

##### EXAMPLE
function testPromise() { 
  var thisPromiseCount = ++promiseCount;
  console.log(thsiPromiseCount + ': Started =Sync code started');
  
  var p1 = new Promise(function(resolve, reject){
    console.log(thisPromiseCount + ': Promise started = Ascync code started');
    // This is only and example to create asynchronism
    window.setTimeout(function() {
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

testPromise();